---
name: question-type-teaching-research
description: Use when the user asks to do Chinese-first question-type teaching research, 待教研课件整理, 题型教研, 知识点与题型方法整理, or to generate matched 教师版 and 学生版 Word files from a focused question type. Prioritize Chinese reading, classical Chinese, poetry, and integrated-learning materials, while allowing other subjects by using the same method-summary plus leveled-example workflow.
---

# 题型教研整理

Use this skill to turn a focused question-type packet into two polished Word documents:

- `题型名称_教师版.docx`
- `题型名称_学生版.docx`

Default to Chinese-language teaching research standards. If the material is from another subject, keep the same structure but adapt terminology and examples to that subject.

## Non-Negotiable Quality Gate

This skill is for **精修教研成果**, not bulk content reshaping. Never satisfy a request by simply extracting every packet and pushing it through a generic template.

- Do not batch-generate a whole folder of题型成果 unless each题型 is still individually solved, screened, method-summarized, example-selected, and layout-checked.
- If the source folder contains many题型, process in small batches and tell the user which batch is being精修. Prefer finishing one年级/one题型 group at high quality over producing many low-quality files.
- Before overwriting an existing成果文件, inspect it. If it may be a previous standard/high-quality version, back it up or ask before replacing it.
- If a standard example file is available in the workspace or supplied by the user, treat it as the layout authority. Extract its document structure, colors, table/card pattern, and heading hierarchy before generating new files.
- The output must read like a teaching-research handout, not an automatically reformatted question bank.
- For best quality, process **one question type at a time**. Two closely related, clean question types are the upper limit. Do not take on three or more question types in one pass if the user expects premium教研 quality.
- When changing layout or method-analysis standards, first produce one sample question type and inspect/ask for confirmation before applying the pattern widely.

## Core Workflow

1. **Identify the question-type boundary**
   - Determine the target question type from the file name, headings, source collection, or user instruction.
   - Exclude neighboring question types even when they look related.
   - Example: for `停顿断句`, keep slash-based断句/停顿题; exclude朗读指导, 语调, 重音, 心理揣摩 unless the user explicitly wants them.
   - Do a **same-family boundary check** before writing the knowledge section. Many Chinese question types share words such as `理解`、`内涵`、`启示`、`品质`、`感悟`, but they may belong to different题型. Do not let broad source headings pull in adjacent types.
   - For `理解内涵`, keep questions with a clear词句/诗句/关键语句理解对象, such as “谈谈你对画线句的理解”“某词体现了怎样的情感”“两句话有何异曲同工之妙”. Exclude standalone人物品质、道理启示、生活感悟、人物形象概括 unless the prompt explicitly asks to merge them.

2. **Do the full set first**
   - Quickly solve all questions in the type before drafting.
   - Look for repeated wording, answer logic, common signals, and likely student errors.
   - Do not expose every rough solution unless the user asks; use this pass to form the method.
   - Mark and exclude duplicates, malformed answer records, or neighboring question types before selecting examples.

3. **Build the knowledge section**
   - Prefer clear prose over all-table output.
   - Include: 题型定位, 出题形式, 核心方法, 常见信号/判断依据, 易错提醒.
   - Use a small table or callout only when it improves scanning, such as signal lists or method steps.
   - The `出题形式/常见问法` must be screened against the target题型 boundary. Do not list every related prompt from the packet if some prompts actually belong to neighboring题型. When confusion is likely, add a student-facing `易混淆题型提醒`, explaining how students should distinguish the nearby题型.
   - The files are **direct teaching handouts**, not research notes. Do not expose internal process phrases such as `从待教研材料看`、`来源依据`、`依据来源`、`边界提醒`、`题库筛选发现`. Convert them into student-facing wording such as `课堂上常见问法`、`抓题方法`、`易混淆题型提醒`.
   - If a boundary warning is needed, phrase it as a student learning distinction, not as the author's screening logic. Example: use `易混淆题型提醒：人物形象题围绕“人物言行—人物品质”；理解内涵题重在解释词句深层含义；道理启示题重在谈做人道理或生活感悟。`

4. **Define the reusable method**
   - Make the method operational, not conceptual.
   - Add short mini-examples inside the method section.
   - For 文言停顿断句, prefer:
     1. 盲翻句意
     2. 找标志词
     3. 主谓宾梳理层次
     4. 按限定处数复核

