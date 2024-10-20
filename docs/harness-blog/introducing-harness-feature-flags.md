# 引入线束特征标志|线束

> 原文：<https://www.harness.io/blog/introducing-harness-feature-flags>

利用特性标志允许组织以更低的风险更快地交付特性。了解更多信息，并立即试用。

线束特征标志是线束软件交付平台的最新成员。该模块允许组织以更低的风险更快地交付功能。

## 软件交付总是变得更快

公司不断为他们的客户开发新的软件功能。传统上，这些功能是通过软件部署实现的，并且同时对所有用户可见。

因此，每次部署新功能时，都存在由于功能实现不佳而导致客户体验不佳的风险。修复实现不佳的特性的唯一方法是立即回滚到以前的版本，或者尽快创建一个修复程序，并通过部署新版本来前滚。

在这个传统的发布过程中，许多问题变得显而易见:

*   与新特性发布相关的风险最终会拖开发人员的后腿，因为他们必须在发布之前彻底验证设计和实现。
*   通常，一个新特性的外观和功能有多种可能的版本，由开发人员选择一个(不总是正确的)并实现它。
*   何时发布新软件特性的决定是由开发人员而不是企业来控制的。
*   淘汰旧功能会给可能依赖旧代码的新功能带来风险。
*   要么全有，要么全无——一个特性同时向每个人推出，而不是为了验证的目的而逐步推出。
*   当团队受制于工程发布周期(例如，一个月一次)时，多个特性同时发布，引入了复杂性和风险，可能导致部署作战室、大规模回滚和不满意的客户。

简单地说，归结为两件事:

1.  组织需要更快地交付特性，同时最小化风险。
2.  当前的工具和流程不够快，但仍然需要巨额投资。

那么，一个组织如何在不破坏现有流程的情况下实现更高的工程速度，甚至进一步降低部署风险呢？

[*Source*](https://www.prnewswire.com/news-releases/feature-flags-have-gone-mainstream-yet-challenges-remain-reveals-study-from-rollout-and-atlassian-300751151.html)

## 旧工具不能解决新问题

如今，公司主要试图通过重新规划现有的发布流程来解决这些问题。这意味着他们正在使用成熟且复杂的方法来逐步或更快地发布特性。想一想试图用大炮打死一只苍蝇——可以奏效，但很可能是矫枉过正。虽然重新利用现有的工具可以在某些方面进行补偿，但是它最终会非常昂贵，并且可能会错过单个特性版本的特定需求。

大多数公司仍然没有使用功能标志。它仍然不是一个普遍采用的实践，尽管它正在成为一个普遍采用的实践。显然，改变现有工具的用途并不能解决问题。所以团队需要找到新的方法来解决这个问题。快点。

### 关于特征标志成熟之旅的问题

团队面临的主要问题是快速开始并实现价值。团队可能会陷入如何开始的困境，他们可能会以适得其反的方式设计标志，并且他们可能会由于开始时的不成熟而造成未来的问题。

对于功能标志更成熟的团队来说，存在一个“最佳实践”和管理问题。一旦一个团队有几十或几百个标志，这意味着有很多陈旧的代码，没有很多管理它的过程，并且团队经常在操作上努力将它作为健康工作流的一部分来处理。

对于一些最成熟的团队来说，特性标志通常与他们的软件交付过程紧密联系在一起，但是由于现有的供应商都是独立的工具，所以从根本上与 it 脱节。这意味着团队必须投入大量时间将特性标志与度量系统、构建系统等联系起来。因为这些工具不是本地集成的。它还引入了大量的维护开销，以确保所有这些系统随着时间的推移继续协同工作。

很明显，有可行的解决方案，但似乎它们都有自己的问题…

## 驾驭特征标志=速度更快，风险更低

利用功能标志作为一个内部项目开始，将功能标志用于我们自己的软件。从该项目中吸取的经验教训被应用于构建面向客户的线束特征标志——每个人都可以从我们的成功和失败中受益。

The Harness Feature Flags UI - designed for simplicity and speed.

具体而言，线束特征标志侧重于以下关键概念:

*   **开发人员体验** -非常重视开发人员体验，以确保设置过程快速而直观，团队能够立即开始并从功能标志中看到价值。
*   **管理&治理**——让团队建立规则和流程，并自动清理和标记生命周期管理。确保团队能够尽可能地保持他们的系统安全、合规和标准化对他们的目标至关重要。
*   **2+2 = 5**——利用 Harness 平台，使构建工作流变得容易，否则这些工作流很难手工构建。虽然用户不需要使用其他线束产品，但他们创造了一个大于零件总和的整体。

## 线束特征标志的独特之处是什么？

虽然市场上有各种强大的功能标志解决方案，包括内部构建，但它们往往会忽略客户的一些关键需求。利用功能标志满足客户在以下领域的需求:

*   **简单的基于用户界面的功能发布工作流程** -客户能够创建模板和流程，他们可以跨具有相同运营需求的功能标志标准化这些模板和流程。功能标志现在包含在一个可视化管道中，该管道包括与治理和验证相关的步骤。
*   **治理&验证**——客户可以确保生产推动总是符合定义的组织标准，并且他们可以最小化生产中任何问题的负面影响。Harness 使客户能够在他们的功能发布过程中创建控制，包括强制批准和创建审计跟踪。此外，一旦某项功能上线，客户可以自动进行服务验证，确保在出现问题时关闭该功能，以最大限度地减少影响。
*   **集成到 CI/CD 中**——许多特性标志工具将特性标志从软件开发生命周期的其余部分中分离出来。这给客户带来了一个问题，他们固有地将特性标志视为生命周期的另一个阶段(许多公司甚至重新规划他们现有的软件发布过程来模仿特性标志的功能)。通过将特性标志表示为管道，特性标志管理成为开发团队日常工作流程中的一个自然步骤，并作为一个统一的管道集成到 CI/CD 中。

Create visual feature release pipelines.

## 如何开始

要开始使用装具特征标志，只需[注册](https://harness.io/platform/feature-flags/)进行演示，装具专家会让你上手。

更好的是，您将很快能够以完全自助的方式开始利用特性标志。几周后再来查看更多开发者的好消息！

你也可以看看这个[视频](https://harness-1.wistia.com/medias/h6iegycy0a)，它展示了 Harness 特性标志是如何专门为开发人员设计的。