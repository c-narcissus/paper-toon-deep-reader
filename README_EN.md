# Paper Deep Reading Teaching Explainer

**One line: turn a paper into a teachable, defensible, phone-readable cartoon deep-reading PDF.**

[中文 README](README.md)

This skill is built for seminars, classes, reproduction prep, and defense rehearsal. It first creates a source-grounded Markdown deep reading report from a paper PDF and/or LaTeX source, then turns the report into staged cartoon explainers for background, method, experiments, limitations, and future directions, and finally assembles approved cartoon pages and the Markdown report into one PDF, with cartoon pages first and the report after them. It defaults to phone portrait, Chinese dialogue, and consistent storyboard style, while allowing custom aspect ratio, language, and cartoon style.

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
- Skill package: use the latest zip file in the repository root.

## What It Does

- **Reads first**: produces an evidence-grounded report covering motivation, problem setting, assumptions, method, experiments, limitations, and research opportunities.
- **Explains next**: prepares 30-second, 3-minute, and 10-minute explanations, plus formula, figure, table, experiment, misconception, and defense scripts.
- **Draws in stages**: generates a continuous cartoon comic made of multiple separate pages for background, method, experiments, limitations, future directions, and presentation packaging.
- **Not a single image**: the default output is not one large poster or merged long image; a single image is only an explicitly requested compact overview.
- **Small batches**: one page teaches one point, and complex sections can be generated across multiple replies with only a few pages each time.
- **Assembles the PDF**: places approved cartoon pages first, renders the Markdown deep-reading report after them, and combines both into one shareable handout.
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
| Step 7 | Final PDF assembly from approved cartoon pages plus the Markdown report, with cartoons first |

## Usage

The skill works in both ChatGPT Web/App and Codex / coding-agent environments. If you want to save tokens, prefer completing the full reading, image-generation, and PDF workflow in a ChatGPT Web Project; Codex is better for local file organization, script execution, packaging, and GitHub publishing.

### ChatGPT Web/App

1. Create or open a Project in ChatGPT Web/App.
2. Add the repository skill zip to Project `Sources` first.
3. After the skill is present in `Sources`, upload the paper PDF and/or LaTeX source.
4. Ask for the full text-only deep reading report first. Do not generate images in the first step.
5. Generate cartoon pages stage by stage in small batches. When the next step is image generation, explicitly ask for `生成多张连续的卡通图`; for complex sections, continue with `继续生成下一批多张连续的卡通图`.
6. After approving all images, run the final PDF assembly step: cartoon pages first, Markdown deep-reading report after them.

Copy-ready prompts:

```text
严格遵守skill里的步骤：精读这篇论文，先生成完整文字报告，不要生成图片。
```

```text
严格遵守skill里的步骤：根据状态，执行第1步：生成多张连续的卡通图，内容是背景、旧方法缺陷、论文问题和灵感来源。
```

```text
严格遵守skill里的步骤：根据状态，执行最后一步：把所有已经生成并确认的卡通图和Markdown精读报告合成一个PDF，卡通图在前面。
```

If you do not know what to ask next:

```text
严格遵守skill里的步骤：根据状态，告知下一步应该问什么。
```

### Codex / Coding Agents

Codex, Claude Code, and other coding-agent environments can use the skill. Full long-running local-agent workflows usually consume more tokens; if the main goal is to save tokens and quickly get cartoon pages, prefer ChatGPT Web/App.

- Prefer the `imagegen` skill for cartoon image generation.
- If `imagegen` is unavailable or insufficient, fall back to ChatGPT Images 2.0 API or another user-approved image-generation API.
- Codex is useful for local file organization, README checks, skill updates, zip packaging, PDF assembly, and GitHub publishing.
- The combined PDF script defaults to `1080x1920` for 9:16 phone portrait. Use `scripts/assemble_storyboard_report_pdf.py`; image/report page-size parameters can override the defaults.

## Defaults

- **Aspect ratio**: default `9:16` phone portrait; users can switch to `16:9`, `4:5`, `1:1`, `3:4`, or a custom ratio.
- **Language**: default Chinese dialogue, narrator captions, titles, and labels; users can switch to English, bilingual Chinese-English, or another language.
- **Style**: default classroom blackboard cartoon; alternatives include flat educational infographic, hand-drawn whiteboard sketch, light anime research classroom, and soft 3D clay/cartoon.
- **Characters**: default classroom scene with one teacher/narrator and 2-3 student or researcher listeners.
- **Batch size**: default 2-4 images per generation reply to avoid overloaded pages; complex sections continue in later batches.
- **Image count**: more images is not automatically better. Each image needs a distinct teaching contribution, and redundant opening, motivation, transition, or recap pages are pruned.

## Who It Is For

- Graduate students, researchers, and research engineers who need to explain papers clearly.
- Users preparing seminars, course presentations, reproduction reports, or defense materials.
- Teachers and presenters who want to turn dense algorithms and experiments into visual narratives.
- Researchers who want to extract future research ideas from papers.

## License

MIT-0
