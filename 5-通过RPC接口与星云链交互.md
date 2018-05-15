# 通过RPC接口与星云链交互

* [Nebulas 101 - 05 通过RPC接口与星云链交互](https://github.com/nebulasio/wiki/blob/master/tutorials/%5B%E4%B8%AD%E6%96%87%5D%20Nebulas%20101%20-%2005%20%E9%80%9A%E8%BF%87RPC%E6%8E%A5%E5%8F%A3%E4%B8%8E%E6%98%9F%E4%BA%91%E9%93%BE%E4%BA%A4%E4%BA%92.md)

> 星云链已经在每个星云节点中实现了RPC服务器和HTTP服务器。


## 接口模块

* API：提供所有和用户私钥无关的接口
* Admin：提供所有和用户私钥相关的接口


## 配置文件

> 星云节点中的RPC服务器和HTTP服务器都可以在节点的配置中配置对应的端口，以及开放的模块。

```
# 用户与节点交互的服务配置，同一台机器启动多个时注意修改端口防止占用
rpc {
    # gRPC API服务端口
    rpc_listen: ["127.0.0.1:8684"]
    # HTTP API服务端口
    http_listen: ["127.0.0.1:8685"]
    # 开放可对外提供http服务的模块
    http_module: ["api","admin"]
}
```


## 使用实例 - HTTP

> 通过HTTP接口和星云节点交互。


* GetNebState: 我们可以调用API模块中的GetNebState接口来获取节点当前状态，包括所在链ID，最新区块，协议版本等等。

```
curl -i -H Accept:application/json -X GET http://localhost:8685/v1/user/nebstate
# {"result":{"chain_id":100,"tail":"b1ed8a3739fd8a1ced24c7de94d31a792b27250f083bbd23bf58374bfd3f8da2","lib":"0000000000000000000000000000000000000000000000000000000000000000","height":"90","protocol_version":"/neb/1.0.0","synchronized":false,"version":"1.0.1"}}
```

* UnlockAccount: 调用Admin模块中的UnlockAccount接口来在节点内存中解锁一个账户。所有解锁的账户都可以被用来直接发送交易，而不需要密码。

```
curl -i -H 'Content-Type: application/json' -X POST http://localhost:8685/v1/admin/account/unlock -d '{"address":"n1FF1nz6tarkDVwWQkMnnwFPuPKUaQTdptE", "passphrase": "passphrase"}'
# {"result":{"result":true}}
```


## 使用实例 - RPC

skip


## 接口列表

* [rpc](https://github.com/nebulasio/wiki/blob/master/rpc.md)
* [rpc_admin](https://github.com/nebulasio/wiki/blob/master/rpc_admin.md)
