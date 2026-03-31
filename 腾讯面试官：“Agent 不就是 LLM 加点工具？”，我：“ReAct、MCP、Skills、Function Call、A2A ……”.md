

大家好，我是小林。

今年，AI 圈子里最火的一个词，毫无疑问就是 **Agent（智能体）**。

打开技术社区，满屏都是 Agent，各大厂商发布会也都在讲 Agent，甚至连招聘 JD 上，都写着：

> 有 Agent 开发经验优先

很多同学反馈，大厂后端面试已经开始大量问 AI 相关问题，一堆概念直接砸过来。

本文整理了 Agent 高频面试题：

- LLM 和 Agent 有什么区别？
    
- Agent 和 Workflow 有什么区别？
    
- Agent 有什么工作模式？
    
- Function Call 是什么？
    
- MCP 是什么协议？
    
- Skills 是什么？
    
- Function Call / MCP / Skills 有什么区别？
    
- 什么是 A2A 协议？
    

---

# 一、LLM 和 Agent 的区别

## 1. 什么是 LLM？

LLM（Large Language Model，大语言模型）

👉 本质：**预测下一个词**

特点：

- 学习海量文本数据
    
- 能写作 / 编程 / 翻译 / 问答
    

代表：

- ChatGPT
    
- Claude
    
- DeepSeek
    
- 文心一言
    

---

## 2. LLM 的四大局限

### ❌ 1. 只会说，不会做

- 不能操作系统
    
- 不能执行任务
    

### ❌ 2. 没有长期记忆

- 仅限当前上下文
    

### ❌ 3. 不会用工具

- 不能查实时数据
    
- 容易产生幻觉
    

### ❌ 4. 不会规划

- 无法拆解复杂任务
    

---

## 3. 什么是 Agent？

👉 **Agent = LLM + 工具 + 循环决策**

核心特征：

- 有大脑（LLM）
    
- 能调用工具
    
- 能循环执行（思考 → 行动 → 观察）
    

---

## 4. Agent 的核心模块

一个完整 Agent = 4 个模块：

1. **LLM（大脑）**
    
2. **规划（Planning）**
    
3. **记忆（Memory）**
    
4. **工具（Tools）**
    

---

## 5. 对比总结

|能力|LLM|Agent|
|---|---|---|
|回答问题|✅|✅|
|调用工具|❌|✅|
|执行任务|❌|✅|
|长期记忆|❌|✅|
|任务规划|❌|✅|

👉 一句话总结：

> LLM 负责“说”，Agent 负责“做”

---

# 二、Agent vs Workflow

## 1. Workflow（工作流）

👉 **流程写死**

特点：

- 每一步 заранее定义
    
- 可控、稳定
    
- 低成本
    

---

## 2. Agent

👉 **目标驱动，自主决策**

特点：

- 动态规划
    
- 灵活
    
- 不确定性高
    

---

## 3. 核心区别

|维度|Workflow|Agent|
|---|---|---|
|控制权|代码|LLM|
|灵活性|低|高|
|成本|低|高|
|可预测性|强|弱|

---

## 4. 实际应用

👉 最常见：**混合架构**

```
Workflow 控主流程
   ↓
复杂节点 → Agent
```

---

# 三、Agent 工作模式

## 1. ReAct（边想边做）

循环：

```
Thought → Action → Observation → (循环)
```

优点：

- 灵活
    
- 可解释
    

缺点：

- token 消耗大
    
- 可能死循环
    

---

## 2. Plan-and-Execute（先计划再执行）

流程：

```
Plan → Execute
```

优点：

- 成本低（≈ ReAct 的 1/5）
    

缺点：

- 不够灵活
    

---

## 3. Reflection（反思机制）

两种方式：

- 自我反思
    
- 双 Agent Review
    

适合：

- 代码生成
    
- 法律文书
    
- 学术论文
    

---

## 4. Multi-Agent（多智能体）

多个 Agent 协作：

- 规划 Agent
    
- 执行 Agent
    
- 测试 Agent
    

⚠️ 不建议过早使用

---

# 四、Function Call

## 1. 定义

👉 **让 LLM 能调用函数（API）**

---

## 2. 工作流程

1. 定义函数（JSON）
    
2. LLM 判断是否调用
    
3. 程序执行函数
    
4. LLM 生成结果
    

---

## 3. 示例

```json
{
  "name": "get_weather",
  "parameters": {
    "city": "上海"
  }
}
```

---

## 4. 核心价值

解决两个问题：

- 调不调用？
    
- 参数是什么？
    

---

## 5. 与 Agent 关系

- Function Call = 原子操作
    
- Agent = 多次 Function Call 循环
    

---

# 五、MCP（模型上下文协议）

## 1. 定义

👉 **AI 世界的 USB-C 接口**

---

## 2. 解决问题

从：

```
N × M 集成
```

变成：

```
N + M
```

---

## 3. 架构

- MCP Host（AI 应用）
    
- MCP Client（中间层）
    
- MCP Server（工具服务）
    

---

## 4. 核心价值

- 工具统一接入
    
- 动态发现能力
    
- 标准化通信
    

---

# 六、Skills（技能）

## 1. 定义

👉 **用自然语言写的“操作手册”**

---

## 2. 本质

- 方法论
    
- 最佳实践
    
- 行为规范
    

---

## 3. 示例结构

```yaml
name: Code_Review
triggers:
  - "代码审查"
```

---

## 4. 类比

|概念|类比|
|---|---|
|MCP|厨房|
|Function Call|工具|
|Skills|菜谱|

---

# 七、三者关系总结

|维度|Function Call|MCP|Skills|
|---|---|---|---|
|本质|API 调用|协议|Prompt|
|作用|调工具|管工具|教方法|
|层级|底层|中层|高层|

---

# 八、A2A 协议

## 1. 定义

👉 Agent-to-Agent 通信协议（Google 提出）

---

## 2. 解决问题

- Agent 之间协作
    

---

## 3. 核心概念

### Agent Card

- 能力描述（类似简历）
    

### Task

- 任务生命周期
    

### Message / Artifact

- 消息 / 结果
    

---

## 4. MCP vs A2A

|协议|作用|
|---|---|
|MCP|Agent → 工具|
|A2A|Agent → Agent|

---

## 5. 技术特点

- HTTP + JSON
    
- 支持异步任务
    
- 支持多模态
    

---

# 九、全文总结

👉 Agent 技术体系三层：

```
Function Call（能力层）
        ↓
MCP（连接层）
        ↓
Skills（知识层）
        ↓
A2A（协作层）
```

---

# 📌 一句话总结

> LLM 是大脑，Function Call 是手，MCP 是接口，Skills 是经验，A2A 是团队协作

---

如果你需要，我可以帮你再做一版👇：

- ✅ 面试速记版（1页总结）
    
- ✅ 思维导图版本
    
- ✅ PPT版本（答辩/分享用）
    
- ✅ 加图解版（更容易记）
    

直接说你要哪种 👍