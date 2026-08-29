---
title: "折叠京张"
author_github: "fjun818-art"
language: "zh"
proposal_format_version: "2"
bilingual_contract_version: "1"
translation_file: "proposal.en.md"
license: "COMMUNITY-DISPLAY-ONLY"
summary: "京张数智折叠带（JDSFB）：以法定控规为基准、以「数据要素折叠」为核心机制的 AI 城市设计方案。7 个时空折叠点全部锚定控规文保清单，京张数据契约对接控规第 82 条数据要素市场化条款，建筑规模严守 2408.0 万㎡ 法定上限；使用 provisional boundary 并保留精度警示，组织方数据缺口不阻断内容评分。"
tracks: ["ai-traffic-walkability", "enterprise-services-ecosystem", "civic-agent-governance"]
scenarios: ["ai-traffic-walkability", "enterprise-service-copilot", "public-safety-operations-review"]
---

# 折叠京张

**京张数智折叠带 · Jingzhang Data-Spatial Fold Belt (JDSFB)**

本方案将纵贯海淀二环至五环、全长约 9 公里的京张铁路遗址廊道，从「物理交通线」升维为「数据要素流通线」与「时空记忆载体」：以京张遗址公园为折叠带本体（物理层），以 1+3+N 数字孪生底座为可编辑城市（数字层），以 7 个锚定法定文保清单的时空折叠点为体验界面（体验层），构建一条「可计算、可感知、可编辑」的城市更新示范带。方案刚性结论以《HD00—1601 等街区控制性详细规划》为法定基准 [source:REGULATORY-PLAN-HD00-1601]，产业事实以官方「三区两翼」发布为基准 [source:THREE-ZONES-TWO-WINGS-RELEASE]，任务来源见征集公告 [source:OFFICIAL-ANNOUNCEMENT]。

面向智能体的具体任务要求见 [source:AGENT-TASKBOOK]。

## 设计依据与资料清单

本 formal 方案的第一依据是北京市规划和自然资源委员会海淀分局发布的《百年京张AI创新带城市设计国际方案征集资格预审公告》[source:OFFICIAL-ANNOUNCEMENT]，并以 `brief/site-package/` 中经维护者登记的临时粗略边界、重点区域、枚举、指标和来源清单为机器可读依据 [source:SITE-PACKAGE]。AI agent 在生成方案前读取了 `design_brief.json`、`sources.json`、`enums/`、`data/source_registry.json` 和 `data/processed/agent_fact_pack.md`，所有设计判断均拆分为可追溯来源、可复算指标、可校验图层和可人工复核假设 [depth:existing_conditions_diagnosis]。

与其他参赛方案相比，本方案额外取得并全文援引两项关键依据：

1. **法定控规**：《北京海淀区京张铁路遗址公园沿线（人工智能创新街区重点地区）HD00—1601 等街区控制性详细规划（街区层面）（2024 年—2035 年）》（中规院编制，甲资规甲字 21110023）[source:REGULATORY-PLAN-HD00-1601]。其刚性管控——规划范围 16.7 km²（北至成府路、南至西直门外大街、西至中关村大街、东至新街口外大街，含 9 个街区）、总建筑规模 2408.0 万㎡、常住人口约 36.4 万人、就业岗位约 39.7 万个、「一带一轴，两心多点」空间结构、75 个主导功能分区、6 类基准高度分区、13 处不可移动文物——优先级高于任何征集叙事，本方案生成的空间结论逐条对照（详见各章 `[source:REGULATORY-PLAN-HD00-1601]` 标注）。
2. **官方「三区两翼」发布口径**：海淀区关于百年京张 AI 创新带的官方发布，明确北部学北园 AI 自主创新加速区、中部北京 AI 原点社区、南部大钟寺 AI 产业集聚区与西翼中关村科技服务翼、东翼小月河场景赋能翼的空间架构及全部产业事实数据 [source:THREE-ZONES-TWO-WINGS-RELEASE]。

资料登记表的使用边界如下 [source:SOURCE-REGISTRY]：

- data/source_registry.json 登记公开、清权与临时资料的用途边界；agent 不得把 background_only 或 provisional_only 资料升级为 official boundary、法定控规、正式评分依据或政府实施承诺。
- `data/processed/agent_fact_pack.md` 是阅读导航层而非权威来源 [source:PROCESSED-FACT-PACK]；事实判断回到已登记原始材料，完整来源关系由 `sources.json` 保存。
- 控规第二、三部分（图纸、图则）为图像格式未能文本化提取，地块级边界精度限制已登记 `assumptions.json`；本方案仅引用控规文本条款，不伪造图则几何 [source:REGULATORY-PLAN-HD00-1601]。

![资料证据链与提交包关系图](assets/figures/site-overview.png)

