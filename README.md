<p align="center">
  <img src="https://github.com/user-attachments/assets/e9d24d47-fe88-4322-be29-64507e0e6cd7" alt="AIP · 墨诩自研 MoXu ZiYan Lab" width="100%" />
</p>

<h1 align="center">AIP · 大模型提示词安全评测平台</h1>

<p align="center">
  <b>面向 LLM 应用的红队演练 · 越狱评测 · 风险报告平台</b><br/>
  <sub>Prompt Security Evaluation &amp; Red-Team Platform</sub><br/>
  <sub>状态：内核已跑通 · 代码即将开源 · Coming Soon</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-coming%20soon-0b0f19?style=flat-square" alt="status" />
  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux-2563eb?style=flat-square" alt="platform" />
  <img src="https://img.shields.io/badge/engine-Go%20%2B%20React%20%2B%20Python-16a34a?style=flat-square" alt="engine" />
  <img src="https://img.shields.io/badge/license-to%20be%20announced-6b7280?style=flat-square" alt="license" />
</p>

---

## 这是什么

AIP 是一套本地部署的大模型安全评测平台。它把「攻击手法 → 批量执行 → 自动判定 → 报告输出」串成一条流水线，用来回答一个很实际的问题：

> 我们上线的那套 Agent / 客服 / RAG 应用，被诱导着说出不该说的话、调用不该调用的工具时，扛不扛得住？

平台自带攻击手法库与评测集，支持任意 OpenAI 兼容接口，也支持 Dify / Coze 等应用型接入。所有数据留在本机，不外传。

## 核心能力

| 能力 | 说明 |
| --- | --- |
| 破甲评测 | 对目标模型批量下发攻击样本，自动判定是否越狱、是否泄露系统提示词、是否输出违规内容 |
| 攻击手法库 | 编码变形、角色扮演、上下文投毒、多轮递进、载荷拆分等手法，可按任务组合启停 |
| 评测集 | 内置通用与行业评测集，支持自定义样本导入；随机种子固定，结果可复现 |
| Agent 扫描 | 针对带工具调用的 Agent 应用，检查越权调用、提示词注入与数据外带路径 |
| 报告输出 | 单次任务生成结构化报告（得分、命中样本、原始响应、修复建议），可导出 CSV 归档 |
| 多模型接入 | 被测模型与裁判模型相互独立，避免自评自判；支持并发与限速控制 |

## 工作流

```mermaid
flowchart TD
    A["① 配置被测模型与裁判模型"] --> B["② 选择评测集与样本规模"]
    B --> C["③ 组合攻击手法"]
    C --> D["④ 批量执行 · 并发调度"]
    D --> E["⑤ 自动判定 · 打分归类"]
    E --> F["⑥ 生成报告 · 导出归档"]
```

## 技术构成

| 层 | 技术选型 | 职责 |
| --- | --- | --- |
| 前端 | React + TypeScript + Vite | 任务编排、实时日志、报告视图 |
| 服务端 | Go | 任务调度、SSE 推送、鉴权与分发 |
| 引擎 | Python | 攻击手法实现、判定逻辑、报告生成 |
| 存储 | SQLite | 任务、样本、结果本地留存 |

## 开源计划

代码整理与合规审查正在进行，按下面的节奏放出：

| 阶段 | 内容 | 时间 |
| --- | --- | --- |
| 第一阶段 | 评测引擎内核 + 攻击手法库 | 2026 年 12 月上旬 |
| 第二阶段 | 服务端与前端完整源码 | 2026 年 12 月中旬 |
| 第三阶段 | 部署文档、自定义手法 SDK、示例评测集 | 2027 年 1 月 |

关注本仓库即可，开源当天会在这里放发布说明。想先聊、想提前试用、想提需求，扫码进群：

<p align="center">
  <img src="assets/join-group.svg" width="220" alt="交流群二维码" /><br/>
  <b>扫码加入交流群</b>
</p>

## 使用边界

本项目仅用于**已获得授权**的目标：自有系统、签署了测试协议的客户环境、或明确的演练靶场。使用者需自行确保授权链条完整，并遵守所在地法律法规。作者不对任何未经授权的使用承担责任。

---

<p align="center">
  <img src="https://github.com/user-attachments/assets/8013ab61-cf21-4fb9-8533-00c0adca4633" alt="MoXu ZiYan Lab" width="100%" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/67d1d685-218f-44d5-b554-314db02a90e6" width="72" alt="logo" /><br/>
  <sub>AIP · Built for defenders. · 墨诩自研 MoXu ZiYan Lab</sub>
</p>
