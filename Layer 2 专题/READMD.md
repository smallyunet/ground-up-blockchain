# 概览

## 为什么需要 Scaling

References:

- [What is Layer 2 Scaling Solutions & Why It Is Required?](https://medium.com/crypto-wisdom/what-is-layer-2-scaling-solutions-why-it-is-required-66b8dbf3bc9c)
- [An Introduction to Cross Layer Transfer](https://medium.com/onther-tech/an-introduction-to-cross-layer-transfer-af7e7183c0b9)
- [Blockchain Scalability](https://medium.com/iovlabs-innovation-stories/blockchain-scalability-4dce74382930)

## 简介

性能概览:

|Solutions|TPS|
|-|-|
|State Channels|10,000|
|Plasma|7,200|
|ZK Rollup|4,500|
|Optimistic Rollup|800|

Rollups 方案的分类：

![80](./assets/1.jpeg)

References:
- [SCALING](https://ethereum.org/en/developers/docs/scaling/)
- [Layer 2 Blockchain Scaling: a Survey](https://arxiv.org/pdf/2107.10881.pdf)
- [What is Layer 2 Scaling?](https://tlu.tarilabs.com/scaling/layer2scaling-survey)

## Sharding

Referneces:
- [What’s Sharding and Why is it Important in the Blockchain World?](https://blog.cryptostars.is/whats-sharding-and-why-is-it-important-in-the-blockchain-world-2dfbcf509627)

## Plasma: 可以扩展的自主管理的智能合约

似乎是把区块链的计算放在 MapReduce function 里进行，区块链的历史状态将作为 MapReduces 的计算因子，这样就可以提高区块链的运算速度。

Reference: [Plasma: Scalable Autonomous Smart Contracts](https://plasma.io/plasma.pdf)

## 侧链

侧链是基于 two-way peg 的方式，通过将链上资源的销毁和凭空产生，达到跨链的效果。

Reference: [Sidechain](https://en.bitcoin.it/wiki/Sidechain)

## 未分类

### ImmutableX

第一个专门用于 NFTs 的 Layer 2 方案。用的还是 ZK Rollups。

References:
- [THE FIRST LAYER 2 FOR NFTS ON ETHEREUM](https://www.immutable.com/)
- [Immutable X Whitepaper](https://support.immutable.com/hc/en-us/articles/4405227590799)

### zkEVM

References: 

- [ZKP — zkEVM](https://starli.medium.com/zkp-zkevm-a9b046789b4e)
- [Zkevm Specifications](https://github.com/appliedzkp/zkevm-specs)
- [ZKEVM](https://hackmd.io/Hy_nqH4yTOmjjS9nbOArgw)
- [zkEVM FAQ](https://docs.zksync.io/zkevm/#general)

### Vitra

Vitra 是一个结合了 Smart contract 和 optimistic rollups 的系统。没看懂具体是干什么的，算是一种 idea 吧。

References:
- [Vitra](https://github.com/pfrazee/vitra)
- [Execution Transparency — Hosted smart contracts using secure, append-only logs](https://paulfrazee.medium.com/execution-transparency-hosted-smart-contracts-using-secure-append-only-logs-51c35b3d057f)
- [vitra/docs/whitepaper.pdf](https://github.com/pfrazee/vitra/blob/master/docs/whitepaper.pdf)

### Obscuro

References:
- [Obscuro](http://obscu.ro/)
- [whitepaper](https://whitepaper.obscu.ro/obscuro-whitepaper/abstract.html)
- [Can Zero-Knowledge Proofs achieve Layer 2 privacy?](https://medium.com/coinmonks/can-zero-knowledge-proofs-achieve-layer-2-privacy-71850ca60ae7)

## 资料推荐

- [An Incomplete Guide to Rollups](https://vitalik.ca/general/2021/01/05/rollup.html)
- [What Are the Bitcoin Layers? – Layer 3 vs. Layer 2 vs. Layer 1 Crypto](https://phemex.com/academy/bitcoin-layer-1-vs-2-vs-3)

