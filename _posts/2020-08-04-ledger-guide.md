# How to use the Ledger Nano in Nault

If you have a Ledger device, you can use it with [Nault](https://nault.cc/) to securely access and send your Nano. Paired together, it is the safest and yet highly convenient way to send and receive Nano! Using this guide you can learn everything needed to send and receive Nano on your Ledger device with Nault.

![Ledger Nano X](/images/ledger_x.jpeg)

============================
## Table of Contents

1. TOC
{:toc}

============================
## Installing The Nano Application

1. Connect your Ledger device via USB to your computer and use your PIN to unlock it. If it hasn't been set up yet, follow [this procedure](https://support.ledger.com/hc/en-us/articles/360000613793-Set-up-as-new-device).
![](/images/ledger_pin.jpg)


1. Open the [Ledger Live](https://www.ledger.com/ledger-live/) and choose how to connect your device.
![](/images/ledger_01.png)


1. Open the Ledger Live Manager.
![](/images/ledger_02.png)


1. Confirm on the device to allow the Ledger Manager. Search for nano and install. When the nano app has been installed you should close Ledger Live because a Nano wallet is not yet supported from inside the application. You will use nault.cc for that.
![](/images/ledger_03.png)


1. Open the Nano application on your Ledger device, you should see ‘Use wallet to view accounts’. If so, you are ready to go!
![](/images/ledger_app.jpg)

============================
## Configuring Your Ledger With Nault

{% include alert.html text="To be able to use your Ledger device with the web wallet, it's recommended to use a Chrome, Brave or Opera browser, and the Ledger Manager application must be closed. There may be an annoying pop-up in Windows 10 so it's even more recommended to use the desktop version found <a href='https://github.com/Nault/Nault/releases'>here</a>." %}

1. Make sure the Nano app on the Ledger device is started, referring to the last point from previous chapter.

1. From Nault.cc, choose the option to ‘Import An Existing Wallet’, and then select the ‘Ledger Nano S’ option from the import type dropdown. Ledger Nano X should work as well even if you choose S. If the device is not detected, try exit and re-open the Nano app on the device or switch USB-port or even try a new cable. Then just hit the "refresh ledger status button" in Nault.
![](/images/ledger_04.png)

1. Once the Ledger is detected, your Nano account will be imported into Nault and your wallet is ready to use! If you have been using more Nano accounts in the Ledger, they should be detected and imported as well.
{% include alert.html text="Other wallets supporting Ledger and Nano (or import of the Ledger mnemonic) may not support the use of multiple Nano accounts. So keep that in mind if you choose to use more than one account (at index 0)." %}
![](/images/ledger_05.png)

============================
## Your Ledger Status

On the left navigation, you can find the current status of your Ledger device. When it is not connected, you will be unable to sign any new transactions or add new accounts. If the device status seems wrong, you can click on it to attempt to reconnect to the Ledger device. Your Ledger will only be marked as ready when it is unlocked and the Nano application is open.
![](/images/ledger_06.png)

============================
## Using Nault to Send, Receive or Change representative via the Ledger
Once your ledger wallet is imported, you can use the ‘Accounts’ page to view the current status of all your Nano accounts. By clicking on one of your accounts, you can view the full details including transaction history.

{% include alert.html text="Before accepting any transaction with the Ledger button, always verify the amount and destination on the device display. This is YOUR responsibility of making sure everything is in order." %}

### Sending Nano

1. Open the ‘Send’ page from the left navigation
1. Select the account you would like to send from and enter the address of the Nano account you would like to send to (Or select a contact from your address book)
1. Enter the exact amount of Nano you would like to send (Or use the FIAT input below to have it automatically converted)
1. Press ‘Send Nano’, then use the confirmation page to ensure the destination and amount are correct.
1. If they are, press ‘Confirm Transaction’ which will send the transaction information to your Ledger device.
1. On your Ledger device, ensure that the destination and amount look accurate, then use the buttons on your Ledger device to confirm or deny the transaction.
![](/images/ledger_07.png)

### Receiving Nano
By default, Nault will attempt to receive incoming transactions automatically. This means that when leaving the wallet open, or re-opening it, incoming transactions will be sent to your Ledger device for on-device confirmation as soon as possible. Most of the time, you should not have to worry about manually receiving a transaction, but if it gets stuck or you have set Nault to "Manual Receive" in the app settings, you can use the following process:

1. Open the ‘Receive’ page from the left navigation
1. Press the ‘Receive’ button on the transaction you want to approve. This will trigger a confirmation on your Ledger device.
1. On your Ledger device, ensure that the transaction information looks correct, then use the buttons on your Ledger device to confirm or deny the transaction.

{% include info.html text="There is also a setting in the Nano app on the Ledger as well called auto-receive. That will skip the manual approval on the device. If you can't receive a transaction, try change this setting. It has happened it's not working properly." %}
![](/images/ledger_08.png)

### Changing Your Representative
If you want to change your account's representative, or if Nault has detected you are using a rep not optimal for the Nano network, you can easily do so from the settings/Representatives or from the Account view for any of your accounts.

1. Easiest way is to go to settings -> Representatives
1. Select one of your accounts (or all) that you want to change
1. Paste any representative account or select one from the Nault recommendations
1. Press the update button and confirm on the Ledger device
![](/images/ledger_09.png)

You can also find what representative you are using for individual accounts via the ‘Accounts’ page. Also change them with the edit button.
![](/images/ledger_10.png)

============================
## Final Words
With that information, you are ready to store Nano with your Ledger Device and access it easily at any time using Nault! Besides just supporting Ledger devices, Nault also adds in lots of helpful features such as local currency values, a fully integrated address book, QR-reader, offline signing capabilities and more which make sending and receiving Nano simple and secure.

### Data Storage
Nault does not store any information about you on a server. The only information stored is in your local browser storage (if not set the app setting to delete it when the browser is closed, or using an incognito tab) which allows you to use your wallet more easily on subsequent visits. With a Ledger device, the only information stored is your public account addresses, since that is the only information exposed by the Ledger device. It's also recommended to secure your Nault wallet with a password and lock it everytime you are done with it. That way your funds can only be accessed with the password.

============================
## Troubleshooting
Some Ledger problems are not related to Nault but to the device itself and limited compatibility.

### Failed to connect the ledger in Nault
If you get errors while importing the ledger or when reconnecting to it, try one or several of the following most common issues. Make sure to reload the Nault app or web page after each step.

* Close other application that may disturb, especially Ledger Live, other running Nault or crypto wallets.
* Make sure the Nano app in the Ledger is running, or restart it.
* Use the latest [Nault desktop app](https://github.com/Nault/Nault/releases). The Ledger protocol used in the Desktop app is usually less sensitive compared to the web version as well. At least try with another browser. Chrome is usually the best one. Latest Edge, Brave and other Chromium based browsers work well too. Firefox currently uses an older protocol but could be more stable.
* Change USB port. It can be in bad shape or just changing from USB2/USB3 or vice versa can help. Try a port that is directly from the computer motherboard, no hubs.
* Change USB cable. A low-quality or very long cable can be problematic. We recommend using the one the came with the Ledger.
* Restart the computer or try with another. Open ledger live and manager to make sure the Ledger works. Upgrade to the latest Ledger firmware. Try a different operating system.

More info in [this video](https://youtu.be/Ob2v02uDCuM)

### Failed to connect using Bluetooth
* PC: Requires [BLE](https://en.wikipedia.org/wiki/Bluetooth_Low_Energy) support
* Android: Currently not supported

### Annoying popup
This is a Windows thing when using the legacy U2F protocol. Usually seen in Firefox or older browsers. Try to use the latest [Nault desktop app](https://github.com/Nault/Nault/releases). The Ledger protocol used in the Desktop app is usually less sensitive compared to the web version as well. At least try with another browser. Chrome is usually the best one. Latest Edge, Brave and other Chromium based browsers work well too.

### The transactions are not received

* There is a setting in the device Nano app that enables automatic receive. Then another setting in Nault app settings for automatic receive. If enabling both of them still doesn't work, go to the "Receive screen" in Nault and manually receive the transaction. That is usually the preferred method when dealing with the Ledger to avoid getting spam transactions.
* It could be an error with the backend server or heavy network traffic going on that has introduced a delay. Try changing to another server from the app settings. More info [here](https://docs.nault.cc/2020/12/02/advanced-features.html). You can also copy your account and open it in another block explorer like [nanocrawler](https://nanocrawler.cc/) to verify the pending/incoming transaction.

### The wallet shows zero balance
Do not panic, this is a common error. If no one else has access to your Ledger backup mnemonic or PIN code, the funds are going nowhere.

* Make sure the Ledger is connected. Should be a green notification.
* Go to the account screen. Make sure the account displayed are the one you sent Nano to. Click on it to check the history. If the account is missing, try "Add new account" or several like 20. If it still doesn't show, you have not sent Nano to the Ledger but to an account that belongs to another seed not stored in the Ledger. You need to find that and import to Nault.
* It could be an error with the backend server or heavy network traffic going on that has introduced a delay. Try changing to another server from the app settings. More info [here](https://docs.nault.cc/2020/12/02/advanced-features.html). You can also copy your account and open it in another block explorer like [nanocrawler](https://nanocrawler.cc/) to verify the balance.

