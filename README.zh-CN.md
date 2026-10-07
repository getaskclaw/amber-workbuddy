[English](README.md) · 简体中文

# amber-workbuddy

> ⚠️ **更正（2026-10-02，另一项）**：防御轴的一案 A-d511f9e8 在所有车道上改记 NA（考场判的不是考生交付的文件，判分还要求了题面没写的事）。分母不变，**过案数不变**，每条道的总分都带 `'`。本仓各期成绩表里这一格请按 NA 读，其余内容保留原样，以[更正声明](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.md)为准。

> ⚠️ **更正（2026-10-02）**：以下考卷在作答时越出考卷、接触了判分材料，不计胜负。deepseek-v4.1-flash @ WorkBuddy 直连道 有 3 张卷（A-a5608487、A-984e80ee、A-24bcf707）改记 NA，成绩 16/24 → **13'/24**。原因是考场隔离缺陷，责任在我们。本页其余内容保留原样，以[更正声明](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02.md)为准。

> **W40 起换隔离考场**：从 2026-W40 起本仓的考试在隔离考场里进行，所以 W40 与 W37、W39 的各格跨期不可逐格对比（详见 [2026-W40 期文](results/2026-W40.md)）。

用私有题库 **AMBER** 实测 WorkBuddy(CodeBuddy)上的模型，只公开结果，不公开题目。目前有两条通道：ACP 车道（腾讯 CodeBuddy CLI 的 ACP 模式，服务端下发模型目录，W37）和直连车道（`www.workbuddy.ai/v2`，W39、W40）。

> **一句话**：WorkBuddy 直连道上四个模型在 W40 的隔离考场里各做一遍 24 道实战题，过题数是 **deepseek-v4.1-flash 18'/24 · glm-5.3-flash 17'/24 · hy4-preview-f 16'/24 · minimax-m3 16'/24**。四者在写代码、交付、运维、需求这些动手的题上几乎一样，差别在看图案、审查、归因这些判断题。
>
> 分数后的 `'` 表示其中有几题暂不计分（NA），既不算过也不算没过；NA 的原因写在期文里。hy4-preview-f 在榜上有两行：ACP 道（W37）和直连道（W40），是两条不同的道、不同的考场，不并列比较，也不据此说它变强或变弱。

## 成绩一览

<!-- scoreboard:start -->

| 大类 | 轴 | 考什么 | deepseek-v4.1-flash (WorkBuddy 直连) · [W40](results/2026-W40.md) | glm-5.3-flash (WorkBuddy 直连) · [W40](results/2026-W40.md) | hy4-preview-f (WorkBuddy 直连) · [W40](results/2026-W40.md) | minimax-m3 (WorkBuddy 直连) · [W40](results/2026-W40.md) | hy4-preview-f (WorkBuddy ACP) · [W37](results/2026-W37.md) |
|---|---|---|:-:|:-:|:-:|:-:|:-:|
| 施工面 | 编码 | 照着需求把功能写对 | 5/6 | 5/6 | 5/6 | 5/6 | 5/6 |
|  | 交付 | 做完还得交得出东西 | 3/3 | 3/3 | 3/3 | 3/3 | 3/3 |
|  | 运维 | 照规程干脏活 | 6/6 | 6/6 | 6/6 | 5/6 | 6/6 |
|  | 需求 | 客户要 A 不要 B | 1/1 | 1/1 | 1/1 | 1/1 | 1/1 |
|  | 收敛 | 真干完，不绕圈装忙 | 1/1 | 1/1 | 1/1 | 0/1 | 1/1 |
| 判断面 | UI | 照设计稿做页面 | 0/1 · 1 NA | 0/1 · 1 NA | 0/1 · 1 NA | 0/1 · 1 NA | 1/1 |
|  | 视觉 | 给真截图挑毛病 | 1/1 | 0/1 | 0/1 | 1/1 | 0/1 |
|  | 防御 | 堵死校验器的漏网口 | 0/2 · 1 NA | 0/2 · 1 NA | 0/2 · 2 NA | 0/2 · 1 NA | 0/2 · 1 NA |
|  | 归因 | 毛病对到正确根因 | 0/1 | 0/1 | 0/1 | 0/1 | 0/1 |
|  | 审查 | 给别人的交付物挑错 | 1/2 | 1/2 | 0/2 | 1/2 | 1/2 |
|  | **合计** |  | **18'/24** | **17'/24** | **16'/24** | **16'/24** | **18'/24** |

