# State channels

状态通道是 Layer 2 的方案之一，在两个节点间建立通道，允许节点间的链下交易。

## 闪电一样的比特币网络：可扩展的即时支付系统

比特币协议支持全球量级的金融电子交易，不需要第三方机构持有资金，交易双方只需要一台可以通过宽带连接的计算机就可以。这里提出一种支持线下交易的系统，可以随时随机使用网络进行小额交易。这些小额交易可以发生在相互不信任的节点之间，这些节点通过在链上合约进行登记建立关系。如果遇到了恶意节点，合约将通过一系列按照时间锁定的事件强制执行交易。

Reference: [The Bitcoin Lightning Network: Scalable Off-Chain Instant Payment](https://lightning.network/lightning-network-paper.pdf)

## Raiden Network 是什么？

雷电网络是针对以太坊 ERC20 的一种链下交易扩容方案，允许即时的、低手续费的、可扩展的、保护隐私的交易。

References: 
- [What is the Raiden Network?](https://raiden.network/101.html)
- [Writing a Simple Payment Channel](https://docs.soliditylang.org/en/v0.5.3/solidity-by-example.html#writing-a-simple-payment-channel)

## Virtual channels

在这篇文章里，我们描述一种状态通道的架构叫做“虚拟通道”，它是唯一支持像付费文件的流式支付之类的架构。虚拟通道可以简化去中心化系统中图式结构的交易查询、Filecoin 内容检索、状态通道网络中的奖励机制等。

### 动机

让我们设计一种不需要信任的支付系统，用于在分布式储存系统中下载文件。如果使用以太坊的主网络，每下载文件的一个小部分，都需要支付最低 2 美元的手续费，而且以太坊每秒钟只能完成 50 笔交易。Optimistic 和 ZK Rollups 都可以增加系统的吞吐量、降低手续费。StarkEx 的 ZK Rollups 支持每秒钟 3000 笔交易的速度，手续费低至 0.03 美元。假如我们要用 1 美元的钱去下载 1GB 的文件，一个文件的分片大小是 256KB，将会产生 5000 笔交易。在网速是 20MB 每秒的情况下，用户需要以 0.0002 的手续费每秒完成 80 笔交易。Rollups 的交易速度好像稍微不太够，手续费更是超出预期了。

对于这样吞吐量和手续费的需求，状态通道的方案开了一个好头。状态通道可以在打开通道后，尽情在通道的两个节点间进行交易，吞吐量只受限于网络带宽。唯一的挑战就是节点需要和其他很多个节点打开通道，打开通道的过程本身是主要和主网络交互的，也是一笔昂贵的开销。

虚拟通道是我们用来解决这些问题设计出的方案。虚拟通道适用于多个节点连接向同一个中间节点的情形，节点都可以连接到一个不受信任的中间节点，然后节点和节点之间建立私有通道进行交易。重要的是，节点可以通过主链的问题挑战收回质押的金额，即使其他节点甚至中间节点都掉线了。

一般情况下，虚拟通道会允许两个节点在任何网络拓扑的结构下打开。

### 相关背景

在目前的区块链生态中，状态通道经常是这样几个步骤：

- 通过链上交易建立关系，并且质押金额
- 通过通道进行交易、交换金额
- 通过链上交易关闭通道，完成质押金额的转移

在之前的文章中，我们已经描述了如何组织通道的结构，以及通过账本通道从一个通道转移金额到另一个通道上。这些架构有一个限制，就是必须通过链上交易建立直接的关系。如果两个节点想要进行交易但没有提前打开通道，这两个节点就需要和合约进行交易并且质押金额进去。

虚拟通道的设计，将支持这样的场景：

- 一个节点建立状态通道到任意一个中间节点
- 另一个节点也建立通道到中间节点
- 在中间节点的帮助下，两个节点可以建立私有的交易通道，而不需要任何链上交易。我们将这种私有通道称为虚拟通道。

节点只需要与中间节点建立关系，就可以和所有连接到中间节点的节点建立虚拟通道。当然，中间节点还是在链上维护了数据的。

我们的协议叫做 Nitro，将支持以下用例：

- 在中间节点的帮助下，两个节点建立了虚拟通道，不过并不是说两个节点就在通道里了，中间节点会负责通道的创建以及在通道关闭时处理最终的金额情况。两个节点通过虚拟通道，不但可以进行交易，而且交易不需要经过中间节点。更重要的是，通道是可编程的，通道可以支持任意形式的数据交换而不只是普通的金额交换，就像以太坊的智能合约一样。比如节点在通过虚拟通道支付之后，对方可以返回一个相同内容的文件，或者支付一笔图式的交易结构等。
- 所有的 Nitro 通道都是可以组合的，或者以其他形式递归地进行组合。一旦节点质押金额，就可以做所有的事情了，和主链合约交互、建立状态通道或者虚拟通道、运行任何自定义的应用等。

### Nitro 的特点

其他状态通道的协议，比如 Raiden，使用哈希时间锁定的机制在两个节点间建立通道。问题在于，它所有的中转交易都必须经过中间节点，由中间节点转发。

一些新的架构像 Scalar，允许节点在连接到中间节点后，点对点地进行交易，但是中间节点仍然需要理解两个节点间的交易方式。而 Nitro 的虚拟通道将可以实现，中间节点不知道明确知道两个节点的交互方式。

Reference: [Virtual channels: creating a state channel network](https://blog.statechannels.org/virtual-channels/)

## Nitro Protocol

Nitro 是一种新的 State channels 协议，允许节点不经过链上交易就可以打开和关闭通道，并且支持多方建立通道、第三方虚拟通道。

Reference: [Nitro Protocol](https://eprint.iacr.org/2019/219.pdf)

## Counterfactual

Reference: [Counterfactual: Generalized State Channels on Ethereum](https://medium.com/statechannels/counterfactual-generalized-state-channels-on-ethereum-d38a36d25fc6)

## Celer Network

Celer Network 号称结合了 State channels 和 Rollup，提供了一个 layer2 平台用于 DeFi。

References:
- [A Coherent Layer2 Scaling Platform](https://www.celer.network/technology)
- [Welcome to CelerCore Documentation](https://www.celer.network/docs/celercore/)

# Perun

Reference: [Perun 2.0](https://perun.network/wp-content/uploads/Perun2.0.pdf)


