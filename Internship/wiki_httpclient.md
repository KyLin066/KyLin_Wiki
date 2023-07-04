# HttpClient学习笔记

## `引用`

---

参考视频：[极速入门httpclient](https://www.bilibili.com/video/BV11541147QF/?spm_id_from=333.337.search-card.all.click&vd_source=d790b157ecc481e5bac9b43baba7a335)

参考文章：[Apache HttpClient 5 使用详细教程](https://blog.csdn.net/hebiwen95/article/details/126405108)

<br>

## `摘要`

---

```
    HttpClient是Apache Jakarta Common下的子项目，可以用来提供高效的、最新的、功能丰富的支持HTTP协议的客户端编程工具包，并且它支持HTTP协议最新的版本和建议。它不仅使客户端发送Http请求变得容易，而且也方便开发人员测试接口（基于Http协议的），提高了开发的效率，也方便提高代码的健壮性。
```

<br>

## `部署`

---

要开始使用HttpClient，需要在的项目中引入httpclient的依赖。例如，在Maven项目中，可以在pom.xml文件中添加以下依赖：

```
<!-- HttpClient相关依赖 -->
<dependency>
	<groupId>org.apache.httpcomponents.client5</groupId>
	<artifactId>httpclient5</artifactId>
	<version>5.2.1</version>
</dependency>
```