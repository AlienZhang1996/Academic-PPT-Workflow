# Introduction to style transfer, with a reference: user prompts

[简体中文](prompt.md) | English

These are English translations of the historical creation and revision requests, preserving their original meaning. Personal absolute paths and client attachment wrappers have been cleaned up.

## Initial creation request

```text
My supervisor is teaching a course on image style transfer this semester and asked me to make a lesson presentation. The audience is undergraduates, most of whom have only studied basic image processing and know little about style transfer. Please first consider how to organize the lesson so that it is easy for them to understand. You may also use tools such as deep research to identify the specific concepts to cover. Then use $academic-ppt-workflow to create this lesson on image style transfer. Use my uploaded image as a style reference.
```

## Revisions to the image-based version

```text
I reviewed the image-based presentation. The overall content and logic are good, but I noticed these issues:

- Slide 25: the fonts and layouts in the three columns appear inconsistent. Some text is bold and some is not; some is left-aligned and some is centered.
- Slide 23: the areas marked by boxes in the house image on the left do not seem to match the contents of the colored boxes on the right. Are the two sides meant to correspond? The right side seems to show different evaluation perspectives, but the purple “computational cost” box does not appear related to the house image. This diagram may need to be reconsidered.
- Slide 14: is the calculation logic clear and accurate? Please check it again.
- Slide 8: the “edge response grid” seems to contain both square and rectangular cells. Should this be improved?
- Slide 5: in the “style” section on the right, the crops marked with different colored boxes should correspond to one another. The contents of the large image and the small boxes do not seem to match.

These are the issues I found. Could you improve them?
```

## Image-based version approval and editable reconstruction request

```text
I have an image-based presentation. Please use $academic-ppt-workflow to reconstruct it as an editable presentation.
```

## Original inputs

The user uploaded S9 as the visual reference. The original image is included.
