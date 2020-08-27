> npm是安装node时自带的包管理工具。

> npm包有很多的镜像源，nrm是切换不同的镜像源的工具，切换后还是用npm安装。

> yarn是facebook公司开发的替代npm的包管理工具，是需要额外安装的，用来解决npm的一些毛病。从工具的使用上理解，yarn与npm是一样的，如果你安装了yarn，那一般都使用yarn，因为它更快更好。

# npm

NPM是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题，常见的使用场景有以下几种：

- 允许用户从NPM服务器下载别人编写的第三方包到本地使用。
- 允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用。
- 允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。

> 由于新版的nodejs已经集成了npm，所以之前npm也一并安装好了。同样可以通过输入 "npm \-v" 来测试是否成功安装。命令如下，出现版本提示表示安装成功:

![](https://user-gold-cdn.xitu.io/2019/11/22/16e92103f8355854?imageView2/0/w/1280/h/960/ignore-error/1)

> 你安装的是旧版本的 npm，可以很容易得通过 npm 命令来升级

```
npm install npm -g
复制代码
```

> 使用淘宝镜像的命令：

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
复制代码
```

## 1.使用 npm 命令安装模块

> npm 安装 Node.js 模块语法格式如下：

```
npm install <Module Name>
复制代码
```

## 2.全局安装与本地安装

> npm 的包安装分为本地安装（local）、全局安装（global）两种，从敲的命令行来看，差别只是有没有-g而已

```
npm install express          # 本地安装
npm install express -g       # 全局安装
复制代码
```

本地安装

- 1.  将安装包放在 ./node\_modules 下（运行 npm 命令时所在的目录），如果没有 node\_modules 目录，会在当前执行 npm 命令的目录下生成 node\_modules 目录。
- 2.  可以通过 require\(\) 来引入本地安装的包。

全局安装

- 1.  将安装包放在 /usr/local 下或者你 node 的安装目录。
- 2.  可以直接在命令行里使用。

## 3.卸载模块

> 我们可以使用以下命令来卸载 Node.js 模块。

```
npm uninstall express
复制代码
```

> 卸载后，你可以到 /node\_modules/ 目录下查看包是否还存在，或者使用以下命令查看：

```
npm ls
复制代码
```

## 4.更新模块

```
npm update express
复制代码
```

## 5.搜索模块

```
npm search express
复制代码
```

# nrm

> **npm包有很多的镜像源，有的源有的时候访问失败，有的源可能没有最新的包,有的要使用公司内部的源，所以有时需要切换npm的源，nrm包就是解决快速切换问题的。**

## 1.安装

```
npm install -g nrm
复制代码
```

> 查看是否安装成功

```
nrm --version
复制代码
```

## 2.使用

### 2.1、列出可选择的源

![](https://user-gold-cdn.xitu.io/2019/11/22/16e9223bfccc7005?imageView2/0/w/1280/h/960/ignore-error/1)

**注： 前面带 \* 号的表示正在使用的源**

### 2.2、切换使用的源

![](https://user-gold-cdn.xitu.io/2019/11/22/16e92261313e4f62?imageView2/0/w/1280/h/960/ignore-error/1)

### 2.3、添加一个源

```
如果你想添加一个源，终端执行命令nrm add <registry> <url> [home]，reigstry为源名，url为源的路径， home为源的主页(可不写)

* URL最后的/也可以不带，下面两个URL都是可以的：
* http://npm.company.com/
* http://npm.company.com
复制代码
```

![](https://user-gold-cdn.xitu.io/2019/11/22/16e922a951d5579e?imageView2/0/w/1280/h/960/ignore-error/1)

### 2.4、删除一个源

```
终端执行命令nrm del <registry>，reigstry为源名
复制代码
```

![](https://user-gold-cdn.xitu.io/2019/11/22/16e922df75227cd6?imageView2/0/w/1280/h/960/ignore-error/1)

### 2.5、测试源速度

> 测试一个源的响应时间：nrm test npm

![](https://user-gold-cdn.xitu.io/2019/11/22/16e922f13780f914?imageView2/0/w/1280/h/960/ignore-error/1)

> 测试所有源的速度：nrm test

![](https://user-gold-cdn.xitu.io/2019/11/22/16e922ff27dc9b70?imageView2/0/w/1280/h/960/ignore-error/1)

### 2.6、访问源的主页

```
nrm home taobao
// 此命令会在浏览器中打开淘宝源的主页：https://npm.taobao.org/
复制代码
```

> 如果要查看自己添加的源的主页，那么在添加源的时候就要把主页带上：

```
nrm add company http://npm.company.com/ http://npm.company.com/
// 如果添加源的时候没有写home信息，那么nrm home命令不会有效果
复制代码
```

# Yarn

> yarn是快速、可靠、安全的包依赖管理工具。是与npm功能一致的工具。只是npm是安装node时自带的，而yarn是需要额外安装的。

> yarn的出世是因为npm有不少毛病，而facebook公司的程序员们鉴于这些毛病开发了yarn来取代npm。

> 看官网介绍及使用教程 [yarnpkg.com/zh-Hans/](https://yarnpkg.com/zh-Hans/)

**所以有更好用的工具，那我们开发中一般用yarn，官网有很详细的使用教程，下面我截取下npm与yarn的cli命令比较**

![](https://user-gold-cdn.xitu.io/2019/11/25/16ea146864037048?imageView2/0/w/1280/h/960/ignore-error/1)

<!---->