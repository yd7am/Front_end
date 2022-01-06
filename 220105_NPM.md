# JavaScript包管理工具

## NPM

NPM 全称 Node Package Manager，它是 JavaScript 的包管理工具, 并且是 Node.js 平台的默认包管理工具。通过NPM 可以安装、共享、分发代码,管理项目依赖关系。

https://www.cnblogs.com/whaleup/p/11517916.html

https://www.cnblogs.com/shcrk/p/10363369.html

### 安装过程

最新版本的 Node.js 已经集成了 npm 工具，所以必须首先在本机安装 Node.js

Node.js 官网下载地址：

- 英文网：https://nodejs.org/en/download/
- 中文网：http://nodejs.cn/download/

选择安装路径：如  E:\nodejs\

Add to PATH 会自动将node.js配置到环境变量

> 环境变量是在操作系统中一个具有特定名字的对象，它包含了一个或者多个应用程序所将使用到的信息。例如Windows和DOS操作系统中的path环境变量，当要求系统运行一个程序或执行命令而没有告诉它程序所在的完整路径时，系统除了在当前目录下面寻找此程序外，还应到path中指定的路径去找。

查看node.js 与 npm 版本：`node -v`  `npm -v`

安装完成后进行NPM命令操作：

1.NPM初始化：通过命令提示符窗口cmd进入新建文件夹，执行命令 `npm init`进行初始化。

`package name: (pm)  命名` 包名不能有大写字母，或直接回车取括号内默认值pm

...

后面会生成一个**package.json**文件，即包的配置文件

```
About to write to g:\Oortcloud\Test\pm\package.json:

{
  "name": "npm-demo",  //包名
  "version": "1.0.0",  //版本号
  "description": "first npm demo",   //描述
  "main": "index.js", "xxx.js", //程序的主入口文件 index.js
  "scripts": {  //脚本命令组成的对象
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"  //许可证 默认即可
}
```

创建一个**index.js**文件作为包入口文件：

当然这是**默认的入口文件**,如果有其他想法的话，完全可以在package.json中进行修改，可以在里面做你想要的操作。

我们需要可以引入这个npm包并调用这个包中的一些方法,因此对这个npm包中的index.js中的内容进行完善。

### 安装模块

npm install 命令用于安装某个模块，安装方式分为 ：**本地安装**（local）、**全局安装**（global）两种.

##### 本地安装

将 JS 库安装在当前执行命令时所在目录下，安装

```
npm install <Module Name>[@版本号]    //版本号可选
```

安装后当前目录下多了**node_modules**文件夹和**package-lock.json**文件

**node_modules**文件夹用于存放下载的js库

**package-lock.json** 是在 npm install 时候生成一份文件。

> 锁定当前项目安装包的版本，避免同一个项目在不同地方安装会出现版本冲突的问题

用以记录当前状态下实际安装的各个包的具体来源和版本号

重新打开**package.json**文件，发现npm install <>下载的模块已经添加到依赖列表中了。

```
  "dependencies": {
    "express": "^4.17.2"
  }
```

>关于模块版本号表示方式：
>
>指定版本号：比如 3.5.2，只安装指定版本。遵循 “大版本.次要版本 小版本”的格式规定。
>
>~波浪号 + 指定版本号：比如 ~3.5.2，安装 3.5.x 的最新版本（不低于 3.5.2），但是不安装 3.6.x，也
>
>就是说安装时不改变大版本号和次要版本号。
>
>^ 插入号 + 指定版本号：比如 ^3.5.2，安装 3.x 新版本（不低于 3.5.2），但是不安装 4.x.x，也
>
>就是说安装时不改变大版本号。需要注意的是，如果 本号为0，则插入号的行为与波浪号相同，这是
>
>因为此时处于开发阶段，即使是次要版本号变动，也可能带来 程序的不兼容。
>
>latest：安装最新版本。

##### 全局安装

```
npm root -g //执行该命令查看全局目录路径
npm install <Module Name>[@版本号] -g

//如果安装时出现如下错误：
npm err! Error: connect ECONNREFUS 27.0.0.1:8087
//解决方法，执行如下命令：
npm config set proxy null
```

