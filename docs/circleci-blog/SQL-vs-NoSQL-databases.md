# SQL 与 NoSQL 数据库| CircleCI

> 原文：<https://circleci.com/blog/SQL-vs-NoSQL-databases/>

应用程序开发人员可以在两大类数据库之间进行选择:SQL(结构化查询语言)和 NoSQL(不仅仅是 SQL)。SQL 数据库，也称为关系数据库，已经使用了 40 多年。尽管年代久远，SQL 数据库仍然非常受开发人员的欢迎。2021 年 9 月，在 DB-Engines 最受欢迎的数据库管理系统列表的前 10 个结果中，有 6 个是关系型的，或基于 SQL 的。

NoSQL 数据库，或者非关系数据库，在过去十年中已经获得了普及和广泛采用。使用最广泛的 NoSQL 数据库之一 MongoDB 在 DB-Engines 的列表中排名第五，并且是前十名中四个非关系数据库中排名最高的。

那么，SQL 和 NoSQL 之间有什么区别，您的下一个应用程序应该使用哪个数据库呢？在本文中，我们将探讨每种方法的优缺点。

## SQL 数据库

SQL 语言是美国国家标准协会(ANSI)标准，有一些方言，如 PL/SQL(在 Oracle 中)和 T-SQL(在 Microsoft SQL Server 中)。编写 ANSI 兼容的 SQL 的优点是，您可以轻松地将脚本转移到另一个 SQL 数据库。

流行的 SQL 数据库包括 Oracle、MySQL、Microsoft SQL Server 和 PostgreSQL。下面，我们将看看使 SQL 成为开发人员普遍选择的一些特性。

### SQL 是关系型的

