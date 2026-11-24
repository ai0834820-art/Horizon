---
layout: default
title: "Horizon Summary: 2026-11-24 (ZH)"
date: 2026-11-24
lang: zh
---

> 从 35 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [英伟达董事会据称恢复黄仁勋 CEO 职务](#item-tech-news-1) ⭐️ 8.0/10
2. [Z.ai 发布 GLM-5.4：首个循环 Transformer，面向通用编程](#item-tech-news-2) ⭐️ 8.0/10
3. [Ladybird 浏览器发布首个 Alpha 版](#item-tech-news-3) ⭐️ 8.0/10
4. [NariQ 发布 Qwen3.8-27B 的 3-bit 及更低比特量化](#item-tech-news-4) ⭐️ 7.0/10
5. [Codex2api 疑遭供应链投毒，3.1.10–3.1.12 需回退](#item-tech-news-5) ⭐️ 7.0/10
6. [Meta AI 负责人称超级智能临近并警告控制风险](#item-tech-news-6) ⭐️ 7.0/10
7. [黎曼猜想「AI 证明」被指空转，作者承认代码满是垃圾](#item-tech-news-7) ⭐️ 7.0/10
8. [Mozilla、Shopify 等联名促欧盟调查苹果浏览器限制](#item-tech-news-8) ⭐️ 7.0/10
9. [黄循财：新加坡不会成为规避美国芯片管制通道](#item-tech-news-9) ⭐️ 7.0/10
10. [Anthropic 据称公开 AI 撰写的 VP≠VNP Lean 4 证明](#item-tech-news-10) ⭐️ 7.0/10

**科技博客**
1. [ERNIE 5.5 Flash 的 vLLM 插件首日支持](#item-tech-blog-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [英伟达董事会据称恢复黄仁勋 CEO 职务](https://www.cnbc.com/2026/11/23/nvidia-jensen-huang-ceo.html) ⭐️ 8.0/10

Hacker News 上的一条投稿称，英伟达董事会已恢复黄仁勋的总裁、CEO 及董事职务；但帖子只给出英伟达新闻稿和 CNBC 的链接，没有正文，现有材料无法独立核实这一说法。评论中引述的董事会声明称，董事会在决策时听取了美国政府高层意见，并据此认为黄仁勋回归不构成国家安全风险。该投稿发布于 2026 年 11 月 23 日，相关公司治理反转和政府介入细节仍属未经证实的报道。

hackernews · jaz · 11月23日 14:00 · [社区讨论](https://news.ycombinator.com/item?id=50611576)

**「背景：从罢免到复职」** 这次复职逆转了英伟达董事会此前解除黄仁勋职务的决定；《卫报》将这一逆转与美国总统特朗普的介入联系起来，称其“说服”了董事会。英伟达投资者关系公告则称，董事会是在与黄仁勋进行一系列讨论和会议后，一致投票决定让其复职，并立即生效。

**「社区讨论」** 评论区主要围绕董事会声明中“听取美国政府高层意见”这一表述展开：有人称，Caremark 判例对董事会问责设定了很高门槛，若司法部不提起诉讼，可能有助于免除董事的个人责任；也有人认为，英伟达与 2023 年 OpenAI 事件一样，说明名义治理结构未必等于实际治理结构。还有评论批评美国在要求阿斯麦和日本芯片企业配合对华制裁的同时，却对英伟达网开一面，认为这构成双重标准。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Board-Reinstates-Jensen-Huang-as-President-CEO-and-Board-Director/default.aspx">NVIDIA Corporation - NVIDIA Board Reinstates Jensen Huang as ...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/23/jensen-huang-reinstated-as-nvidia-chief-executive">Jensen Huang reinstated as Nvidia CEO after Trump intervenes</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#semiconductor industry`, `#corporate governance`, `#US national security policy`, `#Hacker News`

---

<a id="item-tech-news-2"></a>
### [Z.ai 发布 GLM-5.4：首个循环 Transformer，面向通用编程](https://z.ai/blog/glm-5.4) ⭐️ 8.0/10

Z.ai（智谱 AI）发布 GLM-5.4，称这是其首个采用循环 Transformer 架构的模型，面向通用编程。按 Z.ai 的解释，一组共享权重的层在一次前向传播中运行多次并细化隐藏状态，从而在不增加参数量的情况下加深网络；目前公开材料没有给出可独立验证的基准结果。GLM-5.4 尚未开放权重，现阶段需通过 Z.ai 的 Coding Plan 订阅访问，常规 API 套餐不能直接调用；Coding Plan 的密钥可在同一 OpenAI 兼容的 Responses API 端点（https://api.z.ai/api/v1）使用。早期试用者 Simon Willison 用“骑自行车鹈鹕”SVG 测试后发现，5.4 与 5.3 的输出质量相近，最高档位生成的自行车车架仍有明显结构问题。

hackernews · foohis · 11月23日 10:06 · [社区讨论](https://news.ycombinator.com/item?id=50609685)

**「背景」** 标准 Transformer 中每层在一次前向传播中只计算一次；Z.ai 所说的循环 Transformer 让一组共享权重的层反复运行多次，并基于上一轮的隐藏状态继续细化，从而在不增加参数量的情况下加深有效网络。Z.ai 称 GLM-5.4 是其首个采用该架构的模型；此前在 11 月 20 日，Thinking Machines Lab 的 Inkling 2 Mini 也采用了循环结构，其中间层会对每个 token 运行三次。

**「接入门槛」** 对开发者来说，最直接的影响是接入门槛：GLM-5.4 目前尚未开放权重，也不能通过常规 API 套餐或 OpenRouter 调用，只有订阅 Z.ai 的 Coding Plan 才能获得可访问该模型的 API key。该套餐与常规 API 共用同一套 OpenAI 兼容接口（https://api.z.ai/api/v1），因此已有兼容客户端只需更换 key 和端点即可试用，但想要本地部署或自托管的团队暂时没有可用路径。

**「社区讨论」** 有 HN 评论者称赞 Z.ai 公开了较多架构细节，认为循环 Transformer 是明显的发展方向，但也承认仍有问题；另有开发者抱怨部分中国模型在简单任务上反复自我检查，导致完成时间明显长于前沿模型。还有评论从推理瓶颈解释循环架构：每层只计算一次时，权重在 HBM 与芯片间搬运是主要瓶颈，重复使用共享层可减少这类开销。

**标签**: `#LLMs`, `#AI coding`, `#looped transformers`, `#Zhipu AI`, `#model release`

---

<a id="item-tech-news-3"></a>
### [Ladybird 浏览器发布首个 Alpha 版](https://ladybird.org/posts/alpha/) ⭐️ 8.0/10

Ladybird 项目在 2026 年 11 月发布了首个 Alpha 版，macOS 和 Linux 用户现在可以直接下载安装，无需自行编译。它采用自研的 HTML 解析、CSS、布局、JavaScript 和 WebAssembly 组件，仅复用 HarfBuzz、Skia、FFmpeg、SQLite 等外部库。试用显示多数网站能正常渲染，WebAssembly 版 FFmpeg 和 Pyodide 可运行，但 Datasette Lite 因 Service Worker 接口 \`navigator.serviceWorker.startMessages\` 未实现而报错；官方提醒部分网站会失效并可能崩溃。

hackernews · janvdberg · 11月23日 16:13 · [社区讨论](https://news.ycombinator.com/item?id=50614249)

**「背景」** Ladybird 源自 Andreas Kling 发起的 SerenityOS 项目，目标是从零实现 HTML 解析、CSS 引擎、布局、JavaScript 和 WebAssembly 等浏览器核心，目前仍复用 HarfBuzz、Skia、FFmpeg 和 SQLite 等少数外部组件。该项目在 2026 年 2 月宣布借助 Claude Code 和 Codex，将 LibJS 的部分 C++ 代码在两周内移植为约 25,000 行 Rust；据其 2026 年 10 月月报，样式与布局移入独立线程、新 JavaScript JIT 和基于 Cranelift 的新 WebAssembly 引擎相继落地，后者在 JetStream 3 WASM 基准上提升 7 倍，当月 Web 平台测试新增 75,650 项通过。

**「影响」** Web 开发者现在可以把 Ladybird Alpha 作为额外的兼容性测试目标；遇到站点问题可从浏览器内报告，崩溃后可查看并选择发送报告。普通用户若要日常使用，仍应预期部分网站失效和崩溃，官方也明确邀请安全研究者测试。

**「社区讨论」** 多位试用者报告兼容性超出预期，复杂新闻站点和 ProxMox 的 NoVNC 界面可正常打开，甚至比 Firefox 更流畅，但也有人提到页面滚动略显卡顿。评论还担忧指纹识别和权限粒度，并讨论 Ladybird 改用 SQLite、Skia 等成熟外部库与早期 SerenityOS 自研风格之间的取舍。

**标签**: `#browsers`, `#open-source`, `#web-engines`, `#Ladybird`, `#software-engineering`

---

<a id="item-tech-news-4"></a>
### [NariQ 发布 Qwen3.8-27B 的 3-bit 及更低比特量化](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

NariQ 发布了 Qwen3.8-27B 的 3-bit 及更低比特 GGUF 量化，称约 10GB 的文件可保留接近 BF16 的质量，面向本地 LLM 推理用户。厂商公布的基准（BF16 / 3-bit / 2.5-bit / 2-bit）显示，3-bit 与 2.5-bit 在 DeepSWE、Terminal-Bench 2.1、AIME 25+26 等任务上基本持平甚至略高，但 2-bit 明显下降，例如 AIME 为 86.0 对 97.7。其称在 RTX PRO 6000 上解码速度与其他量化相当，3-bit 在 4K 至 64K 上下文为 88.9 至 70.7 tok/s。上述结果尚待独立验证，且目前运行这些量化必须使用其 nari-llama.cpp 分支。

hackernews · toebee · 11月23日 13:42 · [社区讨论](https://news.ycombinator.com/item?id=50611402)

**「背景」** GGUF 是 llama.cpp 使用的模型文件格式，低比特量化通过把权重压缩到更少位数来降低显存占用，但推理框架必须支持对应的量化类型才能加载。社区此前已有 ik\_llama.cpp 这类为特定量化或性能优化而维护的 llama.cpp 分支；NariQ 也以自带 fork 的方式发布，因此用户无法直接用上游 llama.cpp 运行这些文件。

**「影响」** 对本地部署者而言，实际影响是必须改用 nari-llama.cpp 分支，并在 3-bit/2.5-bit 与 2-bit 之间按任务取舍：前者在公布基准中接近 BF16，后者在 AIME 等任务上明显退化，不能只因为文件更小而选择它。

**「社区讨论」** 社区对基准结论仍有分歧：一位评论者肯定该项目覆盖多种长程任务并提到 held out，认为它比常见的高计算量 QAT 量化做了更认真的检查；另一位则根据图表认为大部分提升来自测试框架差异，而非模型本身。还有 M3 Pro 用户报告 3.0bpw 解码约 3.8 tok/s、2.0bpw 约 4.9 tok/s，明显慢于 CUDA。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/ikawrakow/ik_llama.cpp">GitHub - ikawrakow/ik_ llama . cpp : llama . cpp fork with additional...</a></li>

</ul>
</details>

**标签**: `#quantization`, `#local LLM inference`, `#Qwen`, `#llama.cpp`, `#model compression`

---

<a id="item-tech-news-5"></a>
### [Codex2api 疑遭供应链投毒，3.1.10–3.1.12 需回退](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 7.0/10

据事件复盘，Codex2api 作者账号疑似被黑，攻击者绕过 main 分支直接推送 tag，使 Release 构建出带后门的版本；v3.1.11 被指移除鉴权，从而形成无需密码的远程命令执行。相关 workflow 还被指将仓库的 16 个 GitHub Actions secrets 外传，波及同一账号下至少 21 个仓库。复盘建议安装或更新过 3.1.10–3.1.12 的用户立即停用并回退到 3.1.9，同时轮换 GitHub token、SSH key、数据库及 DeepSeek 等相关密钥。上述细节来自该复盘，尚未见独立验证。

telegram · zaihuapd · 11月23日 11:21

**「背景：GitHub Actions 发布链路风险」** Codex2api 的发布依赖 GitHub Actions：维护者账号一旦失守，攻击者就能绕过 main 分支直接推送 tag，触发 Release 构建并接触仓库 secrets。2026 年 10 月披露的 GhostAction 活动采用了类似路径——通过被盗的 GitHub 维护者账号注入恶意 workflow，窃取 CI/CD secrets 和云凭据，报道提到至少 772 个公开仓库受影响。

**「受影响用户处置」** 对安装或更新过 3.1.10–3.1.12 的用户来说，应按凭据已泄露处置：停用并回退到 3.1.9，轮换 GitHub token、SSH 密钥、数据库和 DeepSeek 等密钥，并审计同账号下至少 21 个仓库、轮换被外传的 16 个 Actions secrets。近期已出现劫持 GitHub 账号并向仓库植入窃取 CI secrets 的 workflow 的活动，因此关联仓库的 Actions 凭据也应一并视为暴露。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aviatrix.ai/threat-research-center/ghostaction-github-actions-credential-theft-2026/">GhostAction GitHub Actions Supply Chain Attack Analysis 2026</a></li>
<li><a href="https://cybersecuritynews.com/ghostaction-supply-chain-campaign/">GhostAction Supply Chain Campaign Uses Malicious GitHub ...</a></li>
<li><a href="https://labs.cloudsecurityalliance.org/research/csa-research-note-wfx-github-ci-secret-stealer-20261112-csa/">The wfx Campaign: Hijacked GitHub Accounts Harvest CI Secrets</a></li>
<li><a href="https://thehackernews.com/2026/10/credential-stealing-github-actions.html">Credential-Stealing GitHub Actions Workflows Planted in Tens ...</a></li>

</ul>
</details>

**标签**: `#supply-chain attack`, `#GitHub Actions`, `#security incident`, `#credential rotation`, `#open source security`

---

<a id="item-tech-news-6"></a>
### [Meta AI 负责人称超级智能临近并警告控制风险](https://thenextweb.com/news/metas-ai-chief-says-superintelligence-is-arriving-and-control-is-at-risk) ⭐️ 7.0/10

据报道，Meta 首席 AI 官兼超级智能实验室负责人 Alexandr Wang 在 X 发长文称，超级智能已不再是“未来某天”的议题；他警告人类可能难以继续控制可无限自我改进或比自己聪明 1000 倍的系统，并呼吁紧急投入安全、对齐与防护研究。他援引数学家 Levent Alpöge 借助 Anthropic 的 Claude 完成、并于周六经 Lean 与 Mathlib 社区机器校验的一项所称黎曼猜想证明，认为 AI 与顶尖人类的差距只剩具体知识、工程整合与实验三块。该证明目前尚无人类可读版本，来源也只是简要转述，缺乏独立技术论证，因此不能视为已确认的数学突破。

telegram · zaihuapd · 11月23日 12:49

**「背景」** 黎曼猜想被数学界视为最著名的未解难题之一；据《卫报》报道，Alpöge 公布了用 Lean 语言写成的代码，并称这些代码可以校验其证明。Lean 是一种用于形式化数学证明的证明助手语言，Mathlib 则是 Lean 的主要数学库。Lean FRO 与 Mathlib Initiative 在周六表示，他们对 Alpöge 黎曼猜想证明的正确性有“充分信心”。这也说明，为何 Wang 会把这次校验作为判断 AI 能力接近顶尖人类的依据；不过该证明至今仍没有人类可读版本。

**「实际影响」** 对数学界和 AI 安全团队来说，眼下更稳妥的做法是等待该证明的人类可读版本和独立复核，再把它当作模型能力或安全风险的基准；在此之前引用该案例，应明确它只有 Lean/Mathlib 机器校验、尚无人类可读证明。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2026/nov/21/anthropic-riemann-hypothesis-solved-claude-ai">Two groups verify mathematician’s claim that Claude ... | The Guardian</a></li>
<li><a href="https://www.zerohedge.com/science/did-claude-just-solve-maths-most-famous-problem-even-anthropics-mathematician-admits-timing">Mathematicians Confirm Claude Solved Math&#x27;s Most... | ZeroHedge</a></li>

</ul>
</details>

**标签**: `#AI safety`, `#superintelligence`, `#Riemann hypothesis`, `#Lean/Mathlib`, `#Anthropic Claude`

---

<a id="item-tech-news-7"></a>
### [黎曼猜想「AI 证明」被指空转，作者承认代码满是垃圾](https://x.com/i/web/status/2124987173439209561) ⭐️ 7.0/10

Alpöge 与 Claude 宣称用 Lean 形式化证明了黎曼猜想及广义版本，但公开内容只有约 1700 万行代码和 17.5 万个文件，没有人类可读的证明。Lean 与 Mathlib 社区次日曾表示，对代码证明了该命题“有充分信心”。随后研究者指出，关键定义被写成恒真、几何条件形同虚设，证明可能只是空转；23 日 Alpöge 承认“25 万页是玩笑”，称代码“满是垃圾但能编译”，并认为批评完全合理。该帖未附原始代码或证明链接，上述说法尚无法独立核验。

telegram · zaihuapd · 11月24日 01:29

**「背景」** 这场争议的直接前身是 2026 年 11 月 20 日 Levent Alpöge 公布的证明：他称与 Anthropic 的 Claude 合作，证明了黎曼猜想以及 Dirichlet L 函数的广义黎曼猜想。维基百科条目称，相关的 Lean 形式化工作从 10 月 6 日持续到 11 月 16 日，这意味着公开时它已是一个约六周内完成的超大代码工程，而非经过常规同行评审的论文证明。

**「影响」** 对使用 Lean/Mathlib 评估 AI 形式化证明的开发者而言，此事的直接教训是：编译通过只说明代码能通过类型检查，不能说明定理陈述非平凡或与目标命题一致。在采信此类结果前，应审查定义、几何条件和定理陈述，而不能只看代码规模或社区初期的信心表态。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Riemann_hypothesis">Riemann hypothesis - Wikipedia</a></li>
<li><a href="https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/">Alpöge / Claude proof of the Generalized Riemann Hypothesis</a></li>

</ul>
</details>

**标签**: `#AI for mathematics`, `#Lean theorem proving`, `#formal verification`, `#LLM hype`, `#Riemann Hypothesis`

---

<a id="item-tech-news-8"></a>
### [Mozilla、Shopify 等联名促欧盟调查苹果浏览器限制](https://appleinsider.com/articles/26/11/23/eu-urges-to-challenge-apples-grip-on-iphone-browsers?utm_source=rss) ⭐️ 7.0/10

据报道，一封由 Mozilla、Shopify 等企业及民间组织参与的联名信已致信欧盟委员会，要求就苹果对 iPhone 浏览器的限制正式立案；组织方称署名方合计代表约 4.5 万至 5.5 万家欧盟企业组织，联署将持续到 2026 年 12 月 3 日。信方指出，苹果虽依《数字市场法》允许欧盟竞品浏览器使用自有引擎，但技术与法律要求使厂商无法把现有欧盟用户迁出 WebKit，企业仍依赖 App Store 触达用户。联名方估算，若半数原生 iOS 应用转向 Web，欧盟企业每年可节省 110 亿欧元开发成本和 13 亿欧元 App Store 费用。

telegram · zaihuapd · 11月24日 03:02

**「背景」** 《数字市场法》（DMA）要求被认定为“守门人”的大型平台开放其生态，苹果因此已在欧盟允许第三方浏览器使用非 WebKit 引擎。但据 MacRumors 报道，这封致欧盟委员会主席冯德莱恩的公开信认为，苹果在 DMA 下做出的调整并未带来实质性的浏览器竞争。此前欧盟委员会已就 DMA 合规问题要求苹果采取开放措施，此次联名信实际上是要求委员会进一步立案调查。

**「影响」** 对欧盟的浏览器厂商和 Web 开发者来说，信方点出的实际障碍是既有用户无法随引擎切换迁出 WebKit，且分发仍依赖 App Store；这使立案诉求直接涉及迁移机制和费用，而不只是第三方引擎许可。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.macrumors.com/">MacRumors: Apple News and Rumors</a></li>
<li><a href="https://www.cnbc.com/2025/03/19/eu-orders-apple-to-open-up-app-store-risking-trump-retaliation.html">EU hits Google, Apple with antitrust actions risking Trump retaliation</a></li>

</ul>
</details>

**标签**: `#Apple`, `#EU DMA`, `#iOS browsers`, `#WebKit`, `#tech regulation`

---

<a id="item-tech-news-9"></a>
### [黄循财：新加坡不会成为规避美国芯片管制通道](https://www.bloomberg.com/news/articles/2026-11-24/singapore-won-t-be-conduit-to-skirt-us-chip-curbs-wong-says) ⭐️ 7.0/10

新加坡总理黄循财表示，新加坡不会成为企业规避美国芯片出口管制的通道，并称当局正在调查 Megaspeed 采购英伟达芯片的交易。此前一天，美国商务部将 Megaspeed 及另外 6 家东南亚企业列入贸易黑名单；《联邦公报》称这些企业存在向未获授权用户转移先进计算产品的“重大风险”，名单涉及其在马来西亚和泰国的关联实体。路透社报道，阿里巴巴新加坡子公司 Apex Enterprise Solutions 也在名单中，阿里回应称从未转移受管制的先进计算芯片。

telegram · zaihuapd · 11月24日 05:03

**「背景」** 美国的芯片出口管制由商务部执行，一旦企业被列入其贸易黑名单，相关方在向其转移受管制的先进计算产品时就面临明确限制；《联邦公报》给出的理由正是这些企业存在把先进计算产品转移给未获授权用户的“重大风险”。此次美方名单除 Megaspeed 外还包括另外 6 家东南亚企业及其在马来西亚、泰国的关联实体，而新加坡当局正在调查的，正是 Megaspeed 采购英伟达芯片的交易。

**「合规与采购影响」** 对于在新加坡和东南亚处理英伟达先进芯片的企业来说，被列入贸易黑名单意味着 Megaspeed 及其马来西亚、泰国关联实体，以及阿里巴巴新加坡子公司 Apex Enterprise Solutions，与美国供应商的交易将受到限制；客户和合作方也需要重新核查最终用户和转售路径。Megaspeed 的禁令何时生效尚未明确，短期影响主要是合规审查和交易不确定性；黄循财的表态也意味着新加坡本地调查与执法会加强。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://uz.kursiv.media/en/2026-11-24/us-blacklist-megaspeed-alice-huang/">US blacklists Megaspeed , once led by China spy suspect Alice Huang</a></li>
<li><a href="https://www.bbc.com/news/articles/cv98xpg5dg5zo">US to blacklist Asian AI firm Megaspeed after Nvidia scandal</a></li>

</ul>
</details>

**标签**: `#chip export controls`, `#semiconductors`, `#AI hardware`, `#Singapore`, `#Nvidia`

---

<a id="item-tech-news-10"></a>
### [Anthropic 据称公开 AI 撰写的 VP≠VNP Lean 4 证明](https://github.com/anthropics/formal-math/blob/main/vp-vnp/README.md) ⭐️ 7.0/10

据 Telegram 消息，Anthropic 于 11 月 24 日公开论文《VP ≠ VNP over every field》及 Lean 4 形式化证明，称结果由内部研究用 Claude 模型发现，论文和代码均由 AI 撰写。论文给出哈密顿圈多项式的超多项式算术电路下界，据此推出 VP 是 VNP 的真子类；若成立，这将解决 Valiant 1979 年的代数复杂度猜想，但只针对算术电路，不涉及 P 与 NP。形式化已通过三条标准公理审计和独立内核 nanoda 复核，除预留文件外没有 sorry；不过尚无人类数学家通读，Lean 无法确认形式化陈述与所声称命题一致，附录 Q 列出了出入，结果仍待独立审阅。

telegram · zaihuapd · 11月24日 06:02

**「背景」** VP 与 VNP 是 Valiant 在 1979 年为算术电路复杂性提出的类别；VP≠VNP 猜想询问是否存在某些多项式（如永久式）无法由多项式规模的算术电路计算，这与布尔电路下的 P 与 NP 问题不同。Lean 4 是交互式定理证明器，其小型内核可机械检查证明步骤；形式化能排除证明中的逻辑错误，但不能自动保证被形式化的命题与论文声称的数学命题一致。

**「使用前须核对形式化陈述」** 对想引用该下界或在此基础上继续做算术电路下界工作的研究者来说，目前能被机器检查的只是 Lean 内核与 nanoda 对论文所写出的形式陈述本身的通过，而不是该陈述与《VP ≠ VNP over every field》所声称命题的一致性——源内容明确指出附录 Q 已列出两者的出入。因此在下游引用或扩展之前，需要先由人工作者逐条核对形式化陈述与命题的对应关系，在此之前这项结果应按待独立审阅的预印本处理，而非可直接引用的已证定理。

**标签**: `#computational complexity`, `#Lean 4`, `#formal verification`, `#AI for mathematics`, `#Anthropic`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [ERNIE 5.5 Flash 的 vLLM 插件首日支持](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 7.0/10

rss · vLLM Blog · 11月24日 00:00

**「背景」** ERNIE 5.5 Flash 预览版是 280B 总参数、每 token 激活 14B 的稀疏 MoE，支持 1M 上下文、思考与工具调用，面向长程 Agent；难点是让这种新结构在发布当天进入 vLLM，且不维护分叉。

**「方案」** Baidu ERNIE 团队与 vLLM 采用独立 vLLM-ERNIE 插件：与 vllm==0.32.0 同环境安装，经 vllm.general\_plugins 入口在启动时注册，且仅在 config 指定 ERNIE 架构时惰性导入模型代码，因此无需专用镜像或 nightly wheel，服务其他模型也无额外开销。针对 VHA、Multi-Router Latent MoE、MultiMax 输出头和门控注意力等新结构，作者将可预计算参数折叠进权重并设计融合 kernel，称单 kernel 比逐算子实现快 1.55–6.53 倍，部分输出逐位一致。FlashIndexer 以只依赖当前 token 的小型 head router 选择少量索引头并阈值预过滤，约 1B token 蒸馏微调后在 1M 上下文测得 1.4× 加速；默认路由专家用 MXFP4 W4A8 QAT，KV cache 用 FP8，3 层 DSpark 草稿模型每步最多提议 7 token，编码与 Agent 负载平均接受长度超过 4.0，并支持张量并行、PD 分离与 KV CPU offload。这些加速数字来自厂商博文，缺少完整基准方法和硬件细节，需独立复核。

**「启示」** 作者认为，插件机制让新模型发布当天即可运行在官方 vLLM 上，同时把模型专属优化留在独立包内，避免维护分叉和增加环境负担。更广泛地看，这展示了“上游通用能力加下游模型插件”的交付路径，但其性能收益仍应由独立基准检验。

**标签**: `#vLLM`, `#MoE inference`, `#kernel fusion`, `#speculative decoding`, `#plugin architecture`

---