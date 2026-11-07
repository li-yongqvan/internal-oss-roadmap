# 地图：内部开源社区建设路线图

Labels: wayfinder:map

## Destination

一份《内部开源社区建设路线图》v1 定稿——写给运营者本人（仅 1 人）的执行蓝图：以相对阶段（P0 冷启动 → P1 试点 → P2 扩展）组织，每阶段含目标、机制、细粒度任务分解；未定事项整理成**决策点清单**（每项附推荐方案、选项对比、决策标准、最晚决策时间）；附度量与风险。粗糙可用优先（v0.1 精神），定稿后即可照着执行 P0。

## Notes

- 领域：内部开源（inner-source）社区建设 + 开源人才培养。运营者仅 1 人，中长期项目，当前阶段目标是方向与骨架的粗略成形，不追求完善。
- 语言：路线图及所有产出用中文。
- 参照系：Kubernetes 社区机制调研（2026-10-31 完成）。可裁剪的原材料：成员阶梯（Member→Reviewer→Approver→Owner + OWNERS）、good first issue 流水线、导师体系（GSoC / LFX / 群组队列 / 影子计划）、KEP 提案流程、SIG 组织、CNCF CoC + 执行委员会、devstats 度量。这些是裁剪对象，不是照搬对象——一切以"单人可运营"为准绳。
- 工作方式：grilling 票先调用 Skill("grilling") + Skill("domain-modeling")；research 票调用 Skill("research")；prototype 票调用 Skill("prototype")。
- 本 effort 覆盖 wayfinder 默认的"只规划不执行"：目的地即文档本身，最后一张 prototype 票就是起草路线图。
- 术语：**路线图** = 阶段化执行蓝图；**决策点** = 已识别但留待对应阶段拍板的事项（附推荐/选项/标准/最晚决策时间）；**阶段** = P0/P1/P2 相对阶段，不绑定日历。2026-11-02 讨论新增：**平级自由社区** = 无管理层/无绩效/自发协作的社区形态；**Owner** = 负责某个仓库的人，谁的项目谁维护。
- 追踪器：本地 markdown——地图即本文件，票在 `issues/NN-<slug>.md`（看每张票的 `Type:` / `Status:` / `Blocked by:` 行），研究发现存在 `assets/`。新会话续作入口：按 wayfinder 的 "Work through the map" 模式加载本文件，取前沿票（open 且未被阻塞且未认领的最小号票）执行。**2026-11-03 起本追踪器发布为公开仓库 https://github.com/li-yongqvan/internal-oss-roadmap （本地 `C:\Users\liyongquan\projects\internal-oss-roadmap`），后续更新以仓库为源。**

## Decisions so far

<!-- 一行一票：gist + 链接，详情在票内 -->

- [01 平台选型对比](issues/01-platform-selection.md)：默认挂公司已有 GitLab 开 inner-source 组，无实例则自建 Gitea（2C1G 起步）；GitHub 不作默认（国内访问/合规）；最晚在第一个试点仓库创建前拍板。注意 GitLab 免费版无 CODEOWNERS 强制审批与贡献统计（Premium 功能）。
- [02 机制裁剪：单人可运营的最小机制集](issues/02-mechanism-tailoring.md)：六机制 MVP 化后共约 2–2.5h/周，个位数参与者阶段全套保留；核心组合 = lazy consensus 轻提案 + Owner/Trusted Committer 两级阶梯 + 人工 good first issue + 结对影子导师；砍掉 KEP 式提案状态机与度量面板。
- [03 度量与激励选项](issues/03-metrics-incentives.md)：度量从 L1 手工月度盘点表起步（约 0.5 天/月），GrimoireLab 类留到项目数 >50；激励以公开认可 + 成长机会（大会/转岗 Trusted Committer）为主线，绩效挂钩只做团队级指标 + 主管定性，勿直连个人 commit 数。
- [05 社区礼仪文档](issues/05-community-etiquette.md)：《社区礼仪》成文（[assets/05-community-etiquette.md](assets/05-community-etiquette.md)），11 条来源全部验证；含 Contributor Covenant 官方中文版等六件套引用来源。
- [04 起草路线图并与用户定稿](issues/04-roadmap-draft.md)：**v1 定稿（2026-11-03 用户接受）**——[roadmap-v1.md](roadmap-v1.md)：平级自由社区模式、GitHub 个人账号托管、最简骨架六件套、种子仓库 ai-forum、P0/P1/P2 相对阶段。v0 公司化设计全部推翻。目的地达成，本地图完结。

## Not yet specified

> 无——目的地已于 2026-11-03 达成（v1 定稿），全部雾项在 v1 中成形后清除。后续执行（P0 冷启动）按 [roadmap-v1.md](roadmap-v1.md) 进行，不再开新票。

## Out of scope

- 平台/门户站的实际搭建与部署——路线图只写"何时做、怎么选"，不动手
- 骨架文档正文（CONTRIBUTING、行为准则等）的具体撰写——属路线图 P0/P1 的执行内容
- 面向管理层的立项/汇报文档（用户已确认：本路线图仅供自己执行用）
- Kubernetes 式完整治理的照搬（多 SIG、正式委员会等——明确裁掉）