5. **Select three leveled examples**
   - Use this exact order:
     - `【题目自测】`
     - `【查漏补缺】`
     - `【强化巩固】`
   - Latest selection requirement for Chinese classical-reading question types: all three examples must include `甲/乙` two-text comparison. Prefer课内对比 or课内外古文对比. At least two of the three examples should be课内外古文对比.
   - Do not overuse the same课内 anchor text across all three examples. Rotate课内篇目 where the packet allows, so the three tasks do not all rely on the same课内文章/person/passage.
   - If the source packet does not contain enough clean comparison questions to meet this requirement, create an original question when necessary, but base it on article content already present in the题库/packet or clearly available课内材料. Do not invent unsupported source passages.
   - Keep difficulty smooth. The third example may be slightly harder, but must not jump so much that it hurts student confidence.
   - Prefer representative examples that exercise the method, not obscure edge cases.
   - Do not force three examples from bad material. If there are fewer than three valid examples, first try to adapt or originalize a clean question from valid packet passages to satisfy the comparison requirement; if that still cannot be done, state the limitation.

6. **Create the teacher version**
   - Include knowledge, method, mini-examples, and the three examples.
   - Each example includes: 原文, 题目, 答案, 方法带入解析, 规范书写.
   - The method analysis must map directly to the reusable method. Do not introduce a new method only in the example.
   - In the third step for断句类题, write `主谓宾梳理层次` and explicitly identify subjects, predicates, objects/complements, or semantic layers.

7. **Create the student version**
   - Include the same knowledge, method, mini-examples, original texts, and questions.
   - Do not include answers or teacher-only explanations.
   - `【题目自测】`: direct answer area only.
   - `【查漏补缺】`: provide an answer-framework guide that students complete.
   - `【强化巩固】`: direct answer area only.
   - If the framework already asks for the final answer, do not add another final-answer area.

## Student Answer Framework Rules

Use an answer framework only for `【查漏补缺】`.

Good pattern for a断句题:

```text
【答题框架引导】
①盲翻句意：________________
②找标志词：________________
③主谓宾梳理层次：____________
④断句答案：________________
```

Guidelines:

- Give steps and concise cues, not the answer.
- If filling every step would be unnatural for the subject or question type, provide only a short prompt plus one final answer line.
- Use continuous underscores for answer lines, not dash-like separators.
- Match line length to the available text width and expected answer length. Do not make lines visibly too short or too long.
- Increase the number of lines only when the expected answer genuinely needs more space.

## Chinese-Language Formatting Standards

- 原文 paragraphs use first-line indentation of about two Chinese characters.
- Keep article/material paragraphs separated; do not merge unrelated natural paragraphs or 甲/乙/丙 materials.
- Knowledge sections should feel like a teaching handout, not a spreadsheet.
- Use tables only where they clarify repeated structure.
- Teacher and student versions must share the same examples, order, original text, and question wording.

## Output Naming

Name the final files exactly:

- `题型名称_教师版.docx`
- `题型名称_学生版.docx`

Examples:

- `停顿断句_教师版.docx`
- `停顿断句_学生版.docx`

If the workspace already contains a different naming convention from earlier work, follow the user's latest naming instruction and state the final filenames clearly.

## Visual Style

Use the following **fixed standard layout** across both files. This is the canonical style; do not substitute a plain Word handout layout.

### Fixed Typography and Colors

- Font: `Microsoft YaHei` for title, headings, body, tables, and cards.
- Page setup must match the approved local standard before judging table alignment. This applies to **all题型整理 outputs**, not only one年级 or one文体. Before generating a DOCX, inspect an approved file from the same成果体系/同批次/同目录 and inherit its page size, margins, table widths, and table grids. Do not leave generated DOCX files on a default page size or different margins.
- Title: centered, bold, 21 pt, deep blue `#1F4D78`.
- Subtitle: centered, 10 pt, gray `#5F6368`.
- Heading 1: bold, 15 pt, deep blue `#1F4D78`.
- Heading 2: bold, 12.5 pt, deep blue `#1F4D78`.
- Body: 10.5 pt, dark text `#202124`, line spacing about 1.18.
- Section labels such as `原文`、`题目`、`方法带入解析`: bold, deep blue `#1F4D78`.
- Signal/summary card fill: very light blue-gray `#F5F9FC`.
- Method step boxes: **no background fill**; use only restrained light blue-gray borders.
- Method step titles inside method boxes, such as `第一步  盲翻句意` or `第二步  解释表层含义`, must be deep blue `#1F4D78` and bold. The explanatory body text below the title remains normal dark body text.
- Analysis table header fill: light blue `#DCEAF5`.
- Table/card borders: restrained light blue-gray borders, no heavy black grid.

### Fixed Teacher Version Structure

Teacher version must follow this exact structure:

