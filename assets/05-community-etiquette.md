# 社区礼仪

> 写给每一位参与者，尤其是第一次参与开源的你。
>
> 我们是一个平级小社区：一位发起人，加上一群同事和朋友。没有管理层、没有绩效，所有协作靠几条公开的默认动作来维系。底线规则见我们的行为准则（采用 [Contributor Covenant 2.1 官方中文版](https://www.contributor-covenant.org/zh-cn/version/2/1/code_of_conduct/)，核心正是"提出和大方接受建设性意见""尊重不同的主张、观点和感受"）。
>
> 文中每条建议都附了出处编号，对应文末「来源清单」；少数是我们自己的约定，会明确标注"（本社区约定）"。

## 一、如何上交 PR

**1. 走标准的 fork → 分支 → PR 流程。**
Fork 仓库并克隆到本地，把原仓库配置为 upstream 并经常同步；为每次修改单独创建一个分支，不要直接改在 main 上，最后向本仓库发起 PR。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**2. 小步提交：一个 PR 只做一件事。**
Google 代码评审指南的原话是"一个变更（CL）的正确大小，就是一件自包含的改动"；大约 100 行通常合理，1000 行通常太大，拿不准就宁可更小。（[\[3\]](https://google.github.io/eng-practices/review/developer/small-cls.html)）Kubernetes 社区指南同样强调："小 commit 和小 PR 评审得更快"。（[\[11\]](https://github.com/kubernetes/community/blob/master/contributors/guide/pull-requests.md)）review 过程中按意见修改时，把修改作为**新 commit 追加**、先不要 squash，方便 reviewer 单独查看新改动。（[\[11\]](https://github.com/kubernetes/community/blob/master/contributors/guide/pull-requests.md)）

**3. PR 描述写清楚。**
第一行用一句话概括做了什么；正文补充背景、为什么这样做，并附上相关信息（issue 号、测试结果等）。（[\[4\]](https://google.github.io/eng-practices/review/developer/cl-descriptions.html)）涉及界面或格式的改动附上截图，提交前自测一遍。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**4. 在 PR 描述里关联 issue。**
写上 "Closes #37" 这样的引用，PR 合并时会自动关闭对应的 issue。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**5. PR 提出去不等于结束。**
reviewer 花了时间看你的代码，被要求修改时请及时响应——"开启 PR 然后一走了之是一种恶习"；不会改就先研究、再求助；实在没时间继续，就告诉维护者，让别人接手。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

## 二、什么先开 issue 讨论，什么直接提 PR

**直接提 PR 即可**：错别字、死链、明显错误之类的小修补，以及已经在 issue 里讨论过、任务明确的改动。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**先开 issue 讨论**：报告自己解决不了的 bug、讨论新特性或方向性想法；较大的贡献动手前先开 issue 问一声。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**（本社区约定）** 影响面大的改动（对外接口、数据结构、跨仓库、依赖变更）先开 issue，按四节模板写清「背景 / 方案 / 影响 / 备选」，等该仓库 Owner 和相关参与者点头后再动手。模板本身是我们自己的约定。

**认领 issue 先说一声**：看到想做的 issue，先评论"我来做"，避免重复劳动；对挂了很久的 issue，动手前先确认它是否还有效。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**72 小时惰性共识（lazy consensus）**：对讨论性提案，Owner 在 issue 里公示后，通常 72 小时无人反对即视为通过、可以动手。机制源自 Apache 社区："公开陈述你的意图，然后等待一段时间（通常 72 小时）让任何人提出反对"。（[\[9\]](https://community.apache.org/committers/lazyConsensus.html)）在本社区由 Owner 在 issue 中发起并计时（本社区约定）。

## 三、礼节 Q&A

**Q1：收到 review 意见怎么回应？**
先读懂对方的要求，别把意见当人身攻击——评审者"是在帮你、帮代码库，而不是在攻击你"，（[\[5\]](https://google.github.io/eng-practices/review/developer/handling-comments.html)）而且评审的规矩是"永远评论代码、不评论开发者"，（[\[6\]](https://google.github.io/eng-practices/review/reviewer/comments.html)）反过来你对意见也该如此。理解了但不同意，就把你的理由、利弊和对方可能不知道的背景摆出来协作讨论；如果对方只是没看懂代码，优先把代码本身改得更清楚，而不是只在评论里解释。（[\[5\]](https://google.github.io/eng-practices/review/developer/handling-comments.html)）

**Q2：如何礼貌地跟进 / 催？**
没人有义务秒回：理想情况下，评审请求应在一个工作日内得到响应，（[\[7\]](https://google.github.io/eng-practices/review/reviewer/speed.html)）但大家都有忙的时候。如果过去一周没人响应，就在原线程心平气和地跟帖、寻求他人帮助，可以 @ 提醒合适的评审者；千万不要私下联系——"开源项目所有的沟通都应该是公开的"。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**Q3：不同意 review 意见怎么办？**
第一，别带着情绪回复（"Never respond in anger to code review comments"）。（[\[5\]](https://google.github.io/eng-practices/review/developer/handling-comments.html)）第二，先自问"我真的理解对方要什么吗"，不理解就追问。（[\[5\]](https://google.github.io/eng-practices/review/developer/handling-comments.html)）第三，把讨论当成协作：说明你的取舍和理由，也要想到你可能知道 reviewer 不知道的背景，反之亦然；首要目标永远是和 reviewer 达成共识。（[\[5\]](https://google.github.io/eng-practices/review/developer/handling-comments.html)）确实谈不拢，交由该仓库 Owner 定夺（本社区约定：每个仓库由其 Owner 负责维护），无论结果如何都尊重最终决定。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**Q4：如何感谢？**
reviewer 花时间帮你，无论意见是否被采纳，回一句"谢谢"；报告 bug、顺手修文档的人同样值得被看见。社区也鼓励把每一位参与者记入贡献者名录（CONTRIBUTORS / AUTHORS 文件），"用于记录每一个参与贡献的人"。（[\[2\]](https://opensource.guide/zh-hans/building-community/)）

**Q5：想放弃 / 中断一个 PR 怎么办？**
生活中总有事，中断很正常，关键是别玩消失：告知维护者你无法再继续，"或许有其他人乐意接手你的工作"。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）同时把 PR 标记为未完成——例如标题加 `[WIP]` 前缀或留言说明，Kubernetes 社区就是用 WIP 前缀标记未完成 PR 的。（[\[11\]](https://github.com/kubernetes/community/blob/master/contributors/guide/pull-requests.md)）拿不准的改动也可以一开始就开草稿（Draft）PR 先征求反馈。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**Q6：如何报 bug？**
一份好报告的目标是"让作者亲眼看到程序失败"。（[\[10\]](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html)）在 issue 里写清：
- **复现步骤**：越短越好，最好给出最小复现——能触发问题的最小命令 / 输入 / 文件；（[\[10\]](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html)）
- **错误信息原文**：一字不差地贴出来，尤其是带数字的部分；"It doesn't work!" 没有任何信息量；（[\[10\]](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html)）
- **期望行为 vs 实际行为**，并区分你观察到的事实和你的猜测；（[\[10\]](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html)）
- **环境信息**：版本号、操作系统等。（[\[10\]](https://www.chiark.greenend.org.uk/~sgtatham/bugs.html)）

发帖前先搜一遍 README、文档和已有 issue，避免重复提问。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

**Q7：新人第一次贡献怎么挑任务？**
从打上 `good first issue` 标签的 issue 里认领一个开始（本社区约定：认领制，在 issue 下评论"我来"即视为认领）。新手向标签的作用早有共识——"仅供入门者"之类的标签"能够帮助新人快速浏览 issues 以及开始"；（[\[2\]](https://opensource.guide/zh-hans/building-community/)）GitHub 上每个仓库的 `/contribute` 页面也会列出适合新手的任务。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）第一件事建议挑小的：文档错别字、小 bug，先完整走一遍 分支 → PR → review 流程，熟悉了再接大活。（[\[1\]](https://opensource.guide/zh-hans/how-to-contribute/)）

## 来源清单

以下 URL 均已逐条访问核实（2026-11-02）。

1. **Open Source Guides（GitHub 官方，简体中文版）：《如何为开源做贡献》** — <https://opensource.guide/zh-hans/how-to-contribute/>
2. **Open Source Guides（GitHub 官方，简体中文版）：《打造受欢迎的社区》** — <https://opensource.guide/zh-hans/building-community/>
3. **Google《代码评审指南》：Small CLs（小步提交）** — <https://google.github.io/eng-practices/review/developer/small-cls.html>
4. **Google《代码评审指南》：Writing Good CL Descriptions（如何写变更描述）** — <https://google.github.io/eng-practices/review/developer/cl-descriptions.html>
5. **Google《代码评审指南》：How to Handle Reviewer Comments（如何回应评审意见）** — <https://google.github.io/eng-practices/review/developer/handling-comments.html>
6. **Google《代码评审指南》：How to Write Code Review Comments（如何写评审评论）** — <https://google.github.io/eng-practices/review/reviewer/comments.html>
7. **Google《代码评审指南》：Speed of Code Reviews（评审速度）** — <https://google.github.io/eng-practices/review/reviewer/speed.html>
8. **Contributor Covenant 2.1（官方中文版，本社区行为准则）** — <https://www.contributor-covenant.org/zh-cn/version/2/1/code_of_conduct/>
9. **Apache 社区文档：Lazy Consensus（惰性共识）** — <https://community.apache.org/committers/lazyConsensus.html>
10. **Simon Tatham, *How to Report Bugs Effectively*（如何有效地报告 Bug）** — <https://www.chiark.greenend.org.uk/~sgtatham/bugs.html>
11. **Kubernetes 社区贡献指南：Pull Requests** — <https://github.com/kubernetes/community/blob/master/contributors/guide/pull-requests.md>

> 注：四节 issue 模板、good first issue 认领制、72 小时计时方式、Owner 定夺机制为本社区约定，已在正文明确标注，未借用任何外部出处。
