# listening-furtwangler

本项目用于沉淀一套可复用的“圆桌会议讨论”提示框架，并保存围绕富特文格勒与贝多芬《第五交响曲》的示例讨论记录。

当前仓库既包含原始 prompt，也包含已经转换好的 Codex skill。

## 来源说明

本项目中的 [prompt.md](/Users/guochunyang/anzo/listening-furtwangler/prompt.md) 参考了李继刚公开分享的这份 gist：

- https://gist.github.com/lijigang/a8f9cf12985d474cef15cda63f4e1892

本仓库在此基础上做了适配与整理，包括：

- 转写为本地 `prompt.md`
- 转换为 `skills/roundtable-seminar/SKILL.md`
- 补充会议记录规范与 transcript 整理规范

## 项目内容

- [prompt.md](/Users/guochunyang/anzo/listening-furtwangler/prompt.md)
  原始指令稿，保留最初的提示词结构。

- [skills/roundtable-seminar/SKILL.md](/Users/guochunyang/anzo/listening-furtwangler/skills/roundtable-seminar/SKILL.md)
  已整理为可直接使用的 skill 版本，适用于 Codex / skills 体系。

- [会议记录/2026-03-06-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md](/Users/guochunyang/anzo/listening-furtwangler/会议记录/2026-03-06-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md)
  围绕“富特文格勒战后与维也纳爱乐《贝多芬第五交响曲》如何聆听”的完整圆桌讨论记录。

## Skill 说明

本仓库当前内置 1 个 skill：

### `roundtable-seminar`

位置：

- [skills/roundtable-seminar/SKILL.md](/Users/guochunyang/anzo/listening-furtwangler/skills/roundtable-seminar/SKILL.md)

用途：

- 将一个复杂议题组织成主持人引导下的多人物圆桌会议讨论
- 强调“求真”导向，而不是普通并列观点
- 支持逐轮推进、引入新人物、ASCII 框架总结、会议记录导出

推荐触发词：

- `圆桌会议讨论人工智能是否拥有真正的创造力`
- `圆桌会议讨论富特文格勒的贝五应该怎么听`
- `圆桌会议讨论教育的目标应是选拔还是塑造`

该 skill 当前优先按以下模式触发：

- 用户明确使用 `圆桌会议讨论xxxx`
- 用户明确要求使用“圆桌会议讨论”框架

## 使用方式

如果你在支持 skills 的环境中使用本项目，建议直接用“圆桌会议讨论”作为入口句式，例如：

```text
圆桌会议讨论富特文格勒战后与维也纳爱乐的贝多芬第五交响曲如何聆听
```

讨论过程中支持以下控制指令：

- `可`
- `止`
- `深入此节`
- `引入新人物`

## 输出风格

该 skill 设计目标不是普通问答，而是：

- 主持人明确控场
- 发言人姓名完整、立场清晰
- 发言人之间必须互相回应
- 每轮都要提炼核心争议
- 每轮都要输出 ASCII 结构图
- 最终可整理成纪要、完整记录或 transcript

## 会议记录规范

所有会议记录统一存放在 `会议记录/` 目录下，并遵守以下命名规则：

- 文件名必须以日期开头
- 日期格式统一为 `YYYY-MM-DD`
- 日期后接中文主题名
- 文件名整体使用中文，不再使用英文 slug

推荐格式：

```text
会议记录/YYYY-MM-DD-中文主题名.md
```

例如：

```text
会议记录/2026-03-06-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md
```

## 仓库结构

```text
.
├── README.md
├── AGENTS.md
├── prompt.md
├── 会议记录/
│   └── 2026-03-06-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md
└── skills/
    └── roundtable-seminar/
        └── SKILL.md
```

## 后续可扩展方向

- 为 `roundtable-seminar` 增加 `agents/openai.yaml`
- 增加更多圆桌讨论示例文档
- 将不同主题的圆桌记录拆分为独立案例库
