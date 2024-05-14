# Java基础语法第七部分：方法

## **方法的定义和调用**

![方法的定义](../images/a4d32d7535e6f0b7f6bb44950d515b3ff0c129eeb541430ce2c0a6488763933f.png)  

![方法声明格式](../images/dc43433066476a2b220d11d20afc2bd3e26e8e68b1fccdf4c0f7ed3118b635d9.png)  

![方法的调用过程](../images/56515e3dbd0a7cd2b2bd16b9513593d0e0421c1332bba55e76681d287c231756.png)  


`Java方法的定义和调用案例代码（TestMethod.java）：`
```
package h_method;

// 测试方法的定义和调用
public class TestMethod {
    // main方法，程序的主入口
    public static void main(String[] args) {
        int a1 = add(100, 200);
        int a2 = add(200, 300);
        int sum = add(a1, a2); // 实际参数
        System.out.println(sum);

        printInfo();
    }

    // 定义一个求和的方法（有参数，有返回值）
    public static int add(int n1, int n2) { // 形式参数
        int sum = n1 + n2;
        return sum;
    }

    // 定义一个打印信息的方法（没有参数，没有返回值）
    public static void printInfo() {
        System.out.println("KyLin");
    }
}
```

`简易计算器案例代码（Calculator.java）：`
```
package h_method;

import java.util.Scanner;

// 实现一个计算器
public class Calculator {
    public static void main(String[] args) {
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.print("请输入一个算术表达式：");
            String input = scanner.nextLine();

            String[] parts = input.split(" ");
            double num1 = Double.parseDouble(parts[0]);
            String operator = parts[1];
            double num2 = Double.parseDouble(parts[2]);

            switch (operator) {
                case "+":
                    System.out.println("结果: " + add(num1, num2));
                    break;
                case "-":
                    System.out.println("结果: " + subtract(num1, num2));
                    break;
                case "*":
                    System.out.println("结果: " + multiply(num1, num2));
                    break;
                case "/":
                    System.out.println("结果: " + divide(num1, num2));
                    break;
                default:
                    System.out.println("未知的运算符: " + operator);
                    break;
            }
        } catch (NumberFormatException e) {
            e.printStackTrace();
        }
    }

    // 相加操作
    public static double add(double n1, double n2) {
        double sum = n1 + n2;
        return sum;
    }

    // 相减操作
    public static double subtract(double n1, double n2) {
        double sum = n1 - n2;
        return sum;
    }

    // 相乘操作
    public static double multiply(double n1, double n2) {
        double sum = n1 * n2;
        return sum;
    }

    // 相除操作
    public static double divide(double n1, double n2) {
        double sum = n1 / n2;
        return sum;
    }
}
```

<br>

## **方法的重载**

![方法重载的定义](../images/bebdbc9e4bd510e133f23198ef1b9793d683f97e2c372582fed317afa52d7c1a.png)  

![重载雷区](../images/8260663904e894d611e485bbd2225e688286bd6904081695560101eca8a46137.png)  

![重载的条件](../images/d3624b781ee7c1fcb1a7f175f4704a94c6c8ed218cfda71568cb95af0b4b3204.png)  

`方法重载案例代码（TestOverload.java）：`
```
package h_method;

public class TestOverload {
    public static void main(String[] args) {
        add(100, 200);
        add(100.1, 200);
        add(100, 200, 300);
        add(100, 200.6);
    }

    // 求和的方法
    public static int add(int n1, int n2) {
        int sum = n1 + n2;
        System.out.println(sum);
        return sum;
    }

    // 方法名相同，参数类型不同，构成重载
    public static double add(double n1, int n2) {
        double sum = n1 + n2;
        System.out.println(sum);
        return sum;
    }

    // 方法名相同，参数个数不同，构成重载
    public static int add(int n1, int n2, int n3) {
        int sum = n1 + n2 + n3;
        System.out.println(sum);
        return sum;
    }

    // 方法名相同，参数顺序不同，构成重载
    public static double add(int n1, double n2) {
        double sum = n1 + n2;
        System.out.println(sum);
        return sum;
    }
}
```