1. Title: `题型名称题型教研整理`
2. Subtitle: `知识点梳理 · 方法示例 · 三题分层训练`
3. `一、知识点总结`
   - 2-3 clear prose paragraphs.
   - One single-column signal/summary card when useful.
4. `二、通用答题方法：方法名称`
   - Use separate single-column method boxes, one box per step.
   - Method boxes have borders only and no background fill.
   - Step titles such as `第一步  盲翻句意` must be bold/deep blue.
   - Do **not** include examples in the method boxes. This section teaches the system method only: what to look at, how to judge, how to transform evidence, and how to write.
   - The first selected example `【题目自测】` is where the method is fully demonstrated on a real question.
5. `三、精选题目实战应用`
   - `【题目自测】...`
   - `【查漏补缺】...`
   - `【强化巩固】...`
6. Each teacher example includes:
   - `原文`
   - `题目`
   - `参考答案：...`
   - `方法带入解析`
   - A two-column table with headers `方法步骤` and `本题带入解析`.
   - The table must be visually left-narrow/right-wide. The left column is a short label only, about 18%-22% width, such as `第一步：锁定对象`; the right column takes about 78%-82% width for detailed analysis.
   - For DOCX, do not rely on a width hint only. Lock the table geometry: fixed table layout, explicit `tblGrid`, table width, and every cell width (`tcW`) so Word does not render it as equal-width columns.
   - The right column must actually solve the example step by step. Each row must contain real content from the current question, not a generic instruction. For example, in人物形象题, `第二步：圈画依据` must list the specific人物言行 from this passage, and `第三步：概括特点` must map each言行 to a具体品质.
   - Do not let most of the substantive answer sit only in `第四步`. Steps 1-3 must each do real work: identify the task/object, extract textual evidence, and transform evidence into answer points.
   - `规范书写：...` only when it is meaningfully different from the参考答案, such as when the answer needs a final compressed template after a longer step-by-step explanation. If it duplicates the参考答案, delete `规范书写`.
   - For short-answer questions, `参考答案` should be the final standard answer only. Its logic must match the method/template and include all scoring points, but it should not include long step-by-step reasoning.

### Fixed Student Version Structure

Student version must visually match the teacher version:

1. Title: `题型名称题型练习`
2. Subtitle: `知识点梳理 · 自主作答 · 思路补全`
3. Same knowledge prose, signal card, and method cards as the teacher version.
4. `三、精选题目练习`
5. Same three examples, same order, same original text, same questions.
6. `【题目自测】` and `【强化巩固】`: direct answer line only.
7. `【查漏补缺】`: use a two-column framework table with headers such as `答题框架引导` and `学生填写`; do not add an extra final answer line if the table already contains the final answer row.
8. Student version must not include `答案：` with real answers, `参考答案`, `答案解析`, `方法带入解析`, or `规范书写`.

### Canonical Example Pattern

For `停顿断句`, the standard teacher version uses:

- Knowledge prose explaining that断句 is not guessing slashes but splitting clear semantic layers.
- A signal card covering:
  - 引语信号：`曰、云、谓`
  - 句首/承接信号：`夫、盖、故、乃、遂、若、苟、今`
  - 句尾语气信号：`也、矣、耳、乎、哉、邪`
  - 结构信号：`者……也`、`所以……者`
- Four method boxes, border only and no background fill:
  1. `第一步  盲翻句意`
  2. `第二步  找标志词`
  3. `第三步  主谓宾梳理层次`
  4. `第四步  按限定处数复核`
- Method boxes contain no examples. The complete example demonstration appears under `【题目自测】` in the teacher version.
- Every teacher example has a left-narrow/right-wide two-column table mapping the method steps to the specific answer.

For other题型, keep this visual pattern and replace only the method names, signals, examples, and analysis content.

### Layout Prohibitions

- Do not output a document made only of paragraphs and a generic table.
- Do not use a single giant table for all knowledge.
- Do not nest cards inside cards.
- Do not add decorative colors, gradients, icons, or unrelated page furniture.
- Do not let student answer lines or tables run awkwardly short/long; match expected answer length.
- Do not use filled backgrounds for method step boxes.
- Do not put examples in the method section.
- Do not repeat `规范书写` when it is identical to `参考答案`.

When generating `.docx`, also use the document skill if available and follow its render/QA workflow. If full rendering is blocked because LibreOffice/`soffice` is unavailable, still inspect text structure and available system previews, and disclose the limitation.

## Failure Review and Prevention

This skill was previously misused in a low-quality way. Do not repeat these mistakes:

