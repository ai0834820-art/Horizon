---
layout: default
title: "Horizon Summary: 2026-11-16 (EN)"
date: 2026-11-16
lang: en
---

> From 35 items, 6 important content pieces were selected

---

**Technology News**
1. [Meituan releases LongCat-2.5 weights, claims Huawei-only training](#item-tech-news-1) ⭐️ 8.0/10
2. [Protomaps Guide Makes Self-Hosted Map Tiles Cheap and Easy](#item-tech-news-2) ⭐️ 7.0/10
3. [Sebastian Raschka Explains Positional Embeddings in Modern LLMs](#item-tech-news-3) ⭐️ 7.0/10
4. [MacBook Pro OLED PWM flicker and flicker sensitivity](#item-tech-news-4) ⭐️ 7.0/10
5. [Meta FAIR/NYU: vision encoder pretraining optional, vision-only parameters required](#item-tech-news-5) ⭐️ 7.0/10
6. [Tool claims 5x faster pageable cudaMemcpy on B300, 10.2 to 51.5 GB/s](#item-tech-news-6) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Meituan releases LongCat-2.5 weights, claims Huawei-only training](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

Meituan&\#x27;s LongCat team released the weights for LongCat-2.5, a 1.6-trillion-parameter multimodal agent model, one week after its official launch. The team says it trained the model entirely on Huawei Ascend accelerators without Nvidia GPUs, a vendor claim not independently verified in the supplied material. The model activates about 48 billion parameters per token, accepts text, image, and video inputs, and is available under an MIT license for commercial use. It scored 88.4 on Terminal Bench v2.1, slightly below Claude Opus 5&\#x27;s 89.1.

telegram · zaihuapd · Nov 15, 11:08

**「Background」** Meituan&\#x27;s LongCat family had already staked out the domestic-chip claim: LongCat-2.0 was reported as a 1.6-trillion-parameter model trained and served end-to-end on Huawei Ascend accelerators across a cluster of roughly 50,000 domestic ASICs, with no Nvidia hardware, then open-sourced under an MIT license. Within hours of that release, Huawei Ascend, MetaX and Muxi announced inference compatibility, which matters because the ecosystem around Ascend is younger than CUDA&\#x27;s. LongCat-2.5 therefore extends an existing Ascend-only lineage — per the item, it keeps a 1.6T total size with about 48B parameters activated per token and adds image and video input — rather than being the team&\#x27;s first attempt at training without Nvidia GPUs.

**「Commercial self-hosting with an Ascend caveat」** Because the weights ship under an MIT license, teams can self-host or fine-tune LongCat-2.5 commercially without a per-token API contract — relevant for organizations that cannot send source code to a hosted coding agent. The operational catch is stack-specific: reproducing the reported training setup, or fine-tuning at scale, means working in Huawei&\#x27;s CANN software ecosystem rather than CUDA, and Ascend-versus-CUDA tooling maturity and porting cost remain documented friction points for teams weighing that hardware.

<details><summary>References</summary>
<ul>
<li><a href="https://aicodingweekly.datadriftpress.com/p/61-longcat-edges-out-gpt-5-5">#61 - LongCat edges out GPT-5.5 | AI Coding Weekly</a></li>
<li><a href="https://wireread.com/news/meituan-longcat-2-open-source">LongCat - 2 .0: first trillion -param model built without Nvidia</a></li>
<li><a href="https://www.ainchina.com/blog/meituan-longcat-2-trillion-domestic-chips-china-ai-independence-2026/">How Meituan Built a Trillion - Parameter AI Model on 50,000 Domestic...</a></li>
<li><a href="https://www.spheron.network/blog/huawei-ascend-950-vs-nvidia-b300-b200-llm-inference-2026/">Huawei Ascend 950 vs NVIDIA B300 and B200 for LLM Inference:</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#large language models`, `#AI agents`, `#Huawei Ascend`, `#AI hardware`

---

<a id="item-tech-news-2"></a>
### [Protomaps Guide Makes Self-Hosted Map Tiles Cheap and Easy](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

The linked Protomaps post argues that self-hosting map tiles is now cheap and easy enough for developers, with PMTiles as the tile format. It is practical tooling guidance rather than a product release; the supplied material does not include a version number, pricing, or benchmark results.

hackernews · bcye · Nov 15, 19:26 · [Discussion](https://news.ycombinator.com/item?id=50509837)

**「How PMTiles enables self-hosting」** Protomaps&\#x27; self-hosting model rests on PMTiles, a single-file archive format for pyramids of tiled map data that can be hosted on commodity object storage such as S3 rather than behind a custom tile server. Because clients fetch only the needed byte ranges via HTTP range requests, the map can be served as a static file with no dedicated tile backend or third-party provider.

**「Impact」** Developers who need high-resolution satellite imagery should not assume the same economics: one commenter building a North America mosaic stopped at zoom level 17 because higher zoom levels projected storage requirements in the hundreds of terabytes.

**「Community discussion」** Commenters add alternatives and deployment experience: one points to OpenFreeMap as a similar free option, another serves PMTiles from Cloudflare R2 to keep map infrastructure private and access-controlled, and a third says Protomaps made a live-rendered street-card game affordable enough for a side project. These are individual reports, not independent benchmarks.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/protomaps/PMTiles">GitHub - protomaps/PMTiles: Pyramids of map tiles in a single ...</a></li>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://docs.protomaps.com/pmtiles/">PMTiles Concepts | Protomaps Docs</a></li>

</ul>
</details>

**Tags**: `#Protomaps`, `#self-hosting`, `#map tiles`, `#PMTiles`, `#open source`

---

<a id="item-tech-news-3"></a>
### [Sebastian Raschka Explains Positional Embeddings in Modern LLMs](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

Sebastian Raschka has published an explanatory article on positional embeddings in modern large language models, walking through how the mechanism is implemented rather than presenting a new model, benchmark, or research result. The piece targets readers who want a conceptual and implementation-level grasp of how transformers encode token order. On Hacker News, discussion moved toward the underlying theory, with commenters arguing that a full understanding requires treating positional embeddings as group representations.

hackernews · vismit2000 · Nov 15, 12:14 · [Discussion](https://news.ycombinator.com/item?id=50506376)

**「Background」** Transformer attention has no built-in notion of token order, so models inject position information separately. GPT-2 used learned absolute position vectors added to token embeddings and tied to a fixed 1,024-token context, while contemporary architectures largely use rotary position embeddings \(RoPE\) or adapt or omit explicit position encoding.

**「Community Discussion」** Commenter programjames argued that the article addresses implementation only, and that positional embeddings are properly understood as group representations — citing rotary positional embeddings as representations of the translation group, whose abelian structure makes them tractable to derive and parameterize as learnable components. That is a theoretical framing offered by a commenter, not a result established by the article itself.

<details><summary>References</summary>
<ul>
<li><a href="https://magazine.sebastianraschka.com/p/understanding-positional-embeddings">Understanding Positional Embeddings in Modern LLMs</a></li>
<li><a href="https://sebastianraschka.com/blog/">Blog and Notes - Sebastian Raschka, PhD RoPE vs NoPE: Modern LLM Position Encoding (2026 ... Positional embeddings in modern LLMs: from GPT-2 to RoPE and ... Understanding Positional Embeddings in Modern LLMs Archive - Ahead of AI - Sebastian Raschka, PhD</a></li>

</ul>
</details>

**Tags**: `#positional embeddings`, `#large language models`, `#transformers`, `#deep learning`, `#technical education`

---

<a id="item-tech-news-4"></a>
### [MacBook Pro OLED PWM flicker and flicker sensitivity](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

The article examines PWM flicker on the MacBook Pro’s OLED display and argues that the panel’s technical advantages can make it worse to use for people sensitive to flicker. The discussion centers on measured PWM frequencies and dimming, with Hacker News commenters disputing a cited 240 Hz figure. One commenter suggests the tandem OLED’s two layers may run at 480 Hz out of phase for an effective 960 Hz across most usable brightness.

hackernews · MacAnorak · Nov 15, 13:15 · [Discussion](https://news.ycombinator.com/item?id=50506719)

**「Context: tandem OLED and PWM dimming」** Apple’s tandem-OLED MacBook Pro panel, branded “ProLED XDR,” joins the Mini-LED display that has served the range since 2021 and which Apple continues to sell. OLED brightness is commonly controlled with pulse-width modulation \(PWM\), which switches the display on and off rapidly; a Notebookcheck review measured 240 Hz PWM on the 14-inch model alongside DC dimming, a rate that can still affect flicker-sensitive users.

**「Community Discussion」** Commenters debate the frequency evidence: legitronics argues the 240 Hz figure may be wrong and proposes an effective 960 Hz from out-of-phase tandem OLED layers, while achr2 cites a paper indicating humans can perceive flicker above twice a display’s rate. Others broaden the concern to CRI, motion blur, and screen sensitivity after concussion.

<details><summary>References</summary>
<ul>
<li><a href="https://www.notebookcheck.net/Amazing-OLED-panel-Apple-MacBook-Pro-14-PROLED-XDR-Review.1438048.0.html">Amazing OLED panel - Apple MacBook Pro ... - Notebookcheck Review</a></li>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>

</ul>
</details>

**Tags**: `#OLED`, `#PWM flicker`, `#MacBook Pro`, `#display hardware`, `#eye strain`

---

<a id="item-tech-news-5"></a>
### [Meta FAIR/NYU: vision encoder pretraining optional, vision-only parameters required](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 7.0/10

A Meta FAIR + NYU preprint, announced by an author on Reddit, reports controlled ablations across 200+ multimodal LLMs trained from scratch on the same data, with encoder pretraining counted against the same compute budget. At matched compute, separate encoder pretraining—contrastive, self-supervised, or captioning—at best tied training the encoder from scratch with the LLM; 6.5x longer MetaCLIP pretraining raised ImageNet linear-probe accuracy from 80.4% to 84.4% but did not improve VQA. Vision-only parameters were required: encoder-free models trailed at every backbone size from 0.6B to 6.4B and needed about 3x the compute to catch up, while giving those parameters to the LLM improved text but not VQA. Placement was optional: an “in-fusion” design adding zero-initialized vision-only weights to the LLM’s first eight layers matched an encoder from 1.7B to 6.4B with about 13% lower time to first token.

reddit · r/MachineLearning · /u/trungh98 · Nov 15, 17:38

**「Why the encoder question was open」** Most multimodal language models have followed a common recipe: pair a language model with a vision encoder pretrained separately, either on contrastive image-text data or self-supervised objectives. Recent recipes diverge — some train the encoder alongside the language model from scratch, others remove it — but because published models also differ in data, architecture, and compute, their benchmark results cannot isolate which of the encoder&\#x27;s bundled design choices actually drives performance, as the paper&\#x27;s abstract and Hugging Face listing note.

**「Impact」** Developers weighing an encoder-free multimodal architecture should budget for the training cost: in the study&\#x27;s 0.6B–6.4B scaling ladder, encoder-free models needed about 3x the compute to match encoder-based ones, even though removing the encoder saves parameters — Gemma 4 12B, for instance, drops roughly 150M vision-encoder parameters. The paper&\#x27;s in-fusion variant gives teams a concrete alternative to test: zero-initialized vision-only attention and FFN branches in the LLM&\#x27;s first eight layers were on par with an encoder from 1.7B to 6.4B and cut time to first token by about 13%.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/pdf/2611.17334v1">Unbundling Multimodal Vision Encoding - arXiv.org</a></li>
<li><a href="https://huggingface.co/papers/2611.17334">Paper page - Unbundling Multimodal Vision Encoding</a></li>
<li><a href="https://huggingface.co/google/gemma-4-12B">google/ gemma - 4 - 12 B · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#multimodal LLMs`, `#vision encoders`, `#pretraining`, `#controlled ablations`, `#model scaling`

---

<a id="item-tech-news-6"></a>
### [Tool claims 5x faster pageable cudaMemcpy on B300, 10.2 to 51.5 GB/s](https://www.reddit.com/r/MachineLearning/comments/1xx2n25/making_cudamemcpy_5x_faster_on_a_b300_p/) ⭐️ 7.0/10

A Reddit user published an open-source tool, cudamemcpy-tuner, that tunes pageable CUDA memory transfers and reports a 5x speedup on an Nvidia B300 GPU. In the supplied benchmark, copying a 1 GB uint8 tensor from CPU to GPU through PyTorch rose from 10.2 GB/s under plain \`python\` to 51.5 GB/s when launched through \`cmt tune\`. The claim covers only pageable transfers, not pinned memory, and is self-reported by the author, who links a blog post and GitHub repository but provides no independent verification.

reddit · r/MachineLearning · /u/makneeee · Nov 15, 18:20

**「Why pageable copies are slow」** CUDA cannot DMA directly out of ordinary pageable host memory, because those pages may be swapped to disk; the driver first copies the data into a page-locked &quot;staging&quot; buffer and then transfers it to the GPU over DMA. Allocating host memory as pinned \(for example with cudaMallocHost\) skips that intermediate copy, which is why pinned transfers are faster even though both paths use the same cudaMemcpy\(\) call syntax. NVIDIA ships a bandwidthTest program specifically for comparing pageable and pinned transfer rates.

**「Impact」** Developers whose workloads copy pageable host memory to a GPU can test the tuner before restructuring code around pinned memory or custom transfer kernels, since the same unmodified benchmark script produced the higher number only when launched through \`cmt tune\`. Whether the gain carries over depends on the tuner finding suitable settings for the specific GPU and transfer size, and the 5x figure has not been reproduced outside the author&\#x27;s setup.

<details><summary>References</summary>
<ul>
<li><a href="https://developer.nvidia.com/blog/how-optimize-data-transfers-cuda-cc/">How to Optimize Data Transfers in CUDA C/C++ | NVIDIA Technical...</a></li>
<li><a href="https://stackoverflow.com/questions/5736968/why-is-cuda-pinned-memory-so-fast">c++ - Why is CUDA pinned memory so fast? - Stack Overflow</a></li>
<li><a href="https://jinseok-moon.github.io/p/pinned-memory/">Pageable vs. pinned data transfer | Jinseok Moon</a></li>

</ul>
</details>

**Tags**: `#CUDA`, `#GPU memory`, `#performance optimization`, `#benchmarking`, `#open source`

---