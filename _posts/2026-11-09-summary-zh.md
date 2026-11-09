---
layout: default
title: "Horizon Summary: 2026-11-09 (ZH)"
date: 2026-11-09
lang: zh
---

> 从 30 条内容中筛选出 1 条重要资讯。

---

**科技新闻**
1. [KetchUp：用 Rust 与 WebGPU 构建的开源浏览器版 SketchUp 替代品](#item-tech-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [KetchUp：用 Rust 与 WebGPU 构建的开源浏览器版 SketchUp 替代品](https://ketchup3d.github.io/app/) ⭐️ 7.0/10

KetchUp 是一个用 Rust 和 WebGPU 构建的开源 SketchUp 替代品，可直接在浏览器中运行并进行 3D 建模。Hacker News 上的反馈认可其界面与文本渲染效果，但也指出当前缺少触控板操作、基本只能用鼠标，说明项目仍处于早期阶段。部分用户把它视为 SketchUp 的精神续作，尤其看重简单、快速的自定义建模，但现有信息不足以判断其功能完整度和后续维护情况。

hackernews · dcoulmbe · 11月8日 22:35 · [社区讨论](https://news.ycombinator.com/item?id=50418176)

**「背景」** KetchUp 将自身定位为 SketchUp 的免费开源替代品，目标场景包括木工和家具设计中的精确尺寸建模。项目仓库称其以 Rust 编写，通过 WebAssembly 和 WebGPU 在浏览器或桌面端运行，这解释了它为何能以网页应用形式提供本地 3D 建模界面。

**「对建模用户的实际影响」** 对希望避开桌面建模软件束缚的用户来说，KetchUp 提供的是一个开源、直接在浏览器里运行的建模入口，不必安装本地程序；但输入支持仍是当前的实用短板：有评论者反馈它只能靠鼠标操作，触控板用户无法完成平移、缩放和环绕，笔记本用户需外接鼠标才能顺畅使用。若要承担日常替代桌面 SketchUp 的角色，补齐触控板与手势导航是使用者首先会遇到的兼容性门槛。

**「社区讨论」** 有评论者请求加入触控板支持，称目前只能用鼠标，无法像在 SketchUp 中那样用触控板配合修饰键完成平移、缩放和旋转。另一些用户称赞 Rust 界面和浏览器内文本渲染，并把它看作 SketchUp 在被多次转手、免费功能减少后的精神续作，希望用于 3D 打印所需的简单自定义建模。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/Ketchup3D/app">GitHub - Ketchup3D/app: Free, open-source 3D modeling ...</a></li>
<li><a href="https://ketchup3d.github.io/app/">KetchUp — Free 3D Woodworking &amp; Furniture Design App</a></li>

</ul>
</details>

**标签**: `#Rust`, `#WebGPU`, `#open-source`, `#3D modeling`, `#browser applications`

---