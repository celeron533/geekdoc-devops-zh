# 部署软件不应该像看牙医一样

> 原文：<https://octopus.com/blog/deploying-software-shouldnt-feel-like-visiting-the-dentist>

作为项目经理，部署软件的过程充满了焦虑和恐惧。在我的职业生涯中，我可以无数次地想到，在临近发布截止日期的阴影下，不得不部署我们的应用程序的想法类似于考虑即将去看牙医。事实上，即使是让我们的“令人敬畏的新功能”进入用户手中的机制也感觉像拔牙。

诱惑是尽可能少地部署，就像诱惑是尽可能少地去看牙医。你知道你应该更有规律地去，但是你害怕会很痛。你甚至可能会有一个难以忘怀的记忆，那就是上次去牙钻时，你的珍珠白落在了牙钻的接收端。就我个人而言，光是想想就牙疼。

[![](img/cce781c85da17d572ae9c881785c79c0.png)](#)

你可能会发现自己在找借口并推迟去看牙医，而不是定期去看牙医，也许是每六个月一次。结果，你从来没有抽时间去做检查，两年后，当你有了一个大峡谷大小的蛀牙时，你才不得不去做牙科手术。我知道我已经这样做了，充分意识到它可能发生的风险，并随后在它发生时惩罚了自己。具有讽刺意味的是，最终坐在牙医的椅子上的马拉松式的工作导致了难以忘怀的记忆，迫使我从一开始就避免检查。

在软件开发领域，在软件部署之间留出一段较长的时间就像放弃定期的牙齿检查一样危险。部署之间的差距越大，未经客户验证的工作量就越大——代码更改、数据库模式修改、配置变更。部署之间的功能和代码增量越大，新版本就越有可能破坏一些严重的东西，释放出一大群尖锐的错误，这些错误会消耗您的时间，并使您的下一次开发迭代计划支离破碎。

不要担心在两个版本之间你已经建立了一个巨大的变更列表，只要假设你的决定是正确的，你会感觉更好。你可以假设你做了一个很好的决定，关于添加哪些新功能，如何设计用户界面使其“易于使用”，以及当它以淡紫色绘制时，用户是否会更喜欢它。然而，你只能通过把它交给你的用户来证明你得到了正确的东西。版本之间的差距越大，你赌的开发工作越“正确”。当最终发布时，你的用户会通过销售数据、提出的错误、直接反馈甚至社交媒体来告诉你是否做对了。所以，如果你在紫红色上画错了，痛苦才真正开始。

回到牙医的椅子上，两次检查之间的间隔时间越长，你在两次检查之间吃的食物就越多，牙齿上堆积的未被抑制的细菌就越多。你假设你刷牙的方式是正确的，你对使用牙线的沉默没有对你的牙齿卫生造成太大影响。然而，如果你错了，事情就会变得痛苦。

因此，经常部署似乎是明智的，对吗？问题是，这个比喻已经过时了(抱歉)，软件开发团队觉得部署比看牙医还难。部署过程可能是一项巨大的开销，尤其是与拨打电话号码并前往当地牙科诊所相比。有代码审查要进行，测试计划要执行，文档要写，许多环境要更新，管理任务要完成。开发团队害怕消耗他们生命中几天时间的部署过程，并且总是提出困难的问题和强迫不舒服的决定，这是可以原谅的。

实际上，部署应该比去看牙医更简单、更容易、更便宜、更快捷。为了达到这种状态，软件开发团队需要做三件事:

*   自动化他们的部署机制
*   重新评估并简化他们的管理实践和流程
*   明确专注于向用户交付有价值的、增量的功能

一次做所有的事情看起来令人生畏，所以软件开发团队能做的最好的事情就是“现在”就开始把事情做得更好。即使他们目前只能自动化他们部署机制的一小部分，或者删减他们发布文档的一小部分，或者决定不测试应用程序中未被充分利用的区域。随着他们逐渐减少部署开销，他们将越来越多地获得常规用户验证和风险缓解带来的好处，这些好处远远超过了时间和精力成本。此外，一旦您开始经常部署，每个人都会开始专注于消除剩余的开销。

自 2008 年年中以来，我们一直在努力在 Redgate 应用敏捷软件开发方法，但直到我们要求我们的开发团队更频繁地部署，我们仍然花了五年时间。在应对这一挑战的过程中，我们犯了一些错误，发布了一些不应该发布的版本。然而，我们进行了逐步的改进，我们消除或解决了部署过程中的瓶颈，我们添加了允许我们发现问题版本的机制。

值得一提的是，我们所做的最重要的改进是让每个团队都能够按下按钮来部署他们的软件。Redgate 优秀的 DevOps 团队提供了一个定制的自动化部署工具，让我们可以做到这一点。这涉及到 Redgate 方面的大量投资，但这是值得的，因为这意味着我的团队可以随时部署我们的产品。实际上，我们只是受限于我们将工作分成离散的、有价值的块的能力，以及我们的用户对软件更新的容忍度。

软件开发团队应该尽可能频繁地进行部署。每个月。每次冲刺。甚至每天，如果你的用户对此满意的话。缩短部署之间的时间间隔可以减少未经用户验证的未经证实的变更数量，并降低单个版本中有过多尖锐错误占用您时间的风险。此外，这意味着部署将不再像坐在牙医的椅子上一样。

* * *

这是 Redgate 产品交付主管克里斯·史密斯的客座博文。Redgate 通过加速软件交付和帮助遵守数据保护法规的解决方案，帮助您满足业务和 IT 的需求。[了解更多](https://www.red-gate.com/)。