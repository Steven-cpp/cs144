# CS144 实验记录

为了加强自己对计算机网络的理解，为后续参与网络服务器项目的开发打好基础，我决定要在 1 个月内完成 CS144 的实验任务，每天至少**花 2 小时**在这一任务上面。

## I. Network Warmup

我在 Mac 上使用 UTM 配置好了实验所需的 Ubuntu 环境，由于浏览器的各种异常，我放弃了安装 VS Code 的想法，决定只用命令行，体验原汁原味的 Linux 开发过程，并且<u>记录下在这一过程中用到的各种指令</u>。

但是在实际使用的时候产生了诸多不便，比如说图形界面的体验比较差 (显示分辨率、快捷键)，浏览器界面元素显示异常，复制、粘贴操作不畅并且按键不统一，等等这些问题，实在是劝退了我。于是我决定用 Docker 配置开发环境，然后果然找到了这一插件，下面记录了该环境的配置过程：

- **在 VSCode 中使用 Docker 配置 Ubuntu 开发环境**

  只要安装 DEV-Container 插件就可以达成像 WIndows 中 WSL 一样的开发体验

- **添加 Git Token**

  实际并没有用到，VSCode 跳出了认证框，直接调用了网页认证。并没有用上这个 Token，也可以进行 push, pull 之类的操作

### 0. Shell 命令

我的 Ubuntu Container 中没有 `cmake` 并且 `g++` 版本太低，至少需要 `g++ >= 8`，于是我首先安装了 `cmake`:

```bash
sudo apt update
sudo apt install cmake
```

然后对 `g++` 进行了升级：

```bash
# 1. 当前g++为7.5
$ g++ --version
g++ (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0
Copyright (C) 2017 Free Software Foundation, Inc.
...

# 2. 安装g++-8
$ sudo apt install g++-8

# 3. 但是现在默认使用的仍为7.5
$ g++ --version
g++ (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0
Copyright (C) 2017 Free Software Foundation, Inc.
...

# 4. 将默认的 g++ link到 g++-8
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 20 --slave /usr/bin/g++ g++ /usr/bin/g++-8
update-alternatives: using /usr/bin/gcc-8 to provide /usr/bin/gcc (gcc) in auto mode

# 5. 链接成功
$ g++ --version
g++ (Ubuntu/Linaro 8.4.0-1ubuntu1~18.04) 8.4.0
Copyright (C) 2018 Free Software Foundation, Inc.
```

### 1. 实现 wget

在这个实验中，我需要使用系统自带的 TCP 协议，创建一个网络 socket，与远程主机建立稳定的字节流通道，抓取一个网页。





