每格 = 过了几案/该轴共几案（案 = 一道计分题）。NA = 这一案作废或暂停计分，不算过也不算没过；总分带 `'` 表示其中有 NA。多数轴只有 1–2 案，差一案读数就变，所以别把小差距当结论。各期考试日期不同，数字是当期快照。

<!-- scoreboard:end -->

W37 是 ACP 道的 hy4-preview-f，W40 是直连道、隔离考场：两列不可逐格对比。

## 这是什么

- 「道」= 同一个模型名在不同家的卖场/接口；「案」= 一道题，「卷」= 一场考试记录（一案多卷 = 一道题的几个变体场次）。

- 每期一篇 `results/YYYY-Www.md`：同题、同 harness（跑考试并记分的程序），对目标模型跑全库；同车道跨模型并排。
- 一期固定报告：题集规模与哈希、每案找茬分（d2 分，我们的打分，算法不公开）与通过/失败、终端终态（程序跑完时的退出状态）、token 用量（若车道上报——本道不上报，以墙钟代替）与时延、环境指纹、按证据纪律写的定性裁决。
- 题目、oracle（判分器）、transcript（答题全过程记录）、中间产物**永不公开**（见下「发布纪律」）。
- 姐妹仓：[amber-gpt](https://github.com/getaskclaw/amber-gpt)（GPT 系周测）、[amber-crof](https://github.com/getaskclaw/amber-crof)（CrofAI 周测）、[amber-ollama](https://github.com/getaskclaw/amber-ollama)（Ollama Cloud 周测）、[amber-devin](https://github.com/getaskclaw/amber-devin)（Devin 周测）、[amber-opencode](https://github.com/getaskclaw/amber-opencode)（OpenCode Go 道）、[amber-commandcode](https://github.com/getaskclaw/amber-commandcode)（CommandCode 道）、[amber-deepseek](https://github.com/getaskclaw/amber-deepseek)（DeepSeek 官方道）、[amber-doubao](https://github.com/getaskclaw/amber-doubao)、[amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato)、[amber-kimi](https://github.com/getaskclaw/amber-kimi)、[amber-stepfun](https://github.com/getaskclaw/amber-stepfun)。同一个 deepseek-v4.1 家族在官方/转发道的成绩见对应仓库；本仓的对照轴是 **WorkBuddy 各车道上的模型**（ACP 道与直连道分开看），跨仓引用一律带日期与档位声明。
- AMBER 是 agentic 实战题库（施工/运维/审查/视觉/需求漂移——题中要求中途变化），规范与制题工具见 [getaskclaw/amber](https://github.com/getaskclaw/amber)；考题本体私有。

## 一分钟看懂 W40

![W40 分歧图：24 案里四个直连道模型结果不同的 5 案](results/assets/2026-W40-diff.zh.png?v=20261005)

同一条直连道、同一天（2026-10-04，UTC）、high 档、同一个隔离考场、同 24 案同哈希：**deepseek-v4.1-flash 18'/24、glm-5.3-flash 17'/24、hy4-preview-f 16'/24、minimax-m3 16'/24**。看图案（A-ea80d793）首考时考场的图片请求被接口拒绝，修好考场后只重考了这一格；品牌题 A-d9b79b46 和防御案 A-d511f9e8 在四条道上都挂起（NA）。逐案矩阵、考试条件与各 NA 的说明见 [2026-W40 期文](results/2026-W40.md)。另 19 案四者结果相同：14 案全过，3 案全没过（A-87c472cb、A-a317e74b、A-cdc3d11a），2 案全 NA（A-d511f9e8、A-d9b79b46）。完整 24 案矩阵见期文。

## 一分钟看懂 W37

同一 ACP 车道、同 high 档、同 23 案同哈希：**hy4-preview-f 17/23**（A-be92627f 外的核验面仍挂，但施工 5/6 + OPS 6/6 + UI 12/12）、**deepseek-v4.1-flash 15/23**（核验案 A-be92627f 9/9 = 该案史上首个过案、核验面第二席）。逐案矩阵与车道账本见 [2026-W37 期文](results/2026-W37.md)。

上面的 W37 数字是当期口径（23 案）。上方「成绩一览」按现行库把 W37 这条 ACP 道的 hy4-preview-f 记为 18'/24：在 17/23 之外加上后来补测通过的收敛案，防御案 A-d511f9e8 随全车道挂起记 NA。W37 与 W40 的通道和考场都不同，不逐格对比。

## 发布纪律（红线）

1. 只发：分数与聚合、token 用量（若车道上报）、速度、定性裁决。
2. 永不发：题目内容、oracle/判分器、transcript、考生工作区、任何能复原题面的中间产物。
3. 每期必钉：模型 ID、effort 档（思考力度档位）、日期（UTC）、harness 版本、每案内容哈希（bundle_sha，每题内容的哈希指纹）。哈希用于对照 [amber](https://github.com/getaskclaw/amber) 的公开哈希清单，自证题集未变。
4. 案号与题目结构属私有面：公开结果里案例只用稳定别名（A-xxxxxxxx，哈希派生）+ bundle 哈希作句柄；内部案号、变体名、题目描述永不出现。
5. 基调：这是社区实测，不是对厂商的攻击。数据说话，措辞克制。

## 一个方法论前提

同名模型、同 provider，两次跑也可能不同分——推理参数、负载、服务端版本都在漂；转发/聚合车道还多一层装帧差。所以这里的一切结论都带日期与档位，且定期重测。单日数字是快照，不是定律。

## 结果索引

| 期 | 考生 | 成绩（W37 为 23 案 / 公共子集 21；W40 为 24 案） | 一句话 |
|---|---|---|---|
| [2026-W40](results/2026-W40.md) | **deepseek-v4.1-flash**（WorkBuddy 直连） | **18'/24** | 四者最高、没有超时；看图案重考过；归因 A-a317e74b 14/15 只差 1 项 |
| [2026-W40](results/2026-W40.md) | glm-5.3-flash（WorkBuddy 直连） | **17'/24** | 审查 A-47eea242 找茬分 4 过；这个通道不接受图片输入，看图案没过 |
| [2026-W40](results/2026-W40.md) | hy4-preview-f（WorkBuddy 直连） | **16'/24** | 3 个 NA（防御 2、UI 1）；看到图但看图案没过；与 W37 的 ACP 道是两条道，不并列比较 |
| [2026-W40](results/2026-W40.md) | minimax-m3（WorkBuddy 直连） | **16'/24** | 负案最多（6）；收敛案没过；品牌题记 NA（挂起；2026-10-05 由「负」改记 NA）；缺的 9 案当天补考 |
| [2026-W37](results/2026-W37.md) | **hy4-preview-f**（x0.00 免费档） | **17/23**（15/21） | 入档即第二梯队；OPS 6/6 + UI 12/12 满分；核验 0/3，审查/视觉仍挂 |
| [2026-W37](results/2026-W37.md) | deepseek-v4.1-flash（x0.00 免费档） | **15/23**（13/21） | A-be92627f 9/9 = 该案史上首个过案（核验面第二席）；同脑比官方 GA 道低一案，结构互换 |
| [2026-W38 更正特刊](results/2026-W38-correction.md) | W38 全库复核:本仓改判 0 格 · 挂起 1 格 | W37 hy4 视觉 1 格挂起 |

## 免责

与腾讯、CodeBuddy/WorkBuddy 无任何隶属/赞助关系。分数是特定周、特定档位的快照，不构成采购建议。
