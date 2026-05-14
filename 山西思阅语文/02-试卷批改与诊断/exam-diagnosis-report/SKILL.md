---
name: exam-diagnosis-report
description: Use when the user asks to create, organize, or revise a student exam diagnosis report, test paper analysis report, 错题分析报告, 扣分题型分类, 试卷诊断报告, or a Word report based on an annotated/graded student paper. If the paper is not yet annotated or scored, first run the exam-paper-review workflow to produce a scored annotated PDF, then create the diagnosis report; if it is already annotated/scored, do not repeat annotation.
---

# Exam Diagnosis Report

Create a standardized exam diagnosis report from student papers, original exam papers, scoring standards, question-type references, and sample reports. The default deliverable is a `.docx` report. If the student paper is not yet annotated/scored, first complete the full `exam-paper-review` scoring/annotation workflow and then write the report from that result.

## Role Boundary

This skill is report-first.

- Use `exam-paper-review` for visual paper annotation, scoring labels, teacher-style PDF comments, and annotated PDF export.
- Use this skill for the final diagnosis report: module-level deduction table, key error analysis, review priorities, and experience summary.
- If both are needed, annotate/score first, then diagnose. Do not redo annotation if the student paper already has clear scores, deductions, or comment boxes.
- Do not create a simplified or "quick" annotated PDF inside this skill. When annotation is needed, follow the dedicated `exam-paper-review` skill quality bar and use its annotated PDF as the source of truth.
- Keep annotation and report writing as two phases. After annotation, carry forward only the scoring ledger, key comments, page references, and output file paths needed for the report.

## Default Inputs

Look for and classify these materials:

- Student paper: raw answer sheet, graded paper, annotated PDF, or image previews.
- Original exam paper: question text and total scores.
- Reference answer / scoring standard: official answers, scoring rubrics, composition bands.
- Question-type references: existing题型分类资料, teaching references, prior reports.
- Sample report: used for report structure, table headings, module merging, and red-text conventions.

Ask only if the roles of files cannot be inferred reliably.

## Input State Decision

Before writing the report, decide which path applies:

### A. Already Annotated Or Scored

Use this path when the student paper has visible total score, red deductions, check/cross marks, score labels, teacher comments, or a separate deduction list.

- Treat existing scores and deductions as the baseline.
- Do not rescore the whole paper.
- Extract total score, per-question deductions, visible comments, and key teacher feedback.
- If a score appears inconsistent, report it as `建议复核` instead of silently changing it.

### B. Not Annotated Or Not Scored

Use this path when the student paper has no reliable total score or per-question scoring.

- First complete the `exam-paper-review` workflow using the original exam and scoring standard.
- Produce an annotated/scored PDF when the user expects paper comments.
- Then create the diagnosis report from the generated scoring and comments.
- Do not skip the report after annotation; the final deliverable should include the report unless the user explicitly asks only for annotation.
- Do not downgrade annotation depth to save time for the report. If the combined task is too large, finish and verify the annotated PDF first, then continue the report from its compact scoring ledger.

### C. Partially Annotated

Use this path when some deductions are visible but others are missing or unclear.

- Reuse all reliable existing marks.
- Fill missing scores only from the scoring standard.
- Mark uncertain or inconsistent scoring as `建议复核`.
- Keep the report clear about the final total used.

## Required Report Output

Default file type: `.docx`.

Default filename pattern:

```text
<学生名或文件名>_试卷诊断报告.docx
```

If the source stem is generic, use:

```text
测试试卷分析点评_试卷分析报告.docx
```

The report must use this unified structure unless the user explicitly requests another format:

```text
标题：<学生名或文件名>错题表格分析汇总

试卷总分：<满分>分
学生总分：<得分>分
重点丢分项：<重点题型列表>

一、扣分题型分类
表格：模块｜题号｜考查题型｜得分/扣分

二、重点错因分析
表格：题号｜重点题型｜错因分析｜修改方向｜扣分

三、复习计划
表格：复习优先级｜复习题型

四、经验总结
表格：总结维度｜经验总结
```

Do not add process notes above the first table. Avoid lines like `核查依据`, `说明`, `本报告按...`, or `扣分合计...` unless the user asks for audit details.

## Section 1: Deduction And Question-Type Table

The first table is the core diagnosis table.

Required columns:

```text
模块｜题号｜考查题型｜得分/扣分
```

### Module Column

The first column must be merged/integrated by module, following the sample-report style. Use this format:

```text
模块名 模块总分-模块扣分
```

Examples:

```text
古诗词 13-3
古文阅读 14-9
文学基础 6-1
名著阅读 6-2
文学类阅读 15-8
议论文阅读 10-7
非连续文本阅读 16-5
写作 40-9.5
```

