---
layout: default
title: "Horizon Summary: 2026-11-05 (ZH)"
date: 2026-11-05
lang: zh
---

> 从 52 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [OpenAI 称流水线生成 948 个 Linux 提权利用程序](#item-tech-news-1) ⭐️ 8.0/10
2. [Go 发布新的标准库 JSON API](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic 开源 FlashProve 验证模型身份](#item-tech-news-3) ⭐️ 8.0/10
4. [Trainium2 上 GLM-5.3-Flash 的 NKI 层级 megakernel](#item-tech-news-4) ⭐️ 8.0/10
5. [月之暗面据称开源 Kimi K3.1 Pro 权重](#item-tech-news-5) ⭐️ 8.0/10
6. [AI 漏洞审计被指迫使软件业偿还四十年技术债](#item-tech-news-6) ⭐️ 7.0/10
7. [AMD 预计 Q4 营收将首次超过英特尔](#item-tech-news-7) ⭐️ 7.0/10
8. [腾讯 Hy4 开放权重发布，含科研与游戏适配](#item-tech-news-8) ⭐️ 7.0/10
9. [在 B200 上实测 Huginn 循环 Transformer：权重共享未必减少 HBM 读取](#item-tech-news-9) ⭐️ 7.0/10
10. [甲骨文据报取消腾讯 70 亿美元 AI 芯片租赁](#item-tech-news-10) ⭐️ 7.0/10
11. [华为据报要求客户自购升腾 960DT 所需 HBM](#item-tech-news-11) ⭐️ 7.0/10
12. [蓝牙 HDT 标准获采纳：LE 峰值速率升至 7.5 Mbps](#item-tech-news-12) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 称流水线生成 948 个 Linux 提权利用程序](https://openai.com/index/a-thousand-fewer-paths-to-root/) ⭐️ 8.0/10

OpenAI 表示，其自主漏洞研究流水线在 2026 年 10 月的一次 Linux 内核扫描中动态复现了 1,724 个漏洞，并生成了 948 个能让本地低权限用户获得 root 权限的可用提权利用程序，另有 291 个信息泄露 PoC。OpenAI 给出的总 API 成本为 1,213,430 美元，平均每个成功的本地提权利用程序约 1,279 美元；该公司还称，第三方专家确认其中至少 10 种 Linux 利用技术是新的。上述数字以及“减少通往 root 的路径”的效果均来自 OpenAI 的自述，所给材料缺少文章正文和独立测量，无法核验。

hackernews · dangelosaurus · 11月4日 23:33 · [社区讨论](https://news.ycombinator.com/item?id=50372929)

**「背景」** Linux 本地提权（LPE）漏洞是指本地低权限用户绕过权限边界、最终取得 root 权限的缺陷；要让这类漏洞真正可被利用，通常还需绕过 SMEP、SMAP、KASLR、HARDENED\_USERCOPY 等内核缓解机制，OpenAI 的原型也正是在开启这些防护的系统上验证利用程序。该研究是 OpenAI 于 2026 年 11 月 4 日发布的自主漏洞研究流水线运行结果，公司称已为识别出的漏洞编写补丁，但这仍是研究原型的产出，而非已经合并进主线的内核修复。

**「对运维与补丁节奏的影响」** 对运维团队的直接影响是：在尚未合入上游修复的内核上，应把本地普通账户视为等同于 root，多租户主机、容器宿主和 CI 执行节点尤其需要按这一前提重排补丁优先级；Ubuntu 对 Dirty Frag（CVE-2026-43284、CVE-2026-43500）的处置就是先由上游修复、再由发行版发布更新的流程（tool-3-2）。由于 OpenAI 公布的是其流水线单次扫描的复现结果，而非经第三方逐条确认的 CVE 清单，实际需要修补的范围仍取决于各发行版与内核维护者对具体问题的确认和回填。

**「社区讨论」** 在 Hacker News 的讨论中，有评论者追问内核为何会积累约一千个提权漏洞，怀疑内核复杂性、安全模型或语言实现是根源；也有人反问，在如此多漏洞存在的情况下，互联网和电力等基础设施为何仍能运行。还有评论者表示，自己一直假定拿到本地用户权限就几乎等于能拿到 root，但 948 个可用提权利用程序的数量仍令人震惊。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/a-thousand-fewer-paths-to-root/">A thousand fewer paths to root - OpenAI</a></li>
<li><a href="https://cybersecuritynews.com/openai-uncovers-948-linux-kernel-vulnerabilities/">OpenAI Cyber Model Uncovers 948 Linux Kernel Privilege ...</a></li>
<li><a href="https://ubuntu.com/blog/dirty-frag-linux-vulnerability-fixes-available">Dirty Frag Linux kernel local privilege escalation ... - Ubuntu</a></li>

</ul>
</details>

**标签**: `#Linux kernel`, `#privilege escalation`, `#security research`, `#AI-assisted vulnerability discovery`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Go 发布新的标准库 JSON API](https://go.dev/blog/jsonv2) ⭐️ 8.0/10

Go 官方博客发布了新的标准库 JSON API，面向所有使用 Go 处理 JSON 的开发者，核心的 encoding/json 使用方式将随之调整。现有材料显示这一改动涉及 API 设计与迁移影响，但未给出具体版本号、函数签名或发布时间。开发者需要关注新 API 与旧代码的兼容性及迁移成本。

hackernews · olexsmir · 11月4日 17:52 · [社区讨论](https://news.ycombinator.com/item?id=50369106)

**「背景」** Go 的 encoding/json 包长期提供 Marshal 和 MarshalIndent 等入口来处理 JSON 序列化，其中后者用于带缩进的可读输出。此次官方博客在介绍 v2 API 前，先引入了 encoding/json/jsontext 包，并称其为此后改进 Go 中 JSON 支持的基础。

**「迁移与兼容性」** 现有 Go 项目不能把 encoding/json/v2 当作无缝替换：据第三方梳理，v2 随 Go 1.27 发布并包含破坏性变更，而社区讨论特别提到 MarshalIndent 被移除后，生成带缩进的可读 JSON 需要改写成更复杂的代码。依赖旧版序列化 API 或输出格式的项目应在升级前检查相关调用并补充迁移测试。

**「社区讨论」** 有评论者表示总体上认可 encoding/json/v2 的方向，但抱怨没有保留 MarshalIndent，认为替代写法复杂且不直观，会增加迁移和快速输出可读 JSON 的成本。另一位开发者则分享了在公司使用 jsontext 解析器处理需要针对不同错误给出具体信息的场景，称其性能出色但缺少内省能力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2">A new Go API for JSON - The Go Programming Language</a></li>
<li><a href="https://stackoverflow.com/questions/44495489/what-is-the-difference-between-json-marshal-and-json-marshalindent-using-go">What is the difference between json . Marshal and json . MarshalIndent ...</a></li>
<li><a href="https://antonz.org/go-json-v2/">JSON evolution in Go : from v1 to v 2</a></li>
<li><a href="https://stackoverflow.com/questions/44495489/what-is-the-difference-between-json-marshal-and-json-marshalindent-using-go">What is the difference between json . Marshal and json . MarshalIndent ...</a></li>

</ul>
</details>

**标签**: `#Go`, `#JSON`, `#standard library`, `#API design`, `#encoding/json/v2`

---

<a id="item-tech-news-3"></a>
### [Anthropic 开源 FlashProve 验证模型身份](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic 正在开发并开源 FlashProve，用加密证明核验某段 AI 输出是否由指定模型生成，可帮助识别模型替换，也可核实第三方关于模型执行任务的说法。发布模型的实验室需公开不泄露权重的指纹，供后续匹配输出，验证可在本地设备进行。Anthropic 已发布技术规范和代码，但研究仍在进行，目前没有部署计划。

hackernews · ltononro · 11月4日 17:17 · [社区讨论](https://news.ycombinator.com/item?id=50368626)

**「背景」** 可验证推理要回答的是：用户如何在不看到模型权重的情况下，确认某次输出确实由声称的模型生成；Anthropic 将 FlashProve 描述为模型提供方（证明者）与用户（验证者）之间的加密证明系统，使验证者无需获得专有权重即可核验。该项目的 GitHub 原型显示，FlashProve 以 Llama 4 Maverick 全尺寸模型、1024 token 上下文在单张 H100 上运行，预填充约 110 token/s（24 请求批处理），并致谢 James Petrie 的 VerInf 早期工作；有评论者自称 VerInf 作者，称 FlashProve 大量沿用了该工作但归属不足，这属于社区说法。

**「影响」** 对需要审计模型来源的用户和平台，FlashProve 提供了一种不公开权重也能核验输出模型归属的机制；但评论中提到的约 90–100 倍计算开销，以及单次证明检查在 24 线程下约 17 秒、单线程下约 21 秒的成本，意味着短期部署更可能限于高价值审计场景。

**「社区讨论」** 评论者一方面肯定这是对先前零知识证明结果的显著改进，另一方面集中质疑代价：有评论称其计算开销约为 90–100 倍，并认为对开放权重模型直接重算更便宜，或用多个独立推理提供者、签名响应等方案替代。还有评论者 neuwirth 声称该工作大量沿用了其 VerInf 研究而归属不足，这属于个人指控而非已核实事实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.anthropic.com/research/provable-inference">Progress on provable inference for large language models \ Anthropic</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/anthropic-flashprove-cryptographic-model-verification">Anthropic unveils cryptographic tool to verify model outputs</a></li>
<li><a href="https://github.com/anthropics/FlashProve">GitHub - anthropics/ FlashProve : A research prototype for...</a></li>

</ul>
</details>

**标签**: `#provable inference`, `#LLM verification`, `#zero-knowledge proofs`, `#Anthropic research`, `#verifiable computation`

---

<a id="item-tech-news-4"></a>
### [Trainium2 上 GLM-5.3-Flash 的 NKI 层级 megakernel](https://www.reddit.com/r/MachineLearning/comments/1xo0yuq/p_nki_layer_megakernels_for_glm53flash_on_aws/) ⭐️ 8.0/10

RunAnywhere 开源了面向 AWS Trainium2 的推理引擎 trnrt，可在单台 trn2.48xlarge 上服务 320B MoE、100 万 token 上下文的 GLM-5.3-Flash。作者称，他们把每个层的一半（稀疏注意力层则整层）重写为单个 NKI megakernel，将激活、循环状态和在途权重控制在每个物理 NeuronCore 的 28 MiB SBUF 内，并让两个物理核分担 672–708 GB/s 的权重流。按作者自报，同一布局下 batch-8 解码一步从 10 月 17 日版本的 32.2 ms 降至 11 月 1 日版本的 24.2 ms，其中 6.1 ms 是内存下限；由于最新 vLLM Neuron 插件未注册 GLM 模型、NxD Inference 处于维护模式，没有现成的 AWS 基线可对比。作者还称稀疏注意力 prefill 仍保留一项近似，并且尚未运行任务级评测，相关基准均需独立复现。

reddit · r/MachineLearning · /u/WildCard727 · 11月4日 21:47

**「背景」** Trainium2 是 AWS 的第三代自研机器学习芯片，每颗芯片包含八个 NeuronCore-V3，并引入逻辑 NeuronCore 配置（LNC），可将多个物理核心的计算与内存资源组合成一个逻辑核心。NKI 是面向 Trainium 和 Inferentia 的低层自定义内核编程接口，可直接访问 NeuronCore ISA。这为作者将每层的一半写成一个 NKI 内核、并尽量把工作集留在片上 SBUF 的做法提供了硬件与编程模型基础。

**「对使用者的直接影响」** 对于要在 Trainium2 上部署 GLM-5.3-Flash 的团队，目前没有受支持的现成路径：作者指出最新 vLLM Neuron 插件未注册任何 GLM 模型，NxD Inference 又处于维护模式，因此手写 NKI 内核（Neuron SDK 提供的自定义内核路径）成为实际可行的方案。但单内核的基准测试结果不能直接外推到整步：作者报告一个 dense FFN 内核单独运行时为 84 µs 且比特一致，却因 XLA 重新调度使 batch 2 的整步慢了 55 µs，这说明任何采用者都需要按整步来验证收益。该版本还保留稀疏注意力 prefill 中的一处近似，并且尚未做任务级评测，所以采用者应把 35.9 tokens/s 等端到端数字视为作者自测、待独立复现的结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/latest/general/arch/neuron-hardware/trainium2.html">Trainium2 Architecture — AWS Neuron Documentation</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/latest/general/nki/index.html">Neuron Kernel Interface (NKI) — AWS Neuron Documentation</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/">AWS Neuron Documentation</a></li>

</ul>
</details>

**标签**: `#AWS Trainium`, `#inference optimization`, `#GPU/accelerator kernels`, `#mixture-of-experts`, `#performance profiling`

---

<a id="item-tech-news-5"></a>
### [月之暗面据称开源 Kimi K3.1 Pro 权重](http://platform.kimi.ai/) ⭐️ 8.0/10

据 Telegram 频道“科技圈·茶馆”报道，月之暗面已在 Hugging Face 发布 Kimi K3.1 Pro 的开放权重，并同步在 platform.kimi.ai 提供 API；这是 K3.1 系列首个模型。该模型为原生多模态智能体模型，总参数 2.8T、激活 104B，上下文约 100 万 token，权重以 MXFP4 量化形式发布；API 模型名为 kimi-k3.1-pro，兼容 OpenAI 与 Anthropic 接口。上述信息目前仅来自这一单一来源，尚未获得独立验证，权重许可、实际硬件需求和基准表现均未由来源说明。

telegram · zaihuapd · 11月4日 15:47

**「背景」** Kimi K3.1 Pro 采用稀疏混合专家架构：总参数为 2.8T，但每次推理只激活 104B，以控制实际算力开销。权重以 MXFP4 低精度量化形式发布，目的是压缩模型体积、降低部署门槛；月之暗面将 K3.1 Pro 定位为 K3.1 系列的首个模型，并同时提供托管 API。

**「落地成本」** 量化后的权重体积约 1.63TB，这意味着自建部署需要大容量多卡节点和相应显存，普通团队很难在本地运行完整的 2.8T 参数模型。对多数使用者来说，更现实的路径是通过 platform.kimi.ai 的 kimi-k3.1-pro，即兼容 OpenAI 与 Anthropic 接口的 API，或第三方推理服务来调用，而非直接下载权重自行托管。

**「社区讨论」** 评论者对其实际水平存在分歧：有人称 K3.1 相对 DeepSeekV4.1-Flash 提升有限，并在第三方内部基准上得分不高、疑似“刷榜”；也有人表示自家测试未见到这种现象，认为它是略低于前沿但适合多数用例的强开源模型。还有评论提到本地运行可能需要约 8 块 B300，而 OpenRouter 等第三方推理商已开始托管，吞吐和价格仍有优化空间。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/moonshotai/Kimi-K3">moonshotai/Kimi-K3 · Hugging Face</a></li>
<li><a href="https://www.developersdigest.tech/blog/kimi-k3-open-weights-huggingface-release">Kimi K 3 Weights Land on HuggingFace: 2 . 8 T Open Frontier Model...</a></li>

</ul>
</details>

**标签**: `#open-weights`, `#multimodal-ai`, `#mixture-of-experts`, `#long-context`, `#Kimi`

---

<a id="item-tech-news-6"></a>
### [AI 漏洞审计被指迫使软件业偿还四十年技术债](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

IEEE Spectrum 的一篇分析文章提出，AI 漏洞审计正在迫使软件行业面对约四十年积累的技术债，并以 PHP2Shell 漏洞为案例展开讨论。该文属于观点与分析，并非新工具发布或独立测量结果，也没有给出可验证的漏洞数量、修复成本或时间表。对开源维护者和企业安全团队来说，文章的核心含义是：更多长期未被发现的缺陷会被提前暴露，修复压力也会随之上升。

hackernews · pseudolus · 11月4日 11:52 · [社区讨论](https://news.ycombinator.com/item?id=50364336)

**「背景：PHP2Shell 漏洞」** 这篇分析以一个具体的近期事件为切入点：据 Atlas News 概述，在 2026 年 10 月下旬集中曝光的一批安全事件中，影响最大的是被称作 PHP2Shell 的漏洞，它波及运行 WordPress、Drupal 等基于 PHP 的系统的网站——包括 NASA、维基百科和白宫的站点——攻击者可借此读取敏感数据并在主机服务器上执行恶意代码。IEEE Spectrum 于 2026 年 11 月 2 日刊出 Dina Genkina 的这篇评论，把该事件当作 AI 辅助漏洞挖掘时代的样本，用来讨论行业如何面对长期积累下来的安全欠账。

**「影响」** 直接影响落在开源维护者和依赖这些项目的组织身上：他们需要面对更多漏洞报告的分诊与修复工作。HN 评论指出，其中不少问题无法靠窄补丁解决，可能需要重构，这会进一步挤占功能开发和安全维护资源。

**「社区讨论」** HN 讨论的核心分歧在于，AI 审计究竟是在“偿还”技术债，还是开启一条强制性的、与功能无关的修修补补跑步机；有评论者认为许多缺陷需要重构而非小补丁。另有评论者称，自己此前因指出开源软件存在“总会有人审计”的安全错觉而被踩，并认为 AI 审计可能让外部审查的承诺变得更实际。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability">PHP2Shell Is a Wakeup Call for AI in Cybersecurity - IEEE ...</a></li>
<li><a href="https://www.atlasnews.ai/articles/technology/the-php2shell-vulnerability-heralds-cybersecurity-hell">The PHP2Shell Vulnerability Heralds Cybersecurity Hell</a></li>

</ul>
</details>

**标签**: `#ai-security`, `#vulnerability-discovery`, `#open-source`, `#technical-debt`, `#cybersecurity`

---

<a id="item-tech-news-7"></a>
### [AMD 预计 Q4 营收将首次超过英特尔](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

对关注 CPU 与 AI 加速器市场的客户和投资者而言，AMD 预计第四季度营收将首次超过英特尔，其约 170 亿美元的季度指引高于英特尔同期的预测。该判断来自公司的销售指引，而不是已确认的出货量或财报结果；若指引兑现，将改变两家在 CPU 与 AI 加速器市场的相对销售规模。

hackernews · rbanffy · 11月4日 15:38 · [社区讨论](https://news.ycombinator.com/item?id=50367125)

**「背景」** 标题中的“outsell”对应的是公司季度营收，而不是 CPU 出货量或整体处理器市场份额；按报道所述，AMD 此前从未在单季营收上超过 Intel。两家公司目前给出的都是 Q4 指引，AMD 约为 170 亿美元（±3%），Intel 为 150 亿至 160 亿美元，因此这一判断仍属预测，需待正式财报确认。

**「社区讨论」** 评论者多把 AMD 的潜在反超归因于英特尔自身的执行问题，而非 AMD 已全面领先：有人提到 13/14 代酷睿电压故障和对 Optane 的放弃，也有人指出 AMD 的增长由 Instinct 带动、但其加速器销量仍远不及 Nvidia，而英特尔 Arc 加速器几乎无人采购。另有用户称因英特尔 DCI 而回避其产品，这属于个人安全经验，不是市场份额数据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections">AMD expects to outsell Intel in Q4 for the first time in ...</a></li>
<li><a href="https://wccftech.com/amd-is-set-to-out-earn-intel-for-the-first-time-in-its-history-guiding-to-17-billion-in-q4-revenue-against-intels-15-5-billion-midpoint-projection/">AMD Is Set To Out-Earn Intel For The First Time In Its ...</a></li>
<li><a href="https://latestintech.com/amd-q4-revenue-guidance-beats-intel/">AMD Q4 Revenue Guidance Signals Major Intel Upset</a></li>

</ul>
</details>

**标签**: `#AMD`, `#Intel`, `#CPU market`, `#semiconductor industry`, `#AI accelerators`

---

<a id="item-tech-news-8"></a>
### [腾讯 Hy4 开放权重发布，含科研与游戏适配](https://hy.tencent.ai/research/hy4) ⭐️ 7.0/10

腾讯发布了开放权重模型 Hy4，并称与 Hyra 2.0 共同开源了两个科学基础模型：用于单细胞表征的 HyCell 和用于物理场建模的 HyPDE。针对游戏开发，腾讯表示与 IEG 专业开发者合作整理训练数据和评测，并将 Hy4 适配 Unreal Engine、Unity 和 Godot，扩展至多人游戏开发。腾讯同时承认，Hy4 在研究级数学、长时程编码、模型自我改进和高级视觉问答等内部基准上，与顶级闭源模型仍有明显差距，计划继续扩大预训练和后训练规模。腾讯给出的能力与竞品差距描述尚未获得全面独立验证。

hackernews · Philpax · 11月4日 14:11 · [社区讨论](https://news.ycombinator.com/item?id=50365780)

**「背景」** Hy4 属于开放权重模型，权重文件是否可下载直接决定社区能否复现、微调和本地部署；腾讯在发布公告中称，模型权重和系统卡将在未来几天内发布，而非随发布即时上线。第三方汇总给出的规格是 770B MoE、1M 上下文，并支持视觉与电脑操作，但在权重公开前这些参数仍缺乏独立验证。

**「对游戏开发团队的影响」** 使用 Unreal Engine、Unity 或 Godot 的团队将获得针对功能实现、玩法逻辑、状态跟踪和资产管线调优的模型支持，但 Tencent 公布的游戏开发提升（GameDev 19.1%、GameLogic 9.8%）是相对 Hy4 preview 的内部基准结果，并非绝对性能或独立验证。Tencent 表示模型权重和系统卡将在“未来几天”发布，因此开发者目前还不能下载部署，务实做法是等权重发布后用自有代码库复测，再决定是否接入生产流程。

**「社区讨论」** 有评论者认为，HyCell 与 HyPDE 的开源与部分美国初创公司限制研究用途的做法形成鲜明对比；另一位评论者引用 Plotly 的数据分析基准称，Hy4 位于 GPT-6.1 Sol 与 GPT-6.1 Terra 之间的成本/准确率前沿，但处理每个问题耗时很长、整体偏慢。这些均为社区评价，不能替代全面独立评测。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy4, Joining the Ranks of the World&#x27;s ...</a></li>
<li><a href="https://explainx.ai/blog/tencent-hy4-official-release-770b-vision-computer-use-terminal-bench-44-4-weights-planned-2026">Tencent Hy4 Release: 770B, Computer Use, 12 Benchmarks ...</a></li>
<li><a href="https://hy.tencent.ai/research/hy4">Tencent Hy</a></li>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy4, Joining the Ranks of the World&#x27;s ...</a></li>
<li><a href="https://www.siliconreport.com/tencent-introduces-hy4-foundation-model-with-computer-use-features">Tencent introduces Hy4 foundation model with computer-use ...</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#LLM release`, `#game development`, `#scientific machine learning`, `#Tencent Hy4`

---

<a id="item-tech-news-9"></a>
### [在 B200 上实测 Huginn 循环 Transformer：权重共享未必减少 HBM 读取](https://www.reddit.com/r/MachineLearning/comments/1xnskvt/do_looped_transformers_save_hbm_traffic_profiling/) ⭐️ 7.0/10

一篇技术博客用 Nsight Compute 在单张 B200 上剖析了 Huginn 式循环 Transformer 的权重复用效果：共享权重能节省存储，但只有权重能驻留在缓存中时才会减少 HBM 读取。在微基准中，8 个矩阵乘法共用一份 72 MiB 权重，比使用 8 份相同副本快 24%，且几乎不从 HBM 读取数据；但当权重增至 288 MiB、超出 L2 容量后，这一差距消失。完整 Huginn Core（教学实现、随机权重）运行 8 次迭代，耗时约为单次迭代的 8 倍，从 HBM 读取的数据量也约为 8 倍。作者据此指出，权重共享本身并不能阻止 GPU 在每次迭代时重新从 HBM 加载权重，并询问是否有人尝试用 persistent kernel 等方式让循环权重常驻片上。该结论来自单卡、教学规模实现的初步测量，并非生产级分析。

reddit · r/MachineLearning · /u/2dayyy6 · 11月4日 16:26

**「背景」** Looped（循环）Transformer 会让同一组 Transformer 权重在多个迭代中反复复用，Huginn 是这类架构的一个实例；这种做法能减少需要保存的参数量。GPU 执行矩阵乘法时仍要从内存层级读取权重，只有权重能留在 L2 等片上缓存中，跨迭代复用才可能同时减少 HBM 读取。

**「影响」** 对设计循环深度或权重共享架构的开发者而言，这项测量意味着参数量下降不等于带宽开销下降：在权重超出 L2 的情况下，HBM 流量仍会随迭代次数线性增长，因此需要把循环权重控制在缓存容量内，或改用 persistent kernel 等常驻片上的执行方式，才能兑现共享权重带来的带宽收益。

**标签**: `#looped transformers`, `#HBM bandwidth`, `#GPU profiling`, `#memory hierarchy`, `#Huginn`

---

<a id="item-tech-news-10"></a>
### [甲骨文据报取消腾讯 70 亿美元 AI 芯片租赁](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 7.0/10

据相关报道，甲骨文取消了与腾讯价值约 70 亿美元的 AI 芯片租赁协议；此前美国官员曾向甲骨文表达对该交易的担忧，甲骨文随后面临特朗普政府压力。该五年期协议原计划让腾讯通过甲骨文在东南亚的多个数据中心租用约 10 万枚先进 AI 芯片，首付款约占 30%。目前材料来自二手聚合报道，甲骨文和腾讯均未在其中确认上述取消。

telegram · zaihuapd · 11月4日 11:01

**「背景」** 美国对华先进 AI 芯片出口限制，使中国企业难以在本土获得这类算力，经由第三国数据中心租用芯片因此成为一种替代路径。腾讯与甲骨文的五年期安排正属于这种结构：腾讯计划通过甲骨文在东南亚的数据中心使用约 10 万枚在中国无法获得的先进 AI 芯片。该报道称，美国官员随后就这笔交易向甲骨文表达了担忧。

**「直接影响」** 若取消属实，腾讯通过甲骨文东南亚数据中心获取先进 AI 芯片的五年安排将无法按原计划执行，原定约 10 万枚芯片的租赁规模也将受到影响；这直接涉及腾讯在中国境内无法使用的芯片供应路径。

**标签**: `#AI chips`, `#export controls`, `#Oracle`, `#Tencent`, `#data centers`

---

<a id="item-tech-news-11"></a>
### [华为据报要求客户自购升腾 960DT 所需 HBM](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

据 The Information 报道，华为已告知部分客户，下一代旗舰 AI 芯片升腾 960DT 将主要使用三星和 SK 海力士的 HBM，并要求客户自行解决内存来源，原因是中国厂商的 HBM 产能不足。报道还称，相关 HBM 被焊在性能很弱的处理器上，按处理器编码报关运至香港，再由人携带入内地并加热拆下；一名深圳芯片经纪人称，单颗 HBM3E 价格已从一年前的数百美元涨到约 4000 美元。

telegram · zaihuapd · 11月4日 14:52

**「国产 HBM 良率与既往依赖」** 华为上一代升腾 910C 已被拆解发现使用三星和 SK 海力士的 HBM，说明对外部内存的依赖并非始于 960DT。据 TrendForce 援引路透社报道，国产厂商长鑫存储（CXMT）的 HBM3E 良率仅为 20%–30%，而 SK 海力士约为 70%，这为华为要求客户自行解决内存来源提供了直接解释。

**「采购与合规负担」** 计划采用升腾 960DT 的客户将面临一项额外负担：按报道，他们需自行解决三星、SK 海力士 HBM 的采购；在国产 HBM 产能不足、且货源被指经香港转运入境的情况下，这会把出口管制与来源合规风险直接转嫁给采购方，并使部署成本受单颗 HBM3E 约 4000 美元现货价的牵制。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server Packages...</a></li>
<li><a href="https://www.techradar.com/pro/smugglers-are-reportedly-soldering-top-tier-hbm-onto-deliberately-useless-processors-to-sneak-it-into-china-and-the-trick-isnt-new">Smugglers are reportedly soldering top-tier HBM onto... | TechRadar</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server...</a></li>

</ul>
</details>

**标签**: `#Huawei Ascend`, `#HBM supply chain`, `#AI chips`, `#export controls`, `#semiconductor smuggling`

---

<a id="item-tech-news-12"></a>
### [蓝牙 HDT 标准获采纳：LE 峰值速率升至 7.5 Mbps](https://www.bluetooth.com/press/bluetooth-high-data-throughput-opens-a-new-chapter-in-wireless-performance/) ⭐️ 7.0/10

蓝牙技术联盟（SIG）于 11 月 4 日宣布采纳 Bluetooth HDT（High Data Throughput），将蓝牙 LE 的最高速率从 2 Mbps 提升至 7.5 Mbps，并改善容量、能效和可靠性。HDT 是蓝牙 Core 7.0 的可选特性，可与旧设备兼容共存。首个标准化应用面向高端无线音频，支持无损与高解析度音频，预计 2027 年推出。

telegram · zaihuapd · 11月5日 01:39

**「背景」** 在 HDT 之前，蓝牙 LE 的最高速率为 2 Mbps。HDT 被定义为蓝牙 Core 7.0 的可选特性，将峰值速率提升至 7.5 Mbps，并可与此前的蓝牙设备兼容共存。

**「影响」** 设备厂商只有在终端主动实现 HDT 这一可选特性时才能获得更高吞吐，旧设备不会自动提速，只能以原有速率共存；因此无损音频等收益要等支持 HDT 的产品上市，首批标准化音频应用预计在 2027 年。

**标签**: `#Bluetooth`, `#wireless standards`, `#audio`, `#hardware`, `#protocols`

---