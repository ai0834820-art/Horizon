---
layout: default
title: "Horizon Summary: 2026-11-24 (EN)"
date: 2026-11-24
lang: en
---

> From 35 items, 11 important content pieces were selected

---

**Technology News**
1. [Nvidia board reinstates Jensen Huang as CEO, citing US government input](#item-tech-news-1) ⭐️ 8.0/10
2. [Zhipu&\#x27;s GLM-5.4 debuts looped transformer for coding](#item-tech-news-2) ⭐️ 8.0/10
3. [Ladybird releases first alpha for macOS and Linux](#item-tech-news-3) ⭐️ 8.0/10
4. [NariQ&\#x27;s 3-bit Qwen3.8-27B GGUF claims BF16 quality in 10 GB](#item-tech-news-4) ⭐️ 7.0/10
5. [Codex2api suspected supply-chain compromise: backdoored releases, stolen secrets](#item-tech-news-5) ⭐️ 7.0/10
6. [Meta AI Chief Cites Claude-Assisted Riemann Proof in Superintelligence Warning](#item-tech-news-6) ⭐️ 7.0/10
7. [Alpöge&\#x27;s AI-assisted Riemann proof in Lean criticized as vacuous](#item-tech-news-7) ⭐️ 7.0/10
8. [Coalition asks EU to open case on Apple iPhone browser limits](#item-tech-news-8) ⭐️ 7.0/10
9. [Singapore Says It Won&\#x27;t Be Conduit for Evading US Chip Controls](#item-tech-news-9) ⭐️ 7.0/10
10. [Anthropic claims internal Claude found VP≠VNP; Lean 4 proof awaits review](#item-tech-news-10) ⭐️ 7.0/10

**Technology Blog**
1. [ERNIE 5.5 Flash Preview Gets Day-0 vLLM Plugin Support](#item-tech-blog-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Nvidia board reinstates Jensen Huang as CEO, citing US government input](https://www.cnbc.com/2026/11/23/nvidia-jensen-huang-ceo.html) ⭐️ 8.0/10

Nvidia&\#x27;s board has reinstated Jensen Huang as president, CEO and board director, according to a company newsroom release linked from the Hacker News submission; the linked CNBC report carries a Nov. 23, 2026 date. The board statement, quoted in the discussion thread, says it &quot;received input from senior levels of the United States government&quot; and is confident that Huang&\#x27;s reinstatement &quot;poses no national security risk.&quot; The submission supplies only the two links and no article text, so the sequence of Huang&\#x27;s removal, the substance of the government&\#x27;s involvement, and the board vote could not be verified from the available material.

hackernews · jaz · Nov 23, 14:00 · [Discussion](https://news.ycombinator.com/item?id=50611576)

**「Background」** The Guardian reported that the reinstatement reverses the board’s earlier decision to remove Huang as chief executive, following intervention by President Trump. Nvidia’s own announcement says the board voted unanimously and made the change effective immediately after discussions with Huang.

**「Impact」** The reversal restores the executive associated with Nvidia&\#x27;s AI accelerator roadmap after a gap one commenter describes as under two weeks, avoiding a prolonged leadership vacuum for the company&\#x27;s customers and partners. The board&\#x27;s public citation of executive-branch input as part of a CEO personnel decision is itself the notable governance artifact, though the supplied material gives no detail on what that input consisted of or whether it will be disclosed further.

**「Community Discussion」** Commenters focused on the board&\#x27;s national-security language and its liability implications, with one arguing that Delaware&\#x27;s Caremark standard plus a reported DoJ decision not to prosecute would likely insulate directors, and another expressing surprise that a removal reversed within roughly two weeks was unanimous. Several drew a comparison to OpenAI&\#x27;s 2023 board episode to argue that a firm&\#x27;s nominal governance structure is not necessarily its real one, while others disputed the premise that the intervention was covering up wrongdoing and criticized what they saw as inconsistent treatment of Nvidia versus ASML and Japanese chip-equipment makers under China export controls.

<details><summary>References</summary>
<ul>
<li><a href="https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Board-Reinstates-Jensen-Huang-as-President-CEO-and-Board-Director/default.aspx">NVIDIA Corporation - NVIDIA Board Reinstates Jensen Huang as ...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/23/jensen-huang-reinstated-as-nvidia-chief-executive">Jensen Huang reinstated as Nvidia CEO after Trump intervenes</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#semiconductor industry`, `#corporate governance`, `#US national security policy`, `#Hacker News`

---

<a id="item-tech-news-2"></a>
### [Zhipu&\#x27;s GLM-5.4 debuts looped transformer for coding](https://z.ai/blog/glm-5.4) ⭐️ 8.0/10

Zhipu AI \(Z.ai\) released GLM-5.4, its first model built on a looped transformer architecture in which a group of weight-shared layers runs for multiple iterations, refining hidden states so the network is effectively deeper without increasing parameter count. The model is not available as open weights and could not, at the time of writing, be reached through Z.ai&\#x27;s regular API or OpenRouter; access required a Coding Plan subscription, whose API key worked against the same OpenAI-compatible Responses endpoint at https://api.z.ai/api/v1. The release follows Thinking Machines Lab&\#x27;s Inkling 2 Mini on November 20, which also described itself as a looped transformer running middle layers three times per token. The source reports no benchmark numbers and only informal testing: Simon Willison&\#x27;s pelican SVG renders at low, high, and max effort looked similar in quality to GLM-5.3 and closer to OpenAI and Anthropic outputs than the distinctive 5.1 and 5.2 generations.

hackernews · foohis · Nov 23, 10:06 · [Discussion](https://news.ycombinator.com/item?id=50609685)

**「Looped transformer context」** In a standard Transformer, each layer runs once per forward pass. A loop transformer instead runs a set of weight-shared layers for multiple iterations, refining hidden states and increasing effective depth without raising the parameter count. GLM-5.4 follows Z.ai&\#x27;s earlier GLM-5.3 and arrives shortly after Thinking Machines Lab&\#x27;s November 20 Inkling 2 Mini, which also uses a looped design—running its middle layers three times per token.

**「Access path and tooling friction」** Developers cannot reach GLM-5.4 through Z.ai&\#x27;s regular API plan or OpenRouter; trial access requires the Coding Plan subscription, whose keys nevertheless work against the same OpenAI-compatible Responses API base URL \(https://api.z.ai/api/v1\), so existing OpenAI-format clients can be repointed with a new key rather than rewritten. Client tooling lags the release: the existing llm-zai plugin did not yet support the model, prompting Simon Willison to publish a duplicate llm-glm plugin that he expects to retire once llm-zai catches up.

**「Community discussion」** Commenters praised Zhipu for publishing architectural detail that Western labs keep private, with one arguing looped transformers are an obvious direction because the standard Transformer behaves like an unrolled loop that pairs unrelated weights. A competing complaint held that Chinese models&\#x27; long &quot;marathon thinking&quot; sessions make them slow and second-guess themselves on simple tasks, which one commenter suspected is how they close the gap on benchmarks, while another explained that looping layers on-chip targets the memory-bandwidth bottleneck of moving weights from HBM.

**Tags**: `#LLMs`, `#AI coding`, `#looped transformers`, `#Zhipu AI`, `#model release`

---

<a id="item-tech-news-3"></a>
### [Ladybird releases first alpha for macOS and Linux](https://ladybird.org/posts/alpha/) ⭐️ 8.0/10

Ladybird released its first alpha, with installable builds for macOS and Linux instead of requiring users to compile it themselves. The independent browser implements most core engine components itself—HTML parsing, CSS, layout, JavaScript, and WebAssembly—while relying on external HarfBuzz, Skia, ffmpeg, and SQLite. A tester reported that most sites worked, including an ffmpeg WebAssembly tool and a Pyodide REPL, but Datasette Lite failed because navigator.serviceWorker.startMessages is not implemented; the source contains a FIXME for Service Workers. The project cautions that some sites will not work and the browser will sometimes crash, and it asks users to report broken sites.

hackernews · janvdberg · Nov 23, 16:13 · [Discussion](https://news.ycombinator.com/item?id=50614249)

**「Background」** Ladybird is a from-scratch browser project that implements most core components itself, including HTML parsing, CSS, layout, JavaScript, and WebAssembly, while relying on external libraries such as HarfBuzz, Skia, ffmpeg, and SQLite. It also draws code from its predecessor, SerenityOS, and before this alpha, users had to compile the browser themselves; the alpha release provides downloadable builds for macOS and Linux.

**「Impact」** For users and web developers, the alpha provides a way to test an independent engine on real sites without building it, and the browser includes in-app broken-site reporting. It is not yet a replacement daily driver: crashes are expected, Service Worker support is incomplete, and the project is explicitly seeking security researchers to probe the new attack surface.

**「Community discussion」** Commenters reported that a range of sites, from overloaded news sites to Proxmox/NoVNC, rendered correctly, with one saying NoVNC felt snappier than in Firefox, though another noted slightly jerky scrolling. Others argued Ladybird should prioritize anti-fingerprinting measures such as spoofed or randomized JavaScript values and more granular permissions, while one asked what precautions alpha users should take.

**Tags**: `#browsers`, `#open-source`, `#web-engines`, `#Ladybird`, `#software-engineering`

---

<a id="item-tech-news-4"></a>
### [NariQ&\#x27;s 3-bit Qwen3.8-27B GGUF claims BF16 quality in 10 GB](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

NariQ has published 3-bit, 2.5-bit, and 2-bit GGUF quantizations of Qwen3.8-27B, including a 10 GB file, claiming near-BF16 quality across agentic tasks, math, multilingual reasoning, and image understanding. NariQ says this is the first 3-bit-or-lower quantization to retain BF16-level performance on long-horizon agentic tasks; its own benchmarks put 3-bit and 2.5-bit near or slightly above BF16 on DeepSWE \(41.0 and 41.9 vs 39.8\) and Terminal-Bench \(63.8 and 60.2 vs 62.6\), while 2-bit falls to 28.6 and 52.4. The quantizations currently require NariQ&\#x27;s llama.cpp fork, and NariQ reports decode speed comparable to other quants on an RTX PRO 6000. These are vendor benchmarks and claims that still need independent validation.

hackernews · toebee · Nov 23, 13:42 · [Discussion](https://news.ycombinator.com/item?id=50611402)

**「Why a custom llama.cpp fork is needed」** GGUF is the file format llama.cpp uses to run quantized models locally, and pushing to lower bit-widths normally trades accuracy and long-context behavior for a smaller file and lower memory use. Custom llama.cpp forks that add new quantization types are already an established way to improve that trade-off, which is why NariQ&\#x27;s files currently need the project&\#x27;s own fork rather than upstream llama.cpp.

**「Impact」** Using these files is not a drop-in upstream llama.cpp operation: users must build the nari-labs fork, and on an 18 GB M3 Pro the reported decode rate is about 3.8 tok/s with the 3.0 bpw file \(4.9 tok/s with 2.0 bpw\), far slower than CUDA, so Mac users should verify throughput before depending on it for interactive work.

**「Community discussion」** Commenters were skeptical of quantization benchmark claims even while welcoming the broader checks: rao-v said high-compute QAT-style efforts often over-optimize on benchmark-like data, while WithinReason argued the plots suggest most gains come from a harness difference rather than the model. jedbrooke reported about 3.8 tok/s on an 18 GB M3 Pro with the 3.0 bpw file and asked whether a 16 GB Mac could run it.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/ikawrakow/ik_llama.cpp">GitHub - ikawrakow/ik_ llama . cpp : llama . cpp fork with additional...</a></li>

</ul>
</details>

**Tags**: `#quantization`, `#local LLM inference`, `#Qwen`, `#llama.cpp`, `#model compression`

---

<a id="item-tech-news-5"></a>
### [Codex2api suspected supply-chain compromise: backdoored releases, stolen secrets](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 7.0/10

A Telegram incident summary alleges that the Codex2api author’s account was compromised and that attackers bypassed the main branch by pushing a tag, causing the Release build to ship a backdoored version. The report says v3.1.11 removed authentication, enabling unauthenticated remote command execution, and that a workflow exfiltrated 16 GitHub Actions secrets from at least 21 repositories under the same account. Users who installed or updated to v3.1.10–v3.1.12 are urged to stop using it, roll back to v3.1.9, and rotate the GitHub token, SSH keys, database credentials, DeepSeek and other related secrets. The claims have not been independently verified in the supplied material.

telegram · zaihuapd · Nov 23, 11:21

**「Release pipeline exposure」** Codex2api publishes through GitHub Actions, where pushing a tag can trigger a release build; such workflows can read repository secrets and publish artifacts without merging to the default branch. Similar GitHub Actions credential-theft activity was documented before this incident: the GhostAction campaign reported in October 2026 injected malicious workflow files to steal CI/CD secrets, and November 2026 reporting described stolen GitHub credentials being used to push malicious workflow code.

**「Required response」** Operators who installed or updated to Codex2api v3.1.10–v3.1.12 should stop the service, redeploy v3.1.9, and rotate GitHub tokens, SSH keys, database credentials, and DeepSeek API keys. The urgency is concrete: v3.1.11 removed authentication, potentially allowing unauthenticated remote command execution, and the malicious workflow reportedly exported 16 GitHub Actions secrets across at least 21 repositories under the same account.

<details><summary>References</summary>
<ul>
<li><a href="https://aviatrix.ai/threat-research-center/ghostaction-github-actions-credential-theft-2026/">GhostAction GitHub Actions Supply Chain Attack Analysis 2026</a></li>
<li><a href="https://cyberpress.org/github-attack-exposes-secrets/">GitHub Supply Chain Attack Exposes Developer Secrets as ...</a></li>

</ul>
</details>

**Tags**: `#supply-chain attack`, `#GitHub Actions`, `#security incident`, `#credential rotation`, `#open source security`

---

<a id="item-tech-news-6"></a>
### [Meta AI Chief Cites Claude-Assisted Riemann Proof in Superintelligence Warning](https://thenextweb.com/news/metas-ai-chief-says-superintelligence-is-arriving-and-control-is-at-risk) ⭐️ 7.0/10

Meta chief AI officer and Superintelligence Labs head Alexandr Wang said in a long X post that superintelligence is no longer a &quot;someday&quot; issue, citing a Riemann hypothesis proof that mathematician Levent Alpöge produced with Anthropic&\#x27;s Claude and that the Lean and Mathlib community machine-verified on Saturday. Wang argued that the gap between AI and top humans now comes down to specific knowledge, engineering integration and experimentation, and warned that humans will struggle to control systems that can self-improve without limit or are 1,000 times smarter, calling for urgent safety, alignment and safeguards research. The proof has no human-readable version, and the item is a brief secondhand summary without independent technical substantiation.

telegram · zaihuapd · Nov 23, 12:49

**「Background」** Lean is a proof assistant that lets mathematical arguments be checked as code, and Mathlib is its main mathematics library. According to The Guardian, Anthropic employee Levent Alpöge published Lean code for a claimed Riemann hypothesis proof rather than a human-readable proof, prompting mathematicians to try to verify it. ZeroHedge reported that the Lean FRO and Mathlib Initiative said on Saturday they had full confidence in the proof, and Al Jazeera reported that Wang’s warning followed Alpöge’s announcement.

<details><summary>References</summary>
<ul>
<li><a href="https://www.aljazeera.com/economy/2026/11/23/ai-superintelligence-arriving-warns-top-meta-executive">Artificial superintelligence ‘arriving’, warns top Meta... | Al Jazeera</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/21/anthropic-riemann-hypothesis-solved-claude-ai">Two groups verify mathematician’s claim that Claude ... | The Guardian</a></li>
<li><a href="https://www.zerohedge.com/science/did-claude-just-solve-maths-most-famous-problem-even-anthropics-mathematician-admits-timing">Mathematicians Confirm Claude Solved Math&#x27;s Most... | ZeroHedge</a></li>

</ul>
</details>

**Tags**: `#AI safety`, `#superintelligence`, `#Riemann hypothesis`, `#Lean/Mathlib`, `#Anthropic Claude`

---

<a id="item-tech-news-7"></a>
### [Alpöge&\#x27;s AI-assisted Riemann proof in Lean criticized as vacuous](https://x.com/i/web/status/2124987173439209561) ⭐️ 7.0/10

An AI-assisted claim by Alpöge and Claude to have formalized a proof of the Riemann Hypothesis and its generalized form in Lean has been criticized as potentially vacuous after researchers found key definitions were tautological. The release consisted of 17 million lines of Lean across 175,000 files and no human-readable proof; the Lean and Mathlib community reportedly said the next day it had &quot;sufficient confidence&quot; that the code proved the proposition. Researchers then pointed to definitions written as tautologies and vacuous geometric conditions, suggesting the proof may not establish the intended theorem. Alpöge conceded that the &quot;250,000 pages is a joke&quot; and that the code was &quot;full of garbage but compiles,&quot; calling the criticism entirely reasonable.

telegram · zaihuapd · Nov 24, 01:29

**「Background」** Lean is a proof assistant that mechanically checks formal proofs, so code that compiles need not establish a meaningful theorem if its definitions are vacuous. The disputed claim followed Levent Alpöge&\#x27;s 20 November 2026 announcement, made with Anthropic&\#x27;s Claude, of proofs of the Riemann Hypothesis and the Generalized Riemann Hypothesis for Dirichlet L-functions; an event page dates the Lean development from 6 October to 16 November and describes an early milestone as a descendant of Stepanov&\#x27;s argument for the Riemann Hypothesis over finite fields.

**「Impact」** For Lean users, the episode shows that a compiling, machine-checked artifact can still fail to prove the intended claim if its definitions are tautological; the practical check is to audit the formal statement and definitions, not only whether the code compiles.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Riemann_hypothesis">Riemann hypothesis - Wikipedia</a></li>
<li><a href="https://math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/">Alpöge / Claude proof of the Generalized Riemann Hypothesis</a></li>

</ul>
</details>

**Tags**: `#AI for mathematics`, `#Lean theorem proving`, `#formal verification`, `#LLM hype`, `#Riemann Hypothesis`

---

<a id="item-tech-news-8"></a>
### [Coalition asks EU to open case on Apple iPhone browser limits](https://appleinsider.com/articles/26/11/23/eu-urges-to-challenge-apples-grip-on-iphone-browsers?utm_source=rss) ⭐️ 7.0/10

A coalition including Mozilla and Shopify has sent a letter urging the European Commission to open a formal case against Apple’s iPhone browser restrictions, according to a secondhand account of the campaign. The signatories say they represent roughly 45,000 to 55,000 EU businesses and organizations, with endorsements open until Dec. 3, 2026. They argue that although Apple now allows rival browsers to use their own engines in the EU under the Digital Markets Act, technical and legal requirements keep existing users tied to WebKit and businesses dependent on the App Store.

telegram · zaihuapd · Nov 24, 03:02

**「Background」** The EU&\#x27;s Digital Markets Act is the competition law under which Apple allowed rival browser engines on iPhone in the EU; in March 2025 the European Commission ordered Apple to take steps to comply with the law. The coalition&\#x27;s letter argues that Apple&\#x27;s browser changes still have not delivered meaningful competition, according to MacRumors&\#x27; report.

**「Impact」** For iOS browser vendors and web-app developers, the dispute centers on whether Apple must provide a practical path for existing EU users to move off WebKit; the coalition estimates that moving half of native iOS apps to the web would save EU businesses €11 billion in annual development costs and €1.3 billion in App Store fees, but those figures are the campaign’s estimates rather than independently verified results.

<details><summary>References</summary>
<ul>
<li><a href="https://www.macrumors.com/">MacRumors: Apple News and Rumors</a></li>
<li><a href="https://www.cnbc.com/2025/03/19/eu-orders-apple-to-open-up-app-store-risking-trump-retaliation.html">EU hits Google, Apple with antitrust actions risking Trump retaliation</a></li>

</ul>
</details>

**Tags**: `#Apple`, `#EU DMA`, `#iOS browsers`, `#WebKit`, `#tech regulation`

---

<a id="item-tech-news-9"></a>
### [Singapore Says It Won&\#x27;t Be Conduit for Evading US Chip Controls](https://www.bloomberg.com/news/articles/2026-11-24/singapore-won-t-be-conduit-to-skirt-us-chip-curbs-wong-says) ⭐️ 7.0/10

Prime Minister Lawrence Wong said Singapore will not be used as a conduit for evading US chip export controls, and authorities are investigating Megaspeed&\#x27;s purchases of Nvidia chips. The statement came one day after the US Commerce Department added Megaspeed and six other Southeast Asian firms to its trade blacklist. The Federal Register cited a significant risk that the firms could divert advanced computing products to unauthorized users and listed affiliates in Malaysia and Thailand; Reuters reported that Alibaba&\#x27;s Singapore subsidiary Apex Enterprise Solutions was also named, while Alibaba denied transferring controlled advanced computing chips.

telegram · zaihuapd · Nov 24, 05:03

**「Context: US chip blacklist」** The US Commerce Department added Megaspeed and six other Southeast Asian firms to its trade blacklist one day before Wong spoke, according to the report. The Federal Register cited a significant risk that the companies could divert advanced computing products to unauthorized users. Singapore authorities were already investigating Megaspeed’s Nvidia chip purchases when the prime minister addressed the issue.

**「Supply-chain impact」** Companies in Singapore, Malaysia and Thailand that use Megaspeed or the six other listed firms as procurement or cloud intermediaries now face restricted US trade exposure, so suppliers and customers should verify end users and licensing status before shipping advanced Nvidia hardware. The inclusion of Alibaba&\#x27;s Singapore subsidiary Apex Enterprise Solutions—which denies transferring controlled chips—shows that even firms denying diversion may need to document compliance to keep US-linked supply lines open.

<details><summary>References</summary>
<ul>
<li><a href="https://uz.kursiv.media/en/2026-11-24/us-blacklist-megaspeed-alice-huang/">US blacklists Megaspeed , once led by China spy suspect Alice Huang</a></li>
<li><a href="https://www.bbc.com/news/articles/cv98xpg5dg5zo">US to blacklist Asian AI firm Megaspeed after Nvidia scandal</a></li>

</ul>
</details>

**Tags**: `#chip export controls`, `#semiconductors`, `#AI hardware`, `#Singapore`, `#Nvidia`

---

<a id="item-tech-news-10"></a>
### [Anthropic claims internal Claude found VP≠VNP; Lean 4 proof awaits review](https://github.com/anthropics/formal-math/blob/main/vp-vnp/README.md) ⭐️ 7.0/10

Anthropic has reportedly published a paper, “VP ≠ VNP over every field,” and a Lean 4 formalization, both said to be written by an internal research Claude model; the paper claims a superpolynomial arithmetic-circuit lower bound that would make VP a proper subclass of VNP and resolve Valiant’s 1979 algebraic complexity conjecture, though it does not address P versus NP. The repository says the proof underwent a three-standard-axiom audit and an independent nanoda kernel check with no \`sorry\` outside reserved files, but no human mathematician has read it, Lean cannot confirm the formal statement matches the claimed theorem, and Appendix Q lists discrepancies pending independent review.

telegram · zaihuapd · Nov 24, 06:02

**「Background」** Valiant&\#x27;s 1979 conjecture is the algebraic-complexity analogue of P versus NP: VP and VNP classify polynomials by whether they admit polynomial-size arithmetic circuits, and proving VP ≠ VNP would separate the two classes. Lean 4 checks a proof against its kernel only for the statement as formalized, which is why the source flags that no human has yet confirmed the formal statement matches the paper&\#x27;s claimed theorem.

**「Verification gap」** Researchers and teams citing the result should treat VP ≠ VNP as unverified until human reviewers reconcile the Lean 4 statement with the paper’s theorem, because the source says Lean cannot establish that the formalized statement matches the claimed proposition. Appendix Q’s listed discrepancies are the concrete starting point before relying on the claim in citations or further formalization.

**Tags**: `#computational complexity`, `#Lean 4`, `#formal verification`, `#AI for mathematics`, `#Anthropic`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [ERNIE 5.5 Flash Preview Gets Day-0 vLLM Plugin Support](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 7.0/10

rss · vLLM Blog · Nov 24, 00:00

**「Background」** ERNIE 5.5 Flash Preview is a 280B-parameter sparse mixture-of-experts model with 14B active parameters, a 1M-token context, and tool calling. Baidu&\#x27;s ERNIE team and vLLM built a standalone plugin so it runs on stock vLLM at release without a fork.

**「Solution」** The vLLM-ERNIE plugin installs beside official vllm==0.32.0 and auto-registers through vLLM&\#x27;s general\_plugins entrypoint; architectures load lazily by module path, so other models pay no import cost. To cut memory traffic, the authors fold fixed weights at load time and use fused kernels for VHA cross-head mixing with FP8 quantization, multi-router selection, the MultiMax head, and gated attention, reporting 1.55×–6.53× per-kernel speedups over naive code. For long context, FlashIndexer adds a per-token head router distilled from full DSA token selections on about 1B tokens, plus threshold pre-filtering; the authors report 1.4× indexing speedup at 1M context without changing sparse-attention kernels. The default checkpoint uses MXFP4 W4A8 routed experts with quantization-aware training, FP8 weights and KV cache, and an FP4 indexer; a bundled three-layer DSpark draft model proposes up to seven tokens and is claimed to exceed 4.0 mean acceptance length on coding and agent workloads. vLLM features from prefix caching and CUDA graphs to speculative decoding, PD disaggregation, and KV offload work unchanged, though the reported multipliers and acceptance length lack published benchmark methodology and independent validation.

**「Takeaway」** The authors&\#x27; broader claim is that a thin plugin can deliver day-0, near-native vLLM support without a fork, while architecture-specific fusion and sparse indexing provide the speedups.

**Tags**: `#vLLM`, `#MoE inference`, `#kernel fusion`, `#speculative decoding`, `#plugin architecture`

---