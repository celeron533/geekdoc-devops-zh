# 将特征标志从自主开发迁移到线束特征标志|线束

> 原文：<https://www.harness.io/blog/migrating-feature-flags>

我们推出了一个新产品-马具特征标志-这总是艰难的，令人兴奋的。最重要的是，Harness——就像外面的许多公司一样——已经有了我们内部日常使用的功能标志，通过一个经过多年发展的自制系统。

在 Harness，我们最近做了一件相当困难的事情。实际上，我们做了两件困难的事情，第二个挑战加剧了第一个挑战。

我们推出了一个新产品-马具特征标志-这总是艰难的，令人兴奋的。最重要的是，Harness——就像外面的许多公司一样——已经有了我们内部日常使用的功能标志，通过一个经过多年发展的自制系统。

在推出我们自己的商业功能标志解决方案时，我们还致力于将整个公司从现有的内部系统迁移到我们新的功能标志产品上。替换基础设施(在某个成熟度点上，功能标志实际上是什么)从来都不是一件容易的事，但是当您有各种各样的利益相关者——从设计和支持到 PM——接受过使用现有解决方案的培训时，这就特别困难了。然而，我们设法做到了。

那么，让我们谈一谈我们为什么这样做，以及我们学到了什么。

## 迁移特性标志:为什么我们必须这样做

首先，我们为什么迁移？答案的一半是显而易见的:喝我们自己的香槟。内部使用是产品学习的催化剂，虽然你总是需要小心不要假设你代表你的客户是相同的，让 Harness 使用 Harness(就像我们一直为 CD 做的那样，现在是 CI)意味着我们有一个持续的、容易访问的真实世界使用和反馈流。

每个公司都希望在这方面做得很好，但在现实中，许多公司从来没有兴趣去做艰苦的工作来替换正在使用他们自己的新解决方案的系统。我知道有很多 DevOps 公司仍然在使用他们竞争对手的工具，因为他们无法中断工作足够长的时间来实现他们的狗食愿望。不管是好是坏，我都不会驾驭它！

不过，这只是狗食的一面。迁移还有另一个非常真实的原因，实际上是在价值和工程方面。内部解决方案(正如我在我的“[我应该构建还是购买](https://harness.io/blog/feature-flags/build-or-buy-feature-flags/)”部分中所讨论的)非常昂贵，并且对您通过特性标志获得的价值设置了非常低的上限。具体来说，我们的系统在这里有一些限制:

*   只有布尔标志。我们从未为更复杂的标志配置构建功能
*   有限的自定义规则引擎
*   有限的技术启动支持，在我们添加新服务和产品时停止工作
*   难以正确保护(我们真的想为我们的内部工具构建粒度 RBAC 吗？)
*   可怜的 UX，人们需要非常具体的使用说明

所有这一切的结果是，当我们使用功能标志时，这比不使用要好，甚至以一种非常成熟的方式，因为我们整个组织的人都在使用它们，我们也因为系统的困难和限制而损失了大量时间。我们可能是一个相当高级的用例，我们仍然在努力使它从任何角度都高效。

通过引入合适的产品(尽管是我们自己的)，我们能够立即解决所有这些挑战，同时还消除了全球维护系统所需的工程负担。

## 解决方案与内部比较

在 Harness 功能标志取代它之前，我们有一个快速的内部系统，与我们现在的商业解决方案进行比较。

## 我们在迁移功能标志时面临的挑战

好消息是从我们的内部系统中迁移特性标志非常容易。大概花了一个小时，没有挑战。

如果这是真的，那不是很好吗？功能标志嵌入到我们的一些核心流程中——它们是支持工作方式的一部分，是项目管理工作方式的一部分，等等。你不可能不打嗝就做出那样的改变。

我们可以在另一篇文章中讨论我们如何迁移的技术部分，但在这里我将更多地关注过程和人员方面。我们遇到了什么样的挑战？

*   当我们将所有现有的标志导入到线束特征标志中时，它们…有点难以理解。以前，我们没有命名和描述，所以我们最后得到的是一个标志仪表板，除非你知道你在找什么，否则你永远也弄不明白。

*   在这一变化之前，我们没有花足够的时间来沟通或培训员工。一般来说，一个好的经验法则可能是，无论你花了多少时间与人交流和培训，增加更多的时间，因为这是不够的。我们看到我们的支持团队和其他团队的一些工程师有他们需要完成的重要事情，但他们突然不知道如何去做。这是可以预防的，我们可以从中吸取教训，为以后的改变做准备。

*   我们实际上可能做这个改变太晚了，但是有一些小的 UX 改进将为我们使用产品的团队带来很大的不同，如果我们在时间表上更积极一些，我们甚至可以更早发现。类似于上面关于授权的规则，当你考虑何时开始测试你自己的工具的时间表时，在几乎所有情况下都要加快时间表。

*   我们本可以让支持和升级途径更加清晰。如果现有解决方案有问题，请联系运营团队。但是，如果您对新的商业解决方案有疑问或问题，您会怎么做？你会像顾客一样开罚单吗？到达首相？首席工程师平？这个我们说的不够清楚，也造成了一些不必要的来回。

因此，我们确实遇到了一些挑战——我们不怕在这里分享——但我们能够从中吸取教训，并因此在内部进行产品和流程改进。这就是喝自己的香槟的意义所在！

## 结果还很早

因为我们刚刚进行了这一更改，所以我们将避免谈论迁移功能标志的惊人影响——我们希望给它一些时间，以便我们可以在几个月后看到影响时回头分享更多知识。但是，到目前为止，反应是有希望的，我们已经解放了我们的运营团队，将时间花在更好的问题上。

## 结论

Harness 做了两件在任何情况下都很棘手的事情:推出新产品，替换现有工具。我们一个接一个地做，同时让一个大客户(我们自己)向我们学习。

我可能不需要鼓励公司想这么做。以我的经验来看，养狗的困难从来不在于渴望，而在于致力于完成它的能力。但是，这是绝对值得的——你可能需要你的领导力来打下基础，但这种变化的另一面是对一个充满活力的组织的宝贵学习，它能够更快地行动，更有效地共同建设。

有兴趣了解更多关于特性标志的信息吗？[立即预订您的演示](https://harness.io/platform/feature-flags/)。