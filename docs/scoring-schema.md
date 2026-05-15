# 结构化评分协议

## 设计目标

结构化评分协议用于约束 AI Agent 输出，使前端或后端可以稳定解析问题、评分、追问和建议。

## JSON Schema 示例

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

## 字段说明

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| question | string | 当前面试问题 |
| score | number | 总分，0-100 |
| score_detail | object | 分维度评分 |
| reason | string | 评分理由 |
| follow_up | string | 下一轮追问 |
| suggestion | string | 改进建议 |
| tts_text | string | 用于语音播报的文本 |
| risk_tag | array | 风险标签 |
| next_action | string | 下一步面试策略 |

## 评分维度

- 逻辑结构
- 业务判断
- 数据意识
- 表达清晰度
- 岗位匹配度
- 用户价值理解
- 资源投入判断
