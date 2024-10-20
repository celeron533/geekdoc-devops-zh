# 拉式请求驱动开发|利用

> 原文：<https://www.harness.io/blog/pull-request-driven-development>

在本文中，Brett 向我们介绍了拉式请求驱动开发。

像许多公司一样，Harness 从一组最小的部署环境开始。当我们发布第一个生产应用程序时，我们有三个——持续集成环境、质量保证和生产本身。

开发人员所做的每一项更改都会立即部署到我们的 CI 环境中，这对于快速查看作为实际应用程序部署的最新代码非常有用。然而，当它到达那里时，变更已经被合并到主分支中，所以在合并之前对测试没有帮助。

为了解决这个问题，我们开始从开发人员的功能分支产生可部署的构建。这些可以部署到我们的 QA 环境中，并在合并之前进行测试。这在一段时间内有效，但是一些更改改变了数据模式，当它们从 QA 回滚时，数据也必须被修复，因为我们的 QA 数据是专门为生产部署之前的测试而填充的。

另一个限制是，由于 QA 被用作生产的途径，它并不是一直可用的。因此，我们引入了另一个专门用于部署特性分支构建的开发环境。现在，我们的 QA 数据只被合并到 master 中的变更所改变，并且正在走向生产。我们的开发环境可以部署任何功能构建，如果数据损坏，我们可以重置它。

问题解决了！*除了……*

有些变化需要长时间的实践测试。前端和后端工程师可能需要在一个环境中协作，每个人都在各自的分支机构工作，新功能可能需要由其他团队测试，可能在其他时区。作为我们不断发展的开发过程的一部分，我们希望代码更改由多个团队进行审查、测试和签署，包括质量工程、安全运营和 UX 设计。

我们的开发环境很快成为一个瓶颈。随着我们团队的不断壮大，挑战变得更加严峻。

## 拉请求需要更多的爱

特性和代码变化都是围绕 git 分支和 pull 请求进行的，所以没有什么比将这些作为焦点来驱动所有必需的协作更好的了。我们需要能够像创建一个 git 分支一样廉价和容易地创建和拆除环境。我们需要最大的灵活性，我们需要以经济高效且可扩展的方式解决这个问题。我们需要**利用环境即服务。**

Harness 应用程序最终达到了一个成熟的水平，我们拥有了实现它所需的所有特性。利用 Kubernetes ingress 和 Harness 部署的灵活性，我们现在可以部署到无限数量的限时环境中，这些环境可以动态创建和配置。这使我们的开发人员不必在共享资源上预留时间，并允许任意数量的实验环境同时存在。时间限制确保资源在使用后被释放，防止浪费成本。

最后，我们能够拥有与质量工程师、设计师和开发团队合作的专用环境。我们现在设计我们的流程，允许开发人员在合并代码之前获得签署。

当我们介绍这些用于测试、协作和共享的短暂环境时，我们发现还有其他几个重要的用例也成为可能。

应用程序的资源配置可以作为部署时间变量公开。然后，我们可以部署资源限制的任意组合，并使用相同的负载对它们进行测试，以对各种配置进行压力测试。

我们可以部署旧版本的应用程序，然后在相同的环境中部署新版本，以测试任何特定版本之间的升级迁移路径。

我们可以对这些环境中的数据进行备份快照，以保存特定的状态，并且备份可以恢复到任何其他环境中。这意味着我们可以保留不同的设置来测试不同种类的功能，并将任何相关的设置恢复到包含特定功能构建的环境中。下面将详细介绍我们如何在 Kubernetes 中建立这些短暂的环境，并使用 Harness 来部署它们，从而实现您的所有梦想。

## 战略

对我们来说，一个工作环境由部署到 Kubernetes 集群中的大量微服务组成，路由由入口控制器处理。这里描述的方法应该适用于任何类似的设置。

我们从一个自动扩展的 Kubernetes 集群开始，专门用于托管这些临时环境。入口控制器和不属于按需环境的任何共享服务被安装到专用命名空间中。

每个短暂环境被部署到集群中的唯一命名空间，创建入口规则以基于匹配命名空间名称的路径前缀将流量路由到该命名空间中的服务。

https://adhoc.mydomain.com/namespace/service-path

将注释和元数据一起添加到名称空间中，元数据包括谁部署了它、它最后一次部署的时间以及生存时间(TTL ),在此之后它可以被拆除。

API version:v1
kind:Namespace
metadata:
name:my-awesome-feature
labels:
harness-managed:" true "
annotations:
TTL-hours:" 12 "
last-deployed-by:妮莎弘
last-deployed-at:" 1415926535 "