`npm root -g`查看全局目录路径：C:\Users\Ydam\AppData\Roaming\npm\node_modules

修改全局目录路径：

1. 在nodejs目录(或其他目录)下新建两个文件夹，node_cache  &  node_global
2. `npm config set prefix "E:\\nodejs\\node_global"`
3. `npm config set cache "E:\\nodejs\\node_cache"`

`npm root -g`查看全局目录路径：E:\nodejs\node_global\node_modules

修改环境变量

1. 在【系统变量】下新建【NODE_PATH】，输入【E:\nodejs\node_global】
2. 将用户变量下的【Path】中的【C:\Users\Ydam\AppData\Roaming\npm】修改为：

【E:\nodejs\node_global】



#### 生产环境模块

```
//--save或 -S 参数意思是把模块的版本信息保存 package.json 文件的 dependencies 字段中（生产环境依赖，用户发布环境，需要把它放到服务器上)
npm install <Module Name> [--save|-S]
```

#### 开发环境模块

```
//--save-dev 或 -D 参数是把模块版本信息保存到 package.json 文件的 devDep ncies 字段中（开发环境依赖，用于本地环境开发时候，并不需要把它放到服务器上),所以开发阶段一般使用它:
npm install <Module Name> [--save-dev|-D]
```

举例：安装**eslint**模块，它是语法格式校验，只在**开发环境依赖**中即可

```
npm install eslint -D
```

在 **package.json** 文件的 **devDependencies** 段中:

```
  "devDependencies": {  //用于本地环境开发时候。
    "eslint": "^8.6.0"
  }
```

**dependencies依赖的包不仅开发环境能使用，生产环境也能使用**

#### 批量下载模块

我们从网上下载某些项目后，发现只有 package.json , 没有 node_modules 文件夹，这时我们需要通过命令下载这些js库。

命令提示符进入 package.json 所在目录，执行命令：

```
npm install
```

此时，npm 会自动下载 package.json 中依赖的js库.

#### 查看模块命令

##### 查看本地已安装模块方式

方式1：可以安装目录 node_modules 下的查看包是否还存在

方式2：可以使用以下命令查看：

```
# 查看本地安装的所有模块
npm list
# 查看指定模块
npm list <Module Name>
```

##### 查看模块远程最新版本

```
npm view <Module Name> version  //查看模块远程最新版本
npm view <Module Name> versions  //查看模块远程所有版本
```

#### 卸载模块

```
npm uninstall <Module Name>  //卸载局部模块
npm uninstall -g <Module Name>  //卸载全局模块
```

#### 配置镜像加速

```
npm get registry  //查看当前使用的镜像地址
npm config set registry https://registry.npm.taobao.org //配置淘宝镜像地址
```

### 发布npm包

#### 登录npm(添加用户)

```
npm adduser
npm notice Log in on https://registry.npmjs.org/
Username: yd7am
Password:
Email: (this IS public) 1057037208@qq.com
Logged in as yd7am on https://registry.npmjs.org/.
```

#### npm publish

```
npm publish
npm notice package: npm-demo-czk@1.0.0
npm notice === Tarball Contents ===
npm notice 376B index.html
npm notice 33B  index.js
npm notice 348B package.json
npm notice 24B  test.js
npm notice === Tarball Details ===
npm notice name:          npm-demo-czk
npm notice version:       1.0.0
npm notice filename:      npm-demo-czk-1.0.0.tgz
npm notice package size:  623 B
npm notice unpacked size: 781 B
npm notice shasum:        40586e90dc277cb84d287c84c434a799eb4ac355
npm notice integrity:     sha512-525r1FNukKMZk[...]h69zGMlGkUgMA==
npm notice total files:   4
npm notice
+ npm-demo-czk@1.0.0
```

### 引用npm包

#### 创建一个案例

执行：`npm init -y` yes，生成默认package.json文件
创建一个index.js的入口文件
这样就创建了一个案例了.

#### 下载依赖包

执行：`npm install --save-dev npm-demo-czk`
(或者：` npm install npm-demo-czk`)

打开**package.json**文件

```
  "devDependencies": {
    "npm-demo-czk": "^1.0.0"
  }
```

#### 调用npm包中的文件

