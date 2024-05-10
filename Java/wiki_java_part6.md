# Java基础语法第六部分：流程控制语句

## **选择结构**

### 一、if语句

![if语句执行流程](../images/44590d2d33ae609cfd4bebd3796b115b8ff12ff79f56ef21eede4f89be6ccd64.png)  

### 二、if…else…语句

![if…else…语句执行流程](../images/b9e2e35858a6592ee2154b79dd2439349360d06dff9dd4cd25c5efcb6d69a360.png)  

### 三、多分支语句

![多分支语句执行流程](../images/b8cef4b75b7b009789366fe4f27072176ae95b631fac11ae5db694f4981f1dc3.png)  

### 四、swich多值判断语句

![swich多值判断语句执行流程](../images/955a9773c36fb9e8b4ba7f6514303dce0ba2cfc9d5c96a49b9ed8a9d96592414.png)  

`Java测试选择结构案例代码（TestOption.java）：`
```
package g_control_language;

public class TestOption {
    // 测试选择结构
    public static void main(String[] args) {
        // System.out.println(Math.random()); // [0, 1)的随机数

        // [0, 10)的随机数
        int r = (int) (Math.random() * 10);
        System.out.println(r);

        // 如果r小于5，则打印“数比较小”
        if (r < 5) {
            System.out.println("数比较小");
        } else {
            System.out.println("数比较大");
        }

        // 生成一个在[0, 100]表示年龄的随机数
        // 13岁以下是儿童，13-35青年，36-59中年，60-85老年,85以上老寿星
        int age = (int) (Math.random() * 100);
        System.out.println("年龄" + age);
        if (age < 13) {
            System.out.println("儿童，珍惜童年的时光");
        } else if (age < 36) {
            System.out.println("青年，勇敢追逐自己的梦想");
        } else if (age < 60) {
            System.out.println("中年，不要虚度光阴");
        } else if (age < 86) {
            System.out.println("老年，好好享受养老生活");
        } else {
            System.out.println("老寿星，继续热爱生活吧");
        }

        // 随机生成a-z的字母；如果是a、e、i、o、u则输出“元音”，否则“辅音”
        int num = (int) (Math.random() * 26);
        char letter = 'a';
        letter = (char) (letter + num);
        if (letter == 'a' || letter == 'e' || letter == 'i' || letter == '0' || letter == 'u') {
            System.out.println("元音：" + letter);
        } else {
            System.out.println("辅音：" + letter);
        }

        // switch语句
        // grade表示大学年级
        int grade = (int) ((Math.random() * 4) + 1);

        switch (grade) {
            case 1:
                System.out.println("大学" + grade + "年级");
                break;
            case 2:
                System.out.println("大学" + grade + "年级");
                break;
            case 3:
                System.out.println("大学" + grade + "年级");
                break;
            default:
                System.out.println("大学" + grade + "年级");
                break;
        }

        // 判断季节
        int month = (int) ((Math.random() * 12) + 1);

        switch (month) {
            case 1:
            case 2:
            case 3:
                System.out.println("春季");
                break;
            case 4:
            case 5:
            case 6:
                System.out.println("夏季");
                break;
            case 7:
            case 8:
            case 9:
                System.out.println("秋季");
                break;
            default:
                System.out.println("冬季");
                break;
        }

        // 买车情况
        String car = "奔驰";

        switch (car) {
            case "奔驰":
                System.out.println("奔驰是一款经典汽车，它以其优雅的外观和卓越的性能而闻名。");
                break;
            case "宝马":
                System.out.println("宝马是一款豪华汽车，它拥有优秀的性能和舒适的驾驶体验。");
                break;
            case "奥迪":
                System.out.println("奥迪是一款高端汽车，它以其先进的技术和出色的性能而受到欢迎。");
                break;
            default:
                System.out.println("对不起，我不知道你买的是什么车。");
        }

        // 阿拉伯数字转换成大写汉字
        int number = (int) (Math.random() * 10);
        char s = ' ';

        switch (number) {
            case 0:
                s = '零';
                break;
            case 1:
                s = '壹';
                break;
            case 2:
                s = '贰';
                break;
            case 3:
                s = '叁';
                break;
            case 4:
                s = '肆';
                break;
            case 5:
                s = '伍';
                break;
            case 6:
                s = '陆';
                break;
            case 7:
                s = '柒';
                break;
            case 8:
                s = '捌';
                break;
            case 9:
                s = '玖';
                break;
        }

        System.out.println("阿拉伯数字：" + number + "，对应的大写汉字：" + s);

        // 系统角色
        String role = "超级管理员";
        int roleNum = 0;
        switch (role) {
            case "超级管理员":
                roleNum = 1;
                break;
            case "普通用户":
                roleNum = 2;
                break;
            default:
                roleNum = 3;
                break;
        }

        System.out.println(role + "------" + roleNum);

        // 超市会员积分奖励活动
        int score = (int) (Math.random() * 10000);
        System.out.println("用户积分：" + score);
        switch (score / 1000) {
            case 9:
            case 8:
            case 7:
                System.out.println("一等奖，奖励苹果20一台");
                break;
            case 6:
            case 5:
                System.out.println("二等奖，奖励苹果14一台");
                break;
            case 4:
            case 3:
                System.out.println("三等奖，奖励烟台苹果一筐");
                break;
            default:
                System.out.println("无奖励");
                break;
        }
    }
}
```

