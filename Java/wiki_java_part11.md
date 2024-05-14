# Java基础语法第十一部分：面向对象的三大特征

## **继承**

### 一、继承的实现

1. 继承让我们更容易实现类的扩展。这样就实现了代码的重用，不用再重新发明轮子（don't reinvent wheels）

2. 从英文字面意思理解，extends的意思是“扩展”。子类是父类的扩展。

`继承使用要点：`

1. Java中只有单继承，没有像C++那样的多继承。

2. Java中类没有多继承，接口有多继承。

3. 子类继承父类，可以得到父类的全部属性和方法（除了父类的构造方法），但不见得可以直接访问（比如，父类私有的属性和方法）

4. 如果定义了一个类时，没有调用extends，则它的父类是：java.lang.Object。

### 二、instanceof运算符

```
instanceof的作用：判断对象是否是这个类的实例对象
```

`继承的实现和instanceof的运用案例代码（TestExtends.java）：`
```
package j_inherit;

/**
 * 测试继承的基本用法
 */
public class TestExtends {
    public static void main(String[] args) {
        Student stu1 = new Student("KyLin", 166, "java");
        stu1.rest();
        stu1.study();
        System.out.println(stu1.name);

        // instanceof判断对象是否是这个类的实例对象
        System.out.println(stu1 instanceof Student);
        System.out.println(stu1 instanceof Person);
    }
}

class Person {
    String name;
    int height;

    public void rest() {
        System.out.println("休息一会！");
    }
}

class Student extends Person {
    String major;

    public void study() {
        System.out.println("Student.study");
    }

    public Student(String name, int height, String major) {
        this.name = name;
        this.height = height;
        this.major = major;
    }
}
```

### 三、方法的重写override

```
方法的重写（override）：子类通过重写父类的方法可以用自身的行为替换父类的行为，方法的重写是实现多态的必要条件
```

`方法的重写需要符合下面的三个要点：`

1. “==”：方法名、形参列表相同。
2. “<=”：返回值类型和声明异常类型，子类小于等于父类。
3. “>=”：访问权限，子类大于等于父类。

`方法的重写案例代码（TestOverride.java）：`
```
package j_inherit;

/**
 * 测试重写
 */
public class TestOverride {
    public static void main(String[] args) {
        Horse h1 = new Horse();
        h1.run();

        Plane p1 = new Plane();
        p1.stop();
    }
}

class Vehicle {
    public void run() {
        System.out.println("run…");
    }

    public void stop() {
        System.out.println("stop…");
    }
}

class Horse extends Vehicle {
    @Override
    public void run() {
        System.out.println("四蹄纷飞，嘚嘚…");
    }
}

class Plane extends Vehicle {
    @Override
    public void run() {
        System.out.println("在空中飞…");
    }

    @Override
    public void stop() {
        System.out.println("在机场停下，不能在空中停");
    }
}
```

### 四、final的三种用法

`final关键字的作用：`

- 修饰变量：被它修饰的变量不可改变。一旦赋了初值，就不能被重新赋值。`final int MAX_SPEED = 120;`

- 修饰方法：该方法不可被子类重写。但是可以被重载！`final void study(){}`

- 修饰类：修饰的类不能被继承。比如：Math、String等。`final class A{}`

### 五、继承和组合

`组合的核心：`
```
“组合”的核心就是“将父类对象作为子类的属性”，然后，“子类通过调用这个属性来获得父类的属性和方法”。
```

`组合和继承的比较：`
1. 组合比较灵活。继承只能有一个父类，但是组合可以有多个属性。

2. 对于“is-a”关系建议使用继承，“has-a”关系建议使用组合。

`Java组合的案例代码（TestComposition.java）：`
```
package j_inherit;

/**
 * 测试组合
 */
public class TestComposition {
    public static void main(String[] args) {
        Stu stu = new Stu("KyLin", 166, "java");
        stu.person.rest();
        System.out.println(stu.person.name);
        System.out.println(stu.person.height);
        System.out.println(stu.major);
    }
}

class Stu {
    Person person = new Person();
    String major;

    public void study() {
        System.out.println("Stu.study");
    }

    public Stu(String name, int height, String major) {
        this.person.name = name;
        this.person.height = height;
        this.major = major;
    }
}

class CPU {
    void calculate() {
        System.out.println("CPU.calculate");
    }
}

class Memory {
    void store() {
        System.out.println("Memory.store");
    }
}

class Computer {
    CPU cpu = new CPU();
    Memory memory = new Memory();
}
```

<br>

## **封装**

## **多态**