---
name: essay-polish-finalizer
description: Generate polished Chinese middle-school essay revision DOCX files matching the established 作文精修 format. Use when the user asks to 精修作文, 批改作文, 生成作文精修文件, 按样例生成作文精修, or produce a Word document with审题分类、原文波浪线编号批注、你可以试试、700-800字定稿、山西中考同类题套作迁移.
---

# Essay Polish Finalizer

## Purpose

Create a finished Word essay-polishing file, not just comments in chat. Default to a “保留型精修”: preserve the student’s complete original text and core story, mark only the sentences that need revision, then produce an A-level final draft and transfer-use guidance.

For the full operating standard, read [workflow.md](references/workflow.md). Use this file as the quick execution checklist.

## Required Inputs

- Student essay file or pasted student essay.
- A topic/title when it is not obvious.
- If available, the local reference file `参考依据标准/成长作文分类与套用方法.docx` for growth-essay category matching and 山西中考套作题目.

When files are in a project folder, inspect local files first and preserve original files by creating a backup before overwriting.

## Output

Generate a `.docx` file named and titled:

`作文题目 + 作文精修`

Do not include “保留型精修批注稿” in the title. Do not add a top “批改方式说明” paragraph.

## Fixed Document Structure

1. 审题分类
2. 核心问题分析
3. 原文就地批注与润色
4. 精修后定稿作文
5. 可套用山西中考作文题目与套作思路

## Revision Rules

- Keep the complete student original text in the document.
- In the original text, mark only the sentences that need revision with red wavy underline.
- Insert red numbered labels before each marked sentence: `【1】`, `【2】`, `【3】`.
- Directly below each original paragraph, add matching `批注1：` and `你可以试试：` blocks.
- Do not use tables to summarize revisions.
- Use green text for “你可以试试” content.
- Keep good student material and reusable phrasing. Do not rewrite into an unrelated teacher-composed essay.
- Focus edits on万能开头、名言金句式结尾、空泛议论、缺少动作细节、突然醒悟、扣题不紧.
- Write comments in a real Chinese teacher's voice: use “我读到这里觉得/会有点疑惑...” plus a concrete “为什么”, and avoid AI-like labels such as “空泛、抽象、转折生硬” unless they are immediately explained through the student's original wording.
- Revision suggestions are optional teacher references, not standard answers. Use `你可以试试：`, `如果换成这个说法呢——`, or `不一定照搬，只给你一个方向：`.
- State the polishing principle to the student as: `保留你原有的核心情节和能用的表达，只动那些容易拉低分数的地方：万能金句、说得太满的议论、细节不够具体的句子，以及和题目扣得不够紧的地方。`

## Final Draft Rules

- Produce a final polished essay based on the original.
- Keep 700-800 Chinese characters, ideally around 750.
- Small section titles are allowed when they improve structure.
- The final draft must visibly retain the student’s core events, emotional arc, and usable expressions.

## Transfer-Use Rules

Use the heading:

`可套用山西中考作文题目`

Match the essay to the same growth-writing category in the reference material. For each suitable topic, explain:

- 开头怎么改
- 中间重点句怎么改
- 结尾怎么改
- 题眼如何出现两到三次

Use the principle: 同类可套，跨类慎套；故事少改，题眼必改。

## Word Style

Use the fixed style from [workflow.md](references/workflow.md):

- Main title: 黑体, 20 pt, deep blue, centered, bold.
- Section headings: 黑体, deep blue, bold; level 1 about 17 pt, level 2 about 14 pt.
- Body: 宋体, about 13 pt, 1.35 line spacing.
- Student original: complete paragraph, black text, optional light gray shading and left border.
- Problem text: red numbered label plus red wavy underline.
- Comment block: `批注X：` red and bold, body black, optional light red shading.
- Revision block: `你可以试试：` green and bold, revision text green, optional light green shading.
- Final essay body: 宋体 13 pt, first-line indent, clean spacing.

## Verification

Before final response, verify:

- The output DOCX exists.
- The title is `作文题目 + 作文精修`.
- Original text is complete.
- Red wavy underline and numbered labels appear in the original.
- Each numbered item has a matching批注 and `你可以试试`.
- Each comment explains “我读到什么感觉 + 为什么 + 原文与问题的缺口”; ending comments give concrete deletion/replacement guidance instead of generic “升华主旨”.
- No revision-summary table is used.
- Final essay is 700-800 characters.
- Transfer-use section uses同类型山西中考作文题目 and includes开头、重点句、结尾改法.
