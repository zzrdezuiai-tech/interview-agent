# 更新日志

## 2026.04.15｜项目启动

启动面鸭 interview agent 原型设计，确定以 AI 面试训练为核心方向，围绕简历、JD、岗位能力矩阵、多轮追问、实时评分和面后复盘构建完整闭环。

## 2026.04.26｜完成首版面试官角色模板

整理严厉型、友善型、压力型、Case 型、技术型和业务型面试官风格，并沉淀可复用 Prompt 模板与岗位 Rubric。

## 2026.05.03｜完成结构化评分协议

设计 JSON Schema 输出格式，覆盖 question、score、reason、follow_up、suggestion、tts_text、risk_tag 与 next_action 等字段。

## 2026.05.07｜完成 Agent Harness 架构草案

拆分 Planner、Question、Evaluator、Coach、Report 与 TTS 模块，定义各 Agent 的输入输出边界、调用顺序和异常回退策略。

## 2026.05.09｜完成产品定位与核心流程设计

明确“简历 / JD 输入 → 岗位画像 → 多轮 AI 面试 → 实时评分 → 面后报告”的完整训练闭环，并确定产品经理、AI 产品经理、运营和数据分析师作为首批目标岗位。
