---
layout: default
title: "Horizon Summary: 2026-11-21 (EN)"
date: 2026-11-21
lang: en
---

> From 34 items, 11 important content pieces were selected

---

**Technology News**
1. [KVM Flaw Lets VMs Read AMD Host Memory With Nested Virtualization](#item-tech-news-1) ⭐️ 8.0/10
2. [Aaronson Post Uses &\#x27;Stochastic Parrots&\#x27; to Probe AI Reasoning Claims](#item-tech-news-2) ⭐️ 7.0/10
3. [Terry Tao Post Covers Unforced Navier–Stokes Singularity and Generalized Riemann Hypothesis](#item-tech-news-3) ⭐️ 7.0/10
4. [Thinking Machines releases Inkling 2 Mini, an open-weights looped model for local use](#item-tech-news-4) ⭐️ 7.0/10
5. [Paper Claims Language Models Can Rewrite Their Own Weights](#item-tech-news-5) ⭐️ 7.0/10
6. [Levent Alpöge Claims Generalized Riemann Hypothesis Proof With Lean Formalization](#item-tech-news-6) ⭐️ 7.0/10
7. [Signal moves to block mobile AI agents from capturing chats](#item-tech-news-7) ⭐️ 7.0/10
8. [Draft proof of Generalized Riemann Hypothesis released for review](#item-tech-news-8) ⭐️ 7.0/10
9. [TikTok rolls out global deepfake detection and AI-content checker](#item-tech-news-9) ⭐️ 7.0/10
10. [OpenAI adds background mode for long API requests with token discounts](#item-tech-news-10) ⭐️ 7.0/10
11. [TSMC Said to Pause 16nm-and-Below Orders From Chinese Firms](#item-tech-news-11) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [KVM Flaw Lets VMs Read AMD Host Memory With Nested Virtualization](https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html) ⭐️ 8.0/10

CVE-2026-99312 is a Linux KVM isolation flaw that affects AMD hosts only when nested virtualization is enabled, allowing a virtual machine to read host memory. Researchers reported reading about 127 GB of host memory from inside a VM on DigitalOcean. Upstream fixes shipped on November 18 in stable kernel 7.3.5 and related releases, but Debian and Ubuntu distribution kernels remained unpatched as of the report. Disabling nested virtualization is the suggested mitigation until patched kernels are available.

telegram · zaihuapd · Nov 20, 14:23

**「Why nested virtualization matters」** Nested virtualization—running a hypervisor and its guests inside another VM—is the precondition for CVE-2026-99312, because the flaw sits in KVM&\#x27;s AMD nested-virtualization code. Red Hat rates the issue Moderate rather than Critical because exploitation requires access to a nested guest on an AMD-based KVM host plus specific execution conditions, which limits the exposed population.

**「Impact」** AMD hosts that expose nested virtualization can leak host memory to guest VMs until they run a fixed kernel, such as stable 7.3.5 or a distribution build carrying the patch; Debian and Ubuntu kernels were still unpatched, so administrators should disable nested virtualization as an interim mitigation.

<details><summary>References</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99312">CVE-2026-99312 - Red Hat Customer Portal</a></li>
<li><a href="https://dev.to/etairos/cve-2026-99312-linux-kvm-flaw-let-a-guest-vm-read-127-gb-of-host-memory-on-amd-hosts-4460">CVE-2026-99312: Linux KVM Flaw Let a Guest VM Read 127 GB of ...</a></li>
<li><a href="https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html">Linux KVM Flaw CVE - 2026 - 99312 Lets Guest VMs Access Host...</a></li>
<li><a href="https://www.digitalocean.com/blog/cve-2026-99312-kvm-patch">Virtualization , Responsible Disclosure, and CVE - 2026 - 99312</a></li>

</ul>
</details>

**Tags**: `#KVM`, `#Linux kernel`, `#CVE-2026-99312`, `#AMD virtualization`, `#cloud security`

---

<a id="item-tech-news-2"></a>
### [Aaronson Post Uses &\#x27;Stochastic Parrots&\#x27; to Probe AI Reasoning Claims](https://scottaaronson.blog/?p=10344) ⭐️ 7.0/10

A Scott Aaronson blog post titled &quot;The stochastic parrots have apparently proved the Riemann Hypothesis&quot; uses the &quot;stochastic parrots&quot; critique of large language models to examine claims about AI capability, according to the item&\#x27;s description. The headline is hyperbolic: the item is not evidence of an actual Riemann Hypothesis proof, and the available material contains no source text, paper, or result to verify what Aaronson specifically argues or cites. Discussion of the post on Hacker News centered on whether machine reasoning can be understood or trusted. Readers should treat any claimed LLM mathematical breakthrough described in the commentary as unverified pending the underlying proof or evaluation.

hackernews · stratos123 · Nov 20, 20:03 · [Discussion](https://news.ycombinator.com/item?id=50581084)

**「Background」** “Stochastic parrots” is a 2021 phrase used to criticize large language models as fluent but non-reasoning text predictors. Aaronson’s post responds to social-media claims that LLMs had proved the Riemann Hypothesis; a separate summary describes the underlying claim as Levent Alpöge’s assertion that Anthropic models proved the Generalized Riemann Hypothesis.

**「Impact」** For readers assessing AI capability claims, the item illustrates the gap between a striking headline and a checked result: the post is commentary, not a proof, and no underlying paper or evaluation is provided in the available material. Claims that a model has produced a mathematical breakthrough should be treated as unverified until the argument or benchmark is independently examined.

**「Community discussion」** Commenter janalsncm argued that chess engines such as Stockfish offer &quot;explanations&quot; that are really aggregates of calculations stacked on a neural-network evaluator, leaving &quot;why&quot; questions unsatisfying—an analogy for LLM reasoning. jstummbillig asked whether humans can accept understanding science and engineering to an ever-decreasing degree, while elorant wondered how many mathematicians could reach similar breakthroughs given near-infinite compute.

<details><summary>References</summary>
<ul>
<li><a href="https://scottaaronson.blog/?p=10344">Shtetl-Optimized » Blog Archive » The stochastic parrots have ...</a></li>
<li><a href="https://agihunt.info/en/p/1a1faf3ca85035bde600331be64">Scott Aaronson: Alpöge claims Anthropic models… · AGI Hunt</a></li>

</ul>
</details>

**Tags**: `#AI reasoning`, `#LLM limitations`, `#mathematics`, `#explainability`, `#Hacker News`

---

<a id="item-tech-news-3"></a>
### [Terry Tao Post Covers Unforced Navier–Stokes Singularity and Generalized Riemann Hypothesis](https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/) ⭐️ 7.0/10

Terry Tao published a Nov. 20, 2026 blog post discussing unforced Navier–Stokes singularity and the generalized Riemann Hypothesis. The supplied material contains no post text, so the specific claims, proof status, and any connection drawn between the two topics cannot be verified from the available source. The Hacker News thread centered on AI-assisted proof verification and Lean rather than on details of Tao&\#x27;s argument.

hackernews · archon1410 · Nov 20, 17:21 · [Discussion](https://news.ycombinator.com/item?id=50578358)

**「Background」** The Navier–Stokes existence and smoothness problem concerns whether the three-dimensional incompressible equations with smooth initial data always have smooth solutions, or whether solutions can break down in finite time. In the &quot;unforced&quot; version, the external force is set to zero, so any singularity would have to arise from the equations&\#x27; own nonlinear dynamics rather than from an applied force.

**「Verification gap to watch」** For anyone treating a Lean-checked proof as settled, the practical question is whether the formal statement faithfully encodes the intended theorem. A 2026 arXiv paper \(2610.08144\) documents cases where natural-language statements and proofs were mistranslated into Lean, yielding mismatches between the prose proof and its Lean &quot;verification,&quot; and names OpenAI&\#x27;s announced Navier–Stokes proof among the examples. Separating the released artifacts from independent acceptance is therefore the check to apply before citing a formalization as confirmation of the natural-language claim.

**「Community Discussion」** Commenters debated whether AI systems that generate and verify proofs can create new mathematical abstractions, with one asking how concepts like the Langlands program arise rather than being brute-forced. Another commenter said two independent Lean kernels accepted the result, which they saw as reducing the likelihood of a kernel-bug exploit, while others described excitement and anxiety about AI&\#x27;s effect on research careers.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_existence_and_smoothness">Navier – Stokes existence and smoothness - Wikipedia</a></li>
<li><a href="https://arxiv.org/abs/2610.08144">[2610.08144] Navier-Stokes lost in translation: Why Lean ...</a></li>
<li><a href="https://discoverai.tools/articles/openai-navier-stokes-ai-proof-millennium-problem-2026">OpenAI Navier–Stokes Proof Claim: Verification Status</a></li>

</ul>
</details>

**Tags**: `#mathematics`, `#AI-assisted proof`, `#Lean`, `#Navier-Stokes`, `#Riemann Hypothesis`

---

<a id="item-tech-news-4"></a>
### [Thinking Machines releases Inkling 2 Mini, an open-weights looped model for local use](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 7.0/10

Thinking Machines released Inkling 2 Mini, an open-weights model built on a looped transformer architecture that the team says was trained end-to-end in nvfp4 and sized around what local-inference users ask for. Commenters describe it as competitive with a 27B-class Qwen model, though that comparison rests on early, unverified community testing rather than independent benchmarks. Reported local throughput includes about 27 tokens/s decoding on a Ryzen 395 via llama.cpp&\#x27;s Vulkan backend and roughly 10 tokens/s on a 32GB M1 Pro at q4. Running it in llama.cpp currently requires several unmerged pull requests plus a small patch that one commenter says yields about a 30% speed boost.

hackernews · jasondavies · Nov 20, 20:12 · [Discussion](https://news.ycombinator.com/item?id=50581260)

**「Background」** Looped transformers reuse their middle layers for multiple passes, so the model performs more computation per token instead of generating more tokens; Inkling 2 Mini applies this design in an open-weights mixture-of-experts model with 26.4B total and 5.4B active parameters. Local inference guides point to Unsloth or llama.cpp builds with looped-layer support and per-expert NVFP4 scales.

**「Local deployment depends on unmerged tooling」** Early users report that running the model locally requires unmerged llama.cpp pull requests \(32694, 32657, 32429, 32704\) plus a small llama-graph.cpp patch that one commenter measured at roughly a 30% decoding speedup, so out-of-the-box throughput will hinge on tooling state rather than the weights alone. Reported rates ranged from about 27 tokens/s on a Ryzen 395 via llama.cpp Vulkan to about 10 tokens/s on a 32GB M1 Pro at q4.

**「Community discussion」** One commenter reported that quick coding tests worked well, with correct Python output that was a little chatty, while another argued that resource constraints are what push labs toward efficient designs like this. Others speculated that most open models will adopt looped architectures in response and raised open questions about safety and interpretability at this level of availability; these are opinions, not measured findings.

<details><summary>References</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://unsloth.ai/docs/models/inkling-2-mini">Inkling 2 Mini - Run Locally Guide | Unsloth Documentation</a></li>
<li><a href="https://ollama.com/library/inkling-2-mini">inkling - 2 - mini</a></li>

</ul>
</details>

**Tags**: `#LLM`, `#open-weights`, `#model-release`, `#looped-transformers`, `#local-inference`

---

<a id="item-tech-news-5"></a>
### [Paper Claims Language Models Can Rewrite Their Own Weights](https://arxiv.org/abs/2611.21885) ⭐️ 7.0/10

An arXiv paper claims a language model can rewrite its own weights through reasoning and improve without gradients or training, submitting only edits that pass practice problems. The source provides no paper text, and commenters say the demonstrated gain was mainly shorter reasoning traces to avoid token limits rather than general capability improvement. Discussion compares the work with prior weight-space programming and Google&\#x27;s “sleep” framework for offline weight updates.

hackernews · lwhsiao · Nov 20, 16:29 · [Discussion](https://news.ycombinator.com/item?id=50577265)

**「Background」** Conventionally, a language model is trained once and then frozen: making it better requires another training run, or inference-time aids such as a prompt, a harness, or extra computation that disappear once the task ends. The paper frames its &quot;self-rewriting&quot; claim against that baseline, arguing a model can edit its own weights through its own reasoning without gradients or a separate training run.

**「Impact」** Developers should not treat the result as evidence of general self-improvement: the benefit described in comments is mainly shorter reasoning traces under token limits, not broad capability gains. Safety teams reviewing self-editing loops have a concrete scenario to test—an autonomous model editing activations relevant to safety—though commenters raise this as a hypothetical risk, not a demonstrated outcome.

**「Community Discussion」** Commenters are skeptical of the headline: anesthesia says the only self-improvement was shortening reasoning traces to avoid token limits, Toutouxc questions whether the “no training” framing is meaningful, and gavinray points to Google&\#x27;s “sleep” framework as prior work. LarsDu88 warns that an autonomous model could suppress safety-relevant activations, a risk framed as hypothetical rather than shown in the paper.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2611.21885">[2611.21885] Language Models Can Rewrite Their Own Weights</a></li>

</ul>
</details>

**Tags**: `#large language models`, `#self-modifying models`, `#weight editing`, `#AI safety`, `#research paper`

---

<a id="item-tech-news-6"></a>
### [Levent Alpöge Claims Generalized Riemann Hypothesis Proof With Lean Formalization](https://alpo.ge/remark.pdf) ⭐️ 7.0/10

Levent Alpöge has posted a personal PDF claiming that he and Claude discovered a proof of the Generalized Riemann Hypothesis and formalized the argument in Lean without assumptions. The accompanying Lean artifact is reportedly about 1.3 GB and roughly 15 million lines, according to a commenter who downloaded it. The claim is extraordinary and, in the supplied material, remains unverified by peer review or independent exposition; the PDF itself is the primary account.

hackernews · iamronaldo · Nov 20, 14:16 · [Discussion](https://news.ycombinator.com/item?id=50574968)

**「What the claim extends」** The Riemann Hypothesis asserts that every non-trivial zero of the Riemann zeta function has real part 1/2, and the Generalized Riemann Hypothesis extends the same assertion to Dirichlet L-functions and related zeta functions. Earlier work involving Claude had raised a lower bound on the proportion of zeta zeros provably on the critical line to 67.2% while explicitly not proving the hypothesis, so the new note claims a qualitative jump rather than an incremental bound. Lean is an interactive proof assistant that mechanically checks each inference, which is why the reported scale of the accompanying formalization, rather than the prose note alone, is central to how the claim is being evaluated.

**「Impact」** The reported ~15-million-line Lean artifact makes independent audit resource-intensive, so anyone relying on the claim needs to verify that the formal statement actually encodes the Generalized Riemann Hypothesis and that the proof has no unstated dependencies, not merely that the project compiles.

**「Community Discussion」** Commenters are divided: some describe the result as a historical turning point and discuss pausing AI development, while others urge caution, linking a purported entirely human proof and citing a recent Terence Tao remark that AI systems had not come close to the Riemann Hypothesis. One commenter reported that checks by Andrew Sutherland were underway, but that is a community claim rather than confirmation in the supplied source.

<details><summary>References</summary>
<ul>
<li><a href="https://www.unite.ai/levent-alpoges-unverified-riemann-claim-puts-claudes-lean-code-in-focus/">Levent Alpöge’s Unverified Riemann Claim Puts Claude’s Lean ...</a></li>

</ul>
</details>

**Tags**: `#formal-verification`, `#lean-proof-assistant`, `#riemann-hypothesis`, `#ai-for-mathematics`, `#unverified-claim`

---

<a id="item-tech-news-7"></a>
### [Signal moves to block mobile AI agents from capturing chats](https://signal.org/blog/protecting-your-privacy/) ⭐️ 7.0/10

Signal published a blog post describing its efforts to keep AI agents built into mobile operating systems from capturing user data, with private chats as the focus. The supplied material does not specify which OS-level capabilities or platform versions are involved, nor whether any restriction has shipped in a released Signal build rather than being an announced or in-progress effort. Signal frames the work as progress against a problem it has been pursuing, but the technical details of the defenses are not available here.

hackernews · dotcoma · Nov 20, 09:42 · [Discussion](https://news.ycombinator.com/item?id=50572348)

**「Background」** The privacy issue is OS-level agentic AI that analyzes on-screen information, which can expose a messaging app&\#x27;s contents. Signal&\#x27;s November 20 post says it is restricting screenshot capability on Android and iOS to prevent those built-in agents from capturing or storing Signal data; The Verge describes the move as blocking Gemini and Siri agents from reading messages.

**「Effect on AI agent access」** Signal&\#x27;s screenshot restrictions on Android and iOS mean OS-level AI agents such as Google Gemini and Apple Siri can no longer read Signal chats unless the user explicitly grants permission, so assistant workflows that depended on screen capture will fail rather than silently collecting message content. Third-party tools that screenshot the app will need a user-consented alternative, and users should expect explicit prompts before any agent can access chats.

**「Community discussion」** Commenters debated whether app-level defenses can work at all: one cited a Meredith Whittaker interview arguing that a contact&\#x27;s AI app can expose your chats even if you never install one, another said users need to regain control of the operating system instead of relying on Signal blocking screenshots, and a third asked Signal to publish its forensics findings so smaller developers can benefit. A separate thread criticized Signal&\#x27;s spam protection, reporting that adding contacts over a VPN triggers repeated CAPTCHAs, while another commenter complained that screenshot blocking on Windows removes a basic feature.

<details><summary>References</summary>
<ul>
<li><a href="https://signal.org/blog/protecting-your-privacy/">Signal &gt;&gt; Blog &gt;&gt; Signal is Serious About Protecting Your Privacy</a></li>
<li><a href="https://www.theverge.com/ai-artificial-intelligence/1038390/signal-blocking-ai-agent-screenshots-mobile-app">Signal is blocking Gemini and Siri AI from reading your... | The Verge</a></li>
<li><a href="https://www.digitaltrends.com/phones/signal-adds-screenshot-protections-to-stop-ai-agents-reading-chats/">Signal is fighting back against AI agents snooping on your ...</a></li>
<li><a href="https://www.reuters.com/legal/litigation/signal-restricts-screenshots-block-ai-agents-reading-messages-2026-11-20/">EXCLUSIVE: Signal restricts screenshots to block AI agents ...</a></li>
<li><a href="https://www.theregister.com/security/2026/11/20/signal-slams-door-on-prying-ai-agents-to-protect-privacy/5311466">Signal slams door on prying AI agents to protect privacy</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#AI agents`, `#mobile security`, `#Signal`, `#messaging`

---

<a id="item-tech-news-8"></a>
### [Draft proof of Generalized Riemann Hypothesis released for review](https://simonwillison.net/2026/Nov/20/ravi-vakil/) ⭐️ 7.0/10

Mathematicians now have a public draft of a proposed proof of the Generalized Riemann Hypothesis by Alessandro Masullo, announced by Ravi Vakil. Vakil says Brian Conrad has reviewed it closely for months, gave extensive feedback that is being incorporated, and that it is “so far looking good.” The work is described as entirely human-produced with no AI; the earlier plan was to polish it during a hoped-for year at Stanford and announce it after wider review. The brief announcement includes no technical substantiation or independent verification, so the proof remains unverified.

rss · Simon Willison · Nov 20, 19:21

**「Why the claim drew immediate attention」** The Generalized Riemann Hypothesis extends the Riemann Hypothesis beyond the zeta function to a broader class of L-functions, so a valid proof would settle many results in number theory that are currently only conditional. Vakil&\#x27;s announcement put out an unfinished draft instead of waiting for a polishing year at Stanford, and Brian Conrad — described in the New York Times as Masullo&\#x27;s doctoral thesis adviser — found the approach credible without major gaps; the same day also brought a separate, AI-assisted claim from Dr. Alpoge and Claude, and neither proof has been accepted.

**「Impact」** For mathematicians, the practical consequence is that the draft is now available for public scrutiny before formal peer review; it should be treated as a proposed, unverified proof rather than an established result. Those assessing it will need to account for Conrad&\#x27;s feedback still being incorporated, according to Vakil.

<details><summary>References</summary>
<ul>
<li><a href="https://www.scientificamerican.com/article/dueling-claims-of-riemann-hypothesis-proofs-emerge/">Dueling claims of Riemann hypothesis proofs ... | Scientific American</a></li>
<li><a href="https://www.nytimes.com/2026/11/20/science/anthropic-ai-math-riemann-hypothesis.html">Anthropic Mathematician Claims to Solve Riemann Hypothesis With...</a></li>

</ul>
</details>

**Tags**: `#mathematics`, `#Generalized Riemann Hypothesis`, `#research announcement`, `#proof verification`

---

<a id="item-tech-news-9"></a>
### [TikTok rolls out global deepfake detection and AI-content checker](https://www.straitstimes.com/world/tiktok-launches-tool-to-help-public-figures-detect-deepfakes-globally) ⭐️ 7.0/10

TikTok began a global rollout on Nov. 20 of its Likeness Detection tool, which lets public figures and top creators whose identities have been verified by a third party receive alerts when others use their likeness in unauthorized AI-generated content and report it. A second tool, also launched the same day, lets anyone upload an image or video to check whether it was generated by TikTok&\#x27;s own AI features, with no account required. TikTok said the measures would help protect elections in multiple European countries in 2027. The EU has required labeling of AI-generated content since August.

telegram · zaihuapd · Nov 20, 08:14

**「Regulatory backdrop」** The EU AI Act&\#x27;s Article 50 sets transparency obligations for providers and deployers of certain AI systems, covering disclosure when AI interacts with people and labeling or marking when AI generates content, including deepfakes. The source reports that the EU&\#x27;s requirement to label AI content has applied since August 2026, and TikTok presents its new tools partly as preparation for the 2027 elections in several European countries.

**「Uneven coverage by design」** The practical effect is uneven coverage: only verified public figures and high-follower creators can receive Likeness Detection alerts, and the feature is opt-in, while everyone else has just the public checker, which identifies content made with TikTok&\#x27;s own AI tools rather than deepfakes produced elsewhere.

<details><summary>References</summary>
<ul>
<li><a href="https://prunepad.eu/blog/ai-act-article-50/">AI Act Article 50 in Plain Language | PrunePad Blog</a></li>
<li><a href="https://www.legalithm.com/en/blog/ai-act-transparency-obligations-article-50-deepfake-labeling">AI Act Transparency : Article 50 and Deepfake Rules</a></li>
<li><a href="https://www.straitstimes.com/world/tiktok-launches-tool-to-help-public-figures-detect-deepfakes-globally">TikTok launches deepfake detection tool for public figures ...</a></li>
<li><a href="https://www.euronews.com/2026/11/20/tiktok-rolls-out-deepfake-detection-tool-for-public-figures-to-fight-back-against-disinfor">TikTok rolls out deepfake detection tool for public figures</a></li>

</ul>
</details>

**Tags**: `#deepfake detection`, `#AI content provenance`, `#platform policy`, `#TikTok`, `#EU AI regulation`

---

<a id="item-tech-news-10"></a>
### [OpenAI adds background mode for long API requests with token discounts](https://developers.openai.com/api/docs/guides/background) ⭐️ 7.0/10

OpenAI&\#x27;s background mode moves long-running API requests to asynchronous execution: a request sets \`background: true\` and picks a completion window of 2 or 8 hours via \`background\_options.completion\_window\`, with token rates 30% and 40% below standard pricing respectively. Leaving the window unset defaults to \`soonest\`, which carries no discount. The discounted pricing is in public beta on GPT-6.2 Astra, GPT-6.2 Sol, GPT-6.1 Terra and GPT-6 Luna. The same documentation states that background mode temporarily stores response data even when \`store\` is set to false or zero data retention is enabled. These details come from a Telegram post relaying OpenAI&\#x27;s developer documentation and were not independently verified.

telegram · zaihuapd · Nov 20, 11:15

**「Context」** OpenAI’s background mode is an option on the Responses API for long-running jobs, and OpenAI’s documentation allows streaming only with the default \`soonest\` completion window; for 2h and 8h requests, developers must omit \`stream\` or set it to \`false\` \(tool-2-1, tool-2-3\). In the documented setup, the discounted windows therefore cannot be combined with streamed, token-by-token output.

**「Developer takeaway」** Developers can cut token costs on batch-style or long agentic jobs by accepting multi-hour latency, so workloads should be split between latency-sensitive calls on the standard path and deferrable ones in background mode. Teams in regulated or zero-data-retention environments need to account for the temporary response storage, since the \`store: false\` setting and ZDR do not opt a background request out of it.

<details><summary>References</summary>
<ul>
<li><a href="https://developers.openai.com/api/docs/guides/background">Background mode | OpenAI API</a></li>
<li><a href="https://www.aifeaturedrop.com/2026/11/openai-background-mode-guide-2-hour-and.html">OpenAI Background Mode Guide: 2-Hour and 8-Hour Completion ...</a></li>

</ul>
</details>

**Tags**: `#OpenAI API`, `#async processing`, `#API pricing`, `#data retention`, `#long-running tasks`

---

<a id="item-tech-news-11"></a>
### [TSMC Said to Pause 16nm-and-Below Orders From Chinese Firms](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 7.0/10

TSMC has reportedly notified customers that it is pausing advanced-node orders — 16nm and below — from Chinese companies, which under tightened US semiconductor export rules cannot be served without a prior US export license or exemption. Chinese firms are left with older processes such as 28nm and 40nm and, per the report, are cut off from the high-bandwidth memory that AI data-center hardware requires. The change in procedure is that TSMC previously assessed on its own whether a customer&\#x27;s design qualified for an exemption, whereas customers must now apply in advance; the US approved list includes Apple, AMD and Nvidia, with no Chinese companies yet, and TSMC said it will comply with the new rules. The account is a brief curated summary without primary-source documents or independent verification, so the scope and effective date of the pause remain unconfirmed.

telegram · zaihuapd · Nov 21, 02:01

**「What changed in the exemption process」** The item says TSMC previously assessed on its own whether a customer’s chip design met U.S. export-rule exemption criteria. Under the tightened rules, Chinese customers must instead apply in advance for a U.S. license or exemption, and the approved list cited in the report includes Apple, AMD and Nvidia but no Chinese company. The 16nm threshold separates the restricted advanced processes from older 28nm and 40nm production that the report says Chinese firms can still use.

**「Impact」** Chinese chip designers now need a U.S. license or exemption before TSMC will accept 16nm-and-below orders, so teams without one must retarget designs to 28nm or 40nm processes or lose access to the advanced nodes and high-bandwidth memory used in AI data-center hardware. Reuters reports the suspension also covers some previously permitted advanced manufacturing orders, and TrendForce reports the pause may extend to some consumer-chip shipments.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/world/china/tsmc-tightens-china-ai-chip-curbs-new-us-rules-close-manufacturing-loophole-2026-11-19/">TSMC tightens China AI chip curbs as new US rules close ...</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/20/news-tsmc-samsung-reportedly-pause-china-consumer-chip-shipments-under-new-u-s-rules-16nm-orders-affected/">[News] TSMC, Samsung Reportedly Pause China Consumer Chip ...</a></li>

</ul>
</details>

**Tags**: `#TSMC`, `#semiconductor supply chain`, `#US export controls`, `#China tech`, `#AI chips`

---