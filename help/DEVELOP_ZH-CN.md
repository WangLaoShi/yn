# 开发环境搭建指南

[English](./DEVELOP.md) | 中文

## 开发环境搭建

### 安装 node 系列环境

> 首先你需要确保你的电脑上有一个可以运行的 `node` 环境，推荐[安装教程地址](https://www.runoob.com/nodejs/nodejs-install-setup.html)

> 这个情况下，不需要一定保证 Node 的具体版本，可以使用最新的版本，下面会有一个办法来切换版本。
> 
### 安装 n，进行版本切换

`n` 是 `node` 的版本控制软件可以随意切换 `node` 版本，因为 `yn` 需要 12.0 以上的版本可以用
`n` 进行切换

查看当前node版本：

`node –v`

安装n模块

`npm install -g n`

升级到指定版本/最新版本（该步骤可能需要花费一些时间）升级之前，可以执行 n ls （查看可升级的版本）
`n v16.0.0`

> 按照 yn 官方的 Actions 中的说明，使用的是 v14 版本，经过测试，也是 14 版本比较好用。wanglaoshi 使用的是 **v14.19.2**

> n v14.19.2

或者你也可以告诉管理器，安装最新的稳定版本
`n stable | n latest`

### 安装依赖

`yarn install`

注意，有时并不能成功的安装所以的依赖，所以需要一个一个手动安装
这时只需要 `npm install package@version` 如 `npm install mine@2.5.2`

> 这里有一个小问题是，一定要从 package.json 中找到这个包的详细版本，而不是简单的 `npm install typescript`，否则带来的版本管理问题会让你的脑仁疼 

有时候electron和node-pty模块不能简单的安装成功，可以像下面介绍的那样进行操作

### 安装electron

electron 的官方源头和介绍如下： https://www.npmjs.com/package/electron

[找到 Electron 和 nodejs 的对照关系](https://releases.electronjs.org/history)

比喻说：

![NHYk08](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/NHYk08.png)

推荐采用淘宝源进行下载

设置源

`npm config set electron_mirror http://npm.taobao.org/mirrors/electron/`

设置下载的electron版本

`npm config set electron_custom_dir "16.0.0"`

这里的16.0.0 是指当前node对应的版本具体的版本可以在
http://npm.taobao.org/mirrors/electron

指定版本安装

`npm install electron@16.0.0`

### 安装electron-rebuild
`npm install --save-dev electron-rebuild`

### 重新编译pty

`npm run rebuild-pty`

### 启动调试
`npm run dev`


## 具体步骤

1. Clone

'git clone https://github.com/purocean/yn.git'

> 注意：官方的默认分支是 `develop`

2. 安装和调整 node 版本

> 安装请参考上面的过程

[也可以使用 nvm 来进行版本管理](https://github.com/nvm-sh/nvm#install--update-script)

[nvm 的使用方法](https://github.com/nvm-sh/nvm#usage)

`node -v`

![3IXQLo](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/3IXQLo.png)

3. 安装 `yarn`

![ETMY44](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/ETMY44.png)

全局安装 yarn


4. 在本项目目录安装 electron 和 electron-rebuild

![IXdcbM](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/IXdcbM.png)

但是，到这一步，注意一点，package.json 中的 electron 的版本号会改。

![OMkTyV](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/OMkTyV.png)


下面是安装 `electron-rebuild`

![zpgKIn](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/zpgKIn.png)

之后 package.json 会改变

![kYybY2](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/kYybY2.png)

5. 执行 `yarn install` 安装需要的包

这个是根据 package.json 安装需要的包

这里经常会出现一个问题，有些包，下载不下来。

![hiaSbb](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/hiaSbb.png)

![5EzqRl](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/5EzqRl.png)

**yarn 切换 设置 镜像 源**


1、查看一下当前源

<pre class="brush:javascript;gutter:true;">
yarn config get registry
</pre>

2、切换为淘宝源

<pre class="brush:javascript;gutter:true;">
yarn config set registry https://registry.npm.taobao.org
</pre>

3、或者切换为自带的

<pre class="brush:javascript;gutter:true;">
yarn config set registry https://registry.yarnpkg.com
</pre>

![NTsDMM](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/NTsDMM.png)

6. 生成 pty

```
npm run rebuild-pty
```

7. build

```
yarn build
```

8. 运行 Electron

```
yarn start
```

![MPsB66](https://upiclw.oss-cn-beijing.aliyuncs.com/uPic/MPsB66.png)

使用 Electron 打开的视图

9. 开发

```
yarn dev
```



