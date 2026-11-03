# 03 度量与激励选项（D3/D4 事实基础）

调研日期：2026-10-31。前提：运营者 1 人兼职、粗糙可用优先。

## 一、度量：手工 → 半自动 → 自动

### 平台自带统计能力（可直接回答的问题）

- **GitLab**：组级"贡献分析"（push/MR/关闭 issue/评论，周/月/3 月维度，需 Premium）；项目级"贡献者分析"（commits 与增删行数，Free 可用）；"价值流分析"看各阶段耗时。能回答：谁在贡献、贡献多少、流转速度。[贡献分析](https://docs.gitlab.com/user/group/contribution_analytics)、[贡献者分析](https://docs.gitlab.com/user/project/repository/contributor_analytics)、[价值流](https://docs.gitlab.com/user/analytics/value_stream_analytics)
- **GitHub**：仓库 Insights → Contributors（top 100，不含 merge/空 commit）、Commits 活跃图。能回答：谁在贡献、活跃趋势；组织级聚合能力弱。[contributors](https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-projects-contributors)、[commits graph](https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/analyzing-changes-to-a-repositorys-content)
- **Gitea**：仓库 Activity 页（1.9+，贡献者/commit/PR/issue 按时间段统计，实时算自 git 历史）+ REST API（`/repos/{owner}/{repo}/activity/authors` 等）。实例级汇总统计欠缺（ [#18777](https://github.com/go-gitea/gitea/issues/18777)）。[API 文档](https://docs.gitea.com/next/development/api-usage)

### 三档方案

| 档位 | 做法 | 一次性成本 | 持续成本 | 能回答的问题 | 适用阶段 |
|---|---|---|---|---|---|
| L1 手工 | 月度盘点表：从平台 Activity 页抄录贡献者数、MR/合并数、复用项目数、人才流向 | 0（建表 1 小时） | 约 0.5 天/月 | 参与人数与趋势、活跃项目 Top、人才去向 | ≤20 项目，起步首选 |
| L2 半自动 | 平台自带统计 + 用平台 API 写脚本拉数入表/简单看板（GitLab GraphQL、Gitea API） | 1–2 天 | 每月 <2 小时维护 | 同上 + 精确到项目/人的时序对比 | 20–50 项目 |
| L3 自动 | [GrimoireLab](https://github.com/chaoss/grimoirelab)（docker-compose，2C/8G 起，痛点是数据源配置）；[Augur](https://chaoss.community)（部署复杂，正用 Go 重写以降低门槛）；[DevStats](https://github.com/cncf/devstats)（GitHub 归档→Postgres+Grafana，Helm/K8s，偏 GitHub） | 1–2 周 | 需专人不定期维护 | 跨平台全量指标、CHAOSS 标准度量（如贡献者留存） | >50 项目或跨多托管平台、有专人 |

**推荐**：单人兼职从 **L1 起步**——平台自带统计已能回答 D3 所需的"贡献量与人才成长"基本问题，月度粒度足够支撑路线图决策；项目数过 50 或跨多平台再评估 L3，不建议一开始上 GrimoireLab。

## 二、激励选项谱系

| 选项 | 适用前提 | 已知风险 | 适用阶段 |
|---|---|---|---|
| 公开认可（感谢榜、案例分享、newsletter） | 无预算；运营者有产出渠道 | 低 | 全阶段，起步首选 |
| 徽章/游戏化 | 有发放渠道（平台或人工）；华为 "Knights and Gold Stars" 即此路线（[论文](https://www.researchgate.net/publication/365128717_Knights_and_Gold_Stars_A_Tale_of_InnerSource_Incentivization)） | 徽章贬值、为徽章而贡献 | 有一定参与量后 |
| 排行榜 | 数据准确可得 | **Goodhart 风险最大**：commit/PR 数易刷（小提交、拆单）；建议只做团队级、不当考核指标（[GitClear](https://www.gitclear.com/popular_software_engineering_metrics_and_how_they_are_gamed)、[Keypup](https://www.keypup.io/blog/goodharts-law-in-action-why-your-dev-metrics-are-being-gamed-and-how-to-fix-it)） | 谨慎使用 |
| 职级/绩效挂钩 | 中层管理者认可（pattern：[Change the Middle Management Mindset](https://patterns.innersourcecommons.org)、[Contracted Contributor](https://github.com/InnerSourceCommons/InnerSourcePatterns) 解决跨团队借调与考核错位） | 诱发刷量、与本职冲突、度量失真；建议团队级指标+主管定性评价，不直连个人指标与奖金 | 有管理层支持后 |
| 物质奖励 | 有预算；过 IP/合规审批（对外开源需 CLA/法务） | 挤出内在动机、低质量 PR | 少量、事件性使用 |
| 成长机会（外部大会、转岗/轮岗任 Trusted Committer） | 有预算与岗位通道 | 名额稀缺需公平规则 | 中长期，最可持续 |

**结论**：最稳妥组合 = **公开认可 + 成长机会**为主（PayPal/Bosch 等案例主线，见 [Adopting InnerSource](https://innersourcecommons.org/learn/books/adopting-innersource-principles-and-case-studies) 与 [InnerSource Patterns](https://patterns.innersourcecommons.org)），绩效挂钩用"团队级 + 定性"轻量方式，避免个人 commit 类 KPI 直连薪酬。
