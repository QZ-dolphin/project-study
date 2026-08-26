# project-study

<p align="center">
  <img src="assets/project-study.svg" alt="project-study" width="160" />
</p>

用于系统性研究学习已有项目的 AI 技能：回答用户关于项目代码框架与功能的问题，并将问答持续整理为一份项目学习文件（Markdown 知识库）。

## 技能特性

- **强制信息确认**：开始前必须向用户确认项目路径、项目名、学习文件保存目录，不自行推断或跳过
- **持续积累**：在学习目录维护 `<项目名>.md` 学习文件，每次问答按 `Q<序号>-<日期>.md` 存入 `questions/` 子目录，并在学习文件中维护问题索引
- **基于代码的回答**：回答必须实际阅读项目代码，标注文件路径与行号证据，区分事实与推断
- **自动维护**：内容去重、过时内容更新（附更新记录）、问题超过 20 条时合并归档

## 触发条件

- **触发**：用户希望学习、理解某个项目，或对其代码框架、运行流程、功能实现进行提问
- **禁止触发**：用户要求实际开发、修改代码功能时

## 使用

- 将本目录作为技能安装（个人技能可放至 `~/.qoder/skills/project-study/`）
- 完整的工作流程、内容规范、文件模板与更新逻辑见 [SKILL.md](SKILL.md)

## 在其他 Agent 中使用（Claude Code / Codex）

本技能遵循通用的 Agent Skills 标准（`SKILL.md` + 目录），可直接在 Claude Code 与 OpenAI Codex 中使用，目录名保持 `project-study` 即可：

### Claude Code

- 个人级（所有项目可用）：将本目录复制到 `~/.claude/skills/project-study/`
- 项目级（仅当前项目）：复制到项目内 `.claude/skills/project-study/`
- 无需额外配置，Claude Code 会在相关提问时自动发现并加载该技能

### OpenAI Codex

- 全局：将本目录复制到 `~/.agents/skills/project-study/`
- 项目级：复制到仓库内 `.agents/skills/project-study/`
- Codex 自 2025 年 12 月起支持 Skills，会在相关任务中自动读取 `SKILL.md`

### 多 Agent 共用同一份

若希望修改一处、多个 Agent 同时生效，可将技能放在 `~/.agents/skills/project-study/`，再为 Claude Code 创建目录链接：

- Windows（PowerShell，无需管理员权限）：
  `New-Item -ItemType Junction -Path "$HOME\.claude\skills\project-study" -Target "$HOME\.agents\skills\project-study"`
- macOS / Linux：
  `ln -s ~/.agents/skills/project-study ~/.claude/skills/project-study`
