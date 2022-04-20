# Optimistic rollups

Reference: 
- [Optimistic Rollups: How They Work and Why They Matter](https://medium.com/stakefish/optimistic-rollups-how-they-work-and-why-they-matter-3f677a504fcf)
- [How does Optimism's Rollup really work?](https://research.paradigm.xyz/optimism)
- [(Almost) Everything you need to know about Optimistic Rollup](https://research.paradigm.xyz/rollups)

## Arbitrum

### 动机

Reference: [Beyond State Channels](https://medium.com/offchainlabs/beyond-state-channels-ed810a743c25)

### 简介

Arbitrum 有和 Ethereum 一样的 API 接口，支持 Ethereum 所有的语言，不需要更改任何内容或者下载任何新的软件，就可以无缝从 Ethereum 切换到 Arbitrum。

Reference: [Arbitrum Rollup Basics](https://developer.offchainlabs.com/docs/rollup_basics)

### 协议设计

Reference: [Arbitrum Rollup Protocol](https://developer.offchainlabs.com/docs/rollup_protocol)

## Optimistic Ethereum (OE)

Optimistic 是以太坊上的一种针对以太坊应用的交易扩容协议，它可以让交易真正变得便宜，让每个人都轻易使用、都能够负担起在以太坊进行交易的费用。

这个文档向所有想深入了解 optimistic 协议的人解释协议的工作原理。

Optimistic Ethereum 意味着和以太坊一样的使用感受，但是速度更快、费用更低。开发者可以基于我们的框架进行操作，我们也在尽可能让协议的使用变得简单。除了个别例外的特性，所有能在 L1 上运行的 Solidty 合约都可以在 L2 上运行。同样的，链下应用也只需要改变接口地址就可以无缝衔接使用。

Optimistic 使用了一种 OVM，其中包含了 EVM 的功能。

References:
- [Contract Overview for OVM 1.0](https://community.optimism.io/docs/protocol/protocol.html)
- [Attacking an Ethereum L2 with Unbridled Optimism](https://www.saurik.com/optimism.html)

