# Visual Production Methods

Read “Thumbnails and style” in Steps 5–6, “Individual slide production” in Step 7, and “Editable reconstruction” in Step 8. Both Step 8's initial review and Step 9's second review must read the entire [Reconstruction and fidelity acceptance](quality-checks.md#reconstruction-and-fidelity-acceptance) section and perform applicable checks. For real-world incident cases or other authentic images, read “Authentic images and placeholders” during planning rather than waiting until assets are selected. The templates below are natural-language inputs; actual calls must follow the current tool's parameters and limits. The [main workflow](../SKILL.md) governs progression, authorization, and artifact roles.

## Thumbnails and style

### Grid and capacity

Default to `c=4` columns and `r=3` rows; replace these when the user specifies otherwise. Capacity is `k=c×r`. The main candidate grid uses the first `min(k,N)` slides, and the complete overview is batched every k slides in display order. Derive batch counts, cell numbers, and empty cells from the current parameters rather than hard-coding another capacity. Use row-major order. Empty cells retain the same size without invented slides.

The individual slide area w,h follows the requested aspect ratio. Record outer margins mx,my, gaps gx,gy, and the height t of the page-number strip outside each row's slides. Set t=0 when no strip is used:

```text
W = 2mx + c×w + (c−1)×gx
H = 2my + r×(h+t) + (r−1)×gy
```

All slide frames have equal width and height. Page numbers and whitespace do not count toward the individual slide ratio. The full canvas is not fixed at 16:9 or 64:27. If the tool limits canvas size, fit the entire grid proportionally with whitespace rather than compressing a row or cropping content. Prompts cannot guarantee pixel precision. If grid cells distort, generate smaller batches/independent previews and assemble them deterministically. Split batch images only when their slides are complete and boundaries clear. Previews still use summaries and do not replace final individual slides.

### Candidates and shared styles

All candidates use the same content, slide order, and reference constraints; variation is limited to color, composition, typographic character, and graphic language. If the first batch lacks important later charts or complex slides, choose the same additional representative slides to test each candidate and label them supplemental samples. Do not change the complete overview's order or let candidates choose different content.

Before actually calling the image generation tool, define each candidate's design direction, such as information organization, main visual placement, or diagram approach. When comparing them, explain which differences help the current content. Consider the reference's hierarchy, visual focus, semantic graphics, and whitespace organization rather than extracting only a few colors. Not every decoration must differ, but changing only the background color, corner radius, or title bar of one layout does not constitute multiple design options. Choose diagrams to suit content; do not require icons, gradients, or complex decoration on every slide.

Presentation summaries retain the exact title, slide role, main points, necessary qualifications, graphical relationships, and applicable authentic-asset placeholders. Secondary explanations may be summarized; do not use fake fine print as filler. If a summary is too dense, shorten the summary first rather than deleting content from the complete outline.

The style record establishes actually available Chinese/Latin and mathematical fonts, colors, grid, and whitespace. By slide role, fix title font/size/weight/position/baseline, section numbers and box sizes, dividers, and page numbers. A prompt alone does not verify a bitmap's font. For long titles, first adjust width or use controlled line breaks rather than silently shrinking individual titles. Return to the master record if wording must change.

```text
Create style-option {option_name} thumbnails: {c} columns × {r} rows, {k} cells, in row-major order.
Each slide area is {w}×{h}, aspect ratio {ratio}; total canvas {W}×{H}, margins {mx,my}, gaps {gx,gy}, page-number strip {t}.
Use {actually supplied reference images and purposes}; style direction: {direction}. Keep all frames equal in size and do not vary row heights.
Cell content: {cell, slide_id, exact title, slide role, summary, necessary qualifications, graphical relationships}.
Asset placeholders: {asset IDs, regions/ratios, labels or pending status for applicable slides}. Preserve their layout; do not generate fake news images or text.
Empty cells {list} retain their positions without fictitious slides. Prioritize titles and structure; add no facts or pseudo-text.
```

## Individual slide production

After the complete thumbnail set passes review, call the image generation tool to independently generate slides from the complete per-slide records. Supply the inspected, selected thumbnails as actual visual inputs, identifying the corresponding cells and their reference purpose. If necessary, extract the relevant cell under the tool's rules. Thumbnails guide design, not body text; do not recover content from their blurry text or enlarge them for delivery. Choose output resolution according to the target display size and body/label readability, and check actual aspect ratio and content boundaries. Except for explicit exceptions in the main workflow, every slide needs its own generated design output. Generating only a cover or decorative assets and filling the remaining deck with a fixed code template is insufficient.

Choose the method in advance based on content, without waiting for a failure. Hybrid approaches still preserve image-generated page design:

- The generation tool handles overall composition, visual hierarchy, semantic diagrams, and suitable graphics. Do not first specify a fixed-coordinate template and then present its reduced screenshot as design exploration.
- For dense Chinese text, formulas, precise data charts, or shared titles, directly use “generated slide design + deterministic text/chart/asset compositing.” Define exact regions in advance and composite within the generated design's positions, scale, and hierarchy. Do not retain only a generated decoration while rearranging the main content into a simplified template. Save the generated base, compositing regions, and final image. Existing constructed objects may be reused, but easier later reconstruction must not come at the expense of current design quality.
- Draw charts from source data when it exists. Preserve original scientific figures and evidentiary assets, their sources, and necessary annotations; do not redraw them with a model in ways that change data, curves, or real signals. Without source data, retain images rather than guessing data for reconstruction.

Hybrid methods follow the tool's rules. Remove replaced text and check covering panels, default shadows, and occlusion to prevent duplicate labels. An intermediate file with only a little native text is not a fully editable deck.

If the tool cannot complete generation, record actual discovery/attempts and limitations, and first finish content and asset preparation. You may deliver valid artifacts already produced and a generation plan, but tool limitations do not authorize substituting a programmatically drawn full deck on your own. If the user explicitly switches to purely native or code-based production, follow that method and mark generation checks not applicable. Local repairs to existing slides, precise scientific figures, and Step 8's native reconstruction are not subject to the new-full-slide generation requirement.

```text
Create {slide_id} independently, with aspect ratio {ratio} and target display size {dimensions/readability requirements}.
Use the style and composition of {reference image and cell}; the complete content record is authoritative.
Role: {role}; title: {exact title}; body and labels: {established wording}; data/units/formulas: {verified content}.
Structure: {nodes, relationships, edges, layout}; shared style: {parameters relevant to this slide}.
Design intent: {visual focus, reading path, diagram purpose, role hierarchy}. Preserve the reference option's design quality.
Separately composited text/chart/authentic-asset regions: {list, if any}; placeholder assets: {IDs, positions, ratios, labels, if any}.
Preserve established wording and necessary qualifications. Render text and graphics clearly without inheriting preview typos, artifacts, or distortions.
Adjust whitespace and local layout as needed for complete expression while retaining the deck's style. Do not generate a photographed scene around the slide.
```

After generation, apply [Individual slide acceptance](quality-checks.md#individual-slide-acceptance). OCR only assists localization; specifically recheck Chinese text, names, subscripts/superscripts, decimals, minus signs, units, and axes. Preserve scientific textures and genuine signals when cleaning generated artifacts. Cross-check common components on adjacent slides, long/short titles, and different batches; do not rely only on declared parameters.

When assembling the image-based PPT, place one image per slide in display order without changing its proportions, and match slide dimensions to the actual image ratio. If ratios differ, regenerate or add proportional whitespace without loss rather than stretching or cropping content. Write the master record's notes into the actual PPT. Provide current-version renders and confirmation materials under Steps 7C/7D.

## Authentic images and placeholders

For incident-related news photographs, article screenshots, and report covers, use “select assets early → reserve appropriately proportioned placeholders during generation → insert assets during reconstruction” to prevent fabricated evidence. First determine the image plan from the slide's purpose under [Real-world incident cases](content-patterns.md#real-world-incident-cases); lack of an image is not a reason to skip planning. This default applies to these asset types, not to all charts.

1. When selecting an asset, register its `asset_id`, slide ID, original image/source and date, pixel dimensions, key region, and display intent. Use a webpage screenshot only when the page itself has display value. If no asset is found, mark it pending selection.
2. Design the placeholder from the verified original image or intended display region. Record position, aspect ratio, caption, and planned crop. Mark pending assets' ratios provisional and calibrate them after verification. Do not crop important information to fit an arbitrary box. Include the plan in thumbnail and single-slide prompts. During generation, draw explicit placeholders only, not fake news text.
3. At 7D, provide a placeholder list and the original images/sources already found; clearly identify pending items. If the current endpoint is image-based review with editable reconstruction still planned, keep these placeholders for review. If the final delivery scope is explicitly image-based only, composite authentic assets before delivery unless the user explicitly requests placeholders. At any stage, insert authentic assets earlier if image details are essential evidence for understanding the argument. Do not claim placeholders are filled or the task is fully complete while assets remain unfound.
4. Insert assets as independent image objects, normally fitting the whole image proportionally. If cropping is necessary, retain the subject, key text, and context. Check source, clarity, captions, and crops.
5. Validate planned replacements against the original assets while comparing other regions with the original visual baseline. After they pass, synchronize delivered images and previews, preserving the original placeholder baseline and replacement record. Handle content/layout changes outside the plan under the main workflow's change rules; do not automatically require approval of the entire deck again.

If generation puts fake news or unreliable decoration inside a placeholder, restore the agreed placeholder. Having a real screenshot available is not by itself a reason to insert it early. Apply item 3's delivery-stage and evidence requirements to decide when to composite it, and record the applicable basis.

## Editable reconstruction

### Element decomposition and object selection

Use the content record, visual baseline, and authorization verified at the entry point. Measure positions, dimensions, layers, colors, styles, and grouping relative to slide width/height. Identify backgrounds, text, basic shapes, icons, illustrations, data charts, and connections rather than tracing every element in one image uniformly. Mark uncertain parameters as estimates and calibrate them with actual rendering. Judge complexity per element, not per slide: a complex illustration may remain a bitmap while its independent simple icons, text, boxes, and lines are reconstructed separately. A complex overall style does not justify screenshotting everything.

| Element | Preferred method |
| --- | --- |
| Text, labels, page numbers | Native text boxes and text runs |
| Boxes, circles, numbers, lines, arrows | Native shapes, text, and connectors; manually authored SVG/native paths when unusual contours are hard to match |
| Tables and flows | Native tables or semantically grouped shapes/text/connectors; combine elements to reproduce special borders |
| Standard charts with source data | Native data charts; if matching is genuinely impossible, use data-grounded native shapes and record the editing method |
| Icons and decorative symbols | Manually authored SVG or native vector paths; simple structures may combine native shapes |
| Mixed elements such as a background texture plus an icon | Decompose and choose methods separately, then group semantically |
| Formulas | Prefer the target software's native equations for structured expressions such as fractions, sums, and nested subscripts/superscripts; simple inline variables may use text. Teaching matrices requiring cell-by-cell labels/colors may use semantically grouped native tables or cells. Record alternatives according to actual editing capabilities |
| Photographs, complex illustrations, scientific figures without source data | Independent image objects preserving sources and necessary details |

Prioritize faithful reconstruction; do not change the original merely to use a particular object type. Take text from the verified master record and numbers from source data; do not guess unreadable image content. Native objects allow editing of internal properties. Verify per-path SVG editing in the target software. Bitmaps support only independent movement/cropping; record the actual capability.

First establish the target editing software without asking again about an existing user preference. If it is unknown but work can proceed, record the assumed target and limitations. For complex styles or formulas actually present, validate object structure and rendering on a representative instance before expanding reuse. A missing convenience API in the current library does not mean the target format lacks the capability. Where needed, inspect available native-format features or other construction methods rather than immediately using screenshots, flat colors, or scattered text boxes. If something genuinely cannot be done, record the specific limitation under [Reconstruction alternatives and fidelity loss](quality-checks.md#reconstruction-alternatives-and-fidelity-loss); do not invent attempts.

### Geometry, color, and text

- Measure corner radii and scale, stroke width/color, opacity, gradients, and padding. Convert tool parameters using actual width/height rather than one default corner ratio. For continuous gradients, check the color transition, direction, and extent. Do not automatically replace gradient text with separate solid-colored characters or fading borders with complete solid outlines.
- Sample clean background regions, excluding text, borders, nested cards, and noise. If obscured, use comparable nearby regions and recheck. Preserve white cards, meaningful color distinctions, and prominent gradients rather than blindly darkening the deck.
- Distinguish object bounds/SVG `viewBox` from visible contours. Restore the visible content's position relative to its background. Adjust optical centering only where centering is intended, preserving deliberate offsets.
- Check actual fonts and substitutions, size, weight, tracking, line spacing, wrapping, baselines, and vertical position. Avoid excessive negative character spacing to force text to fit. Keep appropriate space around final characters, formulas, and borders.
- Restore table rows/columns, merges, dividers, and complete highlight extents. Preserve flow endpoints, direction, feedback paths, and hierarchy; avoid missing edges and unintended line crossings/occlusion. Check dash rhythms, line caps, local emphasis, soft transparency, and layering. “Same meaning” after substitution with default shapes does not establish fidelity.
- Preserve each slide's specific background/decorative composition and crops. Reuse a common background only after verifying that the originals are actually the same. Do not replace individual backgrounds with a shared or regenerated image merely in the same style. When removing text from bitmap backgrounds, avoid changing adjacent textures, borders, or patterns.

### Icons, complex assets, and reuse

First compare the original's specific variant, parts, proportions, line widths, and negative space. Do not substitute a stock icon with roughly the same meaning. When extracting a region, retain enough margin and inspect components touching the crop boundary. Do not indiscriminately delete boundary-connected regions; if parts are missing, enlarge the crop and recheck first.

Assess reconstruction accuracy and drawing quality separately for icons. Inspect assets before import and against the actual background after import. When needed, use light/dark backgrounds to reveal white fringes, wrong colors, breaks, or residue. Distinguish intentional white parts/holes from artifacts; do not delete genuine details as cleanup.

Extract complex illustrations as independent images where appropriate. Rebuild text/lines separately where possible to avoid residual lettering overlapping native text. If the user explicitly requests vector reconstruction of complex artwork and manual drawing cannot faithfully reproduce it, use an available tracing tool such as Vtracer. Inspect contours, holes, color regions, curves, and nodes; clean the result, then import and render it. State tool unavailability or unacceptable results honestly; producing an SVG is not completion.

Validate representative instances and actual variants/backgrounds before reusing components through stable `asset_id` values. Register distinct variants separately. Check every referencing slide after modifying an asset, and expand investigation of similar defects by asset, style, or reconstruction method. After construction, perform Step 8's complete initial review and corrections using the entire [Reconstruction and fidelity acceptance](quality-checks.md#reconstruction-and-fidelity-acceptance) section, save the corrected version, and then perform Step 9's second slide-by-slide review. A representative instance passing cannot replace either complete review.
