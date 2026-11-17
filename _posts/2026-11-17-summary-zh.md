---
layout: default
title: "Horizon Summary: 2026-11-17 (ZH)"
date: 2026-11-17
lang: zh
---

> 从 41 条内容中筛选出 10 条重要资讯。

---

**科技新闻**
1. [vLLM v0.34.0：默认启用可扩展 KV 缓存并移除 Model Runner V1](#item-tech-news-1) ⭐️ 8.0/10
2. [Optimizely 被曝遭入侵，向 Zoom、GitLab 等站投放恶意代码](#item-tech-news-2) ⭐️ 8.0/10
3. [Jiff 1.0 发布：Rust 日期时间库新选择](#item-tech-news-3) ⭐️ 8.0/10
4. [美国将先进 AI 芯片及服务器管制扩至远程访问](#item-tech-news-4) ⭐️ 8.0/10
5. [CMU CS Learn 在 YouTube 免费发布完整课程讲座](#item-tech-news-5) ⭐️ 7.0/10
6. [Linebender 技术资料：squircle 与平滑曲线几何](#item-tech-news-6) ⭐️ 7.0/10
7. [Marimba：单次冻结 ASR 编码支持多类语音查询](#item-tech-news-7) ⭐️ 7.0/10
8. [美国与九国签署《旧金山宣言》共保 AI 供应链](#item-tech-news-8) ⭐️ 7.0/10
9. [亚马逊：Artex 驱动 AI 代理窃取并共享 API 密钥](#item-tech-news-9) ⭐️ 7.0/10
10. [阿里、腾讯、月之暗面据悉收紧新模型网络攻击能力](#item-tech-news-10) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0：默认启用可扩展 KV 缓存并移除 Model Runner V1](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM 发布 v0.34.0，包含 1,061 个提交和 412 名贡献者。该版本在 CUDA 和 ROCm 上默认启用可扩展 KV 缓存，按预热后的实际空闲显存确定缓存大小；官方举例称 MiniMax-M3 在 H200 上从 433k 增至 672k tokens。Model Runner V1 被移除，Model Runner V2 成为唯一 GPU runner，默认 block size 从 16 改为 64。升级还要求删除 VLLM\_USE\_V2\_MODEL\_RUNNER=0、改用 ROCm 10.0 构件，并满足 huggingface\_hub &gt;= 2.0.0。官方基准称 GB200 上部分解码最高提升 1.95 倍，但也提示可扩展 KV 缓存可能使部分 H200 模型在并发 128 时 TPOT 增加 6–18%。

github · khluu · 11月16日 23:22

**「背景」** vLLM 是面向大语言模型推理与在线服务的开源框架；其 KV cache 保存生成过程中已计算的注意力键值，避免每步重复计算，因此缓存能开多大直接影响并发吞吐和首 token 延迟。此次版本还把 GPU 执行路径统一切到 Model Runner V2，并改变了 KV cache 的容量计算方式，所以升级前需要了解这些默认行为的变化。

**「升级影响」** 现有部署若依赖 V1 logits processor，必须迁移到 vllm.v1.worker.gpu.sample.logits\_processor；若要保留旧缓存策略，可传 --gpu-memory-utilization 0.9 或 --no-enable-extensible-kv-cache。ROCm 7.2 镜像和 wheel 不再发布，相关环境需改用 ROCm 10.0。

**标签**: `#vLLM`, `#LLM inference`, `#KV cache`, `#GPU performance`, `#release engineering`

---

<a id="item-tech-news-2"></a>
### [Optimizely 被曝遭入侵，向 Zoom、GitLab 等站投放恶意代码](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

据安全博客 Report-URI 报道，Optimizely 遭到入侵，攻击者借其第三方 JavaScript 分发渠道，在 Zoom、GitLab 等使用该服务的网站上投放恶意代码。报道称，Optimizely 自有站点（包括 www.optimizely.com 和 login.optimizely.com）的代码片段也带有该代码；目前尚不清楚攻击者如何取得可跨多个客户项目写入的权限。该事件并非已确认的 CDN 缓存投毒，具体范围和受影响站点仍应以 Optimizely 的说明为准。

hackernews · kristjansson · 11月16日 23:00 · [社区讨论](https://news.ycombinator.com/item?id=50524767)

**「背景：Optimizely 脚本如何成为攻击面」** Optimizely Web 是一个 A/B 测试与实验平台，客户只要在页面中嵌入一段 Optimizely 提供的 snippet，测试代码就会从 Optimizely 的 CDN 加载执行；这与 Google Tag Manager 让市场团队无需工程介入即可加脚本的模式相同，因此单个第三方供应商能同时触达大量站点的访客。据 Report URI 的报道，此次攻击者把恶意代码写入 188 个 Optimizely Web snippet 的 Project JavaScript 字段，代码经 Optimizely 自有 CDN 以有效证书下发，受影响组织的服务器本身并未显示被入侵迹象，178 家机构（包括 Zoom、GitLab、BBC、CNN、Salesforce 等）的访客因此被波及，且其中仅 24 家部署了内容安全策略（CSP）。

**「受影响站点与迁移取舍」** 对嵌入 Optimizely 片段的站点（如 Zoom、GitLab）来说，恶意代码是随第三方脚本进入访客浏览器的，站点自身代码未必被改动，因此清理时需要逐一排查并替换页面中引用的第三方脚本。将外部脚本改为自行托管可以消除 CDN 供应链风险，但代价是必须自行管理更新、可能错过安全补丁，并可能破坏内联脚本和部分第三方集成。

**「社区讨论」** 评论者把矛头指向第三方标签管理带来的结构性风险：有人批评，为了让市场团队不必依赖工程团队就能添加标签，网站堆叠了大量脚本，结果每个新闻页面都加载约 10MB 的 JavaScript；也有人认为，Optimizely 和大型站点都缺少发布冷却、分阶段上线和安全检查等问责机制。另有评论追问：如果 CNN、BBC 这类网站并不处理加密货币或支付，恶意脚本为何仍能造成危害，或者是否还涉及浏览器安全问题。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cybersecuritynews.com/optimizely-websites-hijacked/">Hackers Infect 178 Major Websites via Optimizely to Steal ...</a></li>
<li><a href="https://blog.tmcnet.com/blog/rich-tehrani/msp/optimizelys-trusted-script-hit-178-companies-visitors-your-vendors-vendor-is-now-your-attack-surface.html">Optimizely’s Trusted Script Hit 178 Companies’ Visitors. Your ...</a></li>
<li><a href="https://www.systemshardening.com/articles/cross-cutting/cdn-third-party-script-supply-chain/">CDN and Third - Party Script Supply Chain Security: Lessons from...</a></li>

</ul>
</details>

**标签**: `#supply chain security`, `#third-party scripts`, `#web security`, `#Optimizely`, `#malware`

---

<a id="item-tech-news-3"></a>
### [Jiff 1.0 发布：Rust 日期时间库新选择](https://burntsushi.net/jiff/) ⭐️ 8.0/10

Jiff 1.0 已发布，这是 burntsushi 开发、面向 Rust 开发者的日期时间库，旨在为日期、时间和时区处理提供一套新的 API 选择。现有材料没有给出具体 API、性能基准或与 chrono 的兼容性细节，因此 1.0 的实际能力和迁移成本仍需以项目文档和后续验证为准。

hackernews · burntsushi · 11月16日 16:53 · [社区讨论](https://news.ycombinator.com/item?id=50519744)

**「背景」** 在 Rust 生态中，chrono 长期是常用的日期时间库；其前维护者在讨论中表示，稳定的 API 是它被采用的重要原因，但也让大幅改进变得困难。burntsushi 现已发布 Jiff 1.0，作为面向同类需求的新日期时间库进入这一领域。

**「对 Rust 项目的影响」** 对于需要处理本地时间和夏令时的 Rust 项目，Jiff 把时区处理放进核心 API，并自动处理常见的 DST 问题，这意味着这部分逻辑不必再由应用层手工补齐；1.0 的版本号也为依赖方提供了相对稳定的接口前提。是否从 chrono 迁移仍需各项目自行评估，社区评论中出现的只是希望生态更多采用 Jiff 的期待，并未提供兼容性或迁移成本的证据。

**「社区讨论」** 曾维护 chrono 约五年的 quodlibetor 表示，chrono 的 API 稳定性既是用户继续使用它的原因，也让改进面临很大阻力，他因难以推动改变而停止维护；另有评论者赞赏 Jiff 明确说明自己并非适用于所有场景。还有人询问 Jiff 如何处理 TAI、UT1 等时间尺度，显示社区关注它在专业时间计算中的适用范围。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://burntsushi.net/jiff/">A datetime library for Rust - Andrew Gallant&#x27;s Blog</a></li>
<li><a href="https://news.ycombinator.com/item?id=50519744">Jiff 1 . 0 : A datetime library for Rust | Hacker News</a></li>

</ul>
</details>

**标签**: `#Rust`, `#datetime`, `#open-source`, `#libraries`, `#timezones`

---

<a id="item-tech-news-4"></a>
### [美国将先进 AI 芯片及服务器管制扩至远程访问](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 8.0/10

美国商务部于 11 月 16 日发布临时最终规则，将先进 AI 芯片和服务器的出口管制扩大到远程访问，以封堵经由第三国数据中心规避限制的路径。据路透社和 The Verge 报道，规则还要求向印度尼西亚、马来西亚、新加坡、泰国和巴西再出口 AI 芯片时申请许可。报道并称规则由财政部和国家安全委员会主导起草，可能进一步收紧中国获取先进芯片的渠道；现有信息未提供规则全文或生效细节。

telegram · zaihuapd · 11月16日 14:44

**「背景」** 美国对先进 AI 芯片的出口管制由商务部工业与安全局（BIS）执行，传统上针对芯片和服务器的实体出口与再出口。此次临时最终规则把管制范围延伸到远程访问，正是为了封堵通过第三国数据中心远程调用芯片这一路径。规则同时要求向印尼、马来西亚、新加坡、泰国和巴西再出口 AI 芯片须申请许可。

**「合规影响」** 对在印尼、马来西亚、新加坡、泰国和巴西运营数据中心或从事再出口的企业来说，向受限方提供先进 AI 芯片和服务器的远程访问，或再出口这类设备，都需先取得许可；原本借助第三国数据中心提供算力的安排将需要重新进行合规审查，交付时间也可能更不确定。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://qz.com/us-ai-chip-reexport-licenses-five-countries-111626">U . S . is requiring licenses to reexport AI chips to five countries</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-16/us-moves-to-limit-remote-access-to-advanced-ai-chips">US Moves to Curb China’s Remote Access to Nvidia’s AI Chips</a></li>

</ul>
</details>

**标签**: `#AI chips`, `#export controls`, `#semiconductor policy`, `#data centers`, `#US-China tech`

---

<a id="item-tech-news-5"></a>
### [CMU CS Learn 在 YouTube 免费发布完整课程讲座](https://www.cs.cmu.edu/learn/) ⭐️ 7.0/10

卡内基梅隆大学的 CS Learn 已上线，开始在 YouTube 免费发布该校当前计算机科学课程的整学期讲座，内容涵盖机器学习系统、概率与计算等主题；本周每天上线一门课程，并计划在明年 1 月增加更多课程。现有信息未说明课程作业、习题或评估是否也会一并开放。

hackernews · pcompeau · 11月16日 20:43 · [社区讨论](https://news.ycombinator.com/item?id=50522980)

**「背景」** CMU 的 CS Learn 由 Kenneth C. Griffin 计算机科学学院推出，平台把课程做成完整学期的 YouTube 播放列表，免费向所有人开放，而不是只提供片段或课程介绍。项目负责人 Phillip Compeau 在讨论中将此举与 MIT 约 25 年前的开放课件传统相比较，并强调学生开发的工具自动化了大量制作流程。

**「影响」** 对自学者和开发者而言，可以直接观看 CMU 现授课程的完整讲座，但若没有配套作业和评估，这仍更接近视频讲座资源，而不是可完整跟学的课程包。

**「社区讨论」** 评论中有人询问是否会开放 15-122、15-150 等核心课程以及作业，主办方未在现有评论中回答；也有校友对 Tianqi Chen 的 ML Systems 和 15-259 概率课表示期待。另有评论认为，扎实掌握基础能让 AI 成为工具，否则可能被替代，这属于个人观点而非已证实的结论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/channel/UCqvooOJo8792T83va7LMMSA">CS Learn at Carnegie Mellon - YouTube</a></li>
<li><a href="https://www.pressreleasepoint.com/cmu-opens-access-top-computer-science-classes-through-free-cs-learn-platform">CMU Opens Access to Top Computer Science Classes Through Free ...</a></li>

</ul>
</details>

**标签**: `#computer science education`, `#open courseware`, `#CMU`, `#online learning`, `#YouTube`

---

<a id="item-tech-news-6"></a>
### [Linebender 技术资料：squircle 与平滑曲线几何](https://linebender.org/wiki/curves/squircle/) ⭐️ 7.0/10

Linebender 的 wiki 提供了一篇关于 squircle（方圆形）与平滑曲线几何的技术资料，主要面向图形渲染和 UI 实现人员。内容属于技术讲解，而非产品发布或性能对比；现有材料没有给出版本、兼容性或独立测量结果可供核对。

hackernews · raphlinus · 11月16日 07:55 · [社区讨论](https://news.ycombinator.com/item?id=50515151)

**「背景」** squircle（方圆形）是一种介于正方形与圆形之间的超椭圆曲线。它与普通圆角矩形的关键区别在于曲率连续性：直线边与圆角衔接处不会出现曲率突变，因此视觉过渡更平滑。Apple 在 iOS 应用图标及部分界面元素中采用这种形状，使其成为 UI 与图形渲染领域常见的几何参照。

**「对 UI 与图形实现的影响」** 对需要复现平台视觉的 UI 与图形工程师而言，普通的圆角矩形（border-radius）并不等同于 iOS 图标所采用的超椭圆；若目标是贴合系统图标或硬件外观，就需要按超椭圆曲线来实现，例如使用 figma-squircle 库或 CSS 的 corner-shape，而不是单纯调大圆角半径。这也带来了兼容性取舍：不同平台与浏览器对这类形状的支持程度不一，采用前需确认目标环境是否原生支持，或是否必须依赖第三方库。

**「社区讨论」** 评论者分享了实际案例和工具：有人提到第二代 Zune 的 squircle 方向键既可点击又适合滑动操作，也有人正在开发以 clothoid 为核心的样条／超椭圆创作工具并给出早期演示。另有评论指出，导数连续、避免不连续性的曲线在与物理交互结合时尤其有价值。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://squircle.js.org/blog/math-behind-squircles">The Squircle Formula: Superellipse Math Explained</a></li>
<li><a href="https://squircle.js.org/blog/squircles-in-apple-design">How Apple Uses Squircles in iOS Design - Squircle.js</a></li>
<li><a href="https://squircle.js.org/blog/squircles-in-apple-design">How Apple Uses Squircles in iOS Design - Squircle.js</a></li>
<li><a href="https://elsolitario.org/en/2026/11/16/squircle-css-ios-icon-superellipse/">Squircle in CSS: What It Is and How to Build One</a></li>

</ul>
</details>

**标签**: `#squircles`, `#superellipses`, `#curve-geometry`, `#graphics-rendering`, `#ui-design`

---

<a id="item-tech-news-7"></a>
### [Marimba：单次冻结 ASR 编码支持多类语音查询](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

这篇预印本提出 Marimba：对每个 8 秒音频窗口只运行一次冻结的 Qwen3-ASR-0.6B 编码器，随后用同一表征回答多类带类型的问题（词项检测、语种识别、话轮结束、说话人变化与计数），并返回校准后的概率。作者自报在 1,000 条公开问题的 9 项测试中有 6 项持平或超过 30B-A3B 的 Qwen3-Omni，但在 Speech Commands 上落后。语种识别在 300 条 FLEURS 片段上达到 100%，说话人变化在 AMI 和 VoxConverse 上 AUROC 为 0.966–0.980 并高于 ECAPA，说话人计数优于 pyannote 3.1。局限也很明确：话轮结束读数用 Smart Turn 数据训练，在该测试集上 AUROC 0.930，低于 Smart Turn v3.2 的 0.982；在 ICSI 上 0.716 对 0.712 基本持平；面对 CochlScene 等未见任务时各预测头仅达随机水平。

reddit · r/MachineLearning · /u/solanotodesch · 11月16日 15:47

**「背景」** 语音识别模型通常先把音频窗口编码成声学表示，再由解码器输出转写，beam search 则会保留多条候选转写。Marimba 的前提是，冻结的 Qwen3-ASR 0.6B 编码器特征及其候选转写已包含足够信息，可通过轻量读出器或打分来回答词项、语种和话轮结束等不同类型的判断，而不必为每个任务单独训练完整模型。

**「影响」** 对语音应用开发者，Marimba 以 Apache-2.0 权重、演示和 \`pip install marimba-audio\` 提供可直接试用的 0.6B 共享编码器方案，适合在自有数据上复核词项检测、语种和说话人相关任务。但不应把话轮结束或未见任务当作开箱即用能力：前者仅在 Smart Turn 分布内报告有竞争力，后者在 CochlScene 上已退化为随机，部署前需按目标场景重新验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/html/2611.18330v1">marimba: A System One Model for Speech - arXiv.org</a></li>
<li><a href="https://www.emergentmind.com/papers/2611.18330">Marimba: A System One Model for Speech - emergentmind.com</a></li>

</ul>
</details>

**标签**: `#speech-recognition`, `#asr`, `#model-calibration`, `#efficient-inference`, `#machine-learning-research`

---

<a id="item-tech-news-8"></a>
### [美国与九国签署《旧金山宣言》共保 AI 供应链](https://www.state.gov/releases/office-of-the-spokesman/2026/11/the-san-francisco-declaration-on-the-secure-foundations-of-enduring-prosperity/) ⭐️ 7.0/10

11 月 15 日，美国与澳大利亚、印度、以色列、日本、韩国、卡塔尔、新加坡、阿联酋和英国签署《旧金山宣言》，确认经济安全是国家安全的基础，并将共同保护支撑超级智能（SI）供应链的敏感技术与关键基础设施。宣言提出设立五个工作组，分别负责创新政策框架、SI 在关键领域的应用、SI 全栈供应链协作、安全港与供应链安全枢纽，以及 SI 安全与韧性。目前公开内容仅为一份宣言，未列出约束性承诺、具体技术措施或执行时间表。

telegram · zaihuapd · 11月16日 10:40

**「背景」** 从目前公开摘要看，这份宣言属于政策协调框架，列出签署方和五个工作组，但未给出约束性承诺、技术细节或时间表。它把“供应链安全”用于超级智能（SI）领域，关注支撑 SI 的敏感技术和关键基础设施，而不仅是单一模型或产品。

**「对供应链企业的影响」** 对在签署国运营的 AI 芯片、模型和关键矿产供应链企业而言，宣言把政策协调落实到五个工作组，并以降低对美方所称对手的依赖为目标。但从现有材料看，宣言未列出约束性承诺、时间表或具体合规细则，企业暂时无法据此判断采购、许可或本地化要求，需等待工作组后续产出。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/San_Francisco_Declaration_on_the_Secure_Foundations_of_Enduring_Prosperity">San Francisco Declaration on the Secure Foundations of Enduring Prosperity</a></li>
<li><a href="https://www.state.gov/releases/office-of-the-spokesman/2026/11/the-san-francisco-declaration-on-the-secure-foundations-of-enduring-prosperity/">The San Francisco Declaration on the Secure Foundations of ...</a></li>

</ul>
</details>

**标签**: `#AI governance`, `#AI supply chain`, `#geopolitics`, `#technology policy`, `#superintelligence`

---

<a id="item-tech-news-9"></a>
### [亚马逊：Artex 驱动 AI 代理窃取并共享 API 密钥](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

亚马逊报告称，攻击者利用开源渗透测试框架 Artex 操控 AI 代理，从公网暴露的 LiteLLM、Dify 等 AI 应用中窃取 API 密钥，验证后将密钥集中到共享池，并用于支付更多大模型调用。亚马逊称，该活动自 10 月 3 日持续至 11 月 5 日，最终被诱饵网络 MadPot 截获并阻断。亚马逊以中等信心将行动归因于与中国相关的威胁组织，同时表示并非所有被列目标都已失陷，并已通知可能受影响的 AWS 客户。

telegram · zaihuapd · 11月16日 13:00

**「背景」** Artex 是一个开源的代理式 AI 渗透测试框架，原本用于安全测试，但可被滥用来驱动 AI 代理自动执行侦察与攻击任务。亚马逊的 MadPot 是一套全球分布的诱饵传感器网络，负责捕获并阻断此类攻击流量。LiteLLM、Dify 等则是常见的 AI 应用网关与开发平台，其配置中通常保存大模型提供商的 API 密钥，一旦暴露在公网便成为窃取目标。

**「影响」** 使用 LiteLLM、Dify 等公网暴露 AI 应用的组织，面临上游模型 API 密钥被窃取并用于支付攻击者调用的风险；应立即排查未授权访问、轮换暴露实例上的密钥并限制密钥权限。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aws.amazon.com/blogs/security/amazon-threat-intelligence-observes-threat-actors-running-cybercrime-campaigns-with-artex-ai-agents/">Amazon Threat Intelligence observes threat actors running ...</a></li>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM, Dify ...</a></li>
<li><a href="https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/">AI credential theft campaign used stolen API keys to scale</a></li>

</ul>
</details>

**标签**: `#AI security`, `#API keys`, `#autonomous agents`, `#cybercrime`, `#open-source security`

---

<a id="item-tech-news-10"></a>
### [阿里、腾讯、月之暗面据悉收紧新模型网络攻击能力](https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models) ⭐️ 7.0/10

据 Telegram 频道「科技圈·茶馆」转述彭博社报道，阿里巴巴、腾讯、月之暗面等中国头部 AI 公司在新一代模型中削弱了进攻性网络能力，同时提升防御表现。报道称，阿里最新旗舰 Qwen 未开放权重，用户无法下载并自定义完整版本；腾讯在本月发布 Hy4 之前也已削减相关网络功能。这一做法与商务部上月公布的出口管制草案相关，该草案拟禁止可攻击关键基础设施和政府网络的 AI 工具出口。上述说法来自二手转述，源材料未包含相关公司的回应，出口管制措施目前仍为草案。

telegram · zaihuapd · 11月17日 02:20

**「背景」** 中国商务部上月公布出口管制草案，拟禁止可攻击关键基础设施、政府网络的 AI 工具出口。该草案是这轮模型能力调整的直接政策背景，厂商据报在新模型发布前重新评估网络攻击相关功能。

**「影响」** 对依赖完整权重做微调或私有部署的开发者，最直接的变化是最新旗舰 Qwen 不再提供这条路径。若拟议的出口管制落地，面向关键基础设施和政府网络的攻击性 AI 工具出口将受到限制，涉及跨境交付此类能力的团队需要提前评估合规安排。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models">China’s Top AI Firms Limit Cyber Capabilities in Latest ...</a></li>
<li><a href="https://www.business-standard.com/world-news/chinese-ai-firms-scale-back-cyber-capabilities-amid-proposed-export-ban-126111700190_1.html">Chinese AI firms scale back cyber capabilities amid proposed ...</a></li>

</ul>
</details>

**标签**: `#China AI`, `#AI policy`, `#cybersecurity`, `#open weights`, `#export controls`

---