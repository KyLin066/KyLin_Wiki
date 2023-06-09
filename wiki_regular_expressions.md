# 正则表达式

## 引用

推荐文章：[可能是最好的正则表达式的教程笔记了吧...](https://juejin.cn/post/6844903648309297166#heading-19)

推荐文章：[正则表达式教程-菜鸟教程](https://www.runoob.com/regexp/regexp-tutorial.html)

<br>

## 摘要

**基本语法**

| single char             | quantifiers             | position                |
| ----------------------- | ----------------------- | ----------------------- |
| \d 匹配数字              | * 0个或者更多            | ^一行的开头              |
| \w 匹配word(数字、字母)  | + 1个或更多，至少1个      | $一行的结尾              |
| \W 匹配非word(数字、字母)  | ? 0个或1个,一个Optional      | \b 单词"结界"(word bounds)              |
| \s 匹配white space(包括空格、tab等)  | {min,max}出现次数在一个范围内  |            |
| \S 匹配非white space(包括空格、tab等)  | {n}匹配出现n次的      |               |
| . 匹配任何，任何的字符  |      |               |

<br>

**single char**

- \w

    将匹配所有word，当然，() - 等字符除外

- \w\w\w

    发现匹配的有'`The`se `are` `som`e `pho`ne `number`s ...' 注意正则表达式是匹配一个连续串的规则，所以可以看到三个字母的单词可以匹配到，6个单词的也可以匹配到。

- \s\s

    匹配到一行中连续两个空格

<br>

**position**

- \w+

    这个应该毫无疑问，匹配所有的words

- ^\w+
    
    多了一个^，这样子，就只能匹配到每一行开头的单词了This is a words sequence Hello GoodBye Go

- \w+$
    
    这样就能匹配到每行的最后一个字母

<br>

**分类的简单应用**

字符序列：

> The lynk is quite a link don't you think? l nk l(nk

正则表达式： `l[yi (]nk`

结果:

> lynk  link  l nk   l(nk

很容易理解的，就是表达`或`逻辑。

<br>

**[]的特殊语法**

1. -连接符是第一个字符时

    比如[-.]的含义是连字符-或者点符.。 但是，如果当连字符不是第一个字符时，比如[a-z]，这就表示是从字母a到字符z。

2. []中的^

    ^在之前介绍中，是表示一行开头，但是在[]中，有着不同的含义。
    [ab] 表示a或者b
    [^ab] 啥都行，只要不是a或b(anythings except a and b)，相当于取反

> 除了使用`[]`表示或逻辑,`()`也是可以的。用法是`(a|b)`表示a或者b

<br>

**总结1**

1. `[]`的作用，用英文表达就是"alternation",表达一个或的逻辑；
2. `/[-.(]/` 在符号中的连字符-放在第一位表示连字符本身，如果放在中间，表示"从..到.."，比如`[a-z]`表示a-z
3. `[.)]` 括号中的特殊符号不需要转义，就表示其本身
4. `[^ab]` 括号中的^表示非，anythings except a and b
5. `(a|b)`也可表示选择，但是它有更强大的功能....

<br>

**匹配一个以1开头的电话号码**

        ^1\d{10}$
