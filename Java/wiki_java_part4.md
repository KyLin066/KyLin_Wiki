# Java基础语法第四部分：基本运算符

## **算术运算符**

![算术运算符](../images/9725cb683d8c49053a39b9912646a668d2148e1ac47c52c31c4a42ffa152c945.png)  

<br>

## **扩展运算符**

![扩展运算符](../images/c891d03eb99d7c1d31627800be5b048dbde828d95be14a3b49d807d3aeb88fb9.png)  

<br>

## **关系运算符**

![关系运算符](../images/67318be7244f433a0ad8339520cc7846753a270353781591f0be1ef9d4733886.png)  

<br>

## **逻辑运算符**

![逻辑运算符](../images/86c0e1418f85da3f3ecbcafc641dbde7e30aeb000bdf8e35e94f3c4af710ef5a.png)  

<br>

## **位运算符**

![位运算符](../images/dc154b968235a534a1966c2cc8ddd1ff27821c8aeea77fb8fe2cd520bf876e73.png)  

<br>

## **条件运算符**

![条件运算符](../images/8e99228574e5b9b23454c3a71fb0886957cab7f09add3254cd0152f481f3522d.png)  

`Java基本运算符案例代码（TestOperator.java）：`

```
package d_operator;

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
        int min = y1 < y2 ? y1 : y2; // 总是返回y1和y2比较小的值

        System.out.println(min);
    }
}
```