- **Mistake: Bulk generation replaced teaching research.** A script extracted many课件 and pushed them into a generic template, producing many files but little教研 value.
  - Prevention: Process one focused题型 or a small batch. For each题型, solve, screen, summarize, select, write, and check.
- **Mistake: Standard layout was not extracted first.** The generated files ignored the canonical `停顿断句` layout, colors, cards, and per-example analysis tables.
  - Prevention: If a standard file exists or is supplied, inspect its paragraph styles, colors, headings, cards, and tables before writing.
- **Mistake: Neighboring题型 leaked in.** For example,朗读指导 was mixed into停顿断句.
  - Prevention: Apply the question-type boundary gate before example selection.
- **Mistake: Same-family concepts widened the题型 definition.** For example, `理解内涵` was allowed to absorb standalone人物品质、道理启示、生活感悟 because these also ask students to interpret meaning.
  - Prevention: Build a positive/negative boundary list before drafting the knowledge section. Positive list = prompts that directly ask for词语、画线句、诗句、关键语句的内涵; negative list = adjacent prompts such as单纯人物品质、做人启示、生活经验感悟、人物形象概括. The knowledge section's `常见问法` must include only the positive list and must explicitly warn about likely negative-list confusion.
- **Mistake: Internal research language leaked into teachable handouts.** Phrases such as `从待教研材料看`、`依据来源`、`边界提醒` made the document read like a production note instead of a classroom file.
  - Prevention: Rewrite all knowledge and signal-card language as student-facing teaching language. Use `课堂上常见问法` instead of `从待教研材料看`; use `抓题方法/抓人物的方法` instead of `依据来源`; use `易混淆题型提醒` instead of `边界提醒`.
- **Mistake: Three selected examples did not all train comparison reading.** A set could contain single-text tasks or repeat the same课内 passage too much, weakening the intended课内外迁移.
  - Prevention: Before drafting, audit the three-example set: every example must be甲乙对比; at least two should be课内外古文对比; the课内 anchor should rotate where possible. If the packet lacks enough suitable questions, create an original question from existing packet/课内 passages rather than lowering the comparison standard.
- **Mistake: Existing成果 were overwritten.** A previous standard file was replaced by a rough generated one.
  - Prevention: Inspect and protect existing成果 before writing. Back up or ask when uncertain.
- **Mistake: Student version looked clean but was not pedagogically paired.**
  - Prevention: Student and teacher versions must share examples and layout, while the student file removes only answers and teacher-only reasoning.
- **Mistake: Method examples were misplaced.** Method boxes used examples, making the system method cluttered and fragmentary.
  - Prevention: Method boxes teach only the method. Put the complete example demonstration in `【题目自测】`.
- **Mistake: Method-step visual hierarchy was too weak.** Step titles inside method boxes looked like ordinary body text, so the reusable method did not scan clearly.
  - Prevention: Format each method-step title as bold deep blue `#1F4D78`, with normal dark body text for the explanation. Verify this in both teacher and student files, not just one version.
- **Mistake: Answers and规范书写 duplicated each other.**
  - Prevention: Use `参考答案` as the standard answer generated by steps; include `规范书写` only when it adds a distinct final compressed expression.
- **Mistake: Table column widths were declared but not visually fixed.** Word rendered the analysis table close to equal-width columns even though the intended design was left-narrow/right-wide.
  - Prevention: Use fixed OOXML table geometry (`tblLayout` fixed, `tblGrid`, `tcW`) and visually inspect a sample before scaling.
- **Mistake: Table/card widths were close but not identical to the established standard.** New files used slightly different single-card widths, analysis-table grids, and student-framework grids, so the documents looked subtly inconsistent with prior成果 even though the colors and headings matched.
  - Prevention: Before generating any题型 output, inspect a current approved standard file from the same成果体系/同批次/同目录 and extract the actual `tblGrid` values. Reuse those exact grids for the same element type. If the user is working in a new年级、文体、学科或输出目录, first identify the nearest approved local standard and follow that standard exactly.
- **Mistake: Table alignment was debugged at the table level only, while the real mismatch was page setup.** The table `tblGrid` values were changed, but the files still used a different page size and left/right margins from the approved files, so the visual table boundaries still did not align with the surrounding正文 and with previous成果.
  - Prevention: Treat table alignment as a three-part check for every DOCX: page size, page margins, then table grid. Compare the generated file against an approved local standard file by inspecting `w:pgSz`, `w:pgMar`, `w:tblW`, and `w:tblGrid`. Do not hard-code one年级's values as a universal truth; use the approved values for the current output family.
