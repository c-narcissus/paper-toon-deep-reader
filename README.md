# Paper Deep Reading Teaching Explainer

**一句话：把论文变成能讲、能答、能在手机上翻看的卡通精读 PDF。**

[English README](README_EN.md)

## 100 字总结

这个 skill 面向组会、课程、复现和答辩场景：先基于论文 PDF/LaTeX 生成可追溯的精读报告，再按背景、方法、实验、局限、未来方向分阶段生成连续卡通图，最后把确认后的图片合成 PDF。默认手机竖屏、中文对白、风格一致，也支持自定义画幅、语言和漫画风格。

## 案例效果

示例来自 `SemiDFL` 论文：先产出精读报告，再分阶段生成 18 张卡通讲解页，最后合成为 PDF。该示例是早期 16:9 横版效果；当前版本默认生成 9:16 手机竖屏，用户仍可切回 16:9。

<div align="center">
  <img src="assets/demo/storyboard-pages-01-18-contact-sheet.jpg" width="680" alt="18-page cartoon storyboard overview" />
</div>

<p align="center">
  <img src="assets/demo/page-01.png" width="22%" alt="Cartoon explainer page 1: background and motivation" />
  <img src="assets/demo/page-07.png" width="22%" alt="Cartoon explainer page 7: algorithm round workflow" />
  <img src="assets/demo/page-13.png" width="22%" alt="Cartoon explainer page 13: experiment setup" />
  <img src="assets/demo/page-18.png" width="22%" alt="Cartoon explainer page 18: final summary" />
</p>

- 示例 PDF：[SemiDFL_cartoon_explainer_pages_1-18.pdf](example/SemiDFL_cartoon_explainer_pages_1-18.pdf)
- ChatGPT 项目页面导出示例：[SemiDFL deep reading report .mhtml](example/SemiDFL%20deep%20reading%20report%20.mhtml)
- Skill 包：[paper-deep-reading-teaching-explainer-v10.1.12-clawhub.zip](paper-deep-reading-teaching-explainer-v10.1.12-clawhub.zip)
- ClawHub 地址：[paper-deep-reading-teaching-explainer](https://clawhub.ai/c-narcissus/paper-deep-reading-teaching-explainer)

## 它能做什么

- **先精读**：生成证据约束的论文精读报告，覆盖背景、问题、假设、方法、实验、局限和可延伸研究方向。
- **再讲解**：把论文转成 30 秒、3 分钟、10 分钟都能讲清楚的版本，并准备公式、图表、实验、误解提醒和答辩 Q&A。
- **再画图**：把报告拆成背景、方法、实验、局限、未来方向等阶段，生成连续卡通漫画页。
- **最后合成 PDF**：把用户确认后的图片按顺序合成为一份可分享的讲义。
- **防止跑偏**：生图前检查原文和精读报告，避免编造数据、模块、结论或实验细节。
- **保持连续**：角色、风格、画幅、对白语言、符号、页面编号、运镜和数据流方向会在后续批次中继承。

## 主要步骤

| 阶段 | 产出 |
| --- | --- |
| Step 0 | 完整文字精读报告、教学讲解准备、当前状态、下一步提示 |
| Step 1 | 背景、旧方法缺陷、论文问题、灵感来源 |
| Step 2 | 算法整体流程、模块输入输出、符号、维度、训练和推理 |
| Step 3 | 数据集、指标、baseline、主结果、消融、例外和复现风险 |
| Step 4 | 局限性、审稿质疑、答辩口径和防御性解释 |
| Step 5 | 未来方向、隐藏假设和创新图谱 |
| Step 6 | 封面、总结页和 Q&A 备用页 |
| Step 7 | 将所有确认后的卡通图合成为 PDF |

## 推荐使用方法

### ChatGPT 网页版 / App

强烈建议在 ChatGPT 网页版 / App 的 Project 中使用。卡通图阶段最适合直接使用 ChatGPT 的 **Create image** 能力。

1. 打开 [ClawHub 页面](https://clawhub.ai/c-narcissus/paper-deep-reading-teaching-explainer)，下载 skill zip。
2. 在 ChatGPT 网页版中新建或打开一个 Project。
3. 先把 skill 放进 Project 的 `Sources`，建议上传 skill zip。
4. 确认 skill 已在 `Sources` 后，再上传论文 PDF / LaTeX。
5. 先让 skill 生成完整文字精读报告，不要第一步就生图。
6. 按状态提示逐阶段生成卡通图。下一步要生图时，明确说：`生成多张连续的卡通图`。
7. 所有图片确认后，执行最终 PDF 合成。

可直接使用的提示词：

```text
使用这个skill，精读这篇论文，先生成完整文字报告，不要生成图片。
```

```text
使用这个skill，根据状态，执行第1步：生成多张连续的卡通图，内容是背景、旧方法缺陷、论文问题和灵感来源。
```

```text
使用这个skill，根据状态，执行最后一步：把所有已经生成并确认的图合成一个PDF。
```

如果不知道下一步怎么问：

```text
使用这个skill，根据状态，告知下一步应该问什么。
```

### Codex / coding-agent

Codex、Claude Code 或其他 coding-agent 环境也可以使用，但完整卡通生图流程通常更适合在 ChatGPT 网页版完成。

- 生图时优先使用 `imagegen` skill。
- `imagegen` 不可用或能力不足时，再使用 ChatGPT Images 2.0 API 或其他用户批准的生图 API。
- Codex 更适合整理文件、检查 README、更新 skill、打包 zip、合成 PDF 和提交 GitHub。
- PDF 合成脚本默认使用 `1080x1920` 的 9:16 手机竖屏画幅，也可通过 `--page-width` / `--page-height` 修改。

## 默认设置

- **画幅**：默认 `9:16` 手机竖屏，可改为 `16:9`、`4:5`、`1:1`、`3:4` 或自定义比例。
- **语言**：默认中文对白、旁白、标题和标签；可改为英文、中英双语或其他语言。
- **风格**：默认课堂板书漫画，也可选扁平教育信息图、手绘白板草图、轻日漫科研课堂、柔和 3D 黏土/立体卡通。
- **人物设定**：默认课堂场景，一个老师/讲解者加 2-3 个学生或研究者听众。
- **图片数量**：多图不是越多越好。每张图必须有独立教学增量，重复的开场、动机、转场或总结页会被剪掉。

## 适合谁用

- 需要快速讲清一篇论文的研究生、科研人员和工程研究团队。
- 要准备组会、课程展示、论文复现汇报或答辩材料的用户。
- 想把抽象算法、实验和局限性转成直观视觉材料的讲解者。
- 需要从论文中挖掘后续研究想法的人。

## OpenClaw / ClawHub CLI

```bash
openclaw skills install paper-deep-reading-teaching-explainer
```

## License

MIT-0
