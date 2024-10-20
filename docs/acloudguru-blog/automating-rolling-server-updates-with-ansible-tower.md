# 使用 Ansible Tower 自动进行滚动服务器更新

> 原文：<https://acloudguru.com/blog/engineering/automating-rolling-server-updates-with-ansible-tower>

Ansible Tower 是一个有用的工具，可以显著改善您的工作流程，并且可以根据您公司的流程进行定制。许多不同环境都有一个共同点，那就是需要从负载均衡器中移除 web 服务器，更新其软件，然后将其添加回负载均衡池。在这篇文章中，我将展示如何使用 Ansible 和 Ansible Tower 来实现这一点。

## 什么是 Ansible？什么是安西布尔塔？

Ansible 是一个很好的管理基础设施的工具，它允许你将基础设施定义为代码。从部署环境、管理软件到其他日常维护，您都可以使用 Ansible 来完成。Ansible Tower 将 Ansible 的所有功能整合到一个功能性的 web 界面中。

## 如何使用 Ansible 自动滚动服务器更新

您需要做的第一件事是为您的项目建立一个 git 存储库。我这里有我的:

[https://github . com/Linux academy/content-ex 447-ansi ble-best-practice](https://github.com/linuxacademy/content-ex447-ansible-best-practice)

我们将在这里使用的行动手册在 **blog/manage_LB.yml** 中

在 Ansible Tower 中创建您的项目:

我们将 SCM(源代码管理)类型设置为 Git，给出一个到我们的存储库的链接，并将项目命名为。

现在，我们可以创建作业模板来实际运行行动手册。

对于对服务器进行更改的剧本，我更喜欢将作业类型设置为“Check ”,这样意外的作业运行就不会进行我不期望的更改。选中“启动时提示”框将允许我在需要时更改它。

我们将库存设置为我们的生产库存，选择相关的项目和剧本，并设置我们的凭证。最后，我设置了一个“web”限制，因为我将整个生产库存发送到剧本，但是我只想在 web 服务器上运行这个剧本。

一旦我们在“检查”模式下运行该作业，并看到一切都按预期运行，我们就可以在“运行”模式下重新运行它。这是结果页面的外观:

正如您在这里看到的，从负载均衡器中删除服务器的第一个任务成功完成，运行了更新(大约需要 20 分钟)，然后服务器被添加回负载均衡器。添加/删除的脚本编辑 nginx 配置文件并重新启动服务。这不是最完美的解决方案，但对于这个例子来说是可行的。

如你所见，使用 Tower 来管理任务既有用又简单。使用这种方法，您可以运行各种任务来修改和管理您的环境。如果需要，您甚至可以使用工作流来设置您的任务，以便更好地管理。

![](img/1e9cd30974358a0a1c25da2ed3769dea.png)

在这里，我们同步我们的项目，以确保我们拥有最新的行动手册信息，然后我们尝试从负载均衡器中删除一台服务器，如果它失败，就会发出失败警报。但是，如果成功了，我们就更新 web 服务器上的软件——同样，如果有问题，就会发出失败警报。最后，我们尝试将服务器重新添加到负载均衡器中，如果它不工作，这里只有一个警告，没有其他任务。

想知道更多关于安西布尔塔的事情吗？查看 ACG 的[高级自动化红帽认证专家:Ansible 最佳实践(EX447)考试准备课程](https://acloud.guru/overview/red-hat-ex447-ansible-best-practices)，我们将在其中涵盖这一内容及更多内容！

* * *

## 掌握最受欢迎的技能

无论您是云新手还是经验丰富的专家，云专家都可以让您轻松(而且非常棒)地提升您的云职业生涯。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-june-2021)或[立即开始](https://acloudguru.com/pricing)免费试用。