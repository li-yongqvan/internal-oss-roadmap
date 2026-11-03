# 02 机制裁剪：单人可运营的最小机制集

Type: research
Status: resolved

## Question

Kubernetes 的六项机制（成员阶梯 + OWNERS、good first issue 流水线、导师计划、轻量提案流程（KEP 裁剪版）、行为准则、贡献度量）如何裁剪成"1 名运营者 + 首批个位数参与者"就能跑起来的 MVP 版本？

对每个机制给出：

- MVP 版本的具体形态（需要哪些文件/流程/人工节奏）
- 运营成本（每周小时数量级）
- 升级触发条件（出现什么信号时值得升级到更重的版本）
- 明确裁掉什么、为什么

参考对象不限于 Kubernetes：Apache、CNCF（LFX Mentorship）、Rust 等社区在早期/小团队阶段的实践也可引用。

产出：机制裁剪表，供路线图 P0/P1 阶段内容与决策点 D2（机制取舍）直接引用。发现写入 `../assets/02-mechanism-tailoring.md`。

## Answer

- 六项机制 MVP 化后总成本约 2-2.5 h/周，个位数参与者阶段一套即可全部保留：成员阶梯压成两级（Owner + Trusted Committer）、gfi 靠人工每周挑 1-2 题、导师=结对 shadow、提案=issue 模板 + 72h lazy consensus、CoC 直接采用 Contributor Covenant、度量用平台自带统计每月记 3 个数。
- 最值得保留的 MVP：lazy consensus 提案流程（Apache 旁证，几乎零成本防决策僵局）、两级 TC 阶梯（InnerSource Trusted Committer 模式）、人工 gfi + 结对 shadow（保留 K8s gfi 定义但去掉全部自动化）。
- 建议直接砍掉：KEP 式正式提案状态机（仅留 4 节 issue 模板，Rust RFC 0002 明文小改动免提案）和任何度量面板/devstats（月度 3 个数 + Praise Participants 表扬足够，与 KPI 硬挂钩前三月禁止）。
- 升级触发信号与三阶段路线速查见资产文件第三节（10-30 人升自动化、>50 人才上 K8s 四级阶梯/SIG）。

发现全文：[../assets/02-mechanism-tailoring.md](../assets/02-mechanism-tailoring.md)
