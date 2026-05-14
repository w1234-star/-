---
name: exam-paper-review
description: Use when the user asks to review, score, annotate, 批改, 点评, or 批注 student exam papers, answer sheets, scanned test images, or PDFs against a matching scoring standard/rubric, and produce annotated pages plus a shareable PDF. Handles already-scored papers by analyzing deducted questions, or unscored papers by scoring first.
---

# Exam Paper Review

## Reference Assets

This skill includes the binding visual standard files:

- `assets/standard-sample.png` - primary reference image for annotation layout and visual style.
- `assets/standard-sample.pdf` - original sample PDF copied from `省适应模拟卷分析/样例文件点评标准/点评样例标准pdf.pdf`.

Use `assets/standard-sample.png` as the source of truth for annotation style. Open it when the style needs confirmation or comparison, but do not repeatedly load it during the same task after the style has been established. Use `assets/standard-sample.pdf` only as a fallback when the PNG is unavailable or insufficient.

## Overview

Review student exam papers against the provided scoring standard, add teacher-style comments for deducted questions, and export a polished annotated PDF. Default to a low-load, incremental workflow: process one student at a time, avoid unnecessary rescoring, and request approval before changing the sample-style layout. The established review standard is:

- **Whole answer-sheet PDF or full-page scan:** preserve the original page/panel layout exactly and add comments directly on the original page. Prefer a tidy edge-aligned layout: place each question's comment on the right edge beside that question area, keeping comments vertically aligned when possible. Do not split, reorder, enlarge into separate pages, or create a separate wide explanation column unless the user explicitly asks.
- **Fragment images:** if the student's pending-review files are one-by-one cropped fragments or small question images, place each fragment on a clean page/canvas with its comment beside the fragment, then combine those annotated canvases into a PDF.

Keep the annotation style consistent with the established sample: small pale-yellow translucent boxes, red borders/titles, dark readable feedback text, concise but specific `错因` + `修正` feedback, and compact placement close to the original red scoring marks.

## Default Operating Mode

Use **low-load mode** unless the user explicitly asks for a full-batch review:

- Process one student file at a time. If multiple students or many pages are present, make a short batch plan and process the first manageable unit only.
- For large PDFs or many images, start with 1-2 pages, then continue in batches after confirming the style and method are working.
- Do not load or summarize the entire scoring standard when only a few deducted questions need comments. Extract only the rubric details needed for visible deductions.
- If the paper already has red scores, checkmarks, crosses, or deduction marks, treat those as the baseline and only explain the deducted items. Do not rescore the full paper unless the user asks.
- If the paper has no visible scores, score the paper and add a separate score label for every question. Put each score label beside the matching question number, not inside the comment box.
- Use `assets/standard-sample.png` as the visual style contract. Do not repeatedly load the sample PDF unless the PNG is unavailable, unclear, or the user specifically asks for PDF comparison.
- Prefer a short intermediate deduction list before drawing annotations when the page is dense or uncertain: question number, visible score/deduction, likely comment, and intended placement.
- Save generated annotated images and PDFs to disk instead of embedding them in chat. Do not inline full-resolution page previews, base64 image data, or multiple generated images in the response. If a visual check is needed, do it before final PDF export and use local files or one small downscaled preview only.
- After a valid annotated PDF has been generated, stop after a lightweight file check and report the path. Do not run post-export visual review or extra polishing passes unless the user explicitly asks.
- Write a small completion note text file next to the PDF with the final PDF path and key uncertainties, so the output can still be found if the chat response fails.

### Approval Gate For Special Cases

If the sample-style overlay cannot be followed cleanly, stop before generating the final PDF and ask the user to approve an adjustment. The request must include:

```text
无法完全按样例执行的原因：...
建议调整形式：...
影响：...
请确认是否按此调整继续。
```

Ask for approval before any of these changes:

- Splitting a full-page answer sheet into separate pages or panels.
- Adding a side column, summary page, table, or report-style explanation area.
- Moving comments far from the deducted question because nearby space is unavailable.
- Enlarging/cropping/rearranging the original answer sheet.
- Rescoring an already-scored paper.
- Processing a large batch in one pass instead of batching.
- Skipping comments for visible deducted questions because the handwriting, score mark, or rubric is unclear.

## Established Sample Layout Standard

When the user refers to the uploaded sample image, `assets/standard-sample.png`, or asks for the standard/sample layout, use the following layout as the binding standard. This standard applies especially to full-page answer sheets like the 2026 Shanxi Chinese answer card sample:

