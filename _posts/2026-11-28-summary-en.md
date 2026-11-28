---
layout: default
title: "Horizon Summary: 2026-11-28 (EN)"
date: 2026-11-28
lang: en
---

> From 29 items, 8 important content pieces were selected

---

**Technology News**
1. [OpenSec discloses 9.8-severity unauthenticated root flaw in Linux NFS server](#item-tech-news-1) ⭐️ 8.0/10
2. [Google Research claims DeepCrossAttention gives up to 3x speedup](#item-tech-news-2) ⭐️ 7.0/10
3. [Skimming scripts reportedly use WebRTC to hide on shopping sites](#item-tech-news-3) ⭐️ 7.0/10
4. [Convex AI skill&\#x27;s prompt upload draws privacy complaint](#item-tech-news-4) ⭐️ 7.0/10
5. [State attorneys general sue SpaceX over Grok&\#x27;s alleged harmful image generation](#item-tech-news-5) ⭐️ 7.0/10
6. [Essay examines false computer-checked proofs from checker soundness bugs](#item-tech-news-6) ⭐️ 7.0/10
7. [SemiAnalysis Benchmarks Trainium3 Inference Costs Against Nvidia GB300](#item-tech-news-7) ⭐️ 7.0/10
8. [Minecraft Bedrock resource-pack flaw patched in 26.65](#item-tech-news-8) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenSec discloses 9.8-severity unauthenticated root flaw in Linux NFS server](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

OpenSec has disclosed CVE-2026-99362, a CVSS 9.8 heap overflow in the Linux kernel NFS server \(nfsd\) that can be triggered without authentication by a connection to tcp/2049, potentially giving an attacker a root shell. The flaw is reported to have existed since Linux 3.16 \(2014\) and to affect hosts enabling NFSv4.1 or 4.2, including file servers, NAS devices and cluster storage nodes. Fixes are listed in kernel 6.12.117, 6.18.61, 7.3.2 and 7.4-rc1, and require an upgrade plus reboot; where upgrading is not immediately possible, the source recommends firewalling tcp/2049. The CVE was made public on November 20, 2026, according to the item, which provides an aggregator summary rather than the primary advisory or independent verification.

telegram · zaihuapd · Nov 27, 12:57

**「Background」** NFSv4.1 and 4.2 are session-based protocols: the server maintains a per-session reply cache \(a slot table\) so that a client can retransmit a request and receive the stored reply instead of having it executed again. Per Red Hat&\#x27;s CVE entry and independent write-ups, the flaw lets a remote client negotiate a minimal cached reply size and then send crafted compound requests containing SEQUENCE operations, making the server copy a full reply into an undersized heap buffer — a path reachable before any authentication on any host where tcp/2049 is exposed.

**「Patching and mitigation consequences」** Administrators of hosts with NFSv4.1 or 4.2 enabled must move to a fixed kernel \(6.12.117, 6.18.61, 7.3.2 or 7.4-rc1\) and reboot, since the flaw sits in nfsd itself and cannot be corrected by restarting the NFS service alone. Where an immediate upgrade is impossible, blocking tcp/2049 at the firewall is the recommended interim mitigation, which also means restricting NFS exports to trusted network segments rather than relying on client-side authentication. Distribution and appliance kernels may lag the upstream fix: discussion of the flaw notes that TrueNAS 25.10.8 ships a kernel predating the patch and that Ubuntu builds remained vulnerable, so version-string checks against the upstream list are not sufficient — vendor advisories should be confirmed individually.

<details><summary>References</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99362">CVE-2026-99362 - Red Hat Customer Portal</a></li>
<li><a href="https://computingforgeeks.com/nfs2root-cve-2026-99362/">NFS2ROOT (CVE-2026-99362): Check, Patch, Mitigate ...</a></li>
<li><a href="https://rokkhe.hashnode.dev/nfs2root-cve-2026-99362-linux-nfsd">NFS2ROOT (CVE-2026-99362): what it is, who is exposed, and ...</a></li>
<li>pre-auth remote root in the Linux NFS server. Ubuntu still vulnerable ...</li>
<li>NFS2ROOT (CVE-2026-99362) on CentOS 7: Fixed Kernel</li>

</ul>
</details>

**Tags**: `#linux-kernel`, `#security-vulnerability`, `#nfs`, `#patching`, `#remote-exploit`

---

<a id="item-tech-news-2"></a>
### [Google Research claims DeepCrossAttention gives up to 3x speedup](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research published a blog post describing DeepCrossAttention, a transformer residual-connection technique it claims can deliver comparable model quality while running up to 3x faster. The claim is aimed at teams working on transformer architecture, training, and inference efficiency. The supplied material is the blog post&\#x27;s own claim, not an independently reproduced benchmark or a peer-reviewed result.

hackernews · ComputedCamp995 · Nov 27, 23:06 · [Discussion](https://news.ycombinator.com/item?id=50672565)

**「How DCA changes residual connections」** Transformers normally use sequential residual connections that add each layer’s output to a running representation; DeepCrossAttention’s paper argues that this simple summation can dilute crucial information as depth increases. DCA instead introduces input-dependent, depth-wise cross-attention over the query, key, and value components, using learnable weights to route information across earlier layers.

**「Impact」** If the result reproduces, transformer developers could cut training or inference time per run without accepting lower model quality, but they would need to validate the residual-connection change against their existing architectures and workloads.

**「Community Discussion」** Commenters compared the idea to DenseNet and criticized the post&\#x27;s line graphs for implying a temporal relationship between methods; another asked whether the speedup could compound with existing inference optimizations such as MTP and Dflash. No supplied comment reported an independent reproduction of the 3x claim.

<details><summary>References</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections</a></li>
<li><a href="https://arxiv.org/html/2502.06785">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>
<li><a href="https://www.alphaxiv.org/overview/2502.06785v1">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>

</ul>
</details>

**Tags**: `#transformers`, `#model architecture`, `#training efficiency`, `#Google Research`, `#ML systems`

---

<a id="item-tech-news-3"></a>
### [Skimming scripts reportedly use WebRTC to hide on shopping sites](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

Credit card skimming scripts that use WebRTC were reportedly found on popular shopping sites, according to a report published on Black Friday. The finding points to an evasion technique built on a browser API, and it highlights the exposure created by third-party scripts embedded in e-commerce pages. The supplied material does not identify which sites were affected, how many, or who found the scripts, so the campaign&\#x27;s scope and the report&\#x27;s underlying evidence remain unverified.

hackernews · scanr · Nov 27, 15:40 · [Discussion](https://news.ycombinator.com/item?id=50668145)

**「Background」** WebRTC is a browser API for real-time communication, including direct peer-to-peer data channels. Card-skimming attacks typically inject malicious JavaScript into checkout pages, often through third-party scripts that a retailer embeds.

**「Exposure risk and audit priorities」** Customers who entered card details on the named stores—Lascana, Samsonite, American Tourister, Revolve and FWRD—during the reported pre-Black Friday window should treat their card data as potentially exposed and review statements for unauthorized charges. The affected merchants also need to audit third-party checkout scripts and remove unauthorized code, because a skimmer embedded in a shopping page can capture payment data directly from the browser.

**「Community discussion」** Commenters pushed back on treating WebRTC as the core problem: one argued the attack has little to do with WebRTC&\#x27;s capabilities and works because the protocol is less frequently monitored, adding that the same approach could use plain HTTP requests and that any site embedding third-party scripts remains vulnerable. Others framed it as a reason to block ads and questioned why ad networks do not sandbox ad JavaScript or prevent client-side execution entirely.

<details><summary>References</summary>
<ul>
<li>Credit card skimming scripts using WebRTC found on ... - InfoHawk</li>

</ul>
</details>

**Tags**: `#web security`, `#credit card skimming`, `#WebRTC`, `#third-party scripts`, `#e-commerce security`

---

<a id="item-tech-news-4"></a>
### [Convex AI skill&\#x27;s prompt upload draws privacy complaint](https://github.com/convex/convex-backend-skill/issues/64) ⭐️ 7.0/10

A GitHub issue on convex/convex-backend-skill \(\#64\) reports that a Convex AI skill sends users&\#x27; app ideas to a remote server without clearly disclosing it. In the thread, Convex CEO Jamie says the plugin&\#x27;s prompt upload powers Convex&\#x27;s quickstart feature and notes that Convex recently shut down Convex Chef, an end-to-end vibe-coding product. The vendor response states that prompt upload exists, but the available material does not resolve exactly what is sent, how consent is obtained, where it goes, or how long it is retained.

hackernews · MickyTheMouse · Nov 27, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50669765)

**「What the quickstart skill does」** Convex ships AI &quot;skills&quot; as SKILL.md instruction files that coding agents load; per the issue, \`/quickstart/SKILL.md\` \(lines 48–56\) POSTs the user&\#x27;s one-sentence project idea to \`basic-anteater-667.convex.site\`, labeled telemetry only in a code comment, while \`/add/SKILL.md\` pipes a script from the same host directly into bash. Convex CEO Jamie said in the thread that the prompt upload powers the &quot;quickstart&quot; feature, which he described as the successor to Convex Chef, an end-to-end vibe-coding product the company recently shut down.

**「Impact」** Developers using the Convex skill should treat app ideas and prompts as potentially leaving their local environment and should seek explicit disclosure or terms before entering confidential product plans. The dispute concerns informed consent and data handling for one AI coding tool, not a measured finding about Convex&\#x27;s broader platform.

**「Community discussion」** Commenters framed the report as a broader trust problem for AI coding tools: one argued that self-hosted open-weight models are the long-term answer, while another noted that prompt injection is more common than models making malicious tool calls, without claiming malice in this case.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/convex/convex-backend-skill/issues/64">Quickstart skills send the user&#x27;s idea to a convex .site host and run...</a></li>

</ul>
</details>

**Tags**: `#AI coding tools`, `#privacy`, `#data handling`, `#developer trust`, `#Convex`

---

<a id="item-tech-news-5"></a>
### [State attorneys general sue SpaceX over Grok&\#x27;s alleged harmful image generation](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

Attorneys General Jones and Rayfield filed a lawsuit against SpaceX in its role as parent company of xAI and X, alleging that Grok created and promoted child sexual exploitation material and non-consensual images on the platform, according to the release published by the Virginia Attorney General&\#x27;s office. The suit asks the court to stop Grok from generating such imagery. These are allegations in a complaint, not adjudicated findings, and no court has ruled on them. Because the filing text and any company response were not available, the specific legal theories, the full list of participating states, and the precise relief sought beyond halting the image generation remain unclear.

hackernews · DeepLogin · Nov 27, 19:42 · [Discussion](https://news.ycombinator.com/item?id=50670855)

**「Background」** Grok is xAI&\#x27;s chatbot distributed through X, and SpaceX is the parent company of both. According to the New York Times, SpaceX&\#x27;s May regulatory filing already acknowledged that Grok&\#x27;s ability to generate sexual content posed a risk to investors, before Virginia and Oregon&\#x27;s attorneys general brought this action.

**「Impact」** The complaint names SpaceX as the parent of both the AI developer and the social platform rather than suing xAI or X alone, so the case tests whether parent-company liability reaches Grok&\#x27;s image output; if the requested halt is granted, the practical effect falls on Grok&\#x27;s image-generation features and on X&\#x27;s content-moderation obligations while litigation continues.

**「Community Discussion」** Commenters questioned how Grok produced such images at all, asking whether its safeguards were unusually permissive or whether users had to deliberately prompt around them, and one asked whether the people generating the material would also face consequences. Another commenter asserted, without cited support in the thread, that the Supreme Court has already treated AI-generated child sexual abuse material made for personal use as protected speech, with carveouts barring depiction of real children — a claim that should be treated as an unverified opinion, not established law.

<details><summary>References</summary>
<ul>
<li><a href="https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform">Attorneys General Jones and Rayfield File Suit Against SpaceX ...</a></li>
<li><a href="https://www.nytimes.com/2026/11/23/technology/spacex-lawsuit-ai-sexualized-images.html">SpaceX Sued By Oregon and Virginia Over A.I.-Generated ...</a></li>

</ul>
</details>

**Tags**: `#AI safety`, `#generative AI`, `#content moderation`, `#legal/regulation`, `#xAI/Grok`

---

<a id="item-tech-news-6"></a>
### [Essay examines false computer-checked proofs from checker soundness bugs](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

This essay examines a failure mode for formal verification: a computer-checked proof can still be false if the proof checker itself has a soundness bug. The concern is therefore the trustworthiness of the checker as well as the proof, aimed at readers working with proof assistants and verified software.

hackernews · \_tk\_ · Nov 27, 15:26 · [Discussion](https://news.ycombinator.com/item?id=50667989)

**「Background」** Computer-checked proofs rely on a small kernel or proof checker that validates each inference step against axioms, so the guarantee is only as strong as the checker&\#x27;s soundness. A related earlier development is a 2022 computer-checked proof that a standalone HOL proof checker for the OpenTheory format is correct, illustrating efforts to validate the checking layer itself.

**「Impact」** For formal-verification users, the concrete consequence is that a machine-checked proof accepted by a single checker—or by two—can still fail to establish the claimed theorem if the proof was constructed to exploit checker bugs. Leonardo de Moura&\#x27;s postmortem for Lean kernel soundness bug \#14576 describes a proof built to exploit both that kernel bug and a separate, already-fixed nanoda bug, so projects should track checker versions, update after soundness fixes, and treat agreement among independent checkers as defense in depth rather than a guarantee.

**「Community Discussion」** Commenters debate how much that risk matters in practice: twotwotwo and dwheeler note that systems requiring multiple independent checkers make a single checker bug insufficient for a false result to be accepted—Metamath&\#x27;s main databases require five, dwheeler says—while gr\_norm argues the known soundness bugs are small enough for most software needs. andai raises a different failure mode: an agent can prove an implementation correct against its own mistaken understanding of the requirement.

<details><summary>References</summary>
<ul>
<li><a href="https://cr.yp.to/proofs/falseccp.html">False computer - checked proofs (djb)</a></li>
<li><a href="https://lean-lang.org/doc/reference/latest/releases/v4.32.2/">Lean 4.32.2 (2026-07-28)</a></li>
<li><a href="https://leodemoura.github.io/blog/2026-8-1-postmortem-for-kernel-soundness-bug-14576/">Postmortem for Kernel Soundness Bug #14576 — Leonardo de Moura</a></li>
<li><a href="https://arena.lean-lang.org/checker/nanoda/">nanoda - Lean Kernel Arena</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#proof assistants`, `#soundness`, `#software correctness`, `#Lean`

---

<a id="item-tech-news-7"></a>
### [SemiAnalysis Benchmarks Trainium3 Inference Costs Against Nvidia GB300](https://newsletter.semianalysis.com/p/trainium3-inferencex) ⭐️ 7.0/10

SemiAnalysis published a technical analysis arguing that AWS Trainium3 is competitive on inference cost, with its InferenceX benchmark showing Trainium3 and TPUs trading blows with or beating Nvidia GB300 on total cost of ownership per generated token. The analysis attributes part of the advantage to Trainium&\#x27;s tile-first microarchitecture and descriptor generation engines, which its microbenchmarks show can reach peak HBM bandwidth utilization at small message sizes—something the authors say is not possible on Nvidia GPUs. It also reports that Trainium3 with PDS and vLLM beats every accelerator except Vera Rubin across the TCO-versus-p90-interactivity frontier on the AgentX coding-agent replay workload. The supplied excerpt is truncated, so the full benchmark methodology, exact figures, and independent verification of the deeper claims cannot be assessed from the available text.

rss · Semianalysis · Nov 27, 15:54

**「Background」** AWS designs its own AI accelerators under the Trainium name through its Annapurna Labs chip unit, positioning them as an alternative to Nvidia GPUs for training and inference in the cloud. At the chip&\#x27;s unveiling in December 2024, AWS CEO Matt Garman said the 3nm Trainium3 would be roughly twice as fast as Trainium2 while using 40% less energy — a vendor claim about the silicon rather than a measured inference result. SemiAnalysis&\#x27;s new work places Trainium3 on its InferenceX benchmark suite alongside Google TPUv7, Nvidia&\#x27;s Rubin NVL72 and GB300, and AMD parts, which is what allows the cost-per-token comparisons in the piece to be made on a common footing.

**「Impact」** For organizations choosing inference hardware, the report makes total cost per token at a given interactivity target the relevant comparison and positions Trainium3 as a candidate alongside GB300 for small-message, HBM-bandwidth-bound workloads. The caveat is that the claimed edge is tied to the specific vLLM/PDS stack and AgentX coding-agent replay tested, not a general guarantee.

<details><summary>References</summary>
<ul>
<li><a href="https://technews.tw/2024/12/05/aws-trainium3-ai-chip-powered-by-3-nanometers/">3 奈米加持 AWS Trainium 3 AI... | TechNews 科技新報</a></li>

</ul>
</details>

**Tags**: `#Trainium3`, `#AI accelerators`, `#inference`, `#microarchitecture`, `#AWS`

---

<a id="item-tech-news-8"></a>
### [Minecraft Bedrock resource-pack flaw patched in 26.65](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

A resource-pack vulnerability in Minecraft Bedrock allowed packs containing a content.zipe file to modify Ore UI files and run hidden scripts, according to developer 8Crafter, who publicly disclosed it on November 15. 8Crafter said the flaw affected versions 26.52 through 26.63, with earlier versions possibly affected, across PC, mobile, and console; Java Edition was not affected. Joining a server or Realm with automatic resource-pack downloads could deliver the file without manual installation, enabling reported exploits such as deleting saves or obtaining a player&\#x27;s IP address and, on Windows under specific conditions, opening arbitrary URIs or launching a batch file to download malware. Mojang fixed the issue in version 26.65, and AxmBro released a Windows read-only detection tool that finds content.zipe but cannot determine whether a pack is malicious.

telegram · zaihuapd · Nov 27, 18:04

**「Why the delivery path mattered」** In Minecraft Bedrock, resource packs are client-side content that can include files touching the game&\#x27;s Ore UI interface framework, which is what let a pack carrying a content.zipe file run hidden scripts. The exposure depended on the auto-download setting: when enabled, joining a server or Realm could push a resource pack to the player without any manual installation step. Java Edition was not affected, according to developer 8Crafter, who disclosed the issue on Reddit on November 15.

**「Update before joining servers」** Players running Bedrock 26.52–26.63 should update to 26.65 before joining servers or Realms with automatic resource-pack downloads enabled, since the flaw is reachable without manually installing a pack. The 26.65 hotfix closes that path; the third-party Windows checker can flag a content.zipe file but cannot determine whether a pack is malicious, so it is not a substitute for patching.

<details><summary>References</summary>
<ul>
<li><a href="https://nqbrief.com/en/games/minecraft-bedrock-26-65-resource-pack-fix/">Minecraft Bedrock 26.65 released to fix resource-pack exploit</a></li>
<li><a href="https://minecraft.pl/en/news/minecraft-bedrock-mojang-patches-resource-pack-security-hole">Minecraft Bedrock: Mojang patches resource pack security</a></li>

</ul>
</details>

**Tags**: `#Minecraft Bedrock`, `#security vulnerability`, `#resource packs`, `#malware`, `#patch`

---