Use the exact module names from the sample when available. Otherwise infer conservative Chinese-language exam modules from the paper.

### Question-Type Naming

Match existing question-type names first. If no existing type fits, create a concise name based on the assessed ability.

Good names:

- 古诗文默写
- 古诗词赏析：手法+内容+表达效果
- 文言实词解释
- 文言句子翻译
- 写景类古文：景物描写+景物特点
- 对比阅读：语言特点赏析
- 字音字形
- 词语补写/语境概括
- 仿写句子
- 撰写议论性文字：人物经历+观点启示
- 情境补写：人物心理活动
- 赏析微写作：人物形象角度/主题思想角度
- 论点提取/关键词概括
- 论证思路分析
- 图表信息概括
- 图文转化：流程介绍
- 材料总结：针对性回应与劝说
- 成长体验类作文：审题立意、内容选材、结构层次、语言表达

Avoid vague names like `阅读题`, `主观题`, `作文`, or `理解题` when a more specific ability point is available.

### Score Format

Use:

```text
满分-扣分
```

Examples:

```text
10-1
3-2
40-9.5
```

If the sample uses `得分/扣分`, preserve the column heading but still write values as `满分-扣分` unless the user requests another convention.

### Red Text Rules

Use red text for重点丢分题型, not for every deducted item.

Mark red when a question is:

- High deduction relative to its score.
- High-value subjective question.
- A clear bottleneck for later improvement.
- 作文低于30分（40分制）或低于同等比例的及格/中档线，才作为特殊重点项标红.

Serious-loss modules may also have red module text. Do not overuse red; it should guide scanning.

For rows marked as serious in the first deduction table, the whole row may use red text or a very light warm fill. In the key-error table, do **not** make large blocks of analysis text red; keep red limited to the deduction amount, priority label, or a short key phrase. Red is a scanning signal, not the default text color.

Foundation losses must be explicit in the first table. If questions 1, 2, 3, 4, 8, 9, or 10 lose points, include a short parenthetical note in the question type, such as `基础丢分：错字、漏字，需逐字巩固` or `基础表达丢分`, instead of hiding the issue only in the review plan.

## Section 2: Key Error Analysis

Only analyze重点错题. Do not write a row for every deduction.

Prioritize:

- Highest deduction questions.
- High-value subjective questions.
- Errors that reveal a recurring ability gap.
- Questions that are most useful for later review.
- 作文 only when it is below 30/40, is the dominant loss, or the user explicitly asks for composition analysis. If the composition is 30 or above, mention it only as a non-serious improvement item when it helps the review plan.

Required columns:

```text
题号｜重点题型｜错因分析｜修改方向｜扣分
```

Each row must answer three things:

1. Why the student likely wrote it that way.
2. Why that answer loses points.
3. How to revise or train the skill.

Avoid shallow comments:

```text
审题不清。
答案不完整。
需要加强。
表述不准确。
```

Prefer diagnostic comments:

```text
学生知道齐木匠诚信严谨，但没有把“木尺”和技术、戒尺、良知底线等象征意义连起来，具体情节支撑也不足。这样写的问题是只有印象判断，没有形成“句子含义-人物品质-主题升华”的赏析链。
```

Modification directions should give a usable answer frame:

```text
若写人物，按“事件+细节+品质”展开；若写主题，按“木尺多重含义+诚信底线+传承升华”组织。
```

## Section 3: Review Plan

Only give concise review question types and priority levels. Do not write a daily schedule or long training explanation unless asked.

Required columns:

```text
复习优先级｜复习题型
```

Priority order rules:

1. 基础部分优先判断。If questions 1, 2, 3, 4, 8, 9, or 10 lose relatively many points, put the relevant foundation items in `第一优先` before other modules. Questions 1-2 are古诗词基础, questions 3-4 are古文实词翻译和句子翻译基础, and questions 8-10 are文学基础. These are not trained question types in the course materials, so state that parents need to plan foundation review for the child rather than assigning course practice material.
2. 现代文阅读理解 comes next. Focus on questions 12-15. Use the question-type reference/material summary table to identify the corresponding trainable question types, and name exactly what should be practiced.
3. 古文阅读 comes after modern reading. Focus on questions 5, 6, and 7. Use the question-type reference/material summary table to identify the corresponding trainable question types, and name exactly what should be practiced.
4. 写作 comes after reading modules unless it is the dominant loss. Focus the review type on the single main writing bottleneck: 审题立意, 语言表达, or 内容选材. Do not list all three by default. Choose from the actual composition comments: if the problem is topic depth/theme direction, write `写作：审题立意`; if examples are thin or events are flat, write `写作：内容选材`; if wording is unclear, repetitive, or weakly expressive, write `写作：语言表达`.