一个常见的误解是，SQL 数据库被认为是关系数据库，因为您可以使用外键来定义数据库中记录之间的关系。事实上，这个名字是基于关系的数学概念，指的是唯一的[元组](https://en.wikipedia.org/wiki/Tuple)的集合。元组只是值的有序集合。

在 SQL 数据库中，关系被表示为表，关系中的每个元组构成表中的一行(通常称为记录)。它就像一个大型的、正式的 Excel 电子表格，供软件使用。我们把表和行的定义称为模式。

在关系数据库中，您可以(并且通常应该)通过不冗余地存储数据来规范化数据。在过去，存储非常昂贵，规范化数据可以节省存储。

### SQL 是健壮的

拥有一个模式有利也有弊。一方面，您总是知道应用程序期望的实体和值。另一方面，它不擅长处理动态数据。

拥有模式意味着您可以验证您的数据。例如，ID 字段必须是唯一的，并且不能为空。还可以强制外键关系，这意味着一条记录不能引用数据库中不存在的另一条记录。

拥有一个规范化的数据库和这些验证使您的数据变得可靠。有了其他 SQL 特权，比如[事务](https://en.wikipedia.org/wiki/Database_transaction)，SQL 数据库通常是快速、可靠和健壮的。

## NoSQL 数据库

关于 NoSQL 数据库的一个常见误解是“否”意味着数据库中不使用任何 SQL。如前所述,“不”代表“不仅”你可以在 NoSQL 的数据库中找到一些 SQL。

另一个混乱的来源是 NoSQL 数据库没有单一的定义。事实上，NoSQL 数据库有四大类:

*   文档存储
*   图形数据库
*   键值存储
*   宽列数据存储

一些数据库，比如 Cosmos DB，跨越不同的类别，但是 NoSQL 数据库很少可以互换，而且看起来完全不一样。它们的一个共同点是牺牲一些健壮性来获得速度和可伸缩性。

### 文档存储

最流行的 NoSQL 数据库类型是文档存储。文档存储看起来最像传统的 SQL 数据库，只是没有模式和规范化。不是列和行，你只是有一个你放进去的东西的集合。

向实体添加新字段很容易，但这意味着一些实体定义了这个字段，而另一些实体没有。您可以使用不同的值多次存储同一个实体。你也很容易把事情弄得一团糟！

然而，这些数据库在具有高度动态数据的环境中发展良好，并且比 SQL 数据库具有更好的伸缩性。文档存储通常可以在多台服务器上运行，而 SQL 数据库通常绑定到一台服务器上。由于文档存储没有所有这些烦人的字段验证，它们的速度非常快！

流行的文档存储包括 MongoDB、DynamoDB、Couchbase、Firebase 和 Cosmos DB。

### 图形数据库

图形数据库是 NoSQL 数据库的一种特殊类型，非常专业。

这种类型的数据库最常见的用例是“你可能认识的人”的例子。想象一下一些社交网站，比如脸书或 LinkedIn，向你展示你朋友认识的人。

在图数据库中，所有这些人都表示为节点，他们之间的关系表示为边。要找到你朋友的所有朋友，你可以从一个节点开始，简单地“走”边。你会先走到你朋友的边上，然后走到他们朋友的边上。假设你有 200 或 300 个朋友，每个朋友自己也有 200 到 300 个朋友(有一些重叠)，你最终会找到 20，000 到 60，000 个节点。您可以通过简单地检查这些节点的所有边来深入了解。

有了足够大的数据集，一个图形数据库只需几秒钟就可以获取所有这些朋友的朋友。SQL 数据库很快就会陷入这样的困境。它需要匹配数百万用户，每个用户都有数百万用户，所有用户都有自己的数百万用户，最终过滤数十亿(双倍)用户。

如果你需要一个图形数据库，一些流行的有 Neo4j，ArangoDB，和 Cosmos DB。

### 键值存储

可能最简单的 NoSQL 数据库是键值存储。顾名思义，键值存储保存键值对的集合。该值可以是任何值，从数值到带有子对象的复杂对象。

它的应用并不广泛，但是键值存储非常适合缓存或存储会话数据这样的用例。

Redis、Memcached 和 Cosmos DB 是流行的键值存储。

### 宽列数据存储

宽列数据存储看起来有点像键值存储。但是，键拥有对列的访问，而不是单一的值。

一个值可以由数十亿列组成，并且可以是动态的。想象一个键值存储中的无模式 SQL 数据库或文档数据库。

宽列数据存储是可扩展的，可以容纳高达 Pb 的数据。它们的用例各不相同，例如时间序列数据(如多个服务器的 CPU 使用情况)、金融数据营销、物联网(IoT)数据和图形数据。

这种类型的流行数据库包括 Cassandra、HBase、Bigtable 和 Cosmos DB。

### 其他 NoSQL 数据库

NoSQL 包括其他类型的数据库，如以平面文本文件为中心的数据库。另外，请记住，我们可以将 SQL 出现之前的所有东西归类为 NoSQL。我们将要提到的一种特殊类型的数据库是搜索引擎。

搜索引擎是专门寻找数据内容的 NoSQL 数据库。它们通常支持复杂的搜索查询、全文搜索、结果排序和分组以及分布式搜索，以实现高可伸缩性。Elasticsearch、Solr 和 Splunk 是流行的搜索引擎。

你可能已经注意到了，运行在 Azure 上的云数据库 Cosmos DB 是一个几乎可以做任何事情的数据库。有各种多模型数据库，或者可以以多种方式存储数据的数据库，就像这样。亚马逊有自己的 DynamoDB，这是一个运行在 AWS 中的多模型数据库。

多模型数据库有一些限制。例如，您不能在一个数据库中使用不同的方法，但是您可以创建多个实例并在每个实例上使用不同的方法。

## NewSQL 数据库

有时候，NoSQL 是你唯一的选择。然而，SQL 数据库已经赶上来了，现在在仍然是 SQL 的同时提供了一些 NoSQL 的额外好处。例如，Oracle 和 SQL Server 等数据库使您能够存储动态 JSON，甚至可以使用索引和过滤对这些值的查询。

一些数据库更进一步。例如，雪花是一个托管在云中的分散式 SQL 数据库。它解决了 SQL 不可伸缩的挑战，同时仍然完全保留 SQL。这些类型的数据库通常被称为 NewSQL。

为了让你了解 NewSQL 数据库有多受欢迎，Snowflake 在 2020 年 9 月至 2021 年 9 月的数据库引擎排名中上升了 107 位，攀升至第 21 位(领先 Cosmos DB 5 位)！

其他流行的 NewSQL 数据库包括 CockroachDB 和 Spark SQL。

## SQL vs NoSQL:如何选择

有这么多数据库，可能很难选择一个适合你的。你会经常听到，“为正确的工作选择正确的工具。”然而，合适的工具可能只是您的团队已经知道的工具。一个最佳但不熟悉的数据库可能会对您的项目产生负面影响，而一个次优但熟悉的工具可能足以完成这项工作。

如果您决定使用一个新的数据库，无论是 SQL、NoSQL 还是 NewSQL，都要确保您的团队得到正确实现它所需的培训和指导。

对于大多数项目来说，SQL 通常是一个不错的选择，也是一个非常强大的全能工具。然而，对于更专业的工作，NoSQL 数据库可能是更好的选择。例如，Redis 已经成为缓存的流行选择。如果您正在寻找一个快速和可伸缩的数据库，并且不介意牺牲一些健壮性，MongoDB 可能正是您所需要的。

避免仅仅为了新奇而追求最新最好的。程序员可能喜欢新技术的想法，但今天热门的东西可能五年后就不再流行了。为停产的产品寻找人员或支持是一项挑战，在项目中期更换数据库通常成本高昂。

最终，对于下一个项目应该使用什么数据库的答案是:视情况而定。幸运的是，对于现代架构，如微服务，在 SQL 和 NoSQL 之间的选择不是非此即彼的。它们可以在同一个应用程序环境中并存。

## 结论

SQL 和 NoSQL 都在现代软件开发中占有一席之地。他们各有各的长处和短处。NoSQL 数据库可以包含 SQL 元素，而 SQL 数据库可以通过新功能和成熟的 NewSQL 数据库提供 NoSQL 的一些好处。

在选择数据库时，考虑您的需求以及什么对您的团队最有意义，无论是 SQL 还是 NoSQL。