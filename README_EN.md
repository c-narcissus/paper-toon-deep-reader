# Paper Toon Deep Reader

`paper-toon-deep-reader` first generates a traceable deep-reading report from a paper, then creates multiple continuous cartoon-comic pages in stages, and finally assembles the approved cartoon pages and Markdown report into one PDF. Special thanks to Liu Xinyang from Bristol for providing the SemiDFL example materials.

[中文 README](README.md)

Thumbnail preview of the 12 cartoon deep-reading pages:

| S1 | S2 | S3 | S4 |
| --- | --- | --- | --- |
| <img src="example/S1.png" width="160" alt="SemiDFL cartoon report page S1" /> | <img src="example/S2.png" width="160" alt="SemiDFL cartoon report page S2" /> | <img src="example/S3.png" width="160" alt="SemiDFL cartoon report page S3" /> | <img src="example/S4.png" width="160" alt="SemiDFL cartoon report page S4" /> |

| S5 | S6 | S7 | S8 |
| --- | --- | --- | --- |
| <img src="example/S5.png" width="160" alt="SemiDFL cartoon report page S5" /> | <img src="example/S6.png" width="160" alt="SemiDFL cartoon report page S6" /> | <img src="example/S7.png" width="160" alt="SemiDFL cartoon report page S7" /> | <img src="example/S8.png" width="160" alt="SemiDFL cartoon report page S8" /> |

| S9 | S10 | S11 | S12 |
| --- | --- | --- | --- |
| <img src="example/S9.png" width="160" alt="SemiDFL cartoon report page S9" /> | <img src="example/S10.png" width="160" alt="SemiDFL cartoon report page S10" /> | <img src="example/S11.png" width="160" alt="SemiDFL cartoon report page S11" /> | <img src="example/S12.png" width="160" alt="SemiDFL cartoon report page S12" /> |

## Key Rules

- **Strict stage gates**: report, cartoon images, and PDF assembly are separate stages. Even if the user asks for everything at once, the workflow must stop at the next valid gate and wait for confirmation.
- **Separate text and image turns**: do not generate direct images in the same reply that writes a report, prompt handoff, checklist, or long status.
- **Multiple continuous comic pages**: the default output is a sequence of separate cartoon pages, not one SVG, poster, long image, or merged collage.
- **ChatGPT Web uses Create image**: every direct cartoon batch in ChatGPT Web/App must use Create image.
- **Codex uses imagegen first**: in Codex / coding-agent environments, use `imagegen` first; if unavailable, use ChatGPT Images 2.0 API or another user-approved image API.
- **No SVG substitutes**: SVG, Mermaid, HTML/CSS, canvas, and hand-drawn vector diagrams are not valid cartoon-image outputs for this skill.
- **Small batches**: normally generate 2-4 pages per batch and continue complex sections across multiple user-approved turns.
- **One teaching point per page**: avoid stuffing multiple formulas, modules, tables, and conclusions into one page.
- **Source-grounded visuals**: prompts and generated images must be checked against the original paper and the authoritative report.
- **PDF last**: assemble the final PDF only after all raster cartoon pages are generated and approved.

## Example Files

The repository includes a SemiDFL example showing both the ChatGPT Web interaction and the final outputs:

- `example/S1.png` to `example/S12.png`: 12 generated cartoon pages from the deep-reading report, showing how the paper background, method, experiments, limitations, and summary can be split into a continuous comic sequence.
- [`example/semiDFL.pdf`](example/semiDFL.pdf): the original paper PDF used in the example, provided so users can directly upload it to a ChatGPT Project or place it in a Codex project directory for testing.
- [`example/SemiDFL精读卡通图报告.mhtml`](example/SemiDFL%E7%B2%BE%E8%AF%BB%E5%8D%A1%E9%80%9A%E5%9B%BE%E6%8A%A5%E5%91%8A.mhtml): exported ChatGPT Web conversation example. It records the interaction flow from skill configuration and deep-reading report generation to staged cartoon-image generation and PDF preparation.
- [`example/semiDFL_codex_v.mp4`](example/semiDFL_codex_v.mp4): a partial clip of running this skill in Codex, useful as a reference for local Codex execution.

