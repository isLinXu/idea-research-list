# IDEA-Research 全部工作与论文调研报告（终版 · 完整深度版）

> 调研日期：2026-08-26（2026-09-08 复核更新）
> 数据来源：GitHub 组织官方仓库清单（49 个，via GitHub API，含 license/topics/时间戳）+ 各仓库 README + arXiv 编号核验 + 网络权威资料交叉验证
> 组织：粤港澳大湾区数字经济研究院（International Digital Economy Academy, IDEA）· 计算机视觉与机器人研究中心（IDEA CVR）
> 负责人：张磊（Lei Zhang），前微软研究院首席研究员，IEEE Fellow

---

## 〇、执行摘要

IDEA-Research 是粤港澳大湾区数字经济研究院（IDEA）旗下计算机视觉与机器人研究中心（CVR）的官方开源组织，由张磊教授领衔，是全球**开放世界视觉感知（Open-World Perception）**领域最成体系的团队之一。截至调研日共 **49 个公开仓库**（无归档、无遗漏），论文覆盖 ICLR / CVPR / ICCV / ECCV / NeurIPS / ICML / AAAI 等主流顶会，时间跨度 2022—2026，Star 总量 **58,641**（GitHub API 实测）。

组织技术主线可概括为一条清晰的演进脉络：

```
DETR 收敛性攻坚（DAB→DN→DINO）
        │
        ▼
   开集检测 Grounding DINO ──► Grounding DINO 1.5 ──► DINO-X（统一视觉大模型）
        │                                                    │
        ├──► Grounded-SAM 生态（分割/跟踪）                     ├──► Rex 系列（MLLM 感知理解）
        └──► T-Rex（视觉提示）                                 └──► 视启未来（商业化）
```

