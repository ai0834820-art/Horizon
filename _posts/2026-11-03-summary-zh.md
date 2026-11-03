---
layout: default
title: "Horizon Summary: 2026-11-03 (ZH)"
date: 2026-11-03
lang: zh
---

> 从 46 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [Qwen 3.8 27B 在笔记本上复现权重解读](#item-tech-news-1) ⭐️ 9.0/10
2. [Postman 被指静默安装 AI 插件并尝试共享 API 数据](#item-tech-news-2) ⭐️ 7.0/10
3. [现代象棋引擎在 1996 年奔腾硬件上能击败卡斯帕罗夫吗？](#item-tech-news-3) ⭐️ 7.0/10
4. [大规模运行 macOS 基础设施的运维挑战](#item-tech-news-4) ⭐️ 7.0/10
5. [Colsto 用飞机噪声与 ADS-B 数据定位视频地点](#item-tech-news-5) ⭐️ 7.0/10
6. [DeepSeek V5 据称计划用升腾芯片预训练](#item-tech-news-6) ⭐️ 7.0/10
7. [纽约时报起诉 Brave 转售抓取内容](#item-tech-news-7) ⭐️ 7.0/10
8. [传英伟达要求全球数据中心中企业务占比不超 49%](#item-tech-news-8) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Qwen 3.8 27B 在笔记本上复现权重解读](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) ⭐️ 9.0/10

一篇名为《Sparks of Weight-Space Programming》的论文声称，前沿模型（尤其是 GPT-6 Astra）无需运行代码或工具，就能从原始浮点权重判断网络训练目标，并直接改写权重；论文还称，Astra 仅修改 Qwen3.5-0.8B 的 0.016% 权重，就将其 MATH-500 从 7.9% 提升到 48.1%，IFEval 提升 3 倍。Simon Willison 用论文公开的“只看权重猜游戏”提示做了本地复现：17GB 的 Qwen 3.8 27B（Q4\_K\_M，经 LM Studio 加载并调大默认 8192 上下文）在 46 分 12 秒、43,506 个推理 token 后以 72% 置信度识别出 Pac-Man，又在 1 小时 4 分 54 秒内识别出 Pong；Kimi K3.1 Pro 经 OpenRouter 在 9 分 41 秒内识别出 Breakout。需要注意，这些是论文作者与博客作者的报告，并非独立验证；Matthew Honnibal 批评论文把“无工具读权重”和“借助代码改模型”混为一谈，Sean Goedecke 则认为 Qwen3.5-0.8B 的改进例子走的仍是人类研究者会用的步骤。

rss · Simon Willison · 11月3日 16:29

**「背景」** 这篇论文由 Rikiya Takehi、Jayden Teoh、Alex Zhang 和 Omar Khattab 于 2026 年 11 月发布，其核心实验之一，是把四个用强化学习训练、分别玩 10×10 网格简化游戏的策略网络的权重，直接以浮点数文本形式交给模型，并要求模型在不执行代码、不使用任何工具的前提下判断这些权重属于哪个游戏。据作者本人和 The Register 的报道，这四个游戏的输入通道与动作空间完全相同，模型唯一能依靠的线索就是权重本身；论文所用的提示词和权重文件已公开在 RikiyaT/lm\_understand-logs 仓库，因此任何人都能用本地模型复现同一道题。

**「本地复现门槛」** 对想在本地复现这一实验的开发者来说，直接的约束是上下文与等待时间：Simon Willison 使用 17GB 的 Qwen 3.8 27B（Q4\_K\_M GGUF）时，LM Studio 默认 8192 上下文会报错，必须调大上下文窗口，并把超时提高到 900 秒；Pac-Man 提示词耗时 46 分 12 秒、消耗 43,506 个推理 token，Pong 则耗时 1 小时 4 分 54 秒。同时，该论文关于“无梯度直接改权重提升数学能力”的更强主张已受到 Matthew Honnibal 与 Sean Goedecke 的质疑，认为其混合了“不借助工具”与“借助代码执行”两类能力，因此在把这种方法当作无需梯度的模型改进手段之前，应先区分单次纯推理与工具辅助流程。

**「社区讨论」** 在 Hacker News 讨论中，从事机制可解释性研究的 x313 认为原论文确有夸大：所谓让 Qwen 更会数学，主要是降低了推理循环，而这类循环可用简单的 steering 向量缓解；neom 则称 Astra 改写 Qwen 权重更像已有技术的重新包装，并链接了相关论文。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://rikiyat.github.io/">Rikiya Takehi</a></li>
<li><a href="https://www.startuphub.ai/ai-news/ai-research/2026/llms-can-now-read-and-rewrite-weights-directly">LLMs Can Now Read and Rewrite Weights Directly | StartupHub.ai</a></li>

</ul>
</details>

**标签**: `#weight-space programming`, `#LLM interpretability`, `#model weights`, `#local LLMs`, `#Qwen`

---

<a id="item-tech-news-2"></a>
### [Postman 被指静默安装 AI 插件并尝试共享 API 数据](https://github.com/postmanlabs/postman-app-support/issues/14370) ⭐️ 7.0/10

GitHub 上 postman-app-support 仓库的第 14370 号 issue 指控 Postman 静默自动安装 AI 插件，并尝试共享用户的 API 数据。该报告目前仅是单一 issue 中的指控，所提供材料未包含 Postman 的回应或独立验证，因此应视为待核实的问题，而非已确认的事实。讨论主要面向使用 Postman 处理 API 请求与凭证的开发者，焦点是隐私、客户端臃肿以及是否迁移到其他工具。

hackernews · sidgarimella · 11月3日 17:22 · [社区讨论](https://news.ycombinator.com/item?id=50354960)

**「背景」** Postman 是用于调试和共享 API 请求的客户端；公开报道显示，其曾完成 2.25 亿美元融资，估值达 56 亿美元，产品也已从单机工具扩展为包含账户和云协作的商业平台。API 客户端通常会保存请求内容、环境变量和认证令牌，因此插件自动安装或数据外发行为会直接触及开发者对本地凭据和 API 流量的控制边界。

**「对使用者的影响」** 对处理敏感 API 密钥或生产数据的开发者而言，这一指控意味着需要在升级或继续使用前检查已安装的插件与数据共享设置；若无法接受默认行为，可评估支持本地存储和 Git 管理的替代客户端。

**「社区讨论」** 评论者表达了对 Postman 体积和速度的不满，有人称已迁移到 Bruno，并看重其能把请求定义存入 Git；也有人推荐 JetBrains IDE 内置的 REST 客户端或离线优先的 Kreya。这些是个人使用经验与偏好，不构成对上述指控的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.financialexpress.com/business/industry-225-million-fundraise-postman-valuation-hits-5-6-billion-2313442/">$225-million fundraise: Postman valuation ... | The Financial Express</a></li>

</ul>
</details>

**标签**: `#privacy`, `#security`, `#developer-tools`, `#api-testing`, `#open-source-alternatives`

---

<a id="item-tech-news-3"></a>
### [现代象棋引擎在 1996 年奔腾硬件上能击败卡斯帕罗夫吗？](https://nicholas.carlini.com/writing/2026/algorithmic-improvements-chess.html) ⭐️ 7.0/10

这篇文章探讨一个反事实问题：把现代象棋引擎的算法放到 1996 年奔腾时代的硬件上，是否足以击败卡斯帕罗夫。讨论涉及搜索算法、NNUE 以及当时硬件和工程条件的历史可行性，属于分析性推演，并非产品发布或赛事结果。由于没有提供正文，文章的具体实验设置和结论无法核实。

hackernews · markusw · 11月3日 07:56 · [社区讨论](https://news.ycombinator.com/item?id=50349276)

**「背景」** 这篇文章讨论的是一个反事实问题：如果把现代国际象棋引擎的算法放到 1996 年的 Pentium 级别硬件上运行，能否战胜卡斯帕罗夫。真实历史中，1996 年卡斯帕罗夫在费城与 IBM 的深蓝超级计算机进行了六局比赛，并以 4 比 2 获胜；不过深蓝赢下了第一局，成为计算机首次在标准赛事条件下击败在位世界冠军。

**「影响」** 对想在复古硬件上复现现代棋力的开发者来说，评论指出的关键限制是 NNUE 依赖海量训练数据和可蒸馏的现代教师模型；仅把搜索算法移植到奔腾级 CPU 并不够。

**「社区讨论」** 评论中，FartyMcFarter 不同意文中“特级大师与业余棋手分析的变化数量大致相同”的说法，称从棋手直播可见其会考虑更多分支且算得更深；rockmeamedee 则强调现代引擎棋力很大程度来自 NNUE，而 1990 年代的程序员即使拿到技术蓝图，也缺少用于蒸馏的教师模型。Sharlin 还纠正了对 Pentium Pro 与 Pentium MMX 的类比，指出 Pro 是全新的 P6 乱序架构，MMX 只是增强的 P5。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov">Deep Blue versus Garry Kasparov - Wikipedia</a></li>
<li><a href="https://en.wikipedia.org/wiki/Deep_Blue_versus_Kasparov,_1996,_Game_1">Deep Blue versus Kasparov, 1996, Game 1 - Wikipedia</a></li>

</ul>
</details>

**标签**: `#chess engines`, `#algorithmic progress`, `#retrocomputing`, `#performance`, `#NNUE`

---

<a id="item-tech-news-4"></a>
### [大规模运行 macOS 基础设施的运维挑战](https://namespace.so/blog/mac-at-any-scale) ⭐️ 7.0/10

namespace.so 的技术文章《Mac at Any Scale》梳理了大规模运行 macOS 基础设施的运维难题与变通方案，目标读者是需要 macOS CI 和自动化能力的基础设施与开发团队。文章的核心并不是发布新版本或新产品，而是 Apple 生态在 CI、自动化与数据中心运营上的限制，以及团队为绕开这些限制所付出的工程成本。

hackernews · anner\_ · 11月3日 14:53 · [社区讨论](https://news.ycombinator.com/item?id=50352758)

**「背景」** macOS 的虚拟化同时受技术限制和许可条款约束：Apple 的 Virtualization Framework 允许每台 Mac 同时最多运行两个 macOS 客户机，而 Apple 的软件许可协议还规定 macOS 只能在 Apple 品牌硬件上虚拟化。这两项限制使得需要大规模 macOS 构建与测试环境的团队无法靠普通虚拟机集群扩容，只能转向物理 Mac 机架或第三方托管服务。

**「影响」** 对自建 macOS CI 的团队来说，这类限制意味着预算不能只按 Mac mini 等单机价格计算，还要计入围绕 Apple 工具链开展自动化、维护和绕行所花费的成本；HN 评论中关于“租 Mac 还是买 Mac”的争论也说明，应按使用周期评估总成本。

**「社区讨论」** HN 评论多数批评 Apple 的自动化与 CI 工具不足，认为团队大量精力花在绕过 Apple 自身的 bug 和限制上；也有评论主张 Apple 改进 Xcode Cloud、提供更多 Mac mini 或专用服务器硬件，或放宽虚拟机数量限制。另有评论从成本角度质疑租赁 Mac 的必要性，指出 Mac mini 安静省电，长期自购可能更划算。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://juergenkoller.software/en/blog/more-than-two-macos-vms-on-apple-silicon.html">Running More Than Two macOS VMs on Apple Silicon | Juergen Koller</a></li>
<li><a href="https://virtualizationreview.com/articles/2025/04/28/hands-on-with-macstadium-remote-desktop.aspx">Hands On with MacStadium Remote Desktop -- Virtualization Review</a></li>

</ul>
</details>

**标签**: `#macOS infrastructure`, `#CI/CD`, `#Apple ecosystem`, `#developer tooling`, `#scaling`

---

<a id="item-tech-news-5"></a>
### [Colsto 用飞机噪声与 ADS-B 数据定位视频地点](https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/) ⭐️ 7.0/10

Simon Willison 在一则短链文章中介绍了 Colsto 的 OSINT 演示：从视频音轨中提取几乎不可察觉的飞机噪声，计算其多普勒曲线，再与 ADS-B 航班数据交叉比对。该方法利用航速、距离和不同航班之间的间隔，推断视频的精确拍摄位置。该演示涉及公开视频的音频可能泄露位置信息的隐私风险。

rss · Simon Willison · 11月3日 05:32

**「背景」** 这项技术建立在两个早已公开的基础之上。其一是 ADS-B：现代客机通过应答机持续广播航班号、位置、高度与速度，地面接收站汇总这些信号后在 Flightradar24 一类网站上免费公开，任何人都能回查某个时间、某个空域有哪些航班经过。其二是多普勒效应：飞机高速掠过时，引擎声的音高会随接近与远离连续变化，把视频音轨转成频谱图就能读出这条曲线；Colsto 的演示用频谱图测出的速度与最近点斜距（CPA slant distance）约束候选航班，再用两次飞越之间 920 秒的间隔和一段静音作为额外条件筛出唯一解。

**「影响」** 对公开发布视频的人来说，背景中的飞机声可能成为位置信息来源；若不想暴露拍摄地点，可考虑在上传前处理或移除这类音频。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=UytYrhYLOKI">I discovered a sound that leaks your exact location ... - YouTube</a></li>

</ul>
</details>

**标签**: `#OSINT`, `#privacy`, `#geolocation`, `#signal-processing`, `#ADS-B`

---

<a id="item-tech-news-6"></a>
### [DeepSeek V5 据称计划用升腾芯片预训练](https://www.reddit.com/r/LocalLLaMA/comments/1xmmadn/deepseek_v5_is_planned_to_be_pretrained_on_huawei/) ⭐️ 7.0/10

据《科创板日报》援引多位供应链人士，DeepSeek 下一代大模型 V5 计划使用华为升腾芯片进行预训练；该消息尚未获得 DeepSeek 或华为官方确认，也未披露芯片型号、集群规模和时间表。此前升腾主要承担 DeepSeek 模型的推理任务：2025 年春节，华为与 DeepSeek 在华为云贵安数据中心部署并验证了 3000 多颗升腾芯片来承载 V3/R1；2026 年 4 月 V4 发布后，华为称全系升腾超节点产品可支持 V4 系列。DeepSeek 还在 9 月 30 日开源了适配升腾的 TileLang、DeepGEMM、FlashMLA、DeepEP 等基础设施组件；但近期基于升腾 910C 的 1.6 万亿参数 V4-Pro 只完成了全参数后训练，未包含预训练阶段。若 V5 确实在升腾上预训练，这将首次检验中国顶级大模型能否用国产算力完成预训练；目前这仍只是计划传闻，训练生态迁移成本也是关键变量。

reddit · r/LocalLLaMA · /u/hedgehog0 · 11月3日 07:07

**「背景」** 此前华为 Ascend 芯片主要用于推理：2025 年春节前后，华为与 DeepSeek 在贵安数据中心完成 3000 多颗 Ascend 芯片的部署验证，并承载 DeepSeek-V3/R1 模型。2026 年 4 月 DeepSeek-V4 发布后，华为称其 Ascend 超节点产品可全面支持 V4 系列；同年 9 月，DeepSeek 又开源了面向 Ascend 平台的 TileLang、DeepGEMM、FlashMLA、DeepEP 等基础设施组件。不过，国内算力部署仍以推理为主，近期基于 Ascend 910C 的集群只完成了 1.6 万亿参数 DeepSeek-V4-Pro 的全参数后训练，并未包含预训练阶段。

**「对开发者的实际影响」** 若该计划属实，直接影响是训练侧的软件栈选择：DeepSeek 已在 9 月 30 日开源面向升腾平台的 TileLang 编译工具、DeepGEMM、FlashMLA、TileKernel、DeepSelect 及通信库 DeepEP，并配合华为的 Ascend C 接口与底层指令集，开发者适配的对象将从 CUDA 转向 CANN 一系工具链。报道同时提示迁移成本仍是关键变量——目前国内算力部署主要集中在推理，升腾 910C 集群仅完成过 DeepSeek-V4-Pro 的 1.6 万亿参数全参数后训练（不含预训练），且 V5 预训练使用升腾一事尚未获得 DeepSeek 或华为官方确认。

**标签**: `#DeepSeek`, `#Huawei Ascend`, `#AI hardware`, `#LLM pretraining`, `#China AI`

---

<a id="item-tech-news-7"></a>
### [纽约时报起诉 Brave 转售抓取内容](https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/) ⭐️ 7.0/10

纽约时报周一起诉隐私浏览器 Brave，指控其抓取受版权保护的内容并出售给 Anthropic、Perplexity、Mistral、xAI、Cohere 等 AI 公司，并寻求禁令和赔偿。同日在曼哈顿联邦法院，纽约每日新闻、芝加哥论坛报等也提起类似诉讼。诉状称 Brave 使用未披露的爬虫建立超过 300 亿网页的索引，还绕过付费墙、屏蔽出版商广告；这些均为原告指控，Brave 暂未回应。

telegram · zaihuapd · 11月3日 06:50

**「背景」** 这起诉讼的核心争议在于，浏览器或搜索服务商能否将抓取到的网页内容转售给 AI 公司。诉状称，Brave 通过未披露的爬虫建立了超过 300 亿网页的索引，还绕过出版商的付费墙并屏蔽其广告，因此案件同时涉及版权、内容访问控制和广告收入。

**「潜在影响」** 原告寻求禁令和赔偿，若诉求获法院支持，Brave 将面临停止相关抓取或调整向 AI 公司提供内容方式的直接约束；目前尚未有司法认定。

**标签**: `#AI版权`, `#网页抓取`, `#Brave浏览器`, `#AI数据来源`, `#媒体诉讼`

---

<a id="item-tech-news-8"></a>
### [传英伟达要求全球数据中心中企业务占比不超 49%](https://www.tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims-allegedly-restricted-to-49-percent-of-the-total-ensuring-51-percent-are-non-chinese-outfits) ⭐️ 7.0/10

据《金融时报》报道，英伟达已要求全球数据中心运营商把来自中国企业的业务占比限制在 49%以内，以确保至少 51%的业务来自非中国企业。该要求仅针对新签和未来合同，不影响已签订的租赁协议；报道称规定由销售团队和区域团队口头传达，未见正式文件。英伟达表示，美国芯片是美国模型与应用厂商参与全球竞争的基础，现行美国政策鼓励云服务商基于美国基础设施接受各地业务。

telegram · zaihuapd · 11月3日 16:19

**「背景」** 这一说法最早来自《金融时报》基于匿名消息人士的报道，彭博社随后援引同一报道跟进，英伟达并未发布正式文件（tool-2-1、tool-2-3）。英伟达的芯片大量经由数据中心运营商和云服务商以算力形式对外提供，因此按客户来源限制这类运营商来自中国企业的业务占比，等于把约束对象从直接采购芯片的客户扩展到转售算力的下游环节。

**「影响」** 对拥有中国客户的数据中心运营商而言，新签合同的中国业务占比需控制在 49%以内，现有租赁协议不受影响，因此需要调整未来的客户结构；但该要求尚未见正式文件，具体执行范围和力度仍不明确。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.ft.com/content/1902df70-1380-4588-bad5-171352b575f2?syn-25a6b1a6=1">Nvidia orders data centre clients to reduce China exposure</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-03/nvidia-tells-data-center-clients-to-trim-china-business-ft-says">Nvidia Tells Data Center Clients to Trim China Business, FT ...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#data centers`, `#China`, `#export controls`, `#AI infrastructure`

---