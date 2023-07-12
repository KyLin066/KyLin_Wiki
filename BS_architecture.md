# B/S架构及其运行原理

> [参考连接](https://blog.csdn.net/qq_40587575/article/details/79673478)

## 一、B/S的概念

> &ensp;&ensp;&ensp;&ensp;B/S（Brower/Server,浏览器/服务器）模式又称B/S结构，是Web兴起后的一种网络结构模式。Web浏览器是客户端最主要的应用软件。
>
> &ensp;&ensp;&ensp;&ensp;这种模式统一了客户端，将系统功能实现的核心部分集中到服务器上，简化了系统的开发、维护和使用；
>
> &ensp;&ensp;&ensp;&ensp;客户机上只需要安装一个浏览器，服务器上安装SQL Server, Oracle, MySql等数据库；浏览器通过Web Server同数据库进行数据交互。

Browser指的是Web浏览器，极少数事务逻辑在前端实现，但主要事务逻辑在服务器端实现。

B/S架构的系统无须特别安装，只有Web浏览器即可。

其实就是我们前端现在做的一些事情，大部分的逻辑交给后台来实现，我们前端大部分是做一些数据渲染，请求等比较少的逻辑。

**B/S架构的分层：**

与C/S架构只有两层不同的是，**B/S架构有三层**，分别为：

**第一层表现层**：主要完成用户和后台的交互及最终查询结果的输出功能。

**第二层逻辑层**：主要是利用服务器完成客户端的应用逻辑功能。

**第三层数据层**：主要是接受客户端请求后独立进行各种运算。

如图所示：  

![](https://img-blog.csdnimg.cn/20200118143816483.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NlYV9zbm93,size_16,color_FFFFFF,t_70)

**B/S架构的优点：**

> 1、客户端无需安装，有Web浏览器即可。 
> 
> 2、BS架构可以直接放在广域网上，通过一定的权限控制实现多客户访问的目的，交互性较强。 
> 
> 3、BS架构无需升级多个客户端，升级服务器即可。可以随时更新版本，而无需用户重新下载。

**B/S架构的缺点：**

> 1、在跨浏览器上，BS架构不尽如人意。
>  
> 2、表现要达到CS程序的程度需要花费不少精力。 
> 
> 3、在速度和安全性上需要花费巨大的设计成本，这是BS架构的最大问题。 
> 
> 4、客户端服务器端的交互是请求-响应模式，通常需要刷新页面，这并不是客户乐意看到的。（在Ajax风行后此问题得到了一定程度的缓解）

## 二. B/S工作原理
**B/S架构采取浏览器请求，服务器响应的工作模式。**

> &ensp;&ensp;&ensp;&ensp;用户可以通过浏览器去访问Internet上由Web服务器产生的文本、数据、图片、动画、视频点播和声音等信息；
> 
> &ensp;&ensp;&ensp;&ensp;而每一个Web服务器又可以通过各种方式与数据库服务器连接，大量的数据实际存放在数据库服务器中；
>
> &ensp;&ensp;&ensp;&ensp;从Web服务器上下载程序到本地来执行，在下载过程中若遇到与数据库有关的指令，由Web服务器交给数据库服务器来解释执行，并返回给Web服务器，Web服务器又返回给用户。在这种结构中，将许许多多的网连接到一块，形成一个巨大的网，即全球网。而各个企业可以在此结构的基础上建立自己的Internet。

**一张图看懂B/S架构工作原理：**  
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNjA2MjUwMDctMTQ3NzY3NzM3NC5wbmc?x-oss-process=image/format,png)

![](https://img-blog.csdnimg.cn/20181126145205809.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L251b3l1ZXp1bw==,size_16,color_FFFFFF,t_70)

> 工作流程：
>
> 1. 客户端发送请求： 用户在客户端【浏览器页面】提交表单操作，向服务器发送请求，等待服务器响应；
>
> 2. 服务器端处理请求： 服务器端接收并处理请求，应用服务器端通常使用服务器端技术，如JSP等，对请求进行数据处理，并产生响应；
>
> 3. 服务器端发送响应： 服务器端把用户请求的数据（网页文件、图片、声音等等）返回给浏览器。
>
> 4. 浏览器解释执行HTML文件，呈现用户界面。

- **浏览器：**
> &ensp;&ensp;&ensp;&ensp;是阅读和浏览Web的工具，它是通过B/S方式与Web服务器交互信息的。
>
> &ensp;&ensp;&ensp;&ensp;一般情况下，浏览器就是客户端，它要求服务器把指定信息传送过来，然后通过浏览器把信息显示在屏幕上。
>
> &ensp;&ensp;&ensp;&ensp;浏览器实际上是一种允许用户浏览Web信息的软件，只不过这些信息是由Web服务器发送出来的。

- **服务器：**
> &ensp;&ensp;&ensp;&ensp;服务器（Server），它既是计算机硬件的称谓，有时又是计算机服务端软件的称谓，用户应该区分开它们，主要就是从语境上去区分。
>
> &ensp;&ensp;&ensp;&ensp;（1）、服务器是一种计算机硬件：服务器应该算是一种高性能的计算机，它作为网络的节点，存储、处理网络上的数据、信息，因此也被称为网络的灵魂。 
>
> &ensp;&ensp;&ensp;&ensp;（2）、服务器是一种计算机软件：一般IIS服务器、Java服务器、.NET服务器等名词，一般都是指一种计算机软件。当用户使用计算机上网时，其实是访问服务器硬件。但 是，这个服务器硬件上安装了服务器软件，例如IIS服务器、Java服务器、.NET服务器，它们负责接收用户的访问请求，并根据请求经过计算将数据返回给用户的客户端（浏览器）。
>
> &ensp;&ensp;&ensp;&ensp;服务器软件分为两类：一类是Web服务器；另一类是应用程序服务器（简称为App Server）。IIS服务器和Apache是最常用的Web服务器软件；Java服务器、.NET服务器、PHP服务器是最常用的应用程序服务器软件。
>
> &ensp;&ensp;&ensp;&ensp;（3）、Web服务器：Web服务器实际上是一种连接在Internet上的计算机软件。它负责Web浏览器提交的文本请求。

- **Web应用程序：**
> &ensp;&ensp;&ensp;&ensp;最简单的Web应用程序其实就是一些HTML文件和其它的一些资源文件组成的集合。
>
> &ensp;&ensp;&ensp;&ensp;Web站点则可以包含多个Web应用程序。它们位于Internet上的一个服务器中，一个Web站点其实就对应着一个网络服务器（Web服务器）.

## 三、B/S的优点：
> 1. B/S最大的优点就是可以在任何地方进行操作而不用安装任何专门的软件，只要有一台能上网的电脑就能使用，客户端零安装、零维护。系统的扩展非常容易。
> 2. 由需求推动了AJAX技术的发展，它的程序也能在客户端电脑上进行部分处理，从而大大的减轻了服务器的负担；并增加了交互性，能进行局部实时刷新。
> 3. B/S结构主要利用了不断成熟的Web浏览器技术：结合浏览器的多种脚本语言和ActiveX技术，用通用浏览器实现原来需要复杂专用软件才能实现的强大功能，节约了开发成本。

## 四、B/S体系结构的特点：
> 1. 由于Web支持底层的TCP/IP协议，使Web网与局域网都可以做到连接，从而彻底解决了异构系统的连接问题。
> 2. 由于Web采用了“瘦客户端”，使系统的开放性得到很大的改善，系统对将要访问系统的用户数的限制有所放松。
> 3. 系统的相对集中性使得系统的维护和扩展变得更加容易。比如数据库存储空间不够，可再加一个数据库服务器；系统要增加功能，可以新增—个应用服务器来运行新功能。
>4. 界面统一（全部为浏览器方式），操作相对简单。
>5. 业务规则和数据捕获的程序容易分发。

## 五、与传统C/S的联系与区别：
- C/S（Client/Server）,即客户端/服务端

我们把响应服务的计算机称为服务器，接受请求服务的计算机成为客户机【也叫工作站（workstations）】。

C/S架构软件（即客户机/服务器模式）分为客户机和服务器两层：第一层是在客户机系统上结合了表示与业务逻辑，第二层是通过网络结合了数据库服务器。

简单的说就是第一层是用户表示层，第二层是数据库层。需要程序员自己写客户端。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNjU1MTMxMDEtMTA2NTM3ODkzNi5qcGc?x-oss-process=image/format,png)
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNjU1NDI2OTUtNjY4NTY4MDk5LnBuZw?x-oss-process=image/format,png)

