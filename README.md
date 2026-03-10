# listening-furtwangler

本项目用于沉淀两类可复用的古典音乐分析 skill：

- “圆桌会议讨论”提示框架
- “录音版本比较”分析框架

当前仓库既包含原始 prompt，也包含已经转换好的 Codex skill。

## 来源说明

本项目中的 [prompt.md](/Users/guochunyang/anzo/listening-furtwangler/prompt.md) 参考了李继刚公开分享的这份 gist：

- https://gist.github.com/lijigang/a8f9cf12985d474cef15cda63f4e1892

本仓库在此基础上做了适配与整理，包括：

- 转写为本地 `prompt.md`
- 转换为 `skills/roundtable-seminar/SKILL.md`
- 新增 `skills/recording-version-comparison/SKILL.md`
- 补充会议记录规范、transcript 整理规范与版本比较导聆规范

## 项目内容

- [prompt.md](/Users/guochunyang/anzo/listening-furtwangler/prompt.md)
  原始指令稿，保留最初的提示词结构。

- [skills/roundtable-seminar/SKILL.md](/Users/guochunyang/anzo/listening-furtwangler/skills/roundtable-seminar/SKILL.md)
  已整理为可直接使用的 skill 版本，适用于 Codex / skills 体系。

- [skills/recording-version-comparison/SKILL.md](/Users/guochunyang/anzo/listening-furtwangler/skills/recording-version-comparison/SKILL.md)
  用于比较两个或多个古典音乐录音版本，强调逐乐章拆开比较、保留每个乐章聆听要点，并可按版本 A 时间轴输出详细导聆记录。

- [会议记录/2026-03-06-02-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md](/Users/guochunyang/anzo/listening-furtwangler/会议记录/2026-03-06-02-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md)
  围绕“富特文格勒战后与维也纳爱乐《贝多芬第五交响曲》如何聆听”的完整圆桌讨论记录。

- [会议记录/2026-03-06-04-舒曼第二交响曲详细导聆记录.md](/Users/guochunyang/anzo/listening-furtwangler/会议记录/2026-03-06-04-舒曼第二交响曲详细导聆记录.md)
  以 Sawallisch 与 Szell 为基准，对舒曼《第二交响曲》做逐乐章、带时间轴的详细版本比较记录。

## Skill 说明

本仓库当前内置 2 个 skill：

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

### `recording-version-comparison`

位置：

- [skills/recording-version-comparison/SKILL.md](/Users/guochunyang/anzo/listening-furtwangler/skills/recording-version-comparison/SKILL.md)

用途：

- 比较两个或多个古典音乐录音版本
- 保留作品本体聆听主线，再拆到每个乐章逐段比较
- 支持以版本 A 为时间轴基准输出详细对照导聆文档
- skill 一旦触发，默认就按完整导聆记录文档落地到 `会议记录/`

推荐触发词：

- `比较萨瓦利什和塞尔的舒曼第二交响曲版本区别`
- `比较富特文格勒和托斯卡尼尼的贝多芬第五交响曲版本区别`
- `这两个指挥这首曲子怎么不同，逐乐章拆开说`

该 skill 当前优先按以下模式触发：

- 用户明确说“比较 xx 和 xx 的某个曲子的版本区别”
- 用户明确要求“版本比较”“录音版本对比”“唱片比较”
- 用户要求“逐乐章拆开”“保留每个乐章聆听要点”“用某个版本作为时间轴”

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

如果你要触发“录音版本比较” skill，建议直接用类似句式：

```text
比较萨瓦利什和塞尔的舒曼第二交响曲版本区别
```

或者：

```text
比较富特文格勒和托斯卡尼尼的贝多芬第五交响曲版本区别，逐乐章拆开，用富特文格勒版做时间轴
```

## 输出风格

`roundtable-seminar` 的设计目标不是普通问答，而是：

- 主持人明确控场
- 发言人姓名完整、立场清晰
- 发言人之间必须互相回应
- 每轮都要提炼核心争议
- 每轮都要输出 ASCII 结构图
- 最终可整理成纪要、完整记录或 transcript

`recording-version-comparison` 的设计目标则是：

- 先给版本基准与总体美学分野
- 每个乐章单独拆开比较
- 每个乐章都保留聆听要点
- 每个乐章尽量落到具体乐器、句子、动机与段落功能，而不是只写抽象形容词
- 必要时以版本 A 作为时间轴逐段对照
- 最后给出综合判断、适合人群与推荐听法
- 默认直接整理成 md 文档，而不是只给聊天体回答

## 会议记录规范

所有会议记录统一存放在 `会议记录/` 目录下，并遵守以下命名规则：

- 标题下必须先写：
  - `作者模型`
  - `模型版本`
  - `写作时间`
- 默认写法为：
  - `作者模型：Codex`
  - `模型版本：GPT-5`
- 文件名必须以日期开头
- 日期格式统一为 `YYYY-MM-DD`
- 日期后必须紧跟两位编号，例如 `01`、`02`
- 编号后接中文主题名
- 文件名整体使用中文，不再使用英文 slug

推荐格式：

```text
会议记录/YYYY-MM-DD-编号-中文主题名.md
```

例如：

```text
会议记录/2026-03-06-02-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md
```

以及：

```text
会议记录/2026-03-06-03-萨瓦利什与塞尔舒曼第一交响曲对比导聆记录.md
会议记录/2026-03-06-04-舒曼第二交响曲详细导聆记录.md
```

## 仓库结构

```text
.
├── README.md
├── AGENTS.md
├── prompt.md
├── skills/
│   ├── recording-version-comparison/
│   │   └── SKILL.md
│   └── roundtable-seminar/
│       └── SKILL.md
├── 会议记录/
│   ├── 2026-03-06-01-如何评价指挥家尼尔森斯圆桌讨论完整记录.md
│   ├── 2026-03-06-02-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md
│   ├── 2026-03-06-03-萨瓦利什与塞尔舒曼第一交响曲对比导聆记录.md
│   ├── 2026-03-06-04-舒曼第二交响曲详细导聆记录.md
│   └── 2026-03-06-05-富特文格勒战后维也纳与卡拉扬1963DG贝多芬第五交响曲版本对比导聆记录.md
```

## 后续可扩展方向

- 为 `roundtable-seminar` 增加 `agents/openai.yaml`
- 为 `recording-version-comparison` 增加 `agents/openai.yaml`
- 增加更多圆桌讨论示例文档
- 增加更多版本比较示例文档
- 将不同主题的圆桌记录拆分为独立案例库
