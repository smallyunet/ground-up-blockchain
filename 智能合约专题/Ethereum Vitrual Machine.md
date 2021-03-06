# Ethereum Vitrual Machine (EVM)

## 简介

EVM 很难被描述为云集群之类的概念，但是它存在并运行于上千个以太坊客户端中。

以太坊的协议本身需要维护一个不可中断的、不可修改的特殊状态机，状态机内包含了以太坊账户和智能合约的环境。链上所有的区块，以太坊都对它有一个独一无二的状态，EVM 就是定义这种状态规则并且计算出新状态的东西。

Reference: [ETHEREUM VIRTUAL MACHINE (EVM)](https://ethereum.org/en/developers/docs/evm/)

## Gas

以太坊中有三个 Gas 相关的变量： Gas limit、Gas price、Value。

GasLimit 是一笔交易消耗的计算资源上限，GasPrice 是 Gas unit 的单价。GasLimit 用以保证计算资源的消耗是可控的，GasPrice 控制整笔交易的手续费维持在市场平均水平。

References:
- [Understanding Gas in Ethereum](https://www.investopedia.com/terms/g/gas-ethereum.asp#:~:text=%22Gas%20limit%22%20refers%20to%20the,ETH%20or%20a%20smart%20contract.&text=If%20the%20gas%20price%20limit,choose%20to%20ignore%20such%20transactions.)
- [GAS AND FEES](https://ethereum.org/en/developers/docs/gas/)

## 优化

References:
- [Solidity Gas Optimisation](https://deeprnd.medium.com/solidity-gas-optimisation-83c75170f534)