- **Mistake: Verification trusted internal XML changes without measuring the rendered result.** The file had changed, but the user still saw the same visual problem because the check did not compare the rendered table left/right edges against the正文 block.
  - Prevention: After layout fixes, clear/refresh previews when possible and inspect an actual rendered page. Do not report success from `tblGrid` values alone. In the rendered preview, confirm the signal card and all method boxes start and end at the same x-positions and sit within the正文 text area.
- **Mistake: Four-step method boxes collapsed into one continuous-looking block or did not match the approved separated-card rhythm.** The content was correct, but the section did not look like the earlier files.
  - Prevention: Render each method step as its own separate one-column table/card with border only, no fill, full standard text width, and a visible paragraph gap between cards. Do this in both teacher and student versions.
- **Mistake: Student direct-answer areas used a different label/style from prior files.** Using `作答：____` or multiple extra lines made the student version diverge from the established handout pattern.
  - Prevention: For `【题目自测】` and `【强化巩固】`, use the existing standard direct answer pattern from approved student files, normally `答案：_______________________________________________________________________________`. For `【查漏补缺】`, use only the framework table; do not add another direct answer line outside the table.
- **Mistake: Step analysis became generic and lopsided.** Steps 1-3 contained generic instructions while the real answer was dumped into step 4.
  - Prevention: Every row in `方法带入解析` must execute that step on the current passage. Step 2 must quote/list concrete evidence; step 3 must map evidence to qualities/effects/themes; step 4 only compresses the already-built points into final answer language.
- **Mistake: Too many question types were modified at once.** Batch edits hid quality failures until they appeared across many files.
  - Prevention: For premium教研, handle one题型 per turn. Build and inspect one样板 before applying any new layout or reasoning pattern.

## Delivery Checklist

Before responding, verify:

- Two files exist and use `题型名称_教师版.docx` / `题型名称_学生版.docx`.
- Existing high-quality files were not accidentally overwritten without backup or explicit intent.
- Teacher version has full answers, method analysis, and规范书写.
- Student version has no answer leakage.
- Example order is `题目自测 -> 查漏补缺 -> 强化巩固`.
- All three selected examples are甲乙两文对比; at least two are课内外古文对比 unless the source material truly cannot support it and the limitation is disclosed.
- The three examples do not over-rely on the same课内文章/person/passage when alternatives are available.
- Difficulty gradient is smooth.
- The teacher analysis maps one-to-one to the method section.
- The knowledge section's common-question list has been filtered against the target题型 boundary; adjacent题型 are excluded and named when likely to be confused.
- Knowledge prose and signal cards use classroom-facing language, with no internal process phrases such as `从待教研材料看`、`来源依据`、`依据来源`、`边界提醒`.
- For断句类题, the third method step uses主谓宾梳理层次.
- Student answer lines are continuous underscores with appropriate length.
- Student direct-answer areas use the approved label/style from standard student files, normally `答案：_____`, not a newly invented `作答：_____` style.
- `查漏补缺` does not duplicate final answer areas.
- Original text, question wording, and example order match across both versions.
- Layout follows the fixed standard: `Microsoft YaHei`, title `#1F4D78`, subtitle `#5F6368`, body `#202124`, signal card fill `#F5F9FC`, method boxes no fill, table header fill `#DCEAF5`.
- Page setup matches the approved local standard for the current output family, not just the content styles. Verify `w:pgSz` and `w:pgMar` against an approved file from the same成果体系/同批次/同目录.
- Table/card geometry matches the approved local standard exactly, not just approximately. Verify `tblGrid` for each recurring element type: signal/method cards, teacher analysis tables, student framework tables, and any knowledge-summary tables.
- Rendered preview confirms visual alignment: signal card, four method boxes, and later tables share the same left/right edges and align with the正文 content block. Do not rely only on XML/table-width inspection.
- The four method steps are four separate one-column border-only method boxes/cards in both teacher and student files, with consistent spacing between boxes.
- Method-step titles inside method boxes are bold deep blue `#1F4D78` in both teacher and student versions; method explanation text remains normal body style.
- Method section contains no examples, only detailed system方法.
- Teacher examples use per-example two-column method analysis tables with left column about 18%-22% and right column about 78%-82%; DOCX table geometry is fixed, not merely hinted.
- In every teacher analysis table, steps 1-3 contain concrete current-question work, and step 4 only finalizes the answer.
- Teacher answers are labeled `参考答案`; `规范书写` is omitted when duplicate.
- Student `查漏补缺` uses a framework table and contains no real answer.
- Layout, colors, title hierarchy, cards, tables, and spacing are consistent across both files.
