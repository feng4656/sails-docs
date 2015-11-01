# 第一次接触 [Node.js](https://soundcloud.com/marak/marak-the-node-js-rap)？
没关系！我们将指引你往正确的方向迈进。


依 [nodejs.org](http://nodejs.org) 表示：
> "Node.js 是一个建构于 Chrome 的 Javascript 执行期平台，可方便地建立快速、可扩充的网路应用程序。Node.js 采用事件导向、非阻塞 I/O 模型，使得它轻量、高效能，非常适合在分散式装置上执行的数据密集型即时应用程序。"

更简单地说，Node.js 是个快速、有效率且允许你同时在前端及后端使用相同语言的 http 服务器。

##我需要什么操作系统？

Node.js 可安装于大多数主流操作系统。MacOSX、许多类型的 Linux 及 Windows 皆有支持。

现在，请从下列选择有关设置 Node.js 的说明：

我有 [Mac OSX](#/getStarted?q=--install-on-osx-)

我有 [Linux](#/getStarted?q=--install-on-linux-)

我有 [Windows](#/getStarted?q=--install-on-windows-)

<h2>
<a id="install-on-osx" name="/getStarted?q=--install-on-osx-" class="anchor" href="#/getStarted?q=--install-on-osx-"><span class="mini-icon mini-icon-link"></span></a>
安装在 OSX
</h2>

使用[软件包](http://nodejs.org/download/)：

_只需[下载 Macintosh Installer](http://nodejs.org/download/)。_

使用 [homebrew](https://github.com/mxcl/homebrew)：

```
brew install node
```

使用 [macports](http://www.macports.org/)：

```
port install nodejs
```

<h2>
<a id="install-on-linux" name="/getStarted?q=--install-on-linux-" class="anchor" href="#/getStarted?--install-on-linux-"><span class="mini-icon mini-icon-link"></span></a>
安装在 Linux
</h2>

### Ubuntu、Mint

安装例子：

```
sudo apt-get install python-software-properties python g++ make
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs
```

它安装了目前在稳定版 Ubuntu 的稳定版 Node。Quantal（12.10）使用者可能需要安装 *software-properties-common* 套件让 `add-apt-repository` 指令可正常执行：`sudo apt-get install software-properties-common`

自 Node.js v0.11.*.0 起，从 [Chris Lea](https://chrislea.com/2013/03/15/upgrading-from-node-js-0-8-x-to-0-10-0-from-my-ppa/) 的储存库来的 nodejs 套件同时包含了 npm 和 nodejs-dev。

存在与 node 套件的命名冲突（Amateur Packet Radio Node Program），且 nodejs 二进位文档已经由 `node` 重新命名为 `nodejs`。你需要建立软连结 `/usr/bin/node` 到 `/usr/bin/nodejs`，或者可以移除 Amateur Packet Radio Node Program 以避免冲突。

### Fedora

Fedora 18 及更高版本提供 [Node.js](https://apps.fedoraproject.org/packages/nodejs) 和 [npm](https://apps.fedoraproject.org/packages/npm)。只需用你喜欢的图形界面软件包管理工具或在终端机执行以下指令来安装 node 及 npm：

```
sudo yum install npm
```

### RHEL/CentOS/Scientific Linux 6

[Fedora Enterprise Linux 附加软件包 (EPEL)](https://fedoraproject.org/wiki/EPEL) _测试_储存库提供 Node.js 和 npm。如果你还没有这样做，首先[启用 EPEL](https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F) 然后执行以下指令来安装node 及 npm：

```
su -c 'yum --enablerepo=epel-testing install npm'
```

### Arch Linux
社区储存库提供 Node.js。

```
pacman -S nodejs
```

### Gentoo
官方 gentoo portage 树提供 Node.js。你必须解除封锁它。

```
# emerge -aqv --autounmask-write nodejs
# etc-update
# emerge -aqv nodejs
```

### Debian、LMDE

*Debian sid（不稳定版）*，[官方储存库提供 Node.js](http://packages.debian.org/search?searchon=names&keywords=nodejs)。

*Debian Wheezy（稳定版）*，[wheezy-backports 提供 Node.js](http://packages.debian.org/wheezy-backports/nodejs)。要安装 [backports](http://backports.debian.org/Instructions/)，将此源加入你的源清单（`/etc/apt/sources.list`）：

```
deb http://YOURMIRROR.debian.org/debian wheezy-backports main
```

然后执行：

```
apt-get update
apt-get install no
```