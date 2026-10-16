# Academic PPT Workflow

[简体中文](README.md) | English

**Make the content clear first, then recreate the design as an editable presentation.**

A Codex skill for academic and teaching presentations. It starts with source analysis, an outline, and logic checks, uses image generation to design slides, and then faithfully reconstructs them as editable presentations. It supports lessons, research introductions, and progress reports, as well as direct reconstruction from existing images, PDFs, or slide decks.

| Ink-wash classroom · Vocal basics | Artistic textures · Image style transfer |
| :---: | :---: |
| [![Vocal basics lesson cover](examples/05-vocal-basics/cover.png)](examples/05-vocal-basics/README.en.md) | [![Image style transfer lesson cover](examples/04-style-transfer-with-reference/cover.png)](examples/04-style-transfer-with-reference/README.en.md) |

*Both covers were exported from the PDFs accompanying the editable presentations. Open an example to see its prompts and the PDFs from both production stages.*

[Skill instructions](skills/en/academic-ppt-workflow/SKILL.md) · [Five complete examples](#examples-and-downloads) · [17 style references](style-references/README.en.md) · [MIT License](LICENSE)

## Core principles

- **Clear logic:** Check the logic between sections, within each section, and within each slide. Record the narrative structure and transitions in the outline so that the content is coherent and flows naturally.
- **Strong visuals:** Use the complete outline to guide an image generation model, turning the content and its relationships into clear, visually appealing slide designs.
- **Editable output:** Analyze the slide images to distinguish elements that can be reconstructed as vectors from complex artwork that is difficult to recreate. Rebuild or retain each as appropriate, then deliver an editable PPTX and a PDF preview.

## Nine-step workflow

| Stage | Main tasks |
| --- | --- |
| 1. Analyze requirements and materials | Define the audience, purpose, content, aspect ratio, and delivery scope |
| 2. Research as needed | Fill only necessary information gaps and record factual sources |
| 3. Write a complete outline | Plan sections, slide text, graphical relationships, and speaker notes |
| 4. Review the outline | Check coverage and narrative logic at all three levels |
| 5. Choose a style | Usually generate A/B/C options; supply reference images as actual generation inputs |
| 6. Create thumbnails for the full deck | Check structure, slide roles, and visual rhythm across all slides |
| 7. Produce the image-based version | Generate individual slides, review, assemble, and confirm |
| 8. Reconstruct an editable version | Decompose the image baseline into objects and complete the first full review and corrections |
| 9. Inspect every slide | Conduct a second full review, fix issues, and verify the final deliverables |

By default, request confirmation once after the complete image-based version passes its internal checks and before editable reconstruction begins. Existing authorization for direct reconstruction or fully automatic completion remains valid. Editable reconstruction includes the subsequent detailed review; it does not introduce another routine approval step. See the [skill instructions](skills/en/academic-ppt-workflow/SKILL.md) for the full rules.

## Installation and use

The skill is available in two independent language directories. Each contains a complete `SKILL.md`, `references/`, `agents/openai.yaml`, and license, with internal links only to documents in that language.

| Version | Installation source directory | Skill instructions |
| --- | --- | --- |
| English | `skills/en/academic-ppt-workflow/` | [English instructions](skills/en/academic-ppt-workflow/SKILL.md) |
| Chinese | `skills/zh-CN/academic-ppt-workflow/` | [Chinese instructions](skills/zh-CN/academic-ppt-workflow/SKILL.md) |

Both versions provide the same workflow and capabilities; only the instructions and interface descriptions differ in language. The presentation language still follows the task requirements. **Install just one version.** Both use the invocation name `$academic-ppt-workflow`. Do not install both versions or copy the entire repository `skills/` directory into a skill discovery directory, as that would introduce duplicate skill names.

The official documentation lists `~/.agents/skills/` for user-level skills and `.agents/skills/` for repository-level skills. You can also use `$skill-installer` to install one of the language-specific directories listed above. See the [OpenAI skills documentation](https://learn.chatgpt.com/docs/build-skills). If your environment uses a different skill directory, follow its actual configuration.

Run one of the following commands from the repository root (Bash). If a skill with the same name is already installed, first move the old `academic-ppt-workflow` folder outside the skill discovery directory and keep it as a backup. Then copy the new version, so that merging directories does not leave old files behind. Use the same whole-folder replacement when switching languages.

**Install the English version:**

```bash
mkdir -p "$HOME/.agents/skills"
cp -R skills/en/academic-ppt-workflow "$HOME/.agents/skills/"
```

**Or install the Chinese version:**

```bash
mkdir -p "$HOME/.agents/skills"
cp -R skills/zh-CN/academic-ppt-workflow "$HOME/.agents/skills/"
```

Keep the entire selected `academic-ppt-workflow/` folder. No file renaming or manual entry-point switching is needed. If the new skill is not discovered, restart the client and try again. Repository documentation, including READMEs and example descriptions, retains Chinese/English navigation; example PDFs and style images remain in their original language.

Example prompt for a new presentation:

```text
Use $academic-ppt-workflow to create a lesson on image style transfer
for undergraduates who have only studied basic image processing.
First plan the content and teaching sequence; research as needed.
Use 16:9 unless otherwise specified.
Use my uploaded style reference. Deliver the image-based version for
review first, then reconstruct the editable version after confirmation.
The final deliverables should include both PPT versions, a PDF of the
editable version, and speaker notes.
```

Example prompt for direct reconstruction:

```text
I have an image-based presentation. Please use $academic-ppt-workflow
to reconstruct it as an editable presentation.
```

The full workflow requires image generation, file access, presentation building, and rendering capabilities. Search is also needed when there are information gaps. The workflow is not tied to a particular library; if a required capability is unavailable, clearly state which stages remain incomplete.

## Examples and downloads

Five examples cover **120 slides**, with **10 PDFs** showing two production stages, plus user prompts and style references.

| Example | Slides | Style reference | Image-based review PDF | Editable reconstruction preview PDF | Prompts |
| --- | ---: | --- | --- | --- | --- |
| [1 · Jailbreak attacks lesson](examples/01-jailbreak-teaching/README.en.md) | 22 | S0 | [PDF](examples/01-jailbreak-teaching/image-review.pdf) | [PDF](examples/01-jailbreak-teaching/editable.pdf) | [Read](examples/01-jailbreak-teaching/prompt.en.md) |
| [2 · Work progress report](examples/02-work-progress/README.en.md) | 18 | S10 | [PDF](examples/02-work-progress/image-review.pdf) | [PDF](examples/02-work-progress/editable.pdf) | [Read](examples/02-work-progress/prompt.en.md) |
| [3 · Style transfer, without a reference](examples/03-style-transfer-no-reference/README.en.md) | 32 | None | [PDF](examples/03-style-transfer-no-reference/image-review.pdf) | [PDF](examples/03-style-transfer-no-reference/editable.pdf) | [Read](examples/03-style-transfer-no-reference/prompt.en.md) |
| [4 · Style transfer, with a reference](examples/04-style-transfer-with-reference/README.en.md) | 30 | S9 | [PDF](examples/04-style-transfer-with-reference/image-review.pdf) | [PDF](examples/04-style-transfer-with-reference/editable.pdf) | [Read](examples/04-style-transfer-with-reference/prompt.en.md) |
| [5 · Vocal basics lesson](examples/05-vocal-basics/README.en.md) | 18 | S1 | [PDF](examples/05-vocal-basics/image-review.pdf) | [PDF](examples/05-vocal-basics/editable.pdf) | [Read](examples/05-vocal-basics/prompt.en.md) |

This package showcases the examples and does not include PPTX source files or font installation packages. An “editable reconstruction preview PDF” is a display copy exported from the editable presentation; the PDF itself does not provide editable PowerPoint objects.

## Repository structure

```text
academic-ppt-workflow/
├── README.md / README.en.md
├── LICENSE / LICENSE-SCOPE.md / LICENSE-SCOPE.en.md / LICENSES/
├── skills/
│   ├── zh-CN/academic-ppt-workflow/  # Standalone Chinese skill
│   └── en/academic-ppt-workflow/     # Standalone English skill
├── examples/                     # Five sets of PDFs, prompts, and two covers
└── style-references/             # Original S0–S16 style reference images
```

The reference images are stored in one gallery and linked from the relevant examples. The skill and examples are separate; install only the `academic-ppt-workflow/` folder under your chosen language. Repository documentation has English companions alongside the Chinese files; the two installable skills keep their languages separate.

## Publishing and licensing

Extract the archive and use this directory's contents as the root of a GitHub repository, then commit them with Git or GitHub Desktop. The skill and content owned by this repository's contributors use the [MIT License](LICENSE), which requires retaining the copyright notice and license text. Third-party materials are covered by the [license scope statement](LICENSE-SCOPE.en.md).
