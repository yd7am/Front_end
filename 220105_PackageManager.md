## JavaScript包管理工具

NPM 全称 Node Package Manager，它是 JavaScript 的包管理工具, 并且是 Node.js 平台的默认包管理工具。通过NPM 可以安装、共享、分发代码,管理项目依赖关系。

https://www.cnblogs.com/whaleup/p/11517916.html

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
  "main": "index.js",  //程序的主入口文件 index.js
  "scripts": {  //脚本命令组成的对象
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"  //许可证 默认即可
}
```

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

#### 生产环境模块

```
//--save或 -S 参数意思是把模块的版本信息保存 package.json 文件的 dependencies 字段中（生产环境依赖)
npm install <Module Name> [--save|-S]
```

#### 开发环境模块

```
//--save-dev 或 -D 参数是把模块版本信息保存到 package.json 文件的 devDep ncies 字段中（开发环境依赖),所以开发阶段一般使用它:
npm install <Module Name> [--save-dev|-D]
```

举例：安装**eslint**模块，它是语法格式校验，只在开发环境依赖中即可

```
npm install eslint -D
```

在 **package.json** 文件的 **devDependencies** 段中:

```
  "devDependencies": {
    "eslint": "^8.6.0"
  }
```

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

