# AGENTS.md

## Project Scope

本仓库用于维护两类古典音乐分析提示体系及其 skill 化版本：

- 圆桌会议讨论
- 录音版本比较

仓库里的核心资产有两类：

- 原始提示词：`prompt.md`
- 可触发的 skill：
  - `skills/roundtable-seminar/SKILL.md`
  - `skills/recording-version-comparison/SKILL.md`

另有示例输出文档：

- `会议记录/2026-03-06-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md`
- `会议记录/2026-03-06-萨瓦利什与塞尔舒曼第一交响曲对比导聆记录.md`
- `会议记录/2026-03-06-舒曼第二交响曲详细导聆记录.md`

## Primary Skill

本项目当前最重要的 skill 有两个：

- `roundtable-seminar`
  路径：`skills/roundtable-seminar/SKILL.md`
- `recording-version-comparison`
  路径：`skills/recording-version-comparison/SKILL.md`

当用户请求明显符合其中某个 skill 时，优先使用它，而不是临时重新发明一套结构。

## Trigger Rules

以下情况优先触发 `roundtable-seminar`：

- 用户明确使用 `圆桌会议讨论xxxx` 这类句式
- 用户明确说要“圆桌会议讨论”
- 用户要求主持人引导、多人物交锋、逐轮总结、ASCII 框架
- 用户在同一轮中继续使用以下控制指令：
  - `可`
  - `止`
  - `深入此节`
  - `引入新人物`

如果用户只是要普通说明文、普通分析或普通摘要，不要强行套用该 skill。

以下情况优先触发 `recording-version-comparison`：

- 用户明确说 `比较 xx 和 xx 的某个曲子的版本区别`
- 用户明确说要“版本比较”“录音版本对比”“唱片比较”
- 用户要求“逐乐章拆开”
- 用户要求“保留每个乐章聆听要点”
- 用户要求“用某个版本做时间轴”

如果用户只是要普通作品介绍、普通导聆或普通摘要，不要强行套用该 skill。

## Working Rules

处理本仓库内容时，遵守以下约束：

1. 修改 skill 时，优先更新 `skills/roundtable-seminar/SKILL.md`，不要只改 `prompt.md`。
2. 如果 `prompt.md` 与 `SKILL.md` 出现不一致，以 `SKILL.md` 为当前可执行版本。
3. 处理版本比较 skill 时，优先更新 `skills/recording-version-comparison/SKILL.md`，不要只在示例文档里隐含规则。
4. 如果用户要求“整理成文档”，先分清是：
   - 纪要
   - 完整记录
   - transcript / 完整实录
5. 如果用户指出“不是纪要，是完整记录”，输出时必须保留过程、主持人串场与人物交锋。
6. 圆桌内容必须让人物相互回应，不能只写成并列观点摘要。
7. ASCII 图是结构工具，不是装饰。每轮总结都应围绕核心争议生成。
8. 所有会议记录统一放在 `会议记录/` 目录下，不要散落在仓库根目录。
9. 会议记录文件名必须以日期开头，格式为 `YYYY-MM-DD-中文主题名.md`。
10. 会议记录文件名优先使用中文，不使用英文 slug，除非用户明确要求英文。
11. 只要用户要求“整理会议记录”“保存会议记录”“导出会议记录”，默认就使用完整记录 / transcript 风格，而不是纪要。
12. 只有用户明确要求“纪要”“摘要”“压缩版”时，才允许改写成纪要。
13. transcript 风格记录应尽量按 `Turn 1`、`Turn 2` 这种逐回合方式整理。
14. transcript 风格记录必须显式保留：
    - 用户指令
    - 主持人每次推进与提示
    - 嘉宾署名发言与回应关系
    - ASCII 框架
    - 中断后继续的说明（如果发生）
15. 除非用户明确要求压缩，不要把多轮圆桌讨论整理成只剩结论的纪要。
16. 版本比较文档默认应保留：
    - 版本基准
    - 各乐章时长
    - 每个乐章的独立比较
    - 每个乐章的聆听要点
    - 如果用户要求，则保留版本 A 时间轴
17. `recording-version-comparison` 一旦被触发，默认就按完整导聆记录文档落地到 `会议记录/`，除非用户明确说不要保存。

## Editing Guidance

新增或修改与 skill 相关的内容时：

- 优先保持中文说明
- 触发词写明确，不要模糊
- 人物名称、控制指令、主持人口吻要稳定
- 如果变更了触发词，也要同步更新 README 和本文件
- 如果整理会议记录，优先保留对话推进链条，而不是优先追求篇幅短

## Files To Check First

处理与本项目有关的请求时，优先查看以下文件：

1. `skills/roundtable-seminar/SKILL.md`
2. `skills/recording-version-comparison/SKILL.md`
3. `README.md`
4. `prompt.md`
5. `会议记录/2026-03-06-富特文格勒战后与维也纳爱乐贝多芬第五交响曲圆桌讨论完整记录.md`
6. `会议记录/2026-03-06-萨瓦利什与塞尔舒曼第一交响曲对比导聆记录.md`
7. `会议记录/2026-03-06-舒曼第二交响曲详细导聆记录.md`

## Expected Output Style For This Repo

如果本仓库的 `roundtable-seminar` skill 被触发，默认输出应符合以下风格：

- 主持人先开场并定义议题
- 明确列出参与人物
- 每位人物署名发言
- 人物之间有直接回应
- 每轮结束有主持人总结
- 每轮总结后附 ASCII 框架
- 最后提示控制指令或输出收束总结

如果本仓库的 `recording-version-comparison` skill 被触发，默认输出应符合以下风格：

- 先列出比较版本与乐章时长
- 先给整体美学分野
- 每个乐章必须单独拆开比较
- 每个乐章必须保留聆听要点
- 如果适合，按版本 A 时间轴逐段对照
- 最后给综合判断，而不是只做中性并列描述
- 默认直接保存为 `会议记录/` 下的 md 文档
