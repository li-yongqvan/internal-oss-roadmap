# 02 机制裁剪：单人可运营的最小机制集（决策点 D2）

准绳：1 名兼职运营者 + 首批个位数参与者，粗糙可用优先。检索时间：2026-10-31。
总纲：InnerSource Commons 的 [Dedicated Community Leader](https://patterns.innersourcecommons.org/p/dedicated-community-leader) 模式记录了 Bosch 的教训——运营者从 50% 降到 30% 后贡献即枯竭。故六项机制全部压到"零仪式化"形态，把运营者时间留给沟通与 review；整个程序按 [Start as Experiment](https://patterns.innersourcecommons.org/p/start-as-experiment) 定位为限时实验，降低上马门槛。

## 一、机制裁剪总表

| 机制 | MVP 形态 | 周成本 | 升级触发条件 | 明确裁掉（理由） |
|---|---|---|---|---|
| 成员阶梯 + OWNERS | 两级：运营者(Owner) + Trusted Committer。每仓库 1 个 CODEOWNERS/OWNERS 文件只写运营者；贡献满约 4 周、≥5 个已合并 PR 即可被公开邀为 TC（给 review+合并权） | ~0.5h | 单仓库 ≥2 名稳定贡献者、review 排队 >1 周 → 加 Reviewer 层；跨仓库复制 → K8s 四级阶梯 | 四级阶梯、正式申请与投票流程（个位数下中间层级无差异，晋升=运营者群里一句话） |
| good first issue 流水线 | 无流水线。运营者每周花 30 分钟手动挑 1-2 个任务打 `good first issue` 标签并写清验收标准（K8s 定义：gfi 是 help wanted 子集、承诺额外辅导） | ~0.5h | ≥3 名新人同时找不到任务，或候选任务池 >20 → 上 label bot + 看板 | Prow 类机器人、多标签体系、双周 triage 会（任务供给人工可保证） |
| 导师计划 | 结对 shadow：运营者/TC 直接带 1-2 名新人，每周一次 30 分钟 1:1 + 指定 1 个入门任务。不接 LFX 这类外部带薪项目 | ~1h | 新人批次 ≥5 人或引入校招生 → 套 LFX 结构做内部营（12 周、期中/期末评审） | 申请筛选、津贴、多导师池、群组队列（LFX 的 HR/经费平台对内部结对是纯开销） |
| 轻量提案流程 | 两档：小改动（文档/修 bug）直接 PR；大改动（新模块/接口变更/跨团队影响）填 issue 模板（背景/方案/影响/备选 4 节），默认 72h 意见期，无人反对即通过 | ~0.5h | 同期 open 提案 ≥3 个或出现跨部门利益冲突 → 引入 InnerSource RFC 模式（RFC 目录 + 状态页） | KEP 的多仓库 YAML 元数据、阶段状态机、SIG 分组评审（个位数参与者没有评审人力） |
| 行为准则 | 整体采用 Contributor Covenant（附中文译文），报告渠道 = 运营者邮箱/私聊；v3.0 支持自定义 reporting 段以匹配单人执行。执行两步：先私下沟通，再上报其主管 | ~0h（一次性 0.5h 落地） | 参与者 >20 或出现跨部门冲突 → 设 2-3 人执行组（对标 CNCF CoC Committee） | 自写条款、匿名举报渠道、独立执行委员会（匿名渠道是规模化防报复设计，熟人小群反而增加摩擦） |
| 贡献度量 | 每月 30 分钟用平台自带统计（Gitea Activity / GitLab Contribution Analytics / GitHub Insights，见 01 号资产）记 3 个数：活跃贡献者数、已合并 PR 数、gfi 完成率，发月度置顶贴；配 InnerSource "Praise Participants" 公开点名表扬 | ~0.1h | 项目 ≥3 个或需向管理层证明 ROI → devstats/CHAOSS/Repository Activity Score | devstats 级自建面板、个人排行榜、与 KPI 硬挂钩（前三月防凑数，细节归 03 号票） |

机制性成本合计约 **2-2.5 h/周**，加上平台运维（01 号票）与答疑，仍在兼职容量内，但已接近 Dedicated Community Leader 模式警示的 30% 红线—— recruiting 新 TC 是第一优先事项。

## 二、三个裁剪原则（旁证）

1. **决策用 lazy consensus，不用投票**。Apache 官方定义：不必等明确批准即可推进，只需准备好在有人反对时倾听（[Decision-Making](https://community.apache.org/committers/decisionMaking.html)）。六项机制中除行为准则外，日常决策（合 PR、收 RFC、晋 TC）全部走 72h lazy consensus。
2. **小改动免提案**。Rust RFC 0002 明文："Some changes do not require an RFC"（改措辞、文档、不改语义的重构）（[RFC 0002](https://rust-lang.github.io/rfcs/0002-rfc-process.html)）。提案流程只管"影响他人"的改动，这与 KEP 只管重大特性一致，但我们把阈值放得更低。
3. **角色两级起步**。Apache 也只有 committer→PMC 两级正式角色；InnerSource 的 [Trusted Committer](https://patterns.innersourcecommons.org/p/trusted-committer) 模式（TC = 唯一可信提交者 + 保持贡献者在环内）是单人运营下最自然的第二级。K8s 的 Member/Reviewer/Approver/Owner 四级是为数百人设计的（[community-membership.md](https://github.com/kubernetes/community/blob/master/community-membership.md)），人数不够时层级只会空转。

## 三、升级路线速查（对应 D2）

- 首批个位数 → **当前 MVP 集全保留，只此一套**。
- 10-30 人（第二阶段）→ 升级 good first issue 自动化、RFC 目录页、CoC 执行组、devstats 度量。
- >50 人（第三阶段）→ 才考虑 K8s 四级阶梯、SIG 组织、LFX 式正式导师营。

## 主要来源

- InnerSource Commons Patterns：[Trusted Committer](https://patterns.innersourcecommons.org/p/trusted-committer)、[Dedicated Community Leader](https://patterns.innersourcecommons.org/p/dedicated-community-leader)、[Start as Experiment](https://patterns.innersourcecommons.org/p/start-as-experiment)、[RFC 决策模式](https://patterns.innersourcecommons.org/)（Transparent Cross-Team Decision Making using RFCs、Praise Participants、Repository Activity Score 均见其模式目录）
- Apache：[Decision-Making / lazy consensus](https://community.apache.org/committers/decisionMaking.html)
- Rust：[RFC 0002 The RFC Process](https://rust-lang.github.io/rfcs/0002-rfc-process.html)
- CNCF/Linux Foundation：[LFX Mentorship](https://mentorship.linuxfoundation.org/)、[文档](https://docs.linuxfoundation.org/lfx/mentorship)（12 周学期、每年 3 期、期中/期末评审，见 [CNCF 博客](https://www.cncf.io/blog/2023/05/30/my-lfx-mentorship-journey-the-best-starting-point-for-contributing-to-open-source)）
- Kubernetes：[help wanted 与 good first issue 标签](https://www.kubernetes.dev/docs/guide/help-wanted/)、[成员阶梯](https://github.com/kubernetes/community/blob/master/community-membership.md)
- Contributor Covenant：[官网](https://www.contributor-covenant.org)、[FAQ（允许自定义执行条款）](https://www.contributor-covenant.org/faq/)、[v3.0 发布说明](https://ethicalsource.dev/blog/contributor-covenant-3)
