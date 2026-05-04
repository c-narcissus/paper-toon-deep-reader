# Paper Deep Reading Teaching Explainer

把一篇论文从“读过”推进到“讲得清、能答辩、可展示”的教学型精读 skill。

这个 skill 面向科研阅读、组会讲解、论文复现准备、答辩演示和课程助教场景。它先生成有证据约束的论文精读报告，再把报告拆成多个阶段的卡通漫画讲解图，最后把确认后的图片合成为一份可分享的 PDF。

[English README](README_EN.md)

## 推荐使用方式：ChatGPT 网页版

**强烈建议在 ChatGPT 网页版 / App 的 Project 里使用这个 skill。** 这个 skill 的核心体验是“先精读，再分阶段生成卡通图，再合成 PDF”，其中卡通图阶段最适合直接使用 ChatGPT 的 Create image 能力。

使用前请先做一件事：**先把 skill 放进 ChatGPT Project 的 Sources 里，再上传论文。** 不建议只上传论文就直接提问，否则模型可能只做普通论文总结，无法稳定遵守分阶段精读、漫画生成和 PDF 合成流程。

ClawHub skill 地址：

[https://clawhub.ai/c-narcissus/paper-deep-reading-teaching-explainer](https://clawhub.ai/c-narcissus/paper-deep-reading-teaching-explainer)

推荐使用步骤：

1. 打开上面的 ClawHub 页面，下载 skill zip。
2. 在 ChatGPT 网页版中新建或打开一个 Project。
3. 在 Project 的 `Sources` 里放入这个 skill，建议上传 skill zip，或上传解压后的 `SKILL.md`、`README.md` 和相关 workflow/schema 文件。
4. 确认 skill 已经在 `Sources` 中后，再上传要精读的论文 PDF / LaTeX。
5. 先要求生成完整文字精读报告，不要在第一步生成图片。
6. 按 skill 给出的下一步提示，分阶段生成卡通图，最后合成 PDF。

OpenClaw / ClawHub CLI 用户也可以使用：

```bash
openclaw skills install paper-deep-reading-teaching-explainer
```

如果在 Codex、Claude Code 或其他 coding-agent 环境中使用，生成卡通图时建议优先调用 `imagegen` skill；只有在 `imagegen` 不可用或能力不足时，再使用 ChatGPT Images 2.0 API 或其他用户批准的生图 API。

## 效果预览

下面示例来自 `SemiDFL` 论文的一次完整运行：先产出精读报告，再分阶段生成 18 张卡通讲解页，最后合成为 PDF。

![18-page cartoon storyboard overview](assets/demo/storyboard-pages-01-18-contact-sheet.jpg)

<p>
  <img src="assets/demo/page-01.png" width="49%" alt="Cartoon explainer page 1: background and motivation" />
  <img src="assets/demo/page-07.png" width="49%" alt="Cartoon explainer page 7: algorithm round workflow" />
</p>
<p>
  <img src="assets/demo/page-13.png" width="49%" alt="Cartoon explainer page 13: experiment setup" />
  <img src="assets/demo/page-18.png" width="49%" alt="Cartoon explainer page 18: final summary" />
</p>

- 示例 PDF：[SemiDFL_cartoon_explainer_pages_1-18.pdf](example/SemiDFL_cartoon_explainer_pages_1-18.pdf)
- ChatGPT 项目页面导出示例：[SemiDFL deep reading report .mhtml](example/SemiDFL%20deep%20reading%20report%20.mhtml)
- Skill 包：[paper-deep-reading-teaching-explainer-v10.1.8-clawhub.zip](paper-deep-reading-teaching-explainer-v10.1.8-clawhub.zip)

## 这个 Skill 做什么

它把论文处理成三个层次的交付物：

1. **论文精读报告**：梳理论文背景、问题、核心假设、方法结构、实验逻辑、局限性和可延伸的研究想法。
2. **教学讲解材料**：把复杂方法转成 30 秒、3 分钟、10 分钟都能讲清楚的版本，并准备公式讲解、图表讲解、实验讲解、误解提醒和答辩 Q&A。
3. **卡通漫画讲解 + PDF**：在精读报告完成后，分阶段生成连续漫画页，覆盖背景动机、旧方法缺陷、算法模块、实验结果、局限与答辩、未来方向，最后合成为一份完整 PDF。
4. **连续分镜一致性**：生成连续多张卡通图时，会要求保持角色、风格、色彩、符号、数据流方向、页面编号和运镜逻辑一致；后续批次会继承前面已生成图片的 storyboard bible。
5. **生图防幻觉检查**：生图提示和生成结果都要尊重原文和前面的权威精读报告；不支持的事实会删除、标为 `未报告`，或要求用户补充证据。
6. **多图拆分表达**：不同部分默认拆成多张连续图，一图一个教学重点，不把背景、算法、实验、局限等内容硬塞进一张大图。
7. **下一步提示更直接**：不再固定输出下一步 skill 推荐；如果下一步是生图，会明确提醒用户说“生成多张连续的卡通图”。

## 推荐工作流

```mermaid
flowchart LR
  A["上传论文 PDF / LaTeX"] --> B["生成精读报告"]
  B --> C["给出当前状态和下一步建议"]
  C --> D["分阶段生成卡通漫画"]
  D --> E["用户确认或要求修改"]
  E --> F["合成最终 PDF"]
```

默认分阶段流程：

| 阶段 | 输出内容 |
| --- | --- |
| Step 0 | 完整文字精读报告、教学讲解准备、当前状态、下一步提示 |
| Step 1 | 背景、旧方法缺陷、论文问题、灵感来源 |
| Step 2 | 算法整体流程与模块解释 |
| Step 3 | 实验设置、指标、结果、消融和鲁棒性 |
| Step 4 | 局限性、审稿答辩和防御性解释 |
| Step 5 | 未来方向和创新图谱 |
| Step 6 | 封面、总结页和 Q&A 备用页 |
| Step 7 | 将所有确认后的图片合成为 PDF |

## 用户体验亮点

- **先读懂，再画图**：不会一上来就生成图片，而是先产出完整精读报告，避免漫画只好看但不准确。
- **分阶段推进**：每次只生成一个阶段，方便用户检查、修改、补充要求。
- **会主动告诉用户下一步怎么问**：每个阶段都会给出当前状态、推荐下一步和可直接复制的用户输入。
- **适合上下文丢失后的恢复**：如果换了新会话，可以用固定句式继续，例如：`使用这个skill，根据状态，执行第2步：生成算法整体流程与各模块解释的连续卡通图。`
- **支持“不知道下一步问什么”**：用户可以直接说：`使用这个skill，根据状态，告知下一步应该问什么。`
- **面向教学和答辩**：不仅总结论文，还会准备讲稿、误解防护、角色扮演讨论、答辩问题库和展示结构。
- **最终交付友好**：漫画页可以合成 PDF，用于组会、课堂、读书会、论文分享或复习材料。

## 适合谁用

- 需要快速讲清一篇论文的研究生、科研人员和工程研究团队。
- 要准备组会、课程展示、论文复现汇报或答辩材料的用户。
- 想把抽象算法、实验和局限性转成直观视觉材料的讲解者。
- 需要从论文中挖掘后续研究想法的人。

## 快速开始

1. 从 ClawHub 下载 skill，或使用本仓库中的 `paper-deep-reading-teaching-explainer-v10.1.8-clawhub.zip`。
2. 推荐在 ChatGPT 网页版 Project 中使用，并先把 skill 放入 Project `Sources`。
3. 然后上传论文 PDF、LaTeX 源码，或同时提供两者。
4. 先让 skill 生成完整文字精读报告。
5. 根据它给出的下一步提示，逐阶段生成卡通图。
6. 所有图片确认后，执行最终 PDF 合成。

可用提示示例：

```text
使用这个skill，精读这篇论文，先生成完整文字报告，不要生成图片。
```

```text
使用这个skill，根据状态，执行第1步：生成背景、旧方法缺陷、论文问题和灵感来源的连续卡通图。
```

```text
使用这个skill，根据状态，执行最后一步：把所有已经生成并确认的图合成一个PDF。
```

## 示例成果

当前仓库中的 `example` 文件夹包含一次完整样例：

- 18 张卡通讲解图片；
- 由 18 张图片合成的 PDF；
- ChatGPT 项目聊天页面导出的 mhtml，展示了实际使用过程和结果。

这些示例可以帮助新用户快速理解：这个 skill 的重点不是一次性生成漂亮插图，而是把论文精读、教学讲解、分阶段视觉化和最终材料打包成一条完整工作流。

## License

MIT-0
