# Work progress report: user prompts

[简体中文](prompt.md) | English

These are English translations of anonymized historical creation and revision requests. The task structure and design requirements are preserved; paper names, submission and acceptance details, review venues, and specific dates have been generalized.

## Initial creation request

```text
We are preparing for a regular group meeting, and I need a work progress presentation. Here is what I plan to cover:

- We recently received updates on two submitted papers:

  - Paper 1 (material: 论文1.pdf, “Paper 1”): it has gone through several submissions and revisions but has not been accepted.
  - Paper 2 (material: 论文2.pdf, “Paper 2”): through teamwork, it was written in a relatively short period and accepted.

  I have some reflections on this. Why has Paper 1 struggled to get accepted despite repeated revisions, while Paper 2 succeeded after a short development cycle? I think Paper 2 benefited from good timing—the recent research interest in agents—and from ideas that others may not have noticed. For example, the paper's execution hallucination (“covert execution”) feels novel. Paper 1, on the other hand, concerns text jailbreaks, which were no longer as popular at the time, and its methodological innovation is more about combining existing techniques.

  I would like to summarize what we learned from submitting these two papers at the group meeting.

- I created a PPT skill, [$academic-ppt-workflow](../../skills/en/academic-ppt-workflow/SKILL.md), to make presentation production a repeatable workflow. This is mainly for future job applications, conference talks, and routine reports. I think I could first introduce the skill's core design principles:

  - Coherent logic: a dedicated outlining step and three levels of logic checks ensure that the presentation makes sense between sections, within sections, and within slides.
  - Appealing visual design: an image generation model designs the slides from the outline rather than using code to lay out each page. A high-fidelity editable reconstruction process then converts the image-based deck into a regular presentation.

  Then briefly introduce the skill's nine steps and acceptance criteria. At the end, leave a slide showing three presentations created with the skill. The examples are in the attached folder, 2_SKILL_结果 (“skill results”). Each subfolder contains the final PDF and a “参考图” (“reference images”) folder with the style reference used at the time. The second example has no reference folder because no reference image was used. We can simply use each presentation's first slide alongside its style reference. I will open the files during the talk, so this slide mainly serves as a pointer.

That is what I plan to cover in this group meeting. Please first organize the content, then use [$academic-ppt-workflow](../../skills/en/academic-ppt-workflow/SKILL.md) to create the work progress report. Use the attached S10.png as the style reference.
```

## Revisions to the image-based version

**Add next week's work**

```text
The image-based presentation looks good. I forgot to add a final slide about next week's work:

- Submit Paper 1 to another journal.
- Prepare Paper 2's camera-ready version, poster, and presentation.
- Complete academic conference reviews.

Please work out how to add this.
```

**Adjust the section structure**

```text
I think slides 15 and 16 could form a separate concluding section.
```

## Image-based version approval and editable reconstruction request

```text
I have an image-based presentation. Please use $academic-ppt-workflow to reconstruct it as an editable presentation.
```

## Original inputs

The submitted manuscripts are not included in the showcase package; their filenames use anonymous labels. Slide 14 retains screenshots showing examples produced with the skill.
