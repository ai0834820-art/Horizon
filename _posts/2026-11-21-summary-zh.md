---
layout: default
title: "Horizon Summary: 2026-11-21 (ZH)"
date: 2026-11-21
lang: zh
---

> 从 34 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [KVM 漏洞 CVE-2026-99312 暴露 AMD 宿主机内存](#item-tech-news-1) ⭐️ 8.0/10
2. [Scott Aaronson 借“随机鹦鹉”讨论 AI 推理可信度](#item-tech-news-2) ⭐️ 7.0/10
3. [陶哲轩博客：无外力纳维-斯托克斯奇点与广义黎曼猜想](#item-tech-news-3) ⭐️ 7.0/10
4. [Inkling 2 Mini：循环架构的开放权重模型](#item-tech-news-4) ⭐️ 7.0/10
5. [语言模型重写自身权重论文遭质疑](#item-tech-news-5) ⭐️ 7.0/10
6. [Levent Alpöge 声称与 Claude 证明广义黎曼假设](#item-tech-news-6) ⭐️ 7.0/10
7. [Signal 试图阻止移动系统 AI 代理读取私聊](#item-tech-news-7) ⭐️ 7.0/10
8. [Ravi Vakil 提前公布 Masullo 的广义黎曼猜想证明草稿](#item-tech-news-8) ⭐️ 7.0/10
9. [TikTok 全球上线 AI 深度伪造检测工具](#item-tech-news-9) ⭐️ 7.0/10
10. [OpenAI 后台模式上线：最长 8 小时，Token 最多便宜 40%](#item-tech-news-10) ⭐️ 7.0/10
11. [台积电暂停对中国企业 16nm 及以下芯片订单](#item-tech-news-11) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [KVM 漏洞 CVE-2026-99312 暴露 AMD 宿主机内存](https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html) ⭐️ 8.0/10

Linux 内核 KVM 的 CVE-2026-99312 漏洞仅影响启用了嵌套虚拟化的 AMD 主机，可使虚拟机读取宿主机内存。研究人员在 DigitalOcean 上从虚拟机内读取到约 127 GB 宿主内存。上游修复已于 11 月 18 日随稳定内核 7.3.5 等版本发布，但 Debian、Ubuntu 等发行版内核尚未修复；在补丁到位前可关闭嵌套虚拟化。

telegram · zaihuapd · 11月20日 14:23

**「背景」** KVM 是 Linux 内核内置的虚拟化层；嵌套虚拟化则允许虚拟机内部再运行自己的 hypervisor 和客户机，因此把虚拟化攻击面从一层扩展到两层。Red Hat 的漏洞说明指出，CVE-2026-99312 要求 AMD 宿主启用嵌套虚拟化，并由攻击者控制的嵌套客户机在分页关闭时触发处理器复位模拟，造成 MMU 状态不一致，从而为读取宿主内存创造条件。

**「处置影响」** 对在 AMD 主机上启用嵌套虚拟化的云平台和自建环境，补丁到位前最直接的处置是关闭嵌套虚拟化，但这会使依赖“虚拟机内再运行虚拟机”的测试、开发或租户工作负载无法运行。DigitalOcean 的漏洞公告列出了已修补内核和缓解措施，可作为运维人员判断升级或临时关闭该功能的依据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99312">CVE-2026-99312 - Red Hat Customer Portal</a></li>
<li><a href="https://www.digitalocean.com/blog/cve-2026-99312-kvm-patch">Virtualization , Responsible Disclosure, and CVE - 2026 - 99312</a></li>

</ul>
</details>

**标签**: `#KVM`, `#Linux kernel`, `#CVE-2026-99312`, `#AMD virtualization`, `#cloud security`

---

<a id="item-tech-news-2"></a>
### [Scott Aaronson 借“随机鹦鹉”讨论 AI 推理可信度](https://scottaaronson.blog/?p=10344) ⭐️ 7.0/10

Scott Aaronson 的博客文章借“随机鹦鹉”这一说法讨论 AI 和大语言模型的能力主张，Hacker News 上的讨论则集中在机器推理能否被理解和信任。文章标题写“随机鹦鹉证明了黎曼猜想”，但现有材料表明这并不是实际的数学证明，而是带有夸张色彩的评论引子。

hackernews · stratos123 · 11月20日 20:03 · [社区讨论](https://news.ycombinator.com/item?id=50581084)

**「背景」** “随机鹦鹉”是 2021 年批评大语言模型时流行起来的说法，用来质疑模型是否真正理解语言，而不只是按统计规律生成文本。Aaronson 的文章引用了社交媒体上的反讽说法——既然这些模型据称已经证明黎曼猜想，再称它们为“随机鹦鹉”是否自相矛盾——并以“ROFL”回应；相关争论还涉及 Levent Alpöge 关于 Anthropic 模型证明广义黎曼猜想的声称。

**「影响」** 对评估大模型数学能力的读者来说，可操作的区分是把“模型给出证明”与“证明经过数学界验证”分开；在缺少可复核推导时，标题中的“证明”不能当作能力证据。

**「社区讨论」** 有评论者以国际象棋引擎 Stockfish 的评估输出作类比，认为系统即使给出结果和分解计算，也未必提供人类想要的“为什么”；还有人担忧人类会越来越难以理解科学和工程系统。这些是评论者的个人观点，并不构成对 LLM 推理能力的验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://scottaaronson.blog/?p=10344">Shtetl-Optimized » Blog Archive » The stochastic parrots have ...</a></li>
<li><a href="https://agihunt.info/en/p/1a1faf3ca85035bde600331be64">Scott Aaronson: Alpöge claims Anthropic models… · AGI Hunt</a></li>

</ul>
</details>

**标签**: `#AI reasoning`, `#LLM limitations`, `#mathematics`, `#explainability`, `#Hacker News`

---

<a id="item-tech-news-3"></a>
### [陶哲轩博客：无外力纳维-斯托克斯奇点与广义黎曼猜想](https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/) ⭐️ 7.0/10

陶哲轩于 2026 年 11 月 20 日发表博客文章，讨论无外力纳维-斯托克斯奇点与广义黎曼猜想；Hacker News 上的相关讨论则集中在 AI 辅助证明验证和 Lean 上。提供的材料没有给出博客正文、证明细节或明确结论，因此无法确认文章是否提出了可验证的完整证明。有评论者链接到 Lean 社区聊天，称两个独立内核接受了相关结果，并认为这降低了内核漏洞导致错误通过的可能性；其他评论则表达了对 AI 快速逼近数学研究能力的担忧。

hackernews · archon1410 · 11月20日 17:21 · [社区讨论](https://news.ycombinator.com/item?id=50578358)

**「背景」** 纳维–斯托克斯存在性与光滑性问题是克雷数学研究所的千禧年大奖难题之一：在三维情形下，给定光滑初值，方程的解是否对任意时间都保持光滑，还是会在有限时间内“爆破”出奇点，至今仍未解决。所谓“无外力”（unforced）版本即把外力项设为零，陶哲轩这篇博文讨论的正是该情形下的奇点问题，并把它与广义黎曼假设联系起来。据 Clarín 报道，同在 11 月 20 日，Levent Alpöge 与 Buckmaster 发布了一篇 79 页、由 Claude 协助完成的论文，声称给出了无外力纳维–斯托克斯方程在有限时间内爆破的结果；该说法尚未在所提供的材料中得到独立验证。

**「形式化验证的边界」** 对使用 Lean 验证数学证明的研究者来说，直接后果是：内核通过并不等于原命题得证，它只确认形式陈述可被推导，不能确认该陈述忠实对应自然语言中的定理。已有论文记录了 AI 将自然语言证明转写为 Lean 时出现错配的案例，包括 OpenAI 公布的 Navier–Stokes 证明，因此评估此类声明时应把形式陈述审查作为独立步骤。

**「社区讨论」** 讨论中最具体的一条是验证层面：有评论者引用 Lean 社区聊天称两个独立内核接受了相关结果，并据此认为内核漏洞导致错误通过的可能性较低；这是评论者说法，材料未独立确认。另有评论者追问 AI 能否创造新的数学抽象，并有人表达了对 AI 研究能力快速提升及科研职业前景的焦虑。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_existence_and_smoothness">Navier – Stokes existence and smoothness - Wikipedia</a></li>
<li><a href="https://www.clarin.com/us-news/who-is-levent-alpoge-the-anthropic-mathematician-who-claims-solved-the-riemann-hypothesis-with-claude_0_2WdGvYKBVM.html">Who is Levent Alpöge? The Anthropic mathematician who claims he...</a></li>
<li><a href="https://explainx.ai/blog/lean-4-formal-proof-cost-collapse-navier-stokes-2026">Lean 4 Formal Proofs: Why OpenAI&#x27;s Cost Collapse Matters ...</a></li>
<li><a href="https://arxiv.org/abs/2610.08144">[2610.08144] Navier-Stokes lost in translation: Why Lean ...</a></li>
<li><a href="https://discoverai.tools/articles/openai-navier-stokes-ai-proof-millennium-problem-2026">OpenAI Navier–Stokes Proof Claim: Verification Status</a></li>

</ul>
</details>

**标签**: `#mathematics`, `#AI-assisted proof`, `#Lean`, `#Navier-Stokes`, `#Riemann Hypothesis`

---

<a id="item-tech-news-4"></a>
### [Inkling 2 Mini：循环架构的开放权重模型](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 7.0/10

Thinking Machines 发布了开放权重模型 Inkling 2 Mini，主打本地可用性；现有信息显示，它采用循环式 Transformer 架构，并在训练中端到端使用 nvfp4。社区早期测试报告称，该模型在 Ryzen 395 上通过 llama.cpp Vulkan 达到约 27 tokens/s，在 32GB M1 Pro 上以 q4 量化运行约 10 tokens/s，但这些数字和基准尚未独立验证。现有材料未提供完整的参数规模、许可证和官方兼容性信息，因此其架构与性能表现仍需进一步确认。

hackernews · jasondavies · 11月20日 20:12 · [社区讨论](https://news.ycombinator.com/item?id=50581260)

**「背景」** Inkling 2 Mini 采用混合专家（MoE）结构，总参数约 260 亿，每个 token 约激活 54 亿；它的“循环”设计通过复用中间层，让同一个 token 获得更多计算，而不是靠生成更多 token 来提升输出。官方发布页称该模型面向笔记本等本地设备，并采用 NVFP4、低位量化以及剪枝与修复等技术。

**「本地部署仍受工具链限制」** 希望本地运行 Inkling 2 Mini 的开发者面临推理框架支持尚未完全就绪的现实：社区测试显示，在 Ryzen 395 上通过 llama.cpp 的 Vulkan 后端可得约 27 token/s，但需先合入尚未合并的 PR（32694、32657、32429、32704），再加一个小补丁才能额外获得约 30% 的提速；M1 Pro（32GB）在 q4 量化下约为 10 token/s。也就是说，这款以本地可用为定位的开放权重模型，当前的实际体验取决于开发者是否愿意跟进上游补丁，而非开箱即用。

**「社区讨论」** 多位评论者认为早期结果值得关注但需要复现：有人报告快速编码测试表现不错，也有人给出上述本地推理速度。另有评论者认为，循环架构若被开放权重模型采用，可能影响后续开放模型设计，并由此提出安全与可解释性方面的疑问；这些仍属社区观点，而非既定结论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://unsloth.ai/docs/models/inkling-2-mini">Inkling 2 Mini - Run Locally Guide | Unsloth Documentation</a></li>
<li><a href="https://ollama.com/library/inkling-2-mini">inkling - 2 - mini</a></li>

</ul>
</details>

**标签**: `#LLM`, `#open-weights`, `#model-release`, `#looped-transformers`, `#local-inference`

---

<a id="item-tech-news-5"></a>
### [语言模型重写自身权重论文遭质疑](https://arxiv.org/abs/2611.21885) ⭐️ 7.0/10

arXiv 预印本 2611.21885 声称，语言模型能靠自身推理直接重写权重，无需梯度或传统训练，并只在练习问题上保留有效编辑。论文还称，连续八次会话中模型准确率持续上升；这些仍是作者主张，尚未经过独立复现。Hacker News 评论则指出，目前展示出的唯一自我修改是缩短推理链以避开 token 上限，因此该工作的实际增益和标题强度受到质疑。

hackernews · lwhsiao · 11月20日 16:29 · [社区讨论](https://news.ycombinator.com/item?id=50577265)

**「背景」** 通常，语言模型训练完成后权重便固定下来；要让它变好，要么再跑一次训练（依赖梯度更新），要么在推理时依赖提示词、外部框架或额外计算，而这些收益在任务结束后就消失了。该论文提出的“自改写”正是针对这一前提：论文摘要称，模型可在推理中直接修改自身权重，无需梯度或训练，并称一个 27B（270 亿参数）模型能诊断自身错误、在未见任务上取得提升。

**「影响」** 对试图复现或评估该工作的研究者而言，关键是把权重编辑带来的收益与缩短推理长度、规避截断的收益分开测量；否则准确率上升不足以证明模型获得了通用的自我改进能力。

**「社区讨论」** 评论者认为，模型唯一的自我改进只是缩短推理链以避开 token 上限，并质疑这与近期权重空间编程工作及 Google 的“sleep”框架相比是否有实质新意。另有评论担心，能自主改写权重的模型可被指示压制与安全对齐相关的激活，构成治理风险。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2611.21885">[2611.21885] Language Models Can Rewrite Their Own Weights</a></li>
<li><a href="https://arxivb.org/abs/2611.21885">Language Models Can Rewrite Their Own Weights</a></li>

</ul>
</details>

**标签**: `#large language models`, `#self-modifying models`, `#weight editing`, `#AI safety`, `#research paper`

---

<a id="item-tech-news-6"></a>
### [Levent Alpöge 声称与 Claude 证明广义黎曼假设](https://alpo.ge/remark.pdf) ⭐️ 7.0/10

2026 年 11 月 20 日，Levent Alpöge 在个人域名发布短文，声称与 Claude 合作发现了黎曼假设的证明，并表示该方法可推广到广义黎曼假设，还称相关论证已在无额外假设的情况下用 Lean 形式化。该声明目前只是作者说法，尚未经过同行评审或独立验证；社区评论称形式化产物约为 1.3GB、1500 万行 Lean 代码。

hackernews · iamronaldo · 11月20日 14:16 · [社区讨论](https://news.ycombinator.com/item?id=50574968)

**「背景」** 黎曼猜想断言黎曼 ζ 函数的非平凡零点都位于临界线 Re\(s\)=1/2 上；广义黎曼猜想把同类断言推广到狄利克雷 L 函数等更广的一类 L 函数。Lean 是交互式定理证明器，能机械检查形式化证明，但检查通过仍取决于定理陈述、公理和代码本身是否被独立核对。据 Unite.AI 报道，Claude 此前的 ζ 零点工作只把一项下界提高到 67.2%，并明确没有证明该猜想；此次 Alpöge 的声明称方法可扩展到 GRH，并称已用 Lean 形式化。

**「影响」** 对 Lean 和形式化验证社区而言，当前最直接的任务是独立复现构建、检查公理依赖，并核对这些形式化陈述是否确实对应黎曼假设与广义黎曼假设；在完成此类检查前，研究者和读者不应把该声明当作已解决的数学结果。

**「社区讨论」** 评论者 Jaxan 指出另有一份据称完全由人类完成的证明，z7 则引用陶哲轩此前对 AI 攻克黎曼假设的怀疑；dawdler-purge 认为多种形式化检查已足以消除疑问，但这些都属于社区说法，不能替代独立确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.unite.ai/levent-alpoges-unverified-riemann-claim-puts-claudes-lean-code-in-focus/">Levent Alpöge’s Unverified Riemann Claim Puts Claude’s Lean ...</a></li>

</ul>
</details>

**标签**: `#formal-verification`, `#lean-proof-assistant`, `#riemann-hypothesis`, `#ai-for-mathematics`, `#unverified-claim`

---

<a id="item-tech-news-7"></a>
### [Signal 试图阻止移动系统 AI 代理读取私聊](https://signal.org/blog/protecting-your-privacy/) ⭐️ 7.0/10

Signal 在博客中表示，正努力阻止移动操作系统中的 AI 代理获取用户数据，尤其是私密聊天内容。现有信息没有说明具体实现方式、覆盖哪些移动平台、何时推出，也没有说明相关防护是否已经生效。因此，这目前更像是对隐私防护方向和进展的说明，而不是可独立验证的已完成能力。

hackernews · dotcoma · 11月20日 09:42 · [社区讨论](https://news.ycombinator.com/item?id=50572348)

**「背景」** 背景是，Android 和 iOS 正在把能分析屏幕内容并代用户操作的系统级 AI 代理纳入操作系统，这使聊天应用面对来自系统层的屏幕读取路径。Signal 在博客中称，其限制措施针对的是这些内置 AI 代理可能抓取并存储 Signal 数据的问题；The Verge 的报道也把该措施描述为 Android 和 iOS 上的截屏限制。

**「对用户的实际影响」** 对普通用户而言，最直接的后果是 Android 与 iOS 上的 Signal 聊天截图将默认受到限制，只有在用户明确授权后，Google Gemini、Apple Siri 等 AI 代理才能读取消息。Signal 把这项措施与此前针对 Microsoft Recall 的截图拦截相提并论，意味着日常截屏留档、向他人展示对话等正当用途也可能一并受限，用户需要留意系统是否给出例外授权的入口。这一保护的效果取决于操作系统层面的截图管控能否真正落实，Signal 目前将其定性为对“生存性威胁”的应对，而非已经封堵全部读取路径。

**「社区讨论」** 有评论者引用 Meredith Whittaker 的访谈称，即使自己没有安装 AI 应用，联系人安装了 AI 应用后，也可能导致聊天内容暴露，因此欢迎 Signal 取得进展；另一些评论则要求 Signal 公开取证调查结果，或直接向用户发出警示，并推荐替代操作系统。上述内容均为社区观点，不能证明当前防护已经有效。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://signal.org/blog/protecting-your-privacy/">Signal &gt;&gt; Blog &gt;&gt; Signal is Serious About Protecting Your Privacy</a></li>
<li><a href="https://www.theverge.com/ai-artificial-intelligence/1038390/signal-blocking-ai-agent-screenshots-mobile-app">Signal is blocking Gemini and Siri AI from reading your... | The Verge</a></li>
<li><a href="https://www.digitaltrends.com/phones/signal-adds-screenshot-protections-to-stop-ai-agents-reading-chats/">Signal is fighting back against AI agents snooping on your ...</a></li>
<li><a href="https://www.reuters.com/legal/litigation/signal-restricts-screenshots-block-ai-agents-reading-messages-2026-11-20/">EXCLUSIVE: Signal restricts screenshots to block AI agents ...</a></li>
<li><a href="https://www.theregister.com/security/2026/11/20/signal-slams-door-on-prying-ai-agents-to-protect-privacy/5311466">Signal slams door on prying AI agents to protect privacy</a></li>

</ul>
</details>

**标签**: `#privacy`, `#AI agents`, `#mobile security`, `#Signal`, `#messaging`

---

<a id="item-tech-news-8"></a>
### [Ravi Vakil 提前公布 Masullo 的广义黎曼猜想证明草稿](https://simonwillison.net/2026/Nov/20/ravi-vakil/) ⭐️ 7.0/10

Ravi Vakil 于 11 月 20 日在博客发布“紧急公告”，称 Alessandro Masullo 已有一份广义黎曼猜想（GRH）的证明草稿，并决定现在就公开当前版本。Vakil 表示，Brian Conrad 已就此仔细审阅数月，给出了大量反馈，这些反馈正在被纳入修改，“目前看起来不错”。他特别强调，这项工作完全由人类完成，没有使用 AI。按原计划，Masullo 本应先到斯坦福待一年打磨写作，并在征询足够多人意见后再公布；现在改为直接放出草稿。这是一份尚未经过验证的提案，而非已获确认的证明。

rss · Simon Willison · 11月20日 19:21

**「背景」** 广义黎曼猜想是黎曼猜想的加强形式：它把关于非平凡零点位于临界线上的断言，从黎曼 ζ 函数推广到更广泛的一类 L 函数，因此被视为更强、更难的目标。此次公告与同期另一项针对原始黎曼猜想的证明声明并存，后者采用了不同路线；Masullo 的这份稿子则被明确说明为完全由人类完成。

**「对关注者的影响」** 草稿提前公开，意味着数学界可以立即着手审查，不必等待原定的打磨和多轮私下征询完成；但 Vakil 的描述本身也说明，写作与同行审阅尚未走完，读者应把这份材料当作待核实的提案，而非可直接引用的结论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.scientificamerican.com/article/dueling-claims-of-riemann-hypothesis-proofs-emerge/">Dueling claims of Riemann hypothesis proofs ... | Scientific American</a></li>
<li><a href="https://www.nytimes.com/2026/11/20/science/anthropic-ai-math-riemann-hypothesis.html">Anthropic Mathematician Claims to Solve Riemann Hypothesis With...</a></li>

</ul>
</details>

**标签**: `#mathematics`, `#Generalized Riemann Hypothesis`, `#research announcement`, `#proof verification`

---

<a id="item-tech-news-9"></a>
### [TikTok 全球上线 AI 深度伪造检测工具](https://www.straitstimes.com/world/tiktok-launches-tool-to-help-public-figures-detect-deepfakes-globally) ⭐️ 7.0/10

TikTok 于 11 月 20 日全球上线 Likeness Detection 工具：经第三方验证身份的公众人物和头部创作者，可在他人未经授权用其形象生成 AI 内容时收到提示并举报。同日上线的透明工具允许任何人在无需账号的情况下上传图片或视频，查询内容是否由 TikTok 的 AI 功能生成。TikTok 称这有助于维护 2027 年欧洲多国选举，欧盟自今年 8 月起已要求标注 AI 内容。上述检测范围和效果来自 TikTok 的说明，来源未提供独立验证。

telegram · zaihuapd · 11月20日 08:14

**「背景：欧盟《人工智能法案》的透明度要求」** 欧盟《人工智能法案》第 50 条是专门针对透明度的条款，其核心义务包括：当 AI 系统与人类交互时必须作出披露，以及必须对 AI 生成的内容进行标注并加上标记，其中也涉及深度伪造内容（tool-2-2、tool-2-3）。该条款还配套一份关于 AI 生成内容透明度的行为准则，用来细化合规路径（tool-2-1）。TikTok 此次推出形象检测功能与公开查询工具，针对的是同一类问题：平台上的内容是否由 AI 生成，以及某个人的形象是否被未经授权地用于生成内容。

**「影响」** 对经第三方验证的公众人物和头部创作者而言，需完成身份验证并选择加入 Likeness Detection，才能收到他人未经授权使用其形象生成 AI 内容的提示并举报。普通用户虽可免账号上传图片或视频查询，但结果仅能说明内容是否由 TikTok 自家 AI 功能生成，无法证明由外部工具制作的深度伪造。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://reliablecontext.com/articles/eu-ai-act-article-50-transparency-marking-synthetic-content">EU AI Act Article 50 : Transparency and AI Content Marking</a></li>
<li><a href="https://prunepad.eu/blog/ai-act-article-50/">AI Act Article 50 in Plain Language | PrunePad Blog</a></li>
<li><a href="https://www.legalithm.com/en/blog/ai-act-transparency-obligations-article-50-deepfake-labeling">AI Act Transparency : Article 50 and Deepfake Rules</a></li>
<li><a href="https://www.straitstimes.com/world/tiktok-launches-tool-to-help-public-figures-detect-deepfakes-globally">TikTok launches deepfake detection tool for public figures ...</a></li>
<li><a href="https://www.euronews.com/2026/11/20/tiktok-rolls-out-deepfake-detection-tool-for-public-figures-to-fight-back-against-disinfor">TikTok rolls out deepfake detection tool for public figures</a></li>

</ul>
</details>

**标签**: `#deepfake detection`, `#AI content provenance`, `#platform policy`, `#TikTok`, `#EU AI regulation`

---

<a id="item-tech-news-10"></a>
### [OpenAI 后台模式上线：最长 8 小时，Token 最多便宜 40%](https://developers.openai.com/api/docs/guides/background) ⭐️ 7.0/10

OpenAI 推出后台模式，将长耗时 API 请求改为异步执行：请求中设置 background: true，并通过 background\_options.completion\_window 选择 2 小时或 8 小时完成时限。按该消息，这两个档位的 Token 费率分别比标准价低 30% 和 40%；不设置完成时限则使用默认的 soonest，且没有折扣。该折扣目前在 GPT-6.2 Astra、GPT-6.2 Sol、GPT-6.1 Terra 和 GPT-6 Luna 上公测。需要注意，后台模式会临时存储响应数据，即使 store 设为 false 或启用零数据保留也不例外。

telegram · zaihuapd · 11月20日 11:15

**「背景」** 后台模式建立在 Responses API 之上：默认请求同步返回结果，调用方要一直等待任务完成；设置 background: true 后，请求会转为异步任务，完成时限则由 background\_options.completion\_window 指定，其中的完成窗口就是拿更长等待换更低 token 费率的调节项。外部指南也指出，2 小时和 8 小时档位并不保证任务一定在该时限内完成，因此需要自行处理排队、失败和乱序完成的情况。另一个使用前提是流式输出只适用于默认的 soonest 窗口，选择 2h 或 8h 时需省略 stream 或将其设为 false。

**「影响」** 使用长任务异步执行的团队不能把 store: false 或零数据保留等同于后台响应完全不落盘；在接入前应确认临时存储的保留期限和合规边界，再决定是否采用 2 小时或 8 小时档。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://developers.openai.com/api/docs/guides/background">Background mode | OpenAI API</a></li>
<li><a href="https://www.aifeaturedrop.com/2026/11/openai-background-mode-guide-2-hour-and.html">OpenAI Background Mode Guide: 2-Hour and 8-Hour Completion ...</a></li>

</ul>
</details>

**标签**: `#OpenAI API`, `#async processing`, `#API pricing`, `#data retention`, `#long-running tasks`

---

<a id="item-tech-news-11"></a>
### [台积电暂停对中国企业 16nm 及以下芯片订单](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 7.0/10

据报道，台积电已通知客户暂停承接中国公司 16nm 及以下先进制程订单；按照收紧后的美国半导体出口新规，除非事先取得美国出口许可或豁免，否则不得供货。台积电表示将遵守新规。此前台积电可自行评估客户设计是否符合豁免条件，现在则须由客户提前申请；美国获批名单中包括苹果、AMD 和英伟达，尚无中国公司。受影响的中国企业因此只能使用 28nm、40nm 等旧制程，也无法获得 AI 数据中心所需的高带宽内存。该消息源自简短转述，未附台积电原始公告或独立核实。

telegram · zaihuapd · 11月21日 02:01

**「背景」** 美国半导体出口管制通过许可证和豁免清单限定先进制程的供货对象，代工厂在接单前必须核验客户设计是否合规。此前台积电可自行评估客户设计是否符合豁免条件，新规要求客户提前申请，审批环节因此前移到接单之前。

**「客户影响」** 对中国芯片设计公司而言，供货前提从“台积电自行评估客户设计是否符合豁免条件”变为“客户须事先取得美国出口许可或豁免”，未获批的订单只能退回 28nm、40nm 等成熟制程，相关产品需要重新设计或转投其他代工产能。据路透社与 TrendForce 报道，此次暂停的范围可能不限于 AI 处理器，还波及部分消费电子芯片的出货，受影响的可能不只是大型 AI 芯片厂商。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/world/china/tsmc-tightens-china-ai-chip-curbs-new-us-rules-close-manufacturing-loophole-2026-11-19/">TSMC tightens China AI chip curbs as new US rules close ...</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/20/news-tsmc-samsung-reportedly-pause-china-consumer-chip-shipments-under-new-u-s-rules-16nm-orders-affected/">[News] TSMC, Samsung Reportedly Pause China Consumer Chip ...</a></li>

</ul>
</details>

**标签**: `#TSMC`, `#semiconductor supply chain`, `#US export controls`, `#China tech`, `#AI chips`

---