- B/S（Brower/Server）,即浏览器/服务器

B/S 与C/S 的两层架构不同，它采取三层架构。只要有浏览器就可以打开，具体工作原理如下。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNjU5Mjk0NDUtMTEwNTI0MjEwNy5qcGc?x-oss-process=image/format,png)
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNzExMzI0MjktMTY1NzI0NjQ5My5wbmc?x-oss-process=image/format,png)

**一张图看懂C/S与B/S的区别：**

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNzA0MjY4NTEtODY5OTk4NTkzLnBuZw?x-oss-process=image/format,png)

补充：

1. HTTP处理流程是怎么样的？

&ensp;&ensp;&ensp;&ensp;建立连接-->客户端浏览器发送请求信息--->web服务器解析请求并找到相应的资源将文件以及其它信息组成HTTP响应返回客户端-->关闭连接。

2. 集中式服务器：

&ensp;&ensp;&ensp;&ensp;服务器，是担负服务任务的机器。这些服务任务由一般专门的软件来完成。

一般地，把具有某种服务功能的服务器软件及其所在的机器，都统称为XX服务器（XX表示某种具体服务）。

&ensp;&ensp;&ensp;&ensp;这些软件可以集中于一台机器中（如图5），这样的机器可以称为集中式服务器；也可以单独存在于某台机器中，这样的机器可以称为独立式服务器，多个独立式服务器可组成服务器群或矩阵。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNzE0MTE0MjktMTE2MTYzODIxMS5wbmc?x-oss-process=image/format,png)

