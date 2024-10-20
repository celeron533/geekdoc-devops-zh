# 线束将持续验证扩展到 Datadog |线束

> 原文：<https://www.harness.io/blog/harness-extends-continuous-verification-datadog>

Harness 帮助客户掌握连续交付(CD ),以便他们能够快速自信地将新应用和服务部署到生产中。

如今，客户在其开发、QA 和生产环境中使用云或基础架构监控软件并不罕见。

早在二月份，我们就宣布了对 [Dynatrace](https://harness.io/2018/02/harness-extends-continuous-verification-dynatrace/) 的支持，以配合我们的 AppDynamics 和 New Relic APM 支持。今天，我们的 Datadog 支持现已正式上市。

## 为什么要 Harness + Datadog？

Harness 帮助客户掌握连续交付(CD ),以便他们能够快速自信地将新应用和服务部署到生产中。

Datadog 帮助客户监控其云应用和基础设施的性能。

对于每个应用程序/服务，客户通常有一个或多个部署管道。典型的管道有几个反映环境的阶段(如开发、质量保证、试运行、生产)，用于在生产部署之前测试/验证代码。

通过将 Harness 与 Datadog 集成，客户现在可以跨部署渠道自动验证云应用和基础设施的性能。

## 简单的部署管道示例

假设我们有一个名为“我的微服务”的 Docker 微服务，我们的持续集成(CI)工具 Jenkins 创建了一个新版本(#101)，为我们带来了一个新的工件版本。

利用 Harness，我们可以获得新版本，并立即触发一个 4 阶段部署管道，如下所示:

Example deployment pipeline

每个管道阶段都将我们的新微服务部署到不同的环境中，运行一些测试，在进入下一阶段之前验证一切正常。

你可以从上面的截图中看到，第 1 到第 3 阶段(开发/质量保证)成功了，变成了绿色。这通常是好的，这意味着工件通过了所有的测试，并且已经为生产和客户做好了准备。

坏消息是，第四阶段:生产变红，我们的管道状态是“失败”。

## 利用线束自动执行部署运行状况检查

在 Harness，我们通过称为[持续验证](https://harness.io/continuous-delivery/continuous-verification/)的东西将 CD 向前推进了一步。

我们的早期客户之一 Build.com 过去常常让 5-6 名团队领导手动分析监控数据和日志文件来验证生产部署。这个过程需要每个团队领导 60 分钟，每周进行 3 次。这相当于团队在验证上花费了 1080 分钟或 18 个小时的时间。借助 Harness，Build.com 将验证时间缩短至仅 15 分钟，并且[使自动回滚能够在生产](https://harness.io/2018/01/how-build-com-automated-ci-cd-rollback/)中发生。

借助 Datadog，Harness 能够在每个环境中即时部署和验证云应用程序部署的性能。一旦部署了新的应用程序或服务构件，Harness 将自动连接到 Datadog，并开始分析应用程序/服务/基础架构性能数据，以了解每个部署的实际业务影响。

Harness 应用无监督的机器学习(隐马尔可夫模型和符号聚合表示)来了解关键服务的性能是否偏离，并相应地标记性能回归。

让我们来看看 Datadog 的验证是什么样子的。

## 使用 Datadog 进行连续验证

以下部署工作流与上述失败的管道相关，特别是生产阶段 4。
你可以看到部署的第一阶段失败了。就部署服务而言，部署是成功的，与 Jenkins 相关的验证和测试也是如此。但是，Datadog 验证失败，这意味着已经发现了新的性能退化。在这种情况下，最终的动作是自动回滚(这是 Harness 提供的安全网)。

单击数据狗失败步骤(红色)向我们展示了验证失败的原因:

我们可以看到，在部署了新的微服务版本之后，一个关键的 web 事务“get_/todolist/inside/load”出现了请求持续时间回归。将鼠标悬停在红点上，我们可以获得更多详细信息–部署后，响应时间实际上增加了 58%，从 840 毫秒增加到 1330 毫秒:

此验证的默认时间段是 15 分钟，但此数字可以自定义。一些部署管道和工作流可能需要几个小时才能完成，因为并非所有事情都是自动化的(手动检查/批准等。).

您还可以通过单击指标过滤器来配置/过滤任何数据狗指标:

## 配置 Datadog 连续验证

使用标准的 Datadog API 构建我们的集成非常简单。

你需要做的第一件事是设置>连接器>‘添加新的验证提供者’:

然后输入您的 Datadog URL、API 密钥和应用密钥:

您可以从 Datadog 集成 API 屏幕获取 API 密钥:

## 将 Datadog 验证添加到部署工作流中

首先，在 Harness 中添加或编辑现有工作流。

只需点击“添加验证”并从菜单中选择数据狗。

接下来，选择您的 Datadog 服务器，输入您想要验证的服务名，选择您想要验证的指标，并输入验证时间段(默认为 15 分钟)。

单击 submit，您的部署工作流现在将使用 Datadog 自动验证应用程序性能。

## Datadog 将带来更多

正如你可能想象的那样，我们可以用 Datadog 做更多的事情。以下是未来几件值得期待的事情:

*   Datadog 用户的线束部署标记
*   支持 Datadog 日志非结构化事件数据(类似于我们的 Splunk、ELK 和 Sumo 逻辑支持)

特别感谢我们的客户和工程团队创造了这种支持。
干杯！

史蒂夫。
@伯顿说