在官方 `SITE_BOUNDARY` 与三处 `KEY_AREA` 精确几何尚未发布的情况下，本方案使用 `brief/site-package/geometry/provisional_boundaries.geojson` 派生的临时边界 [source:BOUNDARY-SOURCE] [source:KEY-AREA-SOURCE]。提交包中的 `geometry/site_boundary.geojson` 与 `geometry/key_areas.geojson` 均标注 `provisional_constraint`、`official_boundary=false`，只能用于方案生成、自检、可视化和设计讨论，不能作为 official redline、审批依据或精确面积依据；该组织方数据缺口不阻断内容评分，官方边界发布后全部图层与指标须重算。临时边界已按控规四至道路与 9 街区编号做交叉校核，面积口径差异（11.4 km² 总体设计范围 vs 16.7 km² 控规范围）在 `assumptions.json` 登记 [data:geometry/site_boundary.geojson#SITE-001] [metric:site_area_sqm]。

## 三层范围工作框架

方案按公告确定的三个层次组织工作，并公开三个口径的嵌套关系：统筹研究范围 43.6 km²（AI 产业生态、战略定位、未来城市形态）⊃ 统筹规划范围约 37 km²（官方发布口径）⊃ 控规重点地区 16.7 km²（法定管控基准）⊃ 总体设计范围约 11.4 km²（公告任务口径，京张遗址公园周边 1—2 公里城市地区）⊃ 重点区域 368.4 公顷（三处详细设计地区）[source:OFFICIAL-ANNOUNCEMENT] [source:REGULATORY-PLAN-HD00-1601]。三口径差异已登记 `assumptions.json` 并在本节披露。三层范围在 `compliance_matrix.json` 中逐条映射，保证公告 1.3、1.4、1.5 与 agent.1—agent.6 的必选任务都有章节、图层、指标、图纸和 HTML 证据 [depth:three_level_scope_framework] [standard:PROJECT-OFFICIAL-ANNOUNCEMENT]。

![三层范围与空间工作框架图](assets/figures/land-use-structure.png)

本方案的总体概念为「**京张数智折叠带（JDSFB）**」：一次「折叠」把 1909 年的铁路遗产与 2035 年的 AI 街区压入同一空间坐标——物理层保留铁路遗产肌理并植入模块化、可拆卸的「AI 城市插件」；数字层构建「可编辑城市底座」，把三片区串联为数据资产化试验带；体验层通过 AR/MR 在法定文保锚点上叠加百年铁路场景与未来 AI 愿景。「折叠」不是造型隐喻，而是数据要素在物理空间中流通、登记、交易、反馈的运行机制（详见「京张数据契约」专节）。

| 层级 | 设计问题 | 方案回答 | 数据落点 |
| --- | --- | --- | --- |
| 统筹研究范围 | AI 产业生态和未来城市形态如何组织 | 「高校策源—开源协作—企业转化—公共体验—国际传播」创新链 + JDSFB 三层折叠结构 | compliance_matrix.json、standard_matrix.json |
| 总体设计范围 | 产业空间、城市更新、交通市政和风貌如何落图 | 用地、建筑、道路、绿地、公共空间、分期图层 + 数据节点网络共同表达 | [data:geometry/land_use.geojson#LU-001]、[data:geometry/roads.geojson#ROAD-001] |
| 重点区域范围 | 三处片区如何达到详细设计深度 | 三区按「数智源点/折叠中枢/流通接口」定位，叠加 7 个时空折叠点 | [data:geometry/key_areas.geojson#PROV-KEY-001]、[data:geometry/public_space.geojson#FOLD-001] |

## 统筹研究范围产业与未来城市研究

统筹研究范围的核心任务是构建世界级 AI 创新生态体系。依据官方发布口径，海淀已集聚 AI 企业 2000 余家、独角兽企业 26 家、备案大模型 130 款，人工智能核心产业规模超 3500 亿元，AI 研发人才 9.5 万人，周边汇聚 30 余所高校院所 [source:THREE-ZONES-TWO-WINGS-RELEASE]。控规进一步登记 9 处现状高校（中科院大学、北京交通大学、北京邮电大学、北京师范大学等），部分拟疏解至延庆、雄安，腾退校园空间将补充区域短板——这是 JDSFB「机遇空间清单」的法定来源 [source:REGULATORY-PLAN-HD00-1601]（控规文本第 6 条）。

JDSFB 把上述产业事实组织为「一轴两面」的数智折叠结构：纵向三区构成折叠带主轴（数据要素从源点产生 → 中枢加工 → 接口流通），东西两翼构成折叠带展开面（服务赋能 × 场景验证）[depth:overall_spatial_structure] [standard:PROJECT-AGENT-OPEN-CALL-TASKBOOK]：

| 重点片区 | 官方定位与产业事实 | JDSFB 主题定位 | 核心功能叠加 |
| --- | --- | --- | --- |
| 北部 · 学北园 AI 自主创新加速区 | 东升科技园学北园载体，总建面 23.83 万㎡，2026 年 7 月开园，国家自然科学基金委签约入驻；布局国家级算力底座、AI 芯片、基础算法平台，配套 1200㎡ 会展空间与 AI 跨境出海服务平台 [source:THREE-ZONES-TWO-WINGS-RELEASE] | **数智源点 · Data Origin** | 城市数据开放沙盒、边缘计算集群、AI 垂直模型训练场、算法贡献指数总部（算力底座 × 数据沙盒形成「算力—数据」双底座） |
| 中部 · 北京 AI 原点社区 | 五道口核心地段，环抱清华、北大、中科院科创圈；320 余家 AI 企业，产业集聚度超 74%，青年研发人员占比突破 70%；「5+5」房租与算力补贴、15 分钟人才生活圈 [source:THREE-ZONES-TWO-WINGS-RELEASE] | **折叠中枢 · Fold Hub** | 可编辑城市底座示范区、AR/MR 时空叙事节点、开发者共创社区、智能驿站网络 |
| 南部 · 大钟寺 AI 产业集聚区 | 依托抖音等头部平台产业势能，主攻智能体、AI 内容消费、智能终端、数字文创；承接原点社区成果，打造大模型商用测试、智能产品量产孵化载体 [source:THREE-ZONES-TWO-WINGS-RELEASE] | **流通接口 · Exchange Port** | 数据资产登记与交易平台、智能原生商务场景、产业测试验证场、数字孪生展示中心 |
| 西翼 · 中关村科技服务翼 | 全球要素连接器：创投资本、知识产权、跨境商事、法律咨询、上市辅导全链条 | 服务展开面 | 数据契约的商务与法律服务接口：数据资产登记确权、合规审查、跨境数据流通咨询 |
| 东翼 · 小月河场景赋能翼 | 智慧城市试验场：具身智能、AI 医疗、影视数字制作、智慧文旅实景试点 | 场景展开面 | 数据要素实景应用出口：自适应公共空间、情感计算、AI 导览优先在本翼滨水空间测试 |

命名体系服务于「百年京张文化带、都市 AI 生活体验带、AI 融合创新带」整体辨识度：中文全称「京张数智折叠带」，英文 Jingzhang Data-Spatial Fold Belt（JDSFB）；Logo 以铁路轨道线条为基底，叠加数据流线与折叠曲面，形成「物理轨道 × 数字折叠」复合符号；主视觉采用「中缝折叠 · 双时代对开」构图——左幅 1909 泛黄工程蓝图（蒸汽机车、老站台、水塔剪影），右幅深蓝数字孪生（AI 光粒列车、边缘节点星云），一条铁轨贯穿中缝完成时空穿越（见 `assets/figures/cover.png`）。未来城市形态研究结论：AI 改变的不只是产业效率，而是「时间的使用方式」——通勤、协作、消费、学习被压缩进同一慢行廊道，这正是「折叠」的城市学含义。涉及全球 AI 活动、开发者社区运营的内容均为概念建议，供专业团队深化，不构成政府实施承诺。

## 总体设计范围城市更新与控规深度城市设计

总体设计范围要求达到控制性详细规划的城市设计深度。本方案直接对位控规法定空间结构「一带一轴，两心多点」（控规文本第 9 条）[source:REGULATORY-PLAN-HD00-1601] [standard:MOHURD-CONTROL-DETAILED-PLANNING] [depth:overall_spatial_structure]：

| 控规法定结构 | 内容 | JDSFB 对位 |
| --- | --- | --- |
| 一带 | 京张铁路遗址公园产业创新带 | 折叠带本体——物理层遗产廊道 × 数字层数据走廊 |
| 一轴 | 中关村大街创新发展轴 | 数据契约的服务接口走廊（衔接西翼） |
| 两心 | 五道口中心、大钟寺中心 | 五道口=折叠中枢 Fold Hub 核心；大钟寺=流通接口 Exchange Port 核心 |
| 多点 | 知春路、四道口（一级）；海淀黄庄、数码大厦、皂君庙、知春路西、银谷、西土城、北邮（二级） | 边缘计算节点与时空折叠点的落位锚点池 |

城市更新总体框架回应官方「近千万平方米存量空间 + 100 万㎡ 更新载体」口径 [source:THREE-ZONES-TWO-WINGS-RELEASE]：低效空间识别以控规 75 个主导功能分区（居住主导 26、文化教育主导 16、混合功能主导 17、绿地水域主导 6 等，控规文本第 12 条）为单元底账，更新强度不突破基准强度五级分区（控规文本第 14 条），建筑高度严守 36/45/60/80/100 米 6 类基准高度分区（控规文本第 16 条）。`geometry/land_use.geojson` 完整覆盖设计边界且无重叠 [data:geometry/land_use.geojson#LU-001] [depth:land_use_layout]，`geometry/buildings.geojson` 表达更新建筑基底 [data:geometry/buildings.geojson#BLDG-001] [metric:building_footprint_area_sqm]，开发强度控制由 [depth:development_intensity_controls] 管理。

### 京张数据契约与算法贡献指数（legal source: REGULATORY-PLAN-HD00-1601 Art. 82）

控规第 82 条明确「探索数据要素市场化配置改革创新路径」[source:REGULATORY-PLAN-HD00-1601]。JDSFB 将该法定条款实施性深化为「京张数据契约」机制：

- **公共数据授权三级清单**：L1 开放层（城市运行匿名聚合数据，免授权调用）、L2 授权层（片区级感知数据，企业 KYC 认证后申请）、L3 沙盒层（敏感场景数据，仅在学北园数据沙盒内可用不可见），目标覆盖比例见 [metric:data_covenant_coverage_ratio]。
- **算法贡献指数**：企业/开发者以优化城市运行的算法换取数据使用权，指数 = 模型调用频次 × 场景权重 × 效果评估分（基线与计算方式见 [metric:algorithm_contribution_index]），高贡献者获得空间奖励阶梯（测试场优先权 → 展示位 → 载体租金减免建议）。
- **合规底线**：企业 KYC、数据脱敏、用途登记、可审计日志四要件缺一不可；指数机制为运营建议，不构成政府审批或承诺。

### 1+3+N 数字孪生架构（对接控规文本第 82 条城市运行智能体系）

「1」城市级数据湖（学北园，依托国家级算力底座）；「3」片区级边缘节点（三片区各一，负责本地实时计算与隐私脱敏）；「N」街道级可插拔 AI 模型与传感节点（模块化临时设施，不计入高度分区管控，图则标注可拆卸属性）。接口标准遵循开放 API + 隐私脱敏前置；节点网络落位见 [data:geometry/public_space.geojson#DATA-001] [metric:data_nodes_count]。全部边缘节点与传感器避开控规地下空间禁建区（不可移动文物保护范围及一类建控地带）[source:REGULATORY-PLAN-HD00-1601]。

## 重点区域详细设计

三处重点区域详细设计引用临时范围 [data:geometry/key_areas.geojson#PROV-KEY-001]、[data:geometry/key_areas.geojson#PROV-KEY-002]、[data:geometry/key_areas.geojson#PROV-KEY-003]，深度由 [depth:three_key_area_detailed_design] 约束，合规矩阵分别覆盖公告 1.5.3.1、1.5.3.2、1.5.3.3。**口径说明**：学北园位于控规范围以外（控规北至成府路），按统筹研究范围对象处理，控规深度落位仅覆盖五道口（原点社区）与大钟寺；公告 1.5.3.1 所称「众智园 AI 自主创新加速区」与官方发布「学北园 AI 自主创新加速区」为同一片区，本方案统一使用「学北园（公告口径：众智园）」。

| 重点片区 | 设计定位 | 空间动作 | AI 产业与运营场景 | 证据引用 |
| --- | --- | --- | --- | --- |
| 学北园 AI 自主创新加速区 | 数智源点 · 花园型全栈自主创新街区 | 强化清河界面、产业展示、低碳创新交往；数据沙盒与算力底座集中布置 | 城市数据开放沙盒、自主模型测试、标准制定工作坊、安全治理展示 | [data:geometry/key_areas.geojson#PROV-KEY-001] |
| 北京 AI 原点社区 | 折叠中枢 · 近校型成果转化与人才社区 | 校区、园区、街区慢行缝合；可编辑城市底座示范区；清华园车站旧址主折叠点 | 开源社区、成果发布、人才特区服务、AR/MR 时空叙事 | [data:geometry/key_areas.geojson#PROV-KEY-002] |
| 大钟寺 AI 产业集聚区 | 流通接口 · 城市型智能经济与国际交往街区 | 大钟寺站一体化、四象限步行连通、数据资产交易平台载体更新 | 数据资产登记交易、智能体与智能终端展示、国际路演 | [data:geometry/key_areas.geojson#PROV-KEY-003] [metric:key_area_count] |

![三处重点区域索引与设计任务图](assets/figures/key-areas.png)

### 7 个时空折叠点设计（全部锚定控规文保清单与重点地区）

按控规文本第 26 条不可移动文物清单与第 9 条空间结构、第 21—23 条二级重点地区（京张沿线、南长河绿廊沿线、西直门枢纽）管控，7 个折叠点全部重新锚定法定资产，原脚手架虚构节点（老站台、水塔、道岔等）一律废弃。全国重点与市级文保仅允许 AR/MR「体验叠加」，严禁任何物理改动（含传感器安装），并遵守保护范围与建控地带管控 [source:REGULATORY-PLAN-HD00-1601]：

| 编号 | 锚点 | 法定级别 | 历史事件层 | 未来场景层（AR/MR 体验叠加） | 落位 |
| --- | --- | --- | --- | --- | --- |
| FOLD-001 | 清华园车站旧址 | 北京市文保 | 1910 年京张铁路清华园站，詹天佑主持修建 | **主折叠点**：「AI 导览员詹天佑」大模型复活历史讲述，时空穿梭首发站 | [data:geometry/public_space.geojson#FOLD-001] |
| FOLD-002 | 高梁闸 | 全国重点文保 | 元代通惠河水闸，漕运咽喉 | 古今水智：AR 叠加漕运水系与当代海绵城市数据 | [data:geometry/public_space.geojson#FOLD-002] |
| FOLD-003 | 元大都城墙遗址 | 全国重点文保 | 元代大都城北垣，800 年城市轮廓 | 城垣时间剖面：MR 展示城市边界生长史 | [data:geometry/public_space.geojson#FOLD-003] |
| FOLD-004 | 铁科院科研专用铁路 | 未定级文物 | 新中国铁道科研试验线 | 「数据折叠」叙事独特资产：轨道 × 科研史，实验数据可视化长廊 | [data:geometry/public_space.geojson#FOLD-004] |
| FOLD-005 | 大慧寺 | 全国重点文保 | 明代古刹，彩塑艺术宝库 | 数字造像研究展示（远程投影，不接触本体） | [data:geometry/public_space.geojson#FOLD-005] |
| FOLD-006 | 五道口中心 | 控规「两心」之一 | 当代宇宙中心青年文化地标 | 折叠中枢客厅：开发者共创、成果首发、夜间数据光毯 | [data:geometry/public_space.geojson#FOLD-006] |
| FOLD-007 | 西直门枢纽 | 控规二级重点地区 | 百年京张起点门户 | 时空折叠南门户：抵达仪式、城市数据总览屏 | [data:geometry/public_space.geojson#FOLD-007] |

折叠点数量见 [metric:fold_nodes_count]，AR/MR 体验点统计见 [metric:ar_mr_experience_points]。折叠点坐标已按文保实体位置示意校准：FOLD-001/006 位于公告临时总体设计范围北缘、FOLD-002/003/004/005/007 分布于控规 16.7 km² 法定范围内（其中 FOLD-003 元大都城墙遗址、FOLD-005 大慧寺位于临时走廊边界之外、属统筹研究范围），全部折叠点以法定控规范围为空间基准、以数据契约跨域串联，不受临时走廊边界限制；落位管控遵循「京张铁路遗址公园沿线」二级重点地区「南北通、东西融」公共空间系统要求（控规文本第 21 条）[source:REGULATORY-PLAN-HD00-1601]。

### 折叠点场景效果图（意向示意）

以下场景图按「中缝折叠 · 双时代对开」视觉体系绘制：左幅为 1909 历史层剪影，右幅为 2035 未来层 AR/MR 意向示意。场景图为设计意向表达，非实景照片；全部体验以数字叠加实现，不改变文物本体 [depth:three_key_area_detailed_design]。

![FOLD-01 清华园车站旧址主折叠点场景示意图](assets/figures/scenes/fold-01-qinghuayuan.png)

![FOLD-02 高梁闸时空折叠点场景示意图](assets/figures/scenes/fold-02-gaoliangzha.png)

![FOLD-03 元大都城墙遗址时空折叠点场景示意图](assets/figures/scenes/fold-03-yuandadu.png)

![FOLD-04 铁科院科研专用铁路时空折叠点场景示意图](assets/figures/scenes/fold-04-tiekeyuan.png)

![FOLD-05 大慧寺时空折叠点场景示意图](assets/figures/scenes/fold-05-dahuisi.png)

![FOLD-06 五道口中心折叠中枢节点场景示意图](assets/figures/scenes/fold-06-wudaokou.png)

![FOLD-07 西直门枢纽时空折叠南门户场景示意图](assets/figures/scenes/fold-07-xizhimen.png)

## AI 创新生态、人才画像与 AI+ 场景

方案建立面向 AI 人才和企业的空间需求画像，覆盖研发办公、开源协作、成果发布、企业服务、人才居住、社交学习、消费生活、运动休闲和国际交往，对接控规文本第 83 条「人工智能、互联网和相关服务业、新媒体为重点的创新集群」与「智慧高效、城绿交融、活力共享的城市创新街区」条款 [source:REGULATORY-PLAN-HD00-1601]。AI+ 场景落到具体图层与治理边界：公共空间场景引用 [data:geometry/public_space.geojson#PUBLIC-001]，慢行场景引用 [data:geometry/roads.geojson#ROAD-001]，开放空间场景引用 [data:geometry/green_space.geojson#GREEN-001] 与 [metric:public_space_ratio]、[metric:green_ratio]。

| 用户画像 | 典型需求 | 空间响应 | 自检边界 |
| --- | --- | --- | --- |
| 开源开发者（原点社区青年研发占比超 70% [source:THREE-ZONES-TWO-WINGS-RELEASE]） | 发布、协作、测试、社区声誉 | 折叠中枢开源发布厅、公共代码墙、夜间协作空间 | 不采集个人行为轨迹；活动数据只做聚合统计 |
| 初创团队 | 低成本办公、算力入口、产品试验场 | 学北园共享测试场、端侧算力服务点、标准治理咨询 | 算力和数据服务需另行授权 |
| 头部企业访客 | 展示、商务、国际接待、人才招聘 | 大钟寺国际路演客厅、轨道站点接驳、重点企业周边公共空间 | 企业标识和案例须清权 |
| 周边居民（控规常住人口基线 [metric:population_baseline]） | 通勤、休闲、社区服务、低扰动更新 | 京张遗址公园慢行环、社区会客厅嵌入、夜间照明和活动分级 | 不将居民画像用于商业推荐 |
| 高校师生（控规 9 处高校） | 成果转化、跨校协作、日常慢行 | 校区—园区慢行缝合、成果转化驿站、AI 教育体验点 | 校园数据和科研成果需授权 |

| 场景卡 | 空间载体 | 设计说明 |
| --- | --- | --- |
| 01 城市数据开放沙盒 | 学北园 | 依托国家级算力底座供企业训练垂直模型，探索公共数据授权运营（京张数据契约 L3 层） |
| 02 开源发布厅 | 北京 AI 原点社区 | 面向高校、开源社区和初创团队的成果发布、代码贡献展示和小型路演空间 |
| 03 端侧算力驿站 | 总体设计范围节点 | 与公共服务、低碳能源策略结合的 1+3+N 街道级节点原型 |
| 04 AI 慢行导航 | 京张遗址公园活力带 | 可解释导视与低侵入传感识别慢行断点、拥挤节点和无障碍需求 |
| 05 大钟寺国际路演客厅 | 大钟寺 AI 产业集聚区 | 智能体、智能终端和内容消费企业的展示、洽谈、媒体发布和国际交流 |
| 06 需求响应式公交与无人公交接驳 | 轨道站点与廊道节点 | 落实控规文本第 52 条特色公交条款，AI 调度微循环接驳 [source:REGULATORY-PLAN-HD00-1601] |
| 07 自适应公共空间 | 小月河场景赋能翼优先测试 | 广场与街道按人流、天气、活动自动调节灯光、座椅与功能，占比目标见 [metric:adaptive_public_space_ratio] |
| 08 AI 历史叙事 | 7 个时空折叠点 | 大模型复活詹天佑等历史人物担任 AI 导览员，讲述百年京张故事 |
| 09 情感计算公共空间 | 东翼滨水 + 社区会客厅 | 实时感知人群情绪与需求，动态调整环境参数，对接 AI+ 康养 |
| 10 具身智能与 AI 医疗实景试点 | 小月河滨水空间 | 呼应官方「智慧城市试验场」定位，AI+ 民生、AI+ 文娱、AI+ 康养多元应用 [source:THREE-ZONES-TWO-WINGS-RELEASE] |

### 伦理与数据治理

感知数据本地化处理（片区边缘节点内脱敏后才可上行）、公众告知与退出机制（场景节点公示数据采集范围与用途，提供实体退出通道）、算法审计与偏见检测（算法贡献指数评审含公平性评估）。城市智能体可辅助识别慢行断点、公共空间热力、设施维护、企业服务需求和活动安全风险，但不能替代规划审批、不能输出未经授权的个人画像、不能声称获得官方实施承诺。所有 AI 场景节点进入结构化图层或合规矩阵，便于评审者核查其与产业、空间和公共利益的关系。

## 用地、建筑规模与拆改留方案

用地方案依据国土空间调查、规划、用途管制分类公开标准表达 [standard:MNR-LAND-USE-CLASSIFICATION-GUIDE]，形成完整、闭合、无缝的用地分区 [data:geometry/land_use.geojson#LU-001]。建筑方案区分保留、改造、更新、新建对象，高度、体量、界面和风貌控制由 [depth:height_massing_character] 管理，拆改留方法由 [depth:retain_renovate_demolish] 管理并对齐控规文本第 84 条「留改拆补多种更新方式」实施策略 [source:REGULATORY-PLAN-HD00-1601]。

**规模刚性约束**：方案任何情景下总建筑规模不突破控规 2408.0 万㎡ 法定上限 [metric:total_floor_area_ceiling_sqm]（控规文本第 7、13 条）；容积率法定基线约 1.46（2408.0 万㎡ ÷ 城乡建设用地 1645.6 公顷推导，标注推导公式与控规依据）[metric:statutory_floor_area_intensity]；提交范围内建筑基底占地比例 [metric:floor_area_ratio]。人口与岗位模拟基数采用控规法定值：常住人口约 36.4 万人 [metric:population_baseline]、就业岗位约 39.7 万个 [metric:employment_baseline]。凡涉及具体地块的建筑高度、开发强度、退线等指标，因控规图则未数字化，统一写为「待正式图则条件确认」，不以推测值冒充审定指标（登记 `assumptions.json`）。

## 交通、轨道、市政与公共服务设施

交通方案对接控规条款：轨道站点一体化管控（控规文本第 36 条）与轨道微中心（适当提高开发强度、鼓励用地混合，控规文本第 37 条）、「轨道交通 + 绿色换乘」体系（控规文本第 51 条）、需求响应式公交与无人公交特色公交（控规文本第 52 条，已纳入场景卡 06）[source:REGULATORY-PLAN-HD00-1601] [depth:traffic_rail_slow_parking]。重点覆盖北五环、京张遗址公园跨环路节点、五道口、清华东路西口、大钟寺站及重点企业周边联系；道路和慢行图层保持在提交边界内，与公共空间、绿地、产业节点相互校核 [data:geometry/roads.geojson#ROAD-001] [data:geometry/public_space.geojson#PUBLIC-001]。

![交通慢行与蓝绿公共空间复合系统图](assets/figures/mobility-bluegreen.png)

市政与公共服务设施落实控规专项统筹：雨污分流（2035 年城市集中建设区雨水管渠覆盖率 100%，控规文本第 58 条）、分布式光伏（控规文本第 60 条）、多网融合 5G（控规文本第 63 条），并与 JDSFB 新型基础设施（分布式能源、端侧算力、边缘节点）融合布局 [depth:municipal_new_infrastructure]。海绵城市按控规年径流总量控制率分区管控（滨水与遗址公园沿线 ≥85%、过渡区 75%—85%、一般建成区 65%—75%，控规文本第 67 条及海绵城市规划图），JDSFB 雨洪调蓄节点优先布置在 ≥85% 管控分区与蓝绿廊道交汇处。设施标准、服务半径、运营模式和分期逻辑在正文说明；管线、能源、排水、防洪（南长河—转河、北护城河 100 年一遇，土城沟 50 年一遇，控规文本第 27 条）、消防等工程资料缺失部分列为正式深化前置条件 [data:geometry/constraints.geojson#CONSTRAINTS]。

## 蓝绿空间、公共空间与城市风貌

蓝绿空间落实控规「三带六轴、多廊多中心」景观格局：三带即京张铁路遗址公园、南长河、小月河三条活力景观带（控规文本第 17 条）[source:REGULATORY-PLAN-HD00-1601] [depth:blue_green_public_space]。方案以遗址公园活力带为骨架，提出南北贯通、东西连通的步道、骑行道和绿色空间体系，识别慢行断点、上跨环路节点与公园南北端景观节点 [data:geometry/green_space.geojson#GREEN-001] [data:geometry/public_space.geojson#PUBLIC-001]。绿地与公共空间占比可复算指标分别为 [metric:green_ratio] 与 [metric:public_space_ratio]。

公共空间落实控规花园城市场景（控规文本第 33 条）、8 处社区会客厅（5 分钟步行生活圈，控规文本第 38 条）、四类游憩体系（专类公园、复合公共空间、社区公园、游园，控规文本第 29 条）与三级绿道网络（市级—区级—社区级，控规文本第 30 条）；JDSFB 自适应公共空间优先选择社区会客厅与游园节点测试。城市风貌执行控规四类风貌分区（创新核心、高校科研、宜居生活、滨水活力）与街道五类管控，融合京张铁路历史文化、中关村创新文化和 AI 创新文化 [standard:MOHURD-URBAN-DESIGN-MEASURES]。AI 朝圣地标体系 = 7 个时空折叠点 + 「折」字视觉符号 + 算法贡献荣誉墙（贡献者姓名上墙须本人授权）；所有品牌、字体、图像、肖像和企业标识均有清权来源，风貌控制分清官方管控、设计建议和待确认条件，不给出伪精确控制线。

## 更新项目清单、实施政策与分期计划

实施项目清单与控规文本第 84—88 条实施策略和适应性规定衔接（三大设施、绿地广场与水域下限管理；公园绿地广场可在主导功能分区内调整位置形状；支路街坊路可优化线位）[source:REGULATORY-PLAN-HD00-1601] [depth:renewal_project_list] [depth:phasing_implementation]，分期空间证据为 [data:geometry/phasing.geojson#PHASE-001]。

| 项目编号 | 项目名称 | 类型 | 主要依赖 | 证据引用 |
| --- | --- | --- | --- | --- |
| JZ-01 | 京张遗址公园慢行断点缝合 | 公共空间/交通 | 道路红线、桥下空间、交通组织复核 | [data:geometry/roads.geojson#ROAD-001] |
| JZ-02 | 学北园数据沙盒与清河创新界面 | 新基建/蓝绿空间 | 算力底座载体、河道蓝线、生态和防洪条件 | [data:geometry/green_space.geojson#GREEN-001] |
| JZ-03 | 原点社区折叠中枢与近校成果转化街 | 城市更新/产业服务 | 校区边界、权属、首层业态 | [data:geometry/buildings.geojson#BLDG-001] |
| JZ-04 | 大钟寺站四象限步行连通与数据资产交易客厅 | 轨道一体化/慢行 | 轨道站点、道路交叉口、市政管线 | [data:geometry/public_space.geojson#PUBLIC-001] |
| JZ-05 | 1+3+N 数字孪生底座与端侧算力节点 | 新基建/公共服务 | 能源、算力、安全和运营主体 | [data:geometry/public_space.geojson#DATA-001] |
| JZ-06 | 7 个时空折叠点 AR/MR 体验工程 | 文化科技/运营 | 文保部门审批（仅限体验叠加）、内容清权 | [data:geometry/public_space.geojson#FOLD-001] |
| JZ-07 | 京张数据契约运营平台 | 数据要素/治理 | 控规文本第 82 条实施路径、企业 KYC 与审计机制 | [metric:data_covenant_coverage_ratio] |
| JZ-08 | 全球 AI 活动周公共路线 | 运营/品牌 | 公共空间许可、活动安全、版权清权 | [data:geometry/phasing.geojson#PHASE-001] |

分期与 100 天征集设计周期区分：近期试点（JZ-01、JZ-06、JZ-08，轻量设施与运营活动先行）、中期更新（JZ-02—JZ-05，待正式控规图则、市政、交通和权属条件确认）、长期治理（JZ-07，数据契约运营机制迭代）。运营机制三项：数据资产登记与交易（AI 企业以贡献算法换取数据使用权）、城市算法贡献指数（优化城市运行的模型获得政策或空间奖励）、时空叙事共创（开放历史数据接口，鼓励开发者创作京张历史 AI 游戏、影视、艺术内容）——均为运营建议，责任边界、转化路径和风险在正文中明示，不构成政府活动安排。

## 指标体系、面积复算与合规矩阵

指标体系分三类 [depth:metrics_recalculation]：第一类可由提交几何直接复算（边界面积、绿地与公共空间比例、建筑基底、重点区数量、折叠点与数据节点数量）；第二类需法定文件支撑（总建筑规模上限、容积率基线、人口与岗位基线，均引自控规）；第三类需运营校准（算法贡献指数、数据契约覆盖率、自适应空间占比、场景使用频次，正式运营后持续校准）。所有 known 指标可从 GeoJSON 或登记来源复算，完整数值、公式、置信度保存在 `metrics.json`；`scripts/spatial_review.py` 与 `scripts/visual_review.py` 结果为 formal 自证证据。

| 指标 | 数值/状态 | 类别 | 依据 |
| --- | --- | --- | --- |
| 总体设计范围面积 [metric:site_area_sqm] | 约 1141.3 万㎡（provisional） | 一 | [data:geometry/site_boundary.geojson#SITE-001] |
| 建筑基底面积 [metric:building_footprint_area_sqm] | 约 31.1 万㎡ | 一 | [data:geometry/buildings.geojson#BLDG-001] |
| 绿地率 [metric:green_ratio] / 公共空间比例 [metric:public_space_ratio] | 12.3% / 7.3% | 一 | [data:geometry/green_space.geojson#GREEN-001] |
| 重点区域数量 [metric:key_area_count] | 3 | 一 | [data:geometry/key_areas.geojson#PROV-KEY-001] |
| 时空折叠点 [metric:fold_nodes_count] / 数据节点 [metric:data_nodes_count] | 7 / 12 | 一 | [data:geometry/public_space.geojson#FOLD-001] |
| 总建筑规模法定上限 [metric:total_floor_area_ceiling_sqm] | 2408.0 万㎡ | 二 | 控规文本第 7、13 条 [source:REGULATORY-PLAN-HD00-1601] |
| 容积率法定基线 [metric:statutory_floor_area_intensity] | 约 1.46（推导） | 二 | 控规文本第 7 条 |
| 建筑基底占地比例 [metric:floor_area_ratio] | 约 2.72% | 一 | [data:geometry/buildings.geojson#BLDG-001] |
| 人口 [metric:population_baseline] / 岗位 [metric:employment_baseline] 基线 | 36.4 万 / 39.7 万 | 二 | 控规文本第 7 条 |
| 算法贡献指数 [metric:algorithm_contribution_index] | 运营期校准 | 三 | 控规文本第 82 条实施建议 |

![核心指标复算与证据链图](assets/figures/metrics-evidence.png)

合规矩阵是任务响应性主控文件：公告 1.3、1.4、1.5 与 agent.1—agent.6 每条必选任务对应报告章节、图层、指标、图纸、HTML 页面、来源、假设和自检项；控规合规模块将 16.7 km² 范围、2408 万㎡ 上限、6 类高度分区、75 主导功能分区、13 处文保、三带六轴、两心多点逐条映射到章节与图层，每条标注 `[source:REGULATORY-PLAN-HD00-1601]`。

## 风险、版权与合规说明

**要求双语言。** 方案主文件为中文，`proposal.en.md` 提供完整对照译文；A3/A0、HTML 和含文字图件均提供对应语言副本，并优先使用 `docs/terminology-glossary.md` 的赛事推荐译法。所有图片、图纸、图标、数据和代码资产在 `sources.json` 或 `report/copyright_statement.md` 中说明来源、许可和授权状态。HTML 页面不加载远程脚本、远程地图瓦片、远程字体、iframe、表单或外部 API，不跟踪评审者行为。

风险与缺资料清单由风险深度项、约束图层和场地包共同校核 [depth:risk_missing_data] [data:geometry/constraints.geojson#CONSTRAINTS] [source:SITE-PACKAGE]，关键风险包括：官方边界与重点区 polygon 未发布（回退：provisional 边界 + 控规四至交叉校核）；控规图则未数字化（回退：仅引用文本条款，地块级结论降级为待确认）；建筑规模突破风险（控制：2408 万㎡ 写入生成约束与自检）；文保禁建风险（控制：文保单位仅体验叠加，传感器不进入保护范围与一类建控地带，地下空间禁建区不布置数据节点）[source:REGULATORY-PLAN-HD00-1601]。

本方案不声称官方批准、审定控规、最终土地权属、最终建设规模或保证实施。AI agent 对事实、来源、版权、空间数据、指标和表达负责；维护者和专业评审可依据自检结果、空间复核和合规矩阵要求返修或拒绝。建筑专业深度规定待取得官方文件后启用，当前作为缺资料清单管理 [standard:MOHURD-ARCH-DESIGN-DEPTH-2016]。

## 参考资料

- 《HD00—1601 等街区控制性详细规划（街区层面）（2024 年—2035 年）》文本条款 [source:REGULATORY-PLAN-HD00-1601]
- 官方「三区两翼」发布口径（百年京张 AI 创新带产业事实）[source:THREE-ZONES-TWO-WINGS-RELEASE]
- brief/public-brief.md、brief/site-package/design_brief.json、brief/site-package/enums/ [source:SITE-PACKAGE]
- data/processed/agent_fact_pack.md [source:PROCESSED-FACT-PACK]
- 征集资格预审公告 [source:OFFICIAL-ANNOUNCEMENT]、面向智能体任务书 [source:AGENT-TASKBOOK]
- 完整机器索引：见 `sources.json`、`metrics.json`、`compliance_matrix.json`、`standard_matrix.json` 与 `design_depth_matrix.json`
