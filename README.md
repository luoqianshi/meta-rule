# meta-rule

这是一套个人代码仓库的起步约定，用来统一项目说明、Agent 工作规则、开发记录和发版习惯。可以从新仓库开始采用，也可以逐步合并到已有项目。

## 应用到项目

1. 新仓库从下表复制基础文件到项目根目录。已有仓库逐份对照，把需要的条目合并进现有文件。
2. 在 README 填写项目用途和快速开始步骤，在 AGENTS 填写该项目实际可运行的验证命令、目录约定和交付流程。
3. 根据项目技术栈调整忽略规则和编辑器配置。项目有了相应的规划、工作记录或发版需求时，再复制对应的文档模板。

| 模板 | 目标路径 | 用途 |
| --- | --- | --- |
| [README](templates/README.md) | `README.md` | 说明项目用途、使用方式和关键目录。 |
| [AGENTS](templates/AGENTS.md) | `AGENTS.md` | 说明 Agent 如何在项目里工作和验证改动。 |
| [Git 忽略规则](templates/.gitignore) | `.gitignore` | 忽略系统杂项、本地环境变量文件和 Agent 任务临时目录。 |
| [EditorConfig](templates/.editorconfig) | `.editorconfig` | 提供编码、缩进和行尾的默认设置。 |
| [工作日志](templates/LOG.md) | `LOG.md` | 需要追溯重要工作时，按时间倒序记录改动、原因和验证结果。 |
| [发版记录](templates/CHANGELOG.md) | `CHANGELOG.md` | 开始维护版本时，记录用户可感知的变化和升级说明。 |
| [PRD](templates/docs/prd/TEMPLATE.md) | `docs/prd/0001-主题.md` | 开始规划较大的需求时，明确范围和验收标准。 |

如果项目已有 `VERSION.md` 作为发版记录，可沿用原名，也可迁移到 `CHANGELOG.md`。保留一份发版说明，发布时用 Git tag 对应具体提交。

## 日常维护

- **规划较大的需求**时，先写 PRD。原型验证导致范围变化时，更新 PRD，再按确认后的标准实现和验收。
- **完成重要改动**时，在 `LOG.md` 留一条记录。影响安装、使用或验证方式时，同时更新 README。
- **准备发版**时，先将用户可感知的变化记在 `CHANGELOG.md` 的 `Unreleased` 小节。正式发布时整理为带版本号和发布日期的条目，并标明兼容性变化和迁移步骤。

## Agent 的工作目录

- **只讨论或规划**时，优先使用工具的只读权限，方案默认留在对话中。
- **需要试跑写文件的插件**时，从规划开始使用独立 Git worktree，并预先约定输出位置。必须在工作树内落盘的临时文件放在 `.agent-tmp/`，只将审查过的改动合入目标分支。
- **管理工具配置**时，按需提交项目共享配置。仅供本机使用的文件按具体路径加入 `.git/info/exclude` 或 Git 的全局忽略文件。

详细的执行与检查要求见本仓库的 [AGENTS.md](AGENTS.md)。已有项目可以把模板的「临时产物与仓库结构」一节连同 `/.agent-tmp/` 忽略项合并到自己的配置中。

## 维护这套模板

本仓库的 [AGENTS.md](AGENTS.md) 说明如何维护模板，[首版 PRD](docs/prd/0001-initial-template.md) 记录设计范围，[LOG.md](LOG.md) 和 [CHANGELOG.md](CHANGELOG.md) 分别记录工作过程和版本变更。其他项目应从 `templates/` 取文件。

模板更新后，已有项目可以对照变更手动合并。个人通用的 Codex 偏好可放在 `~/.codex/AGENTS.md`，各项目的工作命令和边界由项目自己的 `AGENTS.md` 记录。[Codex 的 AGENTS.md 指南](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
