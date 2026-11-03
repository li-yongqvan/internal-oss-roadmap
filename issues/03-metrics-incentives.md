# 03 度量与激励选项

Type: research
Status: resolved

## Question

为路线图的两个决策点准备事实基础：

1. **度量（→ D3）**：单人运营下，如何以最低成本度量"贡献量"与"人才成长"？调研：GitLab/GitHub/Gitea 自带统计能力、CHAOSS/GrimoireLab/DevStats 类开源方案、纯手工方案（月度盘点表）。给出"手工 → 半自动 → 自动"三档方案（各档成本与能回答的问题）。
2. **激励（→ D4）**：内部开源参与的激励选项谱系：公开认可/徽章/排行榜、内部职级或绩效挂钩、物质奖励、成长机会（外部大会、转岗）。各自的适用前提与风险（如绩效挂钩可能诱发刷量、与本职冲突）。

产出：度量三档方案 + 激励选项表，供路线图决策点 D3/D4 引用。发现写入 `../assets/03-metrics-incentives.md`。

## Answer

- **度量**：GitLab（贡献分析/贡献者分析/价值流）、GitHub（Insights）、Gitea（Activity 页 + API）自带统计已够回答"谁在贡献、活跃趋势、人才去向"。单人兼职从 L1 手工月度盘点表起步（约 0.5 天/月，≤20 项目）；20–50 项目升 L2（平台 API 脚本半自动）；>50 项目或跨多平台才考虑 L3（GrimoireLab 2C/8G 起、Augur 部署复杂、DevStats 偏 GitHub/K8s）。
- **激励**：六档谱系 = 公开认可 / 徽章游戏化（华为 "Knights and Gold Stars" 案例）/ 排行榜 / 绩效挂钩 / 物质奖励 / 成长机会。最稳妥起步 = 公开认可 + 成长机会；绩效挂钩需管理层认可（pattern: Contracted Contributor、Change the Middle Management Mindset）且用团队级+定性方式；排行榜 Goodhart 刷量风险最大，勿做个人 commit 类 KPI。
- 详细表格与来源：`../assets/03-metrics-incentives.md`
