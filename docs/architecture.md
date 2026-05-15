# Agent Harness 架构文档

## 架构目标

面鸭 interview agent 使用 Agent Harness 架构，将复杂面试训练流程拆解为多个可维护、可评估、可替换的 Agent 模块。

## 模块划分

### Planner Agent

输入：简历摘要、JD 摘要、岗位类型、候选人目标、语言偏好。

输出：面试路径、能力维度、问题类型、难度曲线、追问策略。

### Question Agent

输入：当前面试阶段、面试官风格、上一轮回答摘要、Planner 策略。

输出：当前问题、追问问题、问题意图、期望考察点。

### Evaluator Agent

输入：问题、用户回答、岗位 Rubric、历史表现摘要。

输出：评分、评分理由、风险标签、建议追问方向。

### Coach Agent

输入：评分结果、用户回答、问题意图、岗位要求。

输出：改进建议、回答模板、表达优化点、下一轮训练建议。

### Report Agent

输入：整场面试记录、逐题评分、风险标签、Coach 建议。

输出：面后报告、能力雷达、薄弱项分析、训练计划。

### TTS Module

输入：面试官问题、追问文本、语气风格。

输出：面试官语音播报资源。

## 调用流程

```text
Resume / JD
  -> Planner Agent
  -> Question Agent
  -> Candidate Answer
  -> Evaluator Agent
  -> Coach Agent
  -> Question Agent
  -> Report Agent
```

## 设计原则

- 模块职责清晰
- 输入输出结构化
- 支持逐步替换模型
- 支持日志记录与结果复盘
- 支持后续扩展 TTS、ASR 和多模态输入