The current version defaults to 9:16 phone portrait, while 16:9, 4:5, 1:1, 3:4, and custom ratios remain available.

## Workflow

| Stage | Output |
| --- | --- |
| Step 0 | Full text report, teaching prep, current status, next-step suggestions |
| Step 1 | Background, old-method defects, paper problem, inspiration |
| Step 2 | Algorithm overview, module IO, symbols, dimensions, training, inference |
| Step 3 | Datasets, metrics, baselines, main results, ablations, exceptions, reproduction risks |
| Step 4 | Limitations, reviewer questions, defense framing |
| Step 5 | Future directions, hidden assumptions, innovation map |
| Step 6 | Cover, final summary, Q&A backup pages |
| Step 7 | Final PDF from approved cartoon pages plus the Markdown report, with cartoons first |

## Recommended Use

If your token budget is sufficient, Codex is recommended.

ChatGPT Web/App and Codex / coding-agent environments follow nearly the same workflow: configure the skill and paper files, generate the text report first, generate multiple continuous cartoon pages in small batches, review each batch, then assemble the final PDF after approval.

If the goal is to save tokens and complete the full visual workflow quickly, ChatGPT Web/App is usually the better environment. Codex is better for local file organization, script execution, README editing, skill updates, zip packaging, PDF assembly, and GitHub publishing.

## ChatGPT Web/App Usage

1. Create or open a ChatGPT Project.
2. Add `paper-toon-deep-reader-v2.0.0.zip` to Project `Sources` first.
3. Add the paper PDF / LaTeX source to `Sources`, for example `semiDFL.pdf`.
4. Send the first-use prompt so ChatGPT configures the skill for the current conversation.
5. The first execution should only produce the text report and status. It should not generate images or assemble a PDF.
6. When the status reaches the cartoon stage, use Create image and explicitly ask for multiple continuous cartoon pages.
7. Review each generated batch before continuing. Assemble the PDF only after all pages are approved.

First-use prompt example:

```text
请严格按照paper-toon-deep-reader-v2.0.0.zip里skill 的步骤对semiDFL.pdf进行分析
```

## Codex Usage

The Codex environment can use the same workflow. Put `paper-toon-deep-reader-v2.0.0.zip` and the paper file in the same project directory, or specify the file path clearly in the prompt.

Codex first-use prompt example:

```text
请为一个 agent 配置 paper-toon-deep-reader-v2.0.0.zip 里的 skill，然后严格按照里面的步骤对 semiDFL.pdf 进行分析。
```

## Defaults

- **Aspect ratio**: default `9:16` phone portrait; users can switch to `16:9`, `4:5`, `1:1`, `3:4`, or custom.
- **Language**: default Chinese dialogue, captions, titles, and labels; users can switch to English, bilingual Chinese-English, or another language.
- **Style**: default classroom blackboard cartoon; alternatives include flat educational infographic, hand-drawn whiteboard sketch, light anime research classroom, and soft 3D clay/cartoon.
- **Characters**: default classroom scene with one teacher/narrator and 2-3 student or researcher listeners.
- **Batch size**: default 2-4 pages per generation reply.
- **Page structure**: page marker/title -> framing question or claim -> central diagram/scene -> 2-5 supporting callouts -> bottom takeaway/evidence note.
- **Composition mode**: default single focal visual argument; users can switch to process strip, split-screen comparison, defense Q&A card, minimal concept card, or reference-guided layout.

## Interaction State

Every text reply should include:

- Current stage and produced artifacts.
- Runtime Environment.
- Image Generation Route.
- PDF Assembly Route.
- Storyboard Aspect Ratio.
- Storyboard Text Language.
- Storyboard Page Composition.
- Suggested next user prompt.

This helps prevent state repetition, skipped stages, SVG fallback, one-shot PDF generation, and mixing text report generation with cartoon-image generation.

## License

MIT-0
