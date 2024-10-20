# 管理 CI/CD 管道中的秘密|线束

> 原文：<https://www.harness.io/blog/secrets-management-ci-cd>

管理 CI/CD 管道中的机密对于提高云安全性至关重要。了解 Harness 如何利用 CI/CD 中的机密管理。

数据泄露和供应链被黑的最常见来源？暴露的数据和秘密。从优步到网络安全管理软件产品，每年公司和客户都会发现安全、数据和治理的重要性。但是工程和产品团队如何平衡创新和速度的需求与交付和变化的信心呢？这个博客解释了秘密以及如何通过自动化、工具和 [CI/CD 管道](https://harness.io/blog/continuous-delivery/ci-cd-pipeline/)来保护它们。

## 什么是秘密？

如果你曾经在你的代码库中发布过一个私钥，那么你就分享了一个秘密。秘密是您想要控制访问的任何信息，例如密码、API 密钥、配置文件、OAuth 令牌和 ssh 密钥。

秘密只有少数人知道。在软件交付中，秘密存在于环境、第三方 API、生产基础设施和工具中。

## 为什么秘密与 CI/CD 相关？

那么，为什么秘密和 CI/CD 管道如此重要呢？

秘密存在于整个交付生命周期中，因为应用程序秘密、凭证和其他敏感信息应该受到保护、混淆和治理。

*   像 GitHub、GitLab 和 BitBucket 这样的代码库。
*   持续集成服务器和持续交付平台——Jenkins、Bamboo、JFrog、TeamCity、Drone、Harness、GitLab CI/CD、CircleCI 等等。
*   云提供商和容器平台——AWS、GCP、Azure、Kubernetes(作为密钥、配置文件和其他信息)。
*   基础设施—(SSH 密钥、负载平衡器凭证)。
*   协作提供商——Slack、SMTP、吉拉、ServiceNow。
*   验证提供商–app dynamics、New Relic、Splunk。
*   以及软件服务或应用程序本身。

如今，组织在不同的环境中部署了多种应用程序服务，使用不同的工具和访问级别来管理流程。CI/CD 管道在开发生命周期的各个阶段快速、安全地传送我们的代码变更，并重复地将任何变更交付给用户。因此，如果我们能够将机密管理实践集成到交付过程中，CI/CD 为整个交付生命周期中的机密管理提供了基础。

在本博客的下半部分，我们将分享如何解决主要的秘密管理挑战。

## CI/CD 中管理机密的挑战

在过去的六个月里，我们倾听了数百名客户分享他们在通过 CI/CD 管道交付时管理机密的痛苦和挑战。以下是软件交付平台最常见的功能要求:

*   一个集中的地方，可以看到 CD 工具中使用的所有秘密。。
*   针对每个秘密的细粒度访问管理。
*   跨部署工作流和管道的秘密使用的可见性，例如在工作流 x 中使用的 ssh 密钥。
*   Changelog 功能可以跟踪秘密是何时添加的，由谁添加的，以及更改了什么。
*   在运行时使用秘密时的通知(例如，用于下载工件的 Jenkins 密码或用于将工件部署到服务器的 SSH 密钥)。
*   弃用并删除过时的机密-实施机密轮换。
*   将现有机密迁移到新服务，例如，将机密移动到不同的保管库设置或不同的亚马逊 KMS。
*   在 KMS 或金库级别禁用秘密，以防有泄露的威胁。

让我们更详细地讨论一下目前存在的应对这些挑战的各种解决方案。

## 机密存储和管理工具

机密管理系统提供了存储和访问机密的解决方案。流行的解决方案包括 HashiCorp 的 Vault、Docker Secrets、KeyWhiz 和 AWS Secrets Manager。现在，秘密管理工具不仅提供秘密存储，还提供密钥管理/加密和身份管理(这是我们分别听到 AWS KMS 和 PKI 即服务等服务的地方)，这已经相当普遍了。让我们更详细地讨论 HashiCorp Vault 和亚马逊 KMS。

### **哈希公司金库**

HashiCorp 的 Vault 是一种常用的存储和管理机密的开源解决方案。存储的数据是加密的，对该数据的访问通过令牌共享。这些令牌可以使用针对特定租用时间的特定特权来创建，从而授予对特定秘密的访问权。令牌可以在任何时候被撤销，使得秘密不可访问。

这是集中敏感数据的一种流行方式。您的交付体系结构中使用机密的每个组件都通过访问令牌在运行时访问它们，并立即丢弃它们，确保机密访问永远不会超过需要的时间。

如果你正在评估秘密管理工具，这个[新栈博客](https://thenewstack.io/using-vault-to-manage-your-apps-secrets/)提供了评估 HashiCorp Vault 特性时的一些考虑。

### **亚马逊 KMS**

亚马逊 KMS 是加密和解密秘密的流行解决方案。使用亚马逊 KMS，用户创建一个分配有亚马逊 IAM 角色的加密密钥，该角色被配置为共享服务、环境、机器和我们架构中任何其他组件的访问级别，包括 CI 和 CD 系统。这个密钥引用用于加密和解密。

为了更好地理解密钥管理系统是如何工作的，下面是加密/解密的步骤。

*   在数据加密期间，从 KMS 请求新的加密密钥，它返回密钥和密钥的加密值。
*   使用明文密钥，秘密被加密。
*   然后存储加密的密钥和加密的秘密。
*   为了解密，加密的密钥被发送到 KMS，后者又返回明文密钥。
*   然后使用明文密钥解密并使用该秘密。

这确保了敏感信息永远不会作为明文数据(密钥或值)存储在系统中，并且对于存储的每个秘密，加密密钥是唯一的。密钥的加密/解密功能可以通过 AWS 控制台进行控制，如果出现漏洞，主密钥可以被禁用，确保没有人能够使用暴露的秘密进行进一步访问。

## 改进 CI/CD 中的机密管理流程

那么，DevOps、DevSecOps 和工程团队如何更好地自动化和利用这些解决方案作为持续交付的一部分呢？今天的软件交付平台需要解决秘密管理过程的某些组件，以便扩展和管理供应链。

在 [Harness](https://harness.io) ，秘密管理也是我们架构和解决方案的核心。

Harness 包含一个内置的机密管理特性，使您能够存储加密的机密，如访问密钥，并在 Harness 应用程序中使用它们。下图展示了如何在 Harness 中使用机密。

这些秘密总是在需要的时候被访问/解密，任何时候都不会以未加密的形式存储。此外，线束管理员无权访问您的钥匙管理系统。代理位于您设置的私有网络中，因此使用 Harness，您永远不必公开您的秘密管理器。这增加了一个重要的安全层。

## 机密管理 CI/CD 工作流程示例

使用 CI/CD 平台解决方案时，通常首先添加一个 secrets manager 工具。在脊甲中，你可以通过选择**安全** > **秘密管理**来实现。该仪表板将允许您点击**配置机密管理器**。

在这里，点击“添加机密管理器”

配置密码管理器对话框添加密码管理器。我们的文档提供了添加以下任何机密管理器的概述。

在本例中，我们将添加一个 AWS KMS 秘密管理器实例。

提供所需的帐户访问信息。

如果用户没有创建任何管理器，默认情况下，Harness 平台使用其 KMS 默认实现来加密/解密您的机密:

您的机密管理器显示到目前为止它已经加密了多少机密。

Harness 还支持将您的秘密迁移到另一个 secret manager 的功能，如果任何 secret manager 存在泄漏的威胁。

需要注意的是，秘密也可以以文件的形式出现。用户可以上传基于[文本](https://docs.harness.io/article/ygyvp998mu-use-encrypted-text-secrets)或[文件的](https://docs.harness.io/article/nt5vchhka4-use-encrypted-file-secrets)秘密。在 Harness CI/CD 平台中，您可以在一个位置跨组织的多个部分和整个交付流程利用这些秘密。

正如你在上面的截图中看到的，这些秘密中的每一个都有关于它们在哪里被引用、谁上传或更改了它们，以及它们在运行时(例如工作流)在哪里被使用的信息。这为您提供了一种集中的方式来管理您的秘密文本和秘密文件，并使您能够看到哪个工作流在哪个环境中使用您的秘密，为您提供了完整的可见性。

## 使用线束 CI/CD 管理机密

这篇博客文章分享了 CI/CD 解决安全和机密管理挑战的多种方法。我们讨论了什么是秘密，使用什么工具来管理敏感信息，以及 [CI/CD 平台](https://harness.io/platform/)如何帮助防止重大黑客攻击和数据泄露。如果您想尝试任何共享的工作流程，[今天就免费试用](https://harness.io/try-free)Harness。