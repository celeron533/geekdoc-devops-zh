# 指标很重要:代码级数据管理服务可靠性管理收集的 4 种类型|管理

> 原文：<https://www.harness.io/blog/4-types-code-level-data-collected>

随着越来越复杂的系统和对数字客户体验不断增长的期望，传统的工具和它们提供的肤浅的数据是不够的。为了充分了解应用程序内部的情况并保持稳定性，必须在代码级别收集这些数据。

如果不是*正确的*数据，世界上所有的数据都毫无意义。但是当涉及到交付可靠的软件和解决问题时，什么样的*才是*正确的数据呢？

为了回答这个问题，我们创建了一个框架，帮助组织找出阻碍他们可靠性之旅的数据和指标中的关键差距。该框架的基础是连续可靠性(CR)的概念，即通过在 SDLC 中采取连续、主动的可靠性方法来平衡速度、复杂性和质量的概念。说到 CR，不仅仅是你能捕捉到什么数据，而是你如何分析和利用它。

随着越来越复杂的系统和对数字客户体验不断增长的期望，传统的工具和它们提供的肤浅的数据是不够的。为了充分了解应用程序内部的情况并保持稳定性，必须在代码级别收集这些数据。

使 Harness service Reliability Management(SRM)成为强大的可靠性工具的原因之一是我们在软件交付生命周期中捕获、分析和呈现代码级数据的方式。在本帖中，我们将分解 SRM 捕获的四种关键类型的数据，以及为什么它们对于推进您的持续可靠性之旅至关重要。

## ‍
1。代码度量

捕获代码中发生的事件的所有信息对于理解需要解决的问题至关重要。在您能够有效地确定关键代码级问题的优先级并修复它们之前，您首先需要准确地了解哪些问题正在发生。

在最基本的层面上，SRM 会自动捕获测试和生产中应用程序内发生的所有事件，甚至是日志记录框架或 APM 工具遗漏的事件。这包括:

*   记录的错误和警告
*   未捕获和已吞咽的异常
*   减速和 APM 瓶颈

有了 SRM，您不再需要依赖日志和对捕获哪些事件、在日志语句中包含什么或如何分析它的预见。

除了检测每个事件之外，SRM 还应用了一个智能层来根据严重性自动确定所有事件的优先级。这样，您的团队可以专注于最重要的问题。

考虑到错误是否是新的、第一次和最后一次出现的时间、出现的次数以及是否突然增加等因素，SRM 能够根据标准将错误标记为严重，例如新的或增加的错误是否未被捕获，或者其数量和速率是否超过特定阈值。它考虑已建立的基线和平均值来查明异常，并立即通知开发运维团队和 SRE 团队需要立即解决的事件。

## 2.真正的根本原因

许多 APM 供应商会告诉你，他们提供了问题的根本原因，包括“代码级”的见解。它们实际上的意思是为你提供一个堆栈跟踪。堆栈跟踪虽然有用，但只能帮助识别发生问题的代码层。从那以后，您就只能靠自己的设备了，包括花时间手动挖掘浅层日志文件，以找到可以帮助您重现问题的上下文。

服务可靠性管理可帮助您超越堆栈跟踪，捕捉深层数据，直至最低级别的细节，而无需依赖开发人员或运营远见。这包括:

*   直接从 JVM 捕获的事件发生时执行的源代码
*   令人不快的代码行
*   与事故相关的关键数据和变量
*   调试和跟踪日志语句
*   环境和容器变量
*   能够将事件映射到特定的应用程序、版本、服务等。

## 3.交易和绩效指标

在软件开发和可靠性的上下文中，事务是作为一个单元处理的一系列调用，通常基于面向用户的功能。当交易失败时，客户体验通常会受到影响，因此能够在其影响的交易环境中识别这些失败并确定其优先级非常重要。

SRM 捕获有关每个事务失败的数据，包括发生的次数、失败的事务数量以及事务的响应时间。使用我们上面提到的代码事件的洞察力，我们可以通过关联给定时间范围内的错误、异常和变慢来确定事务的成功，并将这些数据呈现给我们的用户。

这些性能指标包括吞吐量或给定时间段内发生的事务数量，以及响应时间基线。捕获有关应用程序性能的数据的能力对于了解您的最终用户正在经历的事情以及关联相关事件至关重要，这可能有助于确定根本原因。

## 4.系统度量

SRM 关注应用程序代码级的数据，但是我们认识到将代码级故障与系统的其他方面联系起来的重要性。例如，您最近的部署对 CPU/内存利用率有什么影响？是否有任何与此故障相关的阻塞线程？这个 CPU 峰值是由应用程序引起的吗？

通过 SRM 可靠性控制面板，您可以将事件、事务和性能指标与垃圾收集、线程、CPU、类加载和内存消耗等相关联，从而更全面地了解与您的应用间接相关的依赖关系。

## 我们怎么做呢？

是什么让 SRM 能够捕捉到其他监控工具无法捕捉到的深度和广度的数据？我们独特能力的秘密是几个关键因素的组合:

*   **代码映射&运行时代码分析**–在服务器启动期间加载代码时，SRM 会对其进行映射，并为每条代码指令分配唯一的指纹。然后在运行时，生成的代码图用于高效、安全地访问内存和捕获应用程序状态。

*   **软件数据优化**–我们的代理在 JVM /之间运行。NET CLR 和处理器从实时微服务中捕获实时代码和可变状态，并生成优化的软件数据，以最小的性能开销提供 10 倍的粒度和上下文。

*   **高级机器学习**–SRM 通过机器学习算法来运行这些高保真数据，以进行重复数据删除、分类和异常检测，并提供基于代码运行时行为的代码质量报告。

要了解 SRM 如何帮助您获取更深入的数据，请联系我们的工程师。

## 结论

数据和分析的有力结合是企业规模可观察性和可靠性的关键。SRM 不仅可以帮助您的团队全面了解您的代码是如何执行的，以及发生的错误和速度变慢，还可以分析这些数据并增加其意义，以便您准确地知道哪些问题应该优先处理。