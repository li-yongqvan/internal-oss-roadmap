# 01 平台选型对比（决策点 D1）

准绳：单人兼职运营 + 支撑开源人才协作机制 + 粗糙可用优先。检索时间：2026-10-31。

## 一、对比表

| 维度 | 自建 GitLab（含公司已有实例） | GitHub / GHE | Gitea（自建）/ Gitee（云） |
|---|---|---|---|
| CODEOWNERS | 文件支持，但"代码所有者强制审批"仅 **Premium/Ultimate**（免费版缺失） | 支持，私有仓库需 Pro/Team/Enterprise 档；公共仓库免费 | Gitea 1.17+ 支持，自动指派 reviewer，但强制力有限（[#32602](https://github.com/go-gitea/gitea/issues/32602)） |
| Issue/PR 模板 | 支持免费 | 支持免费（.github/ 模板体系最成熟） | Gitea 支持（.gitea/ 目录）；Gitee 支持 |
| Label 工作流 | 支持；scoped label 为 Premium | 支持免费，生态最佳 | 支持免费 |
| CI | 内置 GitLab CI，免费且强 | Actions，私有仓库按分钟计费（Team 含 3000 min/月） | Gitea Actions 1.21 GA，兼容 GitHub Actions 语法；Gitee Go 为付费企业功能 |
| 机器人/API | API 完整 | API/GitHub Apps 生态最强，人才技能直接迁移 | API 够用，生态较弱 |
| 贡献统计 | Contribution Analytics 仅 Premium；免费版无看板 | Insights（Pulse/贡献者图）免费 | Gitea 内置 Activity 页（基础）；无分析面板 |
| 门户/静态页 | GitLab Pages 免费档可用，自托管可内网访问控制 | GitHub Pages（私有仓库需付费档） | Gitea 无官方 Pages；Gitee Pages 2024-04 起暂停免费服务未恢复（[#I9RGKI](https://gitee.com/oschina/git-osc/issues/I9RGKI)） |
| 自建运维成本 | 重：官方推荐 500 用户内 8 vCPU/16 GB（[安装要求](https://docs.gitlab.com/install/requirements/)），升级/备份/housekeeping 繁多 | GHES 更重：≥4 vCPU/16 GB、3.15 起根盘 400 GB、Actions 需 8 vCPU/64 GB | 极轻：单二进制，2 核 1 GB 起步（[docs.gitea.com](https://docs.gitea.com)） |
| 国内访问性 | 自建内网最佳 | github.com 不稳定，数据出境合规存疑；GHES 自建可内网 | Gitea 自建内网最佳；Gitee 云端国内最快 |

来源：[GitLab Code Owners（Tier: Premium/Ultimate）](https://docs.gitlab.com/user/project/codeowners/)、[GitLab Contribution Analytics](https://docs.gitlab.com/user/group/contribution_analytics/)、[GitHub About code owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)、[GitHub internal 仓库仅 Enterprise](https://github.blog/news-insights/product-news/internal-repositories-are-now-generally-available-for-github-enterprise/)、[GitHub Pricing](https://github.com/pricing)（Team $4/人/月、EC $21/人/月）、[Gitea Code Owners](https://docs.gitea.com/next/usage/repository/code-owners)、[Gitea Actions](https://docs.gitea.com/usage/actions/overview)（1.19 预览、[1.21 GA](https://blog.gitea.com/release-of-1.19.0) 后续版本转正式）、[GHES 系统要求](https://docs.github.com/en/enterprise-server@3.21/admin/installing-your-enterprise-server/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-vmware)。

## 二、每候选结论

**自建 GitLab**
- 上手成本：公司已有实例时≈0（只建 group/项目）；新自建则运维重，不推荐新起。
- 机制覆盖：CI/Pages/模板/label 全齐且免费；缺口是 CODEOWNERS 强制审批与贡献统计看板（Premium）。免费版可用 label + 指定 reviewer + 项目看板替代，统计靠 API 导出。
- 风险：机制为 Premium 缺失后易被"买 Premium"绑架（$29/人/月）；升级维护占兼职运营时间。

**GitHub / GHE**
- 上手成本：机制零搭建（模板/CODEOWNERS/Actions 开箱即用），但国内访问是硬伤。
- 机制覆盖：最全最成熟；inner-source 关键的 internal 可见性需 Enterprise Cloud（$21/人/月）或 GHES。
- 风险：国内访问不稳定影响日常协作；公司代码放境外云过不了多数合规；GHES 自建资源与许可成本高。

**Gitea / Gitee**
- 上手成本：最低（Gitea 单二进制，2 核 1 GB VM 即可，半天上线）。
- 机制覆盖：核心机制基本齐（CODEOWNERS/模板/label/Actions 兼容 GitHub 语法）；缺分析面板与官方 Pages（可用第三方 pages server 或外挂静态托管）；Gitee 云端国内访问最佳但 CI/Pages 受限且收费。
- 风险：Gitea 强制 review 机制弱（多人协作规模大后需补流程）；生态插件少，机器人要自己写；Gitee 私有化部署价格高、平台锁定。

## 三、推荐默认项（供 D1 决策）

**默认：挂在公司已有的 GitLab 实例上开一个 inner-source 顶级组（Group），零新增基础设施。** 若公司无 GitLab，则默认 **Gitea 自建**（2 核 4 GB VM + 1 个 act_runner）。

- 决策标准（按序判断）：① 公司是否已有 GitLab 实例且有闲置容量 → 有即用它；② 代码是否必须留在内网（合规）→ 必须则排除 GitHub 云；③ 是否有上级预算/人数规模（>50 人且需贡献看板）→ 有则评估 GitLab Premium 或 GitHub Enterprise。
- 最晚决策时间：路线图试点期开始前、**第一个试点仓库创建之前**（CODEOWNERS、模板、label 等机制文件与平台绑定，中途迁移成本高）。建议 M1 第 2 周前定稿。
- 迁移兜底：Gitea Actions 与 GitHub Actions 语法兼容、仓库均可标准 git 迁移，未来换平台成本可控。
