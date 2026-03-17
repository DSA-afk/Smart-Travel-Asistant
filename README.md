# Smart-Travel-Asistant
# Smart-Travel-Agent: 基于 ReAct 架构的自研智能旅行助手

![Python Version](https://img.shields.io/badge/python-3.10%2B-blue)
![Framework](https://img.shields.io/badge/Framework-Self--Developed-orange)
![Agent Pattern](https://img.shields.io/badge/Pattern-ReAct-green)

本项目是基于 Datawhale `hello-agents` 开源课程体系开发的实战项目。其核心目标是脱离 LangChain 等高层封装框架，通过原生的 Python 逻辑从零构建一个具备 **推理 (Reasoning)** 与 **行动 (Acting)** 能力的智能体。

## 🌟 项目亮点

- **零框架依赖：** 避开黑盒框架，手写 Agent 核心运行循环（Execution Loop），深入理解大模型如何通过 Prompt 状态机实现自主决策。
- **ReAct 范式实现：** 严格遵循 `Thought -> Action -> Observation` 闭环，确保智能体在复杂任务下逻辑清晰、步骤可控。
- **动态工具调用 (Tool Use)：** 实现了基于 Python 函数注释自动解析的工具注册机制，支持智能体自主调用搜索、天气、地图等外部接口。
- **多约束规划能力：** 能够处理带有预算限制、特定偏好、时间冲突等复杂约束的旅行规划任务。

## 📂 目录结构

```text
Smart-Travel-Agent/
├── agent/
│   ├── core.py          # 核心引擎：实现 ReAct 运行循环与状态管理
│   ├── prompt.py        # 提示词工程：定义 System Prompt 与 ReAct 格式约束
│   └── parser.py        # 输出解析器：从 LLM 回复中提取 Action 与参数
├── tools/
│   ├── search_tool.py   # 搜索工具：基于 Tavily/Serper 接口获取实时信息
│   ├── map_tool.py      # 地图工具：模拟路径规划与距离计算
│   └── hotel_tool.py    # 预订工具：模拟酒店/餐厅查询与预订逻辑
├── main.py              # 项目入口：启动智能助手交互界面
├── requirements.txt     # 项目依赖库
└── README.md            # 项目说明文档
