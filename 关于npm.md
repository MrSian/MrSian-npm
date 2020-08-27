## 一、npm 简介

npm 全称为 Node Package Manager，是一个基于 Node.js 的包管理器，也是整个 Node.js 社区最流行、支持的第三方模块最多的包管理器。

**npm 的初衷：**

JavaScript 开发人员更容易分享和重用代码。

**npm 的使用场景：**

- 允许用户获取第三方包并使用。

- 允许用户将自己编写的包或命令行程序进行发布分享。

**npm 版本查询** npm \-v

**npm 安装：**

1、安装 nodejs

由于新版的 nodejs 已经集成了 npm，所以可直接通过输入 npm \-v 来测试是否成功安装。

2、使用 npm 命令来升级 npm: npm install npm \-g

## 二、npm 的工作原理：

**包和模块**

**什么是包\(package\)\?**

包是描述一个文件或一个目录。一个包的配置通常由以下构成：

- 一个文件夹包含一个 package.json 配置文件。
- 包含（含有 package.json 文件的文件夹）的Ｇ zip 压缩文件。
- 解析 gzip 的 url
- 为注册表添加\@的 url 信息

注意的是即使你从来没有在注册中心发布你的公共包,你可能仍然可以得到很多所有这些 package, 使用 npm 的好处:

- 如果你只是计划想写增加一个节点或/。
- 如果你安装它也希望在其他地方分成一个 tarball 后进行包装

**2.什么是模块（module）\?**

模板是通过配置文件中的一个 dom 节点进行包含一个或多个包。通常一般由包和配置文件以及相关模块程序构成完成一个或多个业务功能操作。

一个模块可以在 node . js 程序中装满任何的 require\(\)任何。 以下是所有事物加载模块的例子 :

- 一个文件夹 package.json 文件包含一个 main 字段。

- 一个文件夹 index.js 文件。

- 一个 JavaScript 文件。

**3.npm 的包和模块的关系：**

一般来说在 js 程序中使用 require 加载它们的模块在节点中进行配置 npm 包，一个模块不一定是一个包。

例如,一些 cli 包, js 程序节点中只包含一个可执行的 命令行界面,不提供 main 字段。 那么这些包不是模块。

几乎所有 npm 包\(至少,那些节点计划\)包含许多模块在他们\(因为每个文件加载 require\(\)是一个模块\)。

几乎所有的 npm 包都关联着多个模块，因为每个文件都使用 require\(\)加载一个模块。

从 module 加载文件中的上下文 node 节点。如：var req = require\('request'\)。我们可能会说,“request 模块赋值给 req 这个变量”。

**4.npm 的生态系统：**

package.json 文件定义的是包。

node_modules 文件夹是存储模块的地方。便于 js 查找模块。

如果创建一个 node_modules/foo.js 文件，通过 var f=require\('foo.js'\)进行加载模块。因为它没有 package.json 文件所以 foo.js 不是一个包。

如果没有创建 index.js 包或者 package.json 文件"main"字段,即使是在安装 node_modules,因为它没有 require\(\)所以它不是一个模块。

# 使用

## npm init

npm init 用来初始化生成一个新的 package.json 文件。它会向用户提问一系列问题，如果你觉得不用修改默认配置，一路回车就可以了。

如果使用了 \-f（代表 force）、-y（代表 yes），则跳过提问阶段，直接生成一个新的 package.json 文件。

```
$ npm init -y
复制代码
```

## npm set

npm set 用来设置环境变量

```
$ npm set init-author-name 'Your name'
$ npm set init-author-email 'Your email'
$ npm set init-author-url 'http://yourdomain.com'
$ npm set init-license 'MIT'
！
复制代码
```

上面命令等于为 npm init 设置了默认值，以后执行 npm init 的时候，package.json 的作者姓名、邮件、主页、许可证字段就会自动写入预设的值。这些信息会存放在用户主目录的 \~/.npmrc 文件，使得用户不用每个项目都输入。如果某个项目有不同的设置，可以针对该项目运行 npm config。

## npm info

npm info 命令可以查看每个模块的具体信息。比如，查看 underscore 模块的信息。

```
$ npm info underscore
复制代码
```

上面命令返回一个 JavaScript 对象，包含了 underscore 模块的详细信息。这个对象的每个成员，都可以直接从 info 命令查询。

```
$ npm info underscore description

$ npm info underscore homepage

$ npm info underscore version

复制代码
```

## npm search

