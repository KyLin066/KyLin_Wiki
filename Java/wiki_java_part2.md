# Java基础语法第二部分：见名知意代码美

## **标识符**

`标识符四大准则：`

![标识符四大准则](../images/f794fe18b6b6bfd9abb22f38b268d1da059801e3054d446a0e7eefc02c5b5a18.png)  

`标识符使用规范：`

![标识符使用规范](../images/73dd58f7ee5a99a56c0e56eb7f033e7734909508aed38fdfad99839972b31859.png)  

<br>

## **注释**

![注释简介](../images/b675de1bdc9ab9ddef6e433942b3e337da2dc0c8d3bf66b6d24aa6093f2b9c30.png)  

<br>

## **Java关键字**

![关键字汇总](../images/c9b8337e3df9c741b115079a41a828085dd67cb0acb98e62abbc53cf5c941c3a.png)  

<br>

## **变量的本质**

![变量的本质](../images/403b00f8151331cd1d6396cc0e81f7bc1199c6b4aeab81adfe1fb21a6a058ac9.png)

`Java标识符以及变量的本质案例代码（TestVariable.java）：`
    
```
package b_variable;

public class TestVariable {
    // Java 标识符以及变量的本质
    public static void main(String[] args) {
        // 以下为合规的标识符
        // int age = 18;
        // int _age = 19;
        // int $age = 20;
        // int age123 = 21;
        // int 年龄 = 22;

        // 以下为不合规的标识符
        // int 123age = 23; // 数字不能做开头
        // int age# = 24; // 标识符只能是：字母、数字、下划线和$
        // int class = 25; // 标识符不能是关键字

        // 变量的本质
        int monthlySalary = 15000;
        int annualSalary = monthlySalary * 12;
        System.out.println("年薪：" + annualSalary);

        double bonus = 3000.1;
        System.out.println("奖金：" + bonus);
    }
}
```