**四大里程碑**：
1. **DETR 检测基础闭环**（2022—2023）：DAB/[DN-DETR](https://arxiv.org/abs/2203.01305) 解决收敛难题，DINO 登顶 COCO 榜并霸榜 5 个月，detrex 平台化，奠定当前 DETR 系检测事实标准。
2. **开放世界感知范式开创**（2023）：Grounding DINO 定义「任意文本 → 开集检测」，催生万星项目 Grounded-Segment-Anything（17.7k★）。
3. **统一视觉大模型**（2024—2025）：Grounding DINO 1.5 → DINO-X，实现检测/分割/姿态/OCR/区域描述一体的 object-centric 视觉模型。
4. **商业化落地**（2025.08）：DINO-X 团队孵化成立「视启未来（Visincept）」，完成近亿元天使轮，估值约 5 亿元。

---

## 〇·1、影响力数据大盘（49 仓库 · GitHub API 实测）

| 指标 | 数值 |
|---|---|
| 公开仓库总数 | 49 |
| **Star 总量** | **58,641**（项目页为您看到的关注数口径总和）|
| Fork 总量 | 5,076 |
| 仓库占用存储 | 约 3.26 GB |
| Open Issues 总量 | 1,555 |
| 首个仓库创建 | 2022-01-28 |
| 最近创建仓库 | 2026-05-11（[SegDINO3D](https://github.com/IDEA-Research/SegDINO3D)）|
| 最近代码活跃 | 2026-07-29 |
| 千星以上仓库 | **12 个** |
| 万星以上仓库 | 2 个（[Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) 17.7k★、[GroundingDINO](https://github.com/IDEA-Research/GroundingDINO) 10.5k★）|

**12 个千星仓库**（按 Star 排序）：

| 仓库 | Stars | 意义 |
|---|---|---|
| [Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) | 17,721 | 开集检测+分割+生成全链路生态 |
| [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO) | 10,551 | 文本开集检测范式开创者 |
| [Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2) | 3,723 | 视频开集分割跟踪 |
| [DINO](https://github.com/IDEA-Research/DINO) | 2,837 | COCO 霸榜 5 个月的 DETR 巅峰 |
| [DWPose](https://github.com/IDEA-Research/DWPose) | 2,815 | 轻量全身姿态（已进 ControlNet 生态）|
| [T-Rex](https://github.com/IDEA-Research/T-Rex) | 2,702 | 文本+视觉提示协同检测 |
| [detrex](https://github.com/IDEA-Research/detrex) | 2,308 | DETR 系统一研究平台 |
| [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni) | 1,574 | 下一关键点预测统一感知（CVPR 2026）|
| [MaskDINO](https://github.com/IDEA-Research/MaskDINO) | 1,562 | 检测+分割统一框架 |
| [DINO-X-API](https://github.com/IDEA-Research/DINO-X-API) | 1,418 | 统一视觉大模型 API |
| [awesome-detection-transformer](https://github.com/IDEA-Research/awesome-detection-transformer) | 1,397 | Detection Transformer 论文导航 |
| [Grounding-DINO-1.5-API](https://github.com/IDEA-Research/Grounding-DINO-1.5-API) | 1,144 | 更强开集检测（Pro/Edge）|

**创建节奏**：2022 年 10 个（DETR 基础奠基）→ 2023 年 22 个（爆发年：Grounding DINO、Grounded SAM、OSX、DWPose、Motion-X 等）→ 2024 年 9 个（DINO-X、ChatRex、Grounded-SAM-2）→ 2025 年 6 个（Rex 系列、SceneMaker）→ 2026 年 2 个（SegDINO3D、V-Reflection）。2023 年为开源密度最高峰，2025—2026 转向大模型化与空间智能。

---


## 〇·2、核心论文引用量快照（2026-09 检索）

> 引用量随时间增长，以下为检索快照近似值，逐条标注口径（Google Scholar=GS / Semantic Scholar=S2 / IEEE 等）；动态数据以原始来源最新值为准。

| 论文 | 会议/年份 | 引用量（约） | 口径 |
|---|---|---|---|
| Grounding DINO | ECCV 2024 | ~4,850 | GS |
| DINO | ICLR 2023 | ~3,810 | GS |
| DAB-DETR | ICLR 2022 | ~1,400（Semantic Scholar / arXiv 单篇，2026-09 实测）；OpenAlex ~400 | S2/OpenAlex |
| DN-DETR | CVPR 2022 / TPAMI 2024 | ~1,579（GS 论文条目页单篇，2026）；Rankless ~545 | GS |
| Grounded SAM | arXiv 2024 技术报告 | ~1,220–1,240 | GS |
| MaskDINO | CVPR 2023 | ~810 | GS |
| Semantic-SAM | ECCV 2024 | ~379（GS）；AMiner ~169 | GS |
| Motion-X | NeurIPS 2023 | ~275 | GS |
| HumanTOMATO | ICML 2024 | ~148 | GS |
| OSX | CVPR 2023 | ~125（IEEE Xplore Crossref，GS 实际更高）| IEEE |
| T-Rex2 | ECCV 2024 | ~110–112（GS）/ ~79（S2）| 双口径 |
| DINO-X | arXiv 2024 技术报告（2411.14347）| ~49–89（SS 作者页 49；Prophy 88；OpenAlex 4）| S2/Prophy |
| TAPTR（v1）| ECCV 2024 | ~49（GS）/ ~53（Papers with Code）| 多口径 |
| ChatRex | arXiv 2024（2411.18363）| ~28（GS）；SS ~10 | GS/S2 |
| Grounded-SAM-2 | 2024.08 开源（非独立论文）| 未以论文单独计引；GitHub Stars ~3,700 | 仓库 |
| DWPose | ICCV 2023 | 未获取精确值（跨机构合作：IDEA 曾爱玲参与，主要作者属腾讯/上海 AI Lab）| — |

> 注：DWPose 仓库确在 IDEA-Research 组织下，但核心作者以腾讯/上海 AI Lab 为主，IDEA 为共同参与者，非本团队主导；本组织人体姿态主线以 OSX / UBody、X-Pose / UniKPT 为主。
> 2025–2026 新作官方状态：Rex-Omni（CVPR 2026，arXiv 2510.12798）、SceneMaker（CVPR 2026）、Rex-Thinker（ICLR 2026）、SegDINO3D（AAAI 2026）、SegVGGT（CVPR 2026，arXiv 2603.19926）、SpatialPoint（arXiv 2603.26690 预印本，顶会归属未确认）、T-Rex2++（IEEE TPAMI 2026）。

## 〇·3、核心数据集生态（规模 / 构成 / 用途）

| 数据集 | 来源工作 | 规模 | 构成要点 | 用途 / 开源 |
|---|---|---|---|---|
| **Grounding-100M** | DINO-X（arXiv 2411.14347）| **>1 亿 grounding 标注样本** | 约 30% 图像含 SAM/SAM2 伪 mask；约 5% 人工标注子集训练 universal object prompt；1,000 万+ region-level caption/OCR/QA 三元组；长尾显著（10M 子集：罕见类 12,340 种，1–10 图/类）| DINO-X 两阶段预训练基座；内部训练集，未公开下载 |
| **Human-Art** | CVPR 2023（2303.02760）| 50,000 张图 / 123,000+ 实例 | 20 个场景（5 自然 + 15 虚拟/人工），人体框+2D 关键点+自接触关键点+描述文本，MSCOCO 格式 | 跨域人体检测/姿态/网格/生成；github.com/IDEA-Research/HumanArt（CC 许可，表单申请）|
| **UBody** | OSX（2303.16160）| **>100 万帧** | 15 个真实生活场景，2D 全身关键点 + SMPL-X 3D 网格标注 | 3D 全身网格恢复 / 手语 / 数字人驱动；已被 MMPose 支持；github.com/IDEA-Research/OSX |
| **UniKPT** | X-Pose（2310.08530）| 226,547 张图 / 418,487 实例 | 统一 13 个关键点数据集，338 类关键点、1,237 个物体类别（含 1,216 生物物种），COCO 风格 JSON | 训练 promptable 关键点检测通用模型；SirenPose 扩展至 ~60 万实例；github.com/IDEA-Research/X-Pose |
| **Motion-X** | NeurIPS 2023（arXiv 2307.00818）| 15.6M SMPL-X 姿态 / 81.1K 序列 | 帧级全身姿态描述 + 序列级语义标签，含自动标注流水线 | 全身（含手指/表情）运动生成基础数据源；github.com/IDEA-Research/Motion-X |

> 注：检索未发现本组织发布名为「UDPose」的独立数据集，对应能力由 UniKPT / UBody 承担，避免误列。
## 〇·4、2025–2026 最新工作官方状态

| 工作 | 官方状态 | 概要 |
|---|---|---|
| **Rex-Omni** | 已录用 **CVPR 2026**（项目页 rex-omni.github.io，arXiv 2510.12798）| 3B MLLM「下一关键点预测」统一感知；零样本 COCO 与 DINO/Grounding DINO 相当或超过（宽松 IoU），严格 IoU 仍逊于回归式检测（性能边界如实注明）|
| **SceneMaker** | 已录用 **CVPR 2026** | 开放集 3D 场景生成（去遮挡+姿态估计解耦），自建 200K 场景数据集 |
| **SegDINO3D** | 已录用 **AAAI 2026** | 图像级+物体级 2D 特征赋能 3D 实例分割，缩小长尾差距 |
| **SegVGGT** | 已录用 **CVPR 2026**（arXiv 2603.19926）| 无位姿多视角 RGB 联合 3D 重建 + 实例分割；Object Queries×VGGT + FADA 注意力策略，ScanNet200 达 SOTA |
| **Rex-Thinker** | 已录用 **ICLR 2026**（OpenReview btWHQoSZZ1）| CoT + GRPO 接地指代推理，具备拒识能力 |
| **SpatialPoint** | arXiv 预印本 2603.26690（2026-03，cs.RO）；2026-04-27 广东省人工智能应用对接大会产品首秀；顶会归属**未确认**（截至 2026-09 无 CVPR/ECCV/ICCV/NeurIPS/ICLR/AAAI 录用证据，dblp 归类 CoRR） | 联合清华/IDEA 的空间智能 VLM；深度图原生输入输出可执行 3D 坐标；实点准确率 79%、误差 17.2mm、虚点方向准确率 48.86%、复杂定位 43%；自建 260 万 RGB-D QA 对，已完成真实机器人部署；项目页 qimingzhu-google.github.io/SpatialPoint、代码数据集"即将开源"；同团队 ECCV 2026 录用为另一篇（Guide, Think, Act，勿混淆） |
| **T-Rex2++** | IEEE **TPAMI 2026** | T-Rex2 期刊扩展版（通用物体感知）|
| **DINO-X Grasp / DINO-X Video / DINO-XSeek** | 产品/技术报告形态 | 机械臂抓取 / 视频事件理解 / 语义推理视觉模型 |

## 〇·5、仓库量化明细速查表（49 仓库 · GitHub API 实测 2026-09-08）

| 仓库 | ⭐ Star | Fork | 主要语言 | 最近推送 | 许可 |
|---|---|---|---|---|---|
| [Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) | 17721 | 1596 | Jupyter Notebook | 2024-09-05 | Apache-2.0 |
| [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO) | 10551 | 1069 | Python | 2024-08-12 | Apache-2.0 |
| [Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2) | 3723 | 429 | Jupyter Notebook | 2025-11-11 | Apache-2.0 |
| [DINO](https://github.com/IDEA-Research/DINO) | 2837 | 309 | Python | 2024-07-31 | Apache-2.0 |
| [DWPose](https://github.com/IDEA-Research/DWPose) | 2815 | 176 | Python | 2023-12-12 | Apache-2.0 |
| [T-Rex](https://github.com/IDEA-Research/T-Rex) | 2702 | 170 | Python | 2025-10-15 | NOASSERTION |
| [detrex](https://github.com/IDEA-Research/detrex) | 2308 | 248 | Python | 2025-09-11 | Apache-2.0 |
| [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni) | 1574 | 112 | Jupyter Notebook | 2026-02-22 | NOASSERTION |
| [MaskDINO](https://github.com/IDEA-Research/MaskDINO) | 1562 | 162 | Python | 2023-12-20 | Apache-2.0 |
| [DINO-X-API](https://github.com/IDEA-Research/DINO-X-API) | 1418 | 64 | Python | 2025-07-23 | Apache-2.0 |
| [awesome-detection-transformer](https://github.com/IDEA-Research/awesome-detection-transformer) | 1397 | 115 | - | 2024-07-04 | 无 |
| [Grounding-DINO-1.5-API](https://github.com/IDEA-Research/Grounding-DINO-1.5-API) | 1144 | 47 | Python | 2025-01-21 | Apache-2.0 |
| [Motion-X](https://github.com/IDEA-Research/Motion-X) | 893 | 25 | Python | 2025-03-03 | NOASSERTION |
| [X-Pose](https://github.com/IDEA-Research/X-Pose) | 815 | 45 | Python | 2024-08-16 | NOASSERTION |
| [OSX](https://github.com/IDEA-Research/OSX) | 794 | 65 | Python | 2024-08-26 | MIT |
| [OpenSeeD](https://github.com/IDEA-Research/OpenSeeD) | 764 | 46 | Python | 2024-01-22 | Apache-2.0 |
| [DN-DETR](https://github.com/IDEA-Research/DN-DETR) | 608 | 73 | Python | 2023-12-20 | Apache-2.0 |
| [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR) | 585 | 95 | Jupyter Notebook | 2023-06-02 | Apache-2.0 |
| [MotionLLM](https://github.com/IDEA-Research/MotionLLM) | 388 | 21 | Python | 2024-09-08 | NOASSERTION |
| [HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO) | 363 | 12 | Python | 2024-06-19 | NOASSERTION |
| [HumanSD](https://github.com/IDEA-Research/HumanSD) | 306 | 21 | Python | 2023-10-24 | Apache-2.0 |
| [HumanArt](https://github.com/IDEA-Research/HumanArt) | 288 | 4 | - | 2023-10-03 | Apache-2.0 |
| [TAPTR](https://github.com/IDEA-Research/TAPTR) | 282 | 16 | - | 2026-08-30 | NOASSERTION |
| [deepdataspace](https://github.com/IDEA-Research/deepdataspace) | 265 | 25 | TypeScript | 2026-03-25 | Apache-2.0 |
| [Stable-DINO](https://github.com/IDEA-Research/Stable-DINO) | 246 | 8 | Python | 2024-04-29 | Apache-2.0 |
| [ChatRex](https://github.com/IDEA-Research/ChatRex) | 216 | 9 | Python | 2025-10-15 | NOASSERTION |
| [Lite-DETR](https://github.com/IDEA-Research/Lite-DETR) | 210 | 18 | Python | 2023-06-01 | Apache-2.0 |
| [ED-Pose](https://github.com/IDEA-Research/ED-Pose) | 190 | 11 | Python | 2023-09-20 | NOASSERTION |
| [DreamWaltz](https://github.com/IDEA-Research/DreamWaltz) | 189 | 10 | Python | 2024-10-15 | NOASSERTION |
| [RexSeek](https://github.com/IDEA-Research/RexSeek) | 188 | 11 | Python | 2025-10-15 | NOASSERTION |
| [3D-deformable-attention](https://github.com/IDEA-Research/3D-deformable-attention) | 186 | 4 | Python | 2025-04-12 | NOASSERTION |
| [Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker) | 154 | 7 | Python | 2025-06-30 | NOASSERTION |
| [SceneMaker](https://github.com/IDEA-Research/SceneMaker) | 151 | 8 | Python | 2026-05-04 | Apache-2.0 |
| [MP-Former](https://github.com/IDEA-Research/MP-Former) | 143 | 7 | Python | 2023-10-22 | NOASSERTION |
| [DINO-X-MCP](https://github.com/IDEA-Research/DINO-X-MCP) | 110 | 10 | TypeScript | 2026-06-17 | Apache-2.0 |
| [Click-Pose](https://github.com/IDEA-Research/Click-Pose) | 86 | 4 | Python | 2023-10-12 | NOASSERTION |
| [SegDINO3D](https://github.com/IDEA-Research/SegDINO3D) | 72 | 1 | Python | 2026-07-29 | Apache-2.0 |
| [DiffHOI](https://github.com/IDEA-Research/DiffHOI) | 67 | 1 | Python | 2023-08-09 | NOASSERTION |
| [V-Reflection](https://github.com/IDEA-Research/V-Reflection) | 62 | 0 | Python | 2026-04-07 | Apache-2.0 |
| [DisCo-CLIP](https://github.com/IDEA-Research/DisCo-CLIP) | 59 | 4 | Python | 2023-08-02 | Apache-2.0 |
| [DQ-DETR](https://github.com/IDEA-Research/DQ-DETR) | 58 | 2 | - | 2022-11-28 | 无 |
| [LipsFormer](https://github.com/IDEA-Research/LipsFormer) | 43 | 6 | Python | 2023-06-07 | Apache-2.0 |
| [SegVGGT](https://github.com/IDEA-Research/SegVGGT) | 38 | 3 | Python | 2026-05-18 | NOASSERTION |
| [TOSS](https://github.com/IDEA-Research/TOSS) | 23 | 3 | Python | 2024-05-05 | Apache-2.0 |
| [MotionCLR](https://github.com/IDEA-Research/MotionCLR) | 17 | 1 | Python | 2024-12-01 | NOASSERTION |
| [hana](https://github.com/IDEA-Research/hana) | 17 | 1 | Python | 2022-12-22 | Apache-2.0 |
| [IYFC](https://github.com/IDEA-Research/IYFC) | 9 | 1 | C++ | 2024-02-19 | 无 |
| [detrex-storage](https://github.com/IDEA-Research/detrex-storage) | 3 | 0 | - | 2024-10-24 | Apache-2.0 |
| [HandOSweb](https://github.com/IDEA-Research/HandOSweb) | 1 | 1 | HTML | 2025-03-19 | 无 |

> 注：按 Star 降序；Star 总量 58,641、Fork 5,076（2026-09-08 实测，较 08-26 快照略有增长）。


## 〇·6、开源生态下游集成清单（2026-09 检索）

### 6.1 Grounding DINO / Grounded-SAM（组织名片级生态）

| 集成对象 | 形态 |
|---|---|
| **Hugging Face** | 官方模型卡 `ShilongLiu/GroundingDINO` + 官方 HF Demo；据作者主页，为 HF 上下载量最高的零样本检测模型（月下载超 200 万次）；Grounded-SAM-2 多 demo 直接以 HF API 推理 Grounding DINO |
| **Roboflow** | 设 Grounding DINO 模型页，Roboflow Inference 部署（CPU/GPU），并借 **Autodistill** 零标注自动标注训练 YOLO 等模型 |
| **Label Studio** | HumanSignal 官方 `label-studio-ml-backend` 含 `grounding_dino` 示例后端，支持文本提示零样本检测 + GroundingSAM 分割（USE_SAM） |
| **ComfyUI** | `storyicon/comfyui_segment_anything` 集成 GroundingDINO_SwinT-OGC/SwinB 作为 text-to-box 节点；多个 ComfyUI 包支持含 GroundingDINO 的 19 种检测器 |
| **阿里巴巴云 PAI** | Model Gallery 集成 Grounded-SAM 为在线服务（WebUI） |
| **Grounding-SAM-2 下游** | 组合 Grounding DINO 1.0/1.5/1.6 + DINO-X + SAM 2 + Florence-2，支持图像/视频 grounding 与 tracking；被 PyImageSearch 教程采用；集成 supervision 可视化、SAHI 高分辨率切片推理 |
| **其他教程生态** | Grounded-SAM 被大量目标检测/分割教程与课程作为标准示例 |

### 6.2 DINO-X

| 集成对象 | 形态 |
|---|---|
| **Hugging Face Daily Papers** | 收录 DINO-X 论文（2411.14347） |
| **DINO-X MCP Server** | 2025.06 发布，接入 Cursor、Claude Desktop 等 MCP 兼容工具（仓库 `DINO-X-MCP` 110⭐） |
| **Grounded-SAM-2** | 自 2024.12 支持 DINO-X + SAM 2 分割/tracking（dds-cloudapi-sdk V2） |
| **T-Rex Label** | 2026 年将 DINO-X 接入标注平台；DINO-X 开放平台（cloud.deepdataspace.com）支持定制模板训练与预标注 |
| **注意** | 检索到的 `timlawrenz/DINO-X` 为同名医学影像项目，**非** IDEA 作品，勿混淆 |

### 6.3 T-Rex / T-Rex2 / 视觉提示

- **T-Rex Label**（trexlabel.com）：基于 T-Rex2（ECCV 2024）+ Grounding DINO 1.5 + DINO-X 的 SaaS 标注平台，支持 COCO/YOLO 导出，集成 Roboflow、Label Studio、Hugging Face、ModelScope、Kaggle、FiftyOne 等。
- 视觉提示计数范式被 AAAI 2025（MI Grounding）、NeurIPS 2024（DiPEx）等后续工作借鉴。

### 6.4 detrex / OSX / DWPose / Motion-X

| 项目 | 集成形态 |
|---|---|
| **detrex** | 与 OpenMMLab/MMDetection 相互参照（benchmark 对比 MMDetection 2.0/3.0 的多代 DETR），支持 19 个 DETR 模型、5 类任务；基于 Detectron2 借鉴 MMDetection 设计；为 DINO/DAB/DN 等的标准复现基线，被多所高校课程与论文采用 |
| **OSX** | UBody 数据集自 2023.10 被 MMPose 官方支持；与 Grounded-SAM 合并（2023.04）实现 promptable 3D whole-body mesh recovery |
| **DWPose** | 基于 MMPose + ControlNet；模型上架 HF（`yzd-v/DWPose`）；为 sd-webui-controlnet 的 `dw_openpose_full` 预处理器（≥v1.1237）；ComfyUI 经 LykosAI/Inference-Core-Nodes 默认姿态预处理器；被 StableAnimator、Animate Anyone 等视频生成框架用作骨架提取；有 YOLOv8 适配分支 |
| **Motion-X** | 被 HumanTOMATO 等文本驱动全身动作生成作为训练基准；2025 升级 Motion-X++ 上架 HF，支持视频/音频/文本多模态，被文本/音频驱动动作生成、3D mesh recovery 等下游采用 |


## 〇·7、核心成员贡献导航（2026-09 检索，去向截至检索时点）

| 成员 | 代表工作 | 当前去向 | 个人主页 |
|---|---|---|---|
| **张磊（Lei Zhang）** | DINO、detrex、Grounding DINO、Grounded SAM、T-Rex2、DINO-X 系列总负责人；IEEE Fellow | CVR 讲席科学家（2021.06 至今）；HKUST(广州) 兼职教授；**视启未来（Visincept）创始人兼 CEO（2025 起）** | leizhang.org |
| **刘世隆（Shilong Liu）** | DAB-DETR、DN-DETR、DINO、MaskDINO、Grounding DINO、Grounded-SAM、LLaVA-Plus | Princeton AI Lab 博士后（2025–2027，导师 Mengdi Wang）→ **2027 秋哥伦比亚大学 EE tenure-track 助理教授**；曾任 ByteDance Seed 研究科学家 | lsl.zone |
| **任天鹤（Tianhe Ren）** | Grounding DINO、Grounded SAM、DINO-X、T-Rex Label、Grounded-SAM-2 | CVR 算法工程师 / HKU 博士生；Visincept 产品线核心研发 | GS `cW4ILs0AAAAJ` |
| **黎鸿扬（Hongyang Li）** | TAPTR/v2/v3、DFA3D、SegDINO3D、OVSeg3R、BEVFormer、UniAD | **HKU 助理教授（2024.09 至今）、OpenDriveLab 负责人；Archon Robotics 创始人（2025）**；曾任 IDEA 长期实习 | lhy-hongyangli.github.io |
| **蒋擎（Qing Jiang）** | T-Rex2、ChatRex、DINO-X、Rex-Omni、Rex-Thinker、Grounded SAM | 华南理工 PhD（导师张磊）；IDEA 实习 2023.06–2026.03；现 **ByteDance Seed（World Model 方向）** | mountchicken.github.io |
| **李峰（Feng Li）** | DN-DETR、DAB-Deformable、Semantic-SAM、Grounding DINO、Visual In-Context Prompting | **Google DeepMind 研究科学家**；曾 IDEA 实习，清华/港科大背景 | GS `U_cvvUwAAAAJ` |
| **陈奕豪（Yihao Chen）** | DINO-X、Grounding DINO 1.5、ChatRex、TinySAM、DisCo-CLIP | IDEA Research 研究员（2021 至今）；DINO-X 主力作者之一 | GS `IA_3Jq8AAAAJ` |
| **曾爱玲（Ailing Zeng）** | Grounded SAM、OSX、Motion-X、DWPose、HumanTOMATO、SMPLest-X、LTSF-Linear | 2022–2024 IDEA 研究员 → 腾讯 AI Lab / 混元 → Anuttacon（米哈游蔡浩宇 AI 公司）→ **2026.07 入职 B站任 AI 视频生成业务负责人** | ailingzeng.site |

> 出处说明：上述去向存在个人主页 / OpenReview / ORCID / GS 等多源交叉，个别成员（如曾爱玲）affiliation 在不同来源存在时间差，已取检索时点最新口径；Tianhe Ren 未见独立个人主页。


## 一、组织与团队全貌

### 1.1 机构背景

- **IDEA（粤港澳大湾区数字经济研究院 / International Digital Economy Academy）**：2020 年 11 月由**沈向洋（Harry Shum）**（前微软全球执行副总裁、微软亚洲研究院联合创始人）在深圳创立，获深圳市政府支持，目标是建设国际 AI 创新枢纽。
- **CVR（Computer Vision and Robotics，计算机视觉与机器人研究中心）**：由张磊 2021 年 6 月加入后创立并担任讲席科学家（Chief Scientist），定位「立足视觉与机器人方向的基础研究，专注大规模视觉表示学习、零/小样本物体识别、智能控制，以智能制造为应用目标」。
- 组织开源策略：通过 detrex、Grounding DINO、DINO-X 系列以 Apache-2.0 开源反哺科研与产业。
- 姊妹线：IDEA-CCNL（NLP/认知计算），产出封神榜（Fengshenbang）与紫冬（Ziya）系列中文大模型，与 CV 线并行。

### 1.2 核心成员与分工

| 成员 | 角色 / 现状 | 主要贡献 |
|---|---|---|
| **张磊（Lei Zhang）** | CVR 讲席科学家、HKUST(广州)兼职教授、Visincept 创始人兼 CEO、IEEE Fellow | 团队总负责；[DINO](https://github.com/IDEA-Research/DINO) 系列、[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO)、DINO-X 总设计与通讯作者；前微软 20 年（MSRA + 微软总部） |
| **任天鹤（Tianhe Ren）** | 原 CVR 高级 CV 工程师，现 HKU CVMI Lab 博士生（导师齐晓娟） | [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO)、Grounded-SAM、DINO-X API、[Grounding DINO 1.5](https://github.com/IDEA-Research/Grounding-DINO-1.5-API) 核心作者 |
| **刘世隆（Shilong Liu）** | 原 CVR 实习生（清华博士），现 Princeton | [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) 一作；[DINO](https://github.com/IDEA-Research/DINO)、[DAB-DETR](https://github.com/IDEA-Research/DAB-DETR)、[DN-DETR](https://github.com/IDEA-Research/DN-DETR)、[Stable-DINO](https://github.com/IDEA-Research/Stable-DINO)、Grounded-SAM 重要贡献者 |
| **赵展（Zhaoyang Zeng）** | CVR 核心研究员 | [Stable-DINO](https://github.com/IDEA-Research/Stable-DINO)、[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO)、DINO-X、[Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)、[ChatRex](https://github.com/IDEA-Research/ChatRex) 等多篇核心论文作者 |
| **冯力（Feng Li）** | CVR 核心研究员 | [DINO](https://github.com/IDEA-Research/DINO)、[DN-DETR](https://github.com/IDEA-Research/DN-DETR)、[DAB-DETR](https://github.com/IDEA-Research/DAB-DETR)、[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO)、T-Rex2、Visual in-Context Prompting、Semantic-SAM |
| **张浩（Hao Zhang）** | CVR 研究员 | [DINO](https://github.com/IDEA-Research/DINO) 一作；[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) 共同作者 |
| **黎鸿扬（Hongyang Li）** | CVR 研究员 | [TAPTR](https://github.com/IDEA-Research/TAPTR)、DINO-X 共同作者 |
| **蒋擎（Qing Jiang）** | 华南理工与 IDEA 联培博士生（师从张磊） | [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)、[ChatRex](https://github.com/IDEA-Research/ChatRex)、T-Rex2、Referring to Any Person、[Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker) |
| **陈一豪（Yihao Chen）** | CVR 研究员 | DINO-X、[Rex-Omni](https://github.com/IDEA-Research/Rex-Omni) 共同作者 |
| **曹赫（He Cao）** | CVR 实习生 | Grounded-SAM、生成模型方向 |
| **谭平（Ping Tan）** | 客座研究员（HKUST 教授，原阿里达摩院 XR 实验室负责人） | 3D / 空间智能方向顾问 |

团队背景多元（微软、DeepMind、腾讯、字节等），博士占比约 40%。

### 1.3 研究里程碑时间线

| 时间 | 里程碑 |
|---|---|
| 2020.11 | IDEA 由沈向洋创立 |
| 2021.06 | 张磊加入 IDEA，创立 CVR |
| 2021 | CVR 入围工信部「2021 人工智能产业创新任务揭榜挂帅」（超大规模多模态数据库方向） |
| 2022 | [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR)（ICLR 2022）、[DN-DETR](https://github.com/IDEA-Research/DN-DETR)（CVPR 2022 Oral）解决 DETR 收敛难题 |
| 2023 | [DINO](https://github.com/IDEA-Research/DINO)（ICLR 2023）登顶 COCO 榜并霸榜 5 个月；[detrex](https://github.com/IDEA-Research/detrex) 开源；**[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) + Grounded-SAM 发布**（开集检测范式） |
| 2023 | [OSX](https://github.com/IDEA-Research/OSX)、[DWPose](https://github.com/IDEA-Research/DWPose)、[Motion-X](https://github.com/IDEA-Research/Motion-X)、[OpenSeeD](https://github.com/IDEA-Research/OpenSeeD)、[HumanArt](https://github.com/IDEA-Research/HumanArt) 等人/运动/分割方向多点开花 |
| 2024.05 | [Grounding DINO 1.5](https://github.com/IDEA-Research/Grounding-DINO-1.5-API)（Pro + Edge，20M+ 训练图像） |
| 2024.11 | DINO-X 统一视觉大模型发布；[ChatRex](https://github.com/IDEA-Research/ChatRex)、T-Rex2 发布 |
| 2025.08 | 张磊带 DINO-X 团队孵化成立视启未来（Visincept） |
| 2025.10 | [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)（CVPR 2026，「下一关键点预测」范式） |
| 2025.11 | DINO-X Grasp（机械臂万物抓取）；视启未来完成近亿元天使轮 |
| 2026 | [SegDINO3D](https://github.com/IDEA-Research/SegDINO3D) / [SegVGGT](https://github.com/IDEA-Research/SegVGGT) / [SceneMaker](https://github.com/IDEA-Research/SceneMaker)（3D 空间智能）；[Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker)（ICLR 2026） |
| 2026 | TPAMI 期刊 / 产品 | T-Rex2++（TPAMI 2026）；EgoTwin（联合百度智能云）、DINO-X Grasp、SpatialPoint、DINO-X Video |

### 1.4 商业化：视启未来（Visincept）

- **公司**：视启未来（深圳）科技有限公司，2025-08-07 成立，总部深圳福田深港国际科技园，由 IDEA 孵化，承接 DINO-X 核心研发团队与知识产权。创始人兼 CEO 张磊，顾问为张钹院士、沈向洋院士。
- **定位**：具身机器人的「视觉中枢」/ 空间智能模型公司，走「视觉原生（vision-native）」技术路线，以物体级理解为核心构建世界模型，融合 VLA 与 3D 空间感知。
- **融资**：2025.09 获安凯微 2000 万元战略投资；2025.11 完成近亿元天使轮（安凯微领投，昊辰资本、德虎资本、元禾璞华、银杏谷资本等跟投），投后估值约 5 亿元。
- **产品矩阵**：
  - 核心模型：DINO-X（开放世界检测+理解）、DINO-XSeek（指代检测 MLLM）、DINO-X Grasp（机械臂抓取）、EgoTwin（人手 3D 对齐引擎，联合百度智能云）、oVP 优化视觉提示/定制模板（长尾场景）。
  - MaaS 平台：DINO-X 开放平台（cloud.deepdataspace.com）、T-Rex Label（AI 标注，省 ~99% 标注耗时）、CountAnything（一键计数 APP）、DINO-X / Grounding DINO 1.5 API（api.deepdataspace.com）、**DINO-X MCP Server**（接入 Cursor/Claude 等 MCP 生态）。
  - 官网：deepdataspace.com（DINO-X 主页 / 开放平台 / Playground）。
- **落地案例**：招商局集团、美团（机器人）、腾讯、阿里、安凯微、百度智能云、中央美院 TxstureAxis（文物纹样识别）等；行业覆盖工业质检、低空经济、自动驾驶、智慧矿山、农业、具身机器人；生态伙伴含 Macks、Lumigrid、Speedhome、UseAd、See&Say、Muda 等。

---

## 二、技术版图：七大主线总览

| 主线 | 仓库数 | 代表项目 | 核心价值 |
|---|---|---|---|
| A. DETR 检测基础 | 14 | [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR)、[DN-DETR](https://github.com/IDEA-Research/DN-DETR)、[DINO](https://github.com/IDEA-Research/DINO)、[MaskDINO](https://github.com/IDEA-Research/MaskDINO)、[detrex](https://github.com/IDEA-Research/detrex) | 组织技术基因：解决 DETR 收敛，奠基开集检测 |
| B. 开放世界 / 通用感知 | 11 | [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO)、DINO-X、[T-Rex](https://github.com/IDEA-Research/T-Rex)、[Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)、[ChatRex](https://github.com/IDEA-Research/ChatRex) | 组织名片：开集检测→统一视觉大模型 |
| C. 分割与 Grounded SAM | 2 | [Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything)、[Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2) | 生态聚合：检测+分割+跟踪+生成 |
| D. 人体 / 姿态 / 手势 | 8 | [OSX](https://github.com/IDEA-Research/OSX)、[DWPose](https://github.com/IDEA-Research/DWPose)、[X-Pose](https://github.com/IDEA-Research/X-Pose)、[HumanArt](https://github.com/IDEA-Research/HumanArt)、[HumanSD](https://github.com/IDEA-Research/HumanSD) | 人类中心感知，2D/3D 全覆盖 |
| E. 3D 场景与空间智能 | 6 | [DreamWaltz](https://github.com/IDEA-Research/DreamWaltz)、[SceneMaker](https://github.com/IDEA-Research/SceneMaker)、[SegVGGT](https://github.com/IDEA-Research/SegVGGT)、[SegDINO3D](https://github.com/IDEA-Research/SegDINO3D) | 从单目标重建走向开放集 3D 场景 |
| F. 人体运动生成与理解 | 4 | [Motion-X](https://github.com/IDEA-Research/Motion-X)、[HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO)、[MotionLLM](https://github.com/IDEA-Research/MotionLLM) | 大规模运动数据 + 生成理解 |
| G. 多模态 LLM 与工程工具 | 7 | [ChatRex](https://github.com/IDEA-Research/ChatRex)、[RexSeek](https://github.com/IDEA-Research/RexSeek)、[Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker)、[deepdataspace](https://github.com/IDEA-Research/deepdataspace)、[DINO-X-MCP](https://github.com/IDEA-Research/DINO-X-MCP) | 感知×LLM 融合 + 落地基础设施 |

> 注：TAPTR 跨 A/B 类，按主属性归入 B；V-Reflection 归入 G。

---

## 三、主线 A：DETR 检测基础（组织基因，14 仓库）深度拆解

**技术演进链**：

```
[DAB-DETR](https://arxiv.org/abs/2201.12329)(锚框query) → DN-DETR(去噪训练) → DINO(对比去噪+混合匹配+look-forward-twice)
     │                     │                     │
     │                     │                     ├─► Stable-DINO(稳定匹配) / Lite-DETR(轻量)
     │                     │                     └─► MaskDINO(检测+分割统一)
     └─────────────────────┴─────────────────────► detrex(研究平台) ◄── detrex-storage(权重)
```

| 仓库 | 论文/会议 | 方法架构与核心设计 | 关键实验/指标 |
|---|---|---|---|
| **[DAB-DETR](https://github.com/IDEA-Research/DAB-DETR)** | [Dynamic Anchor Boxes are Better Queries for DETR](https://arxiv.org/abs/2201.12329)（ICLR 2022）| 将 DETR 的 decoder query 从「可学习向量」显式化为 **4D 动态锚框 (x,y,w,h)**，锚框随层更新并注入位置编码，让 query 具备物理可解释性 | 收敛速度大幅提升：12 epoch 即达传统方案 108+ epoch 效果；R50 4scale 约 45.7 AP（12ep） |
| **[DN-DETR](https://github.com/IDEA-Research/DN-DETR)** | [Accelerate DETR Training by Introducing Query DeNoising](https://arxiv.org/abs/2203.01305)（CVPR 2022 **Oral**）| **去噪训练**：训练时向 decoder 注入「加噪 GT」作为额外 query，并配 attention mask 隔离其与真实 query 的交互，让 decoder 学会去噪，稳定二分匹配 | 把 DETR 训练成本从数百 epoch 降到可接受范围；CVPR 2022 Oral |
| **[DINO](https://github.com/IDEA-Research/DINO)** | [DETR with Improved DeNoising Anchor Boxes](https://arxiv.org/abs/2203.03605)（ICLR 2023）| 集 DAB+DN 大成，三项关键创新：**对比去噪（CDN）**（正/负样本对，负样本可回退）、**混合匹配**（一次匹配双监督）、**look-forward-twice**（用下层预测更新 query 以更准计算辅助 loss）| R50 4scale 约 **50.9 AP**（12ep），**登顶 COCO 榜并霸榜 5 个月**，成为后续开集检测/分割的基础模型 |
| **[Stable-DINO](https://github.com/IDEA-Research/Stable-DINO)** | [Detection Transformer with Stable Matching](https://arxiv.org/abs/2304.04742)（ICCV 2023）| 从「标签含噪」视角剖析 DETR 匹配不稳定问题，提出**稳定匹配**策略（训练早期用预测框与 GT 的匹配信号）| 提升 [DINO](https://github.com/IDEA-Research/DINO) 训练稳定性与最终精度 |
| **[Lite-DETR](https://github.com/IDEA-Research/Lite-DETR)** | [An Interleaved Multi-Scale Encoder for Efficient DETR](https://arxiv.org/abs/2303.07335)（CVPR 2023）| **交错多尺度编码器**：各层只处理部分尺度 token，显著降低高分辨率特征计算开销 | 在 [DINO](https://github.com/IDEA-Research/DINO) 基础上大幅降计算量（~60% FLOPs 降幅），适合端侧/实时场景 |
| **[MaskDINO](https://github.com/IDEA-Research/MaskDINO)** | [Mask DINO: Unified Transformer Framework for Detection and Segmentation](https://arxiv.org/abs/2206.02777)（CVPR 2023）| **掩码作为通用 query**：把检测和分割统一到一个 Transformer 框架，box + mask 联合预测，掩码监督反哺定位质量 | Swin-L 上 COCO bbox 约 57.8 AP / segm 约 51.2 AP，成为统一检测-分割标杆 |
| **[MP-Former](https://github.com/IDEA-Research/MP-Former)** | [Mask-Piloted Transformer for Image Segmentation](https://arxiv.org/abs/2303.07336)（CVPR 2023）| **掩码引导（mask-piloted）** 训练范式：为掩码注意力引入引导信号，减少分割掩码中的假阳性/假阴性 | 在 Mask2Former 等基线上一致提升 |
| **[ED-Pose](https://github.com/IDEA-Research/ED-Pose)** | [Explicit Box Detection Unifies End-to-End Multi-Person Pose Estimation](https://arxiv.org/abs/2302.01593)（ICLR 2023）| **显式框化姿态**：把多人姿态估计重构为「先检测框、再回归关键点」的统一端到端流程 | 首个统一端到端多人姿态估计框架，消除以往自顶向下方法的繁琐 |
| **[DQ-DETR](https://github.com/IDEA-Research/DQ-DETR)** | [Dual Query Detection Transformer for Phrase Extraction and Grounding](https://arxiv.org/abs/2211.15516)（AAAI 2023）| **双查询设计**：一个 query 管短语抽取、一个管指代定位，提出跨模态 AP 新指标 | 统一视觉定位与短语抽取两任务 |
| **DFA3D**（3d-deformable-attention）| [DFA3D: 3D Deformable Attention For 2D-to-3D Feature Lifting](https://arxiv.org/abs/2307.12972)（ICCV 2023）| **3D 可变形注意力**：在可变形注意力中引入 3D 空间索引，高效完成 2D→3D 特征提升 | 为 BEV / 3D 检测提供高效 lifting 模块 |
| **[DisCo-CLIP](https://github.com/IDEA-Research/DisCo-CLIP)** | [Distributed Contrastive Loss for Memory Efficient CLIP Training](https://arxiv.org/abs/2304.08480) | **分布式对比损失**：把 CLIP 大 batch 对比损失拆分到多卡，降低单卡显存压力 | 支持更大 batch 的 CLIP 训练 |
| **[detrex](https://github.com/IDEA-Research/detrex)** | [detrex: Benchmarking and Improving Transferability of Pretrained ViTs on Detection](https://arxiv.org/abs/2306.07265)（研究平台，2.3k★）| **DETR 系统一研究平台**：内置 [DINO](https://github.com/IDEA-Research/DINO) / [DN-DETR](https://github.com/IDEA-Research/DN-DETR) / [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR) / [MaskDINO](https://github.com/IDEA-Research/MaskDINO) / Deformable-DETR / Group-DETR / DETA / Anchor-DETR / H-DETR / Conditional-DETR 全系实现，支持检测/分割/姿态估计 | 文档 [detrex](https://github.com/IDEA-Research/detrex).readthedocs.io，被学术界与工业界广泛采用；提供 Model-EMA、AMP、Activation Checkpoint 等工程能力 |
| **[detrex-storage](https://github.com/IDEA-Research/detrex-storage)** | 权重存储仓库 | [detrex](https://github.com/IDEA-Research/detrex) 配套的模型权重托管 | — |
| **[awesome-detection-transformer](https://github.com/IDEA-Research/awesome-detection-transformer)** | 论文导航列表（1.4k★）| 收录 Detection Transformer 方向论文，社区导航 | — |

---
---

## 四、主线 B：开放世界 / 通用视觉感知（组织名片，11 仓库）深度拆解

**演进链**：

```
Grounding DINO(文本开集检测) ──► Grounding DINO 1.5(更强backbone+多任务)
      │                                    │
      ├──► T-Rex(文本+视觉提示协同)          └──► DINO-X(统一视觉大模型:检测/分割/姿态/OCR/描述)
      ├──► OpenSeeD(开放词汇分割检测)                       │
      └──► Grounded-SAM 生态(见主线C)                       ├──► Rex-Omni(下一关键点预测)
                                                            └──► DINO-X-MCP / API(工程落地)
```

| 仓库 | 论文/会议 | 方法架构与核心设计 | 关键实验/指标 |
|---|---|---|---|
| **[GroundingDINO](https://github.com/IDEA-Research/GroundingDINO)** | [Grounding DINO: Marrying DINO with Grounded Pre-Training](https://arxiv.org/abs/2303.05499)（ECCV 2024，10.5k★）| [DINO](https://github.com/IDEA-Research/DINO)（检测）+ BERT（文本）双编码器，经 **feature enhancer**（自注意力+跨注意力）双向融合图文特征，**language-guided query selection** 用高语义相关文本引导 decoder query 初始化；训练用 grounded pre-training（大规模图文对）| COCO zero-shot 约 46.6 AP（Swin-T）/ 52.5（Swin-L）；**被 PaperDigest 评为 ECCV 2024 最具影响力论文**，成为 Grounded SAM 生态基石 |
| **[Grounding-DINO-1.5-API](https://github.com/IDEA-Research/Grounding-DINO-1.5-API)** | [Grounding DINO 1.5: Advance the Edge of Open-Set Object Detection](https://arxiv.org/abs/2405.10300)（1.1k★）| 更强 backbone（ViT-2B 级）+ DINO-X 同源数据管线；Pro / Edge 双版本；支持 grounding、关键点、检测+分割多任务 | 20M+ 训练图像；Pro 版 COCO 约 59.9 AP、LVIS 约 67.3；Edge 兼顾端侧部署 |
| **[T-Rex](https://github.com/IDEA-Research/T-Rex)** | [T-Rex2: Towards Generic Object Detection via Text-Visual Prompt Synergy](https://arxiv.org/abs/2403.14610)（ECCV 2024，2.7k★）| 首次在同一模型内融合 **文本提示 + 视觉提示**（框选示例即指定类别）协同，对比学习拉近两种 prompt 语义 | 交互式框选即可零样本检测任意类别；ViT-L 上 LVIS zero-shot 约 42.2 AP；配套视觉计数/交互标注应用 |
| **[DINO-X-API](https://github.com/IDEA-Research/DINO-X-API)** | [[DINO-X: A Unified Vision Model for Open-World Object Detection and Understanding](https://arxiv.org/abs/2411.14347)](https://arxiv.org/abs/2411.14347)（1.4k★）| **object-centric 统一视觉模型**：同时支持文本/视觉/自定义三种提示，集成检测、分割、姿态、OCR、区域描述等任务；训练自 Grounding-100M 大规模数据集 | LVIS minival 上 Pro 约 63.9 AP / Edge 约 56.9；COCO 等综合指标行业领先，被定位「世界领先的开放世界检测+理解模型」 |
| **[DINO-X-MCP](https://github.com/IDEA-Research/DINO-X-MCP)** | MCP Server（109★）| 将 DINO-X 封装为 **Model Context Protocol** 服务，赋予 LLM 真实视觉感知（检测/定位/描述）| 可接入 Cursor、Claude 等 MCP 工具生态，对话式完成视觉任务 |
| **[Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)** | [Detect Anything via Next Point Prediction](https://rex-omni.github.io/)（CVPR 2026，1.6k★）| **「下一关键点预测」统一范式**：把检测框、OCR、指代 pointing、关键点、视觉提示全部重写为「预测下一个关键点」的序列任务，3B 多模态模型 | 22M 训练数据 + GRPO 强化学习；一个模型统一感知万物，CVPR 2026 |
| **[RexSeek](https://github.com/IDEA-Research/RexSeek)** | [RexSeek: Referring any person or objects given a natural language description](https://arxiv.org/abs/2503.08507)（ICCV 2025）| 依据自然语言描述指代任意人物/物体（含遮挡、模糊等难例）| 发布 HumanRef 评测基准，提供细粒度人物指代能力 |
| **[Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker)** | [Grounded Object Referring via Chain-of-Thought Reasoning](https://arxiv.org/abs/2506.04034)（ICLR 2026）| 将 **链式思考（CoT）+ GRPO 强化学习**引入接地指代定位 | 提升指代定位的可解释性与推理鲁棒性 |
| **[ChatRex](https://github.com/IDEA-Research/ChatRex)** | [[ChatRex: Taming Multimodal LLM for Joint Perception and Understanding](https://arxiv.org/abs/2411.18363)](https://arxiv.org/abs/2411.18363) | **感知-理解解耦**：MLLM 内用双 tokenizer（区域 token 与文本 token 分开训练），避免感知与对话干扰 | 区域级细粒度感知 + 自然语言理解并存，可局部检测/分割/描述 |
| **[OpenSeeD](https://github.com/IDEA-Research/OpenSeeD)** | [A Simple Framework for Open-Vocabulary Segmentation and Detection](https://arxiv.org/abs/2303.08131)（ICCV 2023）| **首个统一开放词汇分割+检测的简单框架**：文本-像素对齐 + 文本-框对齐双任务统一训练 | 一个模型同时做开放词汇分割与检测，无需两套参数 |
| **[TAPTR](https://github.com/IDEA-Research/TAPTR)** | [TAPTR](https://github.com/IDEA-Research/TAPTR) 系列（[v1](https://arxiv.org/abs/2403.13042) ECCV 2024 / [v2](https://arxiv.org/abs/2407.16291) NeurIPS 2024 / [v3](https://arxiv.org/abs/2411.18671) ICLR 2026）| **视频任意点跟踪重构为类 DETR 集合预测**：在视频上以 query 形式预测任意点轨迹 | v1 提出范式，v2 关注遮挡处理，v3 刷新 Track-Anything 系列性能 |

---

## 五、主线 C：分割与 Grounded SAM 系列（2 仓库）

| 仓库 | 论文/说明 | 组合架构 | 关键价值 |
|---|---|---|---|
| **[Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything)** | [Grounded SAM: Assembling Open-World Models for Diverse Visual Tasks](https://arxiv.org/abs/2401.14159)（**17.7k★，组织内最高**）| **[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO)（开集检测）+ SAM（分割）+ Stable Diffusion（生成）+ Recognize Anything（识别）** 组合管线 | 文本 → 自动检测 → 分割 → 生成/编辑全链路；社区最流行的视觉基础模型组合工具，广泛用于数据自动标注、图像编辑 |
| **[Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2)** | Grounded SAM 2: Ground and Track Anything in Videos（3.7k★）| [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) + Florence-2 + **SAM 2**（视频级分割跟踪）| 把 Grounding 能力扩展到视频：文本指定目标 → 视频内持续分割与跟踪（开集视频分割跟踪） |

---

## 六、主线 D：人体 / 姿态 / 手势（8 仓库）

| 仓库 | 论文/会议 | 核心设计 | 关键价值 |
|---|---|---|---|
| **[OSX](https://github.com/IDEA-Research/OSX)** | [One-Stage 3D Whole-Body Mesh Recovery with Component Aware Transformer](https://arxiv.org/abs/2303.16160)（CVPR 2023）| **单阶段 3D 全身网格恢复**，组件感知 Transformer 分别建模手/脸/体 | 发布更大规模 **UBODY** 训练集，3D 全身重建 SOTA |
| **[DWPose](https://github.com/IDEA-Research/DWPose)** | [Effective Whole-body Pose Estimation with Two-stages Distillation](https://arxiv.org/abs/2307.15880)（ICCV 2023）| **两阶段蒸馏**：teacher→student 蒸馏 + 微调，轻量全身姿态估计 | 兼顾精度与部署效率；已被 ControlNet / Stable Diffusion WebUI 生态广泛集成，用于姿态驱动生成 |
| **[X-Pose](https://github.com/IDEA-Research/X-Pose)** | [X-Pose: Detecting Any Keypoints](https://arxiv.org/abs/2310.08530)（ECCV 2024）| **首个开集关键点检测框架**：多模态提示（文本/视觉/关键点示例）检测任意语义关键点 | 配套 **UniKPT** 数据集（13 个数据集、338 类关键点统一） |
| **[Click-Pose](https://github.com/IDEA-Research/Click-Pose)** | [Neural Interactive Keypoint Detection](https://arxiv.org/abs/2308.10174)（ICCV 2023）| **交互式关键点检测**：用户点击精调关键点（human-in-the-loop）| 适合标注场景，降低人工标注成本 |
| **[HumanArt](https://github.com/IDEA-Research/HumanArt)** | [Human-Art: A Versatile Human-Centric Dataset](https://arxiv.org/abs/2303.02760)（CVPR 2023）| 覆盖自然与人工场景（卡通/雕塑/画作）的**人类中心数据集与基准** | 提升模型对非真实场景人物的泛化 |
| **[HumanSD](https://github.com/IDEA-Research/HumanSD)** | [HumanSD: A Native Skeleton-Guided Diffusion Model for Human Image Generation](https://arxiv.org/abs/2304.04269)（ICCV 2023）| **原生骨架引导扩散模型** | 高精度可控人体图像生成（姿势/构图精确控制）|
| **[HandOSweb](https://github.com/IDEA-Research/HandOSweb)** | [HandOS: 3D Hand Reconstruction in One Stage](https://arxiv.org/abs/2412.01537) | **单阶段 3D 手部重建**：端到端集成检测+2D/3D 姿态+网格 | FreiHand 上 5.0 PA-MPJPE 达 SOTA |
| **[DiffHOI](https://github.com/IDEA-Research/DiffHOI)** | [Boosting Human-Object Interaction Detection with Text-to-Image Diffusion Model](https://arxiv.org/abs/2305.12252) | 用**文生图扩散模型**生成多样交互数据 | 数据增强思路提升人-物交互（HOI）检测 |

---

## 七、主线 E：3D 场景 / 重建 / 空间智能（6 仓库）

| 仓库 | 论文/会议 | 核心设计 | 关键价值 |
|---|---|---|---|
| **[DreamWaltz](https://github.com/IDEA-Research/DreamWaltz)** | [Make a Scene with Complex 3D Animatable Avatars](https://arxiv.org/abs/2305.12529)（NeurIPS 2023）| 文本 + **3D 骨架先验**生成可动画的复杂 3D 化身 | 高一致、可动画的 3D 化身生成 |
| **[TOSS](https://github.com/IDEA-Research/TOSS)** | [High-quality text-guided novel view synthesis from a single image](https://arxiv.org/abs/2310.10644)（ICLR 2024）| 单图 → 文本引导多视角**新视图合成** | 提升单图重建的视角一致性 |
| **[SceneMaker](https://github.com/IDEA-Research/SceneMaker)** | [Open-set 3D Scene Generation with Decoupled De-occlusion and Pose Estimation](https://arxiv.org/abs/2512.10957)（CVPR 2026）| **开放集 3D 场景生成**：解耦「去遮挡」与「姿态估计」两个模型 | 从单图生成完整开放集 3D 场景，CVPR 2026 |
| **[SegVGGT](https://github.com/IDEA-Research/SegVGGT)** | [Joint 3D Reconstruction and Instance Segmentation from Multi-View Images](https://arxiv.org/abs/2603.19926)（ECCV 2026）| 多视图图像 → **3D 重建 + 实例分割联合** | 空间智能基础能力，ECCV 2026 |
| **[SegDINO3D](https://github.com/IDEA-Research/SegDINO3D)** | [SegDINO3D: 3D Instance Segmentation Empowered by Both Image-Level and Object-Level 2D Features](https://github.com/IDEA-Research/SegDINO3D)（AAAI 2026）| 融合**图像级 + 物体级 2D 特征**的高质量 3D 实例分割，用 DINO-X 作 2D 检测模型提供特征 | 实测：ScanNet(val) mAP 64.0 / ScanNet200(val) 40.2 / ScanNet200(test) 34.6（官方 README）；作者含 Qu Jinyuan、Li Hongyang、Liu Shilong、Ren Tianhe、Zhang Lei |
| **[V-Reflection](https://github.com/IDEA-Research/V-Reflection)** | [Transforming MLLMs from Passive Observers to Active Interrogators](https://arxiv.org/abs/2604.03307) | **think-then-look 视觉反思机制**：让 MLLM 从「被动观察」变「主动质询」 | 缓解细粒度感知幻觉，提升视觉问答可靠性 |

---

## 八、主线 F：人体运动生成与理解（4 仓库）

| 仓库 | 论文/会议 | 核心设计 | 关键价值 |
|---|---|---|---|
| **[Motion-X](https://github.com/IDEA-Research/Motion-X)** | [A Large-scale 3D Expressive Whole-body Human Motion Dataset](https://motion-x-dataset.github.io/)（NeurIPS 2023）| 大规模 3D 全身运动数据集：**15.6M SMPL-X 全身姿态标注、81.1K 运动序列**，配套自动标注管线（IDEA + 清华 + 港中文深圳）| 是全身（含手指、表情）运动生成/理解的基础数据源 |
| **[HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO)** | [Text-aligned Whole-body Motion Generation](https://arxiv.org/abs/2310.12978)（ICML 2024）| **Holistic Hierarchical VQ-VAE**（全身分层次离散编码）+ **Hierarchical-GPT** + 文本-运动对齐 | 文本驱动的全身（含手指、表情）运动生成，ICML 2024 |
| **[MotionLLM](https://github.com/IDEA-Research/MotionLLM)** | [MotionLLM: Understanding Human Behaviors from Human Motions and Videos](https://arxiv.org/abs/2405.20340) | 让 LLM 理解人类运动与视频行为，**统一动作理解/生成接口** | 打通运动模态与语言模型 |
| **[MotionCLR](https://github.com/IDEA-Research/MotionCLR)** | [Motion Generation and Training-free Editing via Understanding Attention Mechanisms](https://arxiv.org/abs/2410.18977) | 通过理解**注意力机制**实现运动生成与免训练编辑 | 无需重新训练即可编辑已生成运动 |

---

## 九、主线 G：多模态 LLM 与工程工具（7 仓库）

| 仓库 | 说明 | 关键价值 |
|---|---|---|
| **[ChatRex](https://github.com/IDEA-Research/ChatRex)** | 感知-理解解耦 MLLM（见主线 B）| 区域级感知 + 对话 |
| **[RexSeek](https://github.com/IDEA-Research/RexSeek) / [Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker)** | 指代定位 + 链式推理（见主线 B）| 推理型感知 |
| **[V-Reflection](https://github.com/IDEA-Research/V-Reflection)** | 视觉反思（见主线 E）| 缓解幻觉 |
| **[deepdataspace](https://github.com/IDEA-Research/deepdataspace)** | CV 数据可视化/标注/模型分析一站式平台（264★，官网 [deepdataspace](https://github.com/IDEA-Research/deepdataspace).com）| 协同标注、智能标注、模型分析，支撑产业数据闭环 |
| **[hana](https://github.com/IDEA-Research/hana)** | Google Imagen 的 PyTorch 复现与权重 | 文生图模型工程复现 |
| **[IYFC](https://github.com/IDEA-Research/IYFC)** | seal-gpu 相关 C++ 内部基础设施 | IDEA 内部 GPU 基础设施组件 |
| **[LipsFormer](https://github.com/IDEA-Research/LipsFormer)** | 将 Lipschitz 连续性引入 ViT（Swin/CSwin）| 提升训练稳定性与鲁棒性 |

---

## 十、仓库工程细节速查表（许可证 / 依赖框架 / 安装 / 权重 / 应用）

> 许可证、Star、创建时间均来自 GitHub API 实测；安装/权重方式取自各仓库 README。

### 10.1 许可证分布（49 仓库实测）

| 许可证 | 数量 | 代表仓库 |
|---|---|---|
| Apache-2.0 | 26 | [DINO](https://github.com/IDEA-Research/DINO)、[GroundingDINO](https://github.com/IDEA-Research/GroundingDINO)、[MaskDINO](https://github.com/IDEA-Research/MaskDINO)、[detrex](https://github.com/IDEA-Research/detrex)、[Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything)、[Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2)、[DINO-X-API](https://github.com/IDEA-Research/DINO-X-API)、[DINO-X-MCP](https://github.com/IDEA-Research/DINO-X-MCP)、[OpenSeeD](https://github.com/IDEA-Research/OpenSeeD)、[DWPose](https://github.com/IDEA-Research/DWPose)、[deepdataspace](https://github.com/IDEA-Research/deepdataspace)、[SceneMaker](https://github.com/IDEA-Research/SceneMaker)、[SegDINO3D](https://github.com/IDEA-Research/SegDINO3D) 等 |
| NOASSERTION（自定义/未声明 SPDX）| 18 | [T-Rex](https://github.com/IDEA-Research/T-Rex)、[Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)、[ChatRex](https://github.com/IDEA-Research/ChatRex)、[RexSeek](https://github.com/IDEA-Research/RexSeek)、[Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker)、[Motion-X](https://github.com/IDEA-Research/Motion-X)、[HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO)、[X-Pose](https://github.com/IDEA-Research/X-Pose)、[Click-Pose](https://github.com/IDEA-Research/Click-Pose)、[ED-Pose](https://github.com/IDEA-Research/ED-Pose)、[TAPTR](https://github.com/IDEA-Research/TAPTR)、[DiffHOI](https://github.com/IDEA-Research/DiffHOI)、[DreamWaltz](https://github.com/IDEA-Research/DreamWaltz)、[MotionLLM](https://github.com/IDEA-Research/MotionLLM)、[MotionCLR](https://github.com/IDEA-Research/MotionCLR)、[MP-Former](https://github.com/IDEA-Research/MP-Former)、[3D-deformable-attention](https://github.com/IDEA-Research/3D-deformable-attention)、[SegVGGT](https://github.com/IDEA-Research/SegVGGT) |
| MIT | 1 | [OSX](https://github.com/IDEA-Research/OSX) |
| NONE（未设置）| 4 | [awesome-detection-transformer](https://github.com/IDEA-Research/awesome-detection-transformer)、[DQ-DETR](https://github.com/IDEA-Research/DQ-DETR)、[IYFC](https://github.com/IDEA-Research/IYFC)、[HandOSweb](https://github.com/IDEA-Research/HandOSweb) |

### 10.2 核心仓库工程细节

| 仓库 | 依赖/框架 | 安装方式 | 权重获取 | 应用/集成 |
|---|---|---|---|---|
| **[GroundingDINO](https://github.com/IDEA-Research/GroundingDINO)** | PyTorch、Python 3.8+ | `pip install -e .` | GitHub Release 下载 `groundingdino_swint_ogc.pth`（wget）| 官方 HF Space Demo、Colab、Gradio App；可配合 Stable Diffusion / GLIGEN 做图像编辑；集成进 Grounded SAM |
| **[DINO](https://github.com/IDEA-Research/DINO)** | PyTorch、mmdet 系 | `pip install -r requirements.txt` + `python setup.py build install` | 官方 checkpoint `checkpoint0011_4scale.pth`（Google Drive），README 注明可复现约 **49.0 AP** | 提供完整训练/评估脚本（COCO 2017）|
| **[DINO-X-API](https://github.com/IDEA-Research/DINO-X-API)** | Python + dds-cloudapi-sdk | `pip install -r requirements.txt`；`pip install dds-cloudapi-sdk --upgrade` | **云端 API 模式**（需官网注册获取 API token）| 开放世界检测/分割/姿态/OCR/描述；支持本地 demo 与云端异步任务接口 |
| **[Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything)** | PyTorch、SAM、diffusers、recognize-anything | `pip install -e segment_anything`、`pip install --no-build-isolation -e [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO)`、`pip install -e recognize-anything` | 下载 groundingdino-swin-tiny 权重 + SAM 官方权重 | 自动检测分割标注、图像编辑、数据生成；社区插件生态庞大 |
| **[Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2)** | PyTorch、SAM 2、[Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) | `pip install -e .`、`pip install --no-build-isolation -e grounding_dino` | `bash download_ckpts.sh`（SAM2 + [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) 权重）| 视频开集分割跟踪；支持 HF 模型（可用 HF_ENDPOINT 镜像加速）|
| **[detrex](https://github.com/IDEA-Research/detrex)** | PyTorch、detectron2 风格 | 文档完备（[detrex](https://github.com/IDEA-Research/detrex).readthedocs.io）| [detrex-storage](https://github.com/IDEA-Research/detrex-storage) 权重仓库 | 支持 Model-EMA / AMP / Activation Checkpoint；检测/分割/姿态估计全系模型训练 |
| **[T-Rex](https://github.com/IDEA-Research/T-Rex)** | PyTorch、ONNX | API 代码仓库 | 云端 API（[deepdataspace](https://github.com/IDEA-Research/deepdataspace).com）| 交互式视觉提示检测、目标计数、标注 |
| **[DWPose](https://github.com/IDEA-Research/DWPose)** | PyTorch、MMPose | 标准 MMPose 训练/推理 | 官方权重（onnx 分支提供 ONNX 部署版）| 已被 ControlNet / Stable-Diffusion-WebUI 集成，姿态驱动生成的事实标准 |
| **[OSX](https://github.com/IDEA-Research/OSX)** | PyTorch、SMPL/SMPL-X | 标准项目安装 | 官方权重 + UBODY 数据集 | 3D 全身网格恢复 |
| **[Motion-X](https://github.com/IDEA-Research/Motion-X)** | PyTorch | 标准项目安装 | 数据集与标注管线 | 大规模全身运动数据（NeurIPS 2023 数据集）|
| **[HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO)** | PyTorch、SMPL-X | 标准项目安装 | 官方权重 | 文本→全身运动生成（ICML 2024）|
| **[deepdataspace](https://github.com/IDEA-Research/deepdataspace)** | Python + Web 前端 | 标准部署 | — | CV 数据标注/可视化/模型分析平台，对接 DINO-X API |

---

## 十一、全量论文清单（含 GitHub 仓库之外的论文）

> 仓库对应论文见「十二、论文速查表」；本表补充**未纳入 IDEA-Research 仓库**的高影响力论文（多为张磊微软研究院时期及跨机构合作代表作，作者含张磊/团队核心成员），引用量为 Google Scholar / Semantic Scholar 采集的近似值。

### 11.1 微软研究院时期奠基性 / 高引论文（无组织仓库）

| 论文标题 | 会议/年份 | 代表作者（含张磊）| 引用量（约）|
|---|---|---|---|
| Bottom-up and top-down attention for image captioning and VQA | CVPR 2018 | Anderson, He, Buehler, Teney, Johnson, Gould, Zhang | ~6,300 |
| Are transformers effective for time series forecasting? | AAAI 2023 | Zeng, Chen, Zhang, Xu | ~4,100 |
| CvT: Introducing Convolutions to Vision Transformers | ICCV 2021 | Wu, Xiao, Codella, Liu, Dai, Yuan, Zhang | ~3,150 |
| MS-Celeb-1M: A dataset and benchmark for large-scale face recognition | ECCV 2016 | Guo, Zhang, Hu, He, Gao | ~2,710 |
| Oscar: Object-Semantics Aligned Pre-training for Vision-Language Tasks | ECCV 2020 | Li, Yin, Li, Zhang, Gao | ~2,640 |
| Grounded Language-Image Pre-training (GLIP) | CVPR 2022 | Li, Zhang, Hwang, Chang, Gao | ~1,825 |
| VinVL: Revisiting Visual Representations in Vision-Language Models | CVPR 2021 | Zhang, Li, Hu, Yang, Wang, Choi, Gao | ~1,560 |
| Unified Vision-Language Pre-Training for Image Captioning and VQA (VLP) | AAAI 2020 | Zhou, Palangi, Zhang, Hu, Corso, Gao | ~1,210 |
| HigherHRNet: Scale-Aware Representation Learning for Bottom-Up Human Pose | CVPR 2020 | Cheng, Xiao, Wang, Shi, Huang, Zhang | ~1,210 |
| Dynamic Head: Unifying Object Detection Heads with Attentions | CVPR 2021 | Dai, Chen, Xiao, Chen, Liu, Yuan, Zhang | ~1,190 |
| [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR) | ICLR 2022 | Liu, Li, Zhang, Zhu | ~1,400 |
| [DN-DETR](https://github.com/IDEA-Research/DN-DETR) | CVPR 2022 | Li, Zhang, Liu, Ni | ~1,579 |

### 11.2 其他跨领域代表作（检测 / 分割 / 多模态 / 3D / 姿态 / 导航）

| 方向 | 论文 / 会议 | 说明 |
|---|---|---|
| 高效姿态 | Lite-HRNet（CVPR 2021）| 轻量高分辨率人体姿态网络 |
| 检测 | Dynamic DETR（ICCV 2021）| 动态注意力加速 DETR |
| 视觉编码 | Multi-Scale Vision Longformer（ICCV 2021）| 高分辨率图像编码 |
| 自监督 | SEED: Self-supervised Distillation（ICLR 2021）| 视觉自监督蒸馏 |
| ViT 稀疏化 | Chasing Sparsity in Vision Transformers（NeurIPS 2021）| ViT 稀疏性研究 |
| 3D 点云 | Voxel Set Transformer（CVPR 2022）| 点云 3D 检测 set-to-set 方法 |
| 视觉语言导航 | Reinforced Cross-Modal Matching for VLN（AAAI 2019）| 强化跨模态匹配 + 自监督模仿学习 |
| 人脸/带噪标签 | CleanNet（ICCV 2019）、AnnoSearch（ACM MM 2011）| 带噪声标签训练、人脸检索 |

### 11.3 2024—2026 新范式跨模态感知（部分有仓库，供全景参考）

| 论文 | 年份/会议 | 要点 |
|---|---|---|
| [DINO-X: A Unified Vision Model for Open-World Object Detection and Understanding](https://arxiv.org/abs/2411.14347) | 2024.11（arXiv 2411.14347）| 统一开放世界检测与理解，Grounding-100M 数据集 |
| [ChatRex](https://github.com/IDEA-Research/ChatRex): Taming Multimodal LLM for Joint Perception and Understanding | 2024（arXiv 2411.18363）| 感知-理解解耦 MLLM |
| [T-Rex2: Text-Visual Prompt Synergy](https://arxiv.org/abs/2403.14610) | ECCV 2024 | 通用检测的文本-视觉提示协同 |
| [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni): Detect Anything via Next Point Prediction | CVPR 2026 | 下一关键点预测统一感知 |
| [Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker)（CoT 接地指代）| ICLR 2026 | 链式推理指代定位 |
| Referring to Any Person | 2025 | 人物级指代 |
| Perceive Anything | NeurIPS 2025 | 图像/视频识别-解释-描述-分割 |

---

## 十二、论文速查表（49 仓库 ↔ 论文 ↔ 会议 ↔ arXiv 全量对照）

| # | 仓库 | 论文 | 会议/年份 | arXiv |
|---|---|---|---|---|
| 1 | [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR) | Dynamic Anchor Boxes are Better Queries for DETR | ICLR 2022 | [2201.12329](https://arxiv.org/abs/2201.12329) |
| 2 | [DN-DETR](https://github.com/IDEA-Research/DN-DETR) | Accelerate DETR Training by Introducing Query DeNoising | CVPR 2022 Oral | [2203.01305](https://arxiv.org/abs/2203.01305) |
| 3 | [DINO](https://github.com/IDEA-Research/DINO) | DETR with Improved DeNoising Anchor Boxes | ICLR 2023 | [2203.03605](https://arxiv.org/abs/2203.03605) |
| 4 | [Stable-DINO](https://github.com/IDEA-Research/Stable-DINO) | Detection Transformer with Stable Matching | ICCV 2023 | [2304.04742](https://arxiv.org/abs/2304.04742) |
| 5 | [Lite-DETR](https://github.com/IDEA-Research/Lite-DETR) | An Interleaved Multi-Scale Encoder for Efficient DETR | CVPR 2023 | [2303.07335](https://arxiv.org/abs/2303.07335) |
| 6 | [MaskDINO](https://github.com/IDEA-Research/MaskDINO) | Unified Transformer-based Framework for Detection and Segmentation | CVPR 2023 | [2206.02777](https://arxiv.org/abs/2206.02777) |
| 7 | [MP-Former](https://github.com/IDEA-Research/MP-Former) | Mask-Piloted Transformer for Image Segmentation | CVPR 2023 | [2303.07336](https://arxiv.org/abs/2303.07336) |
| 8 | [ED-Pose](https://github.com/IDEA-Research/ED-Pose) | Explicit Box Detection Unifies End-to-End Multi-Person Pose Estimation | ICLR 2023 | [2302.01593](https://arxiv.org/abs/2302.01593) |
| 9 | [DQ-DETR](https://github.com/IDEA-Research/DQ-DETR) | Dual Query Detection Transformer for Phrase Extraction and Grounding | AAAI 2023 | [2211.15516](https://arxiv.org/abs/2211.15516) |
| 10 | [3D-deformable-attention](https://github.com/IDEA-Research/3D-deformable-attention) | DFA3D: 3D Deformable Attention For 2D-to-3D Feature Lifting | ICCV 2023 | [2307.12972](https://arxiv.org/abs/2307.12972) |
| 11 | [DisCo-CLIP](https://github.com/IDEA-Research/DisCo-CLIP) | Distributed Contrastive Loss for Memory Efficient CLIP Training | — | [2304.08480](https://arxiv.org/abs/2304.08480) |
| 12 | [detrex](https://github.com/IDEA-Research/detrex) | [detrex](https://github.com/IDEA-Research/detrex): Benchmarking and Improving Transferability of Pretrained ViTs on Detection | 研究平台 | [2306.07265](https://arxiv.org/abs/2306.07265) |
| 13 | [GroundingDINO](https://github.com/IDEA-Research/GroundingDINO) | Marrying [DINO](https://github.com/IDEA-Research/DINO) with Grounded Pre-Training for Open-Set Object Detection | ECCV 2024 | [2303.05499](https://arxiv.org/abs/2303.05499) |
| 14 | [Grounding-DINO-1.5-API](https://github.com/IDEA-Research/Grounding-DINO-1.5-API) | Advance the Edge of Open-Set Object Detection | 技术报告 | [2405.10300](https://arxiv.org/abs/2405.10300) |
| 15 | [T-Rex](https://github.com/IDEA-Research/T-Rex) | T-Rex2: Towards Generic Object Detection via Text-Visual Prompt Synergy | ECCV 2024 | [2403.14610](https://arxiv.org/abs/2403.14610) |
| 16 | [DINO-X-API](https://github.com/IDEA-Research/DINO-X-API) | DINO-X: A Unified Vision Model for Open-World Detection and Understanding | — | [2411.14347](https://arxiv.org/abs/2411.14347) |
| 17 | [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni) | Detect Anything via Next Point Prediction | CVPR 2026 | [项目页](https://rex-omni.github.io/) |
| 18 | [RexSeek](https://github.com/IDEA-Research/RexSeek) | Referring any person or objects given a natural language description | ICCV 2025 | [2503.08507](https://arxiv.org/abs/2503.08507) |
| 19 | [Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker) | Grounded Object Referring via Chain-of-Thought Reasoning | ICLR 2026 | [2506.04034](https://arxiv.org/abs/2506.04034) |
| 20 | [ChatRex](https://github.com/IDEA-Research/ChatRex) | Taming Multimodal LLM for Joint Perception and Understanding | — | [2411.18363](https://arxiv.org/abs/2411.18363) |
| 21 | [OpenSeeD](https://github.com/IDEA-Research/OpenSeeD) | A Simple Framework for Open-Vocabulary Segmentation and Detection | ICCV 2023 | [2303.08131](https://arxiv.org/abs/2303.08131) |
| 22 | [TAPTR](https://github.com/IDEA-Research/TAPTR) | Tracking Any Point with Transformers as Detection | ECCV 2024 | [2403.13042](https://arxiv.org/abs/2403.13042) |
| 23 | [TAPTR](https://github.com/IDEA-Research/TAPTR) | TAPTRv2: Effective Point Tracking with Attention to Occlusion | NeurIPS 2024 | [2407.16291](https://arxiv.org/abs/2407.16291) |
| 24 | [TAPTR](https://github.com/IDEA-Research/TAPTR) | TAPTRv3 | ICLR 2026 | [2411.18671](https://arxiv.org/abs/2411.18671) |
| 25 | [Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) | Grounded SAM: Assembling Open-World Models for Diverse Visual Tasks | — | [2401.14159](https://arxiv.org/abs/2401.14159) |
| 26 | [OSX](https://github.com/IDEA-Research/OSX) | One-Stage 3D Whole-Body Mesh Recovery with Component Aware Transformer | CVPR 2023 | [2303.16160](https://arxiv.org/abs/2303.16160) |
| 27 | [DWPose](https://github.com/IDEA-Research/DWPose) | Effective Whole-body Pose Estimation with Two-stages Distillation | ICCV 2023 | [2307.15880](https://arxiv.org/abs/2307.15880) |
| 28 | [X-Pose](https://github.com/IDEA-Research/X-Pose) | [X-Pose](https://github.com/IDEA-Research/X-Pose): Detecting Any Keypoints | ECCV 2024 | [2310.08530](https://arxiv.org/abs/2310.08530) |
| 29 | [Click-Pose](https://github.com/IDEA-Research/Click-Pose) | Neural Interactive Keypoint Detection | ICCV 2023 | [2308.10174](https://arxiv.org/abs/2308.10174) |
| 30 | [HumanArt](https://github.com/IDEA-Research/HumanArt) | Human-Art: A Versatile Human-Centric Dataset | CVPR 2023 | [2303.02760](https://arxiv.org/abs/2303.02760) |
| 31 | [HumanSD](https://github.com/IDEA-Research/HumanSD) | Native Skeleton-Guided Diffusion Model for Human Image Generation | ICCV 2023 | [2304.04269](https://arxiv.org/abs/2304.04269) |
| 32 | [HandOSweb](https://github.com/IDEA-Research/HandOSweb) | HandOS: 3D Hand Reconstruction in One Stage | — | [2412.01537](https://arxiv.org/abs/2412.01537) |
| 33 | [DiffHOI](https://github.com/IDEA-Research/DiffHOI) | Boosting Human-Object Interaction Detection with Text-to-Image Diffusion Model | — | [2305.12252](https://arxiv.org/abs/2305.12252) |
| 34 | [DreamWaltz](https://github.com/IDEA-Research/DreamWaltz) | Make a Scene with Complex 3D Animatable Avatars | NeurIPS 2023 | [2305.12529](https://arxiv.org/abs/2305.12529) |
| 35 | [TOSS](https://github.com/IDEA-Research/TOSS) | High-quality text-guided novel view synthesis from a single image | ICLR 2024 | [2310.10644](https://arxiv.org/abs/2310.10644) |
| 36 | [SceneMaker](https://github.com/IDEA-Research/SceneMaker) | Open-set 3D Scene Generation with Decoupled De-occlusion and Pose Estimation | CVPR 2026 | [2512.10957](https://arxiv.org/abs/2512.10957) |
| 37 | [SegVGGT](https://github.com/IDEA-Research/SegVGGT) | Joint 3D Reconstruction and Instance Segmentation from Multi-View Images | ECCV 2026 | [2603.19926](https://arxiv.org/abs/2603.19926) |
| 38 | [SegDINO3D](https://github.com/IDEA-Research/SegDINO3D) | 3D Instance Segmentation Empowered by Image-Level and Object-Level 2D Features | AAAI 2026 | [未见官方 arXiv，见仓库](<https://github.com/IDEA-Research/SegDINO3D>) |
| 39 | [V-Reflection](https://github.com/IDEA-Research/V-Reflection) | Transforming MLLMs from Passive Observers to Active Interrogators | — | [2604.03307](https://arxiv.org/abs/2604.03307) |
| 40 | [Motion-X](https://github.com/IDEA-Research/Motion-X) | A Large-scale 3D Expressive Whole-body Human Motion Dataset | NeurIPS 2023 | [项目页](https://motion-x-dataset.github.io/) |
| 41 | [HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO) | Text-aligned Whole-body Motion Generation | ICML 2024 | [2310.12978](https://arxiv.org/abs/2310.12978) |
| 42 | [MotionLLM](https://github.com/IDEA-Research/MotionLLM) | Understanding Human Behaviors from Human Motions and Videos | — | [2405.20340](https://arxiv.org/abs/2405.20340) |
| 43 | [MotionCLR](https://github.com/IDEA-Research/MotionCLR) | Motion Generation and Training-free Editing via Understanding Attention Mechanisms | — | [2410.18977](https://arxiv.org/abs/2410.18977) |
| 44 | [Grounded-SAM-2](https://github.com/IDEA-Research/Grounded-SAM-2) | Ground and Track Anything in Videos（应用仓库）| — | [2401.14159](https://arxiv.org/abs/2401.14159) |
| 45 | [deepdataspace](https://github.com/IDEA-Research/deepdataspace) | CV 数据可视化/标注/模型分析工具（非论文）| — | [官网](https://deepdataspace.com) |
| 46 | [hana](https://github.com/IDEA-Research/hana) | Imagen 第三方实现（非论文）| — | — |
| 47 | [IYFC](https://github.com/IDEA-Research/IYFC) | IDEA 内部 GPU 基础设施（非论文）| — | — |
| 48 | [LipsFormer](https://github.com/IDEA-Research/LipsFormer) | Introducing Lipschitz Continuity to Vision Transformers | — | — |
| 49 | [detrex-storage](https://github.com/IDEA-Research/detrex-storage) / [awesome-detection-transformer](https://github.com/IDEA-Research/awesome-detection-transformer) | 权重仓库 / 论文列表 | — | — |

---

## 十三、代表性论文时间线（2022—2026）

| 年份 | 会议 | 论文/工作 |
|---|---|---|
| 2022 | ICLR | [DAB-DETR](https://github.com/IDEA-Research/DAB-DETR) |
| 2022 | CVPR (Oral) | [DN-DETR](https://github.com/IDEA-Research/DN-DETR) |
| 2023 | ICLR | [DINO](https://github.com/IDEA-Research/DINO)、[ED-Pose](https://github.com/IDEA-Research/ED-Pose) |
| 2023 | CVPR | [MaskDINO](https://github.com/IDEA-Research/MaskDINO)、[Lite-DETR](https://github.com/IDEA-Research/Lite-DETR)、[MP-Former](https://github.com/IDEA-Research/MP-Former)、[OSX](https://github.com/IDEA-Research/OSX)、[HumanArt](https://github.com/IDEA-Research/HumanArt)、[HumanSD](https://github.com/IDEA-Research/HumanSD) |
| 2023 | ICCV | [Stable-DINO](https://github.com/IDEA-Research/Stable-DINO)、DFA3D、[OpenSeeD](https://github.com/IDEA-Research/OpenSeeD)、[DWPose](https://github.com/IDEA-Research/DWPose)、[Click-Pose](https://github.com/IDEA-Research/Click-Pose) |
| 2023 | NeurIPS | [Motion-X](https://github.com/IDEA-Research/Motion-X)、[DreamWaltz](https://github.com/IDEA-Research/DreamWaltz) |
| 2023 | AAAI | [DQ-DETR](https://github.com/IDEA-Research/DQ-DETR) |
| 2024 | ECCV | [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO)、T-Rex2、[X-Pose](https://github.com/IDEA-Research/X-Pose)、[TAPTR](https://github.com/IDEA-Research/TAPTR) |
| 2024 | ICML | [HumanTOMATO](https://github.com/IDEA-Research/HumanTOMATO) |
| 2024 | ICLR | [TOSS](https://github.com/IDEA-Research/TOSS) |
| 2024 | NeurIPS | TAPTRv2 |
| 2024 | arXiv | [Grounding DINO 1.5](https://github.com/IDEA-Research/Grounding-DINO-1.5-API)、[ChatRex](https://github.com/IDEA-Research/ChatRex)、DINO-X、[MotionLLM](https://github.com/IDEA-Research/MotionLLM)、[MotionCLR](https://github.com/IDEA-Research/MotionCLR)、HandOS、[V-Reflection](https://github.com/IDEA-Research/V-Reflection) |
| 2025 | ICCV | [RexSeek](https://github.com/IDEA-Research/RexSeek) |
| 2026 | CVPR | [Rex-Omni](https://github.com/IDEA-Research/Rex-Omni)、[SceneMaker](https://github.com/IDEA-Research/SceneMaker) |
| 2026 | ICLR | TAPTRv3、[Rex-Thinker](https://github.com/IDEA-Research/Rex-Thinker) |
| 2026 | ECCV | [SegVGGT](https://github.com/IDEA-Research/SegVGGT) |
| 2026 | AAAI | [SegDINO3D](https://github.com/IDEA-Research/SegDINO3D) |

---

## 十四、技术影响力评估与总结

### 14.1 影响力六大维度

1. **DETR 技术链完整闭环**：DAB/DN 解决收敛 → DINO 性能霸榜（COCO 登顶 5 个月）→ detrex 平台化（2.3k★，全系模型），构成当前 DETR 系检测事实标准之一，学术引用与工业落地双高。
2. **开放世界感知的开创者**：Grounding DINO 定义「文本开集检测」范式并成为 Grounded SAM 生态基石（组织内两个万星项目：Grounded-Segment-Anything 17.7k★、GroundingDINO 10.5k★），随后演进为 DINO-X 通用视觉大模型。
3. **统一感知范式的演进**：从「检测器」走向「object-centric 视觉模型」再到「下一关键点预测」MLLM（Rex-Omni），逐步把检测、分割、姿态、OCR、指代统一到单一框架。
4. **从 2D 感知到 3D 空间智能**：SceneMaker、SegVGGT、SegDINO3D 等 2026 年新作显示组织正向开放集 3D 场景理解与具身智能迁移。
5. **人体/运动全栈**：从 3D 全身重建（OSX）、轻量姿态（DWPose，已进 ControlNet 生态）到大尺度运动数据（Motion-X）与生成理解（HumanTOMATO、MotionLLM），人类中心感知链路完整。
6. **基础设施与生态输出**：deepdataspace（数据标注）、DINO-X-MCP（视觉×LLM 生态）、T-Rex Label（标注工具）构成科研→产品转化闭环，并孵化视启未来实现商业化。

### 14.2 趋势研判

- **范式收敛**：检测/分割/姿态/OCR 正收敛为「一个视觉大模型」+「一个统一预测范式」，Rex-Omni 的 next point prediction 是当前代表。
- **空间智能 + 具身**：DINO-X Grasp、SegDINO3D 等显示组织正切入机器人视觉中枢（视启未来的核心叙事）。
- **开源策略**：核心模型走 Apache-2.0 开源建立生态，商业化通过 API/云平台（deepdataspace、DINO-X API、MCP）变现，是「开源影响力 + 云服务收费」的典型范式。

---



---

## 十五、核心技术深度解析

> 本章对 IDEA-Research 最具代表性的技术创新做原理级拆解，补充前文表格中未能展开的机制细节、数学直觉与设计动机。

### 15.1 DETR 收敛难题的本质与 DAB/DN/DINO 的解决路径

**问题根源**：原始 DETR（Carion et al., 2020）用一组可学习 query 与 GT 做二分匹配（Hungarian Matching），但存在两个根本性困难：

1. **query 无物理锚点**：可学习 query 是抽象向量，与图像空间位置无显式对应，decoder 需自行学会"哪个 query 负责哪个区域"，早期训练信号极弱。
2. **二分匹配不稳定**：训练初期预测框质量差，匹配结果在 epoch 间剧烈抖动（同一 GT 可能在不同 epoch 匹配到不同 query），导致梯度方向不一致，需 500 epoch 才能收敛。

**DAB-DETR 的突破**：将 query 从抽象向量改为 **4D 动态锚框 (x, y, w, h)**，每一层 decoder 用预测框更新锚框并注入正弦位置编码。这一改动的核心价值是：
- query 具备了**空间可解释性**（每个 query 对应图像中一个具体区域）；
- 锚框随层迭代细化，形成由粗到精的定位流程；
- 收敛速度从 108+ epoch 降至 12 epoch 即可达到相当精度。

**DN-DETR 的去噪训练**：在 DAB 基础上，训练时向 decoder 额外注入一组"加噪 GT 框"（对 GT 坐标加随机扰动）作为 query，并通过 attention mask 隔离去噪 query 与正常 query 的交互。decoder 学会从加噪框回归到 GT，这相当于：
- 为二分匹配提供了**稳定的辅助监督信号**（去噪任务的匹配是确定的，不存在抖动）；
- 去噪 query 的梯度帮助 decoder 更快学会框回归能力；
- 去噪与正常检测共享 decoder 参数，推理时无需额外计算。

**DINO 的三位一体**：DINO 在 DAB + DN 基础上引入三项关键创新，将性能推至 COCO 登顶：

| 创新 | 机制 | 解决的问题 |
|---|---|---|
| **对比去噪（CDN）** | 注入正样本对（小幅加噪）和负样本对（大幅加噪，类别也可能错配），负样本可回退到正样本 | 增强 decoder 对模糊/干扰框的判别力，提升分类质量 |
| **混合匹配（Mixed Matching）** | 一次前向中同时用"预测框↔GT"和"GT↔GT"两种匹配做监督 | 训练早期预测框质量差时，GT-GT 匹配提供稳定监督；训练后期预测- GT 匹配提供精确梯度 |
| **look-forward-twice** | 用下一层 decoder 的预测框更新当前层 query，再计算辅助 loss | 让浅层 query 获得更准确的位置信息，缓解层间信息传递滞后 |

这三项设计共同作用，使 DINO 在 R50 4scale 上 12 epoch 达到 50.9 AP，登顶 COCO 并霸榜 5 个月，成为后续几乎所有 DETR 系工作的基础骨架。

### 15.2 Grounding DINO 的跨模态融合机制

Grounding DINO 的核心挑战是：如何让检测模型理解**任意文本提示**并定位对应物体，而不局限于训练时的固定类别集。

**架构设计**：

```
图像 ──► Image Backbone (Swin-T/L) ──► 多尺度图像特征
                                                │
文本 ──► Text Backbone (BERT-base) ──► 文本特征 ──┤
                                                ▼
                                    ┌── Feature Enhancer ──┐
                                    │  (Self-Attn + Cross-Attn) │
                                    └──────────┬───────────────┘
                                               ▼
                                    Language-Guided Query Selection
                                    (用文本特征从图像特征中选 query)
                                               ▼
                                    DINO-style Decoder (带跨模态注意力)
                                               ▼
                                    开集检测框 + 文本对齐的分类logits
```

**三个关键模块的设计动机**：

1. **Feature Enhancer**：图像特征与文本特征先经过一个由自注意力和跨注意力组成的增强模块进行**双向深度融合**。这不同于简单的跨模态注意力（只让图像看文本），而是让两种模态在进入 decoder 前就充分交换信息，使图像特征携带语义、文本特征携带空间线索。

2. **Language-Guided Query Selection**：传统 DETR 的 query 是可学习的（固定数量、无语义），Grounding DINO 改为**用文本特征从图像特征中动态选择 query**——计算文本 token 与图像 token 的相似度，取 top-k 图像 token 作为 decoder query 的初始化。这确保了 query 与输入文本语义相关，避免无关 query 浪费计算。

3. **Grounded Pre-Training**：训练使用大规模图文对数据（检测框 + 对应文本描述），让模型学会"文本短语 ↔ 图像区域"的对齐。这一预训练范式使得模型可以泛化到训练时未见过的类别（zero-shot 检测）。

**与 GLIP 的本质区别**：GLIP（Li et al., CVPR 2022，张磊在微软时参与）将检测重构为短语接地（phrase grounding），用一阶段检测器 + 文本对比学习；Grounding DINO 则基于 DETR 二阶段架构，用 feature enhancer + language-guided query selection 实现更深度的跨模态融合。两者一脉相承（张磊是 GLIP 通讯作者之一），但 Grounding DINO 在 DETR 架构上实现了更强的开集检测能力。

### 15.3 DINO-X 的 object-centric 统一架构

DINO-X 将检测、分割、姿态估计、OCR、区域描述等任务统一到一个 **object-centric** 框架中，其核心设计哲学是：**以物体为中心，所有任务都是对物体 query 的不同预测头**。

**架构要点**：

```
输入图像
    │
    ▼
ViT Backbone (大规模预训练)
    │
    ▼
物体 Query 初始化 (文本/视觉/自定义提示)
    │
    ├──► 检测头：预测框 + 类别 (开放词汇)
    ├──► 分割头：预测实例掩码
    ├──► 姿态头：预测关键点 (人体/通用物体)
    ├──► OCR 头：预测文本区域 + 内容
    └──► 描述头：生成区域级自然语言描述
```

**统一的关键**：
- 所有任务共享同一个 ViT backbone 和同一组物体 query；
- 不同任务只是 query 上的不同预测头，推理时可按需启用；
- 训练使用 **Grounding-100M** 大规模数据集（100M 级图文对，涵盖检测/分割/姿态/OCR 等多种标注），通过多任务联合训练实现能力统一。

**与 Grounding DINO 1.5 的关系**：Grounding DINO 1.5 是 DINO-X 的"检测专用版"（更强 backbone + 更大数据），DINO-X 则在 1.5 基础上扩展了分割/姿态/OCR/描述等任务头，是真正的"通用视觉大模型"。

### 15.4 Rex-Omni：下一关键点预测范式的革命性

Rex-Omni（CVPR 2026）提出了一种全新的统一感知范式：**将所有视觉感知任务重写为"预测下一个关键点"的序列生成任务**。

**范式转换**：

| 传统任务 | 传统表示 | Next Point Prediction 表示 |
|---|---|---|
| 目标检测 | 预测框 (x1,y1,x2,y2) | 依次预测左上角点 → 右下角点 |
| OCR | 检测文本框 + 识别文字 | 预测文本区域角点 + 逐字符中心点 |
| 关键点检测 | 回归所有关键点坐标 | 逐个预测关键点序列 |
| 指代定位 (Referring) | 输出目标框 | 预测目标中心点（pointing） |
| 视觉提示检测 | 框选示例 → 检测同类 | 预测示例框角点 → 预测所有目标角点 |

**为什么这是革命性的**：
1. **任务统一**：所有感知任务都变成同一个"序列点预测"问题，无需为每个任务设计专用头和损失函数；
2. **自然支持交互式感知**：序列生成范式天然支持"用户给一个点 → 模型预测下一个点"的人机协作模式；
3. **与 LLM 范式对齐**：next point prediction 类似于 LLM 的 next token prediction，使得视觉感知模型可以复用大语言模型的训练技术（如 GRPO 强化学习）；
4. **3B 多模态模型**：Rex-Omni 是一个 3B 参数的多模态模型，使用 22M 训练数据 + GRPO 强化学习训练，一个模型统一感知万物。

**GRPO 强化学习的作用**：传统监督学习训练点预测时，每个点的损失是独立的，无法优化"最终检测框质量"这一整体目标。GRPO（Group Relative Policy Optimization）将整个点序列视为一个 action，以最终检测框的 AP 作为 reward，通过强化学习直接优化端到端性能，这是 Rex-Omni 性能突破的关键之一。

### 15.5 TAPTR：将点跟踪重构为集合预测

TAPTR（Tracking Any Point with Transformers as Detection）系列的核心洞察是：**视频中的任意点跟踪可以重构为一个类 DETR 的集合预测问题**。

**传统方法 vs TAPTR**：
- 传统点跟踪（如 RAFT、PIPs）：基于光流或循环网络，逐帧传播点位置，对遮挡和快速运动敏感；
- TAPTR：将视频中一个点的完整轨迹视为一个"轨迹 query"，用 DETR 风格的集合预测直接输出整条轨迹，而非逐帧传播。

**三代演进**：
- **v1（ECCV 2024）**：提出范式，用时空 Transformer 编码视频，query 直接预测轨迹序列；
- **v2（NeurIPS 2024）**：重点解决遮挡问题，引入遮挡感知的注意力机制，让模型学会"点被遮挡时轨迹如何推断"；
- **v3（ICLR 2026）**：刷新 Track-Anything 系列性能，进一步提升长视频和复杂场景下的跟踪精度。

TAPTR 的意义在于：它将 DETR 的集合预测思想从图像检测扩展到了视频时序预测，为视频理解提供了新的范式。

---

## 十六、横向对比分析：与同领域工作的定位差异

> 本章将 IDEA-Research 的核心工作置于全球计算机视觉研究的大背景中，与同领域代表性工作做横向对比，明确其技术定位与差异化价值。

### 16.1 开放集/开放词汇检测领域对比

开放集检测（Open-Set / Open-Vocabulary Detection）是近年来检测领域最活跃的方向，IDEA-Research 的 Grounding DINO 系列是其中的标杆工作之一。

| 工作 | 机构 | 架构基础 | 核心方法 | 开集能力 | 代表指标 |
|---|---|---|---|---|---|
| **GLIP** | 微软（张磊参与）| 一阶段检测器 (ATSS) | 将检测重构为短语接地，文本-区域对比学习 | 强，支持任意短语 | COCO zero-shot ~49.8 AP |
| **OWL-ViT** | Google | ViT + 检测头 | 图像-文本对比预训练 + 轻量检测头 | 中等，适合简单类别 | LVIS zero-shot ~31.5 AP |
| **OV-DETR** | 港中文/上海AI Lab | DETR | 开放词汇 DETR，用 CLIP 特征做分类 | 中等 | COCO zero-shot ~42.5 AP |
| **Grounding DINO** | **IDEA-Research** | **DETR (DINO)** | **Feature Enhancer + Language-Guided Query Selection + Grounded Pre-training** | **极强，支持复杂短语/句子** | **COCO zero-shot 52.5 AP (Swin-L)** |
| **Grounding DINO 1.5** | **IDEA-Research** | **ViT-2B + DINO** | **更大 backbone + 20M+ 训练图像 + 多任务** | **当前最强开集检测之一** | **COCO ~59.9 AP, LVIS ~67.3** |
| **YOLO-World** | Tencent/AlexeyAB | YOLOv8 | 实时开放词汇检测，YOLO 架构 + 文本提示 | 强，主打实时性 | LVIS zero-shot ~37.6 AP (速度快) |
| **DINO-X** | **IDEA-Research** | **ViT + object-centric** | **统一检测/分割/姿态/OCR/描述** | **最强，多任务统一** | **LVIS ~63.9 AP (Pro)** |

**定位差异总结**：
- **Grounding DINO vs GLIP**：两者一脉相承（张磊都是核心作者），GLIP 是一阶段检测器上的开放词汇探索，Grounding DINO 是 DETR 架构上的深度跨模态融合，后者在复杂短语理解和定位精度上更优；
- **Grounding DINO vs OWL-ViT / OV-DETR**：后两者主要用 CLIP 对比特征做开放词汇分类，跨模态融合较浅；Grounding DINO 的 feature enhancer 实现了更深的双向融合，language-guided query selection 确保 query 与文本相关，因此在复杂场景下更鲁棒；
- **Grounding DINO vs YOLO-World**：YOLO-World 主打实时性（YOLO 架构），适合端侧部署；Grounding DINO 主打精度和复杂语义理解，适合云端/高精度场景。Grounding DINO 1.5 Edge 版本则在尝试兼顾精度与部署；
- **DINO-X 的独特性**：DINO-X 不只是开放集检测器，而是统一视觉大模型，同时支持分割/姿态/OCR/描述，这是其他工作尚未实现的多任务统一。

### 16.2 统一视觉大模型对比

2024 年以来，"统一视觉大模型"成为视觉领域的新赛道，多家机构推出了各自的统一感知模型。

| 模型 | 机构 | 发布时间 | 统一任务 | 架构 | 开源 |
|---|---|---|---|---|---|
| **Florence-2** | Microsoft | 2023.11 | 检测/分割/OCR/描述/分类 | 序列到序列 (ViT + 语言模型) | 是 (MIT) |
| **DINO-X** | **IDEA-Research** | **2024.11** | **检测/分割/姿态/OCR/区域描述** | **object-centric Transformer** | **API + 部分开源** |
| **Unified-IO 2** | AI2 | 2024 | 检测/分割/深度/法线/VQA | 统一序列建模 | 是 |
| **Pix2Seq** | Google | 2022/2023 | 检测/分割/关键点 | 序列生成 (ViT + Transformer) | 是 |
| **SEEM** | 南洋理工 | 2023 | 检测/分割/指代 | 统一提示接口 | 是 |
| **Rex-Omni** | **IDEA-Research** | **2025.10** | **检测/OCR/关键点/指代/视觉提示** | **Next Point Prediction (3B MLLM)** | **待开源** |

**DINO-X 的差异化**：
- **object-centric 设计**：DINO-X 以物体 query 为中心，所有任务都是物体 query 上的预测头，这与 Florence-2 的"图像到序列"纯生成范式不同。object-centric 设计使得物体级别的多任务联合更自然，检测/分割/姿态共享同一组物体表示；
- **开放世界基因**：DINO-X 从 Grounding DINO 演进而来，天生具备强开放词汇检测能力，这是 Florence-2 等通用模型在检测精度上难以匹敌的；
- **姿态估计**：DINO-X 支持人体/通用物体姿态估计，这是其他统一视觉模型较少覆盖的任务；
- **Rex-Omni 的范式创新**：Rex-Omni 用 next point prediction 统一感知，是比 DINO-X 更激进的范式统一，代表了 IDEA-Research 在统一感知方向的最新探索。

### 16.3 视觉提示范式对比

视觉提示（Visual Prompting）是指通过用户提供的视觉示例（框选/点选/涂鸦）来指定检测目标，T-Rex 是这一方向的代表性工作。

| 工作 | 机构 | 提示类型 | 核心能力 |
|---|---|---|---|
| **SAM** | Meta | 点/框/掩码提示 | 分割任意物体（不区分类别） |
| **T-Rex / T-Rex2** | **IDEA-Research** | **文本 + 视觉提示（框选示例）** | **检测与示例同类的所有物体（区分类别）** |
| **SEEM** | 南洋理工 | 点/框/文本/涂鸦 | 分割 + 检测（多模态提示） |
| **Painter** | 清华 | 图像示例（in-context） | 用示例图像指定任务和目标 |
| **Grounded-SAM** | **IDEA-Research** | **文本 → 自动检测 → 分割** | **文本指定类别，自动检测+分割** |

**T-Rex 的独特价值**：
- SAM 只能分割"用户点/框选的那个物体"，无法区分"这是什么类别"，也无法自动找到图像中所有同类物体；
- T-Rex 支持"框选一个示例 → 检测图像中所有同类物体"，这是数据标注、目标计数等场景的核心需求；
- T-Rex2 进一步实现了**文本提示与视觉提示的协同**：用户可以同时给文本描述和视觉示例，两种提示互补，提升检测精度。

### 16.4 3D 空间智能领域对比

| 工作 | 机构 | 任务 | 方法特点 |
|---|---|---|---|
| **SceneMaker** | **IDEA-Research** | 开放集 3D 场景生成 | 解耦去遮挡与姿态估计，从单图生成完整 3D 场景 |
| **SegDINO3D** | **IDEA-Research** | 3D 实例分割 | 融合图像级 + 物体级 2D 特征，用 DINO-X 提供 2D 特征 |
| **SegVGGT** | **IDEA-Research** | 多视图 3D 重建 + 分割 | 联合优化重建与分割 |
| **NeRF / 3D Gaussian Splatting** | 多家 | 新视图合成 | 基于神经辐射场/高斯溅射的场景表示 |
| **OpenMask3D** | 慕尼黑工大 | 开放词汇 3D 实例分割 | 用 CLIP 特征做 3D 开放词汇分割 |

IDEA-Research 在 3D 方向的特点是：**将 2D 开放世界感知能力（DINO-X/Grounding DINO）迁移到 3D**，而非从零构建 3D 模型。SegDINO3D 用 DINO-X 作 2D 检测模型提供特征，就是这一思路的体现。

---



## 十七、数据集与训练基础设施

> IDEA-Research 的成功不仅在于算法创新，大规模高质量数据集和系统化训练基础设施是其性能领先的关键支撑。本章梳理组织在数据层面的积累。

### 17.1 Grounding-100M：统一视觉大模型的训练基石

**Grounding-100M** 是 DINO-X / Grounding DINO 1.5 训练使用的大规模图文对齐数据集，是组织最重要的数据资产。

**基本信息**：
- **规模**：约 1 亿张图像（100M），每张图像配有文本描述和物体级标注（检测框/分割掩码/关键点等）；
- **构成细节（2026-09 补充）**：约 30% 图像带 SAM/SAM2 生成的伪 mask；约 5% 人工标注子集用于训练 universal object prompt；含 1,000 万+ region-level caption / OCR / QA 三元组；长尾显著（10M 子集统计：1–10 图/类罕见类 12,340 种、11–100 类 4,712 种、101–1000 类 2,105 种、>1000 类 278 种）；
- **构建方式**：融合多个公开数据集（COCO、LVIS、Objects365、OpenImages 等）+ 互联网图文对爬取 + 自动标注管线（用 Grounding DINO/Grounded-SAM 自动标注）；
- **标注类型**：涵盖检测框、实例分割、人体关键点、OCR 文本区域、区域描述等多种标注，支持多任务联合训练；
- **数据质量控制**：通过自动标注 + 人工抽检 + 模型置信度过滤确保标注质量，低质量样本被剔除或降权。

**Grounding-100M 的战略价值**：
1. **多任务统一训练的前提**：DINO-X 要同时支持检测/分割/姿态/OCR/描述，需要一个包含所有这些标注类型的统一数据集，Grounding-100M 正是为此构建；
2. **开放词汇能力的来源**：数据集中的文本描述覆盖海量类别（远超 COCO 的 80 类），使得模型可以泛化到训练时未见过的物体类别；
3. **数据飞轮效应**：用已有模型（Grounding DINO）自动标注新数据 → 新数据训练更强模型（DINO-X）→ 更强模型标注更多数据，形成正向循环。

### 17.2 各项目训练数据汇总

| 项目/模型 | 训练数据 | 规模 | 数据来源 |
|---|---|---|---|
| DINO | COCO 2017 | 118K 图像 | 公开数据集 |
| Grounding DINO | COCO + Objects365 + GoldG | ~3M 图像 | 公开 + 自建 |
| Grounding DINO 1.5 | Grounding-100M 子集 | 20M+ 图像 | 大规模图文对 |
| DINO-X | Grounding-100M | ~100M 图像 | 统一多任务数据集 |
| Rex-Omni | 多任务感知数据 | 22M 样本 | 检测/OCR/关键点/指代混合 |
| OSX | UBODY（自建）+ 公开数据集 | 大规模 3D 全身标注 | 自建 + 公开 |
| Motion-X | Motion-X（自建） | 81.1K 序列 / 15.6M 姿态帧 | 自建大规模运动数据 |
| *补充* | Motion-X 论文 arXiv 2307.00818，NeurIPS 2023 | — | — |
| HumanArt | HumanArt（自建） | 人类中心多场景数据集 | 自建 |
| X-Pose | UniKPT（自建） | 13 个数据集 / 338 类关键点 | 整合 + 自建 |

### 17.3 数据标注与质量控制管线

IDEA-Research 构建了一套从自动标注到人工校验的完整数据管线：

**1. 自动标注引擎**：
- 用 Grounding DINO / DINO-X 对无标注图像做开集检测，自动生成检测框；
- 用 Grounded-SAM / SAM 对检测框做自动分割，生成实例掩码；
- 用 DWPose / OSX 对人体图像做自动姿态估计；
- 用 Recognize Anything (RAM) 做自动图像标签生成。

**2. 标注工具平台**：
- **deepdataspace**：CV 数据可视化/标注/模型分析一站式平台，支持协同标注、智能标注（模型预标注 + 人工修正）、模型性能分析；
- **T-Rex Label**：基于 T-Rex 视觉提示的 AI 标注工具，用户框选一个示例即可自动标注所有同类物体，官方宣称可节省约 99% 标注耗时；
- **CountAnything**：一键计数 APP，基于 T-Rex 实现目标自动计数，适用于库存盘点、农业统计等场景。

**3. 质量控制机制**：
- 模型置信度阈值过滤：低置信度自动标注结果进入人工复核队列；
- 多人标注 + 一致性校验：关键数据集由多人独立标注，计算标注一致性（IoU/PCK 等），不一致样本进入仲裁；
- 交叉验证：用不同模型（如 Grounding DINO vs DINO-X）对同一批数据标注，结果差异大的样本重点复核。

### 17.4 训练基础设施与工程能力

**detrex 研究平台**（详见第二十二章）提供了系统化的训练框架，支持：
- 全系 DETR 模型的统一训练/评估接口；
- Model-EMA（指数移动平均）提升模型稳定性；
- AMP（自动混合精度）加速训练；
- Activation Checkpoint（激活检查点）降低显存占用，支持更大 batch；
- 分布式训练支持（多机多卡）。

**大规模训练经验**：
- DINO-X / Grounding DINO 1.5 的训练需要数十到数百 GPU 时，组织在大规模分布式训练、梯度累积、学习率调度等方面积累了丰富经验；
- 多任务联合训练的损失平衡（检测/分割/姿态/OCR 损失的权重调优）是关键工程挑战。

---

## 十八、开源生态与社区影响力

> IDEA-Research 是计算机视觉领域最具社区影响力的开源组织之一。本章从下游集成、开发者生态、社区贡献等维度评估其开源影响力。

### 18.1 下游项目集成与引用

**Grounded-Segment-Anything（17.7k★）的生态效应**：
Grounded-SAM 是组织内 Star 数最高的项目，其"文本 → 自动检测 → 分割"的组合管线被大量下游项目集成和二次开发：

| 下游应用方向 | 代表项目/场景 | 集成方式 |
|---|---|---|
| 数据自动标注 | 各类 CV 数据集标注管线 | 用 Grounded-SAM 自动生成检测框+分割掩码，人工修正 |
| 图像编辑 | Stable Diffusion 插件、ControlNet 扩展 | Grounded-SAM 定位目标区域 → Inpainting 编辑 |
| 视频理解 | 视频目标分割/跟踪 | Grounded-SAM-2 扩展到视频 |
| 机器人感知 | 具身机器人视觉系统 | 用 Grounding DINO/DINO-X 做开放世界物体检测 |
| 医学影像 | 医学图像分割 | 用 Grounded-SAM 做零样本医学图像分割 |
| 农业 | 农作物检测/计数/分割 | 用 T-Rex/Grounded-SAM 做农业场景感知 |
| 工业质检 | 缺陷检测/零件识别 | 用 DINO-X/T-Rex 做工业场景开集检测 |

**DWPose 的生态集成**：
DWPose（2.8k★）已被广泛集成到 AIGC 生态中：
- **ControlNet**：DWPose 是 ControlNet 姿态控制的标准姿态估计器之一，用户输入图像 → DWPose 提取姿态 → ControlNet 用姿态骨架引导生成；
- **Stable Diffusion WebUI**：多个扩展（如 openpose-editor、controlnet）内置 DWPose；
- **AnimateDiff**：视频生成中用 DWPose 做姿态序列提取；
- **ComfyUI**：节点式工作流中 DWPose 是常用的姿态预处理节点。

### 18.2 Hugging Face 与 Demo 生态

IDEA-Research 的多个核心项目在 Hugging Face 上提供了在线 Demo，降低了开发者试用门槛：

| 项目 | HF Space / 资源 | 说明 |
|---|---|---|
| Grounding DINO | HF Space Demo | 在线文本开集检测演示 |
| Grounded-SAM | HF Space Demo + 模型权重 | 文本检测+分割全链路演示 |
| Grounded-SAM-2 | HF 模型权重 | 视频开集分割跟踪模型 |
| DWPose | HF 模型权重 | 全身姿态估计模型 |
| T-Rex | 云端 API（deepdataspace.com） | 交互式视觉提示检测 |
| DINO-X | 云端 API + Playground | 统一视觉大模型在线体验 |

**Colab 笔记本**：多个项目提供了 Google Colab 笔记本，用户可以零配置在云端运行模型，这对学生和研究者尤其友好。

### 18.3 社区贡献与活跃度

**GitHub 社区指标**（基于 49 仓库汇总）：
- Open Issues 总量：1,555（反映社区使用中的问题反馈活跃度）；
- 贡献者：核心项目（Grounding DINO、DINO、detrex 等）各有数十到上百位贡献者；
- 代码活跃：最近代码活跃至 2026-07-29，显示组织仍在持续维护和更新。

**社区支持方式**：
- GitHub Issues：核心项目维护者积极回复社区问题；
- 微信/钉钉交流群：部分项目设有用户交流群；
- 文档与教程：detrex 有完整的 readthedocs 文档，Grounding DINO 等有详细的 README 和使用教程。

### 18.4 学术引用与衍生工作

**Grounding DINO 的学术影响**：
- 被 PaperDigest 评为 ECCV 2024 最具影响力论文；
- 大量后续工作以 Grounding DINO 为基础检测器（如 Grounded-SAM、Grounded-SAM-2、各类开放世界分割/跟踪/编辑工作）；
- 在开放世界检测、开放词汇分割、视觉语言导航等领域被广泛引用。

**DINO 的学术影响**：
- DINO 是 DETR 系检测的事实标准之一，后续大量 DETR 改进工作（如 H-DETR、Co-DETR、Group DETR 等）都以 DINO 为基线对比；
- detrex 平台集成了全系 DETR 模型，成为 DETR 研究的标准工具之一。

### 18.5 开发者工具与生态输出

| 工具 | 类型 | 价值 |
|---|---|---|
| DINO-X MCP Server | MCP 协议服务 | 将 DINO-X 视觉能力接入 Cursor/Claude 等 MCP 生态，让 LLM 具备真实视觉感知 |
| DINO-X API | 云端 API | 统一视觉大模型的 RESTful API，支持检测/分割/姿态/OCR/描述 |
| Grounding DINO 1.5 API | 云端 API | 更强开集检测 API（Pro/Edge 双版本） |
| T-Rex Label | 标注工具 | AI 辅助标注，节省 ~99% 标注耗时 |
| CountAnything | 计数 APP | 一键目标计数 |
| deepdataspace | 数据平台 | CV 数据标注/可视化/模型分析一站式平台 |
| detrex | 研究框架 | DETR 系统一研究平台 |

**MCP 生态的战略意义**：DINO-X MCP Server 是组织接入 AI Agent 生态的关键布局。通过 MCP（Model Context Protocol），DINO-X 的视觉能力可以被任意支持 MCP 的 LLM 客户端（Cursor、Claude Desktop 等）调用，使得"对话式视觉任务"成为可能——用户可以用自然语言让 AI 助手"检测这张图里的所有汽车并描述它们"，AI 助手通过 MCP 调用 DINO-X 完成视觉感知。

---

## 十九、学术谱系与人才培养

> IDEA-Research CVR 中心不仅是研究机构，也是视觉领域人才培养的重要阵地。本章梳理团队的学术谱系、人才流动与高校合作网络。

### 19.1 核心成员学术背景

| 成员 | 最高学历 / 母校 | 博士后/工作经历 | 研究方向 |
|---|---|---|---|
| **张磊** | 博士 / 香港中文大学（2001，导师汤晓鸥）| 微软研究院 20 年（MSRA 视觉组 → 微软总部），IEEE Fellow | 目标检测、视觉语言、大规模视觉表示 |
| **冯力** | 博士 / 清华大学 | IDEA CVR 核心研究员 | DETR 检测、开放世界感知 |
| **刘世隆** | 博士 / 清华大学（导师？）| IDEA 实习生 → Princeton | DETR 收敛、开集检测 |
| **任天鹤** | — | IDEA 高级 CV 工程师 → HKU 博士生（导师齐晓娟）| Grounding DINO、DINO-X |
| **赵展** | — | IDEA CVR 核心研究员 | Stable-DINO、DINO-X、Rex 系列 |
| **张浩** | — | IDEA CVR 研究员 | DINO 一作 |
| **黎鸿扬** | — | IDEA CVR 研究员 | TAPTR、DINO-X |
| **蒋擎** | 博士在读 / 华南理工（联培，师从张磊）| IDEA 联培博士生 | Rex-Omni、ChatRex、T-Rex2 |
| **陈一豪** | — | IDEA CVR 研究员 | DINO-X、Rex-Omni |
| **谭平** | 博士 / 香港科技大学 | HKUST 教授，原阿里达摩院 XR 实验室负责人，IDEA 客座 | 3D 视觉、SLAM、空间智能 |

### 19.2 张磊的学术谱系

张磊是 IDEA CVR 的学术灵魂人物，其学术背景和人脉网络深刻影响了团队的研究方向和人才结构。

**师承关系**：
- 张磊的博士导师是**汤晓鸥**（香港中文大学教授，商汤科技创始人，中国计算机视觉领域的泰斗级人物）；
- 汤晓鸥门下培养了大量视觉领域顶尖学者，张磊是其中的代表人物之一；
- 这一师承关系使得 IDEA CVR 与港中文、商汤等机构有着天然的学术联系。

**微软研究院传承**：
- 张磊在微软研究院工作 20 年（MSRA 视觉组 + 微软总部），是微软视觉团队的核心成员之一；
- 微软亚洲研究院（MSRA）视觉组是中国计算机视觉人才的"黄埔军校"，培养了大量顶尖研究者；
- 张磊在微软期间参与了 GLIP、Oscar、VinVL、CvT、Dynamic Head 等重要工作，这些工作为 IDEA CVR 的开放世界感知研究奠定了基础；
- 团队中多名核心成员有微软背景或与微软有合作关系。

### 19.3 实习生培养与人才流动

IDEA CVR 有活跃的实习生计划，大量顶尖高校的学生在此参与研究并发表顶会论文：

| 实习生 | 所属高校 | 在 IDEA 的工作 | 去向 |
|---|---|---|---|
| 刘世隆 | 清华大学 | DAB-DETR、DN-DETR、DINO、Grounding DINO | Princeton（博士/博士后） |
| 任天鹤 | — | Grounding DINO、Grounded-SAM、DINO-X | HKU CVMI Lab 博士生（导师齐晓娟） |
| 蒋擎 | 华南理工（联培）| Rex-Omni、ChatRex、T-Rex2 | 华南理工博士在读 |
| 曹赫 | — | Grounded-SAM、生成模型 | — |

**实习生培养模式**：
- IDEA CVR 的实习生通常参与核心项目的研发，而非打杂式的辅助工作；
- 多名实习生以第一作者身份在 CVPR/ICCV/ECCV/ICLR/NeurIPS 等顶会发表论文；
- 这种"核心项目 + 顶会论文"的培养模式对顶尖学生有很强吸引力，形成了良性的人才循环。

### 19.4 高校合作网络

IDEA CVR 与多所顶尖高校建立了合作关系：

| 合作高校 | 合作形式 | 代表合作 |
|---|---|---|
| **清华大学** | 实习生联合培养 | 刘世隆等清华学生在 IDEA 实习并发表 DINO/Grounding DINO 等 |
| **香港大学（HKU）** | 博士生联合培养 | 任天鹤在 HKU CVMI Lab（齐晓娟组）攻读博士，同时参与 IDEA 项目 |
| **香港科技大学（HKUST）** | 客座研究员 + 兼职教授 | 谭平（HKUST 教授）任 IDEA 客座研究员；张磊任 HKUST(广州) 兼职教授 |
| **华南理工大学** | 联培博士生 | 蒋擎为华南理工与 IDEA 联培博士生（师从张磊） |
| **香港中文大学（深圳）** | 数据合作 | Motion-X 数据集由 IDEA + 清华 + 港中文深圳联合构建 |
| **Princeton** | 学术交流 | 刘世隆赴 Princeton 后仍与 IDEA 保持合作 |

**合作模式总结**：
1. **实习生计划**：顶尖高校学生到 IDEA 实习，参与核心项目；
2. **联培博士生**：高校与 IDEA 联合培养博士，学生在 IDEA 做研究；
3. **客座/兼职教授**：高校教授在 IDEA 担任客座研究员，或 IDEA 负责人在高校兼职；
4. **数据/项目合作**：联合构建数据集、联合发表论文。

这种"研究院 + 高校"的合作模式使得 IDEA CVR 既能保持研究的前沿性（高校的学术氛围），又能具备工程落地能力（研究院的工程资源）。

---



## 二十、商业化与竞争格局深度分析

> 2025 年 8 月，张磊带 DINO-X 团队孵化成立「视启未来（Visincept）」，标志着 IDEA-Research 从纯学术研究走向商业化落地。本章深度分析其商业模式、产品矩阵、竞争格局与差异化优势。

### 20.1 视启未来（Visincept）公司全景

**基本信息**：
- **公司全称**：视启未来（深圳）科技有限公司
- **成立时间**：2025-08-07
- **总部**：深圳福田深港国际科技园
- **创始人兼 CEO**：张磊（Lei Zhang）
- **顾问**：张钹院士（清华大学，AI 领域泰斗）、沈向洋院士（IDEA 创始人，前微软全球执行副总裁）
- **孵化背景**：由 IDEA（粤港澳大湾区数字经济研究院）孵化，承接 DINO-X 核心研发团队与知识产权

**融资历程**：

| 时间 | 轮次 | 金额 | 投资方 | 估值 |
|---|---|---|---|---|
| 2025.09 | 战略投资 | 2000 万元 | 安凯微 | — |
| 2025.11 | 天使轮 | 近亿元 | 安凯微（领投）、昊辰资本、德虎资本、元禾璞华、银杏谷资本 | 约 5 亿元（投后）|

**最新工商与知产补充（2026 检索）**：注册资本约 403.71 万元，参保 15 人（2025 年报）；天使轮跟投方另含**力合中科、数字未来、九安智能、沄柏资本**等；知识产权：专利 31 条、著作权 3 条、商标 19 条（如 CN119579869B「目标关键点检测模型的训练方法」）。

**融资逻辑解读**：
- 安凯微作为领投方和战略投资方，是一家专注于 AIoT 芯片的公司，其投资逻辑是将 DINO-X 的视觉能力与安凯微的端侧芯片结合，打造"芯片 + 算法"的端侧 AI 视觉方案；
- 元禾璞华（半导体领域专业投资机构）、银杏谷资本（硬科技投资）等机构的参与，反映了资本市场对"视觉大模型 + 具身智能"赛道的看好；
- 近亿元天使轮、约 5 亿元估值，在 AI 视觉大模型创业公司中属于较高水平，反映了团队的学术声誉和技术壁垒。

### 20.2 产品矩阵详解

视启未来的产品矩阵围绕"视觉原生（vision-native）"技术路线构建，以物体级理解为核心：

**一、核心模型层**

| 产品 | 定位 | 核心能力 | 应用场景 |
|---|---|---|---|
| **DINO-X** | 统一视觉大模型 | 开放世界检测 + 分割 + 姿态 + OCR + 区域描述 | 通用视觉感知基础设施 |
| **DINO-XSeek** | 指代检测 MLLM | 依据自然语言描述指代任意人物/物体（含遮挡、模糊等难例）| 细粒度视觉指代、人机交互 |
| **DINO-X Grasp** | 机械臂抓取模型 | 开放世界物体抓取规划（6-DoF 抓取位姿预测）| 具身机器人、工业分拣 |
| **EgoTwin** | 人手 3D 对齐引擎 | 第一视角人手 3D 姿态与网格恢复（联合百度智能云）| VR/AR、人机协作、动作捕捉 |
| **DINO-X Video** | 视频事件理解/决策引擎 | 连续视频理解、事件洞察与决策 | 安防、零售 |
| **SpatialPoint** | 空间智能 VLM（2026-03 发布）| 深度图原生输入，输出机器人可执行 3D 坐标（TouchablePoint + AirPoint）| 具身机器人、空间感知 |
| **oVP** | 优化视觉提示/定制模板 | 针对长尾场景的视觉提示优化与定制化检测模板 | 工业质检、农业、特殊场景 |

**二、MaaS 平台与工具层**

| 产品 | 类型 | 核心功能 |
|---|---|---|
| **DINO-X 开放平台**（cloud.deepdataspace.com）| MaaS 平台 | 统一视觉大模型的云端服务，支持 API 调用、在线 Playground、任务管理 |
| **DINO-X API**（api.deepdataspace.com）| RESTful API | 检测/分割/姿态/OCR/描述的异步任务接口，支持批量处理 |
| **Grounding DINO 1.5 API** | RESTful API | 更强开集检测 API（Pro/Edge 双版本） |
| **DINO-X MCP Server** | MCP 协议服务 | 将 DINO-X 接入 Cursor/Claude 等 MCP 生态，对话式完成视觉任务 |
| **T-Rex Label** | AI 标注工具 | 基于视觉提示的交互式标注，官方宣称节省 ~99% 标注耗时 |
| **CountAnything** | 计数 APP | 一键目标计数，适用于库存盘点、农业统计等 |
| **deepdataspace** | 数据平台 | CV 数据可视化/标注/模型分析一站式平台 |

**三、行业解决方案层**

| 行业 | 解决方案 | 核心技术 |
|---|---|---|
| **工业质检** | 缺陷检测、零件识别、装配校验 | DINO-X 开集检测 + oVP 定制模板 |
| **具身机器人** | 机器人视觉中枢、物体抓取、场景理解 | DINO-X Grasp + DINO-X 统一感知 |
| **自动驾驶** | 开放世界障碍物检测、交通标志识别 | Grounding DINO / DINO-X |
| **低空经济** | 无人机场景感知、目标检测跟踪 | DINO-X + Grounded-SAM-2 |
| **智慧矿山** | 矿山设备/人员/安全检测 | DINO-X 开集检测 |
| **农业** | 作物检测、病虫害识别、产量估算 | T-Rex 视觉提示 + CountAnything |
| **文化遗产** | 文物纹样识别、数字化存档 | DINO-X（中央美院 TxstureAxis 合作）|

### 20.3 商业模式与收入路径

视启未来的商业模式是典型的"开源影响力 + 云服务收费"范式：

**收入来源**：

1. **API 调用收费**（核心收入）：
   - DINO-X API、Grounding DINO 1.5 API 按调用次数/处理图像量收费；
   - Pro 版本（高精度）定价高于 Edge 版本（轻量）；
   - 企业客户可购买套餐包或定制化 SLA。

2. **MaaS 平台订阅**：
   - DINO-X 开放平台提供企业级订阅，包含更高 API 配额、专属支持、私有化部署选项；
   - deepdataspace 数据平台的企业版授权。

3. **行业解决方案定制**：
   - 针对工业质检、机器人等垂直行业，提供模型微调、定制化开发、部署实施等服务；
   - 与招商局、美团、腾讯、阿里等大客户的合作可能包含项目制收入。

4. **硬件/芯片合作分成**：
   - 与安凯微等芯片厂商合作，将 DINO-X Edge 版本部署到端侧芯片，可能按芯片出货量分成或收取授权费；
   - 这是长期潜在的重要收入来源。

**开源策略与商业化的平衡**：
- 核心模型（Grounding DINO、DINO 等）以 Apache-2.0 开源，建立学术影响力和社区生态；
- 最新最强模型（DINO-X Pro、Grounding DINO 1.5 Pro）通过 API 商业化，不直接开源权重；
- Edge 版本兼顾部署需求，可能提供有限开源或商业授权；
- 这种"开源旧版/基础版 + 商业化最新版/Pro 版"的策略是 AI 公司的常见做法（类似 OpenAI 的 GPT 系列）。

### 20.4 竞争格局分析

**视觉大模型赛道主要玩家**：

| 公司/机构 | 代表产品 | 技术路线 | 商业化阶段 | 差异化 |
|---|---|---|---|---|
| **视启未来（Visincept）** | DINO-X、Grounding DINO | 视觉原生（vision-native），object-centric | 天使轮，产品已上线 | 开放世界检测最强，物体级理解 |
| **智谱 AI** | GLM-4V、CogVLM | 语言原生（language-native），MLLM | 已商业化，多轮融资 | 强语言理解，视觉为辅助 |
| **阶跃星辰** | Step-VL | 语言原生 MLLM | 已商业化 | 多模态理解 |
| **MiniMax** | ABAB 多模态 | 语言原生 MLLM | 已商业化 | 视频生成 + 理解 |
| **百度** | 文心一言多模态、Florence 合作 | 语言原生 + 视觉模型 | 成熟商业化 | 搜索 + 云服务生态 |
| **腾讯** | 混元多模态、YOLO-World | 语言原生 + 检测模型 | 内部使用 + 部分开放 | 微信/QQ 生态，实时检测 |
| **阿里巴巴** | Qwen-VL、通义千问多模态 | 语言原生 MLLM | 成熟商业化 | 电商/云服务生态 |
| **OpenAI** | GPT-4V / GPT-4o | 语言原生 MLLM | 全球商业化 | 最强通用多模态 |
| **Google** | Gemini、Florence-2 | 语言原生 + 视觉序列模型 | 全球商业化 | 搜索/Android 生态 |
| **Meta** | SAM、SAM 2、DINOv2 | 视觉原生（分割/自监督）| 开源为主 | 分割最强，开源生态 |

**视启未来的差异化定位**：

1. **视觉原生 vs 语言原生**：
   - 大多数多模态大模型（GPT-4V、Gemini、GLM-4V 等）是"语言原生"的——以 LLM 为核心，视觉作为输入模态之一，视觉能力是 LLM 的附属；
   - 视启未来走"视觉原生"路线——以物体级视觉理解为核心，DINO-X 是专门的视觉大模型，在检测/分割/姿态等视觉任务上的精度远超通用 MLLM；
   - 这一定位的优势是：在需要精确视觉感知（如工业质检、机器人抓取）的场景下，视觉原生模型比通用 MLLM 更可靠。

2. **开放世界检测的绝对领先**：
   - Grounding DINO / DINO-X 在开放集检测上的性能是行业标杆，COCO zero-shot 52.5 AP（Swin-L）、LVIS 67.3（GD 1.5 Pro）等指标领先；
   - 这一技术壁垒来自团队在 DETR 检测领域的长期积累（DAB→DN→DINO→Grounding DINO→DINO-X 的完整技术链）。

3. **object-centric 统一架构**：
   - DINO-X 以物体 query 为中心统一检测/分割/姿态/OCR/描述，这一架构在物体级多任务联合上有天然优势；
   - 对于机器人等需要"理解场景中每个物体"的应用，object-centric 架构比全局图像理解更合适。

4. **具身机器人视觉中枢的定位**：
   - 视启未来明确将自己定位为"具身机器人的视觉中枢"，DINO-X Grasp（机械臂抓取）、EgoTwin（人手 3D 对齐）等产品都是围绕机器人场景；
   - 这一定位与具身智能赛道的爆发趋势契合，机器人视觉是 AI 落地的重要场景。

**潜在挑战**：
1. **通用 MLLM 的视觉能力快速提升**：GPT-4o、Gemini 等通用 MLLM 的视觉能力在快速进步，可能在某些场景下侵蚀专用视觉模型的市场；
2. **端侧部署的竞争**：YOLO-World 等实时开放词汇检测模型在端侧部署上有优势，DINO-X Edge 需要在精度和速度之间找到平衡；
3. **商业化人才与销售能力**：视启未来的核心团队是研究背景，商业化销售和客户成功能力需要补全；
4. **大客户的自研倾向**：腾讯、阿里、百度等大公司有自己的多模态团队，可能选择自研而非采购第三方服务。

---

## 二十一、技术路线图与未来展望

> 基于 IDEA-Research 已有的技术积累和 2025—2026 年的最新工作，本章推演其未来技术路线，并分析潜在挑战与机遇。

### 21.1 从 2D 感知到 3D 空间智能的演进路径

IDEA-Research 的技术演进呈现清晰的"从 2D 到 3D"脉络：

```
2D 检测（DAB/DN/DINO）
    │
    ▼
2D 开放世界感知（Grounding DINO → DINO-X）
    │
    ▼
视频感知（Grounded-SAM-2、TAPTR 系列）
    │
    ▼
3D 空间智能（SegDINO3D、SegVGGT、SceneMaker）
    │
    ▼
具身智能 / 世界模型（DINO-X Grasp、EgoTwin、未来方向）
```

**3D 方向的技术路径**：

1. **2D 特征驱动的 3D 感知**（当前阶段）：
   - SegDINO3D 用 DINO-X 作 2D 检测模型提供图像级和物体级 2D 特征，再提升到 3D 做实例分割；
   - 这一路径的优势是可以复用 2D 开放世界感知的强大能力，无需从零训练 3D 模型；
   - 局限性是依赖多视图或深度估计，对单图 3D 感知能力有限。

2. **原生 3D 开放世界模型**（中期方向）：
   - 直接在 3D 空间（点云/体素/高斯溅射）上做开放词汇检测和分割；
   - SceneMaker 的"开放集 3D 场景生成"是这一方向的探索，从单图生成完整 3D 场景；
   - 可能结合 3D Gaussian Splatting 等新兴 3D 表示方法。

3. **时空统一的 4D 感知**（长期方向）：
   - 将 3D 空间感知与时间维度结合，实现动态场景的 4D 理解；
   - TAPTR 系列的视频点跟踪是时空感知的基础；
   - 4D 感知是机器人、自动驾驶等动态场景的核心需求。

### 21.2 具身智能与 VLA 融合

**DINO-X 作为机器人视觉中枢的定位**：
- DINO-X Grasp 已经实现了开放世界物体的 6-DoF 抓取位姿预测，是 DINO-X 从"感知"走向"感知+行动"的第一步；
- 未来可能的演进方向是 VLA（Vision-Language-Action）模型：将 DINO-X 的视觉感知能力与语言模型的推理能力、机器人的动作输出结合，实现端到端的具身智能；
- 视启未来的"视觉原生"路线在 VLA 时代有独特价值：精确的物体级感知是机器人可靠操作的前提，通用 MLLM 的视觉能力在精细操作场景下可能不够可靠。

**可能的技术路径**：

```
DINO-X（视觉感知）+ LLM（语言推理）+ 动作头（机器人控制）
                        │
                        ▼
                VLA 模型（视觉-语言-行动统一）
                        │
                        ▼
                具身智能体（感知→推理→行动闭环）
```

**与现有 VLA 工作的关系**：
- RT-2（Google）、Octo（斯坦福等）、OpenVLA 等现有 VLA 工作大多使用通用视觉编码器（如 DINOv2、SigLIP），缺乏开放世界物体级感知能力；
- DINO-X 作为 VLA 的视觉编码器，可以提供精确的物体检测/分割/姿态信息，使得 VLA 模型在"操作特定物体"的任务上更可靠；
- 这可能是视启未来在具身智能赛道的差异化切入点。

### 21.3 世界模型方向

世界模型（World Model）是 AI 领域的前沿方向，目标是让 AI 学会预测环境状态的变化，从而进行规划和决策。

**IDEA-Research 在世界模型方向的潜在优势**：
1. **object-centric 表示**：DINO-X 的 object-centric 架构天然适合构建以物体为基本单元的世界模型——场景由物体组成，物体的状态变化可以被独立建模；
2. **3D 场景生成**：SceneMaker 的开放集 3D 场景生成能力可以作为世界模型的"场景初始化"模块；
3. **视频理解**：TAPTR、Grounded-SAM-2 等视频感知能力可以为世界模型提供时序监督；
4. **视觉原生路线**：世界模型的核心是物理世界的建模，视觉原生模型比语言原生模型更适合这一任务。

**可能的探索方向**：
- **物体级世界模型**：以 DINO-X 检测到的物体为基本单元，预测物体在物理交互下的状态变化（位置、姿态、形变）；
- **可交互场景生成**：结合 SceneMaker 的 3D 场景生成与物理引擎，构建可交互的 3D 世界模型，用于机器人仿真训练；
- **视觉预测模型**：类似 Sora 的视频生成，但以物体级理解为基础，实现可控的、物理一致的视觉预测。

### 21.4 统一感知范式的进一步收敛

Rex-Omni 的"下一关键点预测"范式代表了统一感知的新方向，未来可能进一步演进：

1. **感知与生成的统一**：next point prediction 本质上是一种序列生成范式，与 LLM 的 next token prediction 同构。未来可能将感知（点预测）与生成（图像/视频生成）统一到同一个序列建模框架中；
2. **2D 与 3D 的统一**：将 next point prediction 从 2D 图像扩展到 3D 空间（预测 3D 点序列），实现 2D/3D 统一感知；
3. **感知与行动的统一**：将机器人动作也表示为"关键点序列"（如机械臂关节角序列、末端执行器轨迹），实现感知与行动的统一序列建模。

### 21.5 潜在挑战与风险

**技术挑战**：
1. **3D 数据稀缺**：3D 场景的高质量标注数据远少于 2D 图像，这是 3D 空间智能发展的主要瓶颈；
2. **实时性与精度的平衡**：机器人等场景需要实时感知，DINO-X 等大模型的推理速度需要进一步优化；
3. **长尾场景的鲁棒性**：开放世界感知在常见物体上表现好，但在极端长尾场景（罕见物体、恶劣光照、严重遮挡）下的鲁棒性仍需提升；
4. **多模态对齐的深度**：视觉与语言的深度对齐仍是开放问题，当前模型在复杂空间关系推理（如"A 在 B 的左后方且被 C 部分遮挡"）上仍有困难。

**商业化挑战**：
1. **从 API 到解决方案的跨越**：单纯卖 API 容易被大客户自研替代，需要提供垂直行业的深度解决方案；
2. **端侧部署的生态建设**：与安凯微等芯片厂商的合作需要时间打磨，端侧生态建设是长期工程；
3. **人才竞争**：视觉大模型领域人才稀缺，视启未来需要与大公司和其他创业公司竞争顶尖人才。

**机遇**：
1. **具身智能爆发**：机器人赛道正处于爆发前夜，视觉中枢是机器人的核心组件，市场空间巨大；
2. **AI Agent 生态**：DINO-X MCP Server 接入 AI Agent 生态，随着 Agent 的普及，视觉感知 API 的需求将增长；
3. **中国 AI 产业政策**：深圳对 AI 产业的支持、IDEA 的政府背景，为视启未来提供了政策和资源优势；
4. **开源生态的复利**：Grounding DINO、DINO 等开源项目积累的社区影响力，将持续为商业化输送客户和人才。

---



## 二十二、工程实践与部署指南

> 本章从工程视角梳理 IDEA-Research 核心项目的架构设计、部署优化与 API 使用最佳实践，为开发者和工程团队提供实操参考。

### 22.1 detrex 研究平台架构深度解析

**detrex**（2.3k★）是 IDEA-Research 推出的 DETR 系统一研究平台，是组织最重要的工程基础设施之一。

**设计理念**：
- detrex 基于 detectron2 的设计哲学，但专门针对 DETR 系检测模型做了深度优化；
- 目标是提供一个"开箱即用"的 DETR 研究平台，让研究者可以快速复现、改进和对比各种 DETR 变体。

**架构分层**：

```
┌─────────────────────────────────────────┐
│              配置层 (Config)              │
│  基于 detectron2 的 LazyConfig 系统       │
│  支持 Python 语法的灵活配置组合            │
├─────────────────────────────────────────┤
│              模型层 (Models)              │
│  Backbone │ Neck │ Encoder │ Decoder     │
│  ──────── │ ──── │ ─────── │ ───────     │
│  ResNet   │ FPN  │ 多种    │ DAB/DN/     │
│  Swin     │ Channel │ Attention │ DINO/   │
│  ViT      │ Lifter │ 变体    │ MaskDINO  │
├─────────────────────────────────────────┤
│              数据层 (Data)                │
│  COCO / LVIS / Objects365 等数据集       │
│  支持自定义数据集注册                      │
│  数据增强管线（Resize/Crop/Flip/Normalize）│
├─────────────────────────────────────────┤
│              引擎层 (Engine)              │
│  Trainer │ Evaluator │ Hook 系统          │
│  支持 AMP / EMA / Activation Checkpoint  │
│  分布式训练（多机多卡）                    │
├─────────────────────────────────────────┤
│              工具层 (Tools)               │
│  训练脚本 │ 评估脚本 │ 推理 Demo          │
│  模型转换 │ 可视化工具                     │
└─────────────────────────────────────────┘
```

**内置模型矩阵**：
detrex 内置了全系 DETR 模型的实现，包括：
- **基础 DETR**：DETR、Deformable-DETR、Conditional-DETR、Anchor-DETR
- **IDEA 自研**：DAB-DETR、DN-DETR、DINO、Stable-DINO、MaskDINO
- **社区改进**：Group-DETR、DETA、H-DETR、Lite-DETR
- **任务扩展**：检测、实例分割、全景分割、姿态估计

**关键工程能力**：

| 能力 | 实现方式 | 价值 |
|---|---|---|
| **Model-EMA** | 训练时维护模型参数的指数移动平均副本，评估时用 EMA 权重 | 提升模型稳定性和最终精度，尤其在小 batch 训练时 |
| **AMP（自动混合精度）** | 用 FP16/BF16 计算前向，FP32 做参数更新和损失计算 | 训练速度提升 ~1.5-2x，显存占用降低 ~40% |
| **Activation Checkpoint** | 在前向时不保存全部中间激活，反向时重新计算 | 大幅降低显存占用，支持更大 batch 和更高分辨率 |
| **分布式训练** | 基于 PyTorch DDP，支持多机多卡 | 支持大规模训练，线性加速比 |
| **LazyConfig** | 基于 Python 导入的配置系统，支持配置继承和覆盖 | 比 YAML 更灵活，便于实验管理和复现 |

**detrex 的使用场景**：
1. **学术研究**：研究者可以在 detrex 基础上快速实现新的 DETR 变体，并与内置的 SOTA 模型公平对比；
2. **工业落地**：企业可以用 detrex 训练自定义数据集的检测模型，detrex 的工程化能力（AMP/EMA/分布式）降低了训练门槛；
3. **教学**：detrex 的清晰架构和丰富文档适合作为 DETR 教学的实验平台。

### 22.2 模型部署与优化

**Grounding DINO 部署路径**：

| 部署方式 | 适用场景 | 优化手段 | 性能参考 |
|---|---|---|---|
| **PyTorch 原生推理** | 研究/原型验证 | 无优化，直接加载权重推理 | GPU 上 ~100-200ms/图（Swin-T） |
| **TorchScript / ONNX 导出** | 生产部署 | 导出为 ONNX，用 TensorRT/ONNX Runtime 加速 | 延迟降低 ~30-50% |
| **TensorRT 优化** | 高性能云端部署 | FP16/INT8 量化、算子融合、动态 shape | 延迟可降至 ~20-50ms/图 |
| **Edge 版本（GD 1.5 Edge）** | 端侧/边缘部署 | 更小 backbone、知识蒸馏、量化 | 适合 Jetson/移动端部署 |
| **云端 API** | 无需自建部署 | 调用 DINO-X / GD 1.5 API | 按调用量付费，无需维护 |

**DWPose 部署特点**：
- DWPose 提供了 ONNX 分支（onnx 分支），支持导出为 ONNX 模型；
- 由于 DWPose 基于 MMPose，可以复用 MMPose 的部署工具链（mmdeploy）；
- DWPose 的轻量特性使其适合端侧部署，已被 ControlNet 等 AIGC 工具广泛集成。

**量化与蒸馏策略**：
1. **知识蒸馏**：用大模型（Teacher，如 Grounding DINO 1.5 Pro）蒸馏小模型（Student，如 Edge 版本），在保持精度的同时减小模型体积；
2. **INT8 量化**：对权重和激活做 INT8 量化，进一步降低显存和计算量，适合端侧部署；
3. **算子融合**：将多个小算子融合为一个大算子，减少 kernel launch 开销和内存访问；
4. **动态 shape 优化**：检测模型的输入图像尺寸不固定，需要支持动态 shape 的推理优化（TensorRT 的 dynamic shape  profile）。

### 22.3 DINO-X / Grounding DINO API 使用最佳实践

**API 接入流程**：

1. **注册与获取 API Token**：
   - 访问 deepdataspace.com 注册账号；
   - 在控制台获取 API Token（用于身份认证）；
   - 安装 SDK：`pip install dds-cloudapi-sdk --upgrade`

2. **基础调用示例**（以 DINO-X 检测为例）：
```python
from dds_cloudapi_sdk import Client, DetectionTask

# 初始化客户端
client = Client(token="your_api_token")

# 创建检测任务
task = DetectionTask(
    url="https://example.com/image.jpg",
    prompts=["cat", "dog"],  # 文本提示：要检测的类别
    confidence_threshold=0.3,
)

# 提交并等待结果
client.run_task(task)
result = task.result
print(result)  # 包含检测框、类别、置信度
```

3. **多任务调用**：DINO-X API 支持检测、分割、姿态、OCR、区域描述等多种任务，可通过不同 Task 类调用。

**最佳实践**：

| 场景 | 建议 |
|---|---|
| **批量处理** | 使用异步任务接口，批量提交图像，轮询任务状态，避免同步调用的等待开销 |
| **提示词优化** | 文本提示尽量具体（如"红色的汽车"而非"汽车"），可以提升检测精度；支持英文和中文提示 |
| **置信度阈值调优** | 根据场景调整 confidence_threshold：高精度场景用 0.5+，召回优先场景用 0.2-0.3 |
| **图像预处理** | 上传前确保图像清晰、分辨率适中（建议最长边 1024-2048px），过小将影响小目标检测 |
| **错误处理** | 实现重试机制（网络超时、限流等），指数退避策略；监控 API 调用量和错误率 |
| **成本优化** | 简单场景用 Grounding DINO 1.5 Edge（更便宜），复杂/高精度场景用 DINO-X Pro；合理设置 batch 大小 |

**DINO-X MCP Server 使用**：
- DINO-X MCP Server 允许在支持 MCP 的 LLM 客户端（如 Cursor、Claude Desktop）中直接调用 DINO-X 的视觉能力；
- 配置 MCP Server 后，可以用自然语言指令完成视觉任务，如"检测这张图里的所有汽车并描述它们的颜色和位置"；
- 适合开发者在编码/写作过程中快速处理图像，无需切换到专门的视觉工具。

### 22.4 Grounded-SAM 全链路部署

Grounded-Segment-Anything 是组织内最流行的组合工具，其部署涉及多个模型的协同：

**组件构成**：
1. **Grounding DINO**：文本开集检测，输出检测框；
2. **SAM（Segment Anything Model）**：用检测框作为提示，输出实例分割掩码；
3. **Recognize Anything (RAM)**（可选）：对分割区域做图像标签识别；
4. **Stable Diffusion**（可选）：对分割区域做图像编辑/生成。

**部署架构**：

```
用户输入：图像 + 文本提示
        │
        ▼
┌───────────────────┐
│  Grounding DINO   │ ──► 检测框列表
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│     SAM 分割      │ ──► 实例分割掩码
└─────────┬─────────┘
          │
    ┌─────┴─────┐
    ▼           ▼
┌────────┐ ┌────────────┐
│  RAM   │ │Stable Diff │
│ 识别   │ │ 图像编辑    │
└────────┘ └────────────┘
```

**部署注意事项**：
- **显存需求**：Grounding DINO（Swin-T）+ SAM（ViT-H）同时加载需要约 12-16GB 显存；如果用 Stable Diffusion 还需额外 8-12GB；
- **模型缓存**：将模型权重加载到显存后复用，避免每次推理重新加载；
- **批处理**：SAM 支持批量提示，可以一次传入多个检测框做分割，提升效率；
- **替代方案**：如果显存有限，可以用 SAM 的 ViT-B 版本（更小），或用 Grounded-SAM-2（基于 SAM 2，视频场景更高效）。

### 22.5 训练自定义数据集的实践指南

**用 detrex 训练自定义检测数据集**：

1. **数据准备**：
   - 将数据集转换为 COCO 格式（annotation JSON + images 目录）；
   - 确保标注质量：检测框坐标正确、类别 ID 连续、无遗漏标注；
   - 划分 train/val 集（建议 8:2 或 9:1）。

2. **配置修改**：
   - 基于 detrex 内置的 DINO 配置文件（如 `projects/dino/configs/dino_r50_4scale_12ep.py`）；
   - 修改 `num_classes` 为自定义类别数；
   - 修改数据路径指向自定义数据集；
   - 根据数据集大小调整训练 epoch（小数据集建议微调预训练权重，epoch 数可减少）。

3. **训练策略**：
   - **微调 vs 从头训练**：建议用 COCO 预训练权重做微调（detrex 提供预训练权重下载），而非从头训练；
   - **学习率**：微调时学习率设为预训练的 1/10（如 1e-5 而非 1e-4）；
   - **数据增强**：小数据集时增强数据增强（随机裁剪、翻转、颜色抖动），防止过拟合；
   - **早停**：监控 val AP，当连续多个 epoch 无提升时停止训练。

4. **评估与部署**：
   - 用 detrex 的评估脚本在 val 集上评估 mAP；
   - 错误分析：查看检测失败的样本，判断是数据问题、标注问题还是模型容量问题；
   - 导出为 ONNX/TensorRT 用于生产部署。

**用 Grounding DINO 做零样本检测**：
- 如果自定义数据集的类别是常见物体，可以直接用 Grounding DINO 做零样本检测，无需训练；
- 只需将类别名作为文本提示传入，Grounding DINO 即可检测对应物体；
- 零样本检测的精度通常低于微调模型，但无需标注数据，适合快速验证和冷启动场景。

---

## 二十三、总结与关键洞察

> 本章提炼对 IDEA-Research 的整体认知，总结其成功要素、技术特质与行业启示。

### 23.1 成功要素分析

IDEA-Research CVR 中心在短短 4 年内（2022—2026）成为全球开放世界视觉感知领域的顶尖团队，其成功可归结为以下要素：

1. **清晰的技术主线与持续深耕**：
   - 从 DAB-DETR 解决收敛难题开始，团队持续深耕 DETR 检测方向，形成了 DAB→DN→DINO→Grounding DINO→DINO-X 的完整技术链；
   - 这种"一个方向打透"的策略，使得团队在 DETR 检测领域积累了深厚的技术壁垒，而非浅尝辄止地追逐热点。

2. **学术领袖的远见与积累**：
   - 张磊在微软研究院 20 年的积累（GLIP、Oscar、VinVL 等视觉语言工作）为 IDEA CVR 的开放世界感知研究奠定了基础；
   - 从 GLIP（一阶段开放词汇检测）到 Grounding DINO（DETR 架构开集检测），是同一研究思路在不同架构上的延续和深化。

3. **开源驱动的生态建设**：
   - 核心模型以 Apache-2.0 开源，快速建立学术影响力和社区生态；
   - Grounded-SAM（17.7k★）、Grounding DINO（10.5k★）等万星项目成为组织的"技术名片"，吸引了大量用户和贡献者；
   - 开源生态反哺研究：社区的问题反馈和使用场景为研究方向提供了输入。

4. **工程化能力的支撑**：
   - detrex 研究平台为团队提供了高效的实验基础设施，加速了模型迭代；
   - 大规模训练经验、数据标注管线、API 服务等工程能力，使得研究成果可以快速转化为可用产品。

5. **人才培养与高校合作**：
   - 活跃的实习生计划和联培博士生机制，吸引了顶尖高校的优秀学生；
   - 与清华、港大、港科大、华南理工等高校的合作，形成了"研究院 + 高校"的人才循环。

6. **适时的商业化决策**：
   - 在技术成熟（DINO-X 统一视觉大模型发布）和市场时机（具身智能爆发）到来时，果断孵化视启未来进行商业化；
   - 近亿元天使轮融资为团队提供了持续研发和商业化的资源。

### 23.2 技术特质总结

IDEA-Research 的技术工作具有以下鲜明特质：

1. **DETR 基因**：几乎所有核心检测工作都基于 DETR 架构（集合预测 + 二分匹配 + Transformer decoder），团队对 DETR 的理解和改进达到了世界顶尖水平；
2. **开放世界导向**：从 Grounding DINO 开始，团队的工作都强调"开放世界"能力——不局限于固定类别集，能理解任意文本提示并定位对应物体；
3. **object-centric 哲学**：DINO-X、Rex-Omni 等最新工作都以物体为中心构建感知框架，所有任务围绕物体 query 展开，这与"全局图像理解"的路线形成对比；
4. **范式创新**：团队不满足于增量改进，多次提出范式级创新——DN-DETR 的去噪训练、Grounding DINO 的 feature enhancer、Rex-Omni 的 next point prediction、TAPTR 的点跟踪集合预测；
5. **统一化趋势**：从单一任务（检测）到多任务统一（DINO-X），再到感知范式统一（Rex-Omni），团队的工作呈现清晰的"统一化"演进趋势。

### 23.3 行业启示

IDEA-Research 的发展路径对 AI 研究机构和创业公司有以下启示：

1. **基础研究的长期价值**：DAB/DN-DETR 解决 DETR 收敛难题时，看似是纯学术问题，但正是这一基础突破为后续 Grounding DINO、DINO-X 的成功奠定了基础。基础研究的价值往往在多年后才显现；
2. **开源是最好的商业化准备**：通过开源建立技术影响力和社区生态，再通过 API/云服务商业化，是 AI 公司的可行路径。Grounding DINO 的开源社区为 DINO-X API 提供了大量潜在客户；
3. **垂直深耕优于横向扩张**：在 DETR 检测这一个方向上持续深耕 4 年，形成了其他团队难以逾越的技术壁垒。相比之下，追逐多个热点方向但都不深入的团队，往往难以建立核心竞争力；
4. **学术与商业的平衡**：IDEA CVR 保持了学术研究的开放性（开源、发顶会），同时通过孵化公司实现商业化。这种"研究院做前沿研究 + 公司做产品落地"的双轨模式，值得其他研究机构借鉴；
5. **人才是核心资产**：张磊的学术声誉和人脉网络吸引了顶尖人才，实习生和联培博士生机制持续输送新鲜血液。AI 领域的竞争归根结底是人才的竞争。

---

*（扩展版补充内容完。以上扩展章节在原报告基础上，从技术原理、横向对比、数据基础设施、开源生态、学术谱系、商业化、技术展望、工程实践等维度做了深度补充，使报告从"工作清单"升级为"全景式深度调研报告"。）*
*（内容由AI生成，仅供参考）*


---

## 附：数据说明与信息来源

- 仓库清单、Star 数、许可证、topics、创建时间：GitHub API 实测（2026-08-26 全量清单，2026-09-08 复核更新，49 个公开仓库，无归档、无遗漏）。
- 论文 arXiv 编号：GitHub README + arXiv 官方查询 + 权威搜索三重核验。
- 组织/团队/商业化信息：IDEA 官网、视启未来工商与融资报道（爱企查、猎云网、证券时报、品玩等）、deepdataspace.com 官方产品页、Google Scholar / Semantic Scholar / dblp。
- 性能指标：来自论文原文与官方 README；部分标注「约」的指标为论文/官方报道公开数字的近似值。
- 影响力数据大盘：Star / Fork / Issues / 仓库存储 / 创建与活跃时间均为 GitHub API 实测（2026-08-26 全量 + 2026-09-08 复核更新）。
- 内容由 AI 整理生成，引用量等动态数据以原始来源最新数据为准。
- 核心论文引用量：为 2026-09 检索快照（Google Scholar / Semantic Scholar / IEEE 等口径）；引用量随时间增长，以原始来源最新值为准。
- 2025-26 最新工作状态与视启未来 2026 进展（EgoTwin 联合百度智能云、SpatialPoint、DINO-X Video、CES2026 端侧方案等）：来自 GitHub 仓库、OpenReview、visincept.com 研究页、爱企查及权威媒体报道交叉核实。

---
*（本报告为终版完整版，覆盖：组织团队全貌、七大主线深度拆解、核心论文技术剖析、全量论文清单（含仓库外）、仓库工程细节、49 项论文速查表、时间线与影响力评估。）*
*（内容由AI生成，仅供参考）*
