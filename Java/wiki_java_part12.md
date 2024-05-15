# Java基础语法第十二部分：Object类

## **Object类源码解析**

在Java中，`Object`类是所有类的最终超类。当你定义一个不扩展任何其他类的类时，它会隐式地扩展`java.lang.Object`。此外，基于接口的匿名类也会扩展`Object`。

`Object`类提供了一些通用的方法，每个对象都实现了这些方法。所有的公共方法都可以在数组或接口上调用。受保护的方法`clone`和`finalize`在数组或接口上不可访问，但所有数组类型都有一个可访问的公共版本的`clone`。

以下是`Object`类的一些主要方法：
- `public boolean equals(Object obj)`：指示某个其他对象是否与此对象“相等”。
- `protected Object clone() throws CloneNotSupportedException`：创建并返回此对象的一个副本。
- `public String toString()`：返回该对象的字符串表示。
- `public final void notify()`、`public final void notifyAll()`：唤醒在此对象监视器上等待的单个线程或所有线程。
- `public final void wait(long timeout) throws InterruptedException`：在其他线程调用此对象的 `notify()` 方法或 `notifyAll()` 方法前，导致当前线程等待。

如果你想深入了解`Object`类的源代码，可以参考[GNU Classpath的文档](https://developer.classpath.org/doc/java/lang/Object-source.html)，它提供了`Object`类的源代码。此外，还有一些工具，如[JArchitect](https://stackoverflow.com/questions/55380529/find-out-used-classes-and-methods-from-java-source-code)、[PMD Java](https://blog.codacy.com/java-static-code-analysis-tools)、[Checkstyle](https://blog.codacy.com/java-static-code-analysis-tools)等，可以帮助你进行静态代码分析，更好地理解和分析Java源代码。

<br>

## **重写toString()方法**
```
@Override
public String toString() {
    return "雇员编号：" + id + "，姓名：" + name;
}
```

<br>

## **重写equals()方法**
```
@Override
public int hashCode() {
    final int prime = 31;
    int result = 1;
    result = prime * result + id;
    return result;
}

@Override
public boolean equals(Object obj) {
    if (this == obj)
        return true;
    if (obj == null)
        return false;
    if (getClass() != obj.getClass())
        return false;
    Employee other = (Employee) obj;
    if (id != other.id)
        return false;
    return true;
}
```

<br>

## **案例代码**
`Java的Object类的案例代码（TestObject.java）：`
```
package k_object;

/**
 * 测试Object类的用法
 */
public class TestObject {
    public static void main(String[] args) {
        Employee e1 = new Employee(1001, "张三");
        Employee e2 = new Employee(1001, "张三");
        System.out.println(e1); // 打印对象默认是调用的toString()

        System.out.println(e1 == e2); // 两个对象是否相同
        System.out.println(e1.equals(e2)); // 重写equals之后，两个对象是否相等（逻辑上某些值的比较）
    }
}

class Employee extends Object {
    int id;
    String name;

    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public String toString() {
        return "雇员编号：" + id + "，姓名：" + name;
    }

    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + id;
        return result;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        Employee other = (Employee) obj;
        if (id != other.id)
            return false;
        return true;
    }
}
```