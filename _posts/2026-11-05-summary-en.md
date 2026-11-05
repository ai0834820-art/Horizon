---
layout: default
title: "Horizon Summary: 2026-11-05 (EN)"
date: 2026-11-05
lang: en
---

> From 52 items, 12 important content pieces were selected

---

**Technology News**
1. [OpenAI reports 948 Linux kernel privilege-escalation exploits](#item-tech-news-1) ⭐️ 8.0/10
2. [Go introduces a new standard-library JSON API](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic publishes FlashProve spec and code for provable inference](#item-tech-news-3) ⭐️ 8.0/10
4. [Trainium2 NKI megakernels cut GLM-5.3-Flash decode step to 24.2 ms](#item-tech-news-4) ⭐️ 8.0/10
5. [Moonshot AI reportedly open-sources Kimi K3.1 Pro weights](#item-tech-news-5) ⭐️ 8.0/10
6. [AI vulnerability auditing confronts four decades of software debt](#item-tech-news-6) ⭐️ 7.0/10
7. [AMD expects first-ever Q4 revenue lead over Intel at $17B](#item-tech-news-7) ⭐️ 7.0/10
8. [Tencent releases Hy4 open-weight model with scientific and game-dev adaptations](#item-tech-news-8) ⭐️ 7.0/10
9. [Huginn weight sharing on B200 cuts HBM reads only when weights fit cache](#item-tech-news-9) ⭐️ 7.0/10
10. [Oracle Reportedly Cancels $7B AI Chip Lease With Tencent](#item-tech-news-10) ⭐️ 7.0/10
11. [Huawei tells Ascend 960DT buyers to source Samsung, SK Hynix HBM](#item-tech-news-11) ⭐️ 7.0/10
12. [Bluetooth HDT standard lifts LE peak throughput to 7.5 Mbps](#item-tech-news-12) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI reports 948 Linux kernel privilege-escalation exploits](https://openai.com/index/a-thousand-fewer-paths-to-root/) ⭐️ 8.0/10

OpenAI says its autonomous vulnerability-research pipeline scanned the Linux kernel in October 2026, reproduced 1,724 vulnerabilities, and generated 948 working local privilege-escalation exploits plus 291 information-leak proofs of concept. OpenAI put the total API cost at $1,213,430 and said outside experts confirmed at least 10 of the exploitation techniques as novel. Those figures are OpenAI&\#x27;s account; the supplied material does not include the post body or an independent reproduction, and it does not identify which kernel versions or configurations are affected. For Linux users, distributors, and kernel maintainers, the reported volume implies a large triage and patching workload.

hackernews · dangelosaurus · Nov 4, 23:33 · [Discussion](https://news.ycombinator.com/item?id=50372929)

**「Background」** Linux local privilege escalation \(LPE\) exploits abuse a kernel bug to turn ordinary user access into root. Because production kernels enable defenses such as SMEP, SMAP, KASLR and HARDENED\_USERCOPY, a bug is only a practical LPE if an exploit still works with those protections in place.

**「Triage load for kernel and distro maintainers」** Linux distributors and kernel maintainers face a triage problem: if OpenAI&\#x27;s figures hold, hundreds of working local-privilege-escalation programs arrive at once, and each must be matched to an upstream fix and backported — the same per-distribution patching burden seen with the &quot;Dirty Frag&quot; LPE pair \(CVE-2026-43284, CVE-2026-43500\) disclosed in May 2026. Until that triage happens, administrators should treat ordinary local user access on Linux as effectively root, and should read the $1,279-per-exploit cost and the $18.9M–$66.3M bounty-value comparison as OpenAI&\#x27;s own accounting rather than an independently verified result.

**「Community Discussion」** Commenters focused on whether the count reflects the kernel being too complex to reason about, a deeper security-model or language flaw, or a broader reality that all software is more compromised than assumed. One commenter said local escalation has long been assumed possible in Linux but 948 was still shocking, while another asked what mitigating factors keep the internet and power infrastructure running.

<details><summary>References</summary>
<ul>
<li><a href="https://cybersecuritynews.com/openai-uncovers-948-linux-kernel-vulnerabilities/">OpenAI Cyber Model Uncovers 948 Linux Kernel Privilege ...</a></li>
<li><a href="https://ubuntu.com/blog/dirty-frag-linux-vulnerability-fixes-available">Dirty Frag Linux kernel local privilege escalation ... - Ubuntu</a></li>

</ul>
</details>

**Tags**: `#Linux kernel`, `#privilege escalation`, `#security research`, `#AI-assisted vulnerability discovery`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Go introduces a new standard-library JSON API](https://go.dev/blog/jsonv2) ⭐️ 8.0/10

Go has introduced a new standard-library JSON API, according to an official Go blog post, changing a core package used widely across the Go ecosystem. The available material does not include the API specification, release timing, or migration guidance; the item&\#x27;s tags point to encoding/json/v2, but that detail is not confirmed by supplied source content.

hackernews · olexsmir · Nov 4, 17:52 · [Discussion](https://news.ycombinator.com/item?id=50369106)

**「Background」** Go&\#x27;s existing encoding/json package has long handled JSON encoding and decoding; json.Marshal emits compact JSON, while json.MarshalIndent adds configurable indentation. The new v2 work is built on the encoding/json/jsontext package, which the Go blog describes as the foundation for improvements to JSON in Go.

**「Migration cost for existing code」** Because encoding/json/v2 is a breaking revision rather than a drop-in replacement, teams upgrading existing services will need to audit call sites and adapt code that relies on v1 behavior. One concrete example raised in the discussion is MarshalIndent: commenters noted it is gone in v2 and that the equivalent indented-output code is considerably more involved, making both migration and quick debugging dumps harder.

**「Community discussion」** One commenter said they generally like encoding/json/v2 but objected to the removal of MarshalIndent, arguing that the replacement is complicated and non-obvious, making both migration and quick generation of readable JSON harder. Another commenter reported using the jsontext package successfully for a parser that needed client-specific error messages while retaining strong performance.

<details><summary>References</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2">A new Go API for JSON - The Go Programming Language</a></li>
<li><a href="https://stackoverflow.com/questions/44495489/what-is-the-difference-between-json-marshal-and-json-marshalindent-using-go">What is the difference between json . Marshal and json . MarshalIndent ...</a></li>
<li><a href="https://antonz.org/go-json-v2/">JSON evolution in Go : from v1 to v 2</a></li>
<li><a href="https://stackoverflow.com/questions/44495489/what-is-the-difference-between-json-marshal-and-json-marshalindent-using-go">What is the difference between json . Marshal and json . MarshalIndent ...</a></li>

</ul>
</details>

**Tags**: `#Go`, `#JSON`, `#standard library`, `#API design`, `#encoding/json/v2`

---

<a id="item-tech-news-3"></a>
### [Anthropic publishes FlashProve spec and code for provable inference](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic has published a technical specification and code for FlashProve, a system that uses cryptographic proofs to verify that a specified model produced an AI output; Anthropic says the research is ongoing and has no deployment plan. The approach requires model labs to publish a fingerprint for each released model without exposing its weights, so users or third parties can match outputs and check claims about which model served a request, with verification possible on local devices. Anthropic presents it as a way to detect model substitution and substantiate third-party claims about model execution, but the supplied material reports no independent validation or production availability.

hackernews · ltononro · Nov 4, 17:17 · [Discussion](https://news.ycombinator.com/item?id=50368626)

**「Background」** Provable inference uses cryptographic proofs to let a user check which model weights produced a response without revealing those weights. Anthropic&\#x27;s FlashProve is a research prototype that runs Llama 4 Maverick at full size with a 1,024-token context on a single NVIDIA H100, and its GitHub page credits James Petrie&\#x27;s VerInf work.

**「Impact」** For enterprise buyers and auditors, the practical test is whether model providers will publish fingerprints and accept per-request proof checks; until then, FlashProve cannot independently confirm which weights serve a production request.

**「Community discussion」** Commenters treated cost as the main obstacle: one cited a 90–100x compute overhead, and another noted that checking a proof takes 17 seconds on 24 threads \(21 seconds on one\), with a roughly 6.5 MB commitment valid for about 16 million requests. Others argued that open-weight models can be verified more cheaply by rerunning deterministic inference, and one researcher said the work builds on their VerInf project with little attribution.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/research/provable-inference">Progress on provable inference for large language models \ Anthropic</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/anthropic-flashprove-cryptographic-model-verification">Anthropic unveils cryptographic tool to verify model outputs</a></li>
<li><a href="https://github.com/anthropics/FlashProve">GitHub - anthropics/ FlashProve : A research prototype for...</a></li>

</ul>
</details>

**Tags**: `#provable inference`, `#LLM verification`, `#zero-knowledge proofs`, `#Anthropic research`, `#verifiable computation`

---

<a id="item-tech-news-4"></a>
### [Trainium2 NKI megakernels cut GLM-5.3-Flash decode step to 24.2 ms](https://www.reddit.com/r/MachineLearning/comments/1xo0yuq/p_nki_layer_megakernels_for_glm53flash_on_aws/) ⭐️ 8.0/10

RunAnywhere open-sourced trnrt, an inference engine that serves the 320B-parameter GLM-5.3-Flash MoE \(1M-token context\) on a single AWS trn2.48xlarge, and reports that rewriting each layer half as one NKI megakernel cut a batch-8 decode step from 32.2 ms in its 17 October build to 24.2 ms on 1 November. Profiling had shown the step was not dominated by model math: in one linear-attention layer the recurrence was 2% of the attention half, while the mHC pre-projection \(36%\) and XLA glue \(33%\) took most of the rest, with chains of small vector instructions at roughly 153 ns fixed cost each, an HBM writeback at every kernel boundary, and 125 cross-chip collectives per step. The kernels keep a layer half&\#x27;s activations, recurrent state and in-flight weights inside each physical NeuronCore&\#x27;s 28 MiB SBUF, split the 340–400 GB/s weight stream across both cores of a logical core, and move a collective inside the kernel when it would otherwise block the next one; the fused sparse-attention layer saved 3.2 ms per batch-8 step and the KDA and MoE kernels together saved another 3.2 ms. The figures are author-reported with no stock-AWS baseline \(the latest vLLM Neuron plugin registers no GLM model and NxD Inference is in maintenance mode\), no task-level eval has been run on this build, and one sparse-attention prefill approximation remains on 1.2% of selections, shifting next-token log-probabilities by 0.012–0.021 nats and changing the top token at 3 of 448 positions.

reddit · r/MachineLearning · /u/WildCard727 · Nov 4, 21:47

**「Trainium2 and NKI context」** NKI is AWS&\#x27;s low-level programming interface for custom kernels on Trainium and Inferentia, giving direct access to the NeuronCore ISA; AWS&\#x27;s Trainium2 documentation describes eight NeuronCore-V3 cores per chip and Logical NeuronCore Configuration, which can combine multiple physical cores into one logical core. NKI kernels also manage the on-chip SBUF explicitly, the memory tier that the post&\#x27;s megakernels try to keep a layer half&\#x27;s working set inside.

**「Custom kernels required」** For teams serving GLM-5.3-Flash on Trainium2, the practical consequence is that there is no stock vLLM or NxD Inference path to benchmark against, so adoption means maintaining custom NKI kernels and re-validating them on device; the author reports three kernels that passed NKI&\#x27;s simulator but returned wrong answers on hardware. The open-source engine and its docs/RESULTS.md make the 24.2 ms batch-8 decode figure reproducible, but the lack of a task-level eval or GPU comparison means the end-to-end throughput numbers remain author-reported.

<details><summary>References</summary>
<ul>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/latest/general/arch/neuron-hardware/trainium2.html">Trainium2 Architecture — AWS Neuron Documentation</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/latest/general/nki/index.html">Neuron Kernel Interface (NKI) — AWS Neuron Documentation</a></li>
<li><a href="https://sampooni.github.io/ai-accelerator-report-2026/aws/05-aws-memory-optimization.html">Chapter 05: Memory Optimization | AWS Trainium</a></li>

</ul>
</details>

**Tags**: `#AWS Trainium`, `#inference optimization`, `#GPU/accelerator kernels`, `#mixture-of-experts`, `#performance profiling`

---

<a id="item-tech-news-5"></a>
### [Moonshot AI reportedly open-sources Kimi K3.1 Pro weights](http://platform.kimi.ai/) ⭐️ 8.0/10

Moonshot AI has reportedly published open weights on Hugging Face for Kimi K3.1 Pro, described in the source as a natively multimodal agent model with 2.8T total parameters, 104B active parameters, and roughly 1M-token context — the first model in the K3.1 series. The weights are released in MXFP4 quantized form, and an accompanying API lets developers call \`kimi-k3.1-pro\` on platform.kimi.ai with OpenAI- and Anthropic-compatible interfaces. The report comes from a single Telegram channel and has not been independently verified, so the parameter counts, context length, and availability should be treated as vendor-style claims rather than confirmed measurements.

telegram · zaihuapd · Nov 4, 15:47

**「Context」** Kimi K3.1 Pro is described as the first model in Moonshot AI&\#x27;s K3.1 series and is being released as open weights on Hugging Face. Its 2.8T total and 104B active parameter counts indicate a sparse mixture-of-experts design, in which only a subset of parameters is used per token; the published weights use MXFP4 quantization.

**「Self-hosting is out of reach for most」** Self-hosting the released weights is a datacenter-scale undertaking rather than a workstation download: reports put the full weights at roughly 1.63 TB in MXFP4, and commenters estimate a node on the order of eight B300 GPUs to serve it. That pushes most users toward the API or third-party hosts, where one commenter reports OpenRouter already lists the model with providers claiming higher throughput than Moonshot&\#x27;s own endpoint at the same price. Teams planning commercial deployment should also read the custom &quot;Kimi K3 License&quot; on Hugging Face rather than assuming permissive open-source terms.

**「Community discussion」** Commenters split on whether the model is genuinely capable or &quot;benchmaxxed&quot;: one said their own testing did not show benchmark-gaming and called it a strong open release slightly off the frontier, while another argued it does not clearly beat DeepSeekV4.1-Flash and scores poorly on a rival&\#x27;s internal benchmarks. Others focused on practicality, estimating an 8x B300 node would be needed to run it locally and noting that third-party providers on OpenRouter are already hosting it with throughput reportedly higher than Moonshot&\#x27;s own endpoint.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/moonshotai/Kimi-K3">moonshotai/Kimi-K3 · Hugging Face</a></li>
<li><a href="https://www.developersdigest.tech/blog/kimi-k3-open-weights-huggingface-release">Kimi K 3 Weights Land on HuggingFace: 2 . 8 T Open Frontier Model...</a></li>

</ul>
</details>

**Tags**: `#open-weights`, `#multimodal-ai`, `#mixture-of-experts`, `#long-context`, `#Kimi`

---

<a id="item-tech-news-6"></a>
### [AI vulnerability auditing confronts four decades of software debt](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

An IEEE Spectrum analysis argues that AI-driven vulnerability discovery is pushing the software industry to confront technical debt accumulated over roughly 40 years, framing the shift as debt repayment rather than a single product release. The piece is an argument about industry practice, not an independently measured result or a vendor announcement. On Hacker News, a large thread disputed the premise, asking whether AI auditing amounts to genuine debt payoff or a compulsory treadmill of feature-neutral fix-work.

hackernews · pseudolus · Nov 4, 11:52 · [Discussion](https://news.ycombinator.com/item?id=50364336)

**「Context」** The debate follows the late-October disclosure of PHP2Shell, a vulnerability affecting sites built on WordPress, Drupal, and other PHP-based platforms — reportedly including NASA, Wikipedia, and White House sites — that could read sensitive data and run malicious code on the host server. IEEE Spectrum frames that episode as the point where AI-assisted vulnerability discovery began exposing decades of accumulated shortcuts faster than maintainers can address them.

**「Community discussion」** The most substantive pushback came from commenters who argued that AI auditing may create a “compulsory endless treadmill of feature-neutral fix-work,” noting that many flaws require restructuring rather than narrow patches. Others said AI makes real the open-source promise that someone else will audit the code, while some hoped the effort ultimately yields more robust software.

<details><summary>References</summary>
<ul>
<li><a href="https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability">PHP2Shell Is a Wakeup Call for AI in Cybersecurity - IEEE ...</a></li>
<li><a href="https://www.atlasnews.ai/articles/technology/the-php2shell-vulnerability-heralds-cybersecurity-hell">The PHP2Shell Vulnerability Heralds Cybersecurity Hell</a></li>

</ul>
</details>

**Tags**: `#ai-security`, `#vulnerability-discovery`, `#open-source`, `#technical-debt`, `#cybersecurity`

---

<a id="item-tech-news-7"></a>
### [AMD expects first-ever Q4 revenue lead over Intel at $17B](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

AMD&\#x27;s Q4 guidance projects roughly $17 billion in revenue, a figure that would exceed Intel&\#x27;s Q4 projection and give AMD the higher quarterly revenue total for the first time. The report describes this as an expectation based on guidance, not a confirmed sales result; the final ranking will depend on the companies&\#x27; actual quarterly reports. For AMD, Intel, and their customers, the forecast points to a possible change in vendor leverage across CPUs and accelerators, but it does not establish a unit-share or technical lead.

hackernews · rbanffy · Nov 4, 15:38 · [Discussion](https://news.ycombinator.com/item?id=50367125)

**「What the comparison actually measures」** The crossover is measured in quarterly revenue, not processor unit shipments: Intel has guided for $15 billion to $16 billion for the same period, against AMD&\#x27;s roughly $17 billion midpoint forecast at plus or minus 3%. Intel has historically been the larger of the two x86 vendors by revenue, and AMD&\#x27;s own growth is being driven by data-center products rather than its client CPU line.

**「Impact」** For buyers and investors, the practical consequence is that AMD&\#x27;s Q4 positioning will be judged on reported data-center and client revenue, not on the guidance headline; a miss would leave Intel&\#x27;s revenue lead intact.

**「Community discussion」** Commenters were split on what the projected lead means: one argued it reflects Intel&\#x27;s missteps more than AMD&\#x27;s strength, citing Intel&\#x27;s Optane exit and AI strategy, while another said AMD&\#x27;s growth is driven by Instinct accelerators even though those sales remain small against Nvidia. Several readers cited Intel 13th- and 14th-generation voltage problems and security concerns as reasons they favor AMD, while others framed the shift as healthy competition.

<details><summary>References</summary>
<ul>
<li><a href="https://wccftech.com/amd-is-set-to-out-earn-intel-for-the-first-time-in-its-history-guiding-to-17-billion-in-q4-revenue-against-intels-15-5-billion-midpoint-projection/">AMD Is Set To Out-Earn Intel For The First Time In Its ...</a></li>
<li><a href="https://latestintech.com/amd-q4-revenue-guidance-beats-intel/">AMD Q4 Revenue Guidance Signals Major Intel Upset</a></li>

</ul>
</details>

**Tags**: `#AMD`, `#Intel`, `#CPU market`, `#semiconductor industry`, `#AI accelerators`

---

<a id="item-tech-news-8"></a>
### [Tencent releases Hy4 open-weight model with scientific and game-dev adaptations](https://hy.tencent.ai/research/hy4) ⭐️ 7.0/10

Tencent released Hy4, an open-weight foundation model, with two open-sourced scientific companions for researchers: HyCell for single-cell representation and HyPDE for physical-field modeling; Tencent says both were co-developed by Hy4 and Hyra 2.0. For game developers, Tencent adapted Hy4 with its Interactive Entertainment Group for feature implementation, gameplay logic, state tracking, and asset pipelines, and added support for Unreal Engine, Unity, Godot, and multiplayer development. Tencent itself says Hy4 still trails top proprietary models on internal benchmarks for research-level mathematics, long-horizon coding, model self-improvement, and advanced visual question answering, and the supplied material includes no independent benchmark verification.

hackernews · Philpax · Nov 4, 14:11 · [Discussion](https://news.ycombinator.com/item?id=50365780)

**「Prior context」** Tencent had already circulated a Hy4 preview before this full release, so the comparison point cited in the material is the preview rather than a first-generation model. Tencent&\#x27;s own launch announcement says the model weights and system cards will be published &quot;in the coming days,&quot; so at announcement time the open-weight status rested on a stated plan rather than artifacts already available for download.

**「Availability and engine support」** Developers working in Unreal Engine, Unity, or Godot are the immediate beneficiaries of Tencent&\#x27;s engine-specific adaptation, with the company reporting a 19.1% gain on its GameDev benchmark and 9.8% on GameLogic versus the Hy4 preview. However, Tencent says model weights and system cards will be released only “in the coming days,” so teams cannot yet download and evaluate the open-weight model locally.

**「Community discussion」** Commenters praised the open release of HyCell and HyPDE as a contrast to proprietary restrictions on scientific work, while one developer reported that Hy4 fell between GPT-6.1 Sol and GPT-6.1 Terra on Plotly&\#x27;s data-analytics cost/accuracy benchmark but was very slow. Another commenter singled out Tencent&\#x27;s acknowledgment of the remaining gap to proprietary models as a positive sign.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy4, Joining the Ranks of the World&#x27;s ...</a></li>
<li><a href="https://hy.tencent.ai/research/hy4">Tencent Hy</a></li>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy4, Joining the Ranks of the World&#x27;s ...</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#LLM release`, `#game development`, `#scientific machine learning`, `#Tencent Hy4`

---

<a id="item-tech-news-9"></a>
### [Huginn weight sharing on B200 cuts HBM reads only when weights fit cache](https://www.reddit.com/r/MachineLearning/comments/1xnskvt/do_looped_transformers_save_hbm_traffic_profiling/) ⭐️ 7.0/10

A new profiling study of Huginn-style looped transformers on an Nvidia B200 found that reusing one set of weights across iterations saves storage but does not by itself reduce HBM traffic. In a chain of eight matmuls with a shared 72 MiB weight, runtime was 24% faster than with eight identical copies and almost no data was read from HBM; at 288 MiB, larger than L2, the advantage disappeared. In the full Huginn Core teaching implementation with random weights, eight iterations took about eight times as long as one and read about eight times as much data from HBM. The author asks whether persistent kernels could keep recurrent weights on chip and provides code and Nsight Compute data, but the results are preliminary and from one GPU.

reddit · r/MachineLearning · /u/2dayyy6 · Nov 4, 16:26

**「Background」** Looped transformers such as Huginn reuse one set of weights across repeated iterations instead of giving every layer its own parameters, which reduces the storage needed for the model. The performance question is separate: on a GPU, each iteration still has to obtain those weights from HBM unless they remain resident in cache \(L2 on the B200\), so weight sharing alone does not guarantee lower memory traffic.

**「Impact」** Developers considering looped transformers should not treat weight sharing as an HBM-bandwidth optimization unless the recurrent weights fit in cache or a persistent-kernel scheme keeps them resident; the profile shows the full Huginn loop still scales HBM reads roughly linearly with iteration count.

**Tags**: `#looped transformers`, `#HBM bandwidth`, `#GPU profiling`, `#memory hierarchy`, `#Huginn`

---

<a id="item-tech-news-10"></a>
### [Oracle Reportedly Cancels $7B AI Chip Lease With Tencent](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 7.0/10

Oracle reportedly canceled a roughly $7 billion, five-year AI chip lease with Tencent after U.S. officials raised concerns and the company faced pressure from the Trump administration. The deal would have let Tencent rent about 100,000 advanced AI chips through Oracle data centers in Southeast Asia, with an upfront payment of about 30%, to obtain chips it could not access in China. The report comes from a brief aggregation citing the Financial Times, and the supplied material does not include confirmation from Oracle or Tencent.

telegram · zaihuapd · Nov 4, 11:01

**「Background」** The reported five-year lease was structured around Oracle data centers in Southeast Asia, letting Tencent rent advanced AI chips that it could not use inside China rather than import them directly. The arrangement drew concerns from US officials before Oracle canceled it, according to the report.

**Tags**: `#AI chips`, `#export controls`, `#Oracle`, `#Tencent`, `#data centers`

---

<a id="item-tech-news-11"></a>
### [Huawei tells Ascend 960DT buyers to source Samsung, SK Hynix HBM](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

Huawei has told some customers that its next flagship AI chip, the Ascend 960DT, will rely mainly on Samsung and SK Hynix HBM and that those customers must arrange memory supplies themselves because Chinese HBM capacity is insufficient, The Information reported. The report says the HBM is soldered onto much weaker processors, declared under processor codes for shipment to Hong Kong, carried into mainland China by individuals, and then heated off; a Shenzhen chip broker quoted HBM3E at about $4,000 per unit, up from a few hundred dollars a year earlier. The account is based on secondary reporting and does not establish that the Ascend 960DT has shipped.

telegram · zaihuapd · Nov 4, 14:52

**「Background」** High-bandwidth memory — stacked DRAM mounted alongside an AI die — is the scarce input for accelerators such as Ascend. China&\#x27;s domestic supplier CXMT is reported to be achieving only 20%–30% yields on HBM3E, well below the roughly 70% attributed to SK hynix, according to Reuters as cited by TrendForce. The workaround is not new: teardowns had already found Samsung and SK hynix memory inside Huawei&\#x27;s Ascend 910C, and TechRadar reported that pairing top-tier HBM with deliberately useless processors so the package clears export rules as a low-end chip is an established trick.

**「Procurement burden shifts to buyers」** Customers deploying the Ascend 960DT must budget for and procure Samsung or SK Hynix HBM separately from the chip, since Huawei has specified those vendors rather than a domestic substitute. With a single HBM3E stack reportedly quoted at roughly $4,000 in Shenzhen, memory now becomes an independent cost and availability variable in cluster planning, and buyers should confirm vendor part numbers and lead times before committing to deployment schedules. TrendForce similarly reports that China&\#x27;s domestic memory suppliers are struggling to meet HBM demand, with Huawei also working with DeepSeek to optimize the chip for pre-training.

<details><summary>References</summary>
<ul>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server Packages...</a></li>
<li><a href="https://www.techradar.com/pro/smugglers-are-reportedly-soldering-top-tier-hbm-onto-deliberately-useless-processors-to-sneak-it-into-china-and-the-trick-isnt-new">Smugglers are reportedly soldering top-tier HBM onto... | TechRadar</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server...</a></li>

</ul>
</details>

**Tags**: `#Huawei Ascend`, `#HBM supply chain`, `#AI chips`, `#export controls`, `#semiconductor smuggling`

---

<a id="item-tech-news-12"></a>
### [Bluetooth HDT standard lifts LE peak throughput to 7.5 Mbps](https://www.bluetooth.com/press/bluetooth-high-data-throughput-opens-a-new-chapter-in-wireless-performance/) ⭐️ 7.0/10

The Bluetooth SIG adopted Bluetooth High Data Throughput \(HDT\), raising Bluetooth LE&\#x27;s peak rate from 2 Mbps to 7.5 Mbps—nearly four times—while improving capacity, energy efficiency, and reliability. HDT is an optional feature of Bluetooth Core 7.0 and is designed to coexist with older devices, so it is not a baseline requirement. The first standardized application is high-end wireless audio with lossless and high-resolution support, expected in 2027.

telegram · zaihuapd · Nov 5, 01:39

**「Background」** Bluetooth LE has until now topped out at 2 Mbps, a ceiling that limits how much data a link can carry and is the constraint the SIG is addressing with HDT for lossless, high-resolution audio. HDT is an optional feature in Bluetooth Core 7.0 and can coexist with older devices, so the higher 7.5 Mbps rate applies only when the equipment on both ends supports it.

**「Device impact」** Hardware makers and developers targeting lossless wireless audio will need devices built to Core 7.0 with the optional HDT feature; existing Bluetooth LE devices can coexist but will not gain the higher rate or lossless audio without HDT-capable hardware.

**Tags**: `#Bluetooth`, `#wireless standards`, `#audio`, `#hardware`, `#protocols`

---