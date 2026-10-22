# 关键词表与指标词典

## 1. 三层级岗位划分（先定位，再选词）

| 层级 | JD 典型描述 | 简历表达重心 | 硬筛选关键词 |
|---|---|---|---|
| 应用接入型 | 基于 LangChain/LlamaIndex 搭建助手后端，接入内部知识库与 API | 业务串联速度、协议/中间件实名（具体协议名不写会被筛掉） | LangChain/LlamaIndex、Function Calling、RAG、向量数据库、FastAPI |
| 框架研发型 | 主导规划、记忆、自反思模块设计，RAG 召回量化提升 | Agent 模块设计与范式取舍（ReAct vs Plan-Execute）、源码级理解 | ReAct、Plan-Execute、Memory、Tool Registry、LangGraph |
| Agent Infra / Runtime 型 | Runtime、任务编排、沙箱、执行链路治理、评测体系 | 运行时与执行链路：可靠性、失败路径、评测、成本、调度 | 见第 2 节关键词表 |

- 「必须命中」关键词：JD 里出现的硬筛选词，简历里没有就直接被滤掉。
- 「加分表达」：拉开差距的地方，如「多 Agent 并发调度」「工具调用失败后的自我纠错」「基于缓存的重复请求推理加速」。
- 一份简历只对齐一个层级；三层混写会被认为哪个都不深。
- 用目标 JD 做关键词回查，核心词至少命中 4 个；拼写与 JD 逐字一致（LangGraph ≠ Langgraph，LangChain ≠ Langchain）。

## 2. Agent Infra / Runtime 关键词表（按 JD 出现频率分组）

- 运行时与执行：Agent Runtime、Sandbox（microVM / E2B）、Code Interpreter、Session 隔离、冷启动、快照恢复
- 编排与状态：Harness、任务编排、State 管理、Checkpoint、Interrupt/Resume、Human-in-the-loop、失败重试与幂等
- 上下文与记忆：Context 管理、短期/长期 Memory、压缩与检索、多模态通信链路
- 工具生态：Tool Registry、动态加载、MCP Server、Schema 校验、权限与审计、限流超时
- 质量与成本：轨迹级评测（Trajectory Eval）、Golden Dataset、回归、Trace / 可观测性、Token 成本与配额、并发调度与利用率

大厂 JD 补充词（用于 Infra 岗对齐）：Harness Engineering、Agent 框架、沙箱与模拟环境、个性化记忆、工具/Skills、自动评估体系、GPU 调度与利用率、任务完成率、pass@k、评测一致性、区分度、根因分析。

## 3. 指标词典（中英对照，量化时按口径取词）

| 中文 | 英文 | 用法 / 口径 |
|---|---|---|
| 任务完成率 | task completion rate / end-to-end task success rate | Agent 岗第一指标，注明测试集规模与来源 |
| pass@k | pass@k | 生成式/评测类任务，k 次尝试至少一次成功 |
| 工具调用成功率 | tool-call success rate | 分母为总调用次数，注明是否含重试 |
| 工具参数错误率 | tool-argument error rate | Schema 校验失败占比 |
| 平均调用链长度 | median tool calls per run | 每次任务的工具调用步数中位数 |
| 人工升级率 / 兜底率 | human escalation rate / handoff rate | 越低越好，与自动解决率互补 |
| 自动应答率 / 自主解决率 | autonomous resolution rate | 分母为总咨询量 |
| p95 延迟 | p95 latency | 服务级指标，附时间窗口 |
| 首 token 延迟 | p95 TTFT (time to first token) | 推理方向头部指标 |
| 吞吐 | tokens/s | 推理方向，注明 batch 与精度 |
| 单任务成本 | cost per task / cost per successful task | 成本优化的落点 |
| 每百万 token 成本 | cost per 1M tokens | 降本项注明质量不退化 |
| 沙箱冷启动 | sandbox cold start | Runtime 岗硬指标 |
| 单机实例密度 | instance density | 沙箱/调度方向 |
| GPU 利用率 | GPU utilization | Infra/推理方向 |
| 检索准确率 | Top-K hit rate / NDCG@10 | RAG 项必写 |
| 答案采纳率 | answer adoption rate | RAG 的业务口径 |
| 评测一致性 / 区分度 | eval consistency / discriminative power | 评测体系专业词，敢写很加分 |
| 轨迹级评测 | trajectory eval | 区别于单步打分 |
| 用户满意度 | CSAT | 5 分制注明样本量 |

原则：量化必须带「质量不退化」前提（如「p95 延迟降 40%，评测集通过率持平」）；每个数字都能解释怎么测的（测试集、基线、时间窗口）。

## 4. 英文 bullet 句式库

强 bullet 公式：**强动词过去式 + 交付物 + 规模（N tools/agents/docs）+ 机制（how）+ 指标（rate across N runs）+ 对比基线（vs X on a controlled comparison）**。

范式示例（数字为句式示意，用真实数据替换）：

- Built and shipped a Claude-based agent with 6 internal tools (ticket lookup, refund, escalation, KB search, email, audit log); median 3.2 tool calls per run, 94% task completion across 4,200 production runs in Q1, and a 31% reduction in median ticket resolution time vs the human-only baseline on a stratified 800-ticket A/B.
- Designed and deployed a multi-agent support system (triage / billing / technical / escalation) handling 50K tickets/month with an 87% autonomous resolution rate.
- Implemented a RAG pipeline with hybrid search and rerank, improving answer accuracy from 64% to 91% across 12K internal documents.

弱 bullet（不要这样写）与替换：

| 弱写法 | 问题 | 替换方向 |
|---|---|---|
| Built an AI agent using LangGraph. | 无指标，像黑客松海报 | 补 end-to-end success rate、tool-argument error rate、cost per successful task |
| Responsible for prompt engineering. | 无产出 | 换成 eval delta（“raising faithfulness score from X to Y on a 500-case golden set”） |
| Improved system performance. | 不可验证 | 补 p95 / tokens/s / cost per 1M tokens + quality guardrail |

铁律：**每处改动都连着一个 eval delta 或 cost delta**（roasted.cv 口径）；以生产口吻开头的动词（shipped / built and run / designed and deployed）比 study / familiar with 可信。

## 5. 量化缺数字时的替代方案（保持真实的前提下）

1. 自建小规模测试集并报告口径：「在自建 150 条对话测试集上，任务完成率 76%」
2. 压测 / 成本估算：本地压测并发数、按 API 定价估算单任务成本
3. 对比基线：改前 vs 改后在同一测试集上的差异
4. 开源可核验数据：仓库 stars、issue 修复数、文档字数与篇数（如实写）
5. 严禁：编造业务数字、照抄模板数字、把估算写成实测（估算就注明「估算」）
