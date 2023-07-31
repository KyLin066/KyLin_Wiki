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