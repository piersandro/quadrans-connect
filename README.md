<div align="center">
  <img src="https://www.quadrans.io/assets/brand/logo_quadrans_color.svg"><br>
</div>

-----------------

## Quadrans Connect

Easily switch between Quadrans Networks from [here](https://quadrans.github.io/quadrans-connect/#/).

[![Telegram](https://shields.io/badge/telegram-join-16173D?logo=telegram&style=flat)](https://t.me/quadrans)
[![Discord](https://shields.io/badge/discord-join-16173D?logo=discord&style=flat)](https://discord.gg/2bMpuU9Z)
[![Reddit](https://shields.io/badge/reddit-join-16173D?logo=reddit&style=flat)](https://reddit.com/r/quadrans)

**[Quadrans](https://quadrans.io)** **Connect** it's not just an useful tool to add Quadrans networks to your Metamask, it's a [VueJS](ttps://vuejs.org/) boilerplate to create dApps on Quadrans Blockchain.

## Building Quadrans Connect

Prerequisites

Building Quadrans Connect requires [NodeJS 14+](https://nodejs.org/en/) installed in your local computer. You can install them using your favourite package manager or follow official documentation. Once you have NodeJS installed you can follow those instructions:

```
sudo npm install -g yarn
git clone https://github.com/quadrans/quadrans-connect/
cd quadrans-connect
yarn
```

Once the dependencies are installed, run following command to run local server and start making changes to create your dApp:

```
yarn serve
```

or, to build for production run:

```
yarn build
```

## Deploy your dApp to web server

After you've successfully created and built your dApp you can deploy it in any standard hosting or web server by uploading the `dist` folder.

## Deploy your dApp to IPFS

If you want to publish the dAPP to [IPFS](https://ipfs.io/) you can follow those steps. Of course be sure you have installed [command line tools](https://docs.ipfs.io/install/command-line/) before follow the steps.

```
yarn build
ipfs daemon
ipfs add -r dist
```

You will receive a response like this one:

```
added QmcvoQG771qk55HSXRMp321Exh3jtZqArJ8B7LXqavbRrU dist/css/app.fc2324d3.css
added QmYgKkhSdN5LpgrQeW78FTqyTVVwnpD4u4qDCCcnMsGAYy dist/css/chunk-vendors.7ef2ddfa.css
added QmfXDwR65nAkAN9muTXqeCdy13KPygYFUn4zHMdPfzqZH9 dist/favicon.png
added QmezrzFHDS6j3A9tuGBMkB6EKyQkEUjfrnvqhZXhBA9gDc dist/img/logo.b96028a6.svg
added QmTshoEXJ1BVbxfMqNngt2wGDYVDwUJAoTyBWgB1skyvPn dist/index.html
added QmTJQMXbuAQfnGzngKg9XFfK2cHLYvPY9AafhYiUYBEHGd dist/js/app.a5c87132.js
added QmWeKhXPZZMPhRFbChBG61w6jT69p66w4HC8nXGk42h22S dist/js/app.a5c87132.js.map
added QmbkCSyAg6GyNsL3RgU8quwP6a9mK3k9Af2QFg5YsHkzHf dist/js/chunk-vendors.2d724254.js
added QmbQg6mpmi1oPTXanPX82dr9JXSXJPbPkCBoYJvbJBXjk4 dist/js/chunk-vendors.2d724254.js.map
added QmURdei4Wpwvx39zn2r7MNC8H2bZ3u1Ssky2oS7fRebJNc dist/robots.txt
added QmWuPhP8u3aSNpPXtDX68J1uWJ7x6wNXYanAaHx4gwDZ9C dist/css
added QmQkYA7h4sUr9wrUzajJgsYaFE9VQHNSumTVqahEccFmsV dist/img
added QmRX4GijnZcoho4FsDxyJKdxRkxeH79YE4cKnVu1SetZis dist/js
added QmXqoCCmu6p185dxE36ZUSKitK2QWUQGrxU2YkT5NNH1HF dist
 7.89 MiB / 7.89 MiB [================================================================================================================================================================================================================================================] 100.00%
 ```

That's it! Be sure your local node can reach the public IPFS network (check your firewall rules) and you will be able to see your dApp following the last CID: https://ipfs.io/ipfs/QmXqoCCmu6p185dxE36ZUSKitK2QWUQGrxU2YkT5NNH1HF

## Contribute

Thank you for considering to help out with the source code! We welcome contributions from anyone on the internet, and are grateful for even the smallest of fixes!

If you'd like to contribute to **Quadrans Connect**, please fork, fix, commit and send a pull request for the maintainers to review and merge into the main code base. If you wish to submit more complex changes though, please check up with the core devs first on our [Discord](https://discord.gg/2bMpuU9Z), [Telegram](https://t.me/quadrans) or [Reddit](https://reddit.com/r/quadrans) channels to ensure those changes are in line with the general philosophy of the project and/or get some early feedback which can make both your efforts much lighter as well as our review and merge procedures quick and simple.

Please make sure your contributions adhere to our coding guidelines:

 * Code must adhere to the official [Code of Conduct](https://quadrans.io/f/code-of-conduct).
 * Pull requests need to be based on and opened against the `main` branch.
 * Commit messages should be prefixed with the package(s) they modify.
   * E.g. "eth, rpc: make trace configs optional"

## License 

This repository is licensed under MIT license.