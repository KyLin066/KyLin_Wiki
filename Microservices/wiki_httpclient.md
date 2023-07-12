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

<br>

## `使用`

---

### 1.HttpClient使用Get发送请求的基本方法

```
package com.KyLin.SpringBoot_User.config;

import java.io.IOException;
import java.util.concurrent.TimeUnit;

import org.apache.hc.client5.http.classic.methods.HttpGet;
import org.apache.hc.client5.http.config.RequestConfig;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.core5.http.HttpEntity;
import org.apache.hc.core5.http.ParseException;
import org.apache.hc.core5.http.io.entity.EntityUtils;

/**
 * HttpClient使用Get发送请求的基本方法
 */
public class HttpClientTest1 {

    public static void main(String[] args) throws IOException, ParseException {

        // 全局参数配置
        RequestConfig requestConfig = RequestConfig.custom()
                .setResponseTimeout(10, TimeUnit.SECONDS)
                .setConnectTimeout(30, TimeUnit.SECONDS)
                .setConnectionRequestTimeout(10, TimeUnit.SECONDS)
                .build();

        /**
         * 发送一个Get请求
         */
        CloseableHttpClient httpClient = HttpClients.createDefault();

        HttpGet httpGet = new HttpGet("http://www.baidu.com");

        // 给Get请求设置全局参数
        httpGet.setConfig(requestConfig);

        CloseableHttpResponse response = httpClient.execute(httpGet);

        // 打印状态码
        // System.out.println(response.getCode());

        // Header[] headers = response.getHeaders();

        // for (Header header : headers) {
        // System.out.println(header.getName());
        // System.out.println(header.getValue());
        // }

        HttpEntity entity = response.getEntity();

        String result = EntityUtils.toString(entity);

        System.out.println(result);

    }

}
```

<br>

### 2.HttpClient使用连接池发送请求的方法

<br>

首先写一个工具类来配置连接池
```
package com.KyLin.SpringBoot_User.utils;

import java.util.concurrent.TimeUnit;

import org.apache.hc.client5.http.config.RequestConfig;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.client5.http.impl.io.PoolingHttpClientConnectionManager;

public class HttpUtils {

    // 创建连接池管理对象
    static PoolingHttpClientConnectionManager manager = new PoolingHttpClientConnectionManager();

    // 全局参数配置
    static RequestConfig requestConfig = RequestConfig.custom()
            .setResponseTimeout(10, TimeUnit.SECONDS)
            .setConnectTimeout(30, TimeUnit.SECONDS)
            .setConnectionRequestTimeout(10, TimeUnit.SECONDS)
            .build();

    static {
        // 配置最大的连接数
        manager.setMaxTotal(300);
        // 每个路由最大连接数，路由是根据host来管理的，所以这里的数量不太容易把握；
        manager.setDefaultMaxPerRoute(20);
    }

    // 获取连接对象，从连接池里面去获取
    public static CloseableHttpClient getHttpConnection() {
        CloseableHttpClient build = HttpClients.custom()
                .setConnectionManager(manager)
                .setDefaultRequestConfig(requestConfig)
                .build();
        return build;
    }

}
```

在主类中调用工具类来实现Get方法
```
package com.KyLin.SpringBoot_User.config;

import java.io.IOException;

import org.apache.hc.client5.http.classic.methods.HttpGet;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.core5.http.ParseException;
import org.apache.hc.core5.http.io.entity.EntityUtils;

import com.KyLin.SpringBoot_User.utils.HttpUtils;

/**
 * HttpClient使用连接池发送请求的方法
 */
public class HttpClientTest2 {

    public static void main(String[] args) throws IOException, ParseException {

        CloseableHttpClient httpConnection = HttpUtils.getHttpConnection();

        HttpGet httpGet = new HttpGet("http://www.baidu.com");

        CloseableHttpResponse execute = httpConnection.execute(httpGet);

        String s = EntityUtils.toString(execute.getEntity());

        System.out.println(s);

    }

}
```

<br>

### 3.HttpClient异步请求

TODO: