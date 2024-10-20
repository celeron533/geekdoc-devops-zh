# 什么是 py torch-py torch | circle ci 简介

> 原文：<https://circleci.com/blog/leading-open-source-ml-advancements-an-introduction-to-pytorch/>

PyTorch 是由脸书人工智能研究小组创建的开源深度学习平台。像 NumPy 一样，PyTorch 是一个张量运算库，但增加了对 GPU 和其他硬件加速的支持，以及为人工智能研究人员探索不同领域提供的有效工具。虽然 PyTorch 最初是 Lua Torch 框架的基于 Python 的后继者，但它的范围已经扩大，不仅是一个研究平台，还是一个部署平台。像斯坦福和 T2 这样的组织依靠 PyTorch 来推动他们的机器学习研究和产品。PyTorch 依靠 CircleCI 为其众多开源贡献者创建了一个平稳可靠的 PR 流程，并且比以前的解决方案更快地交付代码，开销也更少。

PyTorch 团队有近 100 名核心成员(脸书内部和外部)，此外还有 900 多名开源贡献者和 6 名普通维护者。

> “我们接触的东西都是活跃的研究领域，如量子化和低精度神经网络。”

他们的图书馆还支持数百个下游学术和商业项目。“我们接触的东西都是积极研究的领域，如量化和低精度神经网络，”在 PyTorch 工作的脸书产品经理 Joe Spisak 说。“我们认为这些是理所当然的，因为我们今天对翻译和计算机视觉等事物进行了低精度的万亿次预测。但在这个领域，人们仍然发表大量论文，他们正在寻找新的做事方式。”团队在 PyTorch 上的工作为那些进行最新研究的人提供了重要的工具。

### 为社区优先考虑开源

对于大多数人来说，在盈利性公司中管理开源社区的需求可能是一个挑战，但对于 PyTorch 来说，这是他们是谁的核心。“开源从一开始就存在于我们的 DNA 中，”Spisak 说。“当脸书在 2004 年问世时，它是建立在一个开源堆栈上的，包括 Linux、Apache、MySQL 和 PHP，因此，开源一直是脸书工程部门核心文化的一部分。”脸书的开源努力与公司一起成长，使 PyTorch 团队和人工智能部门的其他人能够为世界各地的研究人员提供重要的工具，并建立一个庞大的互联项目网络。

“我们致力于开源我们所做的大部分事情，”Joe 继续说道，“当我们觉得项目是稳定的，并且我们认为它们可以有益于社区或研究时，它就是开源的。我们维护它们，并从 PyTorch 等许多项目中创建社区。”

### 大规模运行操作系统的 CI/CD

超过 900 名 PyTorch 贡献者依靠 CircleCI 来管理他们的软件交付工作流。该团队的堆栈包括 CircleCI、Netlify 和 GitHub 等 CDN 服务。这给了他们一个一致的过程来处理任何提交或拉取请求，不管这个项目有多少贡献者。

“这种类型的系统可以从小项目扩展到大项目，”脸书 OSS 项目的开发者倡导者 Joel Marcey 说。“为这个项目做出贡献的每个人都知道他们将获得一致的体验，并且可以看到他们的公关是通过还是失败。”

> “为这个项目做出贡献的每个人都知道他们将获得一致的体验，并且可以看到他们的公关是通过还是失败。”

“CircleCI 帮助我们以更灵活的方式做事，”脸书开源开发者倡导者 Eric Nakagawa 说。“我们团队直接面对的最大挑战之一就是在网站上创建教程。这个过程以前需要四到六个小时，当你试图在这里或那里进行小的调整时，可能会非常沮丧。”使用 CircleCI，Eric 的团队能够在多个实例类型上并行运行他们的构建，这使得他们的构建时间减少了 75%。更重要的是，通过将自己从保持机器运转的日常顾虑中解放出来，他们能够专注于项目跳动的心脏:他们的社区。

> “通过允许我们不关注基础设施，我们能够将[我们的努力]瞄准我们认为可以提供更多价值的地方，这是我从与 CircleCI 的合作中获得的最大收获之一。”

### 跟上 PyTorch 和脸书·艾

要了解更多关于 PyTorch 和脸书其他人工智能的发展，请访问 https://ai.facebook.com/的 T2。