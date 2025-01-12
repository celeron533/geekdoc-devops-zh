# 组织数据

> 原文：[`refactoringguru.cn/refactoring/techniques/organizing-data`](https://refactoringguru.cn/refactoring/techniques/organizing-data)

这些重构技术有助于数据处理，用丰富的类功能替换原始类型。

另一个重要结果是理顺类之间的关联，使类更加可移植和可重用。

自我封装字段

**问题：** 你直接访问类内部的私有字段。

**解决方案：** 为字段创建一个 getter 和 setter，仅通过它们访问字段。

用对象替换数据值

**问题：** 一个类（或一组类）包含一个数据字段。该字段具有自己的行为和相关数据。

**解决方案：** 创建一个新类，将旧字段及其行为放入该类中，并在原始类中存储该类的对象。

将值更改为引用

**问题：** 所以你有许多相同实例的单一类，需要用一个对象替换它们。

**解决方案：** 将相同的对象转换为单个引用对象。

将引用更改为值

**问题：** 你有一个引用对象，它太小且不常改变，以至于不值得管理其生命周期。

**解决方案：** 将其转换为值对象。

用对象替换数组

**问题：** 你有一个包含各种类型数据的数组。

**解决方案：** 用一个对象替换数组，该对象将为每个元素具有单独的字段。

重复观察数据

**问题：** 域数据是否存储在负责 GUI 的类中？

**解决方案：** 将数据分离到不同的类中，确保领域类与 GUI 之间的连接和同步是个好主意。

将单向关联更改为双向

**问题：** 你有两个类，它们各自需要使用对方的功能，但它们之间的关联仅是单向的。

**解决方案：** 将缺失的关联添加到需要它的类中。

将双向关联更改为单向

**问题：** 你有两个类之间的双向关联，但其中一个类并不使用另一个的功能。

**解决方案：** 删除未使用的关联。

用符号常量替换魔法数字

**问题：** 你的代码使用一个有特定含义的数字。

**解决方案：** 用一个具有可读名称的常量替换这个数字，以解释数字的含义。

封装字段

**问题：** 你有一个公共字段。

**解决方案：** 将字段设为私有并为其创建访问方法。

封装集合

**问题：** 一个类包含一个集合字段，并有简单的 getter 和 setter 用于操作该集合。

**解决方案：** 使 getter 返回的值为只读，并创建用于添加/删除集合元素的方法。

用类替换类型代码

**问题：** 一个类有一个包含类型代码的字段。此类型的值未在操作条件中使用，并且不会影响程序的行为。

**解决方案：** 创建一个新类，使用其对象代替类型代码值。

用子类替换类型代码

**问题：** 你有一个编码类型直接影响程序行为（此字段的值在条件中触发各种代码）。

**解决方案：** 为编码类型的每个值创建子类。然后将相关行为从原始类提取到这些子类中。用多态替换控制流代码。

用状态/策略替换类型代码

**问题：** 你有一个编码类型影响行为，但你无法使用子类来摆脱它。

**解决方案：** 用状态对象替换类型代码。如果需要用类型代码替换字段值，则“插入”另一个状态对象。

用字段替换子类

**问题：** 你有子类仅在其（常量返回）方法上有所不同。

**解决方案：** 用父类中的字段替换方法，并删除子类。
