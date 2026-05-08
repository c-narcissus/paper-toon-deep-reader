# Paper Deep Reading Teaching Explainer

**One line: turn a paper into a teachable, defensible, phone-readable cartoon deep-reading PDF.**

[中文 README](README.md)

## 100-Word Summary

This skill is built for seminars, classes, reproduction prep, and defense rehearsal. It first creates a source-grounded deep reading report from a paper PDF and/or LaTeX source, then turns the report into staged cartoon explainers for background, method, experiments, limitations, and future directions, and finally assembles approved images into a PDF. It defaults to phone portrait, Chinese dialogue, and consistent storyboard style, while allowing custom aspect ratio, language, and cartoon style.

## Demo

The example below comes from a complete `SemiDFL` run: a deep reading report first, then 18 staged cartoon explainer pages, then one combined PDF. This sample is an earlier 16:9 landscape run; the current version defaults to 9:16 phone portrait, while 16:9 remains available.

<div align="center">
  <img src="assets/demo/storyboard-pages-01-18-contact-sheet.jpg" width="680" alt="18-page cartoon storyboard overview" />
</div>

<p align="center">
  <img src="assets/demo/page-01.png" width="22%" alt="Cartoon explainer page 1: background and motivation" />
  <img src="assets/demo/page-07.png" width="22%" alt="Cartoon explainer page 7: algorithm round workflow" />
  <img src="assets/demo/page-13.png" width="22%" alt="Cartoon explainer page 13: experiment setup" />
  <img src="assets/demo/page-18.png" width="22%" alt="Cartoon explainer page 18: final summary" />
</p>

- Example PDF: [SemiDFL_cartoon_explainer_pages_1-18.pdf](example/SemiDFL_cartoon_explainer_pages_1-18.pdf)
- Exported ChatGPT project example: [SemiDFL deep reading report .mhtml](example/SemiDFL%20deep%20reading%20report%20.mhtml)
- Skill package: [paper-deep-reading-teaching-explainer-v10.1.12-clawhub.zip](paper-deep-reading-teaching-explainer-v10.1.12-clawhub.zip)
- ClawHub page: [paper-deep-reading-teaching-explainer](https://clawhub.ai/c-narcissus/paper-deep-reading-teaching-explainer)

## What It Does

- **Reads first**: produces an evidence-grounded report covering motivation, problem setting, assumptions, method, experiments, limitations, and research opportunities.
- **Explains next**: prepares 30-second, 3-minute, and 10-minute explanations, plus formula, figure, table, experiment, misconception, and defense scripts.
- **Draws in stages**: generates continuous cartoon pages for background, method, experiments, limitations, future directions, and presentation packaging.
- **Assembles the PDF**: combines approved images into one shareable handout.
- **Checks hallucinations**: prompts and generated images are checked against the original paper and the prior authoritative report.
- **Keeps continuity**: character design, style, aspect ratio, dialogue language, symbols, page numbering, camera logic, and data-flow direction carry across later batches.

## Main Steps

| Stage | Output |
| --- | --- |
| Step 0 | Full text report, teaching prep, current status, next-step prompts |
| Step 1 | Background, old-method defects, paper problem, inspiration |
| Step 2 | Algorithm overview, module IO, symbols, dimensions, training, inference |
| Step 3 | Datasets, metrics, baselines, main results, ablations, exceptions, reproduction risks |
| Step 4 | Limitations, reviewer questions, defense framing |
| Step 5 | Future directions, hidden assumptions, innovation map |
| Step 6 | Cover, final summary, Q&A backup pages |
| Step 7 | Final PDF assembly from approved cartoon pages |

## Recommended Use

### ChatGPT Web/App

The recommended environment is a ChatGPT Web/App Project. The cartoon stage works best with ChatGPT's **Create image** capability.

1. Open the [ClawHub page](https://clawhub.ai/c-narcissus/paper-deep-reading-teaching-explainer) and download the skill zip.
2. Create or open a Project in ChatGPT Web/App.
3. Add the skill to Project `Sources` first. Uploading the skill zip is recommended.
4. After the skill is present in `Sources`, upload the paper PDF and/or LaTeX source.
5. Ask for the full text-only deep reading report first. Do not generate images in the first step.
6. Generate cartoon pages stage by stage. When the next step is image generation, explicitly ask for `生成多张连续的卡通图`.
7. After approving all images, run the final PDF assembly step.

Copy-ready prompts:

```text
使用这个skill，精读这篇论文，先生成完整文字报告，不要生成图片。
```

```text
使用这个skill，根据状态，执行第1步：生成多张连续的卡通图，内容是背景、旧方法缺陷、论文问题和灵感来源。
```

```text
使用这个skill，根据状态，执行最后一步：把所有已经生成并确认的图合成一个PDF。
```

If you do not know what to ask next:

```text
使用这个skill，根据状态，告知下一步应该问什么。
```

### Codex / Coding Agents

Codex, Claude Code, and other coding-agent environments can use the skill, but the full cartoon-generation workflow is usually smoother in ChatGPT Web/App.

- Prefer the `imagegen` skill for cartoon image generation.
- If `imagegen` is unavailable or insufficient, fall back to ChatGPT Images 2.0 API or another user-approved image-generation API.
- Codex is useful for local file organization, README checks, skill updates, zip packaging, PDF assembly, and GitHub publishing.
- The PDF assembly script defaults to `1080x1920` for 9:16 phone portrait and can be changed with `--page-width` / `--page-height`.

## Defaults

- **Aspect ratio**: default `9:16` phone portrait; users can switch to `16:9`, `4:5`, `1:1`, `3:4`, or a custom ratio.
- **Language**: default Chinese dialogue, narrator captions, titles, and labels; users can switch to English, bilingual Chinese-English, or another language.
- **Style**: default classroom blackboard cartoon; alternatives include flat educational infographic, hand-drawn whiteboard sketch, light anime research classroom, and soft 3D clay/cartoon.
- **Characters**: default classroom scene with one teacher/narrator and 2-3 student or researcher listeners.
- **Image count**: more images is not automatically better. Each image needs a distinct teaching contribution, and redundant opening, motivation, transition, or recap pages are pruned.

## Who It Is For

- Graduate students, researchers, and research engineers who need to explain papers clearly.
- Users preparing seminars, course presentations, reproduction reports, or defense materials.
- Teachers and presenters who want to turn dense algorithms and experiments into visual narratives.
- Researchers who want to extract future research ideas from papers.

## OpenClaw / ClawHub CLI

```bash
openclaw skills install paper-deep-reading-teaching-explainer
```

## License

MIT-0