```
var test = require("npm-demo-czk");
test.testDemo();
//执行命令即可运行案例,可以看到控制台成功调用了方法打印出了日志
//因为默认程序的主入口文件为index.js("npm-demo-czk"中的)，只能调用里面的函数
g:\Oortcloud\Test\download_test>node index.js  //此index.js是此案例中的
this is test demo!!!!!!
```

>然而，这是在 node.js 中才起作用的模块加载方法， node.js 作为一个服务器端语言，有权限访问计算机的文件系统，因此工作良好。Node.js 还知道每个 npm 模块的路径，所以我们不需要写上 `require('./node_modules/npm-demo-czk/index.js)`，而可以直接写 `require('npm-demo-czk')` 
>
>如果把上面的代码运行在浏览器中(HTML 文件)的话，你会得到一个报错 `require is not defined`。因为浏览器没有对文件系统的权限。这就意味着用这种方式加载模块很难搞 -- 文件必须被动态地加载，或者同步地加载（减慢执行速度）或者异步地加载（不能保证时间顺序）。

## 使用 JavaScript 模块打包工具（webpack）

**https://blog.csdn.net/qq_36838191/article/details/80796349**

JavaScript 模块打包器是一个能在代码构建过程（有文件系统权限）绕过上述问题并打包生产出兼容于浏览器的生产版本（不再需要有文件系统权限）的工具。

在上面例子中，我们需要一个模块打包器，找到所有 `require()` 语句（它在浏览器端的 JavaScript 中是非法的）并把它们替换成想 require 的文件实际的内容。最终结果是一个打包后的 JavaScript 文件（没有 require 语句）！2015 年左右，[webpack](https://link.zhihu.com/?target=https%3A//webpack.github.io/)最终成为更为广泛使用的包管理器（[React](https://link.zhihu.com/?target=https%3A//reactjs.org/) 的流行大大推动了这一进程，它充分利用了 webpack 的各种特性）。

#### 安装webpack

```
$ npm install webpack --save-dev
//--save-dev参数，把它作为开发环境的依赖，而不是生产环境，因为并不需要把它放到服务器上
```

```
$ .\node_modules\.bin\webpack ./index.js -o ./dist
//这行命令将会运行位于 node_modules 中的 webpack 工具，它将从 index.js 开始，找到所有require 语句，把它们替换成合适的代码并输出一个单文件叫 bundle.js 。这意味着我们在浏览器中不再需要 index.js，因为它包含非法的 require 语句。而是使用输出的 bundle.js文件
```

```
//出现警告
WARNING in configuration
The 'mode' option has not been set, webpack will fallback to 'production' for this value.
```

解决方法：

https://blog.csdn.net/qq_42506411/article/details/114875492

#### 全局安装webpack

https://blog.csdn.net/weixin_51370367/article/details/115164263

```
C:\Windows\System32>webpack -v
webpack: 5.65.0
webpack-cli: 4.9.1
webpack-dev-server not installed
```

---

注意到每当我们修改 `index.js` 后都要运行 webpack 一长串的命令。而且当我们使用到 webpack 更高级的特性时就更烦了（例如使用 [generating source maps](https://link.zhihu.com/?target=https%3A//webpack.js.org/guides/development/%23using-source-maps) 帮我们从编译后的代码调试原始的代码）。Webpack 可以从项目文件的根目录中的一个叫做 `webpack.config.js`的配置文件中读取相应设置，在我们的栗子中，差不多应该配置成这样：

```javascript
const path = require('path')

// 通过Node模块操作，向外面暴露一个配置对象
module.exports={
	entry:path.join(__dirname, './index.js'),  // 打包文件
	output:{
		path:path.join(__dirname, './dist'),  // 打包好的文件存放地址
		filename: 'bundle.js'  // 打包好文件的文件名
	},
	mode: 'development'  // 设置mode（开发/生产）
}
```

这样每次我们改变 `index.js` 后，就可以在命令行中运行：

```text
$ ./node_modules/.bin/webpack 
```

全局安装webpack和webpack-cli后(项目文件的根目录中有 `webpack.config.js`的配置文件)：

```
$ webpack   //直接执行
```



