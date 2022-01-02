# Peer-to-peer network

网络发现是点对点网络的基础，毕竟网络需要多个节点组成，而这多个节点需要一些机制来相互认识。

一般常用的机制是预置一些种子地址，比如比特币的种子地址列表在 <https://github.com/bitcoin/bitcoin/blob/master/contrib/seeds/nodes_main.txt>。

节点会请求种子地址指向的节点，然后获取到种子地址拥有的节点列表信息。


