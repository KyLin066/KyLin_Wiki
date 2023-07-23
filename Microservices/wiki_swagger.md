# Swagger使用教程

## `引用`

---

[Swagger官网地址](https://swagger.io/)

[SpringDoc官方文档](https://springdoc.org/v2/)

<br>

## `摘要`

---

```
Swagger是一款RESTFUL接口的文档在线生成软件和RESTFUL接口的功能测试软件
```

### **Swagger周边生态**

1. Swagger UI

    进入官网之后，点击UI，选择Live Demo，即查看Swagger UI的效果

    ![picture 1](../images/f5acc2e469672af74aaae430af31d45b823c44e920d9e9f8dbe41c46faf9f924.png)  

    ![picture 2](../images/fd3ab3e3715f013e85cde6f1aa341990daa202c1a7e2b2f9ef0cb554381b1f9c.png)  

2. Swagger Editor

    进入官网之后，点击Editor，选择Try Swagger Editor，即查看Swagger Editor的在线编辑器

    ![picture 3](../images/9b9dbed86b35c442ba9a7f7ac8b0553f04ea53af3e05345b7d8749b2ff5d6404.png)  

    进行编辑之后即可导出相应语言的客户端或服务端的代码

    ![picture 4](../images/a8d6d13233b44fc387344544e1290cdb3df6ebd8de627a9425d5be9be6e41603.png)  

3. Swagger Codegen
   
   TODO:

<br>

## `部署`

---

参考文章：[SpringBoot3中Swagger的引入](https://blog.csdn.net/qq_40109267/article/details/129671447)

1. 在pom.xml中引入依赖

    ```
    <!-- SpringDoc相关依赖 -->
	<dependency>
        <groupId>org.springdoc</groupId>
        <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
        <version>2.1.0</version>
	</dependency>
    ```

2. 在application.properties设置Swagger文档的路径

	```
	# 设置swagger-ui的默认路径
	springdoc.swagger-ui.path=/swagger-ui.html
	```

3. 浏览器输入地址：`http://localhost:8080/swagger-ui/index.html`

	![picture 5](../images/96e376970d9c81d3b5a0885f02aad2af7cc473373f009c9bd1b98539a70ee221.png)  

<br>

## `使用`

---

1. 选择需要测试的功能，点击`Try it out`按钮

    ![picture 6](../images/1dd7d0f1c34979db841fdd744c091e9e7908ad27694b942059f7b380ceef5136.png)  

2. 输入相应的字段，点击`Execute`按钮

    ![picture 7](../images/8349938fc8403f67982e3914cfe370c10731e228122260c2b1ab6a63ca8341c1.png)  

3. 在Server response中可以查看操作是否成功

    ![picture 8](../images/ea7c2bd25edb2af1204983431521c9a35fff9b23df4bdcdaae7baacc08c95eba.png)  