- Treat the sample as the visual contract. If a later instruction says only "按标准", "按样例", "按这个图片", or "和之前一样", it means this exact overlay-style standard.
- Preserve the source image exactly as one full answer-sheet page, including all original columns, panels, margins, black registration marks, barcodes, handwritten answers, printed grids, and existing red scoring marks.
- If the source is a three-panel or multi-panel full-page scan, keep the three panels together on the same output page. Do not crop each panel into separate pages, enlarge individual questions, or rebuild the answer sheet as a new report.
- Put deduction labels in bright red near the existing score/check/cross position, using compact wording such as `2题 扣1分`, `11题 扣2分`, or `13题:4分`, matching the source style when possible.
- Put explanatory comments in small teacher-style marginal boxes: pale sample-like yellow translucent fill, red border, red title, dark red body text, rounded corners, and tight padding.
- Comment boxes should sit on the right edge beside the corresponding question whenever possible. Keep comment boxes in a neat vertical alignment within the same page/panel so the output reads as organized teacher marginalia.
- If the right edge is unavailable, use the nearest clean edge space while preserving alignment. Avoid covering the main handwritten answer.
- For small adjacent deductions, one compact shared box is allowed when it improves readability, as in the sample where several early subquestions share a single box.
- Keep every comment compact enough to look like marginalia, but complete and readable. Prefer 3-5 concise lines when needed; do not truncate `错因` or `修正` just to make a smaller box. Do not create long paragraph cards, wide sidebars, or a separate explanation column.
- Use the title format `题号 扣X分` for comment boxes, for example `5题 扣2分` or `12（1）扣3分`. The body must remain `错因：...` and `修正：...`.
- Red score labels may be placed directly on the answer sheet without a yellow box when the paper is already scored; explanatory text should use yellow boxes.
- For unscored papers, score labels must use the same visual family as comments: pale-yellow translucent fill, red border/title color, and dark readable text. Keep them much smaller than comment boxes.
- Score labels and explanatory comments must be separate objects. Put score labels beside question numbers or along a left/right edge; keep score labels vertically aligned as a tidy score column when possible. Put `错因`/`修正` comment boxes on the right edge beside the matching question area.
- The final PDF should visually resemble teacher annotations over the original paper, not a redesigned worksheet or an analysis handout.

### Layout Priority In Tight Spaces

When the page is crowded, choose in this order:

1. Put the comment box on the right edge beside the matching question area.
2. Align its left/right edge with nearby comment boxes to form a clean vertical column.
3. Shorten wording first, then adjust box width/height while preserving complete, readable `错因` and `修正`.
4. Merge adjacent small deductions into one nearby shared box when it improves alignment and reduces clutter.
5. Use another edge area only if the right edge would cover essential handwriting or printed content.

Do not solve crowding by scattering comments across unrelated blank areas. Prefer consistent right-edge alignment over tiny placement differences near individual red marks. A comment should remain on the same horizontal band or visually adjacent row as its question so the relationship is clear.

### Pre-Export Reject, Ask, Or Redo

Before final PDF export, reject the output and redo the layout if any of these are true and can be fixed while staying within the sample-style overlay:

- A full-page answer sheet was split into multiple pages or panels.
- A new blank page, side report, right-side explanation column, table, or summary sheet was created for a full-page scan.
- The original scan was resized, cropped, rotated, reordered, or had its aspect ratio changed in a way that no longer matches the source page.
- Comment boxes are large report cards rather than compact marginal notes.
- Comment boxes are far away from the deducted question when nearby blank space is available.
- Comment boxes were moved to remote whitespace mainly to avoid overlap, causing the page to look like labeled notes rather than teacher marginalia.
- Comments cover important handwritten answers, printed question numbers, score boxes, or existing teacher marks.
- Deducted questions visible in red marks lack either a red deduction label or a nearby `错因`/`修正` box.
- Comment text was over-compressed into vague tags and no longer gives a concrete cause plus correction path.
- Full-score questions are commented on unnecessarily.
- The visual style differs from the sample: no pale yellow fill, no red border/title, black-only comments, arrows everywhere, or oversized typography.

If fixing one of these would require changing the approved output form, such as splitting pages, adding a side column, or moving comments far away, use the Approval Gate instead of silently changing the format.

Do not use this section to trigger a new visual review after the PDF has already been generated. After export, only file integrity issues should trigger more work.

### Sample-Style Visual Parameters

Use these parameters as defaults when drawing annotations programmatically, adjusting only enough to fit the page:

