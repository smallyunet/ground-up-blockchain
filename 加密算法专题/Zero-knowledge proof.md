## 零知识证明是什么

### 简介

在密码学中，零知识证明或者零知识协议是一种可以让一方证明另一方提供的表达式是否是 true，证明过程不需要任何除了表达式之外的真实信息。零知识证明的过程就是证明一个人拥有的某些信息是可以被简单证明真伪的，难点就在于如何在不获得消息本身相关内容的情况下，证明真伪。如果表达式包含了秘密的信息，验证者将不会通过这个表达式的验证。表达式要能够证明待证明一方确实知道一些信息，但是又不能透露信息本身。

交互式的零知识证明需要在被验证者和验证者之间进行一些交互。

References:
- [Zero-knowledge proof](https://en.wikipedia.org/wiki/Zero-knowledge_proof)
- [A Survey on Zero Knowledge Range Proofs and Applications](https://arxiv.org/pdf/1907.06381.pdf)
- [Demystifying Zero Knowledge Proofs](https://docs.google.com/presentation/d/1gfB6WZMvM9mmDKofFibIgsyYShdf0RV_Y8TLz3k1Ls0/edit#slide=id.p)

### Zilch

Zilch 是一个基于 STARKs 的框架，实现了一种叫做 ZeroJava 的语言，是 Java 的精简版本。

Reference: [Transparent Zero-Knowledge Proofs With Zilch
](https://medium.com/@trustworthy-computing/transparent-zero-knowledge-proofs-with-zilch-2031a63fcef3)

### Awesome

- [Awesome zero knowledge proofs (zkp)](https://github.com/matter-labs/awesome-zero-knowledge-proofs)

## Bulletproofs

### 简介

References:

- [Bulletproofs: Short Proofs for Confidential Transactions and More](https://crypto.stanford.edu/bulletproofs/#:~:text=Bulletproofs%20are%20short%20non%2Dinteractive,anything%20else%20about%20the%20number.)
- [Bulletproofs: Short Proofs for Confidential Transactions and More](https://eprint.iacr.org/2017/1066.pdf)
- [A pure-Rust implementation of Bulletproofs using Ristretto](https://github.com/dalek-cryptography/bulletproofs)
- [Building on Bulletproofs](https://cathieyun.medium.com/building-on-bulletproofs-2faa58af0ba8)

### 教程

Reference: [Module bulletproofs::notes](https://doc-internal.dalek.rs/bulletproofs/notes/index.html)

## zk-SNARK

Reference: [halo2](https://zcash.github.io/halo2/index.html)

## zkSTARKs

Vitalik Buterin’s blog series on zk-STARKs:
- [STARKs, Part I: Proofs with Polynomials](https://vitalik.ca/general/2017/11/09/starks_part_1.html)
- [STARKs, Part II: Thank Goodness It's FRI-day](https://vitalik.ca/general/2017/11/22/starks_part_2.html)
- [STARKs, Part 3: Into the Weeds](https://vitalik.ca/general/2018/07/21/starks_part_3.html)