由交换机可以将多个服务器连接起来称为一个服务器群，以下是常见的服务器软件：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvNjY3MjM4LzIwMTcxMi82NjcyMzgtMjAxNzEyMjkxNzE1MDU0OTItODEzNjUzMDg4LnBuZw?x-oss-process=image/format,png)

## 六、B/S架构的几种形式

<br>

**第一种：客户端-服务器-数据库**

![](https://img-blog.csdnimg.cn/20200118152126513.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NlYV9zbm93,size_16,color_FFFFFF,t_70)

这个应该是我们平时比较常用的一种模式：

1、客户端向服务器发起Http请求

2、服务器中的web服务层能够处理Http请求

3、服务器中的应用层部分调用业务逻辑，调用业务逻辑上的方法

4、如果有必要，服务器会和数据库进行数据交换. 然后将模版＋数据渲染成最终的Html, 返送给客户端

<br>

**第二种：客户端－web服务器－应用服务器－数据库**

![](https://img-blog.csdnimg.cn/20200118151926798.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NlYV9zbm93,size_16,color_FFFFFF,t_70)

类似于第一种方法，只是将web服务和应用服务解耦

> 1 客户端向web服务器发起Http请求
>
> 2 web服务能够处理Http请求，并且调用应用服务器暴露在外的RESTFUL接口
>
> 3 应用服务器的RESTFUL接口被调用，会执行对应的暴露方法.如果有必要和数据库进行数据交互，应用服务器会和数据库进行交互后，将json数据返回给web服务器
> 
> 4 web服务器将模版＋数据组合渲染成html返回给客户端

<br>

**第三种方法：客户端－负载均衡器(Nginx)－中间服务器(Node)－应用服务器－数据库**

这种模式一般用在有大量的用户，高并发的应用中。

![](https://img-blog.csdnimg.cn/20200118152234550.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NlYV9zbm93,size_16,color_FFFFFF,t_70)

> 1、整正暴露在外的不是真正web服务器的地址，而是负载均衡器器的地址
>
> 2、客户向负载均衡器发起Http请求
>
> 3、负载均衡器能够将客户端的Http请求均匀的转发给Node服务器集群
>
> 4、Node服务器接收到Http请求之后，能够对其进行解析，并且能够调用应用服务器暴露在外的RESTFUL接口
>
> 5、应用服务器的RESTFUL接口被调用，会执行对应的暴露方法.如果有必要和数据库进行数据交互，应用服务器会和数据库进行交互后，将json数据返回给Node
>
>6、Node层将模版＋数据组合渲染成html返回反向代理服务器
>
>7、反向代理服务器将对应html返回给客户端

**Nginx的优点有:**

> 1、它能够承受、高并发的大量的请求，然后将这些请求均匀的转发给内部的服务器，分摊压力.
>
> 2、反向代理能够解决跨域引起的问题，因为Nginx，Node,应用服务器，数据库都处于内网段中。
> 
> 3、Nginx非常擅长处理静态资源(img,css,js,video)，所以也经常作为静态资源服务器，也就是我们平时所说的CDN

**比如：前一个用户访问index.html, 经过Nginx－Node－应用服务器－数据库链路之后，Nginx会把index.html返回给用户，并且会把index.html缓存在Nginx上，下一个用户再想请求index.html的时候，请求Nginx服务器，Nginx发现有index.html的缓存，于是就不用去请求Node层了，会直接将缓存的页面(如果没过期的话)返回给用户。**