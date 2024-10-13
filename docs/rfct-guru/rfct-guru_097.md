# 处理泛化

> 原文：[`refactoringguru.cn/refactoring/techniques/dealing-with-generalization`](https://refactoringguru.cn/refactoring/techniques/dealing-with-generalization)

抽象有自己的一组重构技术，主要与沿类继承层次移动功能、创建新类和接口、以及用委托替代继承和反之相关。

提取字段

**问题：** 两个类有相同的字段。

**解决方案：** 从子类中移除字段并将其移动到超类中。

提取方法

**问题：** 你的子类有执行相似工作的 方法。

**解决方案：** 使方法相同，然后将它们移动到相关的超类中。

提取构造函数主体

**问题：** 你的子类的构造函数中的代码大部分是相同的。

**解决方案：** 创建一个超类构造函数，将子类中相同的代码移动到其中，并在子类构造函数中调用超类构造函数。

推送方法

**问题：** 在超类中实现的行为仅被一个（或少数几个）子类使用吗？

**解决方案：** 将该行为移动到子类中。

推送字段

**问题：** 一个字段仅在少数子类中使用吗？

**解决方案：** 将字段移动到这些子类中。

提取子类

**问题：** 一个类的特性仅在某些情况下使用。

**解决方案：** 创建一个子类并在这些情况下使用它。

提取超类

**问题：** 你有两个类有共同的字段和方法。

**解决方案：** 为它们创建一个共享的超类，并将所有相同的字段和方法移动到其中。

提取接口

**问题：** 多个客户端正在使用类接口的相同部分。另一种情况：两个类中的接口部分相同。

**解决方案：** 将这部分相同的内容移动到自己的接口中。

合并层次结构

**问题：** 你有一个类层次结构，其中子类几乎与其超类相同。

**解决方案：** 合并子类和超类。

形成模板方法

**问题：** 你的子类实现的算法包含相似步骤且顺序相同。

**解决方案：** 将算法结构和相同步骤移到超类中，将不同步骤的实现留在子类中。

用委托替换继承

**问题：** 你有一个子类仅使用超类方法的一部分（或无法继承超类数据）。

**解决方案：** 创建一个字段并放入超类对象，将方法委托给超类对象，并去掉继承。

用继承替换委托

**问题：** 一个类包含许多简单的方法，这些方法委托给另一个类的所有方法。

**解决方案：** 使该类成为一个委托继承者，从而使得委托方法变得不必要。