npm search 命令用于搜索 npm 仓库，它后面可以跟字符串，也可以跟正则表达式。

```
$ npm search <搜索词>
复制代码
```

## npm list

npm list 命令以树形结构列出当前项目安装的所有模块，以及它们依赖的模块。

```
$ npm list

# 加上 global 参数，会列出全局安装的模块
$ npm list -global

# npm list 命令也可以列出单个模块
$ npm list underscore
复制代码
```

## npm install

使用 npm 安装包的命令格式为：

npm \[install/i\] \[package_name\]

## 本地模式和全局模式

npm 在默认情况下会从 [npmjs.org](http://npmjs.org) 搜索或下载包，将包安装到当前目录的 node_modules 子目录下。

如果你熟悉 Ruby 的 gem 或者 Python 的 pip，你会发现 npm 与它们的行为不同，gem 或 pip 总是以全局模式安装，使包可以供所有的程序使用，而 npm 默认会把包安装到当前目录下。这反映了 npm 不同的设计哲学。如果把包安装到全局，可以提供程序的重复利用程度，避免同样的内容的多分副本，但坏处是难以处理不同的版本依赖。如果把包安装到当前目录，或者说本地，则不会有不同程序依赖不同版本的包的冲突问题，同时还减轻了包作者的 API 兼容性压力，但缺陷则是同一个包可能会被安装许多次。

我们在使用 supervisor 的时候使用了 npm install \-g supervisor 命令，就是以全局模式安装 supervisor 。

这里注意一点的就是，supervisor 必须安装到全局，如果你不安装到全局，错误命令会提示你安装到全局。如果不想安装到默认的全局，也可以自己修改全局路径到当前路径 npm config set prefix "路径" 安装完以后就可以用 supervisor 来启动服务了。

supervisor 可以帮助你实现这个功能，它会监视你对代码的驱动，并自动重启 Node.js 。

一般来说，全局安装只适用于工具模块，比如 eslint 和 gulp 。关于使用全局模式，多数时候并不是因为许多程序都有可能用到了它，为了减少多重副本而使用全局模式，而是因为本地模式不会注册 PATH 环境变量。

“本地安装”指的是将一个模块下载到当前项目的 node_modules 子目录，然后只有在项目目录之中，才能调用这个模块。

![](https://user-gold-cdn.xitu.io/2019/4/21/16a3f4f7f91c8dfd?imageView2/0/w/1280/h/960/ignore-error/1)

```
# 本地安装
$ npm install <package name>

# 全局安装
$ sudo npm install -global <package name>
$ sudo npm install -g <package name>
复制代码
```

npm install 也支持直接输入 Github 代码库地址。

```
$ npm install git://github.com/package/path.git
$ npm install git://github.com/package/path.git#0.1.0
复制代码
```

安装之前，npm install 会先检查，node_modules 目录之中是否已经存在指定模块。如果存在，就不再重新安装了，即使远程仓库已经有了一个新版本，也是如此。

果你希望，一个模块不管是否安装过， npm 都要强制重新安装，可以使用 \-f 或 \--force 参数。

```
$ npm install <packageName> --force

复制代码
```

## 安装不同版本

install 命令总是安装模块的最新版本，如果要安装模块的特定版本，可以在模块名后面加上 \@ 和版本号。

```
$ npm install sax@latest
$ npm install sax@0.1.1
$ npm install sax@">=0.1.0 <0.2.0"
复制代码
```

install 命令可以使用不同参数，指定所安装的模块属于哪一种性质的依赖关系，即出现在 packages.json 文件的哪一项中。

```
–save：模块名将被添加到 dependencies，可以简化为参数-S。
–save-dev：模块名将被添加到 devDependencies，可以简化为参数-D。

$ npm install sax --save
$ npm install node-tap --save-dev
# 或者
$ npm install sax -S
$ npm install node-tap -D
复制代码
```

## dependencies 依赖

这个可以说是我们 npm 核心一项内容，依赖管理，这个对象里面的内容就是我们这个项目所依赖的 js 模块包。下面这段代码表示我们依赖了 markdown-it 这个包，版本是 \^8.1.0 ，代表最小依赖版本是 8.1.0 ，如果这个包有更新，那么当我们使用 npm install 命令的时候，npm 会帮我们下载最新的包。当别人引用我们这个包的时候，包内的依赖包也会被下载下来。

```
"dependencies": {
    "markdown-it": "^8.1.0"
}
复制代码
```

## devDependencies 开发依赖

在我们开发的时候会用到的一些包，只是在开发环境中需要用到，但是在别人引用我们包的时候，不会用到这些内容，放在 devDependencies 的包，在别人引用的时候不会被 npm 下载。

```
"devDependencies": {
    "autoprefixer": "^6.4.0",0",
    "babel-preset-es2015": "^6.0.0",
    "babel-preset-stage-2": "^6.0.0",
    "babel-register": "^6.0.0",
    "webpack": "^1.13.2",
    "webpack-dev-middleware": "^1.8.3",
    "webpack-hot-middleware": "^2.12.2",
    "webpack-merge": "^0.14.1",
    "highlightjs": "^9.8.0"
}

复制代码
```

当你有了一个完整的 package.json 文件的时候，就可以让人一眼看出来，这个模块的基本信息，和这个模块所需要依赖的包。我们可以通过 npm install 就可以很方便的下载好这个模块所需要的包。

npm install 默认会安装 dependencies 字段和 devDependencies 字段中的所有模块，如果使用 \--production 参数，可以只安装 dependencies 字段的模块。

```
$ npm install --production
# 或者
$ NODE_ENV=production npm install
复制代码
```

一旦安装了某个模块，就可以在代码中用 require 命令加载这个模块。

```
var backbone = require('backbone')
console.log(backbone.VERSION)

复制代码
```

## npm run

npm 不仅可以用于模块管理，还可以用于执行脚本。package.json 文件有一个 scripts 字段，可以用于指定脚本命令，供 npm 直接调用。

package.json

```
{
  "name": "myproject",
  "devDependencies": {
    "jshint": "latest",
    "browserify": "latest",
    "mocha": "latest"
  },
  "scripts": {
    "lint": "jshint **.js",
    "test": "mocha test/"
  }
}

复制代码
```

## scripts 脚本

顾名思义，就是一些脚本代码，可以通过 npm run script-key 来调用，例如在这个 package.json 的文件夹下使用 npm run dev 就相当于运行了 node build/dev-server.js 这一段代码。使用 scripts 的目的就是为了把一些要执行的代码合并到一起，使用 npm run 来快速的运行，方便省事。 npm run 是 npm run-script 的缩写，一般都使用前者，但是后者可以更好的反应这个命令的本质。

```
/ 脚本
"scripts": {
    "dev": "node build/dev-server.js",
    "build": "node build/build.js",
    "docs": "node build/docs.js",
    "build-docs": "npm run docs & git checkout gh-pages & xcopy /sy dist\\* . & git add . & git commit -m 'auto-pages' & git push & git checkout master",
    "build-publish": "rmdir /S /Q lib & npm run build &git add . & git commit -m auto-build & npm version patch & npm publish & git push",
    "lint": "eslint --ext .js,.vue src"
}

复制代码
```

npm run 如果不加任何参数，直接运行，会列出 package.json 里面所有可以执行的脚本命令。 npm 内置了两个命令简写， npm test 等同于执行 npm run test，npm start 等同于执行 npm run start。

```

"build": "npm run build-js && npm run build-css"
复制代码
```

上面的写法是先运行 npm run build-js ，然后再运行 npm run build-css ，两个命令中间用 \&\& 连接。如果希望两个命令同时平行执行，它们中间可以用 \& 连接。

写在 scripts 属性中的命令，也可以在 node_modules/.bin 目录中直接写成 bash 脚本。下面是一个 bash 脚本。

## pre- 和 post- 脚本

npm run 为每条命令提供了 pre- 和 post- 两个钩子（hook）。以 npm run lint 为例，执行这条命令之前，npm 会先查看有没有定义 prelint 和 postlint 两个钩子，如果有的话，就会先执行 npm run prelint，然后执行 npm run lint，最后执行 npm run postlint。

```
{
  "name": "myproject",
  "devDependencies": {
    "eslint": "latest"
    "karma": "latest"
  },
  "scripts": {
    "lint": "eslint --cache --ext .js --ext .jsx src",
    "test": "karma start --log-leve=error karma.config.js --single-run=true",
    "pretest": "npm run lint",
    "posttest": "echo 'Finished running tests'"
  }
}


复制代码
```

上面代码是一个 package.json 文件的例子。如果执行 npm test，会按下面的顺序执行相应的命令。

pretest

test

posttest

如果执行过程出错，就不会执行排在后面的脚本，即如果 prelint 脚本执行出错，就不会接着执行 lint 和 postlint 脚本。

## npm bin

npm bin 命令显示相对于当前目录的，Node 模块的可执行脚本所在的目录（即 .bin 目录）。

```
# 项目根目录下执行
$ npm bin
./node_modules/.bin
复制代码
```

## 创建全局链接

npm 提供了一个有趣的命令 npm link，它的功能是在本地包和全局包之间创建符号链接。我们说过使用全局模式安装的包不能直接通过 require 使用。但通过 npm link 命令可以打破这一限制。举个例子，我们已经通过 npm install \-g express 安装了 express，这时在工程的目录下运行命令：

```
npm link express ./node_modules/express -> /user/local/lib/node_modules/express

复制代码
```

我们可以在 node_modules 子目录中发现一个指向安装到全局的包的符号链接。通过这种方法，我们就可以把全局包当做本地包来使用了。

除了将全局的包链接到本地以外，使用 npm link 命令还可以将本地的包链接到全局。使用方法是在包目录（package.json 所在目录）中运行 npm link 命令。如果我们要开发一个包，利用这种方法可以非常方便地在不同的工程间进行测试。

## 创建包

包是在模块基础上更深一步的抽象，Node.js 的包类似于 C/C++ 的函数库或者 Java、.Net 的类库。它将某个独立的功能封装起来，用于发布、更新、依赖管理和版本控制。Node.js 根据 CommonJS 规范实现了包机制，开发了 npm 来解决包的发布和获取需求。 Node.js 的包是一个目录，其中包含了一个 JSON 格式的包说明文件 package.json。严格符合 CommonJS 规范的包应该具备以下特征：

。package.json 必须在包的顶层目录下； 。二进制文件应该在 bin 目录下； 。JavaScript 代码应该在 lib 目录下； 。文档应该在 doc 目录下； 。单元测试应该在 test 目录下。

Node.js 对包的要求并没有这么严格，只要顶层目录下有 package.json，并符合一些规范即可。当然为了提高兼容性，我们还是建议你在制作包的时候，严格遵守 CommonJS 规范。

我们也可以把文件夹封装为一个模块，即所谓的包。包通常是一些模块的集合，在模块的基础上提供了更高层的抽象，相当于提供了一些固定接口的函数库。通过定制 package.json，我们可以创建更复杂，更完善，更符合规范的包用于发布。

Node.js 在调用某个包时，会首先检查包中 packgage.json 文件的 main 字段，将其作为包的接口模块，如果 package.json 或 main 字段不存在，会尝试寻找 index.js 或 index.node 作为包的接口。

package.json 是 CommonJS 规定的用来描述包的文件，完全符合规范的 package.json 文件应该含有以下字段：

name: 包的名字，必须是唯一的，由小写英文字母、数字和下划线组成，不能包含空格。

description: 包的简要说明。

version: 符合语义化版本识别规范的版本字符串。

keywords: 关键字数组，通常用于搜索。

maintainers: 维护者数组，每个元素要包含 name 、email\(可选\)、web\(可选\)字段。

contributors: 贡献者数组，格式与 maintainers 相同。包的作者应该是贡献者数组的第一个元素。

bugs: 提交 bug 的地址，可以是网址或者电子邮件地址。

licenses: 许可证数组，每个元素要包含

type（许可证的名称）和 url（链接到许可证文本的地址）字段。

repositories: 仓库托管地址数组，每个元素要包含 type（仓库的类型，如 git）、URL（仓库的地址）和 path（相对于仓库的路径，可选）字段。

dependencies: 包的依赖，一个关联数组，由包名称和版本号组成。

## 包的发布

通过使用 npm init 可以根据交互式回答产生一个符合标准的 package.json。创建一个 index.js 作为包的接口,一个简单的包就制作完成了。 在发布前,我们还需要获得一个账号用于今后维护自己的包,使用 npm adduser 根据提示完成账号的创建。

完成后可以使用 npm whoami 检测是否已经取得了账号。

接下来，在 package.json 所在目录下运行 npm publish，稍等片刻就可以完成发布了，打开浏览器，访问 [search.npmjs.org/](http://search.npmjs.org/) 就可以找到自己刚刚发布的包了。现在我们可以在世界的任意一台计算机上使用 npm install neveryumodule 命令来安装它。

如果你的包将来有更新,只需要在 package.json 文件中修改 version 字段，然后重新使用 npm publish 命令就行了。 如果你对已发布的包不满意，可以使用 npm unpublish 命令来取消发布。

<!---->
