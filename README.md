# Paper Deep Reading Teaching Explainer

**一句话：把论文变成能讲、能答、能在手机上翻看的卡通精读 PDF。**

[English README](README_EN.md)

这个 skill 面向组会、课程、复现和答辩场景：先基于论文 PDF/LaTeX 生成可追溯的 Markdown 精读报告，再按背景、方法、实验、局限、未来方向分阶段生成连续卡通图，最后把确认后的卡通图和 Markdown 报告合成同一个 PDF，卡通图在前、报告在后。默认手机竖屏、中文对白、风格一致，也支持自定义画幅、语言和漫画风格。

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
- Skill 包：见本仓库根目录最新 zip 文件。

## 它能做什么

- **先精读**：生成证据约束的论文精读报告，覆盖背景、问题、假设、方法、实验、局限和可延伸研究方向。
- **再讲解**：把论文转成 30 秒、3 分钟、10 分钟都能讲清楚的版本，并准备公式、图表、实验、误解提醒和答辩 Q&A。
- **再画图**：把报告拆成背景、方法、实验、局限、未来方向等阶段，生成多张独立页面组成的连续卡通漫画。
- **不是单图**：默认产物不是一张大海报或合并长图；单张图只作为用户明确要求的压缩概览。
- **少量分批**：一张图只讲一个重点，内容复杂时分多次回答，每次生成几张连续漫画页。
- **主视觉命题**：每页围绕一个中心图式或场景组织信息，少量支撑卡片服务同一个结论，避免多主题清单海报。
- **可配置构图**：默认是主视觉命题，也可改成流程分镜、左右对比、答辩问答卡、极简概念卡，或用参考图引导。
- **最后合成 PDF**：把用户确认后的卡通图放在前面，再把 Markdown 精读报告放在后面，合成为一份可分享的讲义。
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
| Step 7 | 将所有确认后的卡通图和 Markdown 精读报告合成为同一个 PDF，卡通图在前 |

## 使用方法

ChatGPT 网页版 / App 和 Codex / coding-agent 环境都可以使用这个 skill。如果想节省 token，建议优先在 ChatGPT 网页版 Project 中完成完整精读、生图和 PDF 流程；Codex 更适合本地文件整理、脚本执行、打包和 GitHub 提交。

### ChatGPT 网页版 / App

1. 在 ChatGPT 网页版中新建或打开一个 Project。
2. 先把本仓库中的 skill zip 放进 Project 的 `Sources`。
3. 确认 skill 已在 `Sources` 后，再上传论文 PDF / LaTeX。
4. 先让 skill 生成完整文字精读报告，不要第一步就生图。
5. 按状态提示逐阶段、分小批生成卡通图。下一步要生图时，明确说：`生成多张连续的卡通图`；复杂阶段可以继续说：`继续生成下一批多张连续的卡通图`。
6. 所有图片确认后，执行最终 PDF 合成：卡通图在前，Markdown 精读报告在后。

可直接使用的提示词：

```text
严格遵守skill里的步骤：精读这篇论文，先生成完整文字报告，不要生成图片。
```

```text
严格遵守skill里的步骤：根据状态，执行第1步：生成多张连续的卡通图，内容是背景、旧方法缺陷、论文问题和灵感来源。
```

```text
严格遵守skill里的步骤：根据状态，执行最后一步：把所有已经生成并确认的卡通图和Markdown精读报告合成一个PDF，卡通图在前面。
```

如果不知道下一步怎么问：

```text
严格遵守skill里的步骤：根据状态，告知下一步应该问什么。
```

### Codex / coding-agent

Codex、Claude Code 或其他 coding-agent 环境也可以使用。需要注意的是，本地 agent 运行完整长流程通常更消耗 token；如果主要目标是少消耗 token 和快速得到卡通图，优先用 ChatGPT 网页版。

- 生图时优先使用 `imagegen` skill。
- `imagegen` 不可用或能力不足时，再使用 ChatGPT Images 2.0 API 或其他用户批准的生图 API。
- Codex 更适合整理文件、检查 README、更新 skill、打包 zip、合成 PDF 和提交 GitHub。
- PDF 合成脚本默认使用 `1080x1920` 的 9:16 手机竖屏画幅；组合 PDF 使用 `scripts/assemble_storyboard_report_pdf.py`，可通过 image/report page-size 参数修改。

## 默认设置

- **画幅**：默认 `9:16` 手机竖屏，可改为 `16:9`、`4:5`、`1:1`、`3:4` 或自定义比例。
- **语言**：默认中文对白、旁白、标题和标签；可改为英文、中英双语或其他语言。
- **风格**：默认课堂板书漫画，也可选扁平教育信息图、手绘白板草图、轻日漫科研课堂、柔和 3D 黏土/立体卡通。
- **人物设定**：默认课堂场景，一个老师/讲解者加 2-3 个学生或研究者听众。
- **生成批次**：默认每次生成 2-4 张，避免单页信息过载；复杂章节分多批继续。
- **图片数量**：多图不是越多越好。每张图必须有独立教学增量，重复的开场、动机、转场或总结页会被剪掉。
- **页面结构**：推荐“页码/标题 -> 一句话问题或结论 -> 中心图式/场景 -> 2-5 个支撑卡片 -> 底部 takeaway/证据说明”。
- **构图模式**：第一次回答会说明默认构图，并提示可切换为流程分镜、左右对比、答辩问答卡、极简概念卡或参考图引导。

## 适合谁用

- 需要快速讲清一篇论文的研究生、科研人员和工程研究团队。
- 要准备组会、课程展示、论文复现汇报或答辩材料的用户。
- 想把抽象算法、实验和局限性转成直观视觉材料的讲解者。
- 需要从论文中挖掘后续研究想法的人。

## License

MIT-0