- Fill: pale sample-like yellow with transparency, approximately `#FFF3A6` or `#FFF4B8` at 55-70% opacity. The fill should look like a soft teacher note, not saturated marker yellow.
- Border/title: vivid red, approximately `#FF2A1A`.
- Body text: very dark red/brown, approximately `#4A1208` to `#6F1D0E`, full opacity. Avoid light, transparent, or low-contrast text.
- Border width: thin but visible, about 2-3 px on a 1800 px wide scan.
- Corner radius: small rounded rectangle, about 4-8 px on a 1800 px wide scan.
- Padding: compact, about 6-9 px.
- Font: Chinese-capable sans or Song/Kai font; title slightly bold. On an 1800 px wide scan, use body text around 20-24 px and title/score text around 22-26 px. Do not shrink body text below 18 px.
- Box width: only as wide as needed for readable complete feedback; aim for no more than one third of a single answer-sheet panel, and do not exceed it unless unavoidable.
- Text must be wrapped inside the box with enough line height. Never clip, crop, fade, or end feedback with an ellipsis because the box is too small.

## Workflow

1. **Inspect files and choose scope**
   - Look for student papers, scoring standards, original exam papers, and existing outputs.
   - Common folders include `待点评分析试卷`, `待点评学生试卷`, `模拟卷评分标准`, `省适应模拟卷评分标准`, and `试卷已点评批改`.
   - If file roles are unclear, infer from names/content; ask only when the ambiguity blocks reliable work.
   - If multiple students or many pages are present, do not begin a full batch automatically. State the proposed first batch and proceed with the smallest useful unit.

2. **Read only the needed scoring standard**
   - Extract each visible deducted question's reference answer, total score, scoring notes, and deduction rules.
   - For writing/composition, extract the rubric dimensions and score bands.
   - If the scoring standard references the original paper for context, read only the matching question area unless full context is required.
   - Avoid expanding the whole standard into the working context when the current batch only needs a few questions.

3. **Read the student paper**
   - Identify page count, question layout, visible scores, check marks/cross marks, and handwritten answers.
   - Determine the input layout type before annotating:
     - `full-page`: a normal PDF page, answer sheet page, or a scan that already contains multiple answer-card panels.
     - `fragment`: separate cropped images of individual questions/answers without a complete answer-sheet page.
   - If the file is a full-page scan or multi-panel answer-card image, treat the entire source page as the page to annotate.
   - If the file is a set of fragment images, keep each fragment intact and annotate beside it on a generated canvas/page.
   - Decide whether the paper is already scored.
   - If red teacher marks, checkmarks/crosses, scores, or deductions are visible, read and follow those existing marks as the baseline.
   - If handwriting or a question area is unreadable, mark it as an uncertainty instead of inventing details.

4. **Score only if needed**
   - If no score is present, score according to the rubric before commenting.
   - Mark the score clearly beside each corresponding question number.
   - For unscored papers, every scored question needs a visible score label, including full-score questions. The label format should be compact, such as `1题 3/3分`, `5题 2/4分`, or `作文 38/50分`.
   - Use the same pale-yellow/red-border style as comment boxes for score labels, but make score labels smaller and simpler.
   - Keep scoring labels separate from feedback comments: do not combine `分值` with `错因/修正` in the same box.
   - Place score labels beside the question number or along the nearest left/right page edge. Keep them vertically aligned as a neat score column when multiple labels appear on the same page/panel.
   - If scores already exist, treat them as the baseline unless the user explicitly asks for rescoring.
   - If an existing score appears inconsistent with the rubric, mention `建议复核` rather than silently changing it.
   - Do not infer a different deduction just because the rubric allows another score. Existing teacher red marks win unless the user asked for re-scoring.

5. **Comment deducted questions only**
   - Full-score questions do not need analysis.
   - Every deducted question on every answer sheet page needs a visible comment.
   - For full-page scans, place comments directly on the original page, preferably on the right edge beside each corresponding question area.
   - For fragment images, place comments beside the fragment on the same canvas/page.
   - Avoid covering the main answer body. If the right edge is crowded, first shrink or merge nearby comments; only then use the closest left/right edge space.
   - Keep each comment visually attached to the relevant question by row/band alignment. Remote top/bottom-page notes are not acceptable unless the deducted item itself is near that area.
   - Several adjacent small questions may share one compact annotation box if that matches the established sample and improves readability.

