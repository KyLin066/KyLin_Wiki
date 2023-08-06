# Java学习笔记

## Java环境的安装与配置

### `引用`

参考视频：[Java背景知识和JDK安装和配置](https://www.bilibili.com/cheese/play/ep4884?t=469&csource=common_hp_history_null)

<br>

### `部署`

1. 进入官网下载JDK

    官网地址：<https://www.oracle.com/java/>

2. 安装

    下载好后直接安装，一直无脑下一步

3. 配置环境变量

    打开高级系统设置，点击环境变量，在系统变量中按下图配置

    ![picture 1](../images/2309d1c63d18bdfaca4ae7d1d99e690eec8c7d4d53d5eccee6c855a68307997f.png)  

    然后在Path中添加如下图内容，并且移到最上面

    ![picture 2](../images/66f13e6870c3d9c86562078db8bc4aec9012ffc41ecc6980bb96ed2754f5dc05.png)  


4. 测试安装是否成功

    ![picture 3](../images/d04abb34095033fb638ff084676bcabfa3c93ad9c11876de4d2f68c9448e18a1.png)  

<br>

## JDK的重新安装

### `引用`

参考文章：[完整的卸载Jdk java环境教程](https://www.cnblogs.com/pjhaymy/p/13735277.html)

<br>

### `使用`

1. 卸载下图中的两个程序：

    ![picture 4](../images/94ca388ea9815455ac58800f4de189a40697beec1cc4183392554efc72e70950.png)  

2. 在路径 C:\ProgramData\Oracle，删除Oracle文件夹

<br>

## Java基础语法

### `一、Hello World`

1. 写出我们第一个Java程序

    新建一个mycode文件夹，创建一个Welcome.java文件，输入以下代码

    ```
    public class Welcome {
        public static void main(String[] args){
            System.out.println("Hello World");
        }
    }
    ```

    在cmd窗口中执行以下操作：

    ![picture 5](../images/48d7c604ddb013163e585fda12dce3fdb08808fb45a89258230067e9076368f7.png)  

<br>

2. 了解Java程序的运行机制

    ![picture 6](../images/b2122f30c34b913be709bada3640f8a5dea2c77755d3bccf0dbff098bdbabe29.png)  

3. 常用的dos命令介绍

    ![picture 7](../images/c45f83a06114edd88c344f63add0b8d01276721a960c9dfa2f23c8542aac3f8c.png)  

<br>

### `二、见名知意代码美`

1. 标识符

    标识符四大准则：

    ![picture 8](../images/f794fe18b6b6bfd9abb22f38b268d1da059801e3054d446a0e7eefc02c5b5a18.png)  

    标识符使用规范：

    ![picture 9](../images/73dd58f7ee5a99a56c0e56eb7f033e7734909508aed38fdfad99839972b31859.png)  

    Java标识符案例代码（Test01.java）：

    ```
    public class Test01 {
        // Java 标识符
        public static void main(String[] args) {
            // 以下为合规的标识符
            int age = 18;
            int _age = 19;
            int $age = 20;
            int age123 = 21;
            int 年龄 = 22;

            // 以下为不合规的标识符
            // int 123age = 23; // 数字不能做开头
            // int age# = 24; // 标识符只能是：字母、数字、下划线和$
            // int class = 25; // 标识符不能是关键字
        }
    }
    ```

2. 注释

    ![picture 10](../images/b675de1bdc9ab9ddef6e433942b3e337da2dc0c8d3bf66b6d24aa6093f2b9c30.png)  

3. Java关键字

    ![picture 11](../images/c9b8337e3df9c741b115079a41a828085dd67cb0acb98e62abbc53cf5c941c3a.png)  

4. 变量的本质

    ![picture 12](../images/403b00f8151331cd1d6396cc0e81f7bc1199c6b4aeab81adfe1fb21a6a058ac9.png)

    Java变量的本质案例代码（Test01.java）：
    
    ```
    public class Test01 {
        // Java 标识符以及变量的本质
        public static void main(String[] args) {
            // 变量的本质
            int monthlySalary = 15000;
            int annualSalary = monthlySalary * 12;
            System.out.println("年薪：" + annualSalary);

            double bonus = 3000.1;
            System.out.println("奖金：" + bonus);
        }
    }
    ```

<br>

### `三、基本数据类型`

Java的数据类型：

![picture 13](../images/34a8461858494d5cbbdf30123a59a733e0f7035e9a685208f9c4b4af0b34c12b.png)  

#### `3.1 数值型`

#### 整型

![picture 14](../images/6a3a7b4ed265078cb1b4439f28b7298c9fc1dfe617db7aaded96f774bd8e389c.png)  

Java整型数据类型案例代码（TestIntDouble.java）：

```
public class TestIntDouble {
    // Java基本数据类型之整型和浮点型
    public static void main(String[] args) {
        byte age = 20;
        short salary = 25000;
        int beijingPopulation = 30000000;

        // 整型常量默认的类型是int，改成long类型需要后面加：L/l
        long globalPopulation = 7000000000L;
        System.out.println("整型数据类型：" + age + "," + salary + "," + beijingPopulation + "," + globalPopulation);

        // 关于进制
        int t1 = 65; // 十进制
        int t2 = 065; // 八进制
        int t3 = 0x65; // 十六进制
        int t4 = 0b01000001; // 二进制

        System.out.println(t1);
        System.out.println(t2);
        System.out.println(t3);
        System.out.println(t4);
    }
}
```

#### 浮点型

![picture 15](../images/0f2533466b52ada3b4ebcda30398352433c44f6fd324b98911ee7f2ef8fc5904.png)  

![picture 16](../images/47598d7165f6fda5209b754014115d1656182c869895f5504e99c03ae2dbee22.png)  

Java浮点型数据类型案例代码（TestIntDouble.java）：

```
public class TestIntDouble {
    // Java基本数据类型之整型和浮点型
    public static void main(String[] args) {
        // 测试浮点数
        double d1 = 3.14;
        float f1 = 3.14F; // 浮点常量默认是

        double d2 = 314E-2; // 科学计数法：314*10^(-2)

        System.out.println("double型："+d1);
        System.out.println("float型："+f1);
        System.out.println("科学计数法："+d2);

        // 浮点数是不精确的，用于比较要小心
        // 如果要使用精确的运算，使用BigDecimal类
        float f3 = 0.1F;
        double d3 = 0.1;

        System.out.println(f3);
        System.out.println(d3);
        System.out.println(f3 == d3);
    }
}
```

#### `3.2 字符型`

#### 字符集

Java字符集数据类型案例代码（TestChar.java）：

```
public class TestChar {
    // Java基本数据类型之字符集
    public static void main(String[] args) {
        // 测试char
        char c1='A';
        char c2='陈';

        System.out.println(c1);
        System.out.println(c2);
    }
}
```

#### 转义字符

![picture 17](../images/634d8274eef1c38a9cce658b4665270d2df9f5311bc551eec0767d71906b48f3.png)  

#### `3.3 布尔型`

#### boolean型

![picture 18](../images/7cf6b2b0e52b466d2b0c9ff320697eba862fa8c713fd0730c78b339b7871d782.png)  

Java字符集数据类型案例代码（TestBoolean.java）：

```
public class TestBoolean {
    // Java基本数据类型之Boolean型
    public static void main(String[] args) {
        boolean flag = true;
        if(flag){
            System.out.println("I love coding");
        }
    }
}
```

### `四、基本运算符`

#### `算术运算符`

![picture 19](../images/9725cb683d8c49053a39b9912646a668d2148e1ac47c52c31c4a42ffa152c945.png)  

#### `扩展运算符`

![picture 20](../images/c891d03eb99d7c1d31627800be5b048dbde828d95be14a3b49d807d3aeb88fb9.png)  

#### `关系运算符`

![picture 21](../images/67318be7244f433a0ad8339520cc7846753a270353781591f0be1ef9d4733886.png)  

#### `逻辑运算符`

![picture 22](../images/86c0e1418f85da3f3ecbcafc641dbde7e30aeb000bdf8e35e94f3c4af710ef5a.png)  

#### `位运算符`

![picture 23](../images/dc154b968235a534a1966c2cc8ddd1ff27821c8aeea77fb8fe2cd520bf876e73.png)  

#### `条件运算符`

![picture 24](../images/8e99228574e5b9b23454c3a71fb0886957cab7f09add3254cd0152f481f3522d.png)  

Java基本运算符案例代码（TestOperator.java）：

```
public class TestOperator {
    public static void main(String[] args) {
        System.out.println("======算术运算符======");
        int a = 3;
        int b = 4;
        int c = (a + b) * 4;
        System.out.println(c);
        int d = 15 / 4;
        System.out.println(d);
        int e = 5 % 3; // 结果是：余数2
        System.out.println(e);

        a = 10;
        b = a++; // 先赋值，后自增
        c = ++a; // 先自增，后赋值
        System.out.println(a);
        System.out.println(b);
        System.out.println(c);

        System.out.println("======扩展运算符======");
        a = 20;
        b = 30;
        a += b;
        System.out.println(a);
        System.out.println(b);

        System.out.println("======关系运算符======");
        a = 20;
        b = 30;
        boolean result = a < b;
        System.out.println(result);

        System.out.println("======逻辑运算符======");
        boolean b1 = true & false; // false
        boolean b2 = true | false; // true
        boolean b3 = !b2; // false
        boolean b4 = true ^ true; // false
        System.out.println(b1);
        System.out.println(b2);
        System.out.println(b3);
        System.out.println(b4);

        // 短路与、短路或
        // boolean x = 3 < 4 || (4 < 4 / 0);
        // System.out.println(x);

        System.out.println("======位运算符======");
        int m = 3;
        int n = 7;
        int p1 = m & n;
        int p2 = m | n;
        int p3 = m ^ n; // ^是异或的意思，不是数学中的幂运算
        int p4 = ~m; // 按位取反
        System.out.println(p1);
        System.out.println(p2);
        System.out.println(p3);
        System.out.println(p4);

        // 移位运算
        int x = 3 << 3; // 3*2*2 = 24
        int y = 12 >> 2; // 12/2/2 = 3
        System.out.println(x);
        System.out.println(y);

        System.out.println("======字符串连接符======");
        int r1 = 3;
        int r2 = 4;
        System.out.println(r1 + r2);
        System.out.println("结果是：" + r1 + r2); // 结果是：34

        System.out.println("======条件运算符======");
        int y1 = 300;
        int y2 = 40;
        int min = y1<y2?y1:y2; // 总是返回y1和y2比较小的值

        System.out.println(min);
    }
}
```