---
layout: default
title: "Horizon Summary: 2026-11-26 (EN)"
date: 2026-11-26
lang: en
---

> From 31 items, 8 important content pieces were selected

---

**Technology News**
1. [1Password Confirms Customer Account Data Theft After Employee GitHub Compromise](#item-tech-news-1) ⭐️ 8.0/10
2. [Tencent open-sources quantized Hy4 flash GGUF weights, smallest runs on 64 GB Mac mini](#item-tech-news-2) ⭐️ 8.0/10
3. [Minecraft Java RCE via Crafted Fonts Affects 1.20.5–1.21.10](#item-tech-news-3) ⭐️ 8.0/10
4. [Commerce Department Reportedly Threatened Intel Over 10% Government Stake](#item-tech-news-4) ⭐️ 8.0/10
5. [Ubuntu security patch delays draw practitioner scrutiny](#item-tech-news-5) ⭐️ 7.0/10
6. [Shorter Lean version of Anthropic&\#x27;s GRH verification released](#item-tech-news-6) ⭐️ 7.0/10
7. [Windows loudness treatment reverse-engineered for PipeWire](#item-tech-news-7) ⭐️ 7.0/10
8. [Samsung, SK Hynix reportedly to license YMTC Xtacking NAND tech](#item-tech-news-8) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [1Password Confirms Customer Account Data Theft After Employee GitHub Compromise](https://1password.com/blog/update-on-nov-2026-security-incident) ⭐️ 8.0/10

1Password confirmed a security incident in which attackers accessed internal systems and downloaded some customer account information, including names, email addresses, account identifiers, and account creation and last-login times; customer vaults and their contents were not affected. The company said it began investigating on November 19 after signs that an employee&\#x27;s enterprise GitHub account had been compromised, and that the attacker used that access to reach source code and push malicious code to backend services, which led to the information download. 1Password did not disclose how many users were affected; it has disabled the involved account, rotated or revoked potentially exposed internal credentials, and strengthened verification codes for invitation and recovery emails. The company said users do not need to change their accounts but should be alert to phishing.

hackernews · lxhrstn · Nov 25, 17:18 · [Discussion](https://news.ycombinator.com/item?id=50644817)

**「Background」** 1Password is a password manager whose service includes hosted vaults and account infrastructure in addition to its apps. The distinction matters here: the reported compromise involved account data such as names, email addresses, account identifiers and login timestamps, while 1Password said customer vaults and their contents were not affected.

**「Targeted phishing risk」** Customers whose names, email addresses, account identifiers, and login timestamps were accessed should expect phishing messages that cite real account details; the reported lure about a shared vault link is designed to look credible. 1Password says vault data and the keys protecting it were not affected, so users do not need to change their accounts or rotate stored secrets.

**「Community Discussion」** Commenters focused on the SaaS supply-chain path: tptacek called a compromised employee laptop with code-push access the standard pattern behind SaaS breaches, while ctidd asked why the write-up did not say whether branch protection or push-to-main controls were missing or bypassed. A user reported receiving a detailed phishing email, not from an official 1Password domain but including some of their details, that they assumed drew on incident data; a longtime user said the episode reinforced their choice of a local-only vault, and another commenter wanted 1Password to state explicitly that the encrypted vault was not downloaded.

<details><summary>References</summary>
<ul>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving... | 1 Password</a></li>
<li><a href="https://www.macrumors.com/2026/11/25/1password-security-breach/">1 Password Security Breach: What Was Accessed and... - MacRumors</a></li>

</ul>
</details>

**Tags**: `#security`, `#1Password`, `#SaaS`, `#supply-chain`, `#phishing`

---

<a id="item-tech-news-2"></a>
### [Tencent open-sources quantized Hy4 flash GGUF weights, smallest runs on 64 GB Mac mini](https://mp.weixin.qq.com/s/o0xxShVQX6g2UllrrEv1WQ) ⭐️ 8.0/10

Tencent Hunyuan has open-sourced GGUF quantized weights for its 224B-parameter Hy4 flash model through its AngelSlim compression and acceleration toolkit. The original weights are about 410.27 GiB, while the smallest IQ2-AH variant is 125.73 GiB—roughly 30% of the original—and is reported to run on a 64 GB Mac mini with the Strata offload framework, meaning it relies on offloading rather than fitting in memory. Reported figures put a 48 GB VRAM device at 89 tokens/s with 10K context, and an M5 Max 128 GB machine at 47 tokens/s with 32K context using Q3\_K. On evaluations including DeepSWE v1.1, Tencent reports that Q3\_K scored within 0.4 points of the original model.

telegram · zaihuapd · Nov 25, 09:29

**「Background」** GGUF is a quantized weight format used by local inference runtimes; quantization stores weights at lower precision to reduce file size and memory use. A 224B-parameter model normally cannot fit within a 64 GB Mac mini, and the source credits the Strata offload framework with enabling the smallest IQ2-AH release to run there.

**「Practical impact」** Local-inference users now have downloadable GGUF weights and companion inference code, but the smallest IQ2-AH file is still 125.73 GiB, so running on a 64 GB Mac mini depends on Strata offload rather than fitting in memory. A 48 GB VRAM device is cited at 89 tokens/s with 10K context, while the Q3\_K version is reported within 0.4 points of the original on DeepSWE v1.1; the Mac mini claim should be treated as a compatibility statement, not a measured throughput result.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ithome.com/1/032/131.htm">让大模型跑在个人设备上， 腾 讯 混 元 开源 Hy 4 flash GGUF ...</a></li>

</ul>
</details>

**Tags**: `#Tencent Hunyuan`, `#model quantization`, `#GGUF`, `#local inference`, `#Apple Silicon`

---

<a id="item-tech-news-3"></a>
### [Minecraft Java RCE via Crafted Fonts Affects 1.20.5–1.21.10](https://github.com/bikini/minecraft2shell) ⭐️ 8.0/10

A publicly disclosed Minecraft Java Edition vulnerability, minecraft2shell, allows a crafted TrueType font in a server resource pack to trigger a native out-of-bounds write in FreeType 2.14.3 and earlier and execute arbitrary code on a Java Edition 26.3 Windows client. Versions 1.20.5 through 1.21.10 and snapshots 26.1 through 26.4 are affected, while 1.20.4 and earlier and Bedrock Edition are not. As of the report, Mojang had no official patch and still used lwjgl-freetype 3.4.3; the community released m2sfix 1.0.0 on November 24, which uses a Java agent or mod to disable hinting. Users are advised not to add resource packs, to set multiplayer server resource-pack permissions to disabled, or to install the temporary fix.

telegram · zaihuapd · Nov 25, 12:46

**「Background」** Minecraft Java Edition can load resource packs supplied by servers, including custom fonts, which the client renders through the bundled native FreeType library. The public proof of concept is build-specific, targeting the Mojang-signed Java Edition 26.3 Windows client with FreeType 2.14.3 x64.

**「Who needs to act」** Because the exploit arrives through a server-pushed resource pack, the exposure runs in both directions: players on affected Java versions \(1.20.5 through 1.21.10 and the 26.1–26.4 snapshots\) can be compromised by joining an untrusted server, and server operators on those versions can compromise their own players. Until Mojang ships a fix, the practical mitigations are to set multiplayer resource-pack permissions to &quot;Disabled&quot; \(the reporter&\#x27;s advice is to add no resource packs at all\) or to install the community m2sfix 1.0.0, which disables font hinting via a Java agent or mod. Servers running 1.20.4 or earlier, and all Bedrock Edition players, do not need to take these steps.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/bikini/minecraft2shell">GitHub - bikini/ minecraft 2 shell : Minecraft to native RCE · GitHub</a></li>

</ul>
</details>

**Tags**: `#Minecraft`, `#RCE`, `#FreeType`, `#security vulnerability`, `#Java Edition`

---

<a id="item-tech-news-4"></a>
### [Commerce Department Reportedly Threatened Intel Over 10% Government Stake](https://www.wired.com/story/inside-trumps-demands-to-another-chips-ceo/) ⭐️ 8.0/10

Court filings reportedly show that in August 2025, lawyers for the US Commerce Department told Intel&\#x27;s chief financial officer in a phone call not to &quot;mistake this for a negotiation,&quot; and that the president wanted an agreement announced by Friday. The lawyers said the board could refuse, but warned that doing so would bring unpredictable consequences. Days later, Intel&\#x27;s board handed over the requested shares. Trump then announced that the US government &quot;fully owns and controls&quot; 10% of Intel without having paid for the stake, which is now worth about $11 billion. The account comes from a WIRED report relayed in the source item; the details are attributed to court filings rather than independent verification.

telegram · zaihuapd · Nov 25, 13:25

**「Background」** Federal equity stakes in private companies are rare; NPR noted that past examples came during wars or economic crises, whereas the Intel stake was driven by the AI chip race. Earlier reporting described the 10% holding as a conversion of existing grants into Intel shares, a structure distinct from the confrontation described in the court filings.

**「Why It Matters」** The filing, as reported, describes a board told it could reject the demand only at the risk of unspecified consequences, which gives the executive branch a 10% equity voice in Intel&\#x27;s decisions and documents the pressure tactics other chipmakers could face in dealings with the Commerce Department.

<details><summary>References</summary>
<ul>
<li><a href="https://www.npr.org/2025/09/06/nx-s1-5530190/government-stake-intel-ai-competition-china">The U.S. government is taking a stake in Intel . It&#x27;s rare — and... : NPR</a></li>
<li><a href="https://www.finance-monthly.com/us-intel-10-percent-stake/">US Eyes 10 % Stake in Intel to Boost Chip Manufacturing</a></li>

</ul>
</details>

**Tags**: `#Intel`, `#semiconductor industry`, `#US government policy`, `#corporate governance`, `#tech industry`

---

<a id="item-tech-news-5"></a>
### [Ubuntu security patch delays draw practitioner scrutiny](https://www.openwall.com/lists/oss-security/2026/11/25/9) ⭐️ 7.0/10

A thread posted to the oss-security mailing list on 25 November 2026 raises concerns about slow security response times in Ubuntu, prompting Hacker News readers to describe moving production server images to Debian. The item as supplied contains no CVE identifiers, affected package versions, patch dates, or comparison timelines, so the size and scope of any specific delay is not established; the concrete evidence here is practitioner anecdote rather than a measured patch-latency comparison. Commenters describe the issue as a reason to reconsider Ubuntu as the default choice for generic Linux VMs and servers.

hackernews · gslin · Nov 25, 20:38 · [Discussion](https://news.ycombinator.com/item?id=50647181)

**「Context」** The discussion centers on a specific case: an oss-security post reported that Ubuntu took multiple weeks to ship a fix for CVE-2026-98432, a remote TCP corruption flaw. That matters because users of a long-term-support distribution generally do not track upstream releases themselves; they depend on the vendor to backport security patches into the versions they already run, so the vendor&\#x27;s turnaround time effectively becomes their exposure window.

**「Impact」** For teams standardized on Ubuntu servers, the reported consequence is a base-image change: commenter cjk said their workplace moved all server images to Debian over the issue. Commenter alanfranz described a related operational adjustment for those staying on Ubuntu — security fixes appearing in the -updates repository hours before the security repository — and said they switched unattended upgrades from security-only to installing all updates, accepting the risk of breaking a system.

**「Community Discussion」** Commenters disagreed on whether faster patching is the right trade-off: cjk called slow security response from a widely used distribution unacceptable in 2026, while gdgghhhhh argued that major distributions spend substantial time on regression testing and that Debian, despite doing strong work, has limited QA resources, linking a Debian bug report as an example of a regression. skhameneh reported hesitating for the first time and choosing Debian for a generic Linux VM because of the slow patches, and alanfranz noted the ordering of fixes between -updates and the security repository.

<details><summary>References</summary>
<ul>
<li><a href="https://www.openwall.com/lists/oss-security/2026/11/25/9">oss - security - Slow Ubuntu security response times</a></li>

</ul>
</details>

**Tags**: `#Ubuntu`, `#Linux distributions`, `#security patching`, `#open source`, `#vulnerability management`

---

<a id="item-tech-news-6"></a>
### [Shorter Lean version of Anthropic&\#x27;s GRH verification released](https://github.com/lsernau/grh-lean) ⭐️ 7.0/10

A GitHub repository by lsernau offers a much shorter Lean formalization of Anthropic&\#x27;s GRH verification, with a clear separation between &quot;known math&quot; and &quot;new math&quot; and human-readable documentation throughout. Commenters report a reduction from roughly 17 million lines to about 76,000 lines, or 99.56%, although another describes the readable proof as roughly 300,000 lines, so the exact size is not settled in the supplied discussion. The work is a more approachable derivative of the existing verification rather than a new proof, and its claims are being assessed mainly through the repository and community discussion.

hackernews · nb-t · Nov 25, 21:48 · [Discussion](https://news.ycombinator.com/item?id=50648050)

**「Background」** Lean is a proof assistant, so a formalization is checked mechanically rather than by a reader; the Lean community blog describes checkers that carry a formal proof, relative to set theory, that they cannot accept a false proof \(tool-2-1\). Anthropic’s GRH work was already being discussed as a claimed formal proof of the Riemann Hypothesis before this shorter derivative appeared \(tool-2-3\).

**「Impact」** For formal-methods researchers and mathematicians trying to inspect Anthropic&\#x27;s verification, the explicit known-versus-new split and documentation provide a practical way to review the proof&\#x27;s structure without working through an opaque machine-generated artifact.

**「Community discussion」** Commenters broadly welcome the readability gains, with one saying the known-versus-new split and documentation should greatly aid digestion. One commenter asks whether smarter LLMs that can golf and explain proofs address Tao&\#x27;s recent concern about huge proofs lacking insight, while another wants mathematicians to produce a conventional paper and conference presentation explaining the core argument.

<details><summary>References</summary>
<ul>
<li>Lean verification of the Riemann Hypothesis | Lean community blog</li>
<li>Anthropic claims to have proven the Riemann Hypothesis - some thoughts from a mathematician : r/antiai - Reddit</li>

</ul>
</details>

**Tags**: `#Lean`, `#formal verification`, `#AI-assisted mathematics`, `#proof compression`, `#mathematics`

---

<a id="item-tech-news-7"></a>
### [Windows loudness treatment reverse-engineered for PipeWire](https://github.com/xoxorwr/pw-loudness-eq) ⭐️ 7.0/10

A GitHub project called pw-loudness-eq reverse-engineers Windows&\#x27; loudness equalization/normalization behavior and reimplements it as a PipeWire component for Linux audio. The supplied material does not include version, release, or compatibility details. The Hacker News discussion adds two concrete caveats: the effect is loudness normalization rather than equalization unless gain is changed by frequency, and the described algorithm may boost focused impulses or pure tones, so it requires final limiting.

hackernews · ThrowNotAway · Nov 25, 11:34 · [Discussion](https://news.ycombinator.com/item?id=50641171)

**「Why PipeWire is the target」** PipeWire is the Linux audio server that receives streams from applications, mixes them, and routes the result to headphones, speakers, or another output. Windows has long provided a loudness-equalization playback enhancement, while Linux desktop audio stacks have lacked a built-in equivalent; discussion around pw-loudness-eq points to that gap as the reason for the port.

**「Impact」** PipeWire users evaluating the component should check its final limiting and clipping behavior, especially with pure tones or impulse-heavy material, because commenters identified gain boosts on focused impulses as a risk.

**「Community discussion」** Commenters debated terminology, with one arguing the feature is loudness normalization rather than equalization unless gain is adjusted by frequency, and warned that the algorithm could boost focused impulses or pure tones and therefore needs final limiting. Another commenter reported that Windows shared-mode WASAPI, DirectSound, and MME playback apply slight peak compression while WASAPI exclusive and ASIO do not, and others questioned why reverse-engineering a Windows DLL was necessary, calling the behavior simple and raising ethical concerns.

<details><summary>References</summary>
<ul>
<li><a href="https://news.ycombinator.com/item?id=50641171">Windows Loudness Equalization , reverse-engineered... | Hacker News</a></li>
<li><a href="https://dzen.ru/a/awboyMYszWEiZCxr">Алгоритм выравнивания громкости Windows заработал... | Дзен</a></li>

</ul>
</details>

**Tags**: `#audio processing`, `#reverse engineering`, `#PipeWire`, `#Linux audio`, `#DSP`

---

<a id="item-tech-news-8"></a>
### [Samsung, SK Hynix reportedly to license YMTC Xtacking NAND tech](https://tech.ifeng.com/c/8yLRPKxQy4L) ⭐️ 7.0/10

Samsung Electronics and SK Hynix have reportedly agreed, through a cross-license deal, to adopt parts of Yangtze Memory Technologies&\#x27; Xtacking technology in 3D NAND flash production. The arrangement would let the two South Korean memory makers use YMTC&\#x27;s wafer-bonding approach, which fabricates memory cells and CMOS control circuitry on separate wafers before joining them. The report relies on unnamed claims, and Samsung, SK Hynix and YMTC declined to comment, so the scope, terms and timing of any licensing remain unconfirmed.

telegram · zaihuapd · Nov 25, 14:33

**「What Xtacking does」** Xtacking is YMTC&\#x27;s 3D NAND architecture that fabricates the memory cell array and the CMOS control circuitry on two separate wafers, then joins them with a bonding step, so each half can be produced and optimized independently. In the account given in the report, an Omdia senior analyst says the split lets a memory maker build the array itself while handing the logic circuitry to a foundry, gaining access to more advanced process nodes than a conventional single-wafer NAND flow allows.

**「What changes on the fab side」** Both Korean makers are pushing NAND toward hundreds of layers and reportedly hitting single-wafer limits, so adopting Xtacking would mean fabricating the memory array and CMOS logic on separate wafers and bonding them — letting the logic portion be built on a foundry process node rather than the NAND process itself. The arrangement is described as a cross-license, giving YMTC reciprocal access to Samsung and SK Hynix patents, which extends the patent pressure YMTC began with its 2024 infringement suit against Micron. Because all three companies declined to comment, the exact scope of licensed patents and any production timeline remain unconfirmed.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Yangtze_Memory_Technologies">Yangtze Memory Technologies - Wikipedia</a></li>
<li><a href="https://www.techpowerup.com/355199/samsung-and-sk-hynix-to-license-ymtcs-xtacking-technology">Samsung and SK hynix to License YMTC &#x27;s Xtacking ... | TechPowerUp</a></li>

</ul>
</details>

**Tags**: `#3D NAND`, `#semiconductor manufacturing`, `#YMTC`, `#Samsung`, `#SK Hynix`

---