# Nault advanced features: Changing backend servers and using the block explorer

Nault uses the Nano RPC protocol for communication with network nodes. This is done via backend servers, also called proxy servers. To ensure robustness and stability if a backend should go down Nault uses several of them. Some main servers are chosen by random on each wallet load (page refresh) if the connection is interrupted or hitting the rate limit. Others are used as a backup for manual selection.

But stability is not the only reason for having this unique possibility. Nault can also be used on other networks, which will be described further down.

Additionally, Nault has a built-in block explorer that is often overlooked.

============================
## Table on Contents

1. TOC
{:toc}

============================
## When to change server and how to do it
A nano node may suffer from some problem, is stalled or behind in blocks. In that case, the Wallet may indicate that the node is connected and working, but new transactions are not coming in. Could also be that you can send transactions but not receive. If that happens you can go to Nault app settings and check the stats of each server, comparing the block count and stake (total needs to be above required), and switch to another server if needed.

* Random is default. A server will be selected for you on each visit.
* Custom: You can enter any private or public Nano node RPC interface and/or websocket. Then you have full control over your wallet. The auth header can be used to authenticate locked backends or by using tokens for unlimited RPC requests that can for example be purchased at [MyNano.ninja](https://mynano.ninja/api/node).
* Offline mode can be useful if using the desktop app on a remote offline device together with the remote signing procedure. No network actions will be used (less popups).

![](/images/server.png)


============================
## What other networks exist and how to use them
Nault is not only bound to function with the Main public network. In fact, you can choose an RPC backend of any direct Nano fork. That includes the public beta network, the public test network or even a single or multi-node local network using something like the [linuxserver docker images](https://hub.docker.com/r/linuxserver/nano).

Just point the backend server to the node RPC address and you are good to go. If Nault.cc doesn't work, try the desktop app. Usually, you can't mix https and http sources in the browser. The node settings (config-node.toml) must allow RPC (and websocket if you want automatic receive). If you are using a proxy server in between like the [NanoRPCProxy](https://github.com/Joohansson/NanoRPCProxy), [Noxy](https://github.com/BitDesert/Noxy) or the linuxserver docker with its internal proxy you just have to make sure to allow the RPC commands Nault is using:

* accounts_balances
* accounts_frontiers
* account_history
* account_info
* accounts_pending
* blocks_info
* confirmation_quorum
* pending
* process
* representatives_online
* version
* work_generate

To send and receive transactions you need to allow the "work_generate" command with any either of:
* Use the node itself by setting enable_control = true in the config-rpc.toml (and enable opencl in the config-node.toml if you have a GPU)
* Use a work server by adding one or several work_peers in the config-node.toml (currently require a code change in Nault to pass "use_peers" as a parameter for the work_generate command)
* Use a proxy server like [NanoRPCProxy](https://github.com/Joohansson/NanoRPCProxy) that has support for both dpow and bpow as a middleman
* Use some other proxy server that can connect to work peers

============================
## The Nault block explorer
Regardless if you are using the wallet on the Nano main network or some other fork, a block explorer is always useful!

You reach it from:
* The accounts page and click on an account

![Accounts](/images/accounts.png)

* Or enter an address or block hash at the bottom

![Quick Search](/images/explorer.png)

Once you are in the explorer you can further click on other accounts or blocks to drill down. It will grab the latest info, including any balance and pending/incoming transactions.

![Account Info](/images/account_info.png)

![Block Info](/images/block_info.png)

============================
## Other Wallet Settings
There are also some other useful options in the "App settings":

1. **Lock After Inactivity**: Shorten to increase the security or turn off automatic lock.
2. **Wallet Storage**: Select None if you want Nault to reset and delete the seed, settings and everything after browser exit. WARNING: You must write down your seed or your funds will be lost!
3. **PoW Source**: Let Nault decide or force it to use local GPU / CPU or remote server PoW.
4. **Receive Method**: If you get annoying auto receives, you can set it to manual. Then you receive all transactions when needed from the Receive page. Useful when using a Ledger hardware wallet.
5. **Min Receive**: Use this to ignore small spam transactions. 0.000001 is the smallest amount possible to send in most wallets.
6. **Default Representative**: Override the rep that is set to all new accounts you open in the wallet. If blank, one will be selected for you.