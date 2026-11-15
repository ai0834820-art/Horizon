---
layout: default
title: "Horizon Summary: 2026-11-15 (ZH)"
date: 2026-11-15
lang: zh
---

> 从 37 条内容中筛选出 7 条重要资讯。

---

**科技新闻**
1. [Lovable 应用因 RLS 不足泄露护照信息与逾 20 万条私信](#item-tech-news-1) ⭐️ 8.0/10
2. [EFF 指科技公司再次试图改写隐私概念](#item-tech-news-2) ⭐️ 7.0/10
3. [Project Zero 漏洞披露窗口将逐步缩短至 30 天](#item-tech-news-3) ⭐️ 7.0/10
4. [约 200 行纯 JAX 实现 DeepSeek V3 推理](#item-tech-news-4) ⭐️ 7.0/10
5. [Cloudflare 开源无状态 AI 代理浏览器 Kitesurf](#item-tech-news-5) ⭐️ 7.0/10
6. [意大利因 Meta 违规读取相册罚款 8.05 亿欧元](#item-tech-news-6) ⭐️ 7.0/10
7. [FAA 全国停飞：换光纤升级引发路由故障](#item-tech-news-7) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Lovable 应用因 RLS 不足泄露护照信息与逾 20 万条私信](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

一份安全研究报告称，部分由 Lovable 构建的应用因行级安全（RLS）配置不足，泄露了护照详细信息和超过 20 万条私人消息。Lovable 安全负责人 Igor 回应称，根因是这些应用的 RLS 不足；平台会在发布前自动扫描每个应用，向所有用户免费提供更深入的 SAST 扫描，并允许用户选择“Fix”或启用后台自动修复。上述修复能力是厂商陈述，尚不能等同于独立验证。

hackernews · armcat · 11月14日 17:43 · [社区讨论](https://news.ycombinator.com/item?id=50499017)

**「背景」** Supabase 是托管式 Postgres 开发平台，应用无需自建数据库即可直接使用其数据库服务。Postgres 的 Row-Level Security（RLS）用于按用户限制可访问的数据行；当 Lovable 生成的应用未正确启用 RLS 或策略过宽时，公开前端所调用的数据库接口就可能返回本应受保护的记录，这正是此次护照信息和私信泄露报告所指向的配置问题。

**「影响」** 对使用 Lovable 生成并直接上线应用的用户而言，护照等敏感数据一旦进入未正确启用 RLS 的表，就可能通过浏览器的网络请求被读取；上线前应核查 RLS 策略，并对公开表做未授权访问测试。

**「社区讨论」** 评论者把部分责任归向 Supabase：有人指出其默认设置据称已于 10 月 30 日修复，但有报告称现有项目可能仍沿用旧默认值，Lovable 也应承担责任。另有评论认为，AI 生成应用数量多且攻击门槛低，平台应采用默认拒绝的数据库、最小权限 API 和自动化授权测试等更安全的默认设置。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/supabase/supabase">GitHub - supabase / supabase : The Postgres development platform. ...</a></li>

</ul>
</details>

**标签**: `#security`, `#vulnerabilities`, `#Supabase`, `#AI code generation`, `#privacy`

---

<a id="item-tech-news-2"></a>
### [EFF 指科技公司再次试图改写隐私概念](https://www.eff.org/deeplinks/2026/11/tech-companies-are-trying-shift-entire-concept-privacy-again) ⭐️ 7.0/10

EFF 发文批评科技公司再次试图重新定义隐私概念，并将这一趋势与 AI 会议记录工具、职场监控和数字权利议题联系起来。该文属于倡导性分析，并非发布新产品或披露具体技术突破；由于提供的材料没有原文正文，文中具体论据和案例无法进一步核实。对读者而言，最直接的问题是 AI 记录工具进入日常会议后，参与者如何在继续工作的同时避免被转录和留存。

hackernews · gslin · 11月14日 12:45 · [社区讨论](https://news.ycombinator.com/item?id=50496602)

**「背景」** 这篇 EFF 文章把争议放在一组具体产品变化之上：Meta 和 Google 的智能眼镜可录制佩戴者所见并用 AI 描述画面，Apple 的 Audio Intelligence 把 Apple Watch 变成转录设备，Amazon 的 Bee 设备可录制并转写环境声音。EFF 的 Thorin Klosowski 据此认为，隐私问题正从个人是否选择使用设备，转向旁人在不知情中被记录。

**「对参会者与无障碍用户的影响」** 对职场参会者来说，直接后果是录音与转写往往默认开启，而在不丢掉工作的前提下拒绝参加几乎不可行；评论中提出的具体做法，是在会议开始前明确要求关闭 AI 记录员，把“本次会议不需要转写”变成常规请求。对听障等依赖实时转写的用户，同一套技术又是实际可用的无障碍工具。讨论指出，若采用本地模型、不上传也不导出，功能与留存风险之间常常只差一行代码，因此争议焦点更适合放在音频在哪里处理、由谁保存，而不是笼统禁用设备。一家厂商的博文称约四分之三的专业人士已在工作会议中使用 AI 记录工具，若该数字成立，逐个会议协商关闭将成为普遍负担。

**「社区讨论」** 评论中，toddmorey 描述专业会议普遍被 AI 记录且难以退出，询问能否把“本次会议无需转录”变成规范；abecedarius 则强调实时转录对聋人及听障者的可及性价值，并指出本地处理与数据留存之间只差一个开关。另有评论引用《世界人权宣言》第 12 条，讨论隐私不应受到任意干涉。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aiweekly.my/items/46520/tech-companies-are-trying-to-shift-the-concept-of-privacy-again">Tech Companies Are Trying to Shift the Concept of Privacy (Again )</a></li>
<li><a href="https://fellow.ai/blog/ai-notetaker-statistics/">The State of AI Meeting Notetakers 2025 : Why Privacy and Security...</a></li>

</ul>
</details>

**标签**: `#privacy`, `#AI notetakers`, `#digital rights`, `#workplace surveillance`, `#tech policy`

---

<a id="item-tech-news-3"></a>
### [Project Zero 漏洞披露窗口将逐步缩短至 30 天](https://projectzero.google/2026/11/disclosure-policy.html) ⭐️ 7.0/10

据分析摘要及评论中引述的公告，Google Project Zero 将把漏洞披露窗口设为向厂商报告后 90 天，即“Full 90”，并计划在 2027 年 2 月 2 日改为 60 天、2028 年 1 月 3 日改为 30 天。评论中引述的公告称新政策即日起生效，后续窗口将分阶段缩短。由于原始公告页面内容未提供，上述时间表来自二手引述，属于已宣布的分阶段计划，而非已经全部执行的披露结果。

hackernews · hacb · 11月14日 11:13 · [社区讨论](https://news.ycombinator.com/item?id=50496051)

**「此前的 90+30 政策」** Project Zero 长期执行“90+30”漏洞披露政策：厂商在收到详细技术报告后有 90 天时间向用户提供补丁，另有 30 天缓冲期供用户升级，逾期则公开漏洞细节（tool-2-1、tool-2-3）。按这一口径，公告中的“Full 90”取消了额外的 30 天宽限，把公开时点固定在报告后 90 天，并按计划于 2027 年 2 月收紧到 60 天、2028 年 1 月收紧到 30 天。

**「影响」** 对需要较长修复周期的厂商和开源发行版，最终 30 天窗口会显著压缩从收到报告到发布补丁的时间；维护者需提前准备分级响应、回移植和安全公告流程，否则可能在漏洞公开时仍无可用修复。

**「社区讨论」** 评论中，有用户认为 Ubuntu 等开源发行版需要远多于 90 天的修复时间；也有人主张应尽快甚至立即公开漏洞，认为披露压力才是促使厂商修复的关键。上述均为评论者观点，不代表已形成的共识。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://googleprojectzero.blogspot.com/p/vulnerability-disclosure-policy.html">Project Zero : Vulnerability Disclosure Policy</a></li>
<li><a href="https://www.escoffer.com/2025/08/16/google-tightens-security-timelines-through-faster-alerts/">Google Tightens Security Timelines Through Faster Alerts</a></li>

</ul>
</details>

**标签**: `#vulnerability disclosure`, `#Project Zero`, `#security policy`, `#open source maintenance`, `#Google`

---

<a id="item-tech-news-4"></a>
### [约 200 行纯 JAX 实现 DeepSeek V3 推理](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 7.0/10

VaibhaavTiwari 在 Show HN 发布了 deepseek-v3-jax：用约 200 行纯 JAX 代码实现 DeepSeek V3 推理，定位为便于阅读和动手学习的紧凑参考实现，而不是生产级推理框架。现有介绍称它可在 ROCm 硬件上运行；一位使用 RX 7600 XT 16GB 的评论者报告，这是其 Fedora + ROCm 环境中首个端到端跑通的项目，并称需要设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等环境变量。当前材料未提供独立基准或完整源码内容，因此性能、显存占用和更广泛的硬件兼容性仍未得到验证。

hackernews · VaibhaavTiwari · 11月14日 15:04 · [社区讨论](https://news.ycombinator.com/item?id=50497589)

**「背景」** DeepSeek V3 是 DeepSeek 推出的大模型，而 DeepSeek 以开源前沿 LLM 著称。JAX 能把 NumPy 风格的数值计算编译到 GPU 等加速器，并可借助插件支持 AMD ROCm；因此，一份约 200 行的从零推理实现既可作为逐行阅读的教学材料，也为没有 CUDA 环境的 AMD 用户提供了可尝试的路径。

**「影响」** 对想在 AMD 消费级 GPU 上尝试 DeepSeek V3 推理的开发者，一位 RX 7600 XT 16GB 用户的成功案例表明该项目可作为最小起点；复现时需按提示设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等 ROCm 兼容变量，并预期不同显卡与驱动组合仍需额外调试。

**「社区讨论」** 有评论者称赞从第一性原理重建模型有助于理解推理，并有人询问适合 Java/Python 背景开发者的学习路线；另一位 RX 7600 XT 16GB 用户报告在 Fedora + ROCm 上端到端跑通，同时指出需要设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等环境变量。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.deepseek.com/">DeepSeek | Into the Unknown</a></li>

</ul>
</details>

**标签**: `#JAX`, `#DeepSeek V3`, `#LLM inference`, `#model reimplementation`, `#ROCm`

---

<a id="item-tech-news-5"></a>
### [Cloudflare 开源无状态 AI 代理浏览器 Kitesurf](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare 已以 Apache 2.0 许可证开源面向 AI 代理的无状态浏览器 Kitesurf，代码发布在 GitHub。它基于 Cloudflare Workers 构建，无需浏览器容器即可解析 HTML、处理 CSS 并执行 JavaScript。Cloudflare 表示，其目标是让 AI 代理以比 Chromium 更少的 CPU 和内存开销运行，并可在全球 Workers 网络上按需扩展；但此次简讯未给出独立基准或具体性能数据。

telegram · zaihuapd · 11月14日 09:33

**「背景」** 传统 AI 代理浏览器通常依赖 Chromium 等浏览器容器来渲染网页；Kitesurf 的不同点在于，它把 HTML 解析、CSS 处理和 JavaScript 执行放在 Cloudflare Workers 的无状态运行时上，因此无需浏览器容器。这一架构也解释了 Cloudflare 为何宣称其 CPU 和内存占用更低、可在全球 Workers 网络上按需扩展，但这些目前仍是厂商说法。

**「对开发者的影响」** 对需要在边缘批量抓取或操作网页的开发者而言，Kitesurf 可省去自建 Chromium 容器，并在 Workers 上按请求扩展，适合突发、一次性的浏览任务；它也可在 Cloudflare Browser Run 中与 Chromium 并列选用。由于该引擎并非基于 Chromium，迁移前应针对依赖 Chromium 特有行为的页面做兼容性测试，必要时保留 Chromium 作为回退。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://agentpedia.codes/blog/cloudflare-kitesurf-agent-browser-guide">Cloudflare Kitesurf : Agent -First Browser Guide</a></li>
<li><a href="https://groundingpage.com/facts/kitesurf/">Kitesurf : Cloudflare &#x27;s Browser Engine for AI Agents in Browser Run</a></li>
<li><a href="https://www.eesel.ai/blog/cloudflare-kitesurf">Cloudflare Kitesurf : the agent browser that trades speed... | eesel AI</a></li>

</ul>
</details>

**标签**: `#Cloudflare`, `#AI agents`, `#browser automation`, `#open source`, `#Cloudflare Workers`

---

<a id="item-tech-news-6"></a>
### [意大利因 Meta 违规读取相册罚款 8.05 亿欧元](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/10321080) ⭐️ 7.0/10

意大利隐私监管机构 Garante Privacy 对 Meta 处以 8.05 亿欧元罚款，原因是 Facebook 的 Android 应用在未取得具体同意的情况下读取了约 2000 万意大利用户的相册照片、视频及元数据。处罚针对 2023 年上线的相册推荐功能：该功能默认开启，授权提示笼统。Meta 须在 60 天内将功能改为默认关闭并单独征得用户同意，否则不得对未有效授权的用户启用该功能。

telegram · zaihuapd · 11月14日 14:37

**「背景」** 争议功能是 2023 年上线的相册推荐，默认开启，授权提示被监管机构认定为笼统。这里的“具体同意”要求用户能明确知道 Facebook Android 应用会读取相册中的照片、视频及元数据，而不是用一次宽泛授权覆盖该行为。此次处罚即针对这一默认设置和同意机制，并要求在 60 天内整改。

**「实际影响」** Meta 需要在 60 天内重新设计该功能的默认设置和同意流程；若未完成整改，相册推荐功能必须对未有效授权的意大利用户停用，这将直接改变当地约 2000 万 Android 用户的相册访问与推荐体验。

**标签**: `#隐私监管`, `#Meta`, `#用户同意`, `#Android应用`, `#科技行业`

---

<a id="item-tech-news-7"></a>
### [FAA 全国停飞：换光纤升级引发路由故障](https://www.theverge.com/transportation/1033898/faa-ground-stop-sean-duffy-faa-copper-wire) ⭐️ 7.0/10

美国交通部长 Sean Duffy 11 月 14 日表示，周五 FAA 下令的全国停飞源于一处偏远设施将老旧铜线更换为光纤的例行维护，新装路由器随后发生故障，导致数千架航班停飞。该路由器每 4 至 5 秒向其他路由器发出逾千次连接请求，干扰了雷达信号和飞机通信。Duffy 称根因仍未确定，可能是硬件故障、配置错误或承包商 L3Harris 的失误，并呼吁国会追加空管现代化资金。

telegram · zaihuapd · 11月15日 02:10

**「背景」** 涉事承包商 L3Harris 长期参与 FAA 通信网络：CBS 报道称，FAA 早在 2002 年 7 月就把现代化、运营和管理该网络的合同授予其前身 Harris Corp.；AIN 还报道，L3Harris 获得新合同，将升级 700 多个 FAA 地面站并运营全国飞机跟踪网络至 2045 年。这说明此次铜线换光纤的例行升级，发生在一个由长期承包商维护的既有全国性网络之中。

**「影响」** 此次故障已导致数千架航班停飞，并把追加空管现代化资金的请求推到国会面前；在根因确认前，FAA 无法排除同类路由器升级再次干扰雷达和通信。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cbsnews.com/news/faa-issues-nationwide-ground-stop/">FAA lifts nationwide ground stop that disrupted thousands... - CBS News</a></li>
<li><a href="https://www.ainonline.com/aviation-news/air-transport/2026-06-01/faa-dashboard-provides-view-atc-modernization">FAA Dashboard Provides View into ATC Modernization | Aviation ...</a></li>

</ul>
</details>

**标签**: `#FAA`, `#network outage`, `#router failure`, `#critical infrastructure`, `#aviation`

---