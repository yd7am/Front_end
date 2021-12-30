## 计算机网络
[计算机网络基础知识梳理](https://blog.csdn.net/m0_37568814/article/details/81018769?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4.no_search_link&utm_relevant_index=7)

### http超文本传送协议 (Hypertext transfer protocol)

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

