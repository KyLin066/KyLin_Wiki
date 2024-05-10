# Java基础语法第五部分：Java数据类型转换和键盘输入

## **数据类型转化**

![数据类型转化](../images/260798fd606c86792cd996749e83da626eab4e66a7668d03463a8bc6d197b408.png)  

`Java数据类型转换案例代码（TestTypeConvert.java）：`

```
package e_type_convert;

public class TestTypeConvert {
    // 测试基本数据类型的转换（自动转换、强制转换）
    public static void main(String[] args) {
        // 自动类型转换：表数范围小的可以自动转换为表数范围大的
        long a1 = 3456;
        float a2 = a1;
        System.out.println(a2);

        // 整型常量直接赋值给byte/short/char等类型，只要不超过表数范围，则可以自动转换
        // byte b1 = 121;
        // byte b2 = 200; // byte：[-128, 127]，200超过byte的表数范围，则不合法

        // 算术运算符，两个操作数都是整型：有一个是long，则结果为long。否则结果为int（即使byte，结果也是int）
        long c1 = 1234;
        int c2 = 123;
        long c3 = c1 + c2;
        System.out.println(c3);

        // 算术运算符，有一个操作数是double，则结果是double
        double d1 = 3.14;
        int d2 = 3;
        double d3 = d1 + d2;
        System.out.println(d3);

        // 强制类型转换
        double e1 = 3.98;
        int e2 = (int) e1;
        System.out.println(e2);

        char e3 = 'c';
        int e4 = e3 + 2;
        char e5 = (char) e4;
        System.out.println(e5);

        // 当将一种类型强制转换成另一种类型，而又超出了目标类型的表数范围，就会被截断成一个完全不同的值。
        int f1 = 300;
        byte f2 = (byte) f1;
        System.out.println(f2);
    }
}
```

<br>

## **测试键盘输入**

`Java测试键盘输入案例代码（TestSystemIn.java）：`
```
package f_keypad_input;

import java.util.Scanner;

public class TestSystemIn {
    // 测试键盘输入
    public static void main(String[] args) {
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.print("请输入您的用户名：");
            String userName = scanner.nextLine();
            System.out.print("请输入您的年龄：");
            int age = scanner.nextInt();
            System.out.print("请输入您的月薪：");
            double salary = scanner.nextDouble();

            System.out.println("======录入的信息如下======");
            System.out.println("用户名：" + userName);
            System.out.println("年龄：" + age);
            System.out.println("年薪：" + (salary * 12));
        }
    }
}
```
