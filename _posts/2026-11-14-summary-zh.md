---
layout: default
title: "Horizon Summary: 2026-11-14 (ZH)"
date: 2026-11-14
lang: zh
---

> 从 39 条内容中筛选出 5 条重要资讯。

---

**科技新闻**
1. [TorchTitan 在 384 块 GH200 上把 1T MoE 训练提速 14 倍](#item-tech-news-1) ⭐️ 8.0/10
2. [KORS 实时全航空波段监听与 GPU 转录](#item-tech-news-2) ⭐️ 7.0/10
3. [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](#item-tech-news-3) ⭐️ 7.0/10
4. [DeepSeek 开放应用 API：搜索、OCR、语音可单独调用](#item-tech-news-4) ⭐️ 7.0/10
5. [OpenAI 推出 ChatGPT Wallet，智能体支付需生物识别确认](#item-tech-news-5) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [TorchTitan 在 384 块 GH200 上把 1T MoE 训练提速 14 倍](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

一位 Reddit 用户（/u/f14-bertolotti）称，其团队与 TorchTitan/PyTorch 维护者合作，在 JUPITER 超算的 384 块 GH200 上把约 1T 参数 MoE 的训练吞吐做到每 GPU 约 1,300 tokens/s，相比最初起点提升 14 倍。并行方案是 384 路 FSDP 加 4 路专家并行（专家并行严格限制在节点内），并主动放弃流水线并行，以免微批过多拉长步长、故障排查变慢；据此他们指出 JUPITER 上 InfiniBand 每 GPU 约 25 GB/s，比 NVLink 慢 6 倍，基线单步 84 秒中有 68 秒在等网络。作者列举的优化包括：全量激活检查点（4 倍）、把检查点激活卸载到 Grace 并经 900 GB/s C2C 链路提前一层预取、用 Muon 替代 Adam 以支撑 64k token 序列、借 FlexShard 按整个专家分片使 Newton-Schulz 本地无通信执行，并提交补丁让参数驻留主机时 Newton-Schulz 仍在 GPU 上跑（优化器步从 42 秒降到约 2 秒，吞吐 +35%）。其他改动有：按注意力开销分桶打包，把最慢 rank 从均值的 7.9 倍压到 1.15 倍（+13%）；专家梯度改用 bf16 all-to-all 取代 fp32 reduce-scatter，字节数减半且求和顺序内结果一致；FP8 专家 all-gather 配 blockwise scale（+18%）；以及修复 PyTorch 缓存分配器按 CUDA 流分池导致的约 21 GiB 占用（重试从 384 个 rank 归零、峰值预留显存降 13.5 GiB、吞吐 +21%）。这些数字均为团队自述，完整图表在 Domyn 博客、精简版在 PyTorch 博客，目前未见独立复现；组限路由带来的 +7% 负载均衡是否损害训练质量，作者明确表示“尚无定论”。

reddit · r/MachineLearning · /u/f14-bertolotti · 11月13日 16:28

**「背景:TorchTitan 与 JUPITER 上的 MoE 实践」** TorchTitan 是 PyTorch 官方的大模型预训练框架,支持 FSDP、专家并行、流水线并行等多维并行组合,也是这次调优工作的载体。PyTorch 博客已刊出同一项工作的完整版本:在 JUPITER 超算的 384 块 GH200\(96 个节点\)上训练约 1.1 万亿参数的 MoE,吞吐从每 GPU 90 tokens/s 提升到约 1,300 tokens/s——这正是 Reddit 帖中所说“14 倍”的起点。

**「对采用 TorchTitan 的团队意味着什么」** 文中的多数优化已回流到 TorchTitan 上游（FlexShard 分片、GPU 端 Newton–Schulz、FP8 expert all-gather），使用 TorchTitan + FSDP2 的团队可直接复用，而不必只在该项目的 384 卡 GH200 集群上复现；由于 TorchTitan 是 PyTorch 原生训练平台，其模型定义还被训练与 vLLM 推理两侧共用，上游改动的受益面不限于单一集群。需要留意的是，把分配移到计算流所依赖的 \`unshard\_async\_op\` 目前仍是 FSDP2 的私有开关，作者仅表示它“正在成为公开 API”，在正式发布前不宜写入生产配置。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://pytorch.org/blog/training-a-1t-parameter-moe-on-eu-public-infrastructure-with-pytorch-and-torchtitan/">Training a 1T-Parameter MoE on EU public ... - PyTorch</a></li>
<li><a href="https://explore.n1n.ai/blog/training-1t-parameter-moe-pytorch-torchtitan-2026-11-13">Training a 1T-Parameter MoE on EU Public Infrastructure with ...</a></li>
<li><a href="https://github.com/pytorch/torchtitan">GitHub - pytorch/ torchtitan : A PyTorch native platform for training...</a></li>

</ul>
</details>

**标签**: `#MoE`, `#TorchTitan`, `#PyTorch`, `#distributed training`, `#GH200`

---

<a id="item-tech-news-2"></a>
### [KORS 实时全航空波段监听与 GPU 转录](https://orcasairband.com/) ⭐️ 7.0/10

一个面向 KORS（Orcas Island 机场）的实时航空波段监听项目已上线：作者称其使用 Ettus B210 接收机配合两块 RTX 4090，通过 CUDA 多相信道化拆分整个航空波段、解调信号、检测发射并生成文字转录。温哥华发生地面停飞（ground stop）时，该项目直播并记录了相关通话；作者强调这些是未经编辑的原始转录，并称这次事件让项目“意外地有用”。这是一个个人爱好项目，而非厂商产品或经过独立验证的行业系统。

hackernews · mmaunder · 11月13日 22:04 · [社区讨论](https://news.ycombinator.com/item?id=50490593)

**「技术背景」** 该项目的硬件基础是 Ettus Research 的 USRP B210：一块双通道收发器，连续覆盖 70 MHz 至 6 GHz，可一次性采集大段航空波段信号。作者在评论中说明，系统随后在双 RTX 4090 上用 CUDA 运行多相信道化器，把宽带信号拆成多个窄带信道，再进行解调、传输检测和语音转写。

**「复刻门槛与转录可靠性」** 对想自行搭建同类监听的人来说，实际门槛主要在硬件与算力：作者用的是 Ettus B210 接收机加双 RTX 4090 主机，并在 GPU 上用 CUDA 做多相信道化、解调与发射检测。作者贴出的内容明确是未经编辑的原始转录，弱信号下会出现无法辨读的片段，评论区也有听众表示大量通话音质含混；因此这类转录更适合作为实时旁听线索，不宜单独当作可靠记录。

**「社区讨论」** 评论区有人回查 14:03 的录音，找到频率上确认“Encore 3325”涉及温哥华 ground stop、当时没有航班起飞前往温哥华的对话，认为这些录音可用于回查事件；另一名评论者则指出不少通话含混难懂，并感叹专业人员的辨听能力。也有评论将其与用 KiwiSDR 解码船舶 DSC 信号的类似爱好者项目类比。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.ettus.com/all-products/ub210-kit/">USRP B 210 USB Software Defined Radio ( SDR ) - Ettus Research</a></li>

</ul>
</details>

**标签**: `#software-defined radio`, `#GPU signal processing`, `#CUDA`, `#airband monitoring`, `#speech transcription`

---

<a id="item-tech-news-3"></a>
### [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

微软 Outlook、Teams 和 Copilot 在 11 月 13 日仍处于宕机状态，故障已持续超过 12 小时，打乱全球企业与政府的通信。微软称原因在于服务器问题，未发现恶意活动，并表示已扩大修复范围、看到回稳迹象。这是微软 365 服务今年第二次中断。

telegram · zaihuapd · 11月13日 12:21

**「背景」** Outlook、Teams 与 Copilot 同属 Microsoft 365 云服务，后端基础设施出现服务器故障时，多个应用可能同时不可用。此次事件被描述为微软 365 服务今年第二次中断，但来源未说明前一次故障的具体时间与范围。

**「影响」** 对澳大利亚、日本和美国部分政府机构以及金融市场参与者而言，故障直接中断了日常通信：欧交所 Euronext 邮件受阻，台湾有金融机构改用传真确认交易。

**标签**: `#Microsoft 365`, `#cloud outage`, `#service reliability`, `#enterprise software`, `#Microsoft Teams`

---

<a id="item-tech-news-4"></a>
### [DeepSeek 开放应用 API：搜索、OCR、语音可单独调用](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek 宣布开放一套“全家桶”应用 API：开发者在原有 API 中开启对应参数，即可获得深度思考搜索、文件输入、链接阅读和语音等对话能力，工具调用与上下文拼接由服务端完成。V4.1-Flash 模型已在三个接口支持这些能力；Search、Fetch、OCR、ASR、TTS 也可单独调用，官方同时开源了可导入历史对话的前端 Demo。该消息未给出三个接口的具体名称、定价、限流或基准测试结果，实际可用范围仍待开发者验证。

telegram · zaihuapd · 11月13日 14:27

**「背景」** DeepSeek 官方文档将这次更新概括为“完整的 DeepSeek App 体验，现在可通过 API 获得”，并把 Search、Fetch、OCR、ASR、TTS 列为可独立调用的接口，同时标注了 V4.1-Flash-1017 这一模型版本。换言之，这些原本属于 DeepSeek 消费端应用的功能，此前并未以独立 API 的形式开放给开发者。

**「影响」** 已使用 DeepSeek API 的开发者可通过参数开关获得工具调用与上下文编排能力，减少自行拼接搜索、文件读取和语音链路的开发工作；只需要单项能力的场景则可直接调用 Search、Fetch、OCR、ASR 或 TTS。由于官方未披露三个接口的具体名称以及计费和配额，接入前仍需核对文档与账号权限。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://api-docs.deepseek.com/news/news261113/">The full DeepSeek App experience, now via API | DeepSeek API Docs</a></li>

</ul>
</details>

**标签**: `#DeepSeek`, `#AI APIs`, `#tool calling`, `#multimodal AI`, `#open source`

---

<a id="item-tech-news-5"></a>
### [OpenAI 推出 ChatGPT Wallet，智能体支付需生物识别确认](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

一个 Telegram 频道转述称，OpenAI 发布了 ChatGPT Wallet，并与美国运通、万事达和 Visa 合作，让 AI 智能体在不接触用户真实卡号的情况下完成付款，且每笔购买都需要用户验证。按该转述，功能自发布当日（11 月 13 日）起在美国面向 18 岁以上的 ChatGPT Pro 订阅用户开放，需绑定美国发行的银行卡；用户逐笔核对商品与金额并用 Face ID 或指纹确认，支付网络则下发替代真实卡号的支付令牌。转述还提到该功能通过名为 dots 的渠道提供，但未作进一步说明。以上内容均来自一条简短的社交媒体帖子，没有技术细节，也未获独立确认，应视为待核实的发布信息。

telegram · zaihuapd · 11月13日 15:43

**「背景：网络令牌与智能体支付」** 支付令牌（network token）是卡组织已有的机制：由支付网络签发替代真实卡号的凭证，并绑定到特定设备或商户，使商户和中间环节都接触不到原始卡号。ChatGPT Wallet 把这一机制用于智能体发起的购买，OpenAI 表示它由美国运通、万事达和 Visa 合作构建，首批通过 dots 向美国 ChatGPT Pro 订阅用户提供。据 CNBC 报道，参与合作的三家卡组织持卡人仍可保留原有的信用卡积分权益。

**「影响」** 对符合条件的用户（美国 18 岁以上 ChatGPT Pro、使用美国发行卡）而言，智能体代付仍须逐笔人工核对商品与金额，并通过 Face ID 或指纹确认，因此目前更适合有人值守的代买，而非完全无人值守的连续采购。使用非美国发行卡或非 Pro 账户则无法使用这一首批功能。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/introducing-chatgpt-wallet/">Introducing ChatGPT Wallet | OpenAI</a></li>
<li><a href="https://www.cnbc.com/2026/11/13/openai-chatgpt-wallet-dot-purchases.html">OpenAI &#x27;s ChatGPT Wallet allows &#x27; dots &#x27; AI agents to make purchases</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#agentic payments`, `#ChatGPT Wallet`, `#payment tokenization`, `#fintech`

---