6. **Export**
   - Save annotated page images.
   - Do not attach generated full-page images back into the conversation. Large images should remain as local files and be referenced by path.
   - For full-page scans, preserve the original page count, page order, page aspect ratio, and multi-panel layout.
   - For fragment images, create one PDF page per fragment or per logical group of fragments, with each fragment and its beside-comment clearly visible.
   - Combine them into a shareable PDF, usually under `试卷已点评批改/`.
   - Name the PDF with the student name or source stem, such as `雪儿试卷_批注点评版.pdf`.
   - Once the final PDF exists and has a reasonable file size, treat the task as deliverable unless a severe blocking issue is detected.
   - Save a sibling completion note, such as `雪儿试卷_批注点评版_完成路径.txt`, containing the absolute PDF path and any key uncertainties.

7. **Lightweight final check**
   - Default final check is file-based: verify the PDF exists, has nonzero/reasonable size, and the expected page count when that can be checked cheaply.
   - Do not open rendered page previews, attach images, or perform visual review after final PDF generation.
   - Do not perform an automatic second editing pass for minor issues such as a comment that could be slightly closer, a title that could be clearer, or wording that could be more polished.
   - Only redo after export for file integrity issues: missing final PDF, unreadable/corrupt PDF, or clearly wrong page count.
   - If visual quality concerns remain after export, mention them as optional notes or ask the user whether to revise; do not reopen images or render previews automatically.

## Comment Rules

Use this fixed structure for each deducted question:

```text
错因：……
修正：……
```

Good comments must:

- Explain the student's concrete error, not just say the answer is wrong.
- Name the likely cause: misread the prompt, missed an answer angle, used an inaccurate concept, lacked textual evidence, gave weak reasoning, or omitted a required structure.
- Give a specific correction path: add a keyword, use an answer framework, return to a certain material, compare two texts, expand with details, or reorganize the logic.
- Stay short enough to fit beside the answer area while preserving real diagnostic value.
- Include at least one concrete missing point, wrong angle, unsupported claim, or method issue when the answer context allows it.
- Include an actionable repair step, such as the answer structure to use, the keyword to add, the evidence to return to, or the comparison angle to complete.
- Keep both parts complete: every deducted comment should contain a full `错因` sentence and a full `修正` sentence. Do not cut off the end of either part.

Avoid vague comments:

```text
这里错了。
答案不完整。
需要加强。
注意审题。
表述不清。
```

Prefer comments like:

```text
错因：只写到画面内容，没有点出修辞手法和人物精神，导致赏析角度缺失。
修正：按“手法+内容+表达效果”补全，最后落到人物情感或形象特点。
```

If space is tight, compress wording without removing the diagnostic core:

```text
错因：只答内容，缺少手法和情感落点。
修正：补“手法+效果+人物精神”。
```

## Visual Style

Keep annotation boxes visually unified:

- Pale yellow translucent fill matching the sample image; avoid saturated or highlighter-like yellow.
- Red border.
- Red title text.
- Dark red/brown body text with strong contrast.
- Rounded rectangle.
- Compact but readable box size; comments should look like teacher marginalia on the paper, not a separate report. Prefer concise wording, but do not make comments so shallow that the actual cause or correction path is missing.
- Title format: `题号 扣X分`, such as `12（1）扣3分`. If the existing red mark uses `题号:X分`, keep that score wording consistent with the source.
- Body format: `错因：...` and `修正：...`.
- Score label format for unscored papers: `题号 得分/满分`, such as `3题 2/4分`. Score labels should not contain `错因` or `修正`.
- No arrows unless the user asks for arrows.
- For full-page scans, keep annotations overlaid on the original image/page and close to the matching deducted item.
- Do not create a new wide blank comment column for full-page scans unless the source already has a margin that supports it or the user explicitly requests it.
- Do not split a single source page into multiple PDF pages merely to make comments larger. Preserve layout first; use concise comments and compact boxes.
- For fragment images, a generated canvas with the fragment on one side and the comment beside it is allowed and preferred.

For composition/writing tasks, use three separate boxes:

```text
作文 审题立意
作文 内容选材
作文 语言表达
```

Each composition box should still use `错因` and `修正`.

## Practical Tooling Notes

- Use existing PDF/image/document tools in the environment; prefer reliable structured extraction for PDFs when available.
- For scanned answer sheets, use visual inspection and image annotation.
- When generating image annotations programmatically, choose a Chinese-capable font and check that text renders correctly.
- Keep intermediate images alongside the final PDF unless the user asks for cleanup.

## Final Response

Use an ultra-short plain-text final response. Do not include image previews, Markdown image tags, base64 data, long summaries, or rendered page thumbnails.

Preferred final format:

```text
已生成批注点评 PDF：
/absolute/path/to/output.pdf

备注：...
```

Only include `备注` when there is an important uncertainty, such as unreadable handwriting, missing rubric details, or questions that may need score review. If there are no important uncertainties, only report the PDF path.
