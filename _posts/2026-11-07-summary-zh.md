---
layout: default
title: "Horizon Summary: 2026-11-07 (ZH)"
date: 2026-11-07
lang: zh
---

> 从 38 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [百度开源文心 5.5 Flash Base 基座模型](#item-tech-news-1) ⭐️ 8.0/10
2. [Libghostty 1.0 发布，开源终端模拟库迎来 1.0 里程碑](#item-tech-news-2) ⭐️ 7.0/10
3. [Firecracker PwnEscape 逃逸的实战利用分析](#item-tech-news-3) ⭐️ 7.0/10
4. [Boson AI 发布 45B MoE 全双工模型 Higgs Realtime Duplex](#item-tech-news-4) ⭐️ 7.0/10
5. [长江存储拟建武汉第四厂，国产设备占比最高 70%](#item-tech-news-5) ⭐️ 7.0/10
6. [欧盟指控 TikTok 推荐算法违反《数字服务法》](#item-tech-news-6) ⭐️ 7.0/10
7. [淘宝 MNN 开源 0.3B 手机端模型](#item-tech-news-7) ⭐️ 7.0/10
8. [传 Anthropic 下周启动 IPO 路演，拟 11 月 16 日当周上市](#item-tech-news-8) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [百度开源文心 5.5 Flash Base 基座模型](https://www.news.cn/info/20261105/f3bbdb6854f5441ca9fb34062f213875/c.html) ⭐️ 8.0/10

百度宣布正式开源基座模型文心 5.5 Flash Base。该模型采用 MoE 架构，总参数量 2800 亿，每个 Token 激活 140 亿参数，预训练使用 33.5 万亿 Token，预训练上下文最长为 128K，微调与推理支持最长 100 万 Token 上下文。现有信息未包含基准测试结果和开源许可证条款，因此模型的实际能力与使用条件仍需进一步确认。

telegram · zaihuapd · 11月6日 05:41

**「背景」** 文心 5.5 Flash Base 属于混合专家（MoE）架构：模型总参数量远大于每个 Token 实际激活的参数量，推理时只调用部分专家，从而用较低的计算开销获得更大的模型容量。所谓“基座模型”，指未经指令对齐、主要供开发者做后续微调与二次开发的预训练模型，其上下文长度则决定微调和推理阶段一次能处理多长的输入。

**「对开发者的影响」** 对开发者而言，最直接的约束是这次发布的是基座模型，而不是指令微调模型；Hacker News 上有评论因此认为它不能直接按指令使用，团队需要自行完成后训练和对齐，才能用于对话或任务型应用。结合 2800 亿总参数、每 Token 激活 140 亿参数的规模，微调和长上下文推理仍需按大模型来配置算力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://ernie.baidu.com/release/ernie-5-5-flash-base/">ERNIE 5 . 5 Flash Base · ERNIE</a></li>
<li><a href="https://news.ycombinator.com/item?id=50377078">Baidu released ERNIE 5 . 5 Flash Base | Hacker News</a></li>

</ul>
</details>

**标签**: `#Baidu ERNIE`, `#open-source LLM`, `#MoE`, `#long context`, `#model release`

---

<a id="item-tech-news-2"></a>
### [Libghostty 1.0 发布，开源终端模拟库迎来 1.0 里程碑](https://mitchellh.com/writing/libghostty-1-0) ⭐️ 7.0/10

Libghostty 1.0 已发布，这是一个面向终端工具开发者的开源终端模拟库。此次发布是该项目的 1.0 里程碑，服务对象是需要在自有终端或编辑器项目中复用终端模拟能力的开发者。现有材料没有列出具体的 API 变更、支持平台或性能数据，因此这些技术细节尚无法确认。

hackernews · mfiguiere · 11月6日 23:30 · [社区讨论](https://news.ycombinator.com/item?id=50399933)

**「背景」** Libghostty 是从 Ghostty 终端模拟器中抽出的可嵌入终端核心。2024 年 10 月，Mitchell Hashimoto 在关于 Ghostty 1.0 的文章中说明，libghostty 当时还不被视为稳定或可独立使用的公共 API，只作为 Ghostty 的内部组件；一份第三方项目页面在 2025 年 9 月仍将其标为未发布，称仅有供测试的 Zig API，C API 尚待提供。

**「影响」** 对终端或编辑器项目的开发者而言，Libghostty 1.0 提供了一个可单独集成的开源终端模拟层，能减少从零实现终端行为的工作量；但材料未说明支持平台、API 稳定性或升级注意事项，采用前仍需自行核对这些条件。

**「社区讨论」** Hacker News 评论对这次发布整体持正面态度，有开发者表示已在 Android 项目和自建终端项目中使用 Libghostty，认为它确实可用，并节省了大量底层工作；也有人称它促成了 Emacs 终端项目 Ghostel。评论中没有出现具体的技术反对意见。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://mitchellh.com/writing/ghostty-is-coming">Ghostty 1 . 0 is Coming – Mitchell Hashimoto</a></li>
<li><a href="https://playbooks.com/skills/plurigrid/asi/libghostty-vt">libghostty -vt skill by plurigrid/asi</a></li>

</ul>
</details>

**标签**: `#terminal emulators`, `#libghostty`, `#open source`, `#developer tools`, `#libraries`

---

<a id="item-tech-news-3"></a>
### [Firecracker PwnEscape 逃逸的实战利用分析](https://pwn.ai/blog/firecracker-escape) ⭐️ 7.0/10

一篇面向虚拟化与系统安全读者的技术文章，详细演示了如何在实际环境中利用 PwnEscape 实现 Firecracker 虚拟机逃逸。文章明确指出这不是新漏洞，而是对先前已披露问题的利用实践。演示所用配置未启用 jailer；Firecracker 的生产隔离还包括降权、命名空间和 seccomp，因此不能把该结果直接套用到加固部署。对启用这些控制的部署，仍需单独评估 VMM 被攻陷后可获得的权限和资源。

hackernews · SerCe · 11月6日 19:33 · [社区讨论](https://news.ycombinator.com/item?id=50397219)

**「背景」** 本文是 PwnEscape 漏洞的第二篇实战利用分析。该漏洞编号 CVE-2026-99999，由 pwn.ai 的 Paulos Yibelo 在 2026 年 8 月 Vercel 百万美元沙箱挑战赛期间发现，据披露其成因是宿主机 IPv4 网络代码中的校验和处理可被 guest 构造的报文滥用，从而让 KVM 客户机读取宿主机内存。此前的公开讨论集中在漏洞本身，本次则是把利用链落到具体部署上：文中环境用 systemd-run 以 root 直接启动 Firecracker 且未启用 jailer，因此拿到宿主机 root 是该部署方式的结果，而非所有 Firecracker 部署的通用后果。

**「影响」** 对 Firecracker 运维者而言，关键动作是区分未启用 jailer 的实验配置与生产加固配置，并单独评估 VMM 被攻陷后在 jailer、命名空间和 seccomp 限制下仍可触及的权限与资源。

**「社区讨论」** 评论中有人强调这不是新漏洞，而是对数周前披露的 PwnEscape 的实战利用说明；也有人希望文章进一步说明，在启用 jailer、命名空间和 seccomp 的生产配置下，VMM 被攻陷后实际还剩哪些权限。另有运营者表示其 ClickBench playground 完全依赖 Firecracker，并称可在该服务上做逃逸 PoC。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://sesamedisk.com/firecracker-escape-guest-to-host-root/">Firecracker Escape: From Guest to Host Root - Sesame Disk</a></li>
<li><a href="https://cyberexperts.com/2026-10-16-linux-pwnescape/">Linux PwnEscape CVE-2026-99999: KVM Guest Can Read Host Memory</a></li>

</ul>
</details>

**标签**: `#Firecracker`, `#virtualization security`, `#VM escape`, `#exploit development`, `#microVMs`

---

<a id="item-tech-news-4"></a>
### [Boson AI 发布 45B MoE 全双工模型 Higgs Realtime Duplex](https://www.reddit.com/r/MachineLearning/comments/1xpn5pv/higgs_realtime_duplex_a_45b_moe_fullduplex_model/) ⭐️ 7.0/10

Boson AI 发布 Higgs Realtime Duplex，这是一个 45B 的 MoE（混合专家）全双工模型，可同时接收音频和视频、输出语音，并在说话的同时于后台完成推理、工具调用和子任务委派。所有数据流按 160 ms 分块：音频输入每块 1 个 token，音频输出每块 2 个 token，每 6 块插入一帧约 12 token 的摄像头画面；Boson AI 称，音视频合计约 2.6K token/分钟，加上思考与工具轨迹为 2.6K–5K，最近 5 分钟内容加压缩文本历史为 13K–25K token。模型权重不开放，Duplex API 需排队申请，此前的回合制 Higgs Realtime 现已可用；声音与形象在部署时用一段参考音频、一张图片和一段行为提示词零样本设定，无需微调。厂商自测称，该模型在 Big Bench Audio 等 7 项基准中与竞品互有胜负，但 OpenAI 最佳配置在 5 项上领先 1–5 分，Full-Duplex-Bench 的轮次切换是 Boson AI 差距最大处；这些均为厂商数据，部分竞品数字为 Boson AI 自行复现，尚无独立评测。

reddit · r/MachineLearning · /u/Cali\_Cobarde · 11月6日 20:23

**「背景」** 主流语音模型大多仍是&quot;轮次式&quot;的：先听、等用户说完、再思考、最后说话，输入与输出并不重叠。2026 年 5 月 11 日，Thinking Machines Lab 预告了名为 Interaction Model 的全双工系统，以约 200 毫秒的微轮次同时处理音频、视频和文本，边听边看边说，并可在 0.4 秒内响应；Boson AI 在发布中正是把这套模型作为主要对照对象逐项比较。Boson AI 此前已有轮次式的 Higgs Realtime 可用，Duplex 是同一产品线上转向全双工的新版本。

**「对开发者的直接影响」** 对开发者来说，最直接的限制是可用性：Duplex 不开放权重，API 需要排队申请，目前能立即接入的仍是基于轮次的前代 Higgs Realtime，想马上上线实时语音代理的团队只能沿用轮流式方案。Boson AI 给出的设计目标是模型运行一小时的成本不超过人类一小时成本的十分之一，并把较难的问题连同完整共享上下文委派给更大的后端模型，因此实际开销和延迟会随委派频率上升；这些指标目前均为厂商自述，尚无独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aiautomationglobal.com/blog/thinking-machines-interaction-models-full-duplex-voice-ai-2026">Thinking Machines Interaction Models: Voice AI That Listens ...</a></li>
<li><a href="https://ailearningguides.com/thinking-machines-lab-interaction-models-listen-while-speaking/">Thinking Machines Lab&#x27;s Interaction Models Listen While ...</a></li>

</ul>
</details>

**标签**: `#full-duplex speech models`, `#multimodal LLMs`, `#mixture-of-experts`, `#real-time audio/video`, `#tool use`

---

<a id="item-tech-news-5"></a>
### [长江存储拟建武汉第四厂，国产设备占比最高 70%](https://www.reuters.com/world/china/chinas-top-flash-memory-chipmaker-targets-more-homegrown-tools-new-factory-2026-11-06/) ⭐️ 7.0/10

长江存储计划在武汉建设第四座工厂，预计 2027 年开工，目标将国产设备采购比例提升至至少 60%、最高 70%，高于第三座工厂目前超过 50%的水平。新厂将生产 300 层以上的 NAND 闪存，主要面向数据中心和人工智能存储需求。这是规划中的产能项目，并非已投产能力；光刻、检测等先进设备仍依赖海外供应商。

telegram · zaihuapd · 11月6日 08:34

**「背景」** 长江存储是中国最大的闪存芯片制造商，其第三座工厂目前的国产设备采购比例已超过 50%。在美国出口管制收紧先进半导体设备供应的背景下，该公司计划把新工厂的国产设备占比进一步提高到 60%—70%，同时生产 300 层以上的 NAND 闪存。

**「影响」** 若计划推进，清洗、抛光和刻蚀设备供应商将获得新增订单，但光刻和检测环节的海外依赖意味着国产设备尚不能覆盖整条产线，这些环节的供应情况将制约该厂的设备国产化上限。

**标签**: `#semiconductors`, `#NAND flash`, `#YMTC`, `#export controls`, `#supply chain`

---

<a id="item-tech-news-6"></a>
### [欧盟指控 TikTok 推荐算法违反《数字服务法》](https://www.cnbc.com/2026/11/06/eu-charges-tiktok-harmful-algorithmic-rabbit-hole-effects.html) ⭐️ 7.0/10

欧盟委员会指控 TikTok 的推荐算法造成有害的“兔子洞”效应，违反《数字服务法》，并称其未采取有效措施应对相关风险。委员会要求 TikTok 调整“为你推荐”信息流，使其更多依据用户明确偏好，改进控制选项并定期测试算法。若问题未解决，母公司字节跳动明年可能面临最高相当于全球年营收 6% 的罚款；该指控属于更广泛调查的一部分，欧盟还称持续推送相似内容可能影响心理健康。

telegram · zaihuapd · 11月6日 14:03

**「背景」** 《数字服务法》是欧盟用于约束在线平台内容与系统风险的规则框架，平台若被认定不合规可能面临高额罚款。欧盟委员会两年多前已就 TikTok 是否违反该法展开调查；此次针对“为你推荐”信息流“兔子洞”效应的指控属于该调查中的初步认定，尚不是最终处罚决定。

**「整改与罚款风险」** 对 TikTok 的直接后果是必须在回应期内调整“为你推荐”的排序依据、改进用户控制选项并定期测试算法；若欧盟不接受整改，其母公司字节跳动可能面临最高相当于全球年营收 6% 的罚款。TikTok 仍可查阅案卷、作出答复并选择修改算法以避免处罚，因此推荐流的产品逻辑可能先于罚款发生实际变化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktoks-you-feed-breach-digital-services-act-harmful-rabbit-holes">Commission preliminarily finds TikTok’s ‘For You’ feed in ...</a></li>
<li><a href="https://apnews.com/article/tiktok-european-union-brussels-social-media-regulation-f59bbe2045ab842c0a4beef4e9a050e2">EU says ‘rabbit hole’ video feeds on TikTok violate its ...</a></li>
<li><a href="https://reclaimthenet.org/eu-commission-tiktok-algorithm-digital-services-act">European Commission Says TikTok Recommendation Algorithm...</a></li>

</ul>
</details>

**标签**: `#EU Digital Services Act`, `#TikTok`, `#recommendation algorithms`, `#platform regulation`, `#algorithmic accountability`

---

<a id="item-tech-news-7"></a>
### [淘宝 MNN 开源 0.3B 手机端模型](https://www.ithome.com/1/023/212.htm) ⭐️ 7.0/10

11 月 6 日，淘宝 MNN 团队开源了约 3 亿参数的端侧语言模型 MNN-Pocket-0.3B，并分别发布预训练、后训练和端侧部署版本。该模型采用 28 层结构，词表从 151K 精简至 64K；INT4 部署文件为 173 MB，团队称可在 iPhone 18 Pro 上完全离线运行，平均解码约 350 token/s。团队设定的目标是峰值内存低于 300 MB、解码超过 200 token/s；上述设备表现来自团队或报道方说法，尚未见独立复现结果。

telegram · zaihuapd · 11月6日 15:13

**「背景」** 根据 Hugging Face 模型卡，MNN-Pocket-0.3B 面向端侧助手、数据抽取和轻量智能体流程；和多数十亿参数以下模型一样，它不建议用于高难度数学或长程代码生成等推理密集型任务。另一个仓库 MNN-Pocket-0.3B-MNN 提供可由 MNN 引擎运行的 INT4 版本，模型卡列出了 512 token 上下文下的端侧速度数据。

**「对移动开发者的直接影响」** 对移动开发者而言，173 MB 的 INT4 部署文件和低于 300 MB 的峰值内存目标，意味着模型可以放进普通 App 的内存预算内完全离线运行，无需调用云端推理；团队按预训练、后训练、端侧部署分版本开源，实际集成时应选端侧部署版本。需要注意的是，词表已从 151K 精简至 64K，而约 350 token/s 的解码速度是 iPhone 18 Pro 上的数据，其他机型的实际表现仍需自行实测。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B">taobao-mnn/MNN-Pocket-0.3B · Hugging Face</a></li>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B-MNN">taobao-mnn/MNN-Pocket-0.3B-MNN · Hugging Face</a></li>

</ul>
</details>

**标签**: `#on-device LLM`, `#MNN`, `#open-source models`, `#mobile inference`, `#quantization`

---

<a id="item-tech-news-8"></a>
### [传 Anthropic 下周启动 IPO 路演，拟 11 月 16 日当周上市](https://www.theinformation.com/briefings/anthropic-proceed-ipo-roadshow-next-week) ⭐️ 7.0/10

据 Telegram 摘要援引知情人士，Anthropic 计划下周启动 IPO 路演，并拟在 11 月 16 日当周、美国感恩节假期前挂牌上市。摘要称，市场此前预计该公司以 1.5 万亿美元估值募资超 800 亿美元，但近两周科技股剧烈波动及对 AI 股票和支出的担忧，可能促使其寻求更低估值。上述时间表、估值和募资规模均未获 Anthropic 或承销方确认，应视为未经证实的报道。

telegram · zaihuapd · 11月7日 01:27

**「背景」** Anthropic 已于 2026 年 10 月披露 IPO 申报文件，其中显示其 2026 年上半年营收为 162.9 亿美元；当时投资者讨论的估值约为 1.5 万亿美元，但公司尚未公布官方发行价区间。此后 AI 股票遭遇抛售，市场对 Anthropic 的估值预期先后下调，ZeroHedge 援引的报道提到投资者与承销商讨论的“公允价值”已降至约 1.2 万亿美元，这为本次路演可能寻求更低估值提供了直接背景。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.fxstreet.com/news/anthropic-ipo-filing-reveals-rapid-growth-as-investors-weigh-an-80-billion-loss-202610270748">Anthropic IPO filing reveals rapid growth as investors weigh an $ 80 ...</a></li>
<li><a href="https://www.zerohedge.com/markets/haircut-no-2-anthropic-ipo-talk-slides-12-trillion-ai-rout-crushes-odds-november-listing">Haircut No. 2: Anthropic IPO Talk Slides To $ 1 .2 Trillion ... | ZeroHedge</a></li>

</ul>
</details>

**标签**: `#Anthropic`, `#IPO`, `#AI industry`, `#valuation`, `#market news`

---