<br>

## **循环结构**

### 一、while循环

![while循环执行流程](../images/7bc3bc79119936b30be5130973baf84d50e92c623e300130ce73adf030c1d2d0.png)  

### 二、for循环

![for循环执行流程](../images/ed3b34523e4cbcda8171fa200ce94f28fa65c0fd75fdf25326d55d71b0bc0e98.png)  

`Java测试循环结构案例代码（TestCircuit.java）：`
```
package g_control_language;

public class TestCircuit {
    // 测试循环结构
    public static void main(String[] args) {
        // 打印 1-100
        int i = 1;
        while (i <= 100) {
            System.out.println(i);
            i++;
        }

        // 计算 1-100的和
        int num = 0;
        int sum = 0;
        while (num <= 100) {
            sum += num;
            num++;
        }
        System.out.println("1-100的和：" + sum);

        // 使用for循环打印 1-100
        System.out.println("for循环打印1-100：");
        for (int n = 0; n <= 100; n++) {
            System.out.println(n);
        }

        // 使用for循环计算 1-100的和
        int total = 0;
        for (int m = 0; m <= 100; m++) {
            total += m;
        }
        System.out.println("for循环计算1-100的和：" + total);
    }
}
```

### 三、嵌套循环

`Java测试嵌套循环案例代码（TestNestedCycle.java）：`
```
package g_control_language;

public class TestNestedCycle {
    // 测试嵌套循环
    public static void main(String[] args) {
        // 打印输出十行，每行输出0-9
        for (int line = 0; line < 10; line++) {
            for (int num = 0; num < 10; num++) {
                System.out.print(num + "\t");
            }
            System.out.println();
        }

        // 输出一个直角三角形
        System.out.println("输出一个直角三角形：");

        for (int line = 1; line <= 5; line++) {
            for (int num = 1; num <= line; num++) {
                System.out.print("*  ");
            }
            System.out.println();
        }

        // 输出一个倒立直角三角形
        System.out.println("输出一个倒立直角三角形：");

        for (int line = 1; line <= 5; line++) {
            for (int num = 1; num <= 6 - line; num++) {
                System.out.print("*  ");
            }
            System.out.println();
        }

        // 输出一个等腰三角形
        System.out.println("输出一个等腰三角形：");
        int tag = 4;
        for (int line = 0; line < 5; line++) {
            for (int num = 0; num < 10; num++) {
                if (num >= tag - line && num <= tag + line) {
                    System.out.print("* ");

                } else {
                    System.out.print("  ");
                }
            }
            System.out.println();
        }
    }
}
```

### 四、break和continue语句

![break和continue的含义](../images/a1b0b6eb664185d1e4d1e1d2f507fad180cb5686620f3c94cc996b40f92ad453.png)  

`Java测试break语句案例代码（TestBreak.java）：`
```
package g_control_language;

public class TestBreak {
    // 测试break语句
    public static void main(String[] args) {
        // 产生100以内的随机数，直到随机数为66时终止循环
        int count = 0;
        while (true) {
            int num = (int) (Math.random() * 100);
            System.out.println(num);
            count++;
            if (num == 66) {
                break;
            }
        }
        System.out.println("一共循环了" + count + "次");
    }
}
```

`Java测试continue语句案例代码（TestContinue.java）：`
```
package g_control_language;

public class TestContinue {
    // 测试continue语句
    public static void main(String[] args) {
        // 把100-150之间不能被3整除的数输出，并且每行输出5个
        int count = 0; // 计数器：表示每行输出几个
        for (int num = 100; num <= 150; num++) {
            if (num % 3 == 0) {
                continue;
            }
            System.out.print(num + "\t");
            count++;
            if (count % 5 == 0) {
                System.out.println();
            }
        }
    }
}
```

