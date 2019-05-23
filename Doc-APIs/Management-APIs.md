Beside the official [RPC APIs](https://github.com/symverse-lab/Document/blob/master/Doc-APIs/JSON_RPC_API_github.md) interface go-symverse has support for additional management APIs. Similar to the official APIs, these are also provided using [JSON-RPC](http://www.jsonrpc.org/specification) and follow exactly the same conventions. Gsym comes with a console client which has support for all additional APIs described here.



## Enabling the management APIs

To offer these APIs over the Gsym RPC endpoints, please specify them with the `--${interface}api`
command line argument (where `${interface}` can be `rpc` for the HTTP endpoint, `ws` for the WebSocket
endpoint and `ipc` for the unix socket (Unix) or named pipe (Windows) endpoint).

For example: `gsym --ipcapi admin,sym --rpcapi sym,web3 --rpc`

* Enables the admin and official sym API over the IPC interface
* Enables the official sym and web3 API over the HTTP interface

The HTTP RPC interface must be explicitly enabled using the `--rpc` flag.

Please note, offering an API over the HTTP (`rpc`) or WebSocket (`ws`) interfaces will give everyone
access to the APIs who can access this interface (DApps, browser tabs, etc). Be careful which APIs
you enable. By default Gsym enables all APIs over the IPC (`ipc`) interface and only the  `sym`,
`net` and `web3` APIs over the HTTP and WebSocket interfaces.

To determine which APIs an interface provides, the `modules` JSON-RPC method can be invoked. For
example over an `ipc` interface on unix systems:

```
echo '{"jsonrpc":"2.0","method":"rpc_modules","params":[],"id":1}' | nc -U $datadir/gsym.ipc
```

will give all enabled modules including the version number:

```
{  
   "id":1,
   "jsonrpc":"2.0",
   "result":{  
      "admin":"1.0",
      "citizen":"1.0",
      "sym":"1.0",
      "net":"1.0",
      "personal":"1.0",
      "txpool":"1.0",
      "warrant":"1.0",
      "web3":"1.0"
   }
}
```

## Consuming the management APIs

These additional APIs follow the same conventions as the official RPC APIs. Web3 can be
[extended](https://github.com/ethereum/web3.js/pull/229) and used to consume these additional APIs. 

The different functions are split into multiple smaller logically grouped APIs. Examples are given
for the [JavaScript console](https://github.com/symverse-lab/Document/blob/master/Doc-APIs/JavaScriptConsole.md) but can easily be converted to an RPC request.

**example:** 

- Console: `admin.stopRPC()`
- IPC: `echo '{"jsonrpc":"2.0","method":"admin_stopRPC","params":[],"id":1}' | nc -U $datadir/gsym.ipc`
- HTTP: `curl -X POST --data '{"jsonrpc":"2.0","method":"admin_stopRPC","params":[],"id":74}' localhost:8545`



## List of management APIs

Beside the officially exposed official RPC API namespaces (`citizen`, `sym`, `warrant`,`web3`), Gsym provides the following extra management API namespaces:

* `admin`: Gsym node management
* `personal`: Account management
* `txpool`: Transaction pool inspection

| [admin](#admin)              | [personal](#personal)  | [txpool](#txpool) |
| :--------------------------- | :---------------------------------- | ----------------------------------- |
| [addPeer](#admin_addpeer)    | [importRawKey](#personal_importrawkey) | [content](#txpool_content) |
| [datadir](#datadir)          | [listAccounts](#personal_listaccounts) | [inspect](#txpool_inspect) |
| [nodeInfo](#admin_nodeinfo)  | [lockAccount](#personal_lockaccount) | [status](#txpool_status) |
| [peers](#admin_peers)        | [newAccount](#personal_newaccount) |  |
| [startRPC](#admin_startrpc) | [newSymAccount](#personal_newsymaccount) |  |
| [startWS](#admin_startws)   | [unlockAccount](#personal_unlockaccount) |  |
| [stopRPC](#admin_stoprpc) | [sendTransaction](#personal_sendtransaction) |  |
| [stopWS](#admin_stopws)     |  |  |



## Admin

The `admin` API gives you access to several non-standard RPC methods, which will allow you to have
a fine grained control over your Gsym instance, including but not limited to network peer and RPC
endpoint management.

### admin_addPeer

The `addPeer` administrative method requests adding a new remote node to the list of tracked static
nodes. The node will try to maintain connectivity to these nodes at all times, reconnecting every
once in a while if the remote connection goes down.

The method accepts a single argument, the [`enode`](https://github.com/ethereum/wiki/wiki/enode-url-format) URL of the remote peer to start tracking and returns a `BOOL` indicating whether the peer was accepted
for tracking or some error occurred.

| Client  | Method invocation                              |
|:-------:|------------------------------------------------|
| Go      | `admin.AddPeer(url string) (bool, error)`      |
| Console | `admin.addPeer(url)`                           |
| RPC     | `{"method": "admin_addPeer", "params": [url]}` |

#### Example

```javascript
> admin.addPeer("enode://a979fb575495b8d6db44f750317d0f4622bf4c2aa3365d6af7c284339968eef29b69ad0dce72a4d8db5ebb4968de0e3bec910127f134779fbcb0cb6d3331163c@52.16.188.185:30303")
true
```



### admin_datadir

The `datadir` administrative property can be queried for the absolute path the running Gsym node
currently uses to store all its databases.

| Client  | Method invocation                 |
|:-------:|-----------------------------------|
| Go      | `admin.Datadir() (string, error`) |
| Console | `admin.datadir`                   |
| RPC     | `{"method": "admin_datadir"}`     |

#### Example

```javascript
> admin.datadir
"/home/yunee/.symverse"
```

### admin_nodeInfo

The `nodeInfo` administrative property can be queried for all the information known about the running
Gsym node at the networking granularity. These include general information about the node itself as a
participant of the P2P overlay protocol, as well as specialized information added by each of the running application protocols (e.g. `sym`).

| Client  | Method invocation                         |
|:-------:|-------------------------------------------|
| Go      | `admin.NodeInfo() (*p2p.NodeInfo, error`) |
| Console | `admin.nodeInfo`                          |
| RPC     | `{"method": "admin_nodeInfo"}`            |

#### Example

```javascript
> admin.nodeInfo
{
  enode: "enode://ab71c0bb288c1a801bf0ffe4d76e6686ba79e45178e9b080d8a9ee26a69bbe2e9738d26c2f2d2d39a64a1c7e7bc1ef821e27338bc00529e965ec702e197ef5d9@[::]:2007?discport=0",
  id: "ab71c0bb288c1a801bf0ffe4d76e6686ba79e45178e9b080d8a9ee26a69bbe2e9738d26c2f2d2d39a64a1c7e7bc1ef821e27338bc00529e965ec702e197ef5d9",
  ip: "::",
  listenAddr: "[::]:2007",
  name: "Gsym/v0.0.7-Develope-44e71d31/linux-amd64/go1.10.4",
  ports: {
    discovery: 0,
    listener: 2007
  },
  protocols: {
    sym: {
      config: {
        chainId: 8131,
        masterCA: "0x00000000000000000801",
        oraclizer: "0x00000000000000000801"
      },
      genesis: "0xb8082b2f699d9f2bceb98b6f26bcd1891dad1b0df58c37b98d0061f675cc1c62",
      head: "0xeeb4b16557d2a594e9f0db0775b8f5a9c933dccc5d43de965bbdc691f3618ae0",
      network: 8131
    }
  }
}
```

### admin_peers

The `peers` administrative property can be queried for all the information known about the connected
remote nodes at the networking granularity. These include general information about the nodes themselves as participants of the P2P overlay protocol, as well as specialized information added by each of the running application protocols (e.g. `sym`).

| Client  | Method invocation                        |
|:-------:|------------------------------------------|
| Go      | `admin.Peers() ([]*p2p.PeerInfo, error`) |
| Console | `admin.peers`                            |
| RPC     | `{"method": "admin_peers"}`              |

#### Example

```javascript
> admin.peers
[{
    caps: ["sym/31"],
    id: "12af89114e7e6a98e6436afc91cc16990a3a8e4b07bf41fc549c4aa59da3ef50035a8bf2dc4f03da34b3cb309d963b8d0a822ba68f734e778724d7d29e8a8858",
    name: "Gsym/v0.0.7-Develope-44e71d31/linux-amd64/go1.10.4",
    network: {
      inbound: false,
      localAddress: "127.0.0.1:49434",
      remoteAddress: "127.0.0.1:2001",
      static: true,
      trusted: false
    },
    protocols: {
      sym: {
        blocknum: 6028,
        head: "0x17db02e5c80e239803516e0ecf88b7f019ef1ccce1d73a8cac16114c1dfbce98",
        version: 31
      }
    }
}, /* ... */ {
    caps: ["sym/31"],
    id: "f8a38bcf4123f7467be97628aedf817f92b40776a3beb0cf99a3831e12f429a045e8ec0dfb8a1d2e2783afc3e866a87f5a21c6cab52f30c0e136c8e3f4bc7128",
    name: "Gsym/v0.0.7-Develope-44e71d31/linux-amd64/go1.10.4",
    network: {
      inbound: true,
      localAddress: "127.0.0.1:2007",
      remoteAddress: "127.0.0.1:49548",
      static: false,
      trusted: false
    },
    protocols: {
      sym: {
        blocknum: 6030,
        head: "0x1fd492c192a954f6e874961e16bbd01de2b27a8690f9b0b1feaf3e4c17af5372",
        version: 31
      }
    }
}]
```

### admin_startRPC

The `startRPC` administrative method starts an HTTP based [JSON RPC](http://www.jsonrpc.org/specification)
API webserver to handle client requests. All the parameters are optional:

* `host`: network interface to open the listener socket on (defaults to `"localhost"`)
* `port`: network port to open the listener socket on (defaults to `8545`)
* `cors`: [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) header to use (defaults to `""`)
* `apis`: API modules to offer over this interface (defaults to `"sym,net,web3"`)

The method returns a boolean flag specifying whether the HTTP RPC listener was opened or not. Please note, only one HTTP endpoint is allowed to be active at any time.

| Client  | Method invocation                                                                             |
|:-------:|-----------------------------------------------------------------------------------------------|
| Go      | `admin.StartRPC(host *string, port *rpc.HexNumber, cors *string, apis *string) (bool, error)` |
| Console | `admin.startRPC(host, port, cors, apis)`                                                      |
| RPC     | `{"method": "admin_startRPC", "params": [host, port, cors, apis]}`                            |

#### Example

```javascript
> admin.startRPC("127.0.0.1", 8545)
true
```

### admin_startWS

The `startWS` administrative method starts an WebSocket based [JSON RPC](http://www.jsonrpc.org/specification)
API webserver to handle client requests. All the parameters are optional:

* `host`: network interface to open the listener socket on (defaults to `"localhost"`)
* `port`: network port to open the listener socket on (defaults to `8546`)
* `cors`: [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) header to use (defaults to `""`)
* `apis`: API modules to offer over this interface (defaults to `"sym,net,web3"`)

The method returns a boolean flag specifying whether the WebSocket RPC listener was opened or not. Please note, only one WebSocket endpoint is allowed to be active at any time.

| Client  | Method invocation                                                                             |
|:-------:|-----------------------------------------------------------------------------------------------|
| Go      | `admin.StartWS(host *string, port *rpc.HexNumber, cors *string, apis *string) (bool, error)` |
| Console | `admin.startWS(host, port, cors, apis)`                                                      |
| RPC     | `{"method": "admin_startWS", "params": [host, port, cors, apis]}`                            |

#### Example

```javascript
> admin.startWS("127.0.0.1", 8546)
true
```

### admin_stopRPC

The `stopRPC` administrative method closes the currently open HTTP RPC endpoint. As the node can only have a single HTTP endpoint running, this method takes no parameters, returning a boolean whether the endpoint was closed or not.

| Client  | Method invocation                           |
| :-----: | ------------------------------------------- |
|   Go    | `admin.StopRPC() (bool, error`)             |
| Console | `admin.stopRPC()`                           |
|   RPC   | `{"method": "admin_stopRPC", "params": []}` |

#### Example

```javascript
> admin.stopRPC()
true
```

### admin_stopWS

The `stopWS` administrative method closes the currently open WebSocket RPC endpoint. As the node can only have a single WebSocket endpoint running, this method takes no parameters, returning a boolean whether the endpoint was closed or not.

| Client  | Method invocation                          |
| :-----: | ------------------------------------------ |
|   Go    | `admin.StopWS() (bool, error`)             |
| Console | `admin.stopWS()`                           |
|   RPC   | `{"method": "admin_stopWS", "params": []}` |

#### Example

```javascript
> admin.stopWS()
true
```


## Personal

The personal API manages private keys in the key store.

### personal_importRawKey

Imports the given unencrypted private key (hex string) into the key store,
encrypting it with the passphrase.

Returns the address of the new account.

| Client    | Method invocation                                                 |
| :-------: | ----------------------------------------------------------------- |
| Console   | `personal.importRawKey(keydata, passphrase)`                      |
| RPC       | `{"method": "personal_importRawKey", "params": [string, string]}` |

### personal_listAccounts

Returns all the Symverse account addresses of all keys
in the key store.

| Client    | Method invocation                                   |
| :-------: | --------------------------------------------------- |
| Console   | `personal.listAccounts`                             |
| RPC       | `{"method": "personal_listAccounts", "params": []}` |

#### Example

``` javascript
> personal.listAccounts
["0x00000000000000000901","0x00010000000000010009"]
```

### personal_lockAccount

Removes the private key with given address from memory.
The account can no longer be used to send transactions.

| Client    | Method invocation                                        |
| :-------: | -------------------------------------------------------- |
| Console   | `personal.lockAccount(address)`                          |
| RPC       | `{"method": "personal_lockAccount", "params": [string]}` |

### personal_newAccount

Generates new private keys and stores them in the key store directory. 
The key ﬁle is encrypted with a given passphrase. 
Returns the SymID of the new account.

At the gsym console, `newAccount` will prompt for SymID and a passphrase when
it is not provided in the argument.

| Client  | Method invocation                                            |
| :-----: | ------------------------------------------------------------ |
| Console | `personal.newAccount()`                                      |
|   RPC   | `{"method": "personal_newAccount", "params": [address,string]}` |

#### Example

```javascript
>  personal.newAccount()
Sym ID: 0x00010000000000010003
Passphrase:
Repeat passphrase:
"0x00010000000000010003"
```

The passphrase can also be supplied as a string.

```javascript
> personal.newAccount("0x00010000000000010003","yunee")
"0x00010000000000010003"
```

### personal_unlockAccount

Decrypts the key with the given address from the key store.

Both passphrase and unlock duration are optional when using the JavaScript console.
If the passphrase is not supplied as an argument, the console will prompt for
the passphrase interactively.

The unencrypted key will be held in memory until the unlock duration expires.
If the unlock duration defaults to 300 seconds. An explicit duration
of zero seconds unlocks the key until gsym exits.

The account can be used with `sym_sign` and `sym_sendTransaction` while it is unlocked.

| Client    | Method invocation                                                          |
| :-------: | -------------------------------------------------------------------------- |
| Console   | `personal.unlockAccount(address, passphrase, duration)`                    |
| RPC       | `{"method": "personal_unlockAccount", "params": [string, string, number]}` |

#### Examples

``` javascript
> personal.unlockAccount("0x00000000000000000901")
Unlock account 0x00000000000000000901
Passphrase:
true
```

Supplying the passphrase and unlock duration as arguments:

``` javascript
> personal.unlockAccount("0x00000000000000000901","yunee",30)
true
```

If you want to type in the passphrase and stil override the default unlock duration,
pass `null` as the passphrase.

```javascript
> personal.unlockAccount("0x00000000000000000901",null,30)
Unlock account 0x00000000000000000901
Passphrase:
true
```

### personal_sendTransaction

Validate the given passphrase and submit transaction.

The transaction is the same argument as for `sym_sendTransaction` and contains the `from` address. If the passphrase can be used to decrypt the private key belogging to `tx.from` the transaction is verified, signed and send onto the network. The account is not unlocked globally in the node and cannot be used in other RPC calls.

| Client    | Method invocation                                                |
| :-------: | -----------------------------------------------------------------|
| Console   | `personal.sendTransaction(tx, passphrase)`                       |
| RPC       | `{"method": "personal_sendTransaction", "params": [tx, string]}` |

#### Examples

``` javascript
> var tx = {from: "0x00000000000000000901", to: "0x00010000000000010003", value: web3.toHug(920920, "sym")}
undefined
> personal.sendTransaction(tx, "passphrase")
0x8474441674cdd47b35b875fd1a530b800b51a5264b9975fb21129eeb8c18582f
```

## Txpool

The `txpool` API gives you access to several non-standard RPC methods to inspect the contents of the
transaction pool containing all the currently pending transactions as well as the ones queued for
future processing.

### txpool_content

The `content` inspection property can be queried to list the exact details of all the transactions
currently pending for inclusion in the next block(s), as well as the ones that are being scheduled
for future execution only.

The result is an object with two fields `pending` and `queued`. Each of these fields are associative
arrays, in which each entry maps an origin-address to a batch of scheduled transactions. These batches
themselves are maps associating nonces with actual transactions.

Please note, there may be multiple transactions associated with the same account and nonce. This can
happen if the user broadcast mutliple ones with varying gas allowances (or even complerely different
transactions).

| Client  | Method invocation                                            |
| :-----: | ------------------------------------------------------------ |
|   Go    | `txpool.Content() (map[string]map[string]map[string][]*RPCTransaction)` |
| Console | `txpool.content`                                             |
|   RPC   | `{"method": "txpool_content"}`                               |

#### Example

```javascript
> txpool.content
{
  pending: {
     0x00000000000000000401: {
      0: {
        blockHash: "0x0000000000000000000000000000000000000000000000000000000000000000",
        blockNumber: null,
        from: "0x00000000000000000401",
        gas: "0x15f90",
        gasPrice: "0x430e23400",
        hash: "0x7db76e4b4e342c940e2de044a61704e2df8c3b3f3f29f3a45094c5c62c90e889",
        input: "0x",
        nonce: "0x0",
        r: "0x6cd17c232184b39a9c7527fcd3b198cfd127ec71730af022f2926267e78ff154",
        s: "0x8b819fe36540a0ae4aafdbdc4d7308d3065c2f74d5790fc343685db26cb8b19",
        to: "0x00000000000000000901",
        transactionIndex: "0x0",
        type: "0x0",
        v: "0x1",
        value: "0xde0b6b3a7640000",
        workNodes: [...]
      },
    0x00000000000000000501:   
     9: {
        blockHash: "0x0000000000000000000000000000000000000000000000000000000000000000",
        blockNumber: null,
        from: "0x00000000000000000501",
        gas: "0x15f90",
        gasPrice: "0x430e23400",
        hash: "0x4c661f9a520b3675da93e9c7b8027cb60ccd31be2f50555ed76dd439b7972a5f",
        input: "0x",
        nonce: "0x9",
        r: "0xea69651392676698f4a1758bd531164bdb37a2200df6e60a76e467d9920489ee",
        s: "0x465e4314ef26341fecb2e55cdb24c2a1e8100666cdd9c39abebc24ccf2297590",
        to: "0x00000000000000000901",
        transactionIndex: "0x0",
        type: "0x0",
        v: "0x0",
        value: "0xde0b6b3a7640000",
        workNodes: [...]
      }
    }
  },
   queued: {
    0x00000000000000000201: {
      50005: {
        blockHash: "0x0000000000000000000000000000000000000000000000000000000000000000",
        blockNumber: null,
        from: "0x00000000000000000201",
        gas: "0x15f90",
        gasPrice: "0x430e23400",
        hash: "0xa7e10ad03086957049f9583d6d2b3f4e72476bb1362918aa1326601ab1c8880a",
        input: "0x",
        nonce: "0xc355",
        r: "0xc1143ab8428d1c7470a1f9f599a616bb05698ed7aa60b030f1bacb310ea09bf4",
        s: "0x5ffcdbd272b7bc1e0e4b7aaca4f01187f24e8bc7c0b5c100d8cd33115483f1b",
        to: "0x00000000000000000901",
        transactionIndex: "0x0",
        type: "0x0",
        v: "0x0",
        value: "0xde0b6b3a7640000",
        workNodes: [...]
      },{
        blockHash: "0x0000000000000000000000000000000000000000000000000000000000000000",
        blockNumber: null,
        from: "0x00000000000000000201",
        gas: "0x15f90",
        gasPrice: "0x430e23400",
        hash: "0x7960f26a2b360e158f9bd39611cd86ddb44d8df67c8015a66fb78b69dd463542",
        input: "0x",
        nonce: "0xc355",
        r: "0x5834553ba95cba6e3869fed958a444c9a22c3fc0409d14b3d42341ce378b30a6",
        s: "0x4a5288cbbc232b0b44ab0836ab4821e7a995dbc77855d41d1b3909fada07cdca",
        to: "0x00000000000000001001",
        transactionIndex: "0x0",
        type: "0x0",
        v: "0x1",
        value: "0xde0b6b3a7640000",
        workNodes: [...]
      }
    }
  }
}
```

### txpool_inspect

The `inspect` inspection property can be queried to list a textual summary of all the transactions
currently pending for inclusion in the next block(s), as well as the ones that are being scheduled
for future execution only. This is a method specifically tailored to developers to quickly see the
transactions in the pool and find any potential issues.

The result is an object with two fields `pending` and `queued`. Each of these fields are associative
arrays, in which each entry maps an origin-address to a batch of scheduled transactions. These batches
themselves are maps associating nonces with transactions summary strings.

Please note, there may be multiple transactions associated with the same account and nonce. This can
happen if the user broadcast mutliple ones with varying gas allowances (or even complerely different
transactions).

| Client  | Method invocation                                            |
| :-----: | ------------------------------------------------------------ |
|   Go    | `txpool.Inspect() (map[string]map[string]map[string][]string)` |
| Console | `txpool.inspect`                                             |
|   RPC   | `{"method": "txpool_inspect"}`                               |

#### Example

```javascript
> txpool.inspect
{
  pending: {
    0x00021000000000150002: {
      31813: ["0x00021000000000040002: 0 hug + 500000 × 20000000000 gas"]
    },
    0x00021000000000190002: {
      563662: ["0x00021000000000020002: 1051546810000000000 hug + 90000 × 20000000000 gas"],
      563663: ["0x00021000000000240002: 1051190740000000000 hug + 90000 × 20000000000 gas"],
      563664: ["0x00021000000000240002: 1050828950000000000 hug + 90000 × 20000000000 gas"],
      563665: ["0x00021000000000280002: 1050544770000000000 hug + 90000 × 20000000000 gas"]
    },
    0x00021000000000210002: {
      3: ["0x00021000000000240002: 30000000000000000000 hug + 85000 × 21000000000 gas"]
    },
    0x00021000000000280002: {
      777: ["0x00021000000000240002: 0 hug + 1000000 × 20000000000 gas"]
    },
    0x00021000000000290002: {
      2: ["0x00021000000000240002: 26000000000000000000 hug + 90000 × 20000000000 gas", "0x00021000000000310002: 26000000000000000000 hug + 90000 × 20000000000 gas"]
    },
    0x00021000000000310002: {
      0: ["0x00021000000000240002: 1000000000000000000 hug + 50000 × 1171602790622 gas"]
    }
  },
  queued: {
    0x00021000000000010002: {
      6: ["0x00021000000000240002: 9000000000000000000 hug + 21000 × 20000000000 gas"]
    },
    0x00021000000000030002: {
      6: ["0x00021000000000240002: 50000000000000000000 hug + 90000 × 50000000000 gas"]
    },
    0x00021000000000050002: {
      3: ["0x00021000000000240002: 140000000000000000 hug + 90000 × 20000000000 gas"]
    },
    0x00021000000000090002: {
      2: ["0x00021000000000010002: 17000000000000000000 hug + 90000 × 50000000000 gas"],
      6: ["0x00021000000000050002: 17990000000000000000 hug + 90000 × 20000000000 gas", "0x00021000000000070002: 16998950000000000000 hug + 90000 × 20000000000 gas"],
      7: ["0x00021000000000240002: 17900000000000000000 hug + 90000 × 20000000000 gas"]
    }
  }
}
```

### txpool_status

The `status` inspection property can be queried for the number of transactions currently pending for
inclusion in the next block(s), as well as the ones that are being scheduled for future execution only.

The result is an object with two fields `pending` and `queued`, each of which is a counter representing
the number of transactions in that particular state.

| Client  | Method invocation                             |
| :-----: | --------------------------------------------- |
|   Go    | `txpool.Status() (map[string]*rpc.HexNumber)` |
| Console | `txpool.status`                               |
|   RPC   | `{"method": "txpool_status"}`                 |

#### Example

```javascript
> txpool.status
{
  pending: 10,
  queued: 7
}
```

## Debug

The `debug` API gives you access to several non-standard RPC methods, which will allow you to inspect,
debug and set certain debugging flags during runtime.



**The `debug` API is in preparation and will be updated in the near future.**