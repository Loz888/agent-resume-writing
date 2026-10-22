# agent-resume-writing

一个用于生成 / 改写 **AI Agent、Agent Infra、LLM 应用** 方向简历文本的 Trae Skill。产出纯文本简历内容（项目经历、技能栏、自我评价），不含排版与文件导出。

## 适用场景

- 把粗线条的项目经历改写成能扛住面试追问的简历条目
- 按目标 JD（Agent Infra / Runtime、Agent 框架研发、LLM 应用开发）定制关键词与侧重点
- 补齐量化指标、失败路径、评测与诚实边界
- 自测项目能否回答「做了什么 / 为什么这么选 / 重做会改什么」三层追问

## 安装

把本目录放到 Trae 的 skills 目录：

```text
~/.trae-cn/skills/agent-resume-writing/     # CN 版
~/.trae/skills/agent-resume-writing/        # 国际版
```

或作为项目级 skill 放到 `<repo>/.trae/skills/agent-resume-writing/`。

## 文件结构

```text
SKILL.md                              工作流、硬性写作规则、输出格式
references/frameworks-and-examples.md 四段式、Agent 四要素、5 类表达正反例、写法禁忌
references/keywords-and-metrics.md    三层级岗位关键词、Infra 关键词表、中英指标词典、英文 bullet 句式
references/project-templates.md       6 类项目骨架、技能栏与自我评价模板、投递前检查清单
references/interview-defense.md       三层追问自测、失败兜底四层拆解、30/60 秒口述框架
```

## 核心规则（摘要）

- 每个数字都要能说出怎么测的；没有数字就用小规模真实测量替代，不编造
- 每段经历按「场景与约束 → 你负责的那一层 → 关键决策与取舍 → 可核验指标」组织
- 至少一条写失败路径，至少一条写评测 / 回归
- 项目性质如实标注（生产 / 内部 / 课程 / 原型），不把 Demo 写成生产
- 技能栏只留 6-8 个与 JD 逐字一致的关键词，其余能力在项目里当证据

## 素材来源

整理自以下公开资料（方法论与句式，不含任何模板示例数字）：

- [AI Agent 岗位简历模板（牛客）](https://www.nowcoder.com/discuss/912309942026002432)
- [从"功能实现"到"问题解决"：如何描述 Agent 项目](https://devpress.csdn.net/v1/article/detail/154840184)
- [AI 助手开发岗简历怎么写：从 Agent 项目到工具调用](https://hicv.cn/blog/ai-resume-agent)
- [2026 AI Agent 工程师简历：JD 高频 5 类项目经验表达](https://m.zhizuobiao.com/interview/interview-26091600003/)
- [AI Agent Engineer Resume: Examples and Templates (2026)](https://agenticcareers.co/blog/ai-agent-engineer-resume-examples-2026)
- [Junior Agentic AI Engineer Resume Example](https://roasted.cv/p/agentic-ai-engineer/junior)
- [AI Engineer Resume Examples 2026](https://www.rejectless.app/ai-engineer-resume-examples)

## License

MIT
