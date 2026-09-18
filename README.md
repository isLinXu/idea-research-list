---
AIGC:
    Label: "1"
    ContentProducer: 001191440300708461136T1XGW3
    ProduceID: f9643191441a223536fc4b9e1bd9b715_8d373670b33111f1919d525400393706
    ReservedCode1: LfO97Q2RErVhkNXCmndajEwJuwQ9mRJSoRnZghkn0Zm4KeUY5msNhDMdPmsSGEvL0wAw61mrmiFvSq94V44IxcpnAbn2r5eJHxLhIziDOGZfEYzelwlrn6zAgD2EFjU3eIQkVDy7ZjkTm+eq8Nwq6BMJTcvqnuj8etjFZZe6dbH098/HgavtdLjTOKU=
    ContentPropagator: 001191440300708461136T1XGW3
    PropagateID: f9643191441a223536fc4b9e1bd9b715_8d373670b33111f1919d525400393706
    ReservedCode2: LfO97Q2RErVhkNXCmndajEwJuwQ9mRJSoRnZghkn0Zm4KeUY5msNhDMdPmsSGEvL0wAw61mrmiFvSq94V44IxcpnAbn2r5eJHxLhIziDOGZfEYzelwlrn6zAgD2EFjU3eIQkVDy7ZjkTm+eq8Nwq6BMJTcvqnuj8etjFZZe6dbH098/HgavtdLjTOKU=
---

# IDEA-Research 全部工作与论文调研报告（终版 · 完整深度版）

> 调研日期：2026-08-26（2026-09-08 复核更新）
> 数据来源：GitHub 组织官方仓库清单（49 个，via GitHub API，含 license/topics/时间戳）+ 各仓库 README + arXiv 编号核验 + 网络权威资料交叉验证
> 组织：粤港澳大湾区数字经济研究院（International Digital Economy Academy, IDEA）· 计算机视觉与机器人研究中心（IDEA CVR）
> 负责人：张磊（Lei Zhang），前微软研究院首席研究员，IEEE Fellow

---

---

## 概览

IDEA-Research 是粤港澳大湾区数字经济研究院（IDEA）旗下计算机视觉与机器人研究中心（CVR）的官方开源组织，由张磊教授（IEEE Fellow）领衔，是**开放世界视觉感知（Open-World Perception）**领域最成体系的团队之一。本报告覆盖其**全部 49 个公开仓库、全部代表性论文（2022—2026）、七大技术主线、团队与商业化全貌**。

| 维度 | 关键数据 |
|---|---|
| 公开仓库 | 49 个（无归档、无遗漏） |
| Star 总量 | 58,641（GitHub API 实测，2026-09-08） |
| 技术主线 | 7 条（DETR 检测基础 → 开放世界感知 → 统一视觉大模型） |
| 会议覆盖 | ICLR / CVPR / ICCV / ECCV / NeurIPS / ICML / AAAI |
| 时间跨度 | 2022—2026 |
| 组织名片 | Grounding DINO（ECCV 2024 最具影响力论文）、Grounded-Segment-Anything（17.7k★，组织内最高） |
| 商业化 | 视启未来（Visincept，2025.08 成立，近亿元天使轮） |

## 分册导航

| 分册 | 内容 | 覆盖范围 |
|---|---|---|
| 00 | [导览与执行摘要](./docs/00-导览与执行摘要.md) | 导览 · 执行摘要 · 影响力大盘 · 引用量快照 · 数据集生态 · 最新工作状态 · 仓库量化明细 · 下游集成 · 成员导航 |
| 01 | [组织团队与技术版图](./docs/01-组织团队与技术版图.md) | 组织与团队全貌 · 七大技术版图总览 |
| 02 | [七大技术主线深度拆解](./docs/02-七大技术主线深度拆解.md) | 主线 A~G 逐仓库深度拆解（论文 / 核心设计 / 关键实验） |
| 03 | [仓库工程细节速查](./docs/03-仓库工程细节速查.md) | 49 仓库许可证 / 依赖框架 / 安装 / 权重 / 应用 |
| 04 | [论文清单与图鉴](./docs/04-论文清单与图鉴.md) | 全量论文清单 · 论文图鉴（49 张缩略图） · 代表性论文时间线 |
| 05 | [影响力评估与横向对比](./docs/05-影响力评估与横向对比.md) | 技术影响力评估 · 核心技术深度解析 · 横向对比 · 数据集与训练基础设施 · 开源生态 · 学术谱系 |
| 06 | [商业化与未来展望](./docs/06-商业化与未来展望.md) | 商业化与竞争格局 · 技术路线图 · 工程实践与部署指南 · 总结与关键洞察 |
| 07 | [数据说明与信息来源](./docs/07-数据说明与信息来源.md) | 数据说明与信息来源 |

## 阅读路径建议

| 你想了解 | 建议先读 |
|---|---|
| 这个组织是干什么的、实力如何 | [00 导览与执行摘要](./docs/00-导览与执行摘要.md) |
| 每篇论文长什么样（带缩略图） | [04 论文清单与图鉴](./docs/04-论文清单与图鉴.md) |
| 某条技术线怎么演进 | [02 七大技术主线深度拆解](./docs/02-七大技术主线深度拆解.md) |
| 某仓库怎么装、用什么许可证 | [03 仓库工程细节速查](./docs/03-仓库工程细节速查.md) |
| 最新工作（2025—2026） | [00 导览与执行摘要](./docs/00-导览与执行摘要.md) →〇·4 |
| 团队、人才与商业化 | [01 组织团队与技术版图](./docs/01-组织团队与技术版图.md)、[06 商业化与未来展望](./docs/06-商业化与未来展望.md) |
| 与同领域工作的差异 | [05 影响力评估与横向对比](./docs/05-影响力评估与横向对比.md) |

## 数据口径

- **仓库清单 / Star / License / Topics / 时间戳**：GitHub API 实测（时点 2026-09-08）
- **论文信息**：各仓库 README + arXiv 编号核验 + 网络权威资料交叉验证
- **引用量**：Google Scholar / Semantic Scholar 采集的近似值，标注采集时点
- **缩略图**：论文原图、仓库 README 首图或 GitHub 仓库卡片，共 49 张，逐一实测可访问

> 详细口径说明、符号约定与更新方法见 [00 导览与执行摘要](./docs/00-导览与执行摘要.md)。
