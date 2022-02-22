# 零知识证明是什么

在密码学中，零知识证明或者零知识协议是一种可以让一方证明另一方提供的表达式是否是 true，证明过程不需要任何除了表达式之外的真实信息。零知识证明的过程就是证明一个人拥有的某些信息是可以被简单证明真伪的，难点就在于如何在不获得消息本身相关内容的情况下，证明真伪。如果表达式包含了秘密的信息，验证者将不会通过这个表达式的验证。表达式要能够证明待证明一方确实知道一些信息，但是又不能透露信息本身。

交互式的零知识证明需要在被验证者和验证者之间进行一些交互。

References:
- [Zero-knowledge proof](https://en.wikipedia.org/wiki/Zero-knowledge_proof)
- [A Survey on Zero Knowledge Range Proofs and Applications](https://arxiv.org/pdf/1907.06381.pdf)

## Zilch

Zilch 是一个基于 STARKs 的框架，实现了一种叫做 ZeroJava 的语言，是 Java 的精简版本。

Reference: [Transparent Zero-Knowledge Proofs With Zilch
](https://medium.com/@trustworthy-computing/transparent-zero-knowledge-proofs-with-zilch-2031a63fcef3)



