# 面鸭 interview agent

面鸭 interview agent 是一款面向求职训练场景的多模态 AI 面试 Agent 平台，面向产品经理、AI 产品经理、增长运营、数据分析师和技术转产品候选人，提供从简历 / JD 输入到多轮模拟面试、实时评分、TTS 语音播报和面后复盘报告的完整训练闭环。

项目当前处于原型开发阶段，已完成产品定位、核心流程设计、Agent Harness 架构草案、结构化评分协议和首版面试官角色模板设计。

## 在线页面

部署到 GitHub Pages 后，可通过以下地址访问：

```text
https://你的GitHub用户名.github.io/mianya-interview-agent/
```

## 项目介绍

面鸭Agent 将简历、JD、岗位能力矩阵、多轮追问、实时评分、TTS 语音播报和面后复盘报告整合为完整闭环，帮助候选人在接近真实面试的环境中持续训练。

平台不是一个简单的 AI 问答机器人，而是围绕真实求职训练场景设计的 Interview Agent Harness。系统会根据候选人的简历、目标 JD、岗位级别、目标公司和语言偏好，生成候选人画像、岗位能力矩阵、面试风险点和多轮面试路径，并通过多个 Agent 协作完成提问、追问、评分、反馈和报告生成。

## 核心功能

### 简历 / JD 解析

- 支持输入候选人简历、目标岗位 JD、岗位级别和目标公司信息
- 提取候选人的项目经历、能力标签、优势项和潜在短板
- 生成岗位能力矩阵和面试关注点
- 识别高风险问题，例如经历断层、项目深度不足、数据结果不清晰等

### 多轮 AI 模拟面试

- 支持 10–15 轮完整模拟面试链路
- 支持严厉型、友善型、压力型、Case 型、技术型和业务型等多种面试官风格
- 根据用户上一轮回答动态生成追问
- 支持中文、英文和中英混合面试

### 实时结构化评分

- 对每轮回答进行实时评分
- 按照岗位 Rubric 输出结构化评价
- 评分维度包括逻辑结构、业务判断、数据意识、表达清晰度、岗位匹配度等
- 输出改进建议和下一轮追问策略

### TTS 语音播报

- 将面试官问题和追问转为语音播报
- 提供更接近真实面试的交互体验
- 后续可扩展语音回答、语音转写和面试节奏控制

### 面后复盘报告

- 生成逐题评分和整体总结
- 输出能力雷达、薄弱项分析、表达问题和逻辑漏洞
- 提供可复用回答模板
- 生成下一阶段训练计划

## 目标用户

- 产品经理求职者
- AI 产品经理求职者
- 增长运营、用户运营、策略运营候选人
- 数据分析师、商业分析师候选人
- 技术转产品、技术转业务候选人
- 需要进行结构化面试训练的应届生和转岗人群

## 产品流程

```text
简历 / JD 输入
    ↓
候选人画像生成
    ↓
岗位能力矩阵构建
    ↓
面试路径规划
    ↓
多轮 AI 面试与动态追问
    ↓
实时评分与反馈
    ↓
TTS 语音播报
    ↓
面后复盘报告
    ↓
下一轮训练计划
```

## Agent Harness 架构

| 模块 | 职责 |
| --- | --- |
| Planner Agent | 根据简历、JD、岗位目标和候选人水平生成面试路径，决定能力维度、问题顺序和难度曲线 |
| Question Agent | 生成分阶段问题与动态追问，支持不同面试官风格和多语言面试 |
| Evaluator Agent | 基于结构化 Rubric 输出评分、理由、风险标签和改进建议 |
| Coach Agent | 将评分转化为可执行训练建议，包括 STAR 模板、数据分析路径和表达优化 |
| Report Agent | 汇总所有轮次评分，生成面后复盘报告、能力分析和训练计划 |
| TTS Module | 将面试官问题和追问语音化，构建更接近真实面试的交互体验 |

## 结构化评分协议

项目使用 JSON Schema 约束模型输出，提升系统可解析性和结果一致性。

```json
{
  "question": "请用 2 分钟说明：你如何判断一个 AI 产品功能是否值得投入研发？",
  "score": 82,
  "score_detail": {
    "logic": 82,
    "business_judgement": 76,
    "data_awareness": 68,
    "communication": 85
  },
  "reason": "回答覆盖了用户价值和研发成本，但缺少数据验证路径与风险评估。",
  "follow_up": "如果用户反馈很好，但 GPU 成本很高，你会如何设计灰度策略？",
  "suggestion": "建议补充目标用户规模、验证指标、成本阈值和灰度发布策略。",
  "tts_text": "下面我会继续追问一个成本控制相关的问题。",
  "risk_tag": ["数据意识不足", "成本评估不完整"],
  "next_action": "追问商业化和资源投入判断"
}
```

