# Java基础语法第三部分：基本数据类型

## **Java的数据类型：**

![Java数据类型](../images/34a8461858494d5cbbdf30123a59a733e0f7035e9a685208f9c4b4af0b34c12b.png)  

### 数值型

- `整型`

![整型](../images/6a3a7b4ed265078cb1b4439f28b7298c9fc1dfe617db7aaded96f774bd8e389c.png)  

- `浮点型`

![浮点型数据类型](../images/0f2533466b52ada3b4ebcda30398352433c44f6fd324b98911ee7f2ef8fc5904.png)  

![浮点数使用要点](../images/47598d7165f6fda5209b754014115d1656182c869895f5504e99c03ae2dbee22.png)  

Java整型数据类型案例代码（TestIntDouble.java）：

```
package c_data_type;

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

        System.out.println("十进制：" + t1);
        System.out.println("八进制：" + t2);
        System.out.println("十六进制：" + t3);
        System.out.println("二进制：" + t4);

        // 测试浮点数
        double d1 = 3.14;
        float f1 = 3.14F; // 浮点常量默认是

        double d2 = 314E-2; // 科学计数法：314*10^(-2)

        System.out.println("double型：" + d1);
        System.out.println("float型：" + f1);
        System.out.println("科学计数法：" + d2);

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

### 字符型

- `字符集`

    Java字符集数据类型案例代码（TestChar.java）：

    ```
    package c_data_type;

    public class TestChar {
        // Java基本数据类型之字符集
        public static void main(String[] args) {
            // 测试char
            char c1 = 'A';
            char c2 = '陈';

            System.out.println(c1);
            System.out.println(c2);
        }
    }
    ```

- `转义字符`

![转义字符](../images/634d8274eef1c38a9cce658b4665270d2df9f5311bc551eec0767d71906b48f3.png)  

### 布尔型

- `boolean型`

![布尔型](../images/7cf6b2b0e52b466d2b0c9ff320697eba862fa8c713fd0730c78b339b7871d782.png)  

Java字符集数据类型案例代码（TestBoolean.java）：

```
package c_data_type;

public class TestBoolean {
    // Java基本数据类型之Boolean型
    public static void main(String[] args) {
        boolean flag = true;
        if (flag) {
            System.out.println("I love coding");
        }
    }
}
```