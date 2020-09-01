# node包管理器

> npm是[Node.js](http://nodejs.org/)的软件包管理器 。它创建于2009年，是一个 [开源项目， ](https://github.com/npm/npm)旨在帮助JavaScript开发人员轻松共享打包的代码模块。

既然是经常用的，那也整理整理👾（只列出常用的命令）。



## npm

> 官方指路：[https://docs.npmjs.com/about-semantic-versioning](https://docs.npmjs.com/about-semantic-versioning)

按官方来讲，版本号应该是：**主版本号.次版本号.修订号**

| 代码状态             | 阶段     | 规则                                 | 示例版本 |
| -------------------- | -------- | ------------------------------------ | -------- |
| 初版                 | 新产品   | 从1.0.0开始                          | 1.0.0    |
| 向后兼容的错误修复   | 补丁发布 | 递增第三位数                         | 1.0.1    |
| 向后兼容的新功能     | 轻微释放 | 递增中间数字并将最后一位重置为零     | 1.1.0    |
| 更改会破坏向后兼容性 | 主要发行 | 递增第一位并将中间和最后一位重置为零 | 2.0.0    |



### 常见的版本格式

> 官方指路：[https://semver.npmjs.com/](https://semver.npmjs.com/)



**"1.2.3"**

表示精确版本号。只匹配`1.2.3`的版本



**"^1.2.3"**

> 在相同的主要范围内包含比特定版本更大的所有内容

**主版本号** 不等于 **0**时，匹配 **当前版本号** 到该 **主版本号** 的最大的版本

<strong>*主版本号*</strong> 等于 **0**，**次版本号** 不等于 **0** 时，匹配 **当前版本号** 到该 **次版本号** 的最大的版本

<strong>*主版本号*</strong> 等于**0**，*<strong>次版本号</strong>* 等于 **0**，**修订号** 不等于 **0** 时，匹配 **当前版本号** 到该 **修订号** 的最大的版本

```bash
"^1.2.3" 匹配 ">= 1.2.3 < 2.0.0"

"^0.2.3" 匹配 ">= 0.2.3 < 0.3.0"

"^0.0.3" 匹配 ">= 0.0.3 < 0.0.4"
```



**"~1.2.3"**

> 在同一较小范围内包含大于特定版本的所有内容

有 **修订号** 时，匹配 **当前版本号** 到该 **修订号** 最大版本

没有 <strong>*修订号*</strong>，有 **次版本号** 时，匹配 **当前版本号** 到该 **次版本号** 最大版本

没有 <strong>*修订号*</strong>，没有 <strong>*次版本号*</strong>，有 **主版本号** 时，匹配 **当前版本号** 到该 **主版本号** 最大版本

```bash
"~1.2.3" 匹配 ">= 1.2.3 < 1.3.0"

"~1.2" 匹配 ">= 1.2.0 < 1.3.0"

"~1" 匹配 ">= 1.0.0 < 2.0.0
```



### dependencies - 生产依赖

众所周知，生产环境需要的东西，你都需要装在这个选项里供生产环境使用。例如：`vue`、`vue-router`、`vuex`

> 官方指路：[https://docs.npmjs.com/cli/install](https://docs.npmjs.com/cli/install)

**安装**

> `-P, --save-prod`：包裹将出现在您的中`dependencies`。这是默认设置，除非`-D`或`-O`存在。

```bash
npm install/i <package_name> // 既然是默认，那就没必要加参数了
// 等价于
npm i <package_name>
```

**卸载**

> `-D, --save-dev`：包裹将出现在您的中`devDependencies`。

```bash
npm uninstall <package_name>
// 等价于
npm uni <package_name>
```



### devDependencies - 开发依赖

> 官方指路：[https://docs.npmjs.com/cli/install](https://docs.npmjs.com/cli/install)

众所周知，只是开发环境需要的东西，你都应该装在这个选项里只供开发环境使用。例如：`eslint`、`sass`

**安装**

```bash
npm install <package_name> --save-dev
// 等价于
npm install <package_name> -D
```

**卸载**

```bash
npm uninstall <package_name> --save-dev
// 等价于
npm uni <package_name> -D
```

也许`npm`走的国外服务器，时不时会抽抽风下不动。那可以参数一下淘宝的`cnpm`...👇



## cnpm

> 官方指路：[淘宝 NPM 镜像](https://developer.aliyun.com/mirror/NPM)
>
> 这是一个完整 `npmjs.org` 镜像，你可以用此代替官方版本(只读)，同步频率目前为 **10分钟** 一次以保证尽量与官方服务同步。

### 安装/换源

```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

用法同上，但`cnpm install <package_name>`的时候，默认不会添加进`dependencies - 生产依赖`。需要使用`cnpm install <package_name> -S`

为什么是`-S`不是`-P`？我也不知道🙄。



也许你时常能听到，用`cnpm`的时候在某些情况下会出 bug（作者还没遇到过）。既然有可能，那就试试`yarn`...👇



## yarn

> Yarn是您的代码的包管理器。它使您可以使用代码并与世界各地的其他开发人员共享代码。Yarn快速，安全且可靠地执行此操作，因此您不必担心。

在你使用的时候，你看着安装/卸载的进度条，你会感受到什么叫**纵享丝滑**。

用法官网已经写得很清楚了，直接复制粘贴。



### 安装

> 官方指路：[https://yarnpkg.com/getting-started/install](https://yarnpkg.com/getting-started/install)

全局安装来一手

```js
npm install -g yarn
```



### 访问命令列表

```bash
yarn help
```



### 开始一个新项目

```bash
yarn init
```



### 安装所有依赖项

```bash
yarn
yarn install
```



### 添加依赖项

```bash
yarn add [package]
yarn add [package]@[version]
yarn add [package]@[tag]
```



### 将依赖项添加到不同类别的依赖项中

```bash
yarn add [package]  # dependencies
yarn add [package] -D # devDependencies
```



### 升级依赖

```bash
yarn up [package]
yarn up [package]@[version]
yarn up [package]@[tag]
```



### 删除依赖

```bash
yarn remove [package]
```



### 升级yarn

```bash
yarn set version latest
yarn set version from sources
```



## 总结

`npm`抽风的时候，可以使用`yarn`。当然最好是一直都用`yarn`



### npm常用命令

```bash
npm i  # 安装所有依赖项
npm i <package_name>  # 安装包 默认安装到 生产环境 dependencies中
npm uni <package_name>  # 卸载包
npm i <package_name> -D # 安装包到 开发环境 devDependencies中
```



### yarn常用命令

```bash
yarn  # 安装所有依赖项
yarn add <package_name>  # 安装包 默认安装到 生产环境 dependencies中
yarn remove <package_name>  # 卸载包
yarn add <package_name> -D # 安装包到 开发环境 devDependencies中
```

