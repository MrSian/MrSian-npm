## 生成package.json

我们通常会`npm init`命令，然后开始添加npm需要的信息。

但是，如果我们并不真正关心所有这些信息并且我们想要保留默认值，那么我们按下Enter键来快速过完npm询问我们的每一条信息。

为避免这种情况，您只需输入即可`npm init \-y` 。这样就不会出现询问各种问题而直接为您创建有默认值的。package.json

## 安装模块

`npm install`的简写是 `npm i`

## 一次安装多个模块

您可以不用一次一次地执行命令：

```
npm i gulp-pug
npm i gulp-debug
npm i gulp-sass
复制代码
```

可以在同一个命令中安装这些模块：

```
npm i gulp-pug gulp-debug gulp-sass
复制代码
```

甚至，如果这些模块的前缀是一样的，您都不用输入每个模块的全称：

```
npm i gulp{-debug,-sass,-pug}
复制代码
```

## 使用一些安装模式的快捷方式

在您想要安装一个模块并将其作为生产依赖的时候，你通常执行：

```
npm i gulp --save-prod
复制代码
```

其实，你可以这样简写：

```
npm i gulp -P
复制代码
```

对于开发依赖也是一样的道理，您可以用下面的命令来代替`npm i gulp \--save-dev`：

```
npm i gulp -D
复制代码
```

默认情况下，当您运行时npm install没有任何标志时，npm会将包作为依赖项添加到package.json文件中。如果要防止这种情况，请使用no-save标志安装它，如下所示：

```
npm i vue --no-save
复制代码
```

## 获取包的信息

如果您要查看 vue 这个包的信息，会执行`npm view vue`，其实您可以执行它的简写：`npm v vue`

![](https://user-gold-cdn.xitu.io/2018/12/20/167c9b18864833f4?imageView2/0/w/1280/h/960/ignore-error/1)

如果您只想获得最新版本的软件包，可以试试:

```
> npm v vue version 
> 2.5.17
复制代码
```

如果您想获得npm包的完整版本列表，请尝试复数形式:

```
> npm v vue versions 
> ['0.0.0'，
  '0.6.0'，
  '0.7.0'，
  ... 
  '2.5.15'，
  '2.5.16'，
  '2.5.17-beta.0'，
  '2.5.17']
复制代码
```

## 安装特定的软件包版本

如果要安装某个版本不是最新版本的软件包，可以键入:

```
npm i vue@2.5.15
复制代码
```

鉴于记忆名称比数字更容易（至少对我而言），您可以使用运行如上所示的`npm v`命令后列出的`dist-tag`，如下所示：

```
npm i vue @ beta
复制代码
```

### 搜索包裹

有时你不能简单地记住你前一段时间或你朋友推荐的那个包的确切名称。在这种情况下，您可以使用npm搜索直接从终端执行搜索：

```
npm search gulp debug
复制代码
```

或者：

```
npm s gulp debug
复制代码
```

这将打印包含描述，作者和一些其他信息的包列表:

![](https://user-gold-cdn.xitu.io/2018/12/20/167c9b1273afa8f5?imageView2/0/w/1280/h/960/ignore-error/1)

## 卸载包

> ⚠️**这一点貌似只有在npm5+的版本中才有效**（即如下文所说），在npm3版本中测试，`npm i axios`命令并不会把axios登记在package.json中，同样的，`npm uninstall axios`也并不会把axios从package.json中删除。

卸载vue包：

```
npm uninstall vue
复制代码
```

这将从node\_modules文件夹中删除vue包，并在package.json把这个包的记录删除掉，您可以使用rm , un 或者 r 来达到同样的目的：

```
npm rm vue
复制代码
```

如果由于某种原因您只想从node\_modules文件夹中删除包文件但将其作为依赖项保存在package.json文件中，则可以使用no-save标志:

```
npm rm vue --no-save
复制代码
```

## 列出所有依赖

```
npm ls
复制代码
```

这将列出package.json文件中列出的所有依赖项以及它们的所有依赖项。 如果您只想列出您的依赖项，您可以这样做:

```
npm ls --depth=0
复制代码
```

当然，如果要查看所有全局安装的包的列表，可以使用g标志:

```
npm ls -g -depth 0
复制代码
```

## 运行测试

您可以执行`npm run test`来运行测试，但其实您可以简写成`npm test`，甚至更进一步简写成：`npm t`

## 查看可用的scripts

有时，我们希望查看package.json文件中包含的scripts。我们当然可以打开package.json文件，但我们也可以这样做：

```
npm run
复制代码
```

## 从Github仓库安装包

你可以直接从像这样的Github仓库安装一个包:

```
npm i https://github.com/sindresorhus/gulp-debug
复制代码
```

或者您可以省略完整的域部分：

```
npm i sindresorhus/gulp-debug
复制代码
```

## 打开包的Github页面

您当然可以进行Google搜索，然后查找该页面，或者您可以执行以下操作：

```
npm repo create-react-app
复制代码
```

无需安装软件包即可执行上述命令。

## 列出所有可用的NPM环境变量

您可以通过运行来查看可供我们使用的NPM变量的完整列表：

```
npm run env | grep npm_
复制代码
```

关于这些变量的好处是它们可以在你的脚本中使用，你甚至可以创建自己的，让我们看看要怎么添加自己的NPM变量

### 添加自己的NPM变量

您可以通过向package.json文件添加新密钥来添加自己的NPM变量。 它可以是任何键，但我更喜欢将所有NPM变量保留在配置键中，以保持组织有序。像这样：

```
"config": {
  "build_folder":"./dist"
}
复制代码
```

现在，如果您使用前面讨论的命令列出您的变量npm run env | grep npm\_，你会看到你的新变量在那里。

默认情况下，npm会将您的变量命名为npm\_package，并将其结构保存在package.json文件中，即config\_build\_folder。

### 在NPM脚本中使用NPM变量

一旦看到完整的变量列表，并且想要在脚本中使用任何这些变量的值，就可以在package.json中执行此操作（请参阅上一节中变量npm\_package\_config\_build\_folder的值）

```
"scripts": {
  "build": "gulp build --dist $npm_package_config_build_folder"
}
复制代码
```

一旦你用npm run build运行这个命令，它将被执行为:

```
gulp build --dist ./dist
复制代码
```

<!---->