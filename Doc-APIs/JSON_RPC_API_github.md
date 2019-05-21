<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents** 

- [JSON RPC API](#json-rpc-api)
  - [JavaScript API](#javascript-api)
  - [JSON-RPC Endpoint](#json-rpc-endpoint)
  - [Output HEX values](#output-hex-values)
  - [The default block parameter](#the-default-block-parameter)
  - [Curl Examples Explained](#curl-examples-explained)
  - [JSON-RPC methods](#json-rpc-methods)
  - [JSON RPC API Reference](#json-rpc-api-reference)
      - [web3_clientVersion](#web3_clientversion)
        - [Parameters](#parameters)
        - [Returns](#returns)
        - [Example](#example)
      - [web3_sha3](#web3_sha3)
        - [Parameters](#parameters-1)
        - [Returns](#returns-1)
        - [Example](#example-1)
      - [net_version](#net_version)
        - [Parameters](#parameters-2)
        - [Returns](#returns-2)
        - [Example](#example-2)
      - [net_listening](#net_listening)
        - [Parameters](#parameters-3)
        - [Returns](#returns-3)
        - [Example](#example-3)
      - [net_peerCount](#net_peercount)
        - [Parameters](#parameters-4)
        - [Returns](#returns-4)
        - [Example](#example-4)
      - [sym_protocolVersion](#sym_protocolversion)
        - [Parameters](#parameters-5)
        - [Returns](#returns-5)
        - [Example](#example-5)
      - [sym_syncing](#sym_syncing)
        - [Parameters](#parameters-6)
        - [Returns](#returns-6)
        - [Example](#example-6)
      - [sym_symbase](#sym_symbase)
        - [Parameters](#parameters-7)
        - [Returns](#returns-7)
        - [Example](#example-7)
      - [sym_gasPrice](#sym_gasprice)
        - [Parameters](#parameters-8)
        - [Returns](#returns-8)
        - [Example](#example-8)
      - [sym_accounts](#sym_accounts)
        - [Parameters](#parameters-9)
        - [Returns](#returns-9)
        - [Example](#example-9)
      - [sym_blockNumber](#sym_blocknumber)
        - [Parameters](#parameters-10)
        - [Returns](#returns-10)
        - [Example](#example-10)
      - [sym_getBalance](#sym_getbalance)
        - [Parameters](#parameters-11)
        - [Returns](#returns-11)
        - [Example](#example-11)
      - [sym_getTransactionCount](#sym_gettransactioncount)
        - [Parameters](#parameters-12)
        - [Returns](#returns-12)
        - [Example](#example-12)
      - [sym_getBlockTransactionCountByHash](#sym_getblocktransactioncountbyhash)
        - [Parameters](#parameters-13)
        - [Returns](#returns-13)
        - [Example](#example-13)
      - [sym_getBlockTransactionCountByNumber](#sym_getblocktransactioncountbynumber)
        - [Parameters](#parameters-14)
        - [Returns](#returns-14)
        - [Example](#example-14)
      - [sym_getCode](#sym_getcode)
        - [Parameters](#parameters-15)
        - [Returns](#returns-15)
        - [Example](#example-15)
      - [sym_sign](#sym_sign)
        - [Parameters](#parameters-16)
        - [Returns](#returns-16)
        - [Example](#example-16)
      - [sym_sendTransaction](#sym_sendtransaction)
        - [Parameters](#parameters-17)
        - [Returns](#returns-17)
        - [Example](#example-17)
      - [sym_sendRawTransaction](#sym_sendrawtransaction)
        - [Parameters](#parameters-18)
        - [Returns](#returns-18)
        - [Example](#example-18)
      - [sym_call](#sym_call)
        - [Parameters](#parameters-19)
        - [Returns](#returns-19)
        - [Example](#example-19)
      - [sym_estimateGas](#sym_estimategas)
        - [Parameters](#parameters-20)
        - [Returns](#returns-20)
        - [Example](#example-20)
      - [sym_getBlockByHash](#sym_getblockbyhash)
        - [Parameters](#parameters-21)
        - [Returns](#returns-21)
        - [Example](#example-21)
      - [sym_getBlockByNumber](#sym_getblockbynumber)
        - [Parameters](#parameters-22)
        - [Returns](#returns-22)
        - [Example](#example-22)
      - [sym_getTransactionByHash](#sym_gettransactionbyhash)
        - [Parameters](#parameters-23)
        - [Returns](#returns-23)
        - [Example](#example-23)
      - [sym_getTransactionByBlockHashAndIndex](#sym_gettransactionbyblockhashandindex)
        - [Parameters](#parameters-24)
        - [Returns](#returns-24)
        - [Example](#example-24)
      - [sym_getTransactionByBlockNumberAndIndex](#sym_gettransactionbyblocknumberandindex)
        - [Parameters](#parameters-25)
        - [Returns](#returns-25)
        - [Example](#example-25)
      - [sym_getTransactionReceipt](#sym_gettransactionreceipt)
        - [Parameters](#parameters-26)
        - [Returns](#returns-26)
        - [Example](#example-26)
      - [sym_getDeposit](#sym_getdeposit)
        - [Parameters](#parameters-27)
        - [Returns](#returns-27)
        - [Example](#example-27)
      - [warrant_blockNumber](#warrant_blocknumber)
        - [Parameters](#parameters-28)
        - [Returns](#returns-28)
        - [Example](#example-28)
      - [warrant_getWarrantsByBlockHash](#warrant_getwarrantsbyblockhash)
        - [Parameters](#parameters-29)
        - [Returns](#returns-29)
        - [Example](#example-29)
      - [warrant_getWarrantsByBlockNumber](#warrant_getwarrantsbyblocknumber)
        - [Parameters](#parameters-30)
        - [Returns](#returns-30)
        - [Example](#example-30)
      - [warrant_getBlockByHash](#warrant_getblockbyhash)
        - [Parameters](#parameters-31)
        - [Returns](#returns-31)
        - [Example](#example-31)
      - [warrant_getBlockByNumber](#warrant_getblockbynumber)
        - [Parameters](#parameters-32)
        - [Returns](#returns-32)
        - [Example](#example-32)
      - [citizen_sendCitizen](#citizen_sendcitizen)
        - [Parameters](#parameters-33)
        - [Returns](#returns-33)
        - [Example](#example-33)
      - [citizen_sendRawCitizen](#citizen_sendrawcitizen)
        - [Parameters](#parameters-34)
        - [Returns](#returns-34)
        - [Example](#example-34)
      - [citizen_getCitizenByHash](#citizen_getcitizenbyhash)
        - [Parameters](#parameters-35)
        - [Returns](#returns-35)
        - [Example](#example-35)
      - [citizen_getRawCitizenByHash](#citizen_getrawcitizenbyhash)
        - [Parameters](#parameters-36)
        - [Returns](#returns-36)
        - [Example](#example-36)
      - [citizen_getCitizenBySymID](#citizen_getcitizenbysymid)
        - [Parameters](#parameters-37)
        - [Returns](#returns-37)
        - [Example](#example-37)
      - [citizen_getRawCitizenBySymID](#citizen_getrawcitizenbysymid)
        - [Parameters](#parameters-38)
        - [Returns](#returns-38)
        - [Example](#example-38)
      - [citizen_getCitizensByBlockNumber](#citizen_getcitizensbyblocknumber)
        - [Parameters](#parameters-39)
        - [Returns](#returns-39)
        - [Example](#example-39)
      - [citizen_getStatus](#citizen_getstatus)
        - [Parameters](#parameters-40)
        - [Returns](#returns-40)
        - [Example](#example-40)
      - [citizen_getCitizenCountFromPool](#citizen_getcitizencountfrompool)
        - [Parameters](#parameters-41)
        - [Returns](#returns-41)
        - [Example](#example-41)
      - [citizen_pendings](#citizen_pendings)
        - [Parameters](#parameters-42)
        - [Returns](#returns-42)
        - [Example](#example-42)
      - [citizen_blockNumber](#citizen_blocknumber)
        - [Parameters](#parameters-43)
        - [Returns](#returns-43)
        - [Example](#example-43)
      - [citizen_getBlockByHash](#citizen_getblockbyhash)
        - [Parameters](#parameters-44)
        - [Returns](#returns-44)
        - [Example](#example-44)
      - [citizen_getBlockByNumber](#citizen_getblockbynumber)
        - [Parameters](#parameters-45)
        - [Returns](#returns-45)
        - [Example](#example-45)
      - [citizen_getIssuer](#citizen_getissuer)
        - [Parameters](#parameters-46)
        - [Returns](#returns-46)
        - [Example](#example-46)
      - [citizen_getRole](#citizen_getrole)
        - [Parameters](#parameters-47)
        - [Returns](#returns-47)
        - [Example](#example-47)
      - [citizen_getBlockCitizenCountByHash](#citizen_getblockcitizencountbyhash)
        - [Parameters](#parameters-48)
        - [Returns](#returns-48)
        - [Example](#example-48)
      - [citizen_getBlockCitizenCountByNumber](#citizen_getblockcitizencountbynumber)
        - [Parameters](#parameters-49)
        - [Returns](#returns-49)
        - [Example](#example-49)
      - [sct_getContract](#sct_getcontract)
        - [Parameters](#parameters-50)
        - [Returns](#returns-50)
        - [Example](#example-50)
      - [sct_getContractItem](#sct_getcontractitem)
        - [Parameters](#parameters-51)
        - [Returns](#returns-51)
        - [Example](#example-51)
      - [sct_getContractAccount](#sct_getcontractaccount)
        - [Parameters](#parameters-52)
        - [Returns](#returns-52)
        - [Example](#example-52)
      - [sct_getAllowance](#sct_getallowance)
        - [Parameters](#parameters-53)
        - [Returns](#returns-53)
        - [Example](#example-53)
      - [sct_getContractItemsByCategory](#sct_getcontractitemsbycategory)
        - [Parameters](#parameters-54)
        - [Returns](#returns-54)
        - [Example](#example-54)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# JSON RPC API

[JSON](http://json.org/) is a lightweight data-interchange format. It can represent numbers, strings, ordered sequences of values, and collections of name/value pairs.

[JSON-RPC](http://www.jsonrpc.org/specification) is a stateless, light-weight remote procedure call (RPC) protocol. Primarily this specification defines several data structures and the rules around their processing. It is transport agnostic in that the concepts can be used within the same process, over sockets, over HTTP, or in many various message passing environments. It uses JSON ([RFC 4627](http://www.ietf.org/rfc/rfc4627.txt)) as data format.

**go-symverse** supports `JSON-RPC 2.0`



## JavaScript API

To talk to an symverse node from inside a JavaScript application use the [web3.js](https://github.com/ethereum/web3.js)library and additional API library, which we offered. 

the library gives an convenient interface for the RPC methods. See the [JavaScript API](우리 API페이지로 링크) for more. 



## JSON-RPC Endpoint

Default JSON-RPC endpoints:

```
C++: http://localhost:8545
```

You can start the HTTP JSON-RPC with the `--rpc` flag

```bash
gsym --rpc
```

change the default port (8545) and listing address (localhost) with:

```bash
gsym --rpc --rpcaddr <ip> --rpcport <portnumber>
```

If accessing the RPC from a browser, CORS will need to be enabled with the appropriate domain set. Otherwise, JavaScript calls are limit by the same-origin policy and requests will fail:

```bash
gsym --rpc --rpccorsdomain "http://localhost:3000"
```

The JSON RPC can also be started from the gsym console using the `admin.startRPC(addr, port)` command.



## Output HEX values

At present there are two key datatypes that are passed over JSON: unformatted byte arrays and quantities. Both are passed with a hex encoding, however with different requirements to formatting:

When encoding **QUANTITIES** (integers, numbers): encode as hex, prefix with "0x", the most compact representation (slight exception: zero should be represented as "0x0"). Examples:

- 0x41 (65 in decimal)
- 0x400 (1024 in decimal)
- WRONG: 0x (should always have at least one digit - zero is "0x0")
- WRONG: 0x0400 (no leading zeroes allowed)
- WRONG: ff (must be prefixed 0x)

When encoding **UNFORMATTED DATA** (byte arrays, account addresses, hashes, bytecode arrays): encode as hex, prefix with "0x", two hex digits per byte. Examples:

- 0x41 (size 1, "A")
- 0x004200 (size 3, "\0B\0")
- 0x (size 0, "")
- WRONG: 0xf0f0f (must be even number of digits)
- WRONG: 004200 (must be prefixed 0x)

Currently **go-symverse** provides JSON-RPC communication only over http.



## The default block parameter

Some  methods have a extra default block parameter.

The following options are possible for the defaultBlock parameter:

- `HEX String` - an integer block number

- `String "earliest"` for the earliest/genesis block

- `String "latest"` - for the latest mined block

- `String "pending"` - for the pending state/transactions

  

## Curl Examples Explained

The curl options below might return a response where the node complains about the content type, this is because the --data option sets the content type to application/x-www-form-urlencoded . If your node does complain, manually set the header by placing -H "Content-Type: application/json" at the start of the call.

The examples also do not include the URL/IP & port combination which must be the last argument given to curl e.x. 127.0.0.1:8545



## JSON-RPC methods

- [web3_clientVersion](#web3_clientversion)
- [web3_sha3](#web3_sha3)
- [net_version](#net_version)
- [net_peerCount](#net_peercount)
- [net_listening](#net_listening)
- [sym_protocolVersion](#sym_protocolversion)
- [sym_syncing](#sym_syncing)
- [sym_symbase](#sym_symbase)
- [sym_gasPrice](#sym_gasprice)
- [sym_accounts](#sym_accounts)
- [sym_blockNumber](#sym_blocknumber)
- [sym_getBalance](#sym_getbalance)
- [sym_getStorageAt](#sym_getstorageat)
- [sym_getTransactionCount](#sym_gettransactioncount)
- [sym_getBlockTransactionCountByHash](#sym_getblocktransactioncountbyhash)
- [sym_getBlockTransactionCountByNumber](#sym_getblocktransactioncountbynumber)
- [sym_getCode](#sym_getcode)
- [sym_sign](#sym_sign)
- [sym_sendTransaction](#sym_sendtransaction)
- [sym_sendRawTransaction](#sym_sendrawtransaction)
- [sym_call](#sym_call)
- [sym_estimateGas](#sym_estimategas)
- [sym_getBlockByHash](#sym_getblockbyhash)
- [sym_getBlockByNumber](#sym_getblockbynumber)
- [sym_getTransactionByHash](#sym_gettransactionbyhash)
- [sym_getTransactionByBlockHashAndIndex](#sym_gettransactionbyblockhashandindex)
- [sym_getTransactionByBlockNumberAndIndex](#sym_gettransactionbyblocknumberandindex)
- [sym_getTransactionReceipt](#sym_gettransactionreceipt)
- [sym_getDeposit](#sym_getdeposit)
- [warrant_blockNumber](#warrant_blocknumber)
- [warrant_getWarrantsByBlockHash](#warrant_getwarrantsbyblockhash)
- [warrant_getWarrantsByBlockNumber](#warrant_getwarrantsbyblocknumber)
- [warrant_getBlockByHash](#warrant_getblockbyhash)
- [warrant_getBlockByNumber](#warrant_getblockbynumber)
- [citizen_sendCitizen](#citizen_sendcitizen)
- [citizen_sendRawCitizen](#citizen_sendrawcitizen)
- [citizen_getCitizenByHash](#citizen_getcitizenbyhash)
- [citizen_getRawCitizenByHash](#citizen_getrawcitizenbyhash)
- [citizen_getCitizenBySymID](#citizen_getcitizenbysymid)
- [citizen_getRawCitizenBySymID](#citizen_getrawcitizenbysymid)
- [citizen_getCitizensByBlockNumber](#citizen_getcitizensbyblocknumber)
- [citizen_getStatus](#citizen_getstatus)
- [citizen_getCitizenCountFromPool](#citizen_getcitizencountfrompool)
- [citizen_getCitizenCountFromDb](#citizen_getcitizencountfromdb)
- [citizen_pendings](#citizen_pendings)
- [citizen_blockNumber](#citizen_blocknumber)
- [citizen_getBlockByHash](#citizen_getblockbyhash)
- [citizen_getBlockByNumber](#citizen_getblockbynumber)
- [citizen_getIssuer](#citizen_getissuer)
- [citizen_getRole](#citizen_getrole)
- [citizen_getBlockCitizenCountByHash](#citizen_getblockcitizencountbyhash)
- [citizen_getBlockCitizenCountByNumber](#citizen_getblockcitizencountbynumber)
- [sct_getContract](#sct_getcontract)
- [sct_getContractItem](#sct_getcontractitem)
- [sct_getContractAccount](#sct_getcontractaccount)
- [sct_getAllowance](#sct_getallowance)
- [sct_getContractItemsByCategory](#sct_getcontractitemsbycategory)



  

## JSON RPC API Reference

------

#### web3_clientVersion

Returns the current client version.

##### Parameters

none

##### Returns

`String` - The current client version.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc":"2.0",
  "result": "Gsym/v0.0.6-Develope-074c4306/linux-amd64/go1.10.4"
}
```

------

#### web3_sha3

Returns  the standardized SHA3-256 of the given data.

##### Parameters

1. `DATA` - the data to convert into a SHA3 hash.

```js
params: [
  "0x68656c6c6f20776f726c64"
]
```

##### Returns

`DATA` - The SHA3 result of the given string.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"web3_sha3","params":["0x68656c6c6f20776f726c64"],"id":64}'

// Result
{
  "id":64,
  "jsonrpc": "2.0",
  "result": "0x5b2c76da96136d193336fad3fbc049867b8ca157da22f69ae0e4923648250acc"
}
```

------

#### net_version

Returns the current network id.

##### Parameters

none

##### Returns

`String` - The current network id.

- `"1"`: Symverse Mainnet
- `"2"`: Testnet  

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"net_version","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc": "2.0",
  "result": "2"
}
```

------

#### net_listening

Returns `true` if client is actively listening for network connections.

##### Parameters

none

##### Returns

`Boolean` - `true` when listening, otherwise `false`.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"net_listening","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc":"2.0",
  "result":true
}
```

------

#### net_peerCount

Returns number of peers currently connected to the client.

##### Parameters

none

##### Returns

`QUANTITY` - integer of the number of connected peers.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":74}'

// Result
{
  "id":74,
  "jsonrpc": "2.0",
  "result": "0x2" // 2
}
```

------

#### sym_protocolVersion

Returns the current symverse protocol version.

##### Parameters

none

##### Returns

`String` - The current symverse protocol version.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_protocolVersion","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc": "2.0",
  "result": "0x40"
}
```

------

#### sym_syncing

Returns an object with data about the sync status or `false`.

##### Parameters

none

##### Returns

`Object|Boolean`, An object with sync status data or `FALSE`, when not syncing:

- `currentBlock`: `QUANTITY` - The current block, same as sym_blockNumber
- `startingBlock`: `QUANTITY` - The block at which the import started (will only be reset, after the sync reached his head)
- `highestBlock`: `QUANTITY` - The estimated highest block
- `pulledStates`: `QUANTITY` - Number of state trie entries already downloaded
- `knownStates`: `QUANTITY` - Total number of state trie entries known about

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_syncing","params":[],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": {
      startingBlock: "0x0", //0
      currentBlock: "0xe8", //232,
      highestBlock: "0x129", //297,
      pulledStates: "0x10", //16,
      knownStates: "0x10", //16,
  }
}
// Or when not syncing
{
  "id":1,
  "jsonrpc": "2.0",
  "result": false
}

```

------

#### sym_symbase

Returns the client coinbase address.

##### Parameters

none

##### Returns

`DATA`, 10 bytes - the current coinbase address.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_symbase","params":[],"id":64}'

// Result
{
  "id":64,
  "jsonrpc": "2.0",
  "result": "0x00000000000000001001"
}
```

------

#### sym_gasPrice

Returns the current price per gas in hug.

##### Parameters

none

##### Returns

`QUANTITY` - integer of the current gas price in hug.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_gasPrice","params":[],"id":73}'

// Result
{
  "id":73,
  "jsonrpc": "2.0",
  "result": "0x430e23400" // 18000000000
}
```

------

#### sym_accounts

Returns a list of addresses owned by client.

##### Parameters

none

##### Returns

`Array of DATA`, 10 Bytes - addresses owned by the client.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_accounts","params":[],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": ["0x00000000000000000901"]
}
```

------

#### sym_blockNumber

Returns the number of most recent block.

##### Parameters

none

##### Returns

`QUANTITY` - integer of the current block number the client is on.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_blockNumber","params":[],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xc94" // 1207
}
```

------

#### sym_getBalance

Returns the balance of the account of given address.

##### Parameters

1. `DATA`, 10 Bytes - address to check for balance.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```js
params: [
   '0x00000000000000001001',
   'latest'
]
```

##### Returns

`QUANTITY` - integer of the current balance in hug.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getBalance","params":["0x00000000000000001001", "latest"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x0234c8a3397aab58" // 158972490234375000
}
```

------

#### sym_getTransactionCount

Returns the number of transactions sent from an address.

##### Parameters

1. `DATA`, 10 Bytes - address.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```js
params: [
   '0x00000000000000001001',
   'latest' // state at the latest block
]
```

##### Returns

`QUANTITY` - integer of the number of transactions sent from this address.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getTransactionCount","params":["0x00000000000000001001","latest"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x1" // 1
}
```

------

#### sym_getBlockTransactionCountByHash

Returns the number of transactions in a block from a block matching the given block hash.

##### Parameters

1. `DATA`, 32 Bytes - hash of a block.

```js
params: [
   '0x442839b4c7d6ae3bfe52e02e5f1ecca75946b02fe6b721277ab3b5ef64d459db'
]
```

##### Returns

`QUANTITY` - integer of the number of transactions in this block.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getBlockTransactionCountByHash","params":["0x442839b4c7d6ae3bfe52e02e5f1ecca75946b02fe6b721277ab3b5ef64d459db"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xc" // 11
}
```

------

#### sym_getBlockTransactionCountByNumber

Returns the number of transactions in a block matching the given block number.

##### Parameters

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).

```js
params: [
   '0xe8', // 232
]
```

##### Returns

`QUANTITY` - integer of the number of transactions in this block.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getBlockTransactionCountByNumber","params":["0xe8"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xa" // 10
}
```

------

#### sym_getCode

Returns code at a given address.

##### Parameters

1. `DATA`, 10 Bytes - address.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter).

```js
params: [
   '0x00000000000000000901',
   '0x2'  // 2
]

```

##### Returns

`DATA` - the code from the given address.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getCode","params":["0x00000000000000000901", "0x2"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x"
}

```

------

#### sym_sign

The sign method calculates an Symverse specific signature with: `sign(sha256("\x19Symverse Signed Message:\n" + len(message) + message)))`.

By adding a prefix to the message makes the calculated signature recognisable as an Symverse specific signature. This prevents misuse where a malicious DApp can sign arbitrary data (e.g. transaction) and use the signature to impersonate the victim.

**Note** the address to sign with must be unlocked. 

##### Parameters

1. `DATA`, 10 Bytes - address.
2. `DATA`, N Bytes - message to sign.

##### Returns

`DATA`: Signature



##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_sign","params":["0x00000000000000000901", "0xdeadbeaf"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x55e5413cd051640f16b8a8c9659aef7357af5590ebcd51cdf10d3c866fd2ae3c14d9a9aa083f65e8d9a156f1dbea8e3dda72ee8736a4b810b9910c99875a03061c"
}

```

An example how to use solidity ecrecover to verify the signature calculated with `sym_sign` can be found [here](https://gist.github.com/bas-vk/d46d83da2b2b4721efb0907aecdb7ebd). The contract is deployed on the testnet Ropsten and Rinkeby.

------

#### sym_sendTransaction

Creates new message call transaction or a contract creation, if the data field contains code.

##### Parameters

1. `Object` - The transaction object

- `from`: `DATA`, 10 Bytes - the address the transaction is send from.
- `to`: `DATA`, 10 Bytes - (optional when creating new contract) the address the transaction is directed to.
- `gas`: `QUANTITY`  - (optional, default: 90000) integer of the gas provided for the transaction execution. It will return unused gas.
- `gasPrice`: `QUANTITY`  - (optional, default: To-Be-Determined) integer of the gasPrice used for each paid gas.
- `value`: `QUANTITY`  - (optional) integer of the value sent with this transaction.
- `type`:`QUANTITY`  - (optional, default: 0) type of the transaction(0: original, 1: sct, 2: deposit)
- `input`: `DATA`  - the compiled code of a contract OR the hash of the invoked method signature and encoded Parameters.
- `nonce`: `QUANTITY`  - (optional) integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.
- `worknodes`: `Array` - selected work node's SymID to send this transaction. (min: 1, max: 3)

```js
params: [{
    "from": "0x00000000000000000101",
    "to": "0x00000000000000000901",
    "gas": "0x76c0", 
	"gasPrice": "0x9184e72a000", 
    "value": "0x9184e72a"
}]

```

##### Returns

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [sym_getTransactionReceipt](#sym_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_sendTransaction","params":[{see above}],"id":100}'

// Result
{
  "id":100,
  "jsonrpc": "2.0",
  "result": "0x97719876eb686bcd5bd92f41d9646686c4240796c660f04a8d33f88bf6d26424"
}

```

------

#### sym_sendRawTransaction

Creates new message call transaction or a contract creation for signed transactions.

##### Parameters

1. `DATA`, The signed transaction data.

```js
params: ["0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"]

```

##### Returns

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [sym_getTransactionReceipt](#sym_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_sendRawTransaction","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"
}

```

------

#### sym_call

Executes a new message call immediately without creating a transaction on the block chain.

##### Parameters

1. `Object` - The transaction call object

- `from`: `DATA`, 10 Bytes - The address the transaction is sent from.
- `to`: `DATA`, 10 Bytes  - The address the transaction is directed to.
- `gas`: `QUANTITY`  - (optional) Integer of the gas provided for the transaction execution. sym_call consumes zero gas, but this parameter may be needed by some executions.
- `gasPrice`: `QUANTITY`  - (optional) Integer of the gasPrice used for each paid gas
- `value`: `QUANTITY`  - (optional) Integer of the value sent with this transaction
- `data`: `DATA`  - (optional) Hash of the method signature and encoded parameters. For details see [s\Symverse Contract ABI](https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI)

2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Returns

`DATA` - the return value of executed contract.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_call","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x0"
}

```

------

#### sym_estimateGas

Generates and returns an estimate of how much gas is necessary to allow the transaction to complete. The transaction will not be added to the blockchain. Note that the estimate may be significantly more than the amount of gas actually used by the transaction, for a variety of reasons including EVM mechanics and node performance.

##### Parameters

See [sym_call](#sym_call) parameters, expect that all properties are optional. If no gas limit is specified gsym uses the block gas limit from the pending block as an upper bound. As a result the returned estimate might not be enough to executed the call/transaction when the amount of gas is higher than the pending block gas limit.

##### Returns

`QUANTITY` - the amount of gas used.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_estimateGas","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x5208" // 21000
}

```

------

#### sym_getBlockByHash

Returns information about a main block, specified by the hash.

##### Parameters

1. `DATA`, 32 Bytes - Hash of a block.
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

```js
params: [
   '0xbc26bf7324c622b934da753d016768373032b8bbf5488f8be9ad5bbfafd2bd12',
   true
]

```

##### Returns

`Object` - A block object, or `null` when no block was found:

- `blockcreator` : `DATA` ,10 Bytes – address of the primary node. 
- `cihash` : `DATA` , 32 Bytes - hash of a citizen block which is created with the main block. null when it’s not created. 
- `cinum` : `QUANTITY` - latest citizen block number which is created with the main block. 
- `extraData`: `DATA` - the "extra data" field of this block.
- `gasLimit`: `QUANTITY` - the maximum gas allowed in this block.
- `gasUsed`: `QUANTITY` - the total used gas by all transactions in this block.
- `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
- `logsBloom`: `DATA`, 256 Bytes - the bloom filter for the logs of the block. `null` when its pending block.
- `number`: `QUANTITY` - the block number. `null` when its pending block.
- `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
- `receiptsRoot`: `DATA`, 32 Bytes - the root of the receipts trie of the block.
- `sctRoot`: `DATA`, 32 Bytes - the root of the final SCT's state trie of the block.
- `signature` : Object – signature of a block by primary node. 
- `size`: `QUANTITY` - integer the size of this block in bytes.
- `stateRoot`: `DATA`, 32 Bytes - the root of the final state trie of the block.
- `timestamp`: `QUANTITY` - the unix timestamp for when the block was collated.
- `transactions`: `Array` - array of transaction objects, or 32 Bytes transaction hashes depending on the last given parameter.
- `transactionsRoot`: `DATA`, 32 Bytes - the root of the transaction trie of the block.
- `verifier` : `Array` - array of each verifier node’s signature. 
- `vwbnum` :`QUANTITY` - warrant block number which is used for creating the block. 
- `wbhash` : `DATA` , 32 Bytes - hash of the warrant block which is created with the main block. null when it’s not created. 
- `wbnum` : `QUANTITY` - the warrant block number which is created with the main block. null when it’s not created.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getBlockByHash","params":["0x7f335503011fb5fad7cfdc20e08b8c5dd0edc9ce660d9dd4d4cbe7ff79dec363", true],"id":100}'

// Result
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "blockcreator": "0x00021000000000040002",
        "cihash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "cinum": "0x2",
        "extraData": "0xd507846773796d88676f312e31302e31856c696e7578",
        "gasLimit": "0x47e7c4",
        "gasUsed": "0x138be8",
        "hash": "0x7f335503011fb5fad7cfdc20e08b8c5dd0edc9ce660d9dd4d4cbe7ff79dec363",
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "number": "0x2328",
        "parentHash": "0xb8e800f0c995fef17f9409896271c94110739d1a8b70577952ffe9929ae02edc",
        "receiptsRoot": "0x8b4c66061d32afe366f3d3d36bc2aea7c27f2f990cb1d537263b9c32a102f4f3",
        "rewardRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "sctRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
        "signature": {
            "Num": 9000,
            "Sig": "0x246ecb6e607a06b5b5651ce9289e5a8bfd986df1afd15fa2f9e840d5c532a20e460ff6cea0494d8a29f933b935f708904929a10ce6a7d3dd6a3fc01198f21a1201"
        },
        "size": "0x22a8",
        "stateRoot": "0x3196f43468f6572f67083ad0d44e9f6c1b3dba63cad11eb18fcd92301b045a14",
        "timestamp": "0x5cdd52ca",
        "transactions": [
            {
                "blockHash": "0x7f335503011fb5fad7cfdc20e08b8c5dd0edc9ce660d9dd4d4cbe7ff79dec363",
                "blockNumber": "0x2328",
                "from": "0x00021000000000080002",
                "gas": "0x15f90",
                "gasPrice": "0x430e23400",
                "hash": "0x7e9bb72d6920032b46ac72e89f32ec7bd83b4d1fda9e02f03954b8418acccc15",
                "input": "0x",
                "nonce": "0x2573a",
                "to": "0x00021000000000090002",
                "transactionIndex": "0x0",
                "type": "0x0",
                "workNodes": [
                    "0x00021000000000080002"
                ],
                "value": "0xde0b6b3a7640000",
                "v": "0x1",
                "r": "0x47e7dbc63348c888a3c5a9aa32747eafa2ef211e1c8b1847674564d5875944ae",
                "s": "0x4e42c46cd3e5cca3a5061fa7719bcc140039d6320efd5baee8b77d9343f4e413"
            },
            {
                "blockHash": "0x7f335503011fb5fad7cfdc20e08b8c5dd0edc9ce660d9dd4d4cbe7ff79dec363",
                "blockNumber": "0x2328",
                "from": "0x00020000000000010002",
                "gas": "0x15f90",
                "gasPrice": "0x430e23400",
                "hash": "0xe78fa3c02bf80e11c99ad845f0e76c66780ac75ea1663139a54b292029a7570b",
                "input": "0x",
                "nonce": "0x1937d",
                "to": "0x00021000000000080002",
                "transactionIndex": "0x3c",
                "type": "0x0",
                "workNodes": [
                    "0x00020000000000010002"
                ],
                "value": "0xde0b6b3a7640000",
                "v": "0x1",
                "r": "0xfa6ad9aabc402350846e630a6f8f7b807534dc0ae4bc2b7b59d7c0a3d0378fb3",
                "s": "0x5cecf3c8138dbb73944beb121f425faa37fba12e21a9379d37e9633f11fd9847"
            }
        ],
        "transactionsRoot": "0x31bb23f629d617f2bbf867cfa2cadc1f4d0002f57324996f5344438330512222",
        "verifier": [
            {
                "SymID": "0x00021000000000030002",
                "SigOfItem": "0xee0b3da994d81fecb5335b37f632b679d57674bcf69fb54bc3fc42633ac9d2572c08a24e11beb40f3f19afede066073d15827fe6391b948d45276c8acf8da11e01"
            },
            {
                "SymID": "0x00021000000000070002",
                "SigOfItem": "0xe4384e37b0798df2ae7808a9f3bc4017375d3be3239c0bd5b3a2d31e6d7c10d41ffc5a9373ff6404b661d077984761ee0720c310272be76cf16d39eb416af2db00"
            },
            {
                "SymID": "0x00021000000000010002",
                "SigOfItem": "0xd993e18f8573ca12cfa65b8a297f5da2d781ac42d0349999d020fb021cd0a2a45c63c735cb7c482fe38d0f6f9d0b963d77a5d975c18c798a38e390018ccce7ec00"
            },
            {
                "SymID": "0x00021000000000050002",
                "SigOfItem": "0x8f71619f8761bcd02fcf19748b753ecb3775d39b6ad990bea47b6f5fd9f1b56408e6fdcc605b5f5ceb1dac5c0ebf8537eca56a33a54e174085743fafd022813401"
            },
            {
                "SymID": "0x00021000000000020002",
                "SigOfItem": "0x71fb67fe2b32086d6a79dfc731e6e1a62caaf4c696467c51f0b32713d75c52053eaa5084b7159beec3560a6a8d72a84307da4d7f0e03642d654f29a9c03dff4700"
            }
        ],
        "vwbnum": "0x383",
        "wbhash": "0xe715df10809874aa0a4619b97fd53188c2f959a6ce44b1c87e39e35ea6d10b47",
        "wbnum": "0x384"
    }
}
```

------

#### sym_getBlockByNumber

Returns information about a block by block number.

##### Parameters

1. `QUANTITY|TAG` - Integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

```js
params: [
   '0x1', // 1
   true
]

```

##### Returns

See [sym_getBlockByHash](#sym_getblockbyhash)

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getBlockByNumber","params":["0x1", true],"id":100}'

```

Result see [sym_getBlockByHash](#sym_getblockbyhash)

------

#### sym_getTransactionByHash

Returns information regarding transaction requested by transaction hash.

##### Parameters

1. `DATA`, 32 Bytes - Hash of a transaction

```js
params: [
   "0x3a646cbc8f7a2e05c6e0dafaa5ea600a93e72925a188706089a1b32d84090235"
]

```

##### Returns

`Object` - A transaction object, or `null` when no transaction was found:

- `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in. `null` when its pending.
- `blockNumber`: `QUANTITY` - block number where this transaction was in. `null` when its pending.
- `from`: `DATA`, 10 Bytes - address of the sender.
- `gas`: `QUANTITY` - gas provided by the sender.
- `gasPrice`: `QUANTITY` - gas price provided by the sender in Hug.
- `hash`: `DATA`, 32 Bytes - hash of the transaction.
- `input`: `DATA` - the data send along with the transaction.
- `nonce`: `QUANTITY` - the number of transactions made by the sender prior to this one.
- `to`: `DATA`, 10 Bytes - address of the receiver. `null` when its a contract creation transaction.
- `transactionIndex`: `QUANTITY` - integer of the transaction's index position in the block. `null` when its pending.
- `type`:`QUANTITY` - type of the transaction (0: original, 1: sct, 2: deposit)
- `worknodes`: `Array` - Array of selected work nodes via SymID when sending transactions . (min: 1, max: 3)
- `value`: `QUANTITY` - value transferred in Hug.
- `v`: `QUANTITY` - ECDSA recovery id
- `r`: `DATA`, 32 Bytes - ECDSA signature r
- `s`: `DATA`, 32 Bytes - ECDSA signature s

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getTransactionByHash","params":["0x3a646cbc8f7a2e05c6e0dafaa5ea600a93e72925a188706089a1b32d84090235"],"id":100}'

// Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "blockHash": "0x29e38a4b331418e5d4da7a464efc514376f66ad5a88f57d1060d342b94a341d5",
        "blockNumber": "0xa0f",
        "from": "0x00000000000000001001",
        "gas": "0x15f90",
        "gasPrice": "0x430e23400",
        "hash": "0x3a646cbc8f7a2e05c6e0dafaa5ea600a93e72925a188706089a1b32d84090235",
        "input": "0x",
        "nonce": "0x0",
        "to": "0x00000000000000000901",
        "transactionIndex": "0x0",
        "type": "0x0",
        "workNodes": [
            "0x00000000000000001001"
        ],
        "value": "0x1",
        "v": "0x1",
        "r": "0x426abe722a04d2924c40e3008331a1384c6e272155460af16e874fd69c543d0c",
        "s": "0x1857b8e63cc22acdebd5ea9ad8ecdcca3349f81353d8faec80f861f2b6f1f16d"
    }
}

```

------

#### sym_getTransactionByBlockHashAndIndex

Returns information about a transaction by block hash and transaction index position.

##### Parameters

1. `DATA`, 32 Bytes - hash of a block.
2. `QUANTITY` - integer of the transaction index position.

```js
params: [
   '0x2d01dcb69ea3b02d441b6214da5d68a9a0c6c548ac3c17ec388ea7d2b0ff8279',
   '0x2' // 0
]

```

##### Returns

See [sym_getTransactionByHash](#sym_gettransactionbyhash)

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getTransactionByBlockHashAndIndex","params":["0x2d01dcb69ea3b02d441b6214da5d68a9a0c6c548ac3c17ec388ea7d2b0ff8279", "0x2"],"id":1}'

```

Result see [sym_getTransactionByHash](#sym_gettransactionbyhash)

------

#### sym_getTransactionByBlockNumberAndIndex

Returns information about a transaction by block number and transaction index position.

##### Parameters

1. `QUANTITY|TAG` - a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).
2. `QUANTITY` - the transaction index position.

```js
params: [
   '0xd65a', // 54874
   '0x2' // 2
]

```

##### Returns

See [sym_getTransactionByHash](#sym_gettransactionbyhash)

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getTransactionByBlockNumberAndIndex","params":["0xd65a", "0x2"],"id":1}'

```

Result see [sym_getTransactionByHash](#sym_gettransactionbyhash)

------

#### sym_getTransactionReceipt

Returns the receipt of a transaction by transaction hash.

**Note** That the receipt is not available for pending transactions.

##### Parameters

1. `DATA`, 32 Bytes - hash of a transaction

```js
params: [
   '0x77c684a89b85adc04fdf1908347e11705b45d2ad1b4e6237f65e6332b9a08ac4'
]

```

##### Returns

`Object` - A transaction receipt object, or `null` when no receipt was found:

- `transactionHash `: `DATA`, 32 Bytes - hash of the transaction.
- `transactionIndex`: `QUANTITY` - integer of the transaction's index position in the block.
- `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in.
- `blockNumber`: `QUANTITY` - block number where this transaction was in.
- `from`: `DATA`, 10 Bytes - address of the sender.
- `to`: `DATA`, 10 Bytes - address of the receiver. null when it's a contract creation transaction.
- `cumulativeGasUsed `: `QUANTITY ` - The total amount of gas used when this transaction was executed in the block.
- `gasUsed `: `QUANTITY ` - The amount of gas used by this specific transaction alone.
- `contractAddress `: `DATA`, 10 Bytes - The contract address created, if the transaction was a contract creation, otherwise `null`.
- `logs`: `Array` - Array of log objects, which this transaction generated.
- `logsBloom`: `DATA`, 256 Bytes - Bloom filter for light clients to quickly retrieve related logs.
- `status`: `QUANTITY` either `1` (success) or `0` (failure) 

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getTransactionReceipt","params":["0x77c684a89b85adc04fdf1908347e11705b45d2ad1b4e6237f65e6332b9a08ac4"],"id":100}'

// Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "blockHash": "0x2d01dcb69ea3b02d441b6214da5d68a9a0c6c548ac3c17ec388ea7d2b0ff8279",
        "blockNumber": "0xd65a",
        "contractAddress": null,
        "cumulativeGasUsed": "0xf618",
        "from": "0x00000000000000001001",
        "gasUsed": "0x5208",
        "logs": [],
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "status": "0x1",
        "to": "0x00000000000000000901",
        "transactionHash": "0x77c684a89b85adc04fdf1908347e11705b45d2ad1b4e6237f65e6332b9a08ac4",
        "transactionIndex": "0x2"
    }
}

```

------

#### sym_getDeposit

Returns the deposit related information of the account of given address.

##### Parameters

1. `DATA`, 10 Bytes - address to check for deposit related information

##### Returns

`Object` - A  deposit related information object:

- `account`: `DATA`, 10 Bytes - address to check for balance.
- `balance`: `QUANTITY` -  integer of the current balance in hug.
- `deposit`: `QUANTITY`  -  integer of the allocated deposit in hug.
- `since`: `QUANTITY`  - beginning term of deposit.
- `until`: `QUANTITY|DATA` - end term of deposit. if it is 0, it returns "unlimited".

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"sym_getDeposit","params":["0x00000000000000000401"],"id":100}'

// Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "account": "0x00000000000000000401",
        "balance": "0xc097ce7bc8f202c96816a6724359b7",
        "deposit": "0x152d02c7e14af6800000",
        "since": "0x0",
        "until": "unlimited"
    }
}
```

------

#### warrant_blockNumber

Returns the current warrant block number.

##### Parameters

None

##### Returns

`QUANTITY` - Integer of the current warrant block number the client is on.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{ "jsonrpc":"2.0", "method":"warrant_blockNumber", "params":[], "id":100}' http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": "0x97" //151
}
```

------

#### warrant_getWarrantsByBlockHash

Returns information about warrant nodes by the block hash.

##### Parameters

1. `DATA`, 32 Bytes - Hash of a warrant block.

##### Returns

`Array of Object` , N Bytes -  Array of the existing warrant nodes in the designated block or null when failed.

- `blockHash`: `DATA`, 32 Bytes - hash of the block where this warrant node was in.
- `blockNum`: `QUANTITY` - block number where this warrant node was in.
- `symid`:`DATA`, 10 Bytes - the warrant node's identity. 
- `pubkeyhash`: `DATA`, 20 Bytes - public key hash of the warrant node*.*
- `group`: `QUANTITY` - integer denoting for the group type of warrant node. (0: group A, 1: group B)
- `hash`: `DATA`, 32 Bytes - hash of the warrant node.

##### Example 

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{ "jsonrpc":"2.0", "method":"warrant_getWarrantsByBlockHash", "params":["0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba"], "id":100 }' http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": [
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000101",
            "pubkeyhash": "0x18c4fdb750cf3cf60e58fdac3a67419cd5e05836",
            "group": "0x0",
            "hash": "0x7e73a9b6d17902a89f43b4e0c8e31cce237650c10676521644d3bf3e0a88e0d4"
        },
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000201",
            "pubkeyhash": "0x03c223f461d55d0f098261a1a51b01f396807d2d",
            "group": "0x0",
            "hash": "0xe9c78214c21a2bd792806369def48f4755c6087eca3ffb069c6df6beac046fd2"
        },
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000301",
            "pubkeyhash": "0x8c240260f6388fecb1d6538f6a724f3eb0de21f7",
            "group": "0x0",
            "hash": "0xd6c389e17c8b57ca68d9d5bd1a444cde69f0a7e168c90d15630e46a109868d2d"
        },
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000401",
            "pubkeyhash": "0x4c72aba2d236b589cbf22b86d36d688d7b535c77",
            "group": "0x1",
            "hash": "0xe249e41cc617cdeff76b8de8b2051af5439c477e9c82eafa485fe618e1abf833"
        },
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000501",
            "pubkeyhash": "0x8958c65a25f7cc2f2011897f6c679593e27716b6",
            "group": "0x1",
            "hash": "0x778e1ed9f9ffcf26487b09aa4fef55498052d316dde4b5636e032d4737f9e303"
        },
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000601",
            "pubkeyhash": "0x1c921ac91c2dc98718bcac27b5f7fad1799f1951",
            "group": "0x1",
            "hash": "0xe0ee7793ad5b3ddec43236e2420873f7f4a90102eee33ec70341eacb20398b47"
        },
        {
            "blockHash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
            "blockNumber": "0x0",
            "symid": "0x00000000000000000701",
            "pubkeyhash": "0x484e0b5d12913cec0b4e942828f6168e9f464a09",
            "group": "0x1",
            "hash": "0x0e0d00ffccdd817293d928d7634b221ea89c5cefb533f07240eba19bc338cf79"
        }
    ]
}
```

------



#### warrant_getWarrantsByBlockNumber

Returns information about warrant nodes specified by the block number.

##### Parameters

1. `QUANTITY ` - Integer of a block number.

##### Returns

`Array of Object` , N Bytes - For existing warrant nodes information in that block or `null` when it was failed

- `blockHash`: `DATA`, 32 Bytes - hash of the block where this warrant node was in.
- `blockNum`: `QUANTITY` - block number where this warrant node was in.
- `symid`:`DATA`, 10 Bytes -  the warrant node's identity.
- `pubkeyhash`: `DATA`, 20 Bytes - public key hash of the warrant node.
- `group`: `QUANTITY` -  integer denoting for the group type of warrant node. (0: group A, 1: group B)
- `hash`: `DATA`, 32 Bytes - hash of the warrant node.

##### Example 

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0", "method":"warrant_getWarrantsByBlockNumber", "params":["0x0"], "id":100}' http://127.0.0.1:8545

//Result
see warrant_getWarrantsByBlockHash
```

#### warrant_getBlockByHash

Returns information about warrant nodes specified by the block hash.

##### Parameters

1. `DATA`, 32 Bytes - Hash of a warrant block.
2. `Boolean` - If `true` it returns the full warrant Information objects, if `false` only the hashes of the warrants.

##### Returns

`Object` - A warrant block object, or `null` when no warrant block was found:

- `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
- `mainBlockNum`: `QUANTITY` - main block number when this warrant block was created. `null` when its pending block.
- `number`: `QUANTITY` - the block number. `null` when its pending block.
- `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
- `size`: `QUANTITY` - integer the size of this block in bytes.
- `term` : `Object` – range denoting warrant node's active period for creating blocks.
  - `BeginMainBlockNum` : `QUANTITY` - beginning number of the period. 
  - `EndMainBlockNum` : `QUANTITY` - ending number of the period. 
- `warrantInfos` : `Array` – Information of warrant nodes in the designated block, or 32 Bytes warrant information’s hashes depending on the last given parameter. 
- `warrantInfosRoot`: `DATA`, 32 Bytes - the root of the warrant node's Informations trie of the block.

##### Example 

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{ "jsonrpc":"2.0", "method":"warrant_getBlockByHash", "params":["0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",true], "id":100 }' http://127.0.0.1:8545


//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "hash": "0x2a7dff376822c8be6baf3561b393a52bfaffec6c139f72cabc9b74cad7552fba",
        "mainBlockNum": "0x0",
        "number": "0x0",
        "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "primaryTerm": {
            "BeginMainBlockNum": 1,
            "EndMainBlockNum": 1
        },
        "size": "0x13c",
        "warrantInfos":  [{...},{...}],
        "warrantInfosRoot": "0xaeda10d8efd86a7ca8deecea5091944d15cf21d17a1ca946e46603863da3b8a6"
    }
}
```

------

#### warrant_getBlockByNumber

Returns information about a warrant block specified by the block number.

##### Parameters

1. `QUANTITY|TAG ` - Integer of a block number, or the string `"earliest","pending"` or `"latest"`
2. `Boolean` - If `true` it returns the full warrant Information objects, if `false` only the hashes of the warrants.

##### Returns

`Object` - A warrant block object, or `null` when no warrant block was found:

- `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
- `mainBlockNum`: `QUANTITY` - main block number when this warrant block was created. `null` when its pending block.
- `number`: `QUANTITY` - the block number. `null` when its pending block.
- `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
- `size`: `QUANTITY` - integer the size of this block in bytes.
- `term` : `Object` – range denoting warrant node's active period for creating blocks.
  - `BeginMainBlockNum` : `QUANTITY` - beginning number of the period. 
  - `EndMainBlockNum` : `QUANTITY` - ending number of the period. 
- `warrantInfos` : `Array` – Information of warrant nodes in the designated block, or 32 Bytes warrant information’s hashes depending on the last given parameter. 
- `warrantInfosRoot`: `DATA`, 32 Bytes - the root of the warrant node's Informations trie of the block.

##### Example 

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0",  "method":"warrant_getBlockByNumber", "params":["0x0",true], "id":100}' http://127.0.0.1:8545

//Result
see warrant_getblockByHash
```

------

#### citizen_sendCitizen

The message call in order to create new citizen or change citizen information.

##### Parameters

1. `Object` - the Symverse identifier & account properties.

- `from` : `DATA` , 10 Bytes - the address of the CA server that creates SymID. 

- `to` : `DATA` , 10 Bytes - (optional) the address creation transaction is directed to. 

- `symid` : `DATA` , 10 Bytes - hexadecimal SymID identifying an account.

- `pubkeyhash` : `DATA` , 20 Bytes - lower bytes of hashed public key. 

- `vflag` : `DATA` , 1 Byte - (optional ,default:0) veriﬁcation strength of an account represented by bits. 

- `country` : `DATA` , 1 Byte - (optional, default:0) country code.

- `status` : `DATA` , 1 Byte - (optional, default:1, active) account status of an account. (0x1: Active, 0x2: Locked, 0x3: Marked, 0x4: Revoked)

- `credit` : `DATA` , 1 Byte - (optional, default:0) credit rating of an account (0~15) 

- `role` : `DATA` , 2 Bytes - (optional, default: 0x1) account role (0x1: general, 0xf0f0: Master CA, 0xf0f1: CA) 

- `refcode` : `DATA` , 4 Bytes - (optional) issuer's reference code.

- `notbefore` : `DATA` , 8 Bytes - beginning date of available term for SymID. 

- `notafter` : `DATA` , 8 Bytes - end date of available term for SymID. 

- `nonce` : `QUANTITY` - (optional) integer of a nonce. 

  **Note : See  Symverse identifier & account properties in detail.** 

```json
params:[{
    "from": "0x00000000000000000901",
    "to": "0x00000000000000000000",
    "vflag":"0x0",
    "symid":"0x00010000000000010003",
    "pubkeyhash":"0x18c4fdb750cf3cf60e58fdac3a67419cd5e05836",
    "country": "0x0",
    "status": "0x1",
    "credit": "0xf",
    "role": "0x1",
    "notbefore": 19920920,
    "notafter": 20200825
}]

```

##### Returns

`DATA`, 32 Bytes - hash of a citizen.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_sendCitizen","params":[{see above}],"id":100}' http://127.0.0.1:8545

//Result
{"jsonrpc":"2.0","id":100,"result":"0x4841852ea5d07be83b6ffc087619664b4609405c286c7fe325492c16ca53f2c5"}
```

------

#### citizen_sendRawCitizen

The message call in order to create new citizen or change citizen information for signed citizen.

##### Parameters

1. `Object` - signed citizen,  RLP encoded value of signed citizen.

##### Returns

`DATA`, 32 Bytes - hash of a citizen.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_sendRawCitizen","params": "0x20ba02f3659983a51a761ccf7e4d2e4a62610a3e20ba02f3659983a51a761ccf7e4d2e4a62610a3e","id":100}' http://127.0.0.1:8545

//Result
{"jsonrpc":"2.0","id":100,"result":"0x09e67b2f1bd21f6043368f97ebff4f4a2b238111c5a5767b75abde08845bda6e"

```

------

#### citizen_getCitizenByHash

Returns information about a citizen publication requested by the citizen hash.

##### Parameters

1. `DATA`, 32 Bytes - hash of a citizen.

##### Returns

`Object` - A block object, or `null` when it was failed:

- `blockHash`: `DATA`, 32 Bytes - hash of block.
- `blockNumber`: `QUANTITY`  - number of block.
- `citizenIndex`: `QUANTITY` - integer of the citizen's index position in the block. `null` when its pending.
- `from` : `DATA` , 10 Bytes - the address of the CA server that creates SymID. 
- `to` : `DATA` , 10 Bytes - the address creation transaction is directed to. 
- `nonce` : `QUANTITY` - integer of a nonce. 
- `symid` : `DATA` , 10 Bytes - hexadecimal SymID identifying an account.
- `pubkeyhash` : `DATA` , 20 Bytes - lower bytes of hashed public key. 
- `vflag` : `DATA` , 1 Byte - veriﬁcation strength of an account represented by bits. 
- `country` : `DATA` , 1 Byte - country code.
- `status` : `DATA` , 1 Byte - account status of an account. (0x1: Active, 0x2: Locked, 0x3: Marked, 0x4: Revoked)
- `credit` : `DATA` , 1 Byte - credit rating of an account (0~15) 
- `role` : `DATA` , 2 Bytes - account role (0x1: general, 0xf0f0: Master CA, 0xf0f1: CA)
- `refcode` : `DATA` , 4 Bytes - issuer's reference code.
- `notbefore` : `DATA` , 8 Bytes - beginning date of available term for SymID. 
- `notafter` : `DATA` , 8 Bytes - end date of available term for SymID. 
- `writetime` : `QUANTITY` - the unix timestamp for the citizen requested time.
- `hash` : `DATA` , Bytes - citizen hash.
- `v`: `QUANTITY` - ECDSA recovery id
- `r`: `DATA`, 32 Bytes - ECDSA signature r
- `s`: `DATA`, 32 Bytes - ECDSA signature s

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getCitizenByHash","params":["0x82d6fc20acdc12dc6578fef6b558522e2229414506b66a27cc258397a5bfc3d8"],"id":100}' http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "blockHash": "0x35442bfd809586e55c1fa2daaf1f3e2a9d44c99bdb283cb10b12bb2d5bfdf71d",
        "blockNumber": "0x3",
        "citizenIndex": "0x0",
        "from": "0x00000000000000000901",
        "to": "0x00000000000000000000",
        "nonce": "0x0",
        "symid": "0x00010000000000010003",
        "pubkeyhash": "0x18c4fdb750cf3cf60e58fdac3a67419cd5e05836",
        "vflag": "0x0",
        "country": "0x0",
        "status": "0x1",
        "credit": "0xf",
        "role": "0x1",
        "refcode": "0x0",
        "notbefore": 19920920,
        "notafter": 20200825,
        "writetime": 1553483020,
        "hash": "0x82d6fc20acdc12dc6578fef6b558522e2229414506b66a27cc258397a5bfc3d8",
        "v": "0x1",
        "r": "0xd44a9a2c11f8eaa0ccfe7bd99613c970dfc05ea0cc00d7652358b6205f4b0b0c",
        "s": "0x183f6c412863954b9bc4c71326399ba594736c32077bb050771d5499f3c4cc9f"
    }
}

```

------

#### citizen_getRawCitizenByHash

Returns an RLP encoded value of a signed citizen specified by the hash.

##### Parameters

1. `DATA`, 32 Bytes - hash of a citizen.

##### Returns

`DATA` - RLP encoded value of a signed citizen.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getRawCitizenByHash","params":["0x82d6fc20acdc12dc6578fef6b558522e2229414506b66a27cc258397a5bfc3d8"],"id":100}' http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": "0xf893a035442bfd809586e55c1fa2daaf1f3e2a9d44c99bdb283cb10b12bb2d5bfdf71dc0808a000000000000000009018a00000000000000000000808a000100000000000100039418c4fdb750cf3cf60e58fdac3a67419cd5e058368080010f018084012ff8188401343d79845c98450ca082d6fc20acdc12dc6578fef6b558522e2229414506b66a27cc258397a5bfc3d8c0c0c0"
}

```

------

#### citizen_getCitizenBySymID

Returns the information of a citizen by the SymID.

##### Parameters

1. `DATA`, 10Bytes - SymID.
2. `QUANTITY|TAG ` - Integer of a block number, or the string `"earliest"` or `"latest"`

##### Returns

`Object` , N Bytes - For existing citizen information or `null` when it was failed

- `ca`: `DATA`, 10 Bytes - the  issuer's SymID of the citizen.
- `nonce`: `QUANTITY`  - integer of a nonce. 
- `pubkeyhash ` : `DATA`, 20 Bytes  - lower bytes of hashed public key.
- `vflag` : `DATA` , 1 Byte - veriﬁcation strength of an account represented by bits. 
- `country`: `DATA`, 1 Byte - country code.
- `status` : `DATA` , 1 Byte - account status of an account. (0x1: Active, 0x2: Locked, 0x3: Marked, 0x4: Revoked)
- `credit` :  `DATA`, 1 Byte - account credit rating(0~15)
- `role` : `DATA` , 2 Bytes - account role (0x1: general, 0xf0f0: Master CA, 0xf0f1: CA) 
- `refcode`:  `DATA`, 4 Bytes - issuer's reference code.
- `notbefore` : `DATA` , 8 Bytes - beginning date of available term for SymID. 
- `notafter` : `DATA` , 8 Bytes - end date of available term for SymID. 

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getCitizenBySymID", "params":["0x00000000000000000901","latest"],"id":100}' http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "ca": "0x00000000000000000801",
        "nonce": 0,
        "pubkeyhash": "0xf6231e6649cdf3aa13002b659026dba31156036f",
        "vflag": "0x2",
        "country": "0x2",
        "status": "0x1",
        "credit": "0x2",
        "role": "0xf0f1",
        "refcode": "0x0",
        "notbefore": 0,
        "notafter": 0
    }
}
```

------

#### citizen_getRawCitizenBySymID

Returns the RLP encoded value of a signed citizen specified by SymID.

##### Parameters

1. `DATA`, 10Bytes - SymID.

##### Returns

`DATA`  - RLP encoded value of signed citizen.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getRawCitizenBySymID","params":["0x00010000000000010003"],"id":100}' http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": "0xf893a035442bfd809586e55c1fa2daaf1f3e2a9d44c99bdb283cb10b12bb2d5bfdf71dc0808a000000000000000009018a00000000000000000000808a000100000000000100039418c4fdb750cf3cf60e58fdac3a67419cd5e058368080010f018084012ff8188401343d79845c98450ca082d6fc20acdc12dc6578fef6b558522e2229414506b66a27cc258397a5bfc3d8c0c0c0"
}

```

------

#### citizen_getCitizensByBlockNumber

Returns all citizens at the designated citizen block number.

##### Parameters

1.`QUANTITY|TAG ` - Integer of a block number, or the string `"earliest"` or `"latest"`

##### Returns

`Object` , N Bytes - For existing citizen information or `null` when it was failed

- `ca`: `DATA`, 10 Bytes - the  issuer's SymID of the citizen.
- `nonce`: `QUANTITY`  - integer of a nonce. 
- `pubkeyhash ` : `DATA`, 20 Bytes  - lower bytes of hashed public key.
- `vflag` : `DATA` , 1 Byte - veriﬁcation strength of an account represented by bits. 
- `country`: `DATA`, 1 Byte - country code.
- `status` : `DATA` , 1 Byte - account status of an account. (0x1: Active, 0x2: Locked, 0x3: Marked, 0x4: Revoked)
- `credit` :  `DATA`, 1 Byte - account credit rating(0~15)
- `role` : `DATA` , 2 Bytes - account role (0x1: general, 0xf0f0: Master CA, 0xf0f1: CA)
- `refcode`:  `DATA`, 4 Bytes - issuer's reference code.
- `notbefore` : `DATA` , 8 Bytes - beginning date of available term for SymID. 
- `notafter` : `DATA` , 8 Bytes - end date of available term for SymID. 

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getCitizensByBlockNumber","params":["latest"],"id":100}' http://127.0.0.1:8545}

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "00000000000000000101": {
            "ca": "0x00000000000000000901",
            "nonce": 0,
            "pubkeyhash": "0x18c4fdb750cf3cf60e58fdac3a67419cd5e05836",
            "vflag": "0x2",
            "country": "0x2",
            "status": "0x3",
            "credit": "0x2",
            "role": "0x0",
            "refcode": "0x0",
            "notbefore": 0,
            "notafter": 0
        },
        "00000000000000000201": {
            "ca": "0x00000000000000000901",
            "nonce": 0,
            "pubkeyhash": "0x03c223f461d55d0f098261a1a51b01f396807d2d",
            "vflag": "0x1",
            "country": "0x0",
            "status": "0x1",
            "credit": "0x0",
            "role": "0x0",
            "refcode": "0x0",
            "notbefore": 0,
            "notafter": 0
        },
        "00000000000000000301": {
            "ca": "0x00000000000000000901",
            "nonce": 0,
            "pubkeyhash": "0x8c240260f6388fecb1d6538f6a724f3eb0de21f7",
            "vflag": "0x1",
            "country": "0x0",
            "status": "0x1",
            "credit": "0x0",
            "role": "0x0",
            "refcode": "0x0",
            "notbefore": 0,
            "notafter": 0
        },
        "00000000000000000401": {
            "ca": "0x00000000000000001001",
            "nonce": 0,
            "pubkeyhash": "0x4c72aba2d236b589cbf22b86d36d688d7b535c77",
            "vflag": "0x1",
            "country": "0x0",
            "status": "0x1",
            "credit": "0x0",
            "role": "0x0",
            "refcode": "0x0",
            "notbefore": 0,
            "notafter": 0
        }
    }
}
```

------

#### citizen_getStatus

Returns the current status of the citizen.

##### Parameters

1. `Data` , 10 Bytes - SymID.
2. `QUANTITY|TAG ` - Integer of a block number, or the string `"earliest"` or `"latest"`

##### Returns

`DATA`, 1 Bytes - Current status of the citizen.

**Note** 0x01 : Active , 0x02 : Revoked, 0x03 : Locked, 0x04 : Marked

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{ "jsonrpc":"2.0", "method":"citizen_getStatus", "params":["0x00000000000000000001","latest"], "id":100}' http://127.0.0.1:8545

//Result
{"jsonrpc":"2.0","id":100,"result":"0x1"}

```

------

#### citizen_getCitizenCountFromPool

Returns the count of pending citizens in the pool the entity is currently on.

##### Parameters

none

##### Returns

`QUANTITY` - Integer of the number of citizens in this pool.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{ "jsonrpc":"2.0", "method":"citizen_getCitizenCountFromPool",  "params":[], "id":100}’ http://127.0.0.1:8545

//Result
{"jsonrpc":"2.0","id":100,"result":"0x3"}

```

------

#### citizen_pendings

Returns citizen objects in the pool which the entity is currently on.

##### Parameters

none

##### Returns

`Array of Object` , N Bytes - For existing citizen information or `null` when it was failed  or none.

- `blockHash`: `DATA`, 32 Bytes - hash of block.
- `blockNumber`: `QUANTITY`  - number of block.
- `citizenIndex`: `QUANTITY` - integer of the citizen's index position in the block. `null` when its pending.
- `from`: `DATA`, 10 Bytes - the address the CA who creates this SymID.
- `to`: `DATA`, 10 Bytes - the address is directed to. 
- `nonce`: `QUANTITY` - integer of a nonce. 
- `symid` : `DATA`, 10 Bytes - created SymID.
- `pubkeyhash ` : `DATA`, 20 Bytes  - lower bytes of hashed public key.
- `vflag`: `DATA`, 1 Byte - each bit means verification strength of this SymID.
- `country`: `DATA`, 1 Byte - country code.
- `status` :  `DATA`, 1 Byte - account status (0x1: Active, 0x2: Locked, 0x3: Marked, 0x4: Revoked).
- `credit` :  `DATA`, 1 Byte - account credit rating(0~15)
- `role`:  `DATA`, 2 Bytes - account role (0x1: general, 0xf0f0: Master CA, 0xf0f1: CA)
- `refcode`:  `DATA`, 4 Bytes - issuer's reference code.
- `notbefore`: `DATA`, 8 Bytes - beginning date of available term for SymID.
- `notafter`: `DATA`, 8 Bytes - end date of available term for SymID.
- `writetime` : `QUANTITY` - the unix timestamp for the citizen requested time.
- `hash` : `DATA` , 32 Bytes - citizen hash.
- `v`: `QUANTITY` - ECDSA recovery id
- `r`: `DATA`, 32 Bytes - ECDSA signature r
- `s`: `DATA`, 32 Bytes - ECDSA signature s

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_pendings","params":[],"id":100}' http://127.0.0.1:3001

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": [
        {
            "blockHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "blockNumber": null,
            "citizenIndex": "0x0",
            "from": "0x00000000000000000901",
            "to": "0x00000000000000000000",
            "nonce": "0x0",
            "symid": "0x00010000000000010010",
            "pubkeyhash": null,
            "vflag": "0x0",
            "country": "0x0",
            "status": "0x1",
            "credit": "0x0",
            "role": "0x1",
            "refcode": null,
            "notbefore": 19920920,
            "notafter": 20200825,
            "writetime": 1555900702,
            "hash": "0xa6cc9556702557bb076cd50da471bf3e8dc34b5f1d979106e12ce99b44e99f5a",
            "v": "0x1",
            "r": "0x4657844aa213657571de9991d7710644cdd78de37d95808ccfb44f137f26b585",
            "s": "0x52fe5cc7924dbeb5166a162fb338a2ec8e94b77152aefa0afa6a6abeeceed2e9"
        },
        {
            "blockHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "blockNumber": null,
            "citizenIndex": "0x0",
            "from": "0x00000000000000000901",
            "to": "0x00000000000000000000",
            "nonce": "0x1",
            "symid": "0x00010000000000010011",
            "pubkeyhash": null,
            "vflag": "0x0",
            "country": "0x0",
            "status": "0x1",
            "credit": "0x0",
            "role": "0x1",
            "refcode": null,
            "notbefore": 19920920,
            "notafter": 20200825,
            "writetime": 1555900706,
            "hash": "0xef6058e50ff0d68b9624bb78edcb0a62fc5a6fe7db617034e35ed9f8c5ba0199",
            "v": "0x0",
            "r": "0x47f095035e97952a4f63d7cb21a801011419661b4527fe2cb6c364d28f54b470",
            "s": "0x1f180abf67b25b0c0bf478da9367be4270618a241c13795ab1336229e91cc141"
        },
        {
            "blockHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "blockNumber": null,
            "citizenIndex": "0x0",
            "from": "0x00000000000000000901",
            "to": "0x00000000000000000000",
            "nonce": "0x2",
            "symid": "0x00010000000000010012",
            "pubkeyhash": null,
            "vflag": "0x0",
            "country": "0x0",
            "status": "0x1",
            "credit": "0x0",
            "role": "0x1",
            "refcode": null,
            "notbefore": 19920920,
            "notafter": 20200825,
            "writetime": 1555900709,
            "hash": "0xb8bfdcd3c9698b836df8807a7f5cfd6f9d479de57da0521d5fcadf4b257bb656",
            "v": "0x0",
            "r": "0xafb7a215299ee01fc1f99157848d20fa49f8dc73c3919d47447e9563d5ce9809",
            "s": "0x4ae2b65b6489176334a544647e1791437536b85e1b15a66ef5a705c7af2a3159"
        }
    ]
}
```

------

#### citizen_blockNumber

Returns the number of the most recent citizen block.

##### Parameters

none

##### Returns

`QUANTITY` - integer of the current citizen block number the client is on.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_blockNumber","params":[],"id":100}' http://127.0.0.1:8545

//Result

{"jsonrpc":"2.0","id":100,"result":"0x97" //151}
```

------

#### citizen_getBlockByHash

Returns information about a citizen block, specified by the hash.

##### Parameters

1. `DATA`, 32 Bytes - Hash of a citizen block.
2. `Boolean` - If `true` it returns the full citizen objects, if `false` only the hashes of the citizens.

##### Returns

`Object` - A citizen block object, or `null` when no citizen block was found:

- `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
- `mainBlockNum`: `QUANTITY` - main block number when this citizen block was created. `null` when its pending block.
- `stateRoot`: `DATA`, 32 Bytes - the root of the final state trie of the block.
- `citizensRoot`: `DATA`, 32 Bytes - the root of the citizen trie of the block.
- `number`: `QUANTITY` - the block number. `null` when its pending block.
- `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
- `size`: `QUANTITY` - integer the size of this block in bytes.
- `citizens`: `Array` - citizens in this block, or 32 Bytes citizen hashes depending on the last given parameter.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getBlockByHash","params":["0xc50b46e4ca6dbd4f9fbbbe00807590bb892fedee5d2077ff6794988b3c085619", true],"id":100}’ http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": {
        "citizens": [{...},{...}],
        "citizensRoot": "0xc44c78b058eed046bbee7992efad0f11db0ecab1bdcae4b86397c7be5708eb83",
        "hash": "0xc50b46e4ca6dbd4f9fbbbe00807590bb892fedee5d2077ff6794988b3c085619",
        "mainBlockNum": "0x0",
        "number": "0x0",
        "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "size": "0x2de",
        "stateRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421"
    }
}
```

------

#### citizen_getBlockByNumber

Returns information about a citizen block, specified by the citizen block number.

##### Parameters

1. `QUANTITY|TAG ` - Integer of a block number, or the string `"earliest"` or `"latest"`
2. `Boolean` - If `true` it returns the full citizen objects, if `false` only the hashes of the citizens.

##### Returns

`Object` - A citizen block object, or `null` when no citizen block was found:

- `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
- `mainBlockNum`: `QUANTITY` - main block number when this citizen block was created. `null` when its pending block.
- `stateRoot`: `DATA`, 32 Bytes - the root of the final state trie of the block.
- `citizensRoot`: `DATA`, 32 Bytes - the root of the citizen trie of the block.
- `number`: `QUANTITY` - the block number. `null` when its pending block.
- `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
- `size`: `QUANTITY` - integer the size of this block in bytes.
- `citizens`: `Array` - citizens in this block, or 32 Bytes citizen hashes depending on the last given parameter.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getBlockByNumber","params":["0x0", true],"id":100}’ http://127.0.0.1:8545

//Result
citizen_getCitizenBlockByHash
```

------

#### citizen_getIssuer

Returns CA's SymID that created the SymID.

##### Parameters

1. `DATA`, 10Bytes - SymID.
2. `QUANTITY|TAG ` - Integer of a block number, or the string `"earliest"` or `"latest"`

##### Returns

`DATA` - CA node's SymID

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getIssuer","params":["0x00010000000000010003","latest"],"id":100}’ http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": "0x00000000000000000901"
}
```

------

#### citizen_getRole

Returns the role of SyrmID.

##### Parameters

1. `DATA`, 10Bytes - SymID.
2. `QUANTITY|TAG ` - Integer of a block number, or the string `"earliest"` or `"latest"`

##### Returns



`DATA` , 2 Bytes - Role of SymID.

##### Example

```json
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"citizen_getRole","params":["0x00010000000000010003","latest"],"id":100}’ http://127.0.0.1:8545

//Result
{
    "jsonrpc": "2.0",
    "id": 100,
    "result": "0x1"
}
```

------

#### citizen_getBlockCitizenCountByHash

Returns the number of citizens in a block from a block matched with the given block hash.

##### Parameters

1. `DATA`, 32 Bytes - hash of a block.

```js
params: [
   '0x2a80f9f09749fd6e8af257586da0469091839c4365cd20a0e5bbd086d48e3adc'
]
```

##### Returns

`QUANTITY` - integer of the number of citizens in this block.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"citizen_getBlockCitizenCountByHash","params":["0x2a80f9f09749fd6e8af257586da0469091839c4365cd20a0e5bbd086d48e3adc"],"id":1}'

//

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xa" // 10
}
```

------

#### citizen_getBlockCitizenCountByNumber

Returns the number of citizens in a block from a block matched with the given block number.

##### Parameters

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).

```js
params: [
   '0xa', // 10
]
```

##### Returns

`QUANTITY` - integer of the number of citizens in this block.

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"citizen_getBlockCitizenCountByNumber","params":["0xe8"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xa" // 10
}
```

------

#### sct_getContract

Return information about created contract by a transaction of SCT type.

##### Parameters

1. `DATA`, 10 Bytes - SCT contract address.

##### Returns

`Object` -  information about the address. 

- `name`: `DATA` - SCT name.
- `symbol`: `DATA`, 3 Bytes - SCT symbol.
- `total`: `DATA` - total Supply.
- `type`: `DATA` - SCT type.
- `creator`: `DATA`, 10 Bytes - contract creator's address.
- `owner`: `DATA`, 10 Bytes - contract owner's address.

It also returns if it is SCT40:

- `cpoint`: `QUANTITY` - amount of coupon point.

##### Example

```js
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"stm_getContract ","params": "0x0ced1024eed02b234df2"],"id":1}' http://127.0.0.1:8545

//Result
{
    "jsonrpc":"2.0",
    "id":1,
    "result":{
        "cpoint": 10000000000000,
        "creator": "0x00000000000000000001",
        "name": "Coupon",
        "owner": "0x00000000000000000001",
        "state": "active",
        "symbol": "CCC",
        "type": "SCT40"
    }
}
```

------

#### sct_getContractItem

Return information about coupon item in created contract by a transaction of SCT type.

##### Parameters

1. `DATA`, 10 Bytes - SCT contract address.
2. `QUANTITY` - integer of the index position.

##### Returns

`Object` - 설명작성부탁드립니다. 

- `state`: `QUANTITY` - Item state(0:active 1: lock)
- `type`: `DATA` - Item type.
- `name`: `DATA` - Item name.
- `value|usepoint`: `QUANTITY` - value of item if SCT40, use amount of point.
- `property`: `DATA` - item property(unique)
- `category`: `DATA`, 10 Bytes - Item category
- `description`: `DATA`, 10 Bytes - Item description

##### Example

```js
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"sym_getContractItem","params":[" 0x0ced1024eed02b234df2”,”1”],"id":1}' http://127.0.0.1:8545

//Result
{
    "jsonrpc":"2.0",
    "id":1,
    "result": {
    	"couponNo": "2",
    	"etc": "",
      	"groupNo": "1",
      	"name": "coupon2",
      	"state": 0,
      	"type": "123",
      	"usepoint": 500
	}
}
```

------

#### sct_getContractAccount

Retrun balance or index of item depends on the contract type.

##### Parameters

1. `DATA`, 10 Bytes - SCT contract address.
2. `DATA`, 10 Bytes - SymID.

##### Returns

`QUANTITY` - either balance (if it is SCT ~) or index of item(if it is SCT ~)

##### Example

```js
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"src_getContractAccount","params":[”0x0ced1024eed02b234df2
”, ”0x00000000000000000001"],"id":1}' http://127.0.0.1:8545

//Result
{
    "jsonrpc":"2.0",
    "id":1,
    "result":{
        "balance": 10000000000000
    }
}
```

------

#### sct_getAllowance

Retrun balance or index of item depends on the contract type.

##### Parameters

1. `DATA`, 10 Bytes - SCT contract address.
2. `DATA`, 10 Bytes - owner SymID.
3. `DATA`, 10 Bytes - spender SymID.

##### Returns

`QUANTITY` - either balance (if it is SCT ~) or index of item(if it is SCT ~)

##### Example

```js
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"src_getAllowance","params":[”0x0ced1024eed02b234df2
”, ”0x00000000000000000001”, “0x00000000000000000002”],"id":1}' http://127.0.0.1:8545

//Result
{
    "jsonrpc":"2.0",
    "id":1,
    "result":{
        "balance": 10000000000000
    }
}
```

------

#### sct_getContractItemsByCategory

Returns Item list which is created by SCT30 or 40.

##### Parameters

1. `DATA`, 10 Bytes - SCT contract address.
2. `QUANTITY` - category or group number.

##### Returns

`Array of Object` , N Bytes - Array of  Item list

- `state`: `QUANTITY` - state of item(0:active 1: lock)
- `type`: `DATA` - item type.
- `name`: `DATA` - item name(alias)
- `value|usepoint`: `QUANTITY` - value of item if SCT40, use amount of point.
- `Index`: `DATA` - unique key of  internal item.
- `couponNo`: `DATA` - unique key of external item.
- `groupNo`: `DATA` - category of item.
- `etc`: `DATA` - extra description of item.

##### Example

```js
//Request
curl -X POST -H "Content-Type: application/json; charset=utf-8" --data '{"jsonrpc":"2.0","method":"src_getContractItemsByCategory","params":[“0x0ced1024eed02b234df2”,”1"],"id":1}' http://127.0.0.1:8545

//Result
{
    "jsonrpc":"2.0",
    "id":1,
    "result":"[
        {
            "couponNo": "1",
            "etc": "",
            "groupNo": "1",
            "index": 0,
            "name": "coupon1",
            "state": 0,
            "type": "123",
            "usepoint": 500
        }, {
            "couponNo": "2",
            "etc": "",
            "groupNo": "1",
            "index": 1,
            "name": "coupon2",
            "state": 0,
            "type": "123",
            "usepoint": 500
        }
    ]
}
```

