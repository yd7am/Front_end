## 计算机网络

[计算机网络基础知识梳理](https://blog.csdn.net/m0_37568814/article/details/81018769?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4.no_search_link&utm_relevant_index=7)

### http超文本传送协议 (Hypertext transfer protocol)

HTTP协议定义Web客户端如何从Web服务器请求Web页面，以及服务器如何把Web页面传送给客户端。HTTP协议采用了请求/响应模型。客户端向服务器发送一个请求报文，请求报文包含请求的方法、URL、协议版本、请求头部和请求数据。服务器以一个状态行作为响应，响应的内容包括协议的版本、成功或者错误代码、服务器信息、响应头部和响应数据。

[链接1](https://www.cnblogs.com/hello-web/p/10394210.html)

[链接2](https://www.cnblogs.com/mark5/p/11219154.html)

#### URL

URL(UniformResourceLocator), 中文叫统一资源定位符,是互联网上用来标识某一处资源的地址。

URL的一般语法格式为：

(带方括号[]的为可选项)：

protocol :// hostname[:port] / path / \[:parameters][?query]#fragment

**hostname（主机名）**

是指存放资源的服务器的[域名系统](https://baike.baidu.com/item/域名系统)(DNS) 主机名或 IP 地址。有时，在主机名前也可以包含连接到服务器所需的用户名和密码（格式：username:password@hostname）

**parameters（参数）**

这是用于指定特殊参数的可选项,有服务器端程序自行解释。

**query(查询)**

可选，用于给[动态网页](https://baike.baidu.com/item/动态网页)（如使用CGI、ISAPI、PHP/JSP/ASP/ASP.NET等技术制作的网页）传递参数，可有多个参数，用“&”符号隔开，每个参数的名和值用“=”符号隔开。

---

**http协议规定了发送请求的格式**，这个格式有三部分组成**请求行、请求头、请求体**。

> 请求行包括请求的方式（get、post或其他）、要求响应的文件、http版本。
>
> 请求头包括本机信息、浏览器信息等等
>
> 请求体包括POST传递数据的相关信息，Get方式传值时，请求体为空。

请求信息发送至服务器以后，服务器会获取传递过来的相关信息进行后端程序的处理。一般通过request.querystring获取URL传递过来的指，通过request.form获取POST传递过来的值，当然，也是可以获取到所有的其他请求过来的信息，如浏览器信息、cookie信息、操作系统信息等。获取相关的数据以后，服务器就会根据程序进行处理。处理完成以后，服务器会做出响应，向浏览器输出相关信息。

**http对响应的格式也做出了规定**，响应的信息主要包括，**状态行、消息报头、响应正文**。

> 状态行由HTTP协议版本号， 状态码， 状态消息 三部分组成。
>
> 响应头(消息报头)记录服务器相关信息如服务器是否启用压缩、服务器为IIS或Ngnix、程序所用服务端语言等等。当然，缓存也是在这里设置的，通过修改响应头可以修改html在本地缓存的情况，如设置浏览器缓存过期的时间。
>
> 响应体(响应正文)主要是我看到的html的相关内容了。

##### 例子

1、浏览器向 DNS 服务器请求解析该 URL 中的域名所对应的 IP 地址;

2、解析出 IP 地址后，根据该 IP 地址和默认端口 80，和服务器建立**TCP连接**

3、浏览器发出读取文件(URL 中域名后面部分对应的文件)的HTTP 请求，该请求报文作为 **TCP 三次握手**的第三个报文的数据发送给服务器;

4、服务器对浏览器请求作出响应，并把对应的 html 文本发送给浏览器;

5、释放 **TCP连接**

6、浏览器将该 html 文本并显示内容;

### 浏览器工作原理

[链接](https://www.jianshu.com/p/3869802fbe21)

#### 渲染引擎

**渲染引擎**在浏览器窗口中显示所请求的内容，浏览器内核分成两部分：渲染引擎和js引擎，由于js引擎越来越独立，内核就倾向于只指渲染引擎，所以渲染引擎也称为浏览器内核。

> 渲染引擎从解析HTML并将标签转译成DOM节点开始，这种节点树通常被叫做 **content tree（内容树) **。 同时，它也会解析外部CSS文件以及style标签中的样式数据。 这些样式信息连同HTML中的” 可见内容” 一道，被用于构建另一棵树——  **渲染树(Render树)** 。DOM树可视节点的CSS Style就是其对应Render树节点的Style。
>
> 在'render tree' （渲染树）建造完成后，将会进行一个叫 'layout' 的过程。这个过程将会给每个node节点详细的坐标。下一步是 'painting' ,'render tree' （渲染树）将会与节点穿插然后使用UI backend层渲染。

##### 渲染引擎解析

解析的结果通常是表达文档结构的节点树，称为解析树或语法树。

#### JavaScript interpreter

### DNS工作原理

**一般情况下：… . 三级域名 . 二级域名 . 顶级域名**

DNS解析：

在浏览器中输入www.baidu.com域名，操作系统会先检查自己本地的**hosts文件**是否有这个网址映射关系，如果有，就先调用这个ip地址映射，完成域名解析。若无，查找**本地DNS解析器缓存**；若无，首先会找TCP/IP参数中设置的首选DNS服务器，在此我们叫它**本地DNS服务器**。

> 此服务器收到查询时，如果要查询的域名，包含在本地配置区域资源中，则返回解析记过给客户端，完成域名解析，此解析具有权威性。若不由本地DNS服务器区域解析，但该服务器已缓存了此网址映射关系，则调用这个IP地址映射，完成域名解析，此解析不具有权威性。

略。。。

一次完整得查询请求经过得流程

　　　　　　client-->hosts文件-->DNS service

　　　　　　local cache -->DNS server（recursion递归）-->server cache -->iteration(迭代)

客户端到本地DNS服务器是属于递归查询，而DNS服务器之间的交互查询就是迭代查询