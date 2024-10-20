# 发布:带有特征标志的特征发布工作流管线|线束

> 原文：<https://www.harness.io/blog/feature-flags-pipelines>

它在这里！宣布线束特征标志管道-用户现在可以标准化发布特征所需的过程和步骤。

我们很高兴地宣布引入利用功能标志的功能发布工作流，称为管道。功能标志的用户现在可以标准化发布功能所需的流程和步骤，并加入自动化，使功能发布像点击“Go”一样简单

## 特性发布管理是一项繁琐的工作——时间表、批准、监控——天哪！

功能标志解决方案最常见的实现是内部构建的。事实上，大多数时候人们甚至没有意识到他们正在构建一个特性标志解决方案！这很有道理。有许多问题可以用特性标志来解决，工程团队想要解决这些问题。但在他们意识到之前，它已经变成了另一种内部维护和升级工具。

造成这种困难的原因有两个方面:

1.  很难扩展为解决特定问题而构建的解决方案，现在它需要做更多的事情，尤其是当它不是工程师的主要工作时。
2.  该解决方案不可避免地需要集成到发布过程中，包括时间安排、批准和监控。

过程是重要的，尤其是当组织寻求最大化他们已经建立或购买的特征标志解决方案的价值时。即使对于那些已经购买了工具的人来说，他们能够创建一个任何人都可以遵循的标准化发布过程，并保证任何功能发布都经过了适当的步骤，这一点也很重要。让我们不要忘记能够出于合规性的目的审计发布——或者因为出现了问题，需要确定根本原因。

当我们把所有这些东西放在一起看时，很明显所有的需求都是相互关联的。先明确一下需要解决的问题。谁知道呢，也许有一种方法可以一下子解决它们！

*   集成到发布流程中:监控、批准、时间安排等。
*   跨团队、产品、项目等的特性发布的标准化。
*   能够查看审计跟踪以进行合规性和根本原因分析。
*   创建一个任何人都可以使用的通用框架。

你可以想象，能够做到这一点对于任何想要使用特性标志解决方案的人来说都是一个巨大的负担，无论他们是开发人员还是管理人员。如果你能够解决这些问题，你就可以让特性发布变得无足轻重。

或许…你甚至可以自动化它？

## 进入管线:特征发布管理工作流

为了解决这些问题，我们为线束特征标志构建了管道。管道将上面要解决的所有需求和问题放入一个结构中，这个结构比传统的工具、日志、脚本和电子邮件大杂烩更容易理解和使用。

### 为通用发布需求构建工作流

看看下面这个简单的管道。尽管只有三个步骤，但它清楚地概述了您希望发生的事情:打开该功能；获得批准；然后发布给客户的测试版。

如果这是您实际的发布过程，您可以很容易地将这个管道转换成一个可重用的模板。现在，每当你有一个新的功能，你可以只需点击一个按钮，感觉很好，所有的步骤将被照顾。当然，这些也可能变得更加复杂。让我们来看看这可能是什么:

线束中的管道特性标志真正有用的部分原因是集成到您和您的团队可能使用的工具中的深度库。现在我们可以扩展上面的简单用例，其中只需要一个批准。工作流可能包括更新吉拉票证，发送松弛更新，验证日志或健康指标…基本上，你可能需要为了发布一个特性的任何事情。

现在，您已经将所有这些不同的活动整合到一个可管理的工作流中。如果出现问题，您可以轻松地访问审计日志，以查看更改了什么、谁更改了它、什么时候更改的等等。如果您选择使用可视化管道，您还可以使用它来快速检查功能部署的进度或验证是否包含正确的步骤。

### 功能发布的自动化

这不仅仅是通过创建模板化的工作流来消除与特性发布相关的麻烦和头痛。你可能已经了解了管道的本质，那就是它可以自动化。

一旦创建了满足您的工作流需求的管道，您就可以关联任何特性，只需点击众所周知的“Go”按钮。从那里开始，线束管道将负责完成您已经安排好的每个步骤。它可以自动处理推出功能、审批人员、在吉拉进行更改、检查健康指标等等。当然，如果过程中有需要注意的问题或失败，您将会收到警报。这就让你除了照看发布管道之外还要做其他事情，而且你只需要在出错的时候参与进来。

在不久的将来，我们还希望集成自动化健康指标验证，这将更进一步。假设您想向一部分用户推广一个特性，验证事情是否如预期的那样工作，或者正确的业务指标是否在移动，然后逐步向更大部分的用户推广。或者，如果出现问题，您希望采取一些预先指定的补救措施。所有这些事情都将成为可能，这意味着你将真正能够简单地宣布你想要什么，而系统将会负责让它发生。

### 线束平台的附加值

作为一个端到端的软件交付平台，让 Harness 特性标志与软件交付过程的其余部分相互影响是没有多大意义的。我们通常看到特性标志是 CI/CD 的一种放大方法，在许多方面是 CI/CD 管道的第三步。

Harness 实际上是当今市场上唯一一个与 CI/CD 本机集成的功能标志解决方案。这有什么关系？这对产品开发或运营组织有什么价值？为什么高管们也关心这个问题？

让我们从一个我们已经讨论过的话题开始——自动化。线束特征标志中的相同管线特征也可用于线束连续集成和线束连续交付。是的，你得到了一个统一的管道。突然间，您从断开的 CI/CD 和功能标记转变为共享上下文的单一管道，并且可以从构建到向最终用户交付单独的功能实现自动化。你能想象这对你的软件交付过程意味着什么吗？但这不是唯一重要的原因。

分析、治理、合规性、风险——所有这些都是将 CI/CD 和功能标志联系起来的其他真正重要的原因。通过在整个 SDLC 中共享上下文，您可以更好地完成以上所有工作:

*   创建一个规范的分析仪表板来跟踪每个阶段的软件交付度量，以及它们之间的相互作用。
*   对软件交付实施组织范围的治理政策，并确保始终符合治理标准。
*   在软件交付的每个阶段利用审计跟踪来准确地了解发生了什么和在哪里发生了什么，并简化外部和内部审计。
*   在任何阶段消除发布风险，因为您不担心工具间集成或支持以及可能影响业务或客户的关键上下文丢失。

当然，你可以在我们的[博客](https://harness.io/blog/)上详细讨论这些话题。

## 如何开始

如果你已经是一个线束功能标志用户，你可以前往该产品，你会看到一个新的菜单项标签为“管道”，你可以点击并开始建立自己的！

如果你还没有注册使用 Harness 但是想开始使用，你可以很容易地注册一个[免费试用](https://app.harness.io/auth/#/signup/)。快乐发展！