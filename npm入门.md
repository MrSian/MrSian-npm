### 1 简介

[npm](https://www.npmjs.cn/getting-started/what-is-npm/)是一个包管理工具，包括三个部分：

- [网站](https://www.npmjs.com/)：展示、查找各种包（代码模块，package）及其使用方法，设置参数以及管理npm使用体验的平台

- 注册表（registry）：是一个巨大的数据库，保存了每个包的信息

- 命令行工具（CLI）：用来直接使用npm

### 2 安装和使用

由于npm是用Node.js写的，因此要安装Node.js来使用npm。  
最快捷的安装方式是从Node.js[官网](https://nodejs.org/en/download/)直接下载安装Node.js，npm也会自动安装。  
安装后运行以下命令以检测是否安装成功：  
\$ node \-v // 查看Node.js版本  
\$ npm \-v // 查看npm版本

安装成功后，直接运行npm的各种命令来下载、删除、发布包等，例如安装一个第三方包：  
\$ npm install \<package\_name> // 会在当前目录下创建一个  
node\_modules 的目录，并将下载的包保存在该目录下。

### 3 package.json文件

该文件用来描述一个项目所需要用到的所有依赖包及其版本号。 必须包含name和version属性：

```
运行以下命令来创建一个package.json文件：
$ npm init  // 创建一个package.json文件，创建过程中会有一系列关于需要怎样创建package.json的问题需要回答
$ npm init --yes/-y  // 传建一个默认的package.json文件
复制代码
```

一个默认的paskage.json文件：

```
{
  "name": "my_package",  // 当前目录的名字，这个package的名字
  "description": "",  // README.md文档内容的第一行，如果没有 README.md则为空字符串, README.md描述了这个项目的相关信息，有利于npm检索
  "version": "1.0.0",  // 当前版本
  "main": "index.js",  // 入口文件
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/ashleygwilliams/my_package.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/ashleygwilliams/my_package/issues"
  },
  "homepage": "https://github.com/ashleygwilliams/my_package"
}
复制代码
```

可以设置字段值：  
\$ npm set init.author.email "example\@[npmjs.com](http://npmjs.com/)"  
还可以自定义npm init过程中的问答：在家目录下创建一个 .npm-init.js文件自定义问答内容，详见：[github.com/npm/init-pa…](https://github.com/npm/init-package-json)

package.json使用dependencies和devDependencies两个属性用来描述项目所需依赖包：

```
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {  // 生产环境需要用到的依赖包
    "my_dep": "^1.0.0"  // 依赖包的版本号描述使用语义版本(SemVer)语法
  },
  "devDependencies" : {  // 本地开发环境需要用到的依赖包
    "my_test_framework": "^3.1.0"
  }
复制代码
```

不同环境需要用到的依赖包安装方法：  
\$ npm install \<package\_name> \--save // 安装到dependencies  
\$ npm install \<package\_name> \--save-dev // 安装到devDependencies  

# 4 管理本地安装的包

\$ npm update // 更新  
\$ npm uninstall \<package\_name> // 删除  
\$ npm uninstall \--save lodash // 删除package.json文件中dependencies的依赖  
\$ npm uninstall \--save-dev lodash // 删除package.json文件中devDependencies的依赖  
\$ npm install \-g // 安装全局包，如果是命令行工具，应该要全局安装  
\$ npm update \-g // 更新全局包  
\$ npm update \-g // 更新全部全局包  
\$ npm outdated \-g \--depth=0 // 检测那些包需要更新  
\$ npm install npm\@latest \-g // 更新npm  
\$ npm uninstall \-g // 删除全局包  

# 5 发布更新一个包

可以将任何一个包含package.json文件的目录发布到npm中，只有添加到.gitignore或.npmignore中的文件不会被发布到npm上。

## 5.1 发布

首先要在[官网](https://www.npmjs.com/)注册一个npm账号，注册成功后：  
\$ npm login // 登录npm  
\$ npm whoami // 查看当前登录用户以检查是否登录成功

有两点注意：

- 包的名字要唯一并且和包的功能相关
- 添加[readme.md](http://readme.md/)文档便于被优先检索到

\$ npm publish // 发布到npm  
发布时如果提示“ You do not have permission to publish "\<package\_name>". Are you logged in as the correct user\? :\<package\_name>”  
就说明npm上已有同名的包了，需要修改package.json的name字段值。发布成功后就可以在官网上看到自己的包了。

## 5.2 更新包

开发完执行以下命令可以更新包，注意由于reamme.md文档内容会展示在npm官网中该package的详情页面，在更新package时如果有需要也要同步更新readme。

\$ npm version \<update\_type> // 更新  
update\_type有三种类型：patch、minor、major（更多语义化版本的介绍详见：[docs.npmjs.com/about-seman…](https://docs.npmjs.com/about-semantic-versioning)）：

- patch：会增加第三个版本号，表示向后兼容的bug修复
- minor：会增加第二个版本号，表示向后兼容的新特性
- major：会增加第一个版本号并重置后两个版本号，变为x.0.0，表示向后不兼容的重大变更

版本号更新后再执行 \$ npm publish

<!---->