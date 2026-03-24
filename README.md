# Smart-Travel-Agent: 基于 ReAct 架构的智能旅行助手 (设计与规划中)

![Status](https://img.shields.io/badge/Status-In--Planning-yellow)
![Pattern](https://img.shields.io/badge/Pattern-ReAct-green)
![Target](https://img.shields.io/badge/Target-Agent--Infrastructure-blue)

本项目目前处于**架构设计与原型规划阶段**。旨在通过对 Datawhale `hello-agents` 课程体系的深入研究，脱离成熟框架（如 LangChain），从底层逻辑出发构建一个具备自主推理与任务执行能力的智能体原型。

## 🎯 设计目标

本项目旨在探索大模型在处理**多约束条件（预算、时序、偏好）**下的复杂任务规划能力。通过手写 Agent 核心循环，掌握模型如何通过 Prompt 状态机实现从“语义理解”到“工具执行”的跨越。

## 🏗️ 架构设计 (System Architecture)

虽然代码尚未完全实现，但系统将遵循以下模块化设计方案：

### 1. 核心推理引擎 (Agent Core)
- **ReAct 循环：** 拟采用 `while` 循环结构，实现标准的 `Thought -> Action -> Observation` 闭环。
- **输出解析器 (Parser)：** 设计一套基于正则表达式或 JSON 校验的解析机制，将 LLM 的文本输出转化为可执行的 Python 指令。
- **状态追踪：** 使用轻量级字典结构维护对话历史与工具执行轨迹，作为模型的“短期记忆”。

### 2. 工具集成方案 (Tool Integration)
计划封装以下三类核心工具接口：
- **搜索服务：** 对接 Tavily/Serper API 获取实时旅行资讯。
- **地理信息：** 模拟高德/Google Maps 接口进行路径规划。
- **交易模拟：** 模拟酒店、餐厅的预订逻辑，验证 Agent 的闭环操作能力。

### 3. 提示词工程 (Prompt Engineering)
- 采用 **Few-shot Prompting** 引导模型掌握特定的思考格式。
- 设计特定的 **System Role**，强化模型对预算和时间约束的敏感度。

## 📂 规划中的项目结构

```text
Smart-Travel-Agent/
├── docs/                # 设计文档与架构图
├── agent/               # [待开发] 核心推理逻辑与解析器
├── tools/               # [待开发] 工具定义与模拟接口
├── tests/               # [待开发] 测试用例
└── README.md
