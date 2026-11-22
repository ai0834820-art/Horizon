---
layout: default
title: "Horizon Summary: 2026-11-22 (ZH)"
date: 2026-11-22
lang: zh
---

> 从 22 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [黎曼猜想 Lean 形式化证明获多方认证](#item-tech-news-1) ⭐️ 9.0/10
2. [浙江大学在“天目 2 号”芯片实现 QRAM 真机原型](#item-tech-news-2) ⭐️ 8.0/10
3. [显示器 USB 以太网接口导致下载速度下降 75%](#item-tech-news-3) ⭐️ 7.0/10
4. [GPGME 漏洞被指为双重释放而非已证实 RCE](#item-tech-news-4) ⭐️ 7.0/10
5. [Muru：面向 ASGI/WSGI 的 AI 辅助 Rust 服务器](#item-tech-news-5) ⭐️ 7.0/10
6. [微软预览 USB4 RDMA：多台 Windows PC 合跑一个模型](#item-tech-news-6) ⭐️ 7.0/10
7. [OpenRouter 警告 MiniMax 提示词疑遭第三方读取](#item-tech-news-7) ⭐️ 7.0/10
8. [特斯拉海外推送 FSD v15 与 Reality View](#item-tech-news-8) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [黎曼猜想 Lean 形式化证明获多方认证](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) ⭐️ 9.0/10

据条目所附摘要，Levent Alpöge 于 2026 年 11 月 20 日发布黎曼猜想的 Lean 形式化证明（代码库约 1700 万行），直接影响 Lean/Mathlib 用户与形式化数学研究者；次日 Lean FRO 与 Mathlib Initiative 联合声明称命题和证明均正确。同一摘要称，社区确认该命题与 Mathlib 的 RiemannHypothesis 一致、代码库可无错编译，并称多个独立证明检查器验证了证明有效。但条目未提供原始来源内容，上述认证细节无法独立核对，证明本身及各检查器独立性的关键条件仍不完整。

hackernews · g-b-r · 11月21日 14:36 · [社区讨论](https://news.ycombinator.com/item?id=50589618)

**「背景」** Lean 是一个用于机器检验数学证明的证明助手，Mathlib 是其社区维护的数学库。据 Lean 与 Mathlib 社区的联合声明，黎曼猜想的陈述此前已作为 Mathlib 中的 RiemannHypothesis 存在，并由 Lean 与数论专家审校；因此这次要检验的是为既有陈述提供的证明代码，而不是另起一套猜想表述。

**「对复用者的影响」** 如果该验证成立，想要复用这一结果的形式化开发者当前能核验的产物是随 Lean v4.36.0 打包的 con-leche、con-ron 所检查的 solution.ndjson 导出文件，而不是仓库源码；相关验证页面建议在不同构建之间比对该文件的哈希，并指出尚未确认导出格式能否携带源码路径。因此，下游如果要依赖这一结论，应固定 Lean 版本和导出文件哈希，并保留人工复核命题陈述这一环节，因为评论提到该陈述包含 4 个要点；有评论还提到，此前已有虚假的 Collatz 反证通过某个独立检查器，所以仅凭多个检查器都通过，不足以排除它们存在共同缺陷。

**「社区讨论」** 评论区的核心分歧在检查器可信度：rcr-anti 认为多个实现及各自的一致性证明使“利用漏洞”的概率极低，而 thejokeisonme 指出此前已有假 Collatz 反证通过某个独立检查器、独立性被高估，不过本次有人类专家在环；killerstorm 则称 Claude 为证明形式化了大量现代数学，认为其意义超出黎曼猜想本身。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://leanprover-community.github.io/blog/posts/riemann-hypothesis/">Lean verification of the Riemann Hypothesis | Lean community blog</a></li>
<li><a href="https://news.ycombinator.com/item?id=50589618">Lean verification of the Riemann Hypothesis | Hacker News</a></li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof : verification files</a></li>
<li><a href="https://news.ycombinator.com/item?id=50589618">Lean verification of the Riemann Hypothesis | Hacker News</a></li>

</ul>
</details>

**标签**: `#Lean theorem prover`, `#Riemann Hypothesis`, `#formal verification`, `#AI-assisted mathematics`, `#proof assistants`

---

<a id="item-tech-news-2"></a>
### [浙江大学在“天目 2 号”芯片实现 QRAM 真机原型](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 8.0/10

据新浪财经报道，浙江大学团队称在自主制备的超导量子芯片“天目 2 号”上完成全球首次 QRAM 真机实现，并运行了可调取 4 位和 8 位数据的原型；相关成果据称发表于《自然·物理》。该原型在 4 位和 8 位数据调取上的准确率分别为 80.9% 和 60.4%，线路深度较未优化方案降低 30% 以上，并首次验证该架构具备局部抗噪特性。团队下一步将推进 QRAM 的规模化研究。

telegram · zaihuapd · 11月21日 08:31

**「背景：QRAM 与「天目 2 号」」** 量子随机存储器（QRAM）被设想为量子计算机的「内存」：它以量子叠加态的地址并行读取数据，是许多量子算法所需的存储组件。按浙江大学团队的说法，此前 QRAM 尚未在真实硬件上完整实现，相关工作多停留在方案设计与小规模验证层面。本次实验所用的「天目 2 号」，是浙江大学超导量子计算团队与杭州逻辑比特科技联合研制的 100 比特超导量子芯片，它为这次真机演示提供了硬件平台。

**「影响」** 对量子算法与硬件研究者而言，这一原型提供了在超导平台上以较浅线路运行 QRAM 并利用局部抗噪性的可测试方案；但 8 位检索 60.4% 的准确率表明它尚不能承担高保真读取任务，规模化与纠错将是提升可用性的前提。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://baike.baidu.com/en/item/Tianmu-2/4929794">Tianmu-2_Baiduwiki - 百度百科</a></li>

</ul>
</details>

**标签**: `#quantum computing`, `#QRAM`, `#superconducting qubits`, `#quantum hardware`, `#research`

---

<a id="item-tech-news-3"></a>
### [显示器 USB 以太网接口导致下载速度下降 75%](https://blog.tymscar.com/posts/studiodisplayethernet/) ⭐️ 7.0/10

一位用户报告，其下载速度下降 75% 的问题可追溯到显示器内置的 USB 以太网集线器，而非网络线路本身。问题不在链路标称带宽，而在于数据包经显示器转发后增加的延迟：笔记本无法及时确认收到的数据包，以太网适配器缓冲区被填满并开始丢包。换用确认频率更低的适配器后，问题消失。该结论来自作者的个人排查，尚非独立复现的受控测试。

hackernews · soheilpro · 11月21日 10:36 · [社区讨论](https://news.ycombinator.com/item?id=50587875)

**「背景：USB Hub 与 TCP 确认延迟」** 理解这类问题需要知道，显示器或扩展坞上的以太网口通常接在内部 USB Hub 后面，并非主板直连网卡；主机侧 USB 轮询、Hub 多路复用和链路管理都会增加往返延迟。高速 TCP 下载依赖接收端及时回 ACK，延迟升高会让以太网适配器缓冲区积压，填满后丢包并触发拥塞控制退避，吞吐量因此大幅下降。原帖的排查和读者讨论都指向这条 USB 网络路径，而非显示器的显示功能。

**「实际影响」** 对使用显示器或扩展坞内置 USB 网卡的用户而言，这说明链路速率显示正常并不代表实际吞吐正常；排查吞吐异常时，应绕过集线器直连或换用其他适配器，以区分延迟导致的丢包与带宽不足。

**「社区讨论」** 评论中对问题定性存在分歧：有人主张应写成“USB 网络交换机”而非显示器，因为显示器本身并非关键；也有人澄清真正原因是经显示器增加的延迟导致确认不及时和缓冲区丢包。另有评论者报告在 MacBook 与 Thunderbolt 扩展坞上断断续续遇到类似问题一年多，并称启用流控后情况可接受，还有人将其类比为 Ghostty 的 io\_uring 被误判为 I/O 压力的案例。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://news.ycombinator.com/item?id=50587875">My monitor was cutting my download speed by 75 % | Hacker News</a></li>
<li>My monitor was cutting my download speed by 75% | Hacker News</li>

</ul>
</details>

**标签**: `#usb`, `#networking`, `#hardware-debugging`, `#ethernet`, `#latency`

---

<a id="item-tech-news-4"></a>
### [GPGME 漏洞被指为双重释放而非已证实 RCE](https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html) ⭐️ 7.0/10

据社区披露信息，GPGME 的一个安全缺陷于 2026 年 11 月 20 日公开，影响以共享库、DLL 或静态链接方式使用 2.3.0 之前版本的应用，涉及邮件客户端、XMPP 客户端、Samba、Gpg4win 等集成方。公告标题称其为 RCE，但讨论指出该缺陷是双重释放（double-free），并非已展示的远程代码执行链，实际可利用性取决于具体调用路径。相关方称漏洞由 Johan Carlsson 发现，原定 11 月 25 日协调披露，因 Ruby2Shell 漏洞提前至 11 月 20 日。

hackernews · gdgghhhhh · 11月21日 08:32 · [社区讨论](https://news.ycombinator.com/item?id=50587208)

**「背景」** GPGME（GnuPG Made Easy）是让邮件客户端、签名工具等第三方程序接入 GnuPG 加密与签名能力的集成库；此次披露的漏洞编号为 CVE-2026-129975，影响所有使用 2.3.0 之前版本 GPGME 的软件，无论该库以共享库、Windows DLL 还是静态链接方式引入。上游公告称漏洞由 Johan Carlsson 发现，GitLab 于 2026-11-12 通知 GnuPG 项目，这一时间线意味着受影响范围需要沿依赖链向下游应用排查。

**「受影响范围与处置」** 所有以动态库、DLL 或静态链接方式使用 2.3.0 之前版本 GPGME 的软件都受影响，包括 Gpg4win、多数邮件客户端、许多 XMPP 客户端、Samba，以及支持签名提交的 GitLab；GnuPG 公告称，攻击者可通过超长的 OpenPGP 用户 ID 触发双重释放，从而从应用中窃取数据，且不能排除进一步构成 RCE。Corgea 的研究指出，截至 11 月 21 日 GitLab master 仍在构建 GPGME 2.2.0，仅靠输入校验临时防护，这说明下游打包滞后会延长暴露窗口；维护者应确认所依赖的 GPGME 已升级到 2.3.0。

**「社区讨论」** 评论中最集中的异议是公告标题夸大了影响：mik1998 认为这是双重释放缺陷而非已实现的 RCE 链；uptrails 称 Red Hat 五年前已根据常规工具输出修复，但上游遗漏了该修复。wannabe44 列举邮件、XMPP、Samba、Gpg4win 等 GPGME 集成场景，并询问 apt 等是否不受影响，讨论中未见统一确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via...</a></li>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME ...</a></li>
<li><a href="https://techora.ru/news/v-gpgme-kriticheskaya-uyazvimost-utechka-dannykh-2026-11-21">В GPGME критическая уязвимость: утечка данных и RCE для...</a></li>
<li><a href="https://lists.gnu.org/archive/html/info-gnu/2026-11/msg00006.html">GnuPG Security Advisory for GPGME (T8557,CVE-2026-129975)</a></li>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via ...</a></li>
<li><a href="https://corgea.com/research/cve-2026-129975-gpgme-double-free-long-openpgp-user-id-november-2026">GPGME double free via long OpenPGP user IDs (CVE-2026-129975)</a></li>

</ul>
</details>

**标签**: `#GPGME`, `#GnuPG`, `#security vulnerability`, `#double-free`, `#open source`

---

<a id="item-tech-news-5"></a>
### [Muru：面向 ASGI/WSGI 的 AI 辅助 Rust 服务器](https://simonwillison.net/2026/Nov/21/muru/) ⭐️ 7.0/10

曾创建 mod\_wsgi 的 Graham Dumpleton 发布了 Muru：一个借助 AI 开发的 Rust 服务器，目标是在开发和部署环境中运行 ASGI 与 WSGI Python 应用。Simon Willison 在 11 月 21 日的链接博客中推介了该项目，并指出 Dumpleton 在最近三周内发布了 18 篇开发记录，涵盖 worker、开发期 HTTPS、WSGI 与 ASGI 共存、发布不重启、金丝雀发布、Kubernetes 集成、缩容到零和页面工具栏等设计。现有材料只有项目说明与作者自述，未给出性能基准、版本号、采用情况或独立评测，因此它目前是一个值得关注的新服务器，而非已验证的生产替代方案。

rss · Simon Willison · 11月21日 23:56

**「背景」** Graham Dumpleton 20 年前启动了 mod\_wsgi，此后一直关注 Python Web 应用在生产环境中的服务方式。Muru 是他用 Rust 编写、并以 AI 辅助开发的新服务器，目标同时覆盖 ASGI 和 WSGI 应用的开发与生产运行；他此前也在 wrapture 项目中采用过边开发边公开发布详细记录的做法。

**「影响」** 对维护 Python Web 部署的团队来说，Muru 公开设计中的 WSGI 与 ASGI 共存、容器内缩容到零和 Kubernetes 集成值得跟进评估；但在缺少版本、基准和独立评测的情况下，现阶段不宜将其作为生产迁移依据。

**标签**: `#Python`, `#ASGI/WSGI`, `#Rust`, `#web servers`, `#open source`

---

<a id="item-tech-news-6"></a>
### [微软预览 USB4 RDMA：多台 Windows PC 合跑一个模型](https://videocardz.com/newz/microsoft-brings-rdma-over-usb4-to-windows-allowing-multiple-pcs-to-run-one-local-ai-model) ⭐️ 7.0/10

微软发布了 Windows 的 RDMA over USB4 开发者预览，让多台 PC 通过普通 USB4 连接共享内存和 GPU 算力，运行同一个本地 AI 模型，无需专用网卡或交换机。现有演示用三台搭载 AMD Ryzen AI Max+ 395 的机器，以 4-bit 量化运行 Qwen3-235B-A22B，速度约为 18.5 token/s；该预览将通过 Windows Insider 推送。上述信息来自二手报道，所给材料未提供兼容性、延迟或安全隔离等细节，18.5 token/s 也不是独立实测结果。

telegram · zaihuapd · 11月21日 06:13

**「背景：RDMA 与 USB4」** RDMA（远程直接内存访问）让一台计算机直接访问另一台计算机的内存，而不经过普通网络协议栈；这类能力过去主要依赖专用网卡和交换机等数据中心网络设备。微软此次把 RDMA 构建在 USB4 连接之上，使多台 Windows PC 能合并内存容量与 GPU 资源来运行单机放不下的模型，目前该功能仍处于开发者预览阶段。

**「影响」** 对开发者而言，这提供了用现有 USB4 接口尝试聚合多台 Windows 机器的内存和 GPU 资源、运行本地大模型的方式，不必先采购专用网络设备；但作为开发者预览，评估需 Windows Insider 环境和兼容的 USB4 硬件，公开信息也未说明支持的拓扑、驱动和安全要求，暂不适合直接用于生产部署。

<details><summary>参考链接</summary>
<ul>
<li>Introducing RDMA over USB4® on Windows: run larger local AI models across PCs</li>
<li>Tag:&quot;rdma&quot; - Microsoft Community Hub</li>

</ul>
</details>

**标签**: `#RDMA`, `#USB4`, `#local AI inference`, `#Windows`, `#distributed computing`

---

<a id="item-tech-news-7"></a>
### [OpenRouter 警告 MiniMax 提示词疑遭第三方读取](https://news.ycombinator.com/item?id=50585962) ⭐️ 7.0/10

OpenRouter 通过邮件通知用户，发往 MiniMax 模型的请求内容可能已被第三方读取，并已下架相关端点的“零数据保留”标签。通知将问题指向 MiniMax 及其转发方 AtlasCloud、Novita 和 StreamLake；安全研究者在 2026 年 7 月至 10 月发送含测试 URL 的提示词后，这些 URL 在 40 至 130 小时后被第三方访问。OpenRouter 建议涉及敏感凭证的用户更换 API Key 和密码；但相关信息经 Telegram 转述，OpenRouter 官网尚未发布公告，事件范围和影响仍未获官方确认。

telegram · zaihuapd · 11月21日 06:53

**「背景」** 零数据保留（ZDR）标签通常表示上游托管方不会保存用户提示词。据 Privacy Affairs 的报道，OpenRouter 上的该标签由上游提供商传递，而不是由路由平台自行生成的数据处理承诺。

**「对开发者的影响」** 使用 OpenRouter 调用 MiniMax 模型的开发者应立即把相关端点视为不再具备零数据保留保障，并更换曾在提示词中暴露的 API Key、密码等敏感凭证。该限制同时适用于直连 MiniMax 和经由 AtlasCloud、Novita、StreamLake 转发的请求；在 OpenRouter 完成调查并恢复标签前，敏感或受合规约束的请求应改走其他端点。

<details><summary>参考链接</summary>
<ul>
<li>OpenRouter Warns Prompts Sent to MiniMax Models May Have Been Read - Privacy Affairs</li>
<li><a href="https://www.hallattorneys.com/investigations/openrouter-minimax">OpenRouter MiniMax Prompt Exposure Investigation - Hall Attorneys</a></li>
<li><a href="https://www.siliconreport.com/openrouter-drops-minimax-retention-label-over-leak-research">OpenRouter drops MiniMax retention label over leak research</a></li>
<li><a href="https://startupfortune.com/openrouter-warns-minimax-prompts-may-have-been-read-by-a-third-party/">OpenRouter warns MiniMax prompts may have been read by a ...</a></li>

</ul>
</details>

**标签**: `#AI security`, `#data privacy`, `#API providers`, `#OpenRouter`, `#MiniMax`

---

<a id="item-tech-news-8"></a>
### [特斯拉海外推送 FSD v15 与 Reality View](https://x.com/Tesla/status/2124222447855743019) ⭐️ 7.0/10

特斯拉已开始在海外推送 FSD v15。更新引入“Tesla Reality View”可视化界面，可在车机屏幕叠加摄像头画面与 FSD 行驶规划，并支持全屏、地图、分屏视图和安静模式。导航会把转弯等信息叠加显示，转向灯提示音更轻柔且逐渐减弱；更新还称优化了坑洼、碎片等路况的行驶体验，以及学校、恶劣天气下的速度控制。特斯拉宣称本次更新将安全关键场景处理能力提升至 25 倍，但该说法来自其社交账号的简短发布，尚无独立验证或技术细节。

telegram · zaihuapd · 11月22日 00:03

**「背景」** 特斯拉的 FSD 以端到端驾驶网络为核心；特斯拉在 v15 介绍中称，此次升级覆盖该网络的各个环节。发布前 Not a Tesla App 曾报道，v15 计划将参数规模提升 10 倍，以处理更多细微路况，这构成此次版本更新的直接前情。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=eNBqkc7V1nU">Introducing Tesla Self-Driving V 15 - YouTube</a></li>
<li><a href="https://www.notateslaapp.com/news/5057/tesla-fsd-v15-coming-next-month-with-holiday-update-musk">Tesla FSD V 15 Arriving Next Month: Home Garage... - Not a Tesla App</a></li>

</ul>
</details>

**标签**: `#autonomous driving`, `#Tesla FSD`, `#AI safety`, `#computer vision`, `#software update`

---