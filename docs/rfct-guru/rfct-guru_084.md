# 添加参数

> 原文：[`refactoringguru.cn/add-parameter`](https://refactoringguru.cn/add-parameter)

### 问题

方法没有足够的数据来执行某些操作。

### 解决方案

创建一个新参数以传递必要的数据。

之前！添加参数 - 之前之后！添加参数 - 之后

### 为什么重构

您需要对方法进行更改，而这些更改需要添加以前未提供给该方法的信息或数据。

### 好处

+   在这里的选择是添加一个新参数还是添加一个包含方法所需数据的新私有字段。当您需要一些偶尔或频繁变化的数据，而不必一直将其保留在对象中时，使用参数更为合适。在这种情况下，重构会带来收益。否则，添加一个私有字段，并在调用方法之前用必要的数据填充它。

### 缺点

+   添加一个新参数总是比删除它容易，这就是为什么参数列表经常膨胀到离谱的大小。这种现象被称为长参数列表。

+   如果您需要添加一个新参数，这有时意味着您的类不包含必要的数据，或者现有参数不包含必要的相关数据。在这两种情况下，最佳解决方案是考虑将数据移动到主类或其他可以在方法内部访问的类中。

### 如何重构

1.  查看该方法是否在超类或子类中定义。如果该方法存在于它们中，您需要在这些类中重复所有步骤。

1.  接下来的步骤对保持程序在重构过程中的功能至关重要。通过复制旧方法创建一个新方法，并为其添加必要的参数。用对新方法的调用替换旧方法的代码。您可以将任何值插入到新参数中（例如，对于对象使用`null`，对于数字使用零）。

1.  查找所有对旧方法的引用，并将其替换为对新方法的引用。

1.  删除旧方法。如果旧方法是公共接口的一部分，则无法删除。在这种情况下，将旧方法标记为已弃用。

</images/refactoring/banners/tired-of-reading-banner-1x.mp4?id=7fa8f9682afda143c2a491c6ab1c1e56>

</images/refactoring/banners/tired-of-reading-banner.png?id=1721d160ff9c84cbf8912f5d282e2bb4>

您的浏览器不支持 HTML 视频。

### 厌倦阅读了吗？

不奇怪，阅读我们这里的所有文本需要 7 小时。

试试我们的交互式重构课程。它提供了一种不那么乏味的学习新知识的方法。

*让我们看看…*