When multiple modules have losses, preserve the above order unless one module has an overwhelmingly larger deduction and is clearly the main score bottleneck. For foundations, only list the specific foundation area that lost meaningful points; do not add all foundation items automatically.

Keep each review-plan row short. Use the format `模块/范围：题型，题型` when listing course-trainable items. For foundation items, add only a brief note such as `丢分较多，需要家长安排规划复习`.

Example:

```text
第一优先｜基础知识：古诗词默写，丢分较多，需要家长安排规划复习
第一优先｜基础知识：文言实词解释与句子翻译，丢分较多，需要家长安排规划复习
第二优先｜现代文阅读理解：人物形象分析、句段作用、内容概括
第三优先｜古文阅读：内容理解、原因概括、人物品质分析
第四优先｜写作：审题立意，重点训练题意扣合和主题升格
```

## Section 4: Experience Summary

Write a concise summary based on the whole paper, not a repeat of the error-analysis table.

Required columns:

```text
总结维度｜经验总结
```

Recommended rows:

```text
主观题共性问题
提分关键
作文方向
```

Example content:

```text
主观题共性问题｜学生不是完全不会，而是容易把题答成“内容复述”或“印象判断”，缺少题型要求中的结构层次。阅读题要先判断题型，再套对应答题链。
提分关键｜优先训练高分值、可模板化的表达题：赏析微写作、材料劝说、论证思路。先把答题框架稳定下来，再补语言细节。
作文方向｜作文若未达到特殊标注线，只写一个核心提升点，如“审题立意：把题意写成一次变化”，不要泛泛要求审题、选材、语言都练。
```

For the composition summary, name the dominant writing bottleneck only. Avoid generic summaries such as `审题、选材、语言都要加强` unless all three are clearly supported by the paper and the score is low enough to justify broad remediation.

## Formatting Standard

For Word reports:

- Use landscape orientation when tables are wide.
- Keep tables readable and compact.
- Use merged cells in the module column in the first table. The module cell must appear as one integrated block per module, not repeated unmerged text.
- Use left alignment for all table text unless the user asks otherwise.
- Use readable body text, generally around 10.5 pt for Chinese reports. Do not shrink text to make an over-wide table fit; instead adjust column widths and wording.
- Do not use equal-width columns by default. Allocate width by content length: short label columns such as `题号`, `扣分`, `复习优先级`, and `总结维度` should be narrow; long explanation columns such as `考查题型`, `错因分析`, `修改方向`, `复习题型`, and `经验总结` should get most of the width.
- Do not over-compress short columns. Give label columns a minimum readable width: about 0.9-1.0 in for `题号`/`扣分`, 1.2-1.5 in for `模块`/`复习优先级`/`总结维度`, and around 2 in for `重点题型` when it contains Chinese phrases. Adjust long columns after these minima are protected.
- When generating `.docx` tables programmatically, setting only cell widths is not enough. Also set the table `tblGrid/gridCol` values and table width (`tblW`) to the intended non-equal widths; otherwise Microsoft Word may reopen the file with equal-width columns even if a preview looked correct.
- Prefer a clean light-color table style over heavy gray: use a pale blue or similarly soft header fill, thin borders, and optional very light warm fill only for serious rows or priority rows.
- Use red text for重点丢分题型 and first-priority items, but keep red sparse. In `重点错因分析`, do not color whole paragraphs red; usually only the `扣分` cell or a short label should be red.
- Do not nest cards or add decorative sections.
- Keep headings simple: `一、扣分题型分类`, `二、重点错因分析`, `三、复习计划`, `四、经验总结`.
- The report should look like a teacher/教研 diagnostic table, not a narrative essay.

### Word Table Style Contract

Use this stable style unless the user provides a different sample:

- Font: Chinese body text around 10.5 pt; title 16-17 pt; section headings around 14 pt.
- Alignment: table text left-aligned throughout; vertical alignment centered.
- Palette: header fill `D9EAF7`, header text `1F4E79`, borders `5B9BD5`, serious-row light fill `FCE4D6`, priority-row light fill `FFF2CC`, key red text `C00000`, body text `000000`.
- Column sizing: non-equal, content-aware, and readable. Protect minimum widths before giving remaining width to long text columns.
- First table recommended starting widths on landscape pages: `模块` 1.2-1.5 in, `题号` 0.9-1.1 in, `考查题型` gets remaining width, `得分/扣分` 0.9-1.1 in.
- Key-error table recommended starting widths: `题号` 0.8-1.0 in, `重点题型` about 2.0 in, `错因分析` and `修改方向` share the remaining width, `扣分` 0.8-1.0 in.
- Review/summary tables: left label column 1.2-1.5 in, right content column gets the remaining width.

### Common Rework Traps To Avoid

Solve a class of problems before exporting, not one visual complaint at a time:

