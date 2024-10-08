
## 代理合约

Solidity合约部署在链上之后，代码是不可变的（immutable）。这使得合约不能修改和升级，
只能部署新合约，使用代理合约可以在合约部署后进行修改和升级。

代理合约存储数据，逻辑合约存储功能函数，当需要升级合约时，只需要将代理合约指向
新的逻辑合约。

代理合约的优势：
可升级：需要升级合约的逻辑时，只需要将代理合约指向新的逻辑合约。
省gas：如果多个合约复用一套逻辑，只需部署一个逻辑合约，然后再部署多个只保存数据的代理合约指向逻辑合约。

[USDT合约](https://etherscan.io/token/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48#code)就使用了代理合约。

代理合约利用`delegatecall`将函数调用委托给了另一个逻辑合约，使得数据和逻辑分别由不同合约负责。并且利用
内联汇编让没有返回值的回调函数也可以返回数据。



