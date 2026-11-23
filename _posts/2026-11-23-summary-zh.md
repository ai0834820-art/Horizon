---
layout: default
title: "Horizon Summary: 2026-11-23 (ZH)"
date: 2026-11-23
lang: zh
---

> 从 27 条内容中筛选出 3 条重要资讯。

---

**科技新闻**
1. [OpenAI 分析困惑度与模型智能的关系](#item-tech-news-1) ⭐️ 7.0/10
2. [蚂蚁集团领投 Simplexity 1 亿美元 pre-A 轮](#item-tech-news-2) ⭐️ 7.0/10
3. [Windows Server 2028 默认移除 WoW64，32 位应用需手动装回](#item-tech-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 分析困惑度与模型智能的关系](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

OpenAI 发布了一篇分析文章，讨论语言模型的困惑度（perplexity）与智能水平、基准表现之间的关系。对 LLM 评测和基准设计者而言，文章属于分析/评论，而非新模型、版本或产品发布。讨论的核心是交叉熵/困惑度能否作为比现有基准更简单的模型能力信号，以及在 RL 训练普及后这一信号是否仍然成立。

hackernews · acossta · 11月22日 17:06 · [社区讨论](https://news.ycombinator.com/item?id=50601525)

**「背景：困惑度是什么」** 困惑度（perplexity）在数值上等同于交叉熵损失，用来衡量模型预测下一个 token 时的不确定程度：如果每一步都能完美预测，困惑度就是 1；如果完全是随机猜测，则约等于词表大小。它长期以来主要是预训练阶段的内部训练指标，而 OpenAI 首席科学家 Jakub Pachocki 在该文中主张把它提升为可供不同模型开发者横向比较、并服务于共同安全标准的公开指标。

**「对模型评测与选型的影响」** 若把困惑度当作可横向比较的指标，前提是固定同一 held-out 评测集与分词方式：困惑度最坏等于词表大小、最好为 1，换词表或数据集后数值不能直接对比；评论中提到的微软在 OpenAI 评测集上自报 MAI-2 Base 对数困惑度 0.819，也属于需要统一口径的厂商数据。对做基座模型选型的团队来说，这提供了一个比日益复杂的基准套件更简单的预训练进展信号（OpenAI 文章以 GPT-2 在旧数据集上刷新困惑度 SOTA、GPT-3 具备上下文学习为例），但它衡量的是下一 token 预测与压缩能力，不能替代后训练和 RL 之后的推理评测。

**「社区讨论」** 评论者指出文章未定义困惑度，并补充其为模型预测下一 token 的惊讶程度：最差情况等于词表大小，最佳情况为 1。有人惊讶于交叉熵在 RL 时代仍呈现清晰趋势，认为这提供了比日益复杂的基准更简单的信号；也有人从“预测即压缩”的角度认为困惑度与智能的对应并不意外，另有评论者称微软的 MAI-2 Base 已在 OpenAI 的评测集上报告 log-perplexity 0.819。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence | OpenAI</a></li>

</ul>
</details>

**标签**: `#LLM evaluation`, `#perplexity`, `#benchmarking`, `#language models`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [蚂蚁集团领投 Simplexity 1 亿美元 pre-A 轮](https://www.bloomberg.com/news/articles/2026-11-22/ant-group-bets-on-simplexity-to-thrive-in-china-s-humanoid-race) ⭐️ 7.0/10

彭博报道，中国具身智能公司 Simplexity Robotics 完成 1 亿美元 pre-A 轮融资，由蚂蚁集团领投，投后估值 16 亿美元。老股东阿里巴巴、腾讯、HongShan（红杉中国）和蓝驰创投跟投，董事长兼联合创始人 Wang Kai 向彭博确认了这一消息。公司 2025 年 7 月成立于杭州，核心团队来自理想汽车，贾鹏任 CEO、王佳佳任 COO；2026 年 3 月它曾披露成立半年内完成五轮融资、累计 20 亿元人民币，当时投后估值已超过 10 亿美元。彭博称这笔资金将用于与宇树、优必选等更成熟厂商争夺市场，并称中国人形机器人产业占全球出货量约 97%。

telegram · zaihuapd · 11月23日 02:02

**「背景」** Simplexity Robotics 于 2025 年 7 月在杭州成立，核心团队来自理想汽车，贾鹏任 CEO、王佳佳任 COO。公司今年 3 月披露，成立半年内已完成五轮融资、累计 20 亿元人民币，投后估值超过 10 亿美元。

**「影响」** 对关注中国人形机器人供应链的开发者和采购方而言，这笔融资意味着 Simplexity 将获得与宇树、优必选争夺市场的资金，但报道未披露其产品量产、交付时间或技术指标，融资规模不能替代对产品成熟度的验证。

**标签**: `#embodied AI`, `#humanoid robots`, `#funding`, `#China tech`, `#Ant Group`

---

<a id="item-tech-news-3"></a>
### [Windows Server 2028 默认移除 WoW64，32 位应用需手动装回](https://www.windowslatest.com/2026/11/23/32-bit-apps-days-are-numbered-as-microsoft-strips-support-bit-by-bit-starting-with-windows-server-2028-but-windows-11-is-safe-for-now/) ⭐️ 7.0/10

微软在 Ignite 2026 上宣布，计划让 Windows Server 2028 默认不再包含 WoW64 兼容子系统，因此系统开箱即无法运行 32 位应用。该版本计划于 2027 年秋季与 Windows 11 27H2 一同发布。需要时管理员可通过按需功能（FoD）重新安装 WoW64，在 Server Core 上通常使用 PowerShell 或 DISM；微软称此举是为了缩小攻击面并阻止 32 位恶意软件。Windows 11 目前仍保留 WoW64，微软未公布移除计划。

telegram · zaihuapd · 11月23日 03:03

**「背景」** WoW64（Windows 32-bit on Windows 64-bit）是 Windows 的兼容子系统，使 64 位系统能够运行 32 位应用；此前它通常随系统提供，用户无需单独安装。Windows Server 2028 的变化在于把这个组件从默认安装中移出，改为按需功能（FoD），因此旧应用的兼容性从“默认具备”变成需要管理员显式启用。

**「对服务器运维的影响」** 对仍依赖 32 位组件的服务器运维团队来说，升级到 Windows Server 2028 后，需要先通过 PowerShell 或 DISM 手动添加 WoW64 按需功能，并在系统镜像和部署脚本中预先包含这一步，否则旧应用在部署当天会直接无法启动；Server Core 环境尤其要提前验证。微软的“已移除功能”文档还列出该版本不再以内置可选组件或 FoD 形式提供 .NET Framework 3.5，因此依赖旧版 .NET 的 32 位程序，还需要单独规划运行时安装或迁移（tool-2-1、tool-2-3）。

<details><summary>参考链接</summary>
<ul>
<li>Features Removed or No Longer Developed in Windows Server | Microsoft Learn</li>
<li>32-bit apps&#x27; days are numbered as Microsoft strips support bit by bit, starting with Windows Server 2028, but Windows 11 is safe for now</li>

</ul>
</details>

**标签**: `#Windows Server`, `#WoW64`, `#backward compatibility`, `#Microsoft`, `#32-bit applications`

---