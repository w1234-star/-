# 山西思阅语文 Codex Skills 资源库

这里整理的是一组用于语文教学工作的 Codex skills，适合作文精修、试卷批改、诊断报告、题型教研和短视频讲解材料制作。

## 目录分类

```text
山西思阅语文/
  01-作文精修/
    essay-polish-finalizer/
  02-试卷批改与诊断/
    exam-paper-review/
    exam-diagnosis-report/
  03-题型教研/
    question-type-teaching-research/
  04-短视频讲解/
    short-video-teaching-creator/
```

## Skill 说明

| 分类 | Skill | 用途 |
| --- | --- | --- |
| 作文精修 | `essay-polish-finalizer` | 生成作文精修 Word：审题分类、原文批注、精修定稿、山西中考套作迁移。 |
| 试卷批改 | `exam-paper-review` | 根据评分标准批注学生试卷，输出带教师评语的 PDF。 |
| 试卷诊断 | `exam-diagnosis-report` | 根据已批改试卷生成错题分类、重点错因、复习计划和经验总结报告。 |
| 题型教研 | `question-type-teaching-research` | 生成题型教研教师版和学生版 Word 文件。 |
| 短视频讲解 | `short-video-teaching-creator` | 生成短视频讲解脚本和配套 PPT。 |

## 使用方法

如果要安装到 Codex，本仓库里的英文 skill 文件夹可以复制到本地 skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R 山西思阅语文/01-作文精修/essay-polish-finalizer ~/.codex/skills/
cp -R 山西思阅语文/02-试卷批改与诊断/exam-paper-review ~/.codex/skills/
cp -R 山西思阅语文/02-试卷批改与诊断/exam-diagnosis-report ~/.codex/skills/
cp -R 山西思阅语文/03-题型教研/question-type-teaching-research ~/.codex/skills/
cp -R 山西思阅语文/04-短视频讲解/short-video-teaching-creator ~/.codex/skills/
```

安装后可用类似方式调用：

```text
Use $essay-polish-finalizer to polish this student essay.
```

## 命名说明

GitHub 支持中文文件夹名。本仓库使用中文目录做展示分类，同时保留英文 skill 文件夹名，方便 Codex 识别和安装。

## License

MIT License. See [LICENSE](LICENSE).
