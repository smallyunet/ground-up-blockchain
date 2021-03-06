# 区块链的共识概览

## 摘要

区块链网络包含了一些密码学概念，包括非对称加密、哈希算法、共识算法等。尽管现在的一些主流协议被广泛使用，像 Proof of Work 和 Proof of Stake，但它们仍然有缺陷。为了能让共识算法能应用在医学或交通等更多领域。有很多其他协议由此诞生。虽然那些协议有一些值得研究的特性，但还相对不为人知。过去的时间里，有很多新的协议也应用到了区块链中，不过也数量有限，并不能包含大多数的情况。对这些共识算法在设计上的特点进行分析，可能会有助于学者、区块链从业者、研究人员有所帮助。这篇论文包含了过去 3 年新提出的共识协议，我们最终通过吞吐量、安全性、能源消耗等指标评估它们的整体性能，我们分析了这些共识协议在可扩展性和性能上做的权衡。据我们所知，这是第一篇涵盖对这些协议特性分析的论文，强调了这些共识协议的特点以及有可能用于未来共识协议设计的内容。

Reference: [Blockchain Consensus: An Overview of Alternative Protocols](https://www.mdpi.com/2073-8994/13/8/1363)

## 一些知名的共识协议

### Proof of work

最广泛使用的共识协议是 Bitcoin 在 2009 年的简介中出现的 PoW，通过算力胜出的参与者可以向区块链增加新的块。一旦块提交到网络并且被接受，提交者就可以获得网络的出块奖励以及其中交易的手续费。计算的算力将被用来解决一个哈希难题，计算的结果会写在产生出的块中。

### Delayed Proof of Work

dPoW 被用在一个叫 Komodo 的多链结构的平台中。这种共识协议中存在一个第二层的网络节点，这些网络节点使用 PoW 出块提交到主链上。第二层一共 64 个节点，每年通过投票选出。这样的做法避免了额外的算力浪费。

### Proof of Stake

PoS 是一种对 PoW 去其糟粕，取其精华的协议。参与者必须拥有一些系统中的加密货币才可以挖矿或者进行交易的验证。如果一个节点拥有 10% 的货币，那他挖出下一个块的概率就是 10%。PoS 共识协议中，块只由提案节点产生。提案节点同时也是验证节点，验证节点可以根据比例分配得到出块产生的奖励。网络中所有想要参与出块的节点，都必须质押一定金额到网络中。另外，协议中的提案节点将会随机选出一个主节点，主节点负责根据投票结果，决定接受或者拒绝新产生的块，一般投票数量超过 2/3 为通过。

### Delegated Proof of Stake

DPoS 是 Pos 衍生出的一种协议，将权益拥有节点与验证节点分离，强调了选举的过程。

### Proof of Authority

POA 中存在一类被信任的节点，由这些被信任的节点处理交易和块。由于这些 validator 的数量是有限的，整个网络的性能可以非常高，并且拥有良好的扩展性和接近于 0 的手续费用。POA 不需要像 POS 那样质押资产，但是 POA 质押的是节点自身的声誉。声誉可以通过累积参与到网络中的时长增加，这克服了 POS 越是富有的节点越会获得更多激励的问题。不过，POA 是强中心化的，整个网络被控制在少数节点手中。

### Proof of Importance

PoI 依赖 importance score 评估节点的价值，授予节点权限，拥有资产越多，importance score 越高。低于某一种数额的节点将无法参与块的创建。这样的共识机制意在保护整个网络。

### Practical Byzantine Fault Toerance

PBFT 是拥有 1/3 容错能力的共识，解决了经典的拜占庭容错的问题。提案节点将产生出的块分发给其他所有节点，如果超过 2/3 的节点投票通过，则确认该块。

### Ripple Protocol

Ripple 或者叫 XRP 节点共识协议，属于 BFT 共识的一种。validators 会维护一个待执行的交易列表，这些 validators 是诚实节点。当一定数量百分比的节点同意某一个交易集，这些交易将被包含在下一个节点版本中。如果交易集没有通过，节点也会通知其他节点重新处理这些交易。这是一个持续的处理过程，共识可以达到至少 80% validators 的状态是一致的。不过，如果没有达到预期一致的效率，就可能面临网络被攻击的风险。

### Delegated Byzantine Fault Tolerance

DBFT 类似国家的治理系统，有公民、选民、代表等角色，共同管理国家。这种协议依赖投票的程序，类似于 PoS，每个节点都可以投票，随机选出一些代表。选民负责回应和跟踪所有公民的行为。被随机选出的代表负责块的提案，选民参与块数据的验证。块的产生同样需要 2/3 选民同意。不过，如果有 2/3 的选民投票选出新的代表，块的提案过程会重新来过。

### Federated Byzantine Agreement

FBA 在所有的节点中划分出一个子节点的集合，新产生的块将由这个集合中的节点确认，并且这个集合会频繁的更新。

### Proof of Elapsed Time

2016 年，Intel 发布了 PoW 的替代方案 PoET，Hyperledge 的 Sawtooth 项目使用了这种共识机制。PoET 使用一种随机的机制，参与节点等待一个随机的时间值，最新的块将由随机时间最短的节点产生。将块广播到网络的同时，块数据包含本次等待的这个最短时间，用于其他节点确认真伪。这样的共识机制比 PoW 更加去中心化，但是它也有一些问题，不太适用用公有链，因为这样的共识会让整个网络变得混乱，不是足够稳定。另外，PoET 需要使用 Intel 的专用硬件，给这种共识机制的推广带来了困难。使用这种共识机制的前提是，我们需要信任运行节点的硬件设备。

### Proof of Burn

PoBr 不像 PoW 或者 Pos 一样需要强大的算力挖矿，PoBr 采用了另一种思路，节点可以通过销毁 token 争夺最新块的记账权，也就是使用短期内的损失换取出块后的更大奖励。相当于节点质押金额进去挖矿了。这样的共识算法节省了硬件资源的消耗，Slimcoin 是典型的 PoBr 的例子。

### Proof of Capacity

PoC 是一种基于磁盘容量的共识机制。PoC 使用一些方式证明节点的可用容量为某一些数值，整个区块链网络会将这一部分容量用以为其他节点提供服务。可用容量的大小即节点的贡献值，节点根据提供空间的大小获得奖励。PoC 一般使用 hard-to-pebble 的图结构证明节点的可用空间大小。

## 可替代的协议

这一部分我们会讨论 15 种近 3 年的可供选择的协议。这些协议可以按照这样的方式进行分类：

- Consensus Protocol based on Effort or Work (CPE)
- Consensus Protocol based on Wealth or Resources (CPW)
- Consensus Protocol based on Past Behavior or Reputation (CPPB)
- Consensus Protocol based on Representation (CPR)

- Consensus Protocol based on Effort or Work
    - Proof of Benefit
    - Proof of Phone
    - Proof of Learning
    - Proof of Sincerity
    - Proof of Accuracy
    - Proof of Adjourn
    - Proof of search
    - Proof of Evolution
    - Proof of Experience

- Consensus Protocol based on Wealth or Resources
    - Proof of Participation and Fees

- Consensus Protocol based on Past Behavior or Reputation
    - Proof of Familiarity
    - Proof of Reputation
    - Proof of Reputation X

- Consensus Protocol based on Representation
    - Proof of Vote

个人来看，这些所谓可选择作为替代协议的共识机制，并没有特别大的创新，更多是应用形式上的创新。

