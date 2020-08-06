# The security of your Nano

Let us talk about the security of Nano and using [Nault](https://nault.cc/). But before we dive in, you should understand the fundamentals of the Nano protocol and what it means to own Nano. This article will then divide the overall security into the following sections: The Nano protocol, The storage of keys and The usage of keys.

============================
## Table on Contents

1. TOC
{:toc}

============================
## What does it mean to own Nano?
As with most other cryptocurrencies, the Nano protocol is designed to transfer ownership of a stake in the currency total supply. By owning 1 NANO means you own the keys that control an account which is set to a balance of 1 NANO. Any fraction of that, down to the smallest possible unit called raw, can be moved to any other account. That is done by a set of parameters called a block, which is stored on the distributed Ledger. Two of the parameters are the account and the latest balance the account holds. Before the network can accept a new block, it needs to be signed. That can only be done by the private key for that specific account.

The private keys are derived from a 64-char hexadecimal entropy string called a Nano seed. A single seed contains a total of 4,294,967,295 keys (or indexes) where each one unlocks a valid account (Nano address). In many wallets, we are only interested in the first account (index 0) but Nault, for example, can access any index if you so want. That's the principle and also why owning the seed means owning the Nano. Storing Nano at an exchange does NOT technically mean you own them, because the exchange handles the seed for you. They can be hacked or closed down without warning and in that case, the Nano is no longer under your control.

============================
## The Nano Protocol
The blocks are validated and voted on in a distributed consensus model across the world using network nodes. If the nodes agree a block is valid, it's stored in the Ledger which is synchronized between the nodes.

The security of your Nano is bound to the security of the network. Without a functioning network, the Nano can't be transferred and the value of the network (the value of 1 NANO) would eventually drop to zero. That topic is too broad for this article and we will simply assume the network is functioning. There is plenty of material available as it's been discussed for years but easiest would be to refer to the successful [official security audit that was made](https://medium.com/nanocurrency/nano-protocol-security-audit-summary-and-full-report-48760be8ab3d) in 2018. The network has additonally been heavily improved since then.

============================
## The Storage of Keys
There are many ways to store keys/seeds and this is where Wallets come in. A wallet can be digital, analogue, online, offline, encrypted or open. How YOU decide to store the seed is often bound to the level of convenience you are after. That is further described in [this article](https://medium.com/nano-education/how-to-secure-your-cryptocurrency-nano-7a83b194e474). We will be focusing on storing the keys in Nault, a hardware wallet or offline using the [remote-signing procedure](#transact-using-a-remote-signing-procedure).

### Keys in Nault
Nault is a fully client-side wallet meaning it will never send the keys to a remote server. They are stored only in browsers local storage. The default usage in Nault is to encrypt the seed using a password of your choice. The strength of the password will decide the level of security and it will be stored as long as the browser cache lives, which can be forever if you want. Nault can also be set to remove all wallet data on browser exit. Then you will enter your seed/key the next time you need access. Using that method probably means you would store the seed on a paper and scan it using the QR reader. A password manager is also an option but it's recommended to always have a non-digital backup in case the electronic fail. Nault can be used Online or Offline which is described in the [the usage of keys](#the-usage-of-keys) section. You can for example store the keys / seeds in Nault but on a machine that is always offline.
![](/images/security_01.png)

### Keys in a Hardware Wallet
Nault supports the Ledger Nano S and Ledger Nano X devices. This is one of the most secure methods where the keys are encrypted inside the device and can only be unlocked with a 4-8 digit PIN. The wrong PIN will erase the device, and a 24-word backup mnemonic is stored on a paper during the device initialization. The device is known as "unhackable" yet very easy to access. Plug it in via USB, unlock and transact on the Nano network. We can call this method semi-offline since the device is not known to be maliciously accessible but theoretically attached to an online wallet (if not using the remote signing procedure described in [the usage of keys](#the-usage-of-keys)).
![](/images/ledger_x.jpeg)

### Keys on Paper
This is arguable the safest method since a paper is hopefully offline and hidden from prying eyes but also arguably LESS safe than a hardware wallet because if anyone would find the paper it's also directly accessible and unencrypted. The safety relies on where you hid it. A seed on a paper can be scanned by Nault and used when you need access to it, either doing an online signing or offline signing.
![](/images/security_02.png)

============================
## The usage of Keys
The third factor that decides the overall security of your Nano is how you choose to transact it. Using Nault is very secure in itself because no sensitive data is sent over the Internet. Nault connects to a backend server where commands are sent to the Nano network, but the block signing is done on your device using keys on your device. Only the final signed block is sent over the Internet but the signature can't be reversed or tampered with. However, what will reflect the security is the key storage method described in the previous chapter.

### Transact with an online Nault
Your keys are stored encrypted in the browser storage and you unlock the wallet/ decrypt the keys before doing any transactions. This is the most convenient method but not the most secure. Worst case, the wallet is hacked and you are tricked to enter your seed.
![](/images/security_11.png)

### Transact with the Ledger hardware wallet
Your keys are secured by the Ledger device and unlocked before doing any transactions. A difference from the native Nault is you have to validate the destination and balance on the device display and manually approve with the device button. A hacked wallet can't trick you in this case because what's shown on the device is always true. This is medium convenient but not even this is the most secure option. Worst case, an unknown vulnerability exists in the device that tricks you into sending funds to someone else. A full Ledger/Nault user guide is found [here](http://docs.nault.cc/2020/08/04/ledger-guide.html).

### Transact using a remote-signing procedure
Your keys are stored offline, thus avoiding any leaks to the Internet due to malware, hacked password manager or other things that can go wrong in any online device. The principal follows:

1. Create an unsigned block for account X (using the latest data from the network)
1. Transfer it to an offline device where it's signed using a key that owns X
1. Transfer the signed block to any online device where it's sent to the live network

![](/images/security_12.png)

Now, this is the most secure method with the cost of convenience. Nault makes this somewhat usable but you should be prepared for some extra steps. Steps that may, however, be well worth it if transacting large amounts! A [full walkthrough can be found here](https://youtu.be/a4NstF-jrSU), or a [speed demo](https://youtu.be/qThEPwi1csk) showing that offline-signing can be done in less than 5 seconds.

**The full procedure is also described below**

1. Go to the [remote signing page](https://nault.cc/remote-signing) on an **online** Nault (no wallet is required). Paste any account you wish to transact on (SEND, RECEIVE or CHANGE representative). Press the CREATE button that will take you to the account detail page with remote signing enabled.
![](/images/security_03.png)

1. For SEND or CHANGE, press "CREATE NEW BLOCK". Select block type and fill in the destination and amount for SEND, or the new representative for CHANGE. Press "GENERATE BLOCK"
![](/images/security_04.png)

1. A big QR is shown. This is the unsigned block you will now scan or transfer to the **offline** Nault, which you preferably run using the [desktop version](https://github.com/Nault/Nault/releases). If the offline machine doesn’t have a camera you can manually copy the unsigned block using the button above the QR and paste it in STEP 2 over at the [remote signing page](https://nault.cc/remote-signing).
![](/images/security_05.png)

1. When the block has been imported in the offline Nault, user verification is required. This is an important step security-wise where the balance is calculated from the new and previous block provided. Another step happening behind the scenes is the previous block hash is calculated and compared against the new block's frontier parameter. This is to ensure the online Nault can't be hacked and giving you false information like the wrong balance or destination. If the data don't match, the final block will never be accepted by the network.
You can also optionally chose to include proof of work here, but if not done it will automatically be included in the final online step. If the data is correct, accept and sign the block with the methods provided. A secure method here would be to use the Ledger device or scan the seed, mnemonic or private key from a paper wallet. But having a wallet set up in Nault already encrypted with a password is arguably even more safe since it's completely offline. The password you chose should be brute-force proof.
![](/images/security_06.png)
![](/images/security_07.png)

1. The final step is to read back the signed block in the **online** Nault using either the QR reader or manually copy it by other means using the [remote signing page](https://nault.cc/remote-signing).
Now, you just confirm and process! The block will be published and proof of work included if it was not done in the offline device.
![](/images/security_08.png)

1. You can view the result in the block explorer and optionally also do the same procedure for any incoming transactions by pressing the "REMOTE SIGN" button in the table.
![](/images/security_09.png)
![](/images/security_10.png)