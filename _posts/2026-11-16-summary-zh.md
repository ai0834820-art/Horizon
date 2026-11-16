---
layout: default
title: "Horizon Summary: 2026-11-16 (ZH)"
date: 2026-11-16
lang: zh
---

> 从 35 条内容中筛选出 6 条重要资讯。

---

**科技新闻**
1. [美团开源 LongCat-2.5：称全程用华为升腾训练](#item-tech-news-1) ⭐️ 8.0/10
2. [Protomaps 让自托管地图瓦片更便宜、更简单](#item-tech-news-2) ⭐️ 7.0/10
3. [Raschka 解释现代大模型的位置嵌入](#item-tech-news-3) ⭐️ 7.0/10
4. [MacBook Pro 的 OLED 屏幕 PWM 频闪争议](#item-tech-news-4) ⭐️ 7.0/10
5. [Meta FAIR/NYU：编码器预训练可省，视觉专属参数不可省](#item-tech-news-5) ⭐️ 7.0/10
6. [开源工具让 B300 的 pageable cudaMemcpy 提速约 5 倍](#item-tech-news-6) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [美团开源 LongCat-2.5：称全程用华为升腾训练](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

美团 LongCat 团队在模型发布一周后公开了 1.6 万亿参数的多模态智能体模型 LongCat-2.5 的权重，采用 MIT 许可证，允许商用。该模型每个 token 激活约 480 亿参数，支持文本、图像和视频输入，面向可自主完成冗长、多步骤任务（尤其是编程任务）的智能体。团队官方称训练全程使用华为升腾加速卡、未使用英伟达 GPU；其在 Terminal Bench v2.1 上得分 88.4，略低于 Claude Opus 5 的 89.1。

telegram · zaihuapd · 11月15日 11:08

**「前代背景」** LongCat-2.5 的直接前身是美团此前推出的 LongCat-2.0。据当时报道，该模型从训练到推理全程运行在华为升腾芯片上，借助华为 HCCL 通信库处理了超过 30 万亿 token，集群规模约 5 万颗国产 ASIC，并以 MIT 许可证在 GitHub、Hugging Face 和 ModelScope 上开源。发布后数小时内，华为升腾、MetaX 与沐曦（Muxi）即宣布支持推理。LongCat-2.5 延续了“升腾训练 + MIT 开源”这条路线，同时转向支持文本、图像和视频输入的智能体模型。

**「对开发者的直接影响」** 对开发者而言，MIT 许可加上 1.6T 参数权重意味着可以直接下载、修改并用于商业部署，而不必受闭源 API 条款约束；其 Terminal Bench v2.1 得分 88.4 与 Claude Opus 5 的 89.1 接近，为需要自托管的编码智能体提供了可参照的替代选项。不过，若团队想复制其“不用英伟达 GPU”的训练路径，就需评估从 CUDA 迁移到升腾 CANN 软件栈的适配成本，后者已是业界讨论升腾方案时的主要落地障碍之一。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aicodingweekly.datadriftpress.com/p/61-longcat-edges-out-gpt-5-5">#61 - LongCat edges out GPT-5.5 | AI Coding Weekly</a></li>
<li><a href="https://wireread.com/news/meituan-longcat-2-open-source">LongCat - 2 .0: first trillion -param model built without Nvidia</a></li>
<li><a href="https://www.ainchina.com/blog/meituan-longcat-2-trillion-domestic-chips-china-ai-independence-2026/">How Meituan Built a Trillion - Parameter AI Model on 50,000 Domestic...</a></li>
<li><a href="https://www.spheron.network/blog/huawei-ascend-950-vs-nvidia-b300-b200-llm-inference-2026/">Huawei Ascend 950 vs NVIDIA B300 and B200 for LLM Inference:</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#large language models`, `#AI agents`, `#Huawei Ascend`, `#AI hardware`

---

<a id="item-tech-news-2"></a>
### [Protomaps 让自托管地图瓦片更便宜、更简单](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

一篇关于 Protomaps 的博客文章称，借助 PMTiles 等开放格式自托管地图瓦片已经变得便宜且容易，目标读者是需要控制成本、隐私或访问权限的开发者。文章本身是实践指南而非新版本发布，因此其“便宜且容易”的判断应视为作者经验，而不是独立基准测试。Hacker News 评论补充了具体做法：有人把瓦片放在 Cloudflare R2 后面以掌握地图基础设施，另有人提到 OpenFreeMap 这一类似项目，以及用 Protomaps 降低商业地图 API 成本的侧项目体验。

hackernews · bcye · 11月15日 19:26 · [社区讨论](https://news.ycombinator.com/item?id=50509837)

**「背景」** Protomaps 的核心是 PMTiles：一种把分层地图瓦片打包进单个文件的归档格式，可直接放在 S3 等通用对象存储上，不必自建瓦片服务器或依赖第三方地图服务。客户端通过 HTTP Range 请求按需读取文件中的瓦片，因此能以较低成本和近乎零维护的方式提供自托管地图。

**「影响」** 对打算自托管矢量底图的开发者，评论中的做法是把瓦片存入 Cloudflare R2 等对象存储并由边缘服务提供，从而减少对商业地图服务的依赖；但同一讨论指出，高分辨率卫星影像的存储量会随缩放级别快速上升，有人为控制成本只做到 z17。

**「社区讨论」** 评论者 boramalper 推荐了定位相似的 OpenFreeMap，称其公共实例免费且不限地图浏览量或请求数；neomantra 则分享了在 Cloudflare R2 后自托管 PMTiles 以掌握隐私和访问控制的经验，并指出他提到的 gloss 工具目前对大于 128M 的瓦片和部分栅格格式支持不佳。另有开发者表示，Protomaps 的低成本让原本因 Mapbox 或 Google Maps 费用而不会考虑的维基百科步行游戏侧项目变得可行。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/protomaps/PMTiles">GitHub - protomaps/PMTiles: Pyramids of map tiles in a single ...</a></li>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://docs.protomaps.com/pmtiles/">PMTiles Concepts | Protomaps Docs</a></li>

</ul>
</details>

**标签**: `#Protomaps`, `#self-hosting`, `#map tiles`, `#PMTiles`, `#open source`

---

<a id="item-tech-news-3"></a>
### [Raschka 解释现代大模型的位置嵌入](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

Sebastian Raschka 发表了一篇技术解释文章，梳理现代大型语言模型中的位置嵌入。文章定位为概念与实现层面的教学性内容，而非新模型、新版本或新研究结果的发布。Hacker News 上的讨论则把话题延伸到位置嵌入背后的群表示理论。

hackernews · vismit2000 · 11月15日 12:14 · [社区讨论](https://news.ycombinator.com/item?id=50506376)

**「背景」** 位置嵌入用于让 Transformer 区分 token 的先后顺序；GPT-2 采用可学习的绝对位置向量，并在第一个 Transformer 块之前将其加到 token 嵌入上，因此受固定上下文长度限制。Raschka 的这篇文章从这类经典方法讲到 RoPE，并讨论部分 RoPE、NoPE 以及 2025 至 2026 年开放权重模型的不同选择。

**「影响」** 对希望理解位置嵌入实现思路的读者，这篇文章可作为概念梳理材料；但它不是不同位置嵌入在特定模型中性能对比的实证依据，实际采用仍需结合模型代码与评测。

**「社区讨论」** 评论者 programjames 认为，文章主要讲的是位置嵌入的实现，真正理解还需要理论框架：位置嵌入可被视为群表示，旋转位置嵌入对应平移群的表示。这属于评论者提出的理论视角，而非对文章内容的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://magazine.sebastianraschka.com/p/understanding-positional-embeddings">Understanding Positional Embeddings in Modern LLMs</a></li>
<li><a href="https://sebastianraschka.com/blog/">Blog and Notes - Sebastian Raschka, PhD RoPE vs NoPE: Modern LLM Position Encoding (2026 ... Positional embeddings in modern LLMs: from GPT-2 to RoPE and ... Understanding Positional Embeddings in Modern LLMs Archive - Ahead of AI - Sebastian Raschka, PhD</a></li>

</ul>
</details>

**标签**: `#positional embeddings`, `#large language models`, `#transformers`, `#deep learning`, `#technical education`

---

<a id="item-tech-news-4"></a>
### [MacBook Pro 的 OLED 屏幕 PWM 频闪争议](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

MacAnorak 的一篇文章讨论 MacBook Pro 的 OLED 屏幕采用 PWM（脉宽调制）调光所带来的频闪问题：对部分对闪烁敏感的用户来说，这块在亮度、对比度等指标上更优秀的屏幕反而更难长时间使用。文章的核心争议在于实测频率究竟是多少——原文引用了约 240Hz 的说法，但社区读者在核对测量后并不认同。评论者提出，双层串联 OLED 的两层面板可能各自以 480Hz 调光、相位相差 180 度，在两层同时工作时形成约 960Hz 的有效频率，而这一区间覆盖了大部分可用亮度。目前这些频率数字仍是读者基于测量提出的解释，而非厂商确认的结论。

hackernews · MacAnorak · 11月15日 13:15 · [社区讨论](https://news.ycombinator.com/item?id=50506719)

**「背景」** PWM 调光通过快速开关像素或背光来调节亮度，频率越低，对闪烁敏感的用户越容易感到不适。苹果自 2021 年起在 MacBook Pro 上使用 Mini-LED 屏幕，如今转向串联 OLED，并将其命名为“PROLED XDR Display”；Notebookcheck 的评测记录到 240 Hz 的 PWM，并指出即使有 DC 调光，敏感用户仍可能受到影响。

**「影响」** 对频闪敏感的用户来说，分辨率、对比度和亮度等常规规格无法反映屏幕是否容易引发眼疲劳或头痛，选购时只能依赖第三方实测的调光频率和亲自试用；这也意味着同一块屏幕对多数人更好、对少数人更糟，评价出现分化是预期之中的。

**「社区讨论」** 评论者对文章中约 240Hz 的测量结论提出异议，认为串联 OLED 双层面板反相调光可产生约 960Hz 的有效频率，并称原文也提到了 DC 调光行为。另有读者希望针对 PWM 敏感度开展更多研究以估算受影响人群比例，并把显色指数（CRI）、LCD 运动模糊等列为其他可能引起不适的因素；一位有脑震荡经历的读者则表示，几乎所有屏幕都会影响他，而不只是高亮度 OLED。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.notebookcheck.net/Amazing-OLED-panel-Apple-MacBook-Pro-14-PROLED-XDR-Review.1438048.0.html">Amazing OLED panel - Apple MacBook Pro ... - Notebookcheck Review</a></li>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>

</ul>
</details>

**标签**: `#OLED`, `#PWM flicker`, `#MacBook Pro`, `#display hardware`, `#eye strain`

---

<a id="item-tech-news-5"></a>
### [Meta FAIR/NYU：编码器预训练可省，视觉专属参数不可省](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 7.0/10

Meta FAIR 与 NYU 团队公布了一项受控消融研究，称在相同数据、相同总计算预算下从零训练 200 多个多模态大模型后，单独进行视觉编码器预训练并非必需。作者在 Qwen3-1.7B/4B 配置、0.4B 视觉容量以及 0.6B 到 6.4B 的缩放阶梯上称，四种预训练目标最多只能追平随 LLM 一起从零训练的编码器；即使不计预训练成本也没有优势，而把 MetaCLIP 预训练延长 6.5 倍只将 ImageNet 线性探针准确率从 80.4% 提高到 84.4%，并未改善 VQA。相反，视觉专属参数不可省：无编码器模型在 0.6B 到 6.4B 各尺寸都落后，约需 3 倍计算才能追上；把编码器参数转给 LLM 只提升文本、不提升 VQA。作者还称，将零初始化的视觉专属权重加入 LLM 前 8 层的“in-fusion”方案在 1.7B 到 6.4B 上与前置编码器相当，并把首 token 时间降低约 13%，但结果来自 16 个 Cambrian VQA 基准（448px）和 12 个语言基准，且目前是作者在 Reddit 公布的论文与博客结果。

reddit · r/MachineLearning · /u/trungh98 · 11月15日 17:38

**「背景」** 多模态大语言模型长期默认采用“预训练视觉编码器 + 接入 LLM”的方案，但近期公开模型出现分歧：有的从零训练编码器，有的直接去掉编码器。问题在于，标准视觉编码器把三件事捆在一起——上游预训练带来的视觉先验、只服务视觉 token 的独立参数，以及放在 LLM 之前的预融合位置；而已发布模型的数据、架构和算力各不相同，难以单独判断每一项的作用。

**「对多模态架构选型的影响」** 对正在做多模态架构选型的团队来说，这项消融给出的可操作结论是：独立的视觉编码器和它的预训练可以省掉，但视觉专用的参数容量不能一起砍掉。在 0.6B 到 6.4B 的每一档规模上，完全去掉视觉专用参数的无编码器模型都落后于带编码器的版本，要追平约需 3 倍算力；作者采用的 in-fusion 方案在前 8 层加入零初始化的视觉专用权重，在 1.7B 到 6.4B 上与独立编码器持平，首 token 时间还低约 13%。这与已发布的免编码器设计方向一致，例如 Gemma 4 12B 用轻量线性层把原始图像块直接投影进 LLM 嵌入空间。需要注意的是，这些结论来自以 1.7B 和 4B 为主的主实验、448 像素下的 16 个 VQA 基准，尚未经同行评审；更大骨干规模或更高输入分辨率下是否仍成立，仍需自行验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/pdf/2611.17334v1">Unbundling Multimodal Vision Encoding - arXiv.org</a></li>
<li><a href="https://huggingface.co/papers/2611.17334">Paper page - Unbundling Multimodal Vision Encoding</a></li>
<li><a href="https://huggingface.co/google/gemma-4-12B">google/ gemma - 4 - 12 B · Hugging Face</a></li>
<li><a href="https://developers.googleblog.com/gemma-4-12b-the-developer-guide/">Gemma 4 12 B : The Developer Guide - Google Developers Blog</a></li>

</ul>
</details>

**标签**: `#multimodal LLMs`, `#vision encoders`, `#pretraining`, `#controlled ablations`, `#model scaling`

---

<a id="item-tech-news-6"></a>
### [开源工具让 B300 的 pageable cudaMemcpy 提速约 5 倍](https://www.reddit.com/r/MachineLearning/comments/1xx2n25/making_cudamemcpy_5x_faster_on_a_b300_p/) ⭐️ 7.0/10

一位开发者发布了开源工具 cudamemcpy-tuner，声称在 NVIDIA B300 上把 pageable cudaMemcpy 的 CPU→GPU 传输从 10.2 GB/s 提升到 51.5 GB/s，约 5 倍。其示例使用 1 GB uint8 张量，连续 5 次复制并同步计时，通过 \`cmt tune -- python bench.py\` 运行；项目附带基准、博客和代码。上述结果来自作者自测，仅覆盖这一 GPU、数据规模和可页内存传输场景，尚未经过独立验证。

reddit · r/MachineLearning · /u/makneeee · 11月15日 18:20

**「背景：可分页与页锁定内存」** 在 CUDA 中，pageable（可分页）主机内存不能直接用于 GPU 的 DMA 传输，通常要先复制到页锁定（pinned）的暂存缓冲区，再通过 DMA 传到 GPU；而用 cudaMallocHost 分配的 pinned 内存可跳过这一步，因此传输更快。NVIDIA 文档也指出，pinned 与 pageable 传输使用相同的 cudaMemcpy\(\) 调用语法，差别主要在主机内存是否页锁定。

**「影响」** 对需要在 B300 上执行可页内存 CPU-GPU 拷贝的开发者，这个工具提供了一种可直接套在现有脚本前测试的调优方式；但收益目前只在作者的 1 GB 基准中报告，采用前应在自己的数据规模、传输方向和 CUDA 环境中复测，不能把 51.5 GB/s 当作通用保证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://developer.nvidia.com/blog/how-optimize-data-transfers-cuda-cc/">How to Optimize Data Transfers in CUDA C/C++ | NVIDIA Technical...</a></li>
<li><a href="https://stackoverflow.com/questions/5736968/why-is-cuda-pinned-memory-so-fast">c++ - Why is CUDA pinned memory so fast? - Stack Overflow</a></li>
<li><a href="https://jinseok-moon.github.io/p/pinned-memory/">Pageable vs. pinned data transfer | Jinseok Moon</a></li>

</ul>
</details>

**标签**: `#CUDA`, `#GPU memory`, `#performance optimization`, `#benchmarking`, `#open source`

---