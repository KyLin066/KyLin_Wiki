# Java学习笔记

## Java环境的安装与配置

---

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

---

### `引用`

参考文章：[完整的卸载Jdk java环境教程](https://www.cnblogs.com/pjhaymy/p/13735277.html)

<br>

### `使用`

1. 卸载下图中的两个程序：

    ![picture 4](../images/94ca388ea9815455ac58800f4de189a40697beec1cc4183392554efc72e70950.png)  

2. 在路径 C:\ProgramData\Oracle，删除Oracle文件夹

<br>

## Java基础语法

---

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

3. 可能遇到的错误和bug解决之道

4. 常用的dos命令介绍