- **Preview looks right, Word opens wrong:** check and set the underlying `.docx` `tblGrid/gridCol` and `tblW`, not only python-docx cell widths.
- **Columns still feel equal:** inspect the actual XML grid widths; if the grid values are equal or near-equal, regenerate them.
- **Columns become too narrow after fixing equal widths:** protect minimum readable widths for short columns; do not shrink `题号`, `扣分`, `模块`, `复习优先级`, or `总结维度` below practical reading width.
- **Too much red:** red should guide scanning. First table serious rows may be red/light-filled, but `重点错因分析` should usually keep analysis paragraphs black and only mark `扣分` or short labels red.
- **作文被过度诊断:** 40分制作文30分以上 is not a special red item by default. In review plans, choose one dominant writing bottleneck from the actual comment instead of listing 审题、选材、语言 together.
- **Foundation loss hidden:** if foundation questions lose points, state the foundation issue directly in the first table's `考查题型` cell and also reflect it in the review priority if meaningful.
- **Wrong output folder:** the primary report belongs in `试卷诊断报告/`; a student folder copy is secondary.

Before final delivery, do a file-level check and, when table width was adjusted programmatically, an XML-level check of table grids. If possible, convert the DOCX to PDF once with LibreOffice or an equivalent renderer to confirm the document opens cleanly.

### Output Location

Save the final report in the central diagnosis-report folder when it exists, usually `试卷诊断报告/`, using the default filename pattern. If a student-specific reviewed-paper folder exists under `试卷已点评批改/<学生名>/`, also save or copy a synchronized copy there. The central `试卷诊断报告/` version is the primary deliverable path.

## Workflow

1. Inspect files and infer roles.
2. Read sample report structure if available.
3. Determine whether the student paper is already scored/annotated.
4. If unscored/unannotated, complete and verify the dedicated `exam-paper-review` scoring/annotation workflow first. Its deliverables should include an annotated PDF and a compact scoring ledger.
5. Extract total score, per-question deductions, page references, and key comments from the existing or generated annotation.
6. Match each question to a question type using references and the original exam.
7. Build the module-level deduction table.
8. Select only key wrong questions for error analysis.
9. Create review priorities from high-loss and high-leverage question types.
10. Write experience summary from cross-question patterns.
11. Generate the `.docx` report.
12. Verify the document opens/extracts, contains the four required sections, includes no extra process explanation above the first table, and follows the formatting guardrails: merged module cells, left-aligned tables, sparse red text, content-aware column widths, readable font size, correct output folder, and non-equal `tblGrid` values when non-equal columns are intended.

## Context And Delivery Limits

Avoid request-size failures during combined annotation and report tasks.

- Do not paste OCR dumps, rendered page images, or full PDF/Word extracted text back into the final response.
- Do not attach or inline verification screenshots unless the user specifically asks to see them.
- After local verification, report only concise facts: output file paths, page count, section count, and any uncertainty needing review.
- If the source paper is long or image-heavy, process annotation in page batches and maintain a compact scoring ledger instead of keeping every page image in conversation context.
- If a `413 Payload Too Large` error appears, treat the generated files as likely preserved on disk, start a fresh continuation with only the file paths and compact scoring ledger, then finish the report or final summary.

## Final Quality Checklist

Before delivering, verify:

- The report uses the unified four-section format.
- The top of the report contains only试卷总分, 学生总分, and重点丢分项.
- The first table columns are exactly `模块｜题号｜考查题型｜得分/扣分`.
- The module column is integrated/merged by module in the sample style.
- Question-type names are specific and ability-based.
- Red text marks重点丢分题型, not every small deduction.
- Composition is specially marked only when it is below 30/40 or proportionally equivalent; otherwise it is treated as a normal improvement item.
- Error analysis includes only重点错题.
- `重点错因分析` does not contain large paragraphs of red text.
- Each error-analysis row explains why the student wrote that way, why it loses points, and how to fix it.
- Review plan only lists question types and priority levels; the writing row names one dominant bottleneck instead of listing 审题、选材、语言 together by habit.
- Experience summary captures whole-paper patterns.
- Table formatting uses merged first-column modules, left-aligned text, content-aware column widths, readable font size, and a clean light-color style rather than heavy gray or equal-width tables. For `.docx`, verify the underlying `tblGrid` is non-equal for non-equal column designs.
- Short columns are not over-compressed; they meet the minimum readable width guidance in the Word Table Style Contract.
- The Word color palette follows the stable style contract unless the user requested another sample style.
- The primary `.docx` is saved in `试卷诊断报告/` when that folder exists, with a synchronized student-folder copy when useful.
- If the source paper was unannotated, the annotated PDF was produced first or the reason for skipping annotation was explicitly approved by the user.
- If the source paper was already annotated, no duplicate annotation workflow was run.
- The `.docx` exists and can be read back.
