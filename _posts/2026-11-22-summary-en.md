---
layout: default
title: "Horizon Summary: 2026-11-22 (EN)"
date: 2026-11-22
lang: en
---

> From 22 items, 8 important content pieces were selected

---

**Technology News**
1. [Lean formalization of Riemann Hypothesis reported verified](#item-tech-news-1) ⭐️ 9.0/10
2. [Zhejiang University reports first real-device QRAM on Tianmu 2 chip](#item-tech-news-2) ⭐️ 8.0/10
3. [Debugging a 75% Download-Speed Drop Through a Monitor Hub](#item-tech-news-3) ⭐️ 7.0/10
4. [GPGME flaw reported as RCE is a double-free, affecting pre-2.3.0 users](#item-tech-news-4) ⭐️ 7.0/10
5. [Muru: Graham Dumpleton&\#x27;s AI-assisted Rust server for ASGI/WSGI Python apps](#item-tech-news-5) ⭐️ 7.0/10
6. [Microsoft previews RDMA over USB4 for multi-PC local AI inference](#item-tech-news-6) ⭐️ 7.0/10
7. [OpenRouter warns MiniMax prompts may have been read by third parties](#item-tech-news-7) ⭐️ 7.0/10
8. [Tesla starts FSD v15 rollout with Reality View, 25x safety claim](#item-tech-news-8) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Lean formalization of Riemann Hypothesis reported verified](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) ⭐️ 9.0/10

On 20 November 2026, Levent Alpöge announced a Lean formalization of the Riemann Hypothesis in a codebase of about 17 million lines. Lean FRO and the Mathlib Initiative said the next day that the statement and proof are correct: the statement matches Mathlib&\#x27;s \`RiemannHypothesis\`, the code compiles without errors, and multiple separate proof checkers accepted it, according to the supplied account. The effort is described as AI-assisted, with commenters crediting Claude for much of the formal work and Alpöge for directing it; the available material does not include an independent mathematical review beyond those checker and community claims.

hackernews · g-b-r · Nov 21, 14:36 · [Discussion](https://news.ycombinator.com/item?id=50589618)

**「Background」** Lean is a proof assistant whose proofs are checked mechanically, and Mathlib is its community-maintained library of formalized mathematics. The Riemann Hypothesis already had a formal statement in Mathlib, \`RiemannHypothesis\`, which Lean and number-theory experts had vetted before this release claimed to prove it.

**「Reproducibility check」** Re-checking the result depends on reproducing the exported proof artifact \(solution.ndjson\) and comparing its hash across builds using con-leche and con-ron as bundled with Lean v4.36.0. The supplied verification page states that it has not examined whether the export format can carry a source path, so build provenance may need separate evidence even when the independent kernels accept the proof.

**「Community discussion」** Commenters focused on trust in the checking pipeline: one argued that with several separately implemented kernels and self-consistency proofs, a bug invalidating both those checks and the Riemann proof is vanishingly unlikely, while another countered that a fake Collatz refutation had already passed one such checker and that the checkers are less independent than often claimed. Others credited Levent Alpöge with steering the AI-assisted effort and described the formalization as covering a large amount of modern mathematics, while noting that human expert involvement reduces—but does not eliminate—the risk of a model exploiting the checking process.

<details><summary>References</summary>
<ul>
<li><a href="https://leanprover-community.github.io/blog/posts/riemann-hypothesis/">Lean verification of the Riemann Hypothesis | Lean community blog</a></li>
<li><a href="https://news.ycombinator.com/item?id=50589618">Lean verification of the Riemann Hypothesis | Hacker News</a></li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof : verification files</a></li>

</ul>
</details>

**Tags**: `#Lean theorem prover`, `#Riemann Hypothesis`, `#formal verification`, `#AI-assisted mathematics`, `#proof assistants`

---

<a id="item-tech-news-2"></a>
### [Zhejiang University reports first real-device QRAM on Tianmu 2 chip](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 8.0/10

Zhejiang University researchers report the first real-device demonstration of quantum random access memory \(QRAM\), running a prototype on their superconducting chip Tianmu 2 and reporting the work in Nature Physics. The prototype retrieved 4-bit and 8-bit data with 80.9% and 60.4% accuracy, respectively, while using more than 30% less circuit depth than an unoptimized version and showing local noise resilience. The team says its next step is scaling QRAM; the reported fidelities, especially at 8 bits, remain well below what practical data loading would require.

telegram · zaihuapd · Nov 21, 08:31

**「What QRAM is and the chip behind it」** QRAM is a proposed quantum memory that would let an algorithm fetch classical data in superposition, with addresses set by qubits rather than bits — a capability assumed by many quantum algorithms but hard to build because it requires coherent routing of address information. The device used here, Tianmu-2, is a 100-qubit superconducting chip jointly developed by Zhejiang University&\#x27;s superconducting quantum computing team and Hangzhou Logic Bit Technology Co., Ltd.

**「Impact」** For quantum-algorithm developers, this is an early hardware benchmark rather than usable memory: retrieval accuracy drops from 80.9% at 4 bits to 60.4% at 8 bits, so wider QRAM will need materially better fidelity before it can serve as a reliable data-loading primitive.

<details><summary>References</summary>
<ul>
<li><a href="https://baike.baidu.com/en/item/Tianmu-2/4929794">Tianmu-2_Baiduwiki - 百度百科</a></li>

</ul>
</details>

**Tags**: `#quantum computing`, `#QRAM`, `#superconducting qubits`, `#quantum hardware`, `#research`

---

<a id="item-tech-news-3"></a>
### [Debugging a 75% Download-Speed Drop Through a Monitor Hub](https://blog.tymscar.com/posts/studiodisplayethernet/) ⭐️ 7.0/10

A detailed debugging write-up reports that routing Ethernet through a monitor&\#x27;s USB hub cut download speeds by 75%. According to the post, the hub path added latency, so the laptop could not acknowledge packets quickly enough; the Ethernet adapter&\#x27;s buffer filled and packets were dropped. Switching to an adapter that required less frequent acknowledgment fixed the problem.

hackernews · soheilpro · Nov 21, 10:36 · [Discussion](https://news.ycombinator.com/item?id=50587875)

**「Background」** The post is a case study in TCP behavior rather than display hardware: when packets are dropped, TCP backs off and throughput collapses even if the raw link speed is high. USB hubs and docks sit between the laptop and the Ethernet adapter, adding latency and buffering that can make timely acknowledgments harder. The monitor is incidental; the relevant chain is the USB Ethernet adapter and the hub path feeding it.

**「Impact」** For anyone diagnosing slow wired downloads, the practical test is to bypass the monitor or dock and compare the same adapter connected directly; the reported fix came from changing the adapter path, not from adjusting the broadband connection.

**「Community Discussion」** Commenters pushed back on the framing, with one arguing that the monitor is incidental and the real culprit is the USB network switch, while another stressed that the monitor path&\#x27;s added latency caused late acknowledgments, a full adapter buffer, and drops. A reader reported a similar year-long MacBook-and-Thunderbolt-dock problem and said enabling flow control made it good enough, while another shared an unrelated Ghostty/io\_uring I/O-pressure anecdote.

<details><summary>References</summary>
<ul>
<li><a href="https://news.ycombinator.com/item?id=50587875">My monitor was cutting my download speed by 75 % | Hacker News</a></li>

</ul>
</details>

**Tags**: `#usb`, `#networking`, `#hardware-debugging`, `#ethernet`, `#latency`

---

<a id="item-tech-news-4"></a>
### [GPGME flaw reported as RCE is a double-free, affecting pre-2.3.0 users](https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html) ⭐️ 7.0/10

A reported GPGME vulnerability disclosed on 2026-11-20 affects software using GPGME versions before 2.3.0, whether linked as a shared library, DLL, or statically, according to a commenter&\#x27;s summary of the advisory. The gnupg-announce post is titled “RCE in Gnupg,” but commenters say the defect is a double-free rather than a demonstrated remote-code-execution chain. The disclosure was moved up from a planned 2026-11-25 coordinated date because GitLab had to ship an update earlier during the Ruby2Shell bug, according to a commenter involved in the report. Another commenter said Red Hat&\#x27;s packaging had carried a fix for five years while upstream missed it.

hackernews · gdgghhhhh · Nov 21, 08:32 · [Discussion](https://news.ycombinator.com/item?id=50587208)

**「Background」** GPGME \(GnuPG Made Easy\) is the library that applications use to integrate GnuPG encryption and digital-signature functions. The advisory covers all software using GPGME before version 2.3.0, whether the library is loaded as a shared library, a Windows DLL, or statically linked. Johan Carlsson discovered the flaw, and GitLab informed the maintainers on 2026-11-12.

**「Who must rebuild」** Maintainers shipping GPGME inside their own products — mail and XMPP clients, Samba, and GitLab&\#x27;s signed-commit path — must rebuild against the patched release rather than assume a system-level update covers them, since statically linked, DLL, and vendored copies carry the flaw independently. The GnuPG advisory says the double free can be triggered by crafted signed data to exfiltrate information from the application and that an RCE &quot;can&\#x27;t be ruled out&quot;; corgea&\#x27;s analysis notes GitLab Omnibus master was still building GPGME 2.2.0 and relying on validation, which is exactly the gap a rebuild closes.

**「Community discussion」** Commenters challenged the RCE framing: mik1998 called it a double-free bug, not an RCE chain, and asked whether vulnerability reports are being intentionally overstated. wannabe44 listed affected integrations such as Gpg4win, most mail clients, many XMPP clients, Samba, and Flatpak, and asked for confirmation that apt is unaffected; another commenter said Red Hat had fixed the issue in its packaging five years earlier but upstream missed it.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via...</a></li>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME ...</a></li>
<li><a href="https://techora.ru/news/v-gpgme-kriticheskaya-uyazvimost-utechka-dannykh-2026-11-21">В GPGME критическая уязвимость: утечка данных и RCE для...</a></li>
<li><a href="https://lists.gnu.org/archive/html/info-gnu/2026-11/msg00006.html">GnuPG Security Advisory for GPGME (T8557,CVE-2026-129975)</a></li>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via ...</a></li>
<li><a href="https://corgea.com/research/cve-2026-129975-gpgme-double-free-long-openpgp-user-id-november-2026">GPGME double free via long OpenPGP user IDs (CVE-2026-129975)</a></li>

</ul>
</details>

**Tags**: `#GPGME`, `#GnuPG`, `#security vulnerability`, `#double-free`, `#open source`

---

<a id="item-tech-news-5"></a>
### [Muru: Graham Dumpleton&\#x27;s AI-assisted Rust server for ASGI/WSGI Python apps](https://simonwillison.net/2026/Nov/21/muru/) ⭐️ 7.0/10

Graham Dumpleton, who began mod\_wsgi 20 years ago, has introduced Muru, a new AI-assisted Rust server intended to run both ASGI and WSGI Python applications in development and production. From Nov. 4 to Nov. 21, 2026, he published 18 posts, most documenting the design, including import-once/fork-many workers, HTTPS in development, releases without restarts, canary deployments without a service mesh, container and Kubernetes behavior, scaling to zero, and a tracing toolbar. The supplied account describes a project and its design rationale, not a shipped release with versions, benchmarks, or independent production results. Dumpleton says AI does much of the surface work but he decides what is good enough, drawing on his mod\_wsgi experience.

rss · Simon Willison · Nov 21, 23:56

**「Background」** WSGI and ASGI are standard interfaces between Python web applications and a server. Graham Dumpleton started the mod\_wsgi project 20 years ago and has focused since then on how Python apps are served in production; Muru is his new Rust-based server for both interfaces, rather than an update to mod\_wsgi.

**「Impact」** For Python teams, Muru explicitly targets both WSGI and ASGI and spans development through production, making it a candidate alongside established servers. Because the supplied account provides no versioned compatibility guarantees or benchmarks, teams would need to test their own applications before relying on it.

**Tags**: `#Python`, `#ASGI/WSGI`, `#Rust`, `#web servers`, `#open source`

---

<a id="item-tech-news-6"></a>
### [Microsoft previews RDMA over USB4 for multi-PC local AI inference](https://videocardz.com/newz/microsoft-brings-rdma-over-usb4-to-windows-allowing-multiple-pcs-to-run-one-local-ai-model) ⭐️ 7.0/10

Microsoft released a Windows developer preview of RDMA over USB4 that lets multiple PCs share memory and GPU resources to run a single local AI model without dedicated networking hardware. In a demo, three AMD Ryzen AI Max+ 395 systems ran a 4-bit Qwen3-235B-A22B model at about 18.5 tokens per second. The preview is slated to reach users through Windows Insider. The source provides limited technical detail beyond the demo and the USB4-based pooling capability.

telegram · zaihuapd · Nov 21, 06:13

**「Background」** RDMA over USB4 adapts remote direct memory access, a technique for letting one machine access another machine&\#x27;s memory with low CPU overhead, to ordinary USB4 links rather than dedicated datacenter networking. Microsoft&\#x27;s developer preview targets local AI models too large for a single PC by pooling connected Windows PCs&\#x27; memory capacity and GPU resources.

**「Impact」** Developers with multiple USB4-equipped Windows PCs can test pooling memory and GPU compute for one local model without a dedicated network card or switch, though the developer-preview status and the roughly 18.5 token/s demo point to an early-stage capability.

<details><summary>References</summary>
<ul>
<li>Introducing RDMA over USB4® on Windows: run larger local AI models across PCs</li>

</ul>
</details>

**Tags**: `#RDMA`, `#USB4`, `#local AI inference`, `#Windows`, `#distributed computing`

---

<a id="item-tech-news-7"></a>
### [OpenRouter warns MiniMax prompts may have been read by third parties](https://news.ycombinator.com/item?id=50585962) ⭐️ 7.0/10

OpenRouter has reportedly warned users that prompts sent to MiniMax models may have been read by third parties, according to an email notification described in the source. Security researchers who sent prompts containing test URLs to MiniMax models between July and October 2026 found that third parties accessed those URLs 40 to 130 hours later. OpenRouter attributed the issue to MiniMax and its forwarders AtlasCloud, Novita, and StreamLake, removed the &quot;zero data retention&quot; labels from the affected endpoints, and advised users who may have exposed sensitive credentials to rotate API keys and passwords. The report is secondhand, and OpenRouter&\#x27;s website had not published information about the incident at the time of the source.

telegram · zaihuapd · Nov 21, 06:53

**「Background」** Zero data retention \(ZDR\) is a label indicating that the upstream host does not retain prompts; on OpenRouter, the label is passed through from the host rather than serving as an independent guarantee. Coverage of the warning focused on MiniMax requests routed through AtlasCloud, Novita, and StreamLake, noting that Novita had been listed as US-based with ZDR yet still forwarded data to MiniMax in China, so prompts and outputs sent through those intermediaries may have been exposed.

**「Exposure risk for API users」** Developers routing requests through OpenRouter lose the zero-data-retention assurance on MiniMax endpoints, including traffic forwarded via AtlasCloud, Novita, and StreamLake. Because OpenRouter says prompts may have been read, past prompts containing secrets should be treated as potentially exposed, and affected users should follow its advice to rotate API keys and passwords.

<details><summary>References</summary>
<ul>
<li>AGTP on X: &quot;OpenRouter just warned users that MiniMax prompts may have been read ...</li>
<li>OpenRouter Warns Prompts Sent to MiniMax Models May Have Been Read - Privacy Affairs</li>
<li>OpenRouter warns MiniMax prompts may have been read after test URLs were accessed days later - Reddit</li>
<li><a href="https://www.hallattorneys.com/investigations/openrouter-minimax">OpenRouter MiniMax Prompt Exposure Investigation - Hall Attorneys</a></li>
<li><a href="https://www.siliconreport.com/openrouter-drops-minimax-retention-label-over-leak-research">OpenRouter drops MiniMax retention label over leak research</a></li>

</ul>
</details>

**Tags**: `#AI security`, `#data privacy`, `#API providers`, `#OpenRouter`, `#MiniMax`

---

<a id="item-tech-news-8"></a>
### [Tesla starts FSD v15 rollout with Reality View, 25x safety claim](https://x.com/Tesla/status/2124222447855743019) ⭐️ 7.0/10

Tesla has begun an overseas rollout of FSD v15 with a new &quot;Tesla Reality View&quot; interface that overlays camera imagery and the system&\#x27;s driving plan on the in-car screen. The update supports full-screen, map, and split-screen views plus a quiet mode; navigation turn prompts can appear as overlays, and the turn-signal chime is softer and fades gradually. Tesla claims a 25x improvement in handling safety-critical scenarios and says v15 improves driving over potholes and debris and speed control around schools and in bad weather; the short post does not substantiate the safety figure. The post did not specify which countries are covered, which vehicle hardware is supported, or when the rollout will expand.

telegram · zaihuapd · Nov 22, 00:03

**「What v15 was expected to contain」** Tesla&\#x27;s Full Self-Driving is an end-to-end neural-network driver-assistance feature that still requires an attentive driver. Before this rollout, Not a Tesla App reported that v15 was slated to ship alongside Tesla&\#x27;s holiday software update and would include a 10x increase in model parameters — framing the release as a broad rework of the driving network rather than an incremental point update.

**「Impact」** Drivers receiving v15 will get an additional display layer showing camera imagery and the planned path in full-screen, map, or split-screen layouts; because Tesla disclosed no hardware compatibility details, owners cannot tell from the post whether their cars qualify.

<details><summary>References</summary>
<ul>
<li><a href="https://www.notateslaapp.com/news/5057/tesla-fsd-v15-coming-next-month-with-holiday-update-musk">Tesla FSD V 15 Arriving Next Month: Home Garage... - Not a Tesla App</a></li>

</ul>
</details>

**Tags**: `#autonomous driving`, `#Tesla FSD`, `#AI safety`, `#computer vision`, `#software update`

---