---
name: short-video-teaching-creator
description: Create standardized short-video teaching materials from exam or lesson content. Use when the user wants a question, passage, worksheet, PDF, or answer key turned into a direct-to-camera teaching script, a matching PPT/PPTX deck, or a unified short-video teaching package with exam-context framing, step-by-step explanation, answer calibration, and reusable layout standards.
---

# Short Video Teaching Creator

## Core Rule

Do the teaching work in this order:

```text
source material -> solve the question -> calibrate against answers/rubric -> extract teaching method -> write shooting script -> build PPT -> preview and iterate
```

Do not start by writing slides or script copy from instinct. The explanation must be anchored in the original question and the scoring logic.

## Default Outputs

Unless the user asks otherwise, produce both:

- a Word shooting script that can be spoken directly on camera
- a matching PPT or PPTX deck for recording or projection

Use clear, topic-specific filenames such as:

```text
题目名称-讲解拍摄脚本.docx
题目名称-讲解PPT.pptx
```

## Workflow

1. Lock the scope to one question, one sub-question, or one tightly related teaching point.
2. Read the source files and locate:
   - the original question
   - the reference answer
   - the scoring note or rubric when available
3. Solve the problem yourself before teaching it.
4. Compare your answer against the official answer and scoring logic.
5. Extract the transferable method from the knowledge base or reference materials.
6. Match the existing short-video tone or house style when the user provides examples.
7. Write the Word shooting script with:
   - opening exam-context value
   - common mistake or low-score trap
   - layered reasoning
   - answer presentation
   - reusable method summary
8. Build the PPT as visual teaching support rather than copying the script wholesale.
9. Preview the deliverables and fix readability, overflow, and emphasis problems before final delivery.

## Script Writing Standard

Write for speaking, not for reading silently.

- Keep one main idea per paragraph.
- Prefer short, decisive sentences.
- Lead with judgment, then explanation.
- Put the value signal early: why this question matters for the exam.
- Avoid repeating the same “deep point” in slightly different words.
- End with a reusable takeaway that helps the student transfer the method.

Read `references/word-style-guide.md` before creating a new script document or when the user asks for a fixed Word house style.

## PPT Standard

Treat slides as on-screen teaching cues.

- Give each slide one job only.
- Use large, high-contrast text suitable for recording.
- Show the original question when it materially helps the explanation.
- Use comparison layouts for traps vs correct direction.
- Use sequence layouts for layered reasoning or score progression.
- Remove low-value footer noise unless the user explicitly wants it.

Read `references/ppt-style-guide.md` before creating or revising teaching slides.

## When To Read References

- Read `references/workflow.md` before a full file-to-script-and-slides job.
- Read `references/word-style-guide.md` before formatting or regenerating the Word script.
- Read `references/ppt-style-guide.md` before formatting or regenerating the slide deck.
- Read `references/qa-checklist.md` before final delivery or when iterating on user feedback.

## Hard Requirements

- Always verify the explanation against the actual question and answer key when both exist.
- Distinguish clearly between what the student wrote, what the rubric rewards, and what the teaching method abstracts.
- Keep the script and PPT aligned in sequence and terminology.
- Build reusable standards, not one-off layouts, whenever the user wants a repeatable workflow.
- Prefer concise main skill instructions and load detailed references only when needed.
