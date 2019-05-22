## SymVerse BlockChain

SymVerse exists and serves at the pleasure of users and DApps. 
Transactions are intuitively simple and easily performed. Execution is lightening fast and completely reliable. 
The production of new blocks is a cooperative process in which everyone participates and is therefore justly rewarded. 
SymVerse aspires to create a better world.

https://www.symverse.com/

## SymVerse Approach

Blockchains can lead the way to a better world. To achieve this, however, technology must be upgraded while the philosophical foundations are strengthened. 
SymVerse adopts deeper socio-economic ideas and introduces revolutionary technical innovations.

## Go-symverse

go-symverse is a project that is being developed for the SymVerse Blockchain POC based on go-ethereum source code.
Therefore, the build and execution style are almost the same as the go-ethereum.
There is no stable version yet.

## Building the source

For prerequisites and detailed build instructions please read the [Installation Instructions](https://github.com/symverse-lab/Document/wiki/Installation-Instructions) on the wiki.

Building gsym requires both a Go (version 1.7 or later) and a C compiler.
You can install them using your favourite package manager.
Once the dependencies are installed, run

```
make gsym
```

or, to build the full suite of utilities:

```
make all
```

## Executables

The go-symverse project comes with several wrappers/executables found in the `cmd` directory.

|  Command   | Description                                                  |
| :--------: | ------------------------------------------------------------ |
| **`gsym`** | Our main Symverse CLI client. It is the entry point into the Symverse network (main-, test- or private net), capable of running as a full node (default) archive node (retaining all historical state) or a light node (retrieving data live). It can be used by other processes as a gateway into the Symverse network via JSON RPC endpoints exposed on top of HTTP, WebSocket and/or IPC transports. `gsym --help` and the [CLI Wiki page](https://github.com/symverse-lab/Document/wiki/Command-Line-Options) for command line options. |
| `bootnode` | Stripped down version of our Symverse client implementation that only takes part in the network node discovery protocol, but does not run any of the higher level application protocols. It can be used as a lightweight bootstrap node to aid in finding peers in private networks. |

## Running gsym

Going through all the possible command line flags is out of scope here (please consult our
[CLI Wiki page](https://github.com/symverse-lab/Document/wiki/Command-Line-Options), but we've
enumerated a few common parameter combos to get you up to speed quickly on how you can run your
own Gsym instance.

### Full node on the main Symverse network

By far the most common scenario is people wanting to simply interact with the Symverse network:
create accounts; transfer funds; deploy and interact with contracts. For this particular use-case
the user doesn't care about years-old historical data, so we can fast-sync quickly to the current
state of the network. To do so:

```
$ gsym console
```

This command will:

- Start gsym in fast sync mode (default, can be changed with the `--syncmode` flag), causing it to
  download more data in exchange for avoiding processing the entire history of the Symverse network,
  which is very CPU intensive.
- Start up Gsym's built-in interactive [JavaScript console](https://github.com/symverse-lab/Document/wiki/Java-Script-Console), (via the trailing `console` subcommand) through which you can invoke all official [`web3` methods](https://github.com/symverse-lab/Document/wiki/Java-Script-APIs) as well as Gsym's own [management APIs](https://github.com/symverse-lab/Document/wiki/Management-APIs).
  This too is optional and if you leave it out you can always attach to an already running Gsym instance
  with `gsym attach`.

### Full node on the Symverse test network

Transitioning towards developers, if you'd like to play around with creating Symverse contracts, you
almost certainly would like to do that without any real money involved until you get the hang of the
entire system. In other words, instead of attaching to the main network, you want to join the **test**
network with your node, which is fully equivalent to the main network, but with play-Ether only.

```
$ gsym --testnet console
```

The `console` subcommand have the exact same meaning as above and they are equally useful on the
testnet too. Please see above for their explanations if you've skipped to here.

Specifying the `--testnet` flag however will reconfigure your Gsym instance a bit:

- Instead of using the default data directory (`~/.symverse` on Linux for example), Gsym will nest
  itself one level deeper into a `testnet` subfolder (`~/.symverse/testnet` on Linux). Note, on OSX
  and Linux this also means that attaching to a running testnet node requires the use of a custom
  endpoint since `gsym attach` will try to attach to a production node endpoint by default. E.g.
  `gsym attach <datadir>/testnet/gsym.ipc`. Windows users are not affected by this.
- Instead of connecting the main Symverse network, the client will connect to the test network,
  which uses different P2P bootnodes, different network IDs and genesis states.

*Note: Although there are some internal protective measures to prevent transactions from crossing
over between the main network and test network, you should make sure to always use separate accounts
for play-money and real-money. Unless you manually move accounts, Gsym will by default correctly
separate the two networks and will not make any accounts available between them.*

### Programatically interfacing Gsym nodes

As a developer, sooner rather than later you'll want to start interacting with Gsym and the Symverse
network via your own programs and not manually through the console. To aid this, Gsym has built-in
support for a JSON-RPC based APIs ([standard APIs](https://github.com/symverse-lab/Document/wiki/JSON-RPC) and [Gsym specific APIs](https://github.com/symverse-lab/Document/wiki/Management-APIs)). These can be
exposed via HTTP, WebSockets and IPC (unix sockets on unix based platforms, and named pipes on Windows).

The IPC interface is enabled by default and exposes all the APIs supported by Gsym, whereas the HTTP
and WS interfaces need to manually be enabled and only expose a subset of APIs due to security reasons.
These can be turned on/off and configured as you'd expect.

HTTP based JSON-RPC API options:

- `--rpc` Enable the HTTP-RPC server
- `--rpcaddr` HTTP-RPC server listening interface (default: "localhost")
- `--rpcport` HTTP-RPC server listening port (default: 8545)
- `--rpcapi` API's offered over the HTTP-RPC interface (default: "sym,net,web3")
- `--rpccorsdomain` Comma separated list of domains from which to accept cross origin requests (browser enforced)
- `--ws` Enable the WS-RPC server
- `--wsaddr` WS-RPC server listening interface (default: "localhost")
- `--wsport` WS-RPC server listening port (default: 8546)
- `--wsapi` API's offered over the WS-RPC interface (default: "sym,net,web3")
- `--wsorigins` Origins from which to accept websockets requests
- `--ipcdisable` Disable the IPC-RPC server
- `--ipcapi` API's offered over the IPC-RPC interface (default: "admin,debug,sym,dminer,net,personal,shh,txpool,web3")
- `--ipcpath` Filename for IPC socket/pipe within the datadir (explicit paths escape it)

You'll need to use your own programming environments' capabilities (libraries, tools, etc) to connect
via HTTP, WS or IPC to a Gsym node configured with the above flags and you'll need to speak [JSON-RPC](http://www.jsonrpc.org/specification)
on all transports. You can reuse the same connection for multiple requests!

**Note: Please understand the security implications of opening up an HTTP/WS based transport before doing so! Hackers on the internet are actively trying to subvert Symverse nodes with exposed APIs!
Further, all browser tabs can access locally running webservers, so malicious webpages could try to
subvert locally available APIs!**

### Operating a private network

Maintaining your own private network is more involved as a lot of configurations taken for granted in
the official networks need to be manually set up.

Please see [Gsym User Guide](https://github.com/symverse-lab/Document/blob/master/Doc/Gsym-User-Guide.pdf) in repository.

## Contribution

Thank you for considering to help out with the source code! We welcome contributions from anyone on the internet, and are grateful for even the smallest of fixes!

If you'd like to contribute to go-symverse, please fork, fix, commit and send a pull request for the maintainers to review and merge into the main code base. If you wish to submit more complex changes though, please check up with the Symverse engineering team first to ensure those changes are in line with the general philosophy of the project and/or get some early feedback which can make both your efforts much lighter as well as our review and merge procedures quick and simple.

Please make sure your contributions adhere to our coding guidelines:

- Code must adhere to the official Go [formatting](https://golang.org/doc/effective_go.html#formatting) guidelines (i.e. uses [gofmt](https://golang.org/cmd/gofmt/)).
- Code must be documented adhering to the official Go [commentary](https://golang.org/doc/effective_go.html#commentary) guidelines.
- Pull requests need to be based on and opened against the `master` branch.
- Commit messages should be prefixed with the package(s) they modify.
  - E.g. "sym, rpc: make trace configs optional"

Please see the [Developers' Guide](https://github.com/symverse/go-symverse/wiki/Developers-Guide) for more details on configuring your environment, managing project dependencies and testing procedures.

## License

The go-ethereum library (i.e. all code outside of the `cmd` directory) is licensed under the
[GNU Lesser General Public License v3.0](https://www.gnu.org/licenses/lgpl-3.0.en.html), also
included in our repository in the `COPYING.LESSER` file.

The go-symverse binaries (i.e. all code inside of the `cmd` directory) is licensed under the
[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html), also included
in our repository in the `COPYING` file.