## 面试官风格

| 类型 | 描述 |
| --- | --- |
| 友善型 | 语气温和，适合新手训练和基础模拟 |
| 严厉型 | 强调逻辑漏洞和表达缺陷，适合强化训练 |
| 压力型 | 连续追问，模拟高压面试环境 |
| Case 型 | 通过业务案例考察分析能力 |
| 技术型 | 关注技术理解、系统设计和 AI 产品能力 |
| 业务型 | 关注商业判断、增长策略和资源投入产出 |

## 项目结构

```text
mianya-interview-agent/
├── index.html
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── product-design.md
│   ├── architecture.md
│   ├── scoring-schema.md
│   ├── interviewer-roles.md
│   ├── deployment.md
│   └── changelog.md
├── prompts/
│   ├── planner.md
│   ├── question-agent.md
│   ├── evaluator.md
│   ├── coach.md
│   └── report-agent.md
├── examples/
│   ├── sample-resume.md
│   ├── sample-jd.md
│   ├── sample-interview.json
│   └── sample-report.md
└── assets/
    └── screenshots/
```

## 当前项目状态

项目页与 README 更新日志已对齐，当前项目进展周期控制在 **2026.04.15 至 2026.05.09**。截至 2026.05.09，项目处于原型开发与模型接入准备阶段，已完成以下内容：

- 项目启动与产品方向确认
- 首版面试官角色模板设计
- 结构化评分协议设计
- Agent Harness 架构草案设计
- 产品定位与核心流程设计
- GitHub Pages 静态项目页设计

## 更新日志

### 2026.04.15｜项目启动

启动面鸭 interview agent 原型设计，确定以 AI 面试训练为核心方向，围绕简历、JD、岗位能力矩阵、多轮追问、实时评分和面后复盘构建完整闭环。

### 2026.04.26｜完成首版面试官角色模板

整理严厉型、友善型、压力型、Case 型、技术型和业务型面试官风格，并沉淀可复用 Prompt 模板与岗位 Rubric。

### 2026.05.03｜完成结构化评分协议

设计 JSON Schema 输出格式，覆盖 question、score、reason、follow_up、suggestion、tts_text、risk_tag 与 next_action 等字段。

### 2026.05.07｜完成 Agent Harness 架构草案

拆分 Planner、Question、Evaluator、Coach、Report 与 TTS 模块，定义各 Agent 的输入输出边界、调用顺序和异常回退策略。

### 2026.05.09｜完成产品定位与核心流程设计

明确“简历 / JD 输入 → 岗位画像 → 多轮 AI 面试 → 实时评分 → 面后报告”的完整训练闭环，并确定产品经理、AI 产品经理、运营和数据分析师作为首批目标岗位。

## README 与项目页进展校验

| 日期 | README 记录 | 项目页记录 | 状态 |
| --- | --- | --- | --- |
| 2026.04.15 | 项目启动 | 项目启动 | 已对齐 |
| 2026.04.26 | 完成首版面试官角色模板 | 完成首版面试官角色模板 | 已对齐 |
| 2026.05.03 | 完成结构化评分协议 | 完成结构化评分协议 | 已对齐 |
| 2026.05.07 | 完成 Agent Harness 架构草案 | 完成 Agent Harness 架构草案 | 已对齐 |
| 2026.05.09 | 完成产品定位与核心流程设计 | 完成产品定位与核心流程设计 | 已对齐 |

校验结论：当前项目页与 README 的项目进展一致，且所有日志时间均早于 2026.05.10。

## 本地预览

本项目当前为静态 HTML 页面，可直接在浏览器中打开：

```bash
open index.html
```

或使用任意静态服务器：

```bash
python3 -m http.server 3000
```

然后访问：

```text
http://localhost:3000
```

## GitHub Pages 部署

1. 创建 GitHub 仓库，例如 `mianya-interview-agent`。
2. 将本项目所有文件上传到仓库根目录。
3. 进入仓库的 `Settings` -> `Pages`。
4. 在 `Build and deployment` 中选择：

```text
Source: Deploy from a branch
Branch: main
Folder: /root
```

5. 保存后等待 GitHub Pages 自动部署。

## 联系项目

项目当前处于原型开发阶段，欢迎通过以下方式联系：

- Email: `zzrdezuiai@163.com`
- GitHub: `https://github.com/zzrdezuiai-tech/interview-agent`

请在正式部署前将以上联系方式替换为真实信息。
