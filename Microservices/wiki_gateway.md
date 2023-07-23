# 网关学习笔记

微服务工程案例：<https://github.com/KyLin066/Microservices_Start>

Nginx工程案例：<https://github.com/KyLin066/Nginx_Microservices>

<br>

## `引用`

推荐视频：[2021最新版Eureka注册中心教程](https://www.bilibili.com/video/BV1qi4y1A7pj/?p=12&spm_id_from=333.880.my_history.page.click&vd_source=d790b157ecc481e5bac9b43baba7a335)

<br>

## `摘要`

```
通过搭建Eureka网关服务，实现SpringCloud的微服务之间的调用
```

<br>

## `部署`

1. 新建一个SpringBoot微服务作为网关

    ![picture 0](../images/837ab7d42e061b4243745bab6faa6a2cba17c9423c7d5550b9feedb1da6e1fe0.png)  

2. 在父文件的pom文件配置Eureka网关服务的相关依赖：

    ```
    <properties>
		<spring-cloud.version>2022.0.3</spring-cloud.version>
	</properties>

	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-dependencies</artifactId>
				<version>${spring-cloud.version}</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
    ```

3. 在微服务Eureka注册中心添加相关依赖：
   
   ```
   <dependencies>
		<!-- 网关服务Eureka Server相关依赖 -->
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
		</dependency>
	</dependencies>
	```

4. 在application.properties文件中配置Eureka Server

    ```
    # 设置Eureka Server的主机名
    eureka.instance.hostname=localhost

    # 设置Eureka Server的端口号
    server.port=8761

    # 禁用自我保护模式
    eureka.server.enable-self-preservation=false

    # 禁用客户端获取注册信息
    eureka.client.fetch-registry=false

    # 禁用客户端向Eureka Server注册
    eureka.client.register-with-eureka=false

    # 设置Eureka Server的服务URL
    eureka.client.service-url.defaultZone=http://${eureka.instance.hostname}:${server.port}/eureka/
    ```

5. 在Spring Boot应用的主类上添加@EnableEurekaServer注解来启用Eureka Server

6. 运行Spring Boot应用，启动Eureka Server，见到如下界面表示网关服务Eureka配置成功

    ![picture 1](../images/cfc3673b7602f03975801320d2c540855d47773f1ae49b8bb1ee9e314213ddbc.png)  

<br>

## `使用`

1. [查看SpringCloud所支持的SpringBoot版本](https://docs.spring.io/spring-cloud/docs/current/reference/html/)

    ![picture 2](../images/366136aec953634be34424d3992552c4ea0dfe0a086b14eb8ec3cc33c2fab4d6.png)  

2. [查看SpringBoot所支持的JDK和Maven版本](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html#getting-started.system-requirements)

    ![picture 3](../images/ba54bf437c4876d3419436a071a8f4e1bcd3a7af68c2d816e790ff74336fe0fa.png)  

3. 在SwitchHosts修改本地host文件，添加如下配置：

	```
	127.0.0.1       e1.microservices.com
	127.0.0.1       e2.microservices.com
	```

4. 在Nginx的配置文件中配置如下：
   
	```
	server {
        listen       80;
        server_name  e1.microservices.com;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        # 相当于 http://e1.microservices.com/
        location / {
            proxy_pass   http://127.0.0.1:8761;
        }

        # 相当于 http://e1.microservices.com/eureka/
        location ~ ^/eureka/ {
            proxy_pass   http://127.0.0.1:8761;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

    }

    server {
        listen       80;
        server_name  e2.microservices.com;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        # 相当于 http://e2.microservices.com/
        location / {
            proxy_pass   http://127.0.0.1:8762;
        }

        # 相当于 http://e2.microservices.com/eureka/
        location ~ ^/eureka/ {
            proxy_pass   http://127.0.0.1:8762;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

    }
	```

5. 首先配置高可用的注册中心，根据上面部署的步骤再创建一个注册中心，但不同点在application.properties文件中配置如下：

	Eureka_Server的application.properties文件
	```
	# 设置Eureka Server的端口号
	server.port=8761

	# 应用名称
	spring.application.name=eureka-server

	# 设置Eureka Server的主机名
	eureka.instance.hostname=eureka_server

	# 设置Eureka Server的服务URL
	eureka.client.service-url.defaultZone=http://e2.microservices.com/eureka/

	# 增加数据库连接
	spring.datasource.url=jdbc:mysql://127.0.0.1:3306/database_start?useUnicode=true&characterEncoding=utf-8&zeroDateTimeBehavior=convertToNull
	spring.datasource.username=root
	spring.datasource.password=root
	spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
	```

	Eureka01的application.properties文件
	```
	# 设置Eureka Server的端口号
	server.port=8762

	# 应用名称
	spring.application.name=eureka-server

	# 设置Eureka Server的主机名
	eureka.instance.hostname=eureka01

	# 设置Eureka Server的服务URL
	eureka.client.service-url.defaultZone=http://e1.microservices.com/eureka/

	# 增加数据库连接
	spring.datasource.url=jdbc:mysql://127.0.0.1:3306/database_start?useUnicode=true&characterEncoding=utf-8&zeroDateTimeBehavior=convertToNull
	spring.datasource.username=root
	spring.datasource.password=root
	spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
	```

6. 使用IP + 端口的方式来注册服务，在注册中心的application.properties文件都添加如下配置：

	```
	# 是否使用ip地址注册
	eureka.instance.prefer-ip-address=true

	# ip + 端口 注册服务
	eureka.instance.instance-id=${spring.cloud.client.ip-address}:${server.port}
	```

7. 在服务提供者（SpringBoot_World）的pom文件中添加如下依赖：

	```
	<dependencies>
		<!-- 网关服务Eureka Client相关依赖 -->
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
		</dependency>
	</dependencies>
	```

8. 在服务提供者（SpringBoot_World）的application.properties文件添加如下配置：

	```
	# 设置Eureka Server的端口号
	server.port=8086

	# 应用名称（集群下相同）
	spring.application.name=service-provider

	# 是否使用ip地址注册
	eureka.instance.prefer-ip-address=true

	# ip + 端口 注册服务
	eureka.instance.instance-id=${spring.cloud.client.ip-address}:${server.port}

	# 设置Eureka Server的服务URL
	eureka.client.service-url.defaultZone=http://e1.microservices.com/eureka/, http://e2.microservices.com/eureka/
	```

9.  在服务消费者（SpringBoot_User）的pom文件中添加如下依赖：

	```
	<dependencies>
		<!-- 网关服务Eureka Client相关依赖 -->
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
		</dependency>
	</dependencies>
	```

10. 在服务消费者（SpringBoot_User）的application.properties文件添加如下配置：

	```
	# 设置Eureka Server的端口号
	server.port=8080

	# 应用名称（集群下相同）
	spring.application.name=service-consumer

	# 禁用客户端向Eureka Server注册
	eureka.client.register-with-eureka=false

	# 表示Eureka Client间隔多久去服务器拉取注册信息，默认为30秒
	eureka.client.registry-fetch-interval-seconds=10

	# 设置Eureka Server的服务URL
	eureka.client.service-url.defaultZone=http://e1.microservices.com/eureka/, http://e2.microservices.com/eureka/
	```

11. 在您的Spring Boot微服务项目中，Service层注入一个DiscoveryClient实例。这个实例可以帮助您从Eureka注册中心获取服务实例的信息

	```
	@Autowired
	private DiscoveryClient discoveryClient;
	```

12. 在Service层的方法中，使用DiscoveryClient实例来获取目标微服务的实例信息。然后，根据实例信息构造目标微服务的URL

	```
	List<ServiceInstance> instances = discoveryClient.getInstances("service-provider");
	ServiceInstance instance = instances.get(0);
	String url = instance.getUri().toString() + "/world/findAll";
	```

13. 使用构造好的URL来调用目标微服务

	```
	CloseableHttpClient httpClient = HttpClients.createDefault();
	HttpGet httpGet = new HttpGet(url);
	CloseableHttpResponse response = httpClient.execute(httpGet);
	// ...
	```