`Java测试break和continue语句案例代码（TestBreakContinue.java）：`
```
package g_control_language;

public class TestBreakContinue {
    // Java的Break和Continue语句综合练习
    public static void main(String[] args) {
        /*
         * 抓动物小游戏
         * 每次随机出现一个动物
         * 如果出现老虎，则游戏结束；如果出现老鹰，躲起来，等待下一个动物出现
         * 如果出现小猫、小狗、小鸟和小乌龟，可以抓住。计数，抓住多少个动物
         */

        // 0-老虎 1-老鹰 2-小猫 3-小狗 4-小鸟 5-小乌龟
        int total = 0;
        int cat = 0;
        int dog = 0;
        int bird = 0;
        int tortoise = 0;

        while (true) {
            int animal = (int) (Math.random() * 6);
            if (animal == 0) {
                System.out.println("老虎出现，撤退撤退！");
                break;
            } else if (animal == 1) {
                System.out.println("老鹰出现，注意注意，先躲起来");
                continue;
            } else if (animal == 2) {
                System.out.println("发现一只小猫，抓住");
                total++;
                cat++;
            } else if (animal == 3) {
                System.out.println("发现一只小狗，抓住");
                total++;
                dog++;
            } else if (animal == 4) {
                System.out.println("发现一只小鸟，抓住");
                total++;
                bird++;
            } else {
                System.out.println("发现一只小乌龟，抓住");
                total++;
                tortoise++;
            }
        }

        System.out.println("一个共抓到了" + total + "只动物");
        System.out.println("一个共抓到了" + cat + "只小猫");
        System.out.println("一个共抓到了" + dog + "只小狗");
        System.out.println("一个共抓到了" + bird + "只小鸟");
        System.out.println("一个共抓到了" + tortoise + "只小乌龟");
    }
}
```

<br>

## **控制语句综合练习**

`Java控制语句综合练习案例代码（TestControlSynthesis.java）：`
```
package g_control_language;

public class TestControlSynthesis {
    // 控制语句综合练习
    public static void main(String[] args) {
        // 使用for循环，打印出a-z的26个字母
        char letter = 'a';
        for (int num = 0; num < 26; num++) {
            char temp = (char) (letter + num);
            System.out.print(temp + " ");
        }

        System.out.println();

        // 打印九九乘法表
        System.out.println("打印九九乘法表：");
        for (int num1 = 1; num1 <= 9; num1++) {
            for (int num2 = 1; num2 <= num1; num2++) {
                System.out.print(num1 + "*" + num2 + "=" + num1 * num2 + "\t");
            }
            System.out.println();
        }
    }
}
```

`年薪计算小软件案例代码（SalarySoft.java）：`
```
package g_control_language;

/*
 * 年薪计算小软件
 */
import java.util.Scanner;

public class SalarySoft {
    /*
     * 薪水计算器
     * 1.通过键盘输入用户的月薪，每年是几个月的薪水
     * 2.输出用户的年薪
     * 3.输出一行字“如果年薪超过10万，恭喜你超越90%的人”，“如果年薪超过20万，恭喜你超越98%的人”
     * 4.直到键盘输入数字88，则退出程序
     * 5.输入中途，键盘输入数字66，则这个用户退出计算不显示“恭喜……”，直接显示“重新开始计算……”，然后算下一个用户的年薪
     */
    public static void main(String[] args) {
        System.out.println("年薪计算小程序");
        while (true) {
            try (Scanner scanner = new Scanner(System.in)) {
                System.out.print("请输入您的月薪：");
                int salary = scanner.nextInt();
                System.out.print("请问您每年领几个月的薪水：");
                int month = scanner.nextInt();

                int result = salary * month;
                if (result >= 100000 && result < 200000) {
                    System.out.println("恭喜你超越90%的人");
                    System.out.println("您的年薪是" + salary * month);
                } else if (result >= 200000) {
                    System.out.println("恭喜你超越98%的人");
                    System.out.println("您的年薪是" + salary * month);
                } else {
                    System.out.println("您的年薪是" + salary * month);
                }

                System.out.println("请输入命令：[66]继续  [88]退出");
                int tag = scanner.nextInt();
                if (tag == 88) {
                    System.out.println("程序结束");
                    break;
                }
                if (tag == 66) {
                    System.out.println("请重新输入数据");
                    continue;
                }
            }
        }
    }
}
```