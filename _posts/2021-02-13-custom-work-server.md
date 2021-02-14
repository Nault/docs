# Custom Work Server

The default option in Nault is to generate proof of work from the backend servers. 
That, in turn, is using services such as [dPoW](https://github.com/guilhermelawless/nano-dpow) and [boomPoW](https://github.com/BananoCoin/boompow). 
That is fine for most users but it comes with limitations.

The services can be offline or you want to do higher multiplier than what's allowed. 
As a backup, Nault has also supported local CPU or GPU PoW using the browser.

A third option is to use a custom work server running either remotely or localhost. The official work server has been tested with an RTX 2080 GPU with normal 1x pow comnputed in 0.25sec compared to around 5sec with webGL PoW. 
64x pow can be made in 16sec on average.
This can be useful if the network is saturated for example and you want higher priority on your transactions.

============================
## Table of Contents

1. TOC
{:toc}

============================

## Features

* Supports any node, work server or compatible API
* Huge speed improvement of 10-40x compared to webGL
* Allows custom multiplier up to 64x
* Works in both web and desktop app (with limitations mentioned below)
* Future-proof in case of the work algorithm changes and webGL can't be done

## How To

### Work Server

[Download the latest work server](https://github.com/nanocurrency/nano-work-server/releases/latest) and start it e.g. with your default GPU on port 9999:

    nano-work-server.exe -g 0:0 -l 127.0.0.1:9999

Example using both GPU and 12 CPU cores:

    nano-work-server.exe -g 0:0 -c 12 -l 127.0.0.1:9999

Full instructions: 

    nano-work-server.exe --help

### Nault Settings

Specify the work server in the Nault app settings e.g.: 

    http://127.0.0.1:9999

![](/images/custom-work-server.png)

## Limitations

Nault web app will not allow direct connection to `127.0.0.1` due to CORS policy. 
To get that working you have to use a local proxy server that allows cross-origin calls. 
In Apache that's just a `Header set Access-Control-Allow-Origin "*"`

The desktop app works fine with any work server source.