由于每组微服务及其入口和数据库都位于开发人员选择的唯一命名空间中，因此部署是完全隔离的。将所有的部署服务和依赖项(除此之外别无其他)放在它们自己的名称空间中，这样在名称空间过期后就可以很容易地拆除所有的东西。

## 履行

让我们来看看这在 Harness 中是如何配置的。

## 设置

首先，我们希望在部署时收集用户输入，包括名称空间的名称及其所需的 TTL。我们还收集我们希望开发人员输入的任何其他配置。有些是可选的，有些是必需的。一些预填充了合理的默认值，而另一些则留为空白。名称空间被作为输入，并在服务基础设施中使用表达式引用。这可确保所有工作负载和服务都部署到选定的命名空间。

命名空间:$ { workflow . variables . namespace }

我们正在创建一个带有参数化名称和注释的名称空间，因此名称空间规范是模板化的。

API 版本:v1
种类:命名空间
元数据:
名称:{ { {。价值观。命名空间。name } }
注释:
TTL-hours:{ {。价值观。TTL hours | quote } }
最后部署者:{ { {。价值观。lastdeployedby } }

这些值由用户输入的内容或其他可用的表达式(如执行部署的人员的姓名)填充。

TTL 小时数:$ {工作流。变量。namespace _ TTL _ hours }
lastDeployedBy:$ { deploymentTriggeredBy }

我们还需要将 last-deployed-at 设置为以秒为单位的当前时间戳，这样我们就可以在名称空间过期后拆除它。为此，我们使用一个 shell 脚本中的 kubectl 命令。

kubectl annotate 命名空间$ { infra . kubernetes . namespace } last-deployed-at = $(date+% s)-overwrite = true

对于入口规则，我们指定一个路径前缀作为选定的名称空间，并重写不带前缀的目标。现在，所有以名称空间开始的请求都被路由到该名称空间中的服务。

API version:extensions/v1 beta 1
kind:Ingress
元数据:
名称:管理器-api
注释:
kubernetes.io/ingress.class: " nginx "
nginx.ingress.kubernetes.io/rewrite-target:/API
规范:
规则:
- http:
路径:
-路径:{ { { . values . path prefix } }/API
后端:
服务名称:管理器
服务端口:管理器-端口

该值将路径前缀指定为命名空间名称。

路径前缀:/$ { infra。库伯内特。命名空间}

请注意，相同的清单可能用于传统环境中的部署，在这种情况下，pathPrefix 对于这些环境可以留空。
微服务使用 Kubernetes DNS 在名称空间内相互请求，仅通过名称引用每个服务。

SERVER _ URL:https://verification-SVC:7070

对于来自集群外部的请求，比如来自 UI 的请求，环境变量用名称空间参数化，并在使用 Harness 部署服务时使用。

MANAGER _ URL:https://ad hoc。我的领域。com/$ { infra。库伯内特。命名空间}/API/

我们向将每个服务部署到名称空间的工作流添加了一个资源约束。这确保部署到相同名称空间的相同工作流不会同时运行，从而导致冲突。为此，定义一个能力为 1 的资源约束，然后在工作流中使用该资源约束。将单位指定为服务基础设施 ID 和名称空间的组合。容量和使用将被分割成给定表达式的唯一值。

## 部署

一旦开发人员输入要收集的所有值并开始部署，我们要做的第一件事就是创建并注释名称空间。接下来，我们将数据库部署到名称空间中，并用测试数据填充它。

然后，我们部署所有的微服务。

最后，我们用 HTTP 验证来验证服务端点。

新环境现在可以使用了。

## 拆毁

为了拆除过期的名称空间，我们每隔几个小时在时间触发器上执行一次工作流。此工作流运行一个脚本来检查每个命名空间上的 TTL 批注，如果过期，则将其删除。这个脚本也可以作为 Kubernetes CronJob 运行。

namespaces = $(ku bectl get namespaces \
-o JSON path = " {。$namespaces 中 ns 的 items[*]. metadata . name " })
；do
TTL _ hours = $(kube CTL get namespace $ ns \
-o JSON path = ' { . metadata . annotations . TTL-hours } ')
ts _ last = $(kube CTL get namespace $ ns \
-o JSON path = ' { . metadata . annotations . last-deployed-at } ')
if[$ ts _ last-le $($(date+% s)-TTL _ hours * 3600))]；然后
kubectl 删除名称空间$ns
fi
完成

## 摘要

提供无限制的临时环境，以防止开发人员争夺资源，并实现广泛的协作和共享。

在合并代码之前共享功能为有价值的反馈提供了机会，并为团队合作开辟了新的途径。你也可以[报名免费试用](https://app.harness.io/auth/#/signup)吊带。

布雷特·赞