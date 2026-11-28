---
layout: default
title: "Horizon Summary: 2026-11-28 (ZH)"
date: 2026-11-28
lang: zh
---

> 从 29 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [OpenSec 披露 nfsd 9.8 分预认证漏洞，可远程获取 root](#item-tech-news-1) ⭐️ 8.0/10
2. [Google DeepCrossAttention 宣称同等质量下最高快 3 倍](#item-tech-news-2) ⭐️ 7.0/10
3. [黑五购物网站出现 WebRTC 信用卡盗刷脚本](#item-tech-news-3) ⭐️ 7.0/10
4. [Convex 技能被指未经告知上传用户应用创意](#item-tech-news-4) ⭐️ 7.0/10
5. [州总检察长起诉 SpaceX，指 Grok 生成儿童性虐待及非自愿图像](#item-tech-news-5) ⭐️ 7.0/10
6. [计算机检查的证明为何仍可能为假](#item-tech-news-6) ⭐️ 7.0/10
7. [SemiAnalysis 深度分析 Trainium3 推理性价比与微架构](#item-tech-news-7) ⭐️ 7.0/10
8. [《我的世界》基岩版资源包漏洞影响 26.52–26.63，26.65 修复](#item-tech-news-8) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenSec 披露 nfsd 9.8 分预认证漏洞，可远程获取 root](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

据 OpenSec 披露，Linux 内核 NFS 服务器组件 nfsd 存在预认证堆溢出漏洞 CVE-2026-99362，CVSS 评分为 9.8：攻击者无需登录，只需向 tcp/2049 发起连接，就能越界写入内核堆并获取 root shell。该漏洞自 Linux 3.16（2014 年）起存在，影响启用 NFSv4.1 或 4.2 的文件服务器、NAS 和集群存储节点。修复版本为 6.12.117、6.18.61、7.3.2 和 7.4-rc1，升级内核后需重启；无法立即升级的环境可通过防火墙限制 tcp/2049 访问。CVE 于 2026 年 11 月 20 日公开，但这些信息来自一条 Telegram 摘要，未包含原始安全公告或独立验证细节。

telegram · zaihuapd · 11月27日 12:57

**「背景：nfsd 的会话回复缓存」** nfsd 是 Linux 内核内置的 NFS 服务器。NFSv4.1/4.2 引入会话机制后，服务器会为每个会话维护回复缓存，以保证请求重发的 exactly-once 语义；据 Red Hat 的漏洞记录，本次问题正是客户端先协商一个极小的缓存回复尺寸，再发送带 SEQUENCE 操作的构造复合请求，使服务器把完整回复写入过小的缓冲区，而且这条路径在任何身份验证之前就能触达。评分方面，内核 CNA 给出 9.8，Red Hat 自己的评估为 9.4。

**「影响」** 使用发行版或 NAS 定制内核的运维者不能仅凭上游已发布 6.12.117、6.18.61、7.3.2 就认定设备已修复：工具结果显示 TrueNAS 25.10.8 的内核仍早于修复版本。应核对厂商内核是否包含补丁，否则需在边界限制 tcp/2049 访问，并尽快升级内核后重启。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99362">CVE-2026-99362 - Red Hat Customer Portal</a></li>
<li><a href="https://computingforgeeks.com/nfs2root-cve-2026-99362/">NFS2ROOT (CVE-2026-99362): Check, Patch, Mitigate ...</a></li>
<li>pre-auth remote root in the Linux NFS server. Ubuntu still vulnerable ...</li>

</ul>
</details>

**标签**: `#linux-kernel`, `#security-vulnerability`, `#nfs`, `#patching`, `#remote-exploit`

---

<a id="item-tech-news-2"></a>
### [Google DeepCrossAttention 宣称同等质量下最高快 3 倍](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research 在一篇博文中介绍了 DeepCrossAttention：这是一种针对 Transformer 残差连接的架构改动，声称在模型质量相当的情况下最高可快 3 倍。该结果目前来自 Google 自己的博客说明，尚没有独立复现或详细基准数据可供核验。对关心训练和推理效率的团队而言，这是一个值得测试的候选方案，但还不是已经证实的通用加速结论。

hackernews · ComputedCamp995 · 11月27日 23:06 · [社区讨论](https://news.ycombinator.com/item?id=50672565)

**「背景」** Transformer 长期依赖残差连接：把每一层的输出直接加到前一层的表示上，以帮助深层网络训练；但相关论文指出，这种简单相加会稀释关键信息。DeepCrossAttention（DCA）用依赖输入、跨深度的交叉注意力处理 Query、Key、Value，并通过可学习权重在层间路由信息，从而改进而非简单累加残差。Google Research 的博客以标准顺序残差连接为对照介绍了这一方法。

**「影响」** 如果这一加速能在自有工作负载上复现，团队可用它降低 Transformer 的训练或推理成本；但在缺少独立基准、消融实验和兼容性说明的情况下，生产系统应先做小规模对照测试，再决定是否替换现有残差连接方案。

**「社区讨论」** 评论中最具体的质疑针对图表形式：有读者认为不同方法之间没有时间关系，性能对比不应画成折线图，而应使用柱状图。另有评论者关心它能否在 MTP、Dflash 等已有提速手段之上继续把吞吐量推高，但这属于推测而非已验证结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections</a></li>
<li><a href="https://arxiv.org/html/2502.06785">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>
<li><a href="https://www.alphaxiv.org/overview/2502.06785v1">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>

</ul>
</details>

**标签**: `#transformers`, `#model architecture`, `#training efficiency`, `#Google Research`, `#ML systems`

---

<a id="item-tech-news-3"></a>
### [黑五购物网站出现 WebRTC 信用卡盗刷脚本](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

据 Infohawk 报道，热门购物网站上被发现使用 WebRTC 的信用卡盗刷脚本，报道将这一活动与黑色星期五购物季联系起来。报道称，这些脚本利用 WebRTC 规避检测，风险入口是电商网站嵌入的第三方脚本。现有材料没有给出受影响网站名单、脚本样本、拦截数量或独立验证结果，因此这应视为媒体报道，尚非经独立确认的规模事件。

hackernews · scanr · 11月27日 15:40 · [社区讨论](https://news.ycombinator.com/item?id=50668145)

**「背景」** WebRTC 是浏览器内置的实时通信接口，页面脚本可以借此建立点对点数据通道。电商结账页通常嵌入支付、分析或营销等第三方脚本，这些脚本一旦被篡改，就可能借页面权限发起额外的网络请求。

**「对消费者与电商运营方的影响」** 对消费者而言，报道点名 Lascana、Samsonite、American Tourister、Revolve 和 FWRD 等在线商店在黑色星期五前一周被植入盗刷脚本，凡在此期间结账并输入支付卡信息的用户都应把相关卡号视为可能已泄露；对电商运营方而言，这意味着结账页的第三方脚本清单和运行时行为——包括 WebRTC 这类较少被监控的通道——需要纳入支付数据安全审计。

**「社区讨论」** 评论中，afavour 认为问题不在 WebRTC 的技术能力本身，而在于它较少被监控，并称同样的手法也可用普通 HTTP 请求实现，嵌入第三方脚本的站点始终有风险；jszymborski 则把这类攻击视为拦截广告的正当理由之一。另有评论者主张浏览器不应允许第三方广告执行任意 JavaScript，或认为允许陌生代码在本地运行是 Web 的基础设计问题。

<details><summary>参考链接</summary>
<ul>
<li>Credit card skimming scripts using WebRTC found on ... - InfoHawk</li>

</ul>
</details>

**标签**: `#web security`, `#credit card skimming`, `#WebRTC`, `#third-party scripts`, `#e-commerce security`

---

<a id="item-tech-news-4"></a>
### [Convex 技能被指未经告知上传用户应用创意](https://github.com/convex/convex-backend-skill/issues/64) ⭐️ 7.0/10

GitHub issue \#64 指称，Convex 的 AI 技能会把用户的应用创意上传到远程服务器，却没有向用户作出清晰披露。Convex CEO Jamie 在讨论中确认，该插件中的提示词上传用于驱动 Convex 的“quickstart”功能，并称它是已关闭的端到端 vibe-coding 产品 Convex Chef 的延续。当前材料没有说明上传是否可关闭、数据保存多久或覆盖哪些内容，因此这仍是一起针对单一产品数据处理方式的披露争议。

hackernews · MickyTheMouse · 11月27日 18:02 · [社区讨论](https://news.ycombinator.com/item?id=50669765)

**「背景」** Convex 是一个提供数据存储、代码托管和 AI 网关的后端平台，其 AI「skills」由 SKILL.md 这类指令文件构成，供 AI 编码代理在项目中逐步执行。据该 issue 记录，/quickstart/ 技能的 SKILL.md 第 48–56 行会把用户的一句话项目构想 POST 到 basic-anteater-667.convex.site，并在注释中标注为 telemetry；而 /add/ 技能则从同一主机拉取脚本并直接通过管道交给 bash 执行。Convex CEO Jamie 在讨论中回应称，这一提示词上传是为「quickstart」功能提供支持，他称该功能是已关闭的端到端 vibe-coding 产品 Convex Chef 的「精神继任者」。

**「影响」** 对使用该技能的开发者而言，实际影响是应用创意可能随 quickstart 请求进入 Convex 的托管服务；在缺乏保存期限和关闭选项说明的情况下，处理敏感或未公开项目时应先确认技能会发送哪些内容，再决定是否启用。

**「社区讨论」** 评论中，Convex CEO 的说明把上传与 quickstart 功能直接关联起来；其他评论者则从信任、长期应转向自托管开放权重模型，以及提示注入比模型主动恶意调用工具更常见等角度展开讨论。上述均为参与者观点，不能替代对具体数据处理的独立核实，也不代表社区共识。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/convex/convex-backend-skill/issues/64">Quickstart skills send the user&#x27;s idea to a convex .site host and run...</a></li>

</ul>
</details>

**标签**: `#AI coding tools`, `#privacy`, `#data handling`, `#developer trust`, `#Convex`

---

<a id="item-tech-news-5"></a>
### [州总检察长起诉 SpaceX，指 Grok 生成儿童性虐待及非自愿图像](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

多个州的总检察长已对 SpaceX 提起诉讼，指控其子公司 xAI 和 X 旗下的 Grok 生成并推广儿童性虐待材料以及未经同意的私密图像。诉讼寻求法院制止相关行为；诉状中的指控尚未经法院认定，目前只是起诉阶段。诉状把 SpaceX 列为 X 和 xAI 的母公司，使争议从 Grok 的模型输出延伸到平台及母公司责任。

hackernews · DeepLogin · 11月27日 19:42 · [社区讨论](https://news.ycombinator.com/item?id=50670855)

**「背景」** SpaceX 是 X、xAI 及其 Grok 产品的母公司。据《纽约时报》报道，SpaceX 在 5 月的监管申报中曾将 Grok 生成性内容的能力列为对投资者的风险；这为本次诉讼以母公司身份追究 SpaceX 责任提供了背景。

**「影响」** 这起诉讼使 X 和 xAI 的图像生成与内容审核政策直接接受州检察长和法院审查。对使用 Grok 图像功能的用户而言，后续可能看到更严格的提示词过滤、输出拦截或地区性限制；但法院尚未裁决，材料也未显示已有产品变更。

**「社区讨论」** 评论区对责任归属存在分歧：有人质疑 Grok 为何能生成这类内容、是否容易被绕过限制，也有人把责任指向制作图像的用户。另有评论者声称美国最高法院已裁定个人使用 AI 制作儿童性虐待材料受言论自由保护，但该说法未在给定材料中得到证实，评论者本人也对非自愿图像部分表示不确定。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform">Attorneys General Jones and Rayfield File Suit Against SpaceX ...</a></li>
<li><a href="https://www.nytimes.com/2026/11/23/technology/spacex-lawsuit-ai-sexualized-images.html">SpaceX Sued By Oregon and Virginia Over A.I.-Generated ...</a></li>

</ul>
</details>

**标签**: `#AI safety`, `#generative AI`, `#content moderation`, `#legal/regulation`, `#xAI/Grok`

---

<a id="item-tech-news-6"></a>
### [计算机检查的证明为何仍可能为假](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

cr.yp.to 的文章《False computer-checked proofs》讨论一个信任问题：如果证明检查器本身存在 soundness（健全性）漏洞，那么计算机检查通过的证明仍可能是假的；文章面向形式验证、证明助手和软件正确性读者。现有材料没有提供文章正文，也没有给出新的漏洞、版本或独立实测结果；相关具体案例来自 Hacker News 评论，而非文章正文。

hackernews · \_tk\_ · 11月27日 15:26 · [社区讨论](https://news.ycombinator.com/item?id=50667989)

**「背景」** 证明助手（如 Lean、Coq、Metamath）通常把大量自动化推理与一个小的可信内核分开：内核会逐步复核由证明脚本生成的推导，因此整个检验结果的可信度最终取决于内核本身是否可靠。如果内核存在 soundness（可靠性）缺陷，它就可能接受本不合法的推导，而这与证明是如何产生的无关。据该文所述，检查器自身的正确性也早已成为被形式化验证的对象：2022 年曾有人用计算机检验了一个独立 HOL 证明检查器（OpenTheory 格式）的正确性。

**「实践影响」** 对依赖单一证明检查器的团队来说，影响很直接：Lean 内核出现过健全性 bug \#14576，独立的 Rust 检查器 nanoda 也出现过被报告并修复的 bug，因此“通过检查”不能等同于命题为真。可行的做法是用独立实现的检查器交叉验证 Lean 4 导出结果，并锁定检查器版本；Metamath 的 set.mm 和 iset.mm 则要求 5 个独立验证器全部通过后才接纳证明。

**「社区讨论」** Hacker News 评论者 twotwotwo 称，要误导数学家需在多个检查器上同时出现漏洞，并举出一个同时通过 Lean 和当时刚发布一周的 nanoda 版本的“证明”为例；dwheeler 补充说 Metamath 的 set.mm 和 iset.mm 要求 5 个独立验证器通过，因此认为文章的描述偏悲观。gr\_norm 则认为这些 soundness 漏洞少到几乎可以写进一条推文，对 99.9% 的软件已经足够；andai 还报告了另一类风险：自动代理可能证明的是它对需求的错误理解，而非实际需求。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cr.yp.to/proofs/falseccp.html">False computer - checked proofs (djb)</a></li>
<li><a href="https://lean-lang.org/doc/reference/latest/releases/v4.32.2/">Lean 4.32.2 (2026-07-28)</a></li>
<li><a href="https://leodemoura.github.io/blog/2026-8-1-postmortem-for-kernel-soundness-bug-14576/">Postmortem for Kernel Soundness Bug #14576 — Leonardo de Moura</a></li>
<li><a href="https://arena.lean-lang.org/checker/nanoda/">nanoda - Lean Kernel Arena</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#proof assistants`, `#soundness`, `#software correctness`, `#Lean`

---

<a id="item-tech-news-7"></a>
### [SemiAnalysis 深度分析 Trainium3 推理性价比与微架构](https://newsletter.semianalysis.com/p/trainium3-inferencex) ⭐️ 7.0/10

SemiAnalysis 于 11 月 27 日发布对 AWS Trainium3 的推理与微架构分析，称在 InferenceX/UBenchX 的智能体编码会话回放中，Trainium3 搭配 PDS 与 vLLM 在整条 TCO 对 p90 交互性曲线上，每美元推理性能优于除 Nvidia Vera Rubin 外的其他加速器。文章还称，Trainium 的 DGE（对标 Nvidia TMA）让其在较小消息尺寸下达到峰值 HBM 带宽利用率，而 Nvidia GPU 做不到。上述数字来自 SemiAnalysis 的基准与建模，并获 AWS 团队协助验证；由于提供的正文被截断，具体测试配置和完整结果无法从现有材料核实。

rss · Semianalysis · 11月27日 15:54

**「背景：Trainium2 与 tile-first 设计路线」** Trainium 是 AWS 自研的机器学习加速器系列，其前代 Trainium2 已用于 AWS 云上的训练与推理实例。2024 年 12 月，AWS 首席执行官 Matt Garman 曾表示，Trainium3 采用 3 纳米工艺，运算速度约为 Trainium2 的两倍，能效提高 40%；这是厂商说法，为理解本次微架构与推理成本分析提供了基线。与 Nvidia 从图形渲染 GPU 起步、逐代叠加 Tensor Core、TMA、Tensor Memory 等 AI 单元的路线不同，Trainium 从设计之初就把 tile 作为一等原语。

**「对选型的影响」** 若这些结果可复现，正在为大模型推理降本的团队可把 Trainium3 + vLLM/PDS 纳入选型，但应先按自身模型与延迟目标复测：文章的优势结论绑定于 TCO 假设和智能体编码负载，并非跨所有工作负载的保证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://technews.tw/2024/12/05/aws-trainium3-ai-chip-powered-by-3-nanometers/">3 奈米加持 AWS Trainium 3 AI... | TechNews 科技新报</a></li>

</ul>
</details>

**标签**: `#Trainium3`, `#AI accelerators`, `#inference`, `#microarchitecture`, `#AWS`

---

<a id="item-tech-news-8"></a>
### [《我的世界》基岩版资源包漏洞影响 26.52–26.63，26.65 修复](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

《我的世界》基岩版被曝存在资源包漏洞：带有 content.zipe 文件的资源包可修改 Ore UI 界面文件并运行隐藏脚本；8Crafter 于 11 月 15 日在 Reddit 公开该问题，称确认影响 26.52 至 26.63 版本，更早版本也可能受影响，Java 版不受影响。玩家加入服务器或 Realm 时若开启资源包自动下载，无需手动安装就可能收到问题文件；列出的利用方式包括删除全部存档、获取玩家 IP，以及在 Windows 特定条件下无提示打开任意 URI，或启动资源包内的批处理文件下载恶意软件。Mojang 已在 26.65 版修复；AxmBro 发布的 Windows 只读检测工具可查找 content.zipe，但不能判断资源包是否恶意。

telegram · zaihuapd · 11月27日 18:04

**「背景」** 在《我的世界》基岩版中，资源包可用来替换游戏资源与界面文件；本次问题涉及资源包内的 content.zipe 文件，它能改动界面框架 Ore UI 的文件并运行隐藏脚本。玩家加入服务器或 Realm 时，如果启用了资源包自动下载，问题资源包可能在无需手动安装的情况下进入设备，这是漏洞被利用的关键前提。

**「影响与应对」** 仍在 26.52 至 26.63 版本的玩家应尽快升级到 26.65；在升级前，加入陌生服务器或 Realm 时应关闭资源包自动下载，因为问题资源包可在无需手动安装的情况下被接收，Windows 用户还面临打开任意 URI 和下载恶意软件的风险。AxmBro 的检测工具只能发现 content.zipe 文件，不能判断资源包是否恶意，因此不能替代升级。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.techtimes.com/articles/330961/20261117/mojang-patches-bedrock-after-community-discovers-resource-packs-could-execute-malicious-code.htm">Mojang Patches Bedrock After Community Discovers Resource ...</a></li>
<li><a href="https://nqbrief.com/en/games/minecraft-bedrock-26-65-resource-pack-fix/">Minecraft Bedrock 26.65 released to fix resource-pack exploit</a></li>

</ul>
</details>

**标签**: `#Minecraft Bedrock`, `#security vulnerability`, `#resource packs`, `#malware`, `#patch`

---