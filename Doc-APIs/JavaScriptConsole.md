# JavaScript Console



Symverse implements a **javascript runtime environment** (JSRE) that can be used in either interactive (console) or non-interactive (script) mode.

## Interactive use: the JSRE REPL Console

The `symverse CLI` executable `gsym` has a JavaScript console (a **Read, Evaluate & Print Loop** = REPL exposing the JSRE), which can be started with the `console` or `attach` subcommand. The `console`subcommands starts the gsym node and then opens the console. The `attach` subcommand will not start the gsym node but instead tries to open the console on a running gsym instance.

```
$ gsym console
$ gsym attach
```

The attach node accepts an endpoint in case the gsym node is running with a non default ipc endpoint or you would like to connect over the rpc interface.

```
$ gsym attach ipc:/some/custom/path
$ gsym attach http://191.168.1.1:8545
$ gsym attach ws://191.168.1.1:8546
```

Note that by default the gsym node doesn't start the http and weboscket service and not all functionality is provided over these interfaces due to security reasons. These defaults can be overridden when the `--rpcapi` and `--wsapi` arguments when the gsym node is started, or with [admin.startRPC](https://github.com/symverse-lab/Document/blob/master/Doc-APIs/Management-APIs.md#admin_startrpc) and [admin.startWS](https://github.com/symverse-lab/Document/blob/master/Doc-APIs/Management-APIs.md#admin_startws).

If you need log information, start with:

```
$ gsym --verbosity 5 console 2>> /tmp/sym.log
```

Otherwise mute your logs, so that it does not pollute your console:

```
$ gsym console 2>> /dev/null
```

or

```
$ gsym --verbosity 0 console
```

Gsym has support to load custom JavaScript files into the console through the `--preload` argument. This can be used to load often used functions, setup web3 contract objects, or ...

```
gsym --preload "/my/scripts/folder/utils.js,/my/scripts/folder/contracts.js" console
```



## Non-interactive use: JSRE script mode

It's also possible to execute files to the JavaScript interpreter. The `console` and `attach` subcommand accept the `--exec` argument which is a javascript statement.

```
$ gsym --exec "sym.blockNumber" attach
```

This prints the current block number of a running gsym instance.

Or execute a local script with more complex statements on a remote node over http:

```
$ gsym --exec 'loadScript("/tmp/checkbalances.js")' attach http://123.123.123.123:8545
$ gsym --jspath "/tmp" --exec 'loadScript("checkbalances.js")' attach http://123.123.123.123:8545
```

Use the `--jspath <path/to/my/js/root>` to set a libdir for your js scripts. Parameters to `loadScript()` with no absolute path will be understood relative to this directory.

You can exit the console cleanly by typing `exit` or simply with `CTRL-C`.
