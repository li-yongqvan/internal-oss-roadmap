# 01 平台选型对比

Type: research
Status: resolved

## Question

内部开源社区应挂在哪个代码托管平台上？以"单人可运营 + 支撑人才协作机制"为准绳，对比三个候选：

1. 自建 GitLab（国内公司常见现状）
2. GitHub / GitHub Enterprise
3. Gitea / Gitee 等轻量自建

对比维度：CODEOWNERS/OWNERS 权限机制、issue/PR 模板、label 工作流（good first issue 流水线）、CI、机器人/自动化可行性、贡献统计（内置 analytics 或插件）、门户/静态页面能力、自建与运维成本、国内访问性。

产出：一张对比表 + 每候选的"上手成本 / 机制覆盖 / 风险"结论 + 给路线图决策点 D1 的推荐默认项（含决策标准与最晚决策时间）。发现写入 `../assets/01-platform-selection.md`。

## Answer

- 推荐默认：优先挂在公司已有 GitLab 实例开 inner-source 组（零新增运维）；无实例则轻量自建 Gitea（2 核 1 GB 起步，半天上线）。GitHub 云因国内访问与合规硬伤不作默认，机制最全但 internal 可见性需 Enterprise（$21/人/月）。
- 关键事实 1：GitLab 免费版缺 CODEOWNERS 强制审批与贡献统计（Contribution Analytics），均为 Premium 功能——"公司已有 GitLab"路径的代价要明确。
- 关键事实 2：Gitea 1.17+ 支持 CODEOWNERS、1.21 起 Actions GA 且兼容 GitHub Actions 语法，核心协作机制覆盖够用，仅缺贡献分析面板与官方 Pages。
- 最晚决策时间：第一个试点仓库创建之前（机制文件与平台绑定，中途迁移成本高）。
- 详细对比表与来源：`../assets/01-platform-selection.md`
