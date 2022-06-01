# Solidity

## 简介

Solidity 是一种编写以太坊智能合约的专用脚本语言，语法上是面向对象的语言，内置了一些区块链相关的对象，如交易、时间戳、块高度等。

Solidity 由于属于 DSL 的特性，在语言本身上是无法和目前的主流编程语言抗衡的，但我们不需要对它有什么要求。

Solidity 中稍微有趣的特性是 modifier，比如：

``` solidity
modifier A() {
    // some code
    _;
}

modifier B() {
    _;
    // some code
}

function getData() A B {
    // some code
}
```

modifier 是可以自定义内容的修饰符，`_` 代表 `getData` 函数体，意为在 A 中执行 some code，然后执行函数，在 B 中执行函数，然后执行 some code。

modifier 的好处是，可以省去很多重复性的代码，像是一些相同的参数校验，我看到过一些这样的代码：

``` golang
func a() {
    if obj != nil {
        return
    }
}

func b() {
    if obj != nil {
        return
    }
}

// ... 
```

如果有 modifier 就可以在视觉上很好的解决这种难堪的写法。

不过 modifier 的问题是，它会让函数的定义变得丑陋，因为 modifier 是不限制数量的，这对代码美感的破坏性甚至超过重复写一些相同的代码。

另外，Python 的 deorators 似乎也是在解决和 modifier 类似的问题，Java 的 annotaion 也是。modifier 并不算是多么独到的特性。

Reference: [Solidity](https://docs.soliditylang.org/en/v0.8.11/)

## Yul

Yul 是一种中间语言，和 Solidity 没有同等的地位，它似乎不是一种值得去了解的语言。

我们使用这些语言的目的应该还是要开发智能合约而已，而不是学习编程语言。

Reference: [Yul](https://docs.soliditylang.org/en/v0.8.11/yul.html)

## 相关

- [Gas optimizations in Smart Contracts](https://medium.com/@shub.sharma350/gas-optimizations-in-smart-contracts-a894768b274c)


