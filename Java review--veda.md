# Java review--veda

> 本文档由 **veda-chen** (veda-chen@foxmail.com)独立撰写并维护，转载请注明出处。
>
> 引言：本文档为有C++基础的新手学习Java所写，比官方文档易懂(๑>◡<๑)
>
> 版本：2025.12.15

### Chatper1

![image-20251211150325652](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211150325652.png)

Java is a general purpose programming language. 

Key Concepts of the Java Programming Language：

​     Object-oriented    ，Distributed，      Simple   ，    Multi-threaded ，       Secure  ，      Platform-independent

Memory management is automatic.



##### Platform-Independent Programs

![image-20251211172536607](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211172536607.png)

​                                  （配图：.java 源文件 → Java 编译器 → .class 字节码文件 → 不同平台 JVM 执行）
（说明：Java 程序通过 “一次编写，到处运行” 实现跨平台：
编写.java 源文件
经 Java 编译器（javac）编译为.class 字节码文件
任何安装了 Java 虚拟机（JVM）的平台，均可解释执行该字节码



##### JDK、JVM、JRE 概念区分

JVM

Java Virtual Machine (JVM) is required on every platform where your programming will run. The Java Virtual Machine is responsible for <u>interpreting Java technology code, loading Java classes, and executing Java technology programs.</u>

JRE

A Java technology program also <u>needs a set of standard Java class libraries</u> for the platform. Java class libraries are libraries of prewritten code that can be combined with the code that you write to create robust applications.

Combined, <u>the JVM software and Java class librarie</u>s are referred to as the Java runtime environment (JRE).

JDK

<u>Java Development Kit, including JRE/ Java tool(javac/java/jdb) and Java API .</u>

![image-20251211173315043](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211173315043.png)



##### Java 技术产品体系识别

Java SE（标准版）：用于开发 Web 浏览器中的小程序（Applets）和台式计算机应用程序。本书使用 J2SE（Java 2 平台标准版）介绍 Java 编程。
Java EE（企业版）：用于创建大型企业级、服务器端及客户端分布式应用程序。
Java ME（微型版）：用于为资源受限的消费设备开发应用程序。
Java Card（Java 卡）：主要应用于以下领域（及更多场景）：身份认证、安全防护、交易处理、手机 SIM 卡。



关键字（Reserved words）

要运行一个类，该类必须包含 main 方法 —— 程序从 main 方法开始执行。

![image-20251211192059727](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211192059727.png)



##### 编程错误类型

语法错误（Syntax Errors）：编译器可检测到的错误（如语法格式错误）
运行时错误（Runtime Errors）：导致程序异常终止的错误（如除零）
逻辑错误（Logic Errors）：程序运行正常但结果不正确的错误（如算法逻辑错误）



编译命令：javac 文件名.java（如javac GoodMorning.java）
运行命令：java 类名（如java GoodMorning）



### Chatper2

![image-20251211192723937](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211192723937.png)

##### 从控制台读取输入

创建 Scanner 对象：Scanner input = new Scanner(System.in);
使用 nextDouble () 方法获取 double 类型值，示例如下：

```java
System.out.print("输入一个double类型值："); // 提示用户输入
Scanner input = new Scanner(System.in); // 创建Scanner对象
double d = input.nextDouble(); // 读取用户输入的double值并赋值给d
```

An identifier cannot be true, false, or null.

![image-20251211212301571](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211212301571.png)



常量使用final修饰，声明时必须初始化，且初始化后值不可修改



##### 数值运算符

![image-20251211212500126](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211212500126.png)



Floating-point literals can also be specified in scientific notation, for example, 1.23456e+2, same as 1.23456e2, is equivalent to 123.456, and 1.23456e-2 is equivalent to 0.0123456. E (or e) represents an exponent and it can be either in lowercase or uppercase. 



Exponent Operations幂运算

Math.pow(a, b) 用于计算 a 的 b 次幂，返回值为 double 类型。



##### 数值常量字面量（Number Literals）

A literal is a constant value that appears directly in the program. For example, 34, 1,000,000, and 5.0 are literals in the following statements

An integer literal can be assigned to an integer variable as long as it can fit into the variable.

Floating-point literals are written with a decimal point. By default, a floating-point literal is treated as a double type value.

浮点字面量必须包含小数点。默认情况下，浮点字面量是 double 类型。例如，5.0 被视为 double 类型，而非 float 类型。
若要表示 float 类型的浮点字面量，需在末尾加字母 f 或 F；表示 double 类型可加 d 或 D（可省略，默认即为 double）。

The double type values are more accurate than the float type values. 



Augmented Assignment Operators（增强赋值运算符)

例：+=



##### Conversion Rules（类型转换规则）

当二元运算（含两个操作数）的两个操作数类型不同时，Java 会按以下规则自动转换操作数类型：
若其中一个操作数是 double 类型，另一个操作数转为 double 类型。
否则，若其中一个操作数是 float 类型，另一个操作数转为 float 类型。
否则，若其中一个操作数是 long 类型，另一个操作数转为 long 类型。
否则（均为 byte/short/int），两个操作数均转为 int 类型。

增强赋值表达式中的类型转换
在 Java 中，x1 op= x2形式的增强赋值表达式等价于x1 = (T)(x1 op x2)，其中 T 是 x1 的数据类型（自动强制转换）。因此以下代码是合法的：

```java
int sum = 0;
sum += 4.5; // sum becomes 4 after this statement
```



### Chatper3

![image-20251211214945319](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211214945319.png)

##### The boolean Type and Operators

```java
boolean b = (1 > 2); 
```



##### One-way if Statements

```java
if (boolean-expression) {
  statement(s);
}
```

##### The Two-way if Statement

```java
if (boolean-expression) {
  statement(s)-for-the-true-case;
}
else {
  statement(s)-for-the-false-case;
}
```



##### Operator Precedence

![image-20251211220229136](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211220229136.png)



##### Debugger

Debugger is a program that facilitates debugging. You can use a debugger to

Execute a single statement at a time.

Trace into or stepping over a method.

Set breakpoints.

Display variables.

Display call stack.

Modify variables.



### Chatper4

![image-20251211221032976](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211221032976.png)

##### The Math Class

Class constants:

PI

E

Class methods:

######  Trigonometric Methods （三角函数方法）

     核心方法：sin（正弦）、cos（余弦）、tan（正切）、acos（反余弦）、asin（反正弦）、atan（反正切）

​    说明：方法参数为弧度值，若输入角度需用 toRadians (角度) 转换（如 90 度转弧度：Math.toRadians (90)）

###### Exponent Methods（指数函数方法）

exp (double a)：返回 e 的 a 次幂（e 为自然常数）。
log (double a)：返回 a 的自然对数（以 e 为底）。
log10 (double a)：返回 a 的常用对数（以 10 为底）。
pow (double a, double b)：返回 a 的 b 次幂。
sqrt (double a)：返回 a 的平方根（a≥0）。

###### Rounding Methods取整方法

ceil (double x)：向上取整，返回 double 类型（如 2.1→3.0，-2.1→-2.0）。
floor (double x)：向下取整，返回 double 类型（如 2.1→2.0，-2.1→-3.0）。
rint (double x)：四舍五入取整，若 x 距离两个整数相等，返回偶数（如 2.5→2.0，-2.5→-2.0）。
round (float x)：四舍五入取整，返回 int 类型（等价于 (int) Math.floor (x+0.5)）。
round (double x)：四舍五入取整，返回 long 类型（等价于 (long) Math.floor (x+0.5)）

###### min, max, abs, and random Methods

max (a, b)：返回两个参数的最大值（支持 int、double 等数值类型）。
min (a, b)：返回两个参数的最小值。
abs (a)：返回参数的绝对值。
random ()：返回 [0.0, 1.0) 区间的随机 double 值。

###### 随机数方法（random ()）

说明：生成 [0.0, 1.0) 区间的随机 double 值，左闭右开。
示例：
(int)(Math.random () * 10) → 生成 0-9 的随机整数（Math.random ()*10 得到 [0.0,10.0)，强转为 int 后舍弃小数）。
通用公式：a + Math.random () * b → 生成 [a, a+b) 区间的随机数（a 为起始值，b 为区间长度）。
示例：生成 5-15 的随机整数 → (int)(5 + Math.random () * 10)（5 为起始值，10 为区间长度，结果为 5-14 的整数）。



##### Character Data Type（字符数据类型）

char 变量支持自增自减运算符，可获取相邻的 Unicode 字符

ASCII Code for Commonly Used Characters

![image-20251211225527317](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211225527317.png)

![](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211225626602.png)

##### Casting between char and Numeric Types

char 转 int：直接赋值，自动转换为对应的 Unicode 码（ASCII 码是其子集）。
示例：int i = 'a'; → i 的值为 97（'a' 的 ASCII 码），等价于int i = (int)'a';。
int 转 char：需强制转换，将数值作为 Unicode 码转换为对应字符。
示例：char c = 97; → c 的值为 'a'，等价于char c = (char)97;。



##### Character 类的静态方法（字符判断与转换）

| 方法名                   | 功能                     | 示例                           | 结果  |
| ------------------------ | ------------------------ | ------------------------------ | ----- |
| isDigit(char ch)         | 判断是否为数字字符       | Character.isDigit('5')         | true  |
| isLetter(char ch)        | 判断是否为字母字符       | Character.isLetter('A')        | true  |
| isLetterOrDigit(char ch) | 判断是否为字母或数字字符 | Character.isLetterOrDigit('_') | false |
| isLowerCase(char ch)     | 判断是否为小写字母       | Character.isLowerCase('b')     | true  |
| isUpperCase(char ch)     | 判断是否为大写字母       | Character.isUpperCase('c')     | false |
| toLowerCase(char ch)     | 转换为小写字母           | Character.toLowerCase('D')     | 'd'   |
| toUpperCase(char ch)     | 转换为大写字母           | Character.toUpperCase('e')     | 'E'   |

##### 

##### The String Type 

String is actually a predefined class in the Java library just like the System class and Scanner class. The String type is not a primitive type. It is known as a reference type.

String 类的常用实例方法

| 方法名                                  | 功能                                                |
| --------------------------------------- | --------------------------------------------------- |
| length()                                | 返回字符串长度（字符个数）                          |
| charAt(int index)                       | 返回指定索引位置的字符（索引从 0 开始）             |
| concat(String s)                        | 拼接字符串 s，返回新字符串                          |
| toUpperCase()                           | 转换为大写，返回新字符串                            |
| toLowerCase()                           | 转换为小写，返回新字符串                            |
| trim()                                  | 去除首尾空格，返回新字符串                          |
| equals(String s)                        | 比较字符串内容是否相等（区分大小写）                |
| compareTo(String s)                     | 按字典序比较字符串，返回 int 值                     |
| substring(int beginIndex)               | 从 beginIndex 截取到末尾，返回子字符串              |
| substring(int beginIndex, int endIndex) | 从 beginIndex 截取到 endIndex（不含），返回子字符串 |
| indexOf(char ch)                        | 返回字符 ch 首次出现的索引，未找到返回 - 1          |
| indexOf(String s)                       | 返回子字符串 s 首次出现的索引，未找到返回-1         |

示例

```java
String s3 = s1.concat(s2); or String s3 = s1 + s2;
// 拼接三个字符串
String message = "Welcome " + "to " + "Java"; // 结果：Welcome to Java
// 字符串与数字拼接（数字2转为字符串）
String s = "Chapter" + 2; // 结果：Chapter2
// 字符串与字符拼接（字符'B'转为字符串）
String s1 = "Supplement" + 'B'; // 结果：SupplementB
```



##### Comparing Strings

![image-20251211232015166](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251211232015166.png)

只有实现了 java.lang.Comparable<T> 接口的类才拥有 compareTo() 方法，该接口是 Java 用于自然排序的核心接口。



##### Conversion between Strings and Numbers

字符串转数值：

```java
int intValue = Integer.parseInt(intString);
double doubleValue = Double.parseDouble(doubleString);
```

数值转字符串：

```java
String s = number + "";
String s = String.valueOf(number);
String s = Integer.toString(number);
```



##### Formatting Output

```
System.out.printf(format, items);
```

常用格式说明符
格式说明符	输出类型	                                                示例
%b	              布尔值	                                                 true 或 false
%c	               字符	                                                   'A'、'5' 等
%d	               十进制整数	                                        200、-100 等
%f	                浮点型数字	                                        45.46（默认保留 6 位小数）
%e	               科学计数法表示的数字	                      4.556000e+01（即 45.56）
%s	                字符串	                                                 "Java is cool"、"Hello" 等



### Chatper5

![image-20251212162824457](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251212162824457.png)

都是循环语法基础，与C++并无二致



### Chatper6

![image-20251212163525929](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251212163525929.png)

A method is a collection of statements that are grouped together to perform an operation.

Method signature is the combination of the method name and the parameter list.

方法签名：方法名与形参列表的组合，是方法的唯一标识（与返回值无关）。

形参（Formal Parameters）：方法定义时括号内声明的变量，用于接收调用时传入的值。
示例：sum 方法中的int i1, int i2。
实参（Actual Parameters）：调用方法时传入的具体值，需与形参的类型、顺序一致。
示例：sum(1, 10)中的1和10。



##### Reuse Methods from Other Classes

方法的核心优势之一是可复用：TestMax 类中的 max 方法可被其他类调用。
调用语法：类名.方法名(实参)（前提是方法为 public static）。
示例（Test 类调用 TestMax 类的 max 方法）：

```java
public class Test {
  public static void main(String[] args) {
    int a = 10, b = 20;
    // 跨类调用TestMax类的max方法
    int maxValue = TestMax.max(a, b);
    System.out.println("最大值：" + maxValue);
  }
}
```



##### 方法调用栈（Call Stacks）

每个方法调用时，Java 虚拟机（JVM）会创建一个 “激活记录”（存储方法的形参、局部变量、返回地址等）并压入栈中。
执行流程与栈变化：
main 方法调用时，其激活记录入栈，成为栈顶；
main 方法调用 max 方法，max 方法激活记录入栈，成为新栈顶；
max 方法执行完毕，激活记录出栈，栈顶回到 main 方法；
main 方法继续执行，完毕后激活记录出栈，栈为空。



##### Overloading Methods

方法重载：多个方法同名，但形参列表（个数、类型、顺序）不同，用于实现类似功能（如求不同类型数据的最大值）。



##### Ambiguous Invocation

歧义调用：调用重载方法时，多个方法均能匹配实参，编译器无法确定最优匹配，导致编译报错。



##### The RandomCharacter Class

```java
// RandomCharacter.java: Generate random characters
public class RandomCharacter {
  /** Generate a random character between ch1 and ch2 */
  public static char getRandomCharacter(char ch1, char ch2) {
    return (char)(ch1 + Math.random() * (ch2 - ch1 + 1));
  }

  /** Generate a random lowercase letter */
  public static char getRandomLowerCaseLetter() {
    return getRandomCharacter('a', 'z');
  }

  /** Generate a random uppercase letter */
  public static char getRandomUpperCaseLetter() {
    return getRandomCharacter('A', 'Z');
  }

  /** Generate a random digit character */
  public static char getRandomDigitCharacter() {
    return getRandomCharacter('0', '9');
  }

  /** Generate a random character */
  public static char getRandomCharacter() {
    return getRandomCharacter('\u0000', '\uFFFF');
  }
}
```



##### Stepwise Refinement

实现方式：自顶向下（Top-Down）
自顶向下：从结构图表的顶层方法开始，逐步实现下层方法。未实现的方法用 “存根”（stub，简单占位实现）替代，便于测试上层方法。
示例：先实现 main 方法，printMonth 方法用存根（仅打印年份和月份），再逐步实现 getDayOfWeek 等辅助方法。
实现方式：自底向上（Bottom-Up）
自底向上：从结构图表的底层辅助方法开始实现，每个方法实现后单独测试，再逐步整合上层方法。
优势：便于隔离错误，每个方法独立测试通过后再整合，降低调试难度。



### Chatper7

![image-20251212170807600](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251212170807600.png)

##### Declaring Array Variables

```java
datatype[] arrayRefVar;
```

Example:     double[] myList;

```java
double[] myList = new double[10]; // 声明并创建长度为10的double数组
```



- 数组创建后长度固定，通过`arrayRefVar.length`获取长度。

  ```java
  double[] myList = new double[10];
  System.out.println(myList.length); // 输出10
  ```



- 数组创建后，元素自动赋默认值：
  - 数值基本类型（byte/short/int/long/float/double）：0
  - char 类型：'\u0000'（空字符）
  - boolean 类型：false

##### Initializing arrays with input values

```java
java.util.Scanner input = new java.util.Scanner(System.in);
System.out.print("Enter " + myList.length + " values: ");
for (int i = 0; i < myList.length; i++)
  myList[i] = input.nextDouble();
```



##### Enhanced for Loop (for-each loop)

```java
for (double value: myList) {
  System.out.println(value);
}
```



##### Copying Arrays

```java
int[] sourceArray = {2, 3, 1, 5, 10};
int[] targetArray = new int[sourceArray.length];
for (int i = 0; i < sourceArray.length; i++) {
  targetArray[i] = sourceArray[i];
}
```



##### System.arraycopy () 

语法：JDK 提供的高效数组复制方法

```java
System.arraycopy(原数组, 原数组起始索引, 目标数组, 目标数组起始索引, 复制长度);
```

```java
int[] sourceArray = {2, 3, 1, 5, 10};
int[] targetArray = new int[sourceArray.length];
// 从原数组索引0开始，复制到目标数组索引0，复制长度为原数组长度
System.arraycopy(sourceArray, 0, targetArray, 0, sourceArray.length);
```



##### 数组作为方法参数

- 方法定义：数组作为参数时，参数类型为 “数据类型 []”。

  ```java
  // 打印数组元素的方法
  public static void printArray(int[] array) {
    for (int i = 0; i < array.length; i++) {
      System.out.print(array[i] + " ");
    }
  }
  ```

- 调用方式 1（传递已定义数组）：

  ```java
  int[] list = {3, 1, 2, 6, 4, 2};
  printArray(list); // 输出：3 1 2 6 4 2
  ```

- 调用方式 2（传递匿名数组，无需定义变量）：

  ```java
  printArray(new int[]{3, 1, 2, 6, 4, 2}); // 效果同上
  ```



##### Anonymous Array

语法：`new dataType[]{literal0, literal1, ..., literalk};`

说明：无显式引用变量的数组，仅在方法调用时临时使用。

语法：创建数组时不定义引用变量，直接作为方法参数或赋值。

```java
new 数据类型[]{元素0, 元素1, ..., 元素k}
```

```java
// 匿名数组作为方法参数
printArray(new int[]{3, 1, 2});
// 匿名数组直接赋值（较少用）
int[] arr = new int[]{5, 6, 7};
```

优势：简化代码，无需为临时使用的数组定义变量。



数组类型参数：传递数组引用的 “值副本”，副本与原引用指向同一数组，因此方法内修改数组元素会影响原数组。



##### Call Stack & Heap

- 栈内存（Stack）：存储方法调用的激活记录、局部变量（包括数组引用）；
- 堆内存（Heap）：存储数组实体（元素数据）；
- 数组引用变量在栈中，数组实体在堆中，引用变量存储堆中数组的地址。



##### Searching Arrays

查找：在数组中寻找特定元素，返回其索引（未找到返回 - 1）；

两种常用算法：线性查找（无序数组）、二分查找（有序数组）。

###### Linear Search

```java
public static int linearSearch(int[] list, int key) {
  for (int i = 0; i < list.length; i++) {
    if (key == list[i]) {
      return i; // 找到，返回索引
    }
  }
  return -1; // 未找到
}
```

###### Binary Search

- 前提：数组必须有序（升序 / 降序）；
- 逻辑：每次与数组中间元素比对，缩小查找范围：
  1. key < 中间元素 → 查找左半部分；
  2. key == 中间元素 → 找到，返回索引；
  3. key > 中间元素 → 查找右半部分；

```java
/** 二分查找有序数组list中的key，返回索引；未找到返回-1-low */
public static int binarySearch(int[] list, int key) {
  int low = 0;
  int high = list.length - 1;
  while (high >= low) {
    int mid = (low + high) / 2; // 中间索引
    if (key < list[mid]) {
      high = mid - 1; // 查找左半部分
    } else if (key == list[mid]) {
      return mid; // 找到，返回索引
    } else {
      low = mid + 1; // 查找右半部分
    }
  }
  return -1 - low; // 未找到，返回插入点的负数-1
}
```



##### The Arrays.binarySearch Method

```java
int[] list = {2,4,7,10,11,45,50,59,60,66,69,70,79};
System.out.println(java.util.Arrays.binarySearch(list, 11)); // 输出4
char[] chars = {'a','c','g','x','y','z'};
System.out.println(java.util.Arrays.binarySearch(chars, 't')); // 输出-4
```



##### Selection Sort

- 逻辑：
  1. 找到数组未排序部分的最小值；
  2. 将最小值与未排序部分的第一个元素交换；
  3. 重复步骤 1-2，直到整个数组排序完成。



##### Arrays.sort () 方法

```java
double[] numbers = {6.0,4.4,1.9,2.9,3.4,3.5};
java.util.Arrays.sort(numbers); // 升序排序
char[] chars = {'a','A','4','F','D','P'};
java.util.Arrays.sort(chars); // 按Unicode值排序
```



##### The Arrays.toString(list) Method

功能：返回数组的字符串表示（格式：[元素 1, 元素 2, ...]），方便打印。

```java
int[] list = {1,2,3,4}; 
System.out.println(Arrays.toString(list)); // 输出[1, 2, 3, 4]
```



##### Pass Arguments to Invoke the Main Method

- main 方法的参数：`public static void main(String[] args)`，args 接收命令行参数；
- 调用方式：`java 类名 参数1 参数2 ...`；
- 示例：`java Calculator 2 + 3`，args = {"2", "+", "3"}。



### Chatper9

![image-20251212212723407](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251212212723407.png)

##### UML Class Diagram

![image-20251212213009241](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251212213009241.png)

Reference Data Fields：String



##### Default Value for a Data Field

Reference type: null;
Numeric type: 0;
boolean: false;
char: '\u0000';
Local variables have no default values.

Java assigns no default value to a local variable inside a method. 



##### Differences between Variables of Primitive Data Types and Object Types

基本类型变量与引用类型变量的区别

| 维度     | 基本类型变量（如 int、double） | 引用类型变量（如 Circle、String） |
| -------- | ------------------------------ | --------------------------------- |
| 存储内容 | 直接存储值（如 5、3.14）       | 存储对象的引用（堆内存地址）      |
| 内存位置 | 栈内存                         | 变量本身在栈，对象在堆            |
| 默认值   | 有（如 int 默认 0）            | 有（默认 null）                   |
| 赋值操作 | 复制值本身                     | 复制引用（指向同一对象）          |



##### Garbage Collection

当对象没有任何引用变量指向时，成为 “垃圾”；
JVM 自动回收垃圾对象的内存（无需手动释放）；
显式赋值 null 可让对象成为垃圾（如c1 = null;）。



##### Date类

```java
// 导入Date类
import java.util.Date;

public class TestDate {
  public static void main(String[] args) {
    // 创建Date对象（初始化当前日期时间）
    Date date = new Date();
    
    // 调用toString()方法，返回标准格式的日期时间字符串
    System.out.println(date.toString()); 
    // 输出示例：Sun Mar 09 13:50:19 EST 2003
  }
}
```



##### Random 类

Random 类位于 java.util 包，相比 Math.random () 更灵活，支持生成指定范围的整数、长整数、浮点数等。
核心用法：
无参构造器：使用当前时间作为种子，生成随机序列；
带参构造器：使用指定种子（seed），种子相同则生成相同序列（便于测试）；
常用方法：
nextInt (n)：生成 [0, n) 的随机整数；
nextDouble ()：生成 [0.0, 1.0) 的随机浮点数。

```java
import java.util.Random;

public class TestRandom {
  public static void main(String[] args) {
    // 种子为3的Random对象
    Random random1 = new Random(3);
    System.out.print("random1生成的随机数：");
    for (int i = 0; i < 10; i++) {
      System.out.print(random1.nextInt(1000) + " "); // 0-999的随机整数
    }
    
    // 相同种子的Random对象（生成相同序列）
    Random random2 = new Random(3);
    System.out.print("\nrandom2生成的随机数：");
    for (int i = 0; i < 10; i++) {
      System.out.print(random2.nextInt(1000) + " ");
    }
  }
}
```



##### Point2D 类

Point2D 类位于 javafx.geometry 包，用于表示二维平面上的点，提供坐标存储和距离计算功能。

```java
import javafx.geometry.Point2D;

public class TestPoint2D {
  public static void main(String[] args) {
    // 创建Point2D对象（x=1.0，y=2.0）
    Point2D point1 = new Point2D(1.0, 2.0);
    
    // 创建另一个Point2D对象（x=4.0，y=6.0）
    Point2D point2 = new Point2D(4.0, 6.0);
    
    // 计算两点之间的距离
    double distance = point1.distance(point2);
    System.out.println("两点距离：" + distance); // 输出5.0
    
    // 获取point1的x坐标
    System.out.println("point1的x坐标：" + point1.getX()); // 输出1.0
  }
}
```



#####  Visibility Modifiers and Accessor/Mutator Methods

访问修饰符（控制成员的可见范围）：

| 修饰符  | 可见范围       |
| ------- | -------------- |
| public  | 所有类（跨包） |
| private | 仅当前类       |
| 默认    | 同一包内的类   |

The get and set methods are used to read and modify private properties.	



##### Passing Objects to Methods

基本类型参数：传递值的副本，方法内修改不影响原变量；
引用类型参数：传递引用的副本，方法内修改对象的内容会影响原对象（引用指向同一对象）。



Array of Objects对象数组是存储对象引用的数组，数组元素本身是引用变量（默认值为 null），需手动为每个元素创建对象。



#####  Immutable Objects and Classes

不可变对象：创建后内容（数据字段）无法修改的对象；
不可变类：能创建不可变对象的类，需满足以下条件：
所有数据字段声明为 private；
无修改字段的 set 方法（mutator）；
访问器方法（get）不返回可变字段的引用（避免外部修改）。



##### Scope of Variables

实例变量与静态变量（类变量）：
作用域为整个类，可在类内任何位置声明（推荐在类开头）；
有默认值，无需显式初始化即可使用。
局部变量（方法内、代码块内）：
作用域从声明处开始，到包含它的代码块（大括号）结束；
无默认值，必须显式初始化后才能使用；
同名局部变量会隐藏类中的成员变量（需用 this 区分）。



##### The this Keyword 

this 关键字指代当前对象（调用方法或构造器的对象），核心用途：

访问被隐藏的数据字段（当方法参数名与字段一样）

```java
public class Circle {
  private double radius;
  
  // 参数名与字段名相同，用this区分
  public Circle(double radius) {
    this.radius = radius; // this.radius指当前对象的字段
  }
  
  public void setRadius(double radius) {
    this.radius = radius;
  }
```

调用类的重载构造器（必须是构造器的第一条语句）；

```java
public class Circle {
  private double radius;
  
  // 无参构造器
  public Circle() {
    this(1.0); // 调用带参构造器，初始化半径为1.0
  }
  
  // 带参构造器
  public Circle(double radius) {
    this.radius = radius;
  }
}
```



### Chatper10

![image-20251214000349146](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251214000349146.png)

##### Class Abstraction and Encapsulation

类抽象与封装

- 类抽象：将类的 “实现细节” 与 “使用方式” 分离 —— 类的创建者提供使用说明（方法、字段描述），使用者无需关心内部实现。
- 封装：将实现细节隐藏（私有字段），仅通过公开方法暴露接口，确保数据安全与代码可维护性。
- 示例：使用 Java 提供的 GUI 类时，无需知道按钮如何绘制，只需调用点击事件方法即可。



##### 类与类之间的关系

面向对象中类间核心关系：

1. 继承关系：is-a（如学生是人类）；
2. 实现关系：类实现接口（如 Dog 实现 Animal 接口）；
3. 依赖关系：类 A 使用类 B 的方法 / 字段（如测试类依赖 BMI 类）；
4. 关联关系：类间长期关联（如老师与学生）；
5. 聚合关系：has-a（松散依赖，如课程包含学生）；
6. 组合关系：强聚合（整体与部分不可分割，如汽车与发动机）。



##### Object Composition

聚合模型 “has-a” 关系（所属关系）：

- 聚合类（所有者）：如 Course（课程）；
- 被聚合类（被所有者）：如 Student（学生）、Faculty（教师）；
- 实现方式：聚合类将被聚合类作为数据字段。



##### Wrapper Classes

- 包装类是基本数据类型对应的对象类，用于将基本类型 “对象化”（如 int→Integer），支持泛型、集合等仅支持对象的场景。

- 8 个包装类对应关系：

  | 基本类型 | 包装类    |
  | -------- | --------- |
  | boolean  | Boolean   |
  | char     | Character |
  | byte     | Byte      |
  | short    | Short     |
  | int      | Integer   |
  | long     | Long      |
  | float    | Float     |
  | double   | Double    |

- 核心特点：

  1. 无无参构造器，需通过 “值” 或 “字符串” 创建实例（如`new Integer(10)`、`Integer.valueOf("10")`）；
  2. 实例不可变：创建后无法修改内部值（如`Integer i = 5; i = 10;`是重新指向新对象）。



##### Integer 与 Double 类

- The Integer and Double Classes
  - 构造器：`Integer(int value)`、`Integer(String s)`、`Double(double value)`、`Double(String s)`；
  - 类常量：MAX_VALUE（最大值）、MIN_VALUE（最小值）；
  - 转换方法：intValue ()、doubleValue () 等（转换为基本类型）。

- Integer 与 Double 类详解

  - 构造器（创建包装类实例）：

    ```java
    // Integer构造器
    Integer i1 = new Integer(10); // 通过int值创建
    Integer i2 = new Integer("10"); // 通过字符串创建（需为有效数字）
    
    // Double构造器
    Double d1 = new Double(3.14);
    Double d2 = new Double("3.14");
    ```

  - 类常量（获取基本类型的极值）

    ```java
    System.out.println(Integer.MAX_VALUE); // 输出2147483647（int最大值）
    System.out.println(Integer.MIN_VALUE); // 输出-2147483648（int最小值）
    System.out.println(Double.MAX_VALUE); // 输出1.7976931348623157E308（double最大值）
    ```

  - 转换方法（包装类→基本类型）：

    ```java
    Integer i = new Integer(10);
    int num = i.intValue(); // 转换为int类型
    
    Double d = new Double(3.14);
    double num2 = d.doubleValue(); // 转换为double类型
    ```



##### The Static valueOf Methods

- 静态方法，通过字符串或基本类型创建包装类实例（推荐使用，效率高于构造器）。

  ```java
  Double doubleObject = Double.valueOf("12.4");
  Integer integerObject = Integer.valueOf("12");
  Integer integerObject2 = Integer.valueOf(12);
  ```



##### The Methods for Parsing Strings into Numbers

- 静态 parseXxx 方法，将字符串转换为基本类型（无需创建包装类实例）。

  ```java
  int i = Integer.parseInt("12");
  double d = Double.parseDouble("12.4");
  ```



Automatic Conversion Between Primitive Types and Wrapper Class Types

- JDK 1.5 + 支持自动转换：
  - 自动装箱：基本类型→包装类（如`int→Integer`）；
  - 自动拆箱：包装类→基本类型（如`Integer→int`）。

```java
// 自动装箱：int→Integer
Integer i = 10; // 等价于Integer i = Integer.valueOf(10);

// 自动拆箱：Integer→int
int num = i; // 等价于int num = i.intValue();

// 数组中的自动装箱
Integer[] arr = {1, 2, 3}; // 每个元素均自动装箱

// 运算中的自动拆箱
int sum = arr[0] + arr[1]; // 自动拆箱后相加
System.out.println(sum); // 输出3
```



##### BigInteger and BigDecimal

- 用于处理超大整数（超出 long 范围）和高精度浮点数（避免 double 精度丢失）。

  ```java
  // BigInteger示例（超大整数乘法）
  BigInteger a = new BigInteger("9223372036854775807");
  BigInteger b = new BigInteger("2");
  BigInteger c = a.multiply(b); // 乘法（不可用*运算符）
  System.out.println(c); // 输出18446744073709551614
  
  // BigDecimal示例（高精度除法）
  BigDecimal a = new BigDecimal(1.0);
  BigDecimal b = new BigDecimal(3);
  BigDecimal c = a.divide(b, 20, BigDecimal.ROUND_UP); // 保留20位小数，向上取整
  System.out.println(c); // 输出0.33333333333333333334
  ```



##### String 类（不可变字符串）

- String 类用于表示不可变字符串（创建后内容无法修改），提供丰富的字符串操作方法。

- 构造器：

  ```java
  // 直接赋值（推荐，复用常量池中的对象）
  String s1 = "Welcome to Java";
  
  // 构造器创建（新创建对象，不复用常量池）
  String s2 = new String("Welcome to Java");
  
  // 空字符串
  String s3 = new String();
  ```

- 核心方法示例：

  ```java
  String s = "Welcome to Java";
  System.out.println(s.length()); // 输出15（长度）
  System.out.println(s.charAt(0)); // 输出'W'（取索引0的字符）
  System.out.println(s.concat("!!!")); // 输出"Welcome to Java!!!"（拼接）
  System.out.println(s.substring(8)); // 输出"to Java"（从索引8截取）
  System.out.println(s.equals("Welcome")); // 输出false（内容比较）
  System.out.println(s.indexOf("Java")); // 输出11（查找子串位置）
  char[] chars = s.toCharArray(); // 转为字符数组
  ```



##### Strings Are Immutable

- String 对象不可变，修改操作（如拼接）会生成新对象。

  ```java
  String s = "Java";
  s = "HTML"; // s重新指向新对象"HTML"，原"Java"对象未修改
  ```



##### **pool of literal string**

Since strings are immutable and are frequently used, to improve efficiency and save memory, the JVM uses a unique instance for string literals with the same character sequence. Such an instance is called interned.

- 为优化内存，JVM 将字符串字面量（如 "Java"）存入常量池，相同字符序列的字面量复用同一对象（称为 “interned 对象”）。

  ```java
  String s1 = "Java"; // s1指向常量池中的"Java"对象
  String s2 = "Java"; // s2复用常量池对象，与s1指向同一地址
  String s3 = new String("Java"); // s3创建新对象（堆内存），与常量池对象地址不同
  
  System.out.println(s1 == s2); // true（地址相同）
  System.out.println(s1 == s3); // false（地址不同）
  System.out.println(s1.equals(s3)); // true（内容相同）
  ```



##### Replacing and Splitting Strings

- 替换方法：replace ()（替换字符 / 子串）、replaceFirst ()（替换首个匹配）、replaceAll ()（替换所有匹配）；

- 分割方法：split ()（按分隔符分割为数组）；

  ```java
  // 替换
  System.out.println("Welcome".replace('e', 'A')); // 输出"WAlcomA"
  System.out.println("Welcome".replaceFirst("e", "AB")); // 输出"WABlcome"
  System.out.println("Welcome".replace("e", "AB")); // 输出"WABlcomAB"
  
  // 分割
  String[] tokens = "Java#HTML#Perl".split("#");
  for (String t : tokens) System.out.print(t + " "); // 输出"Java HTML Perl"
  ```



##### Matching, Replacing and Splitting by Patterns

- 正则表达式（Regular Expression）：描述字符串模式的语法，用于匹配、替换、分割字符串。

  ```java
  // 匹配
  System.out.println("Java".matches("Java")); // true
  System.out.println("Java is fun".matches("Java.*")); // true（.*匹配任意字符序列）
  
  // 替换（正则匹配$、+、#）
  String s = "a+b$#c".replaceAll("[$+#]", "NNN");
  System.out.println(s); // 输出"aNNNbNNNNNNc"
  
  // 分割（正则匹配标点符号）
  String[] tokens = "Java,C?C#,C++".split("[.,:;?]");
  for (String t : tokens) System.out.println(t); // 输出Java、C、C#、C++
  ```



##### Convert Character and Numbers to Strings

- 使用 String.valueOf () 静态方法，将基本类型、字符、字符数组转为字符串。

  ```java
  String s1 = String.valueOf(5.44); // "5.44"
  String s2 = String.valueOf(true); // "true"
  String s3 = String.valueOf('A'); // "A"
  char[] chars = {'J', 'a', 'v', 'a'};
  String s4 = String.valueOf(chars); // "Java"
  ```



##### StringBuilder and StringBuffer

- 可变字符串类，用于频繁修改字符串（如拼接、插入、删除），效率高于 String。
- 区别：StringBuffer 线程安全（方法带 synchronized），效率较低；StringBuilder 非线程安全，效率较高。
- 核心方法：append ()（拼接）、insert ()（插入）、delete ()（删除）、replace ()（替换）、reverse ()（反转）。

```java
StringBuilder sb = new StringBuilder("Welcome to Java");

sb.append("!!!"); // 拼接→"Welcome to Java!!!"
sb.insert(11, "HTML and "); // 插入→"Welcome to HTML and Java!!!"
sb.delete(8, 11); // 删除索引8-10→"Welcome HTML and Java!!!"
sb.replace(11, 15, "CSS"); // 替换→"Welcome HTML CSS Java!!!"
sb.reverse(); // 反转→"!!!avaJ SSC LMTH emocleW"

String result = sb.toString(); // 转为String
System.out.println(result);
```

###### 字符串类使用建议

1. 效率优先级：StringBuilder（单线程）> StringBuffer（多线程）> String（少量修改）；
2. 特殊情况：字符串字面量直接拼接（如`String s = "a" + "b" + "c"`），编译器会优化为`"abc"`，效率极高（无需创建 StringBuilder）；
3. 场景选择：
   - 少量修改 / 不修改：用 String（简单、线程安全）；
   - 单线程 + 频繁修改：用 StringBuilder（效率最高）；
   - 多线程 + 频繁修改：用 StringBuffer（线程安全）。

###### StringBuilder/StringBuffer 的常用补充方法：

```java
StringBuilder sb = new StringBuilder("Java");

String s = sb.toString(); // 转为String→"Java"
int cap = sb.capacity(); // 容量→16（默认）
int len = sb.length(); // 长度→4
sb.setLength(6); // 设置长度为6，不足部分补'\u0000'
char ch = sb.charAt(0); // 取索引0的字符→'J'
```



正则表达式语法（核心摘要）

| 正则表达式 | 匹配规则                   | 示例                                 |
| ---------- | -------------------------- | ------------------------------------ |
| X          | 指定字符 X                 | "Java" matches "Java" → true         |
| .          | 任意单个字符               | "Java" matches "J..a" → true         |
| (ab\|cd)   | ab 或 cd                   | "ten" matches "t(en\|im)" → true     |
| [abc]      | a、b、c 中的任意一个       | "Java" matches "Ja[uvwx]a" → true    |
| [^abc]     | 非 a、b、c 的任意字符      | "Java" matches "Ja[ars]a" → true     |
| [a-z]      | a-z 的任意小写字母         | "Java" matches "[A-M]av[a-d]" → true |
| \d         | 数字（等价于 [0-9]）       | "Java2" matches "Java\d" → true      |
| \s         | 空白字符（空格、制表符等） | "Java 2" matches "Java\s2" → true    |
| p*         | 零个或多个 p               | "aaaabb" matches "a*bb" → true       |
| p+         | 一个或多个 p               | "able" matches "(ab)+.*" → true      |
| p?         | 零个或一个 p               | "Java" matches "J?ava" → true        |
| p{n}       | 恰好 n 个 p                | "Java" matches "Ja{1}.*" → true      |
| p{n,}      | 至少 n 个 p                | "aaaa" matches "a{1,}" → true        |
| p{n,m}     | n 到 m 个 p（含）          | "aaaa" matches "a{1,9}" → true       |



### Chatper11

![image-20251214155222769](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251214155222769.png)

父类构造器是否被继承？
结论：父类构造器不被子类继承（构造器是类的专属初始化方法，子类无法复用）。
调用方式：
显式调用：子类构造器中通过super(参数)调用父类指定构造器（必须是构造器第一条语句）；
隐式调用：若子类构造器未显式调用super，JVM 自动添加super()，调用父类无参构造器。

父类构造器必被调用

- 规则：创建子类对象时，父类构造器必须先执行，沿继承链向上直至`Object`类，形成 “构造器链”。

- 示例

  ```java
  class A {
    public A() {
      // 隐式调用Object类的无参构造器
      System.out.println("A的无参构造器");
    }
  }
  class B extends A {
    public B() {
      // JVM自动添加super()，调用A的无参构造器
      System.out.println("B的无参构造器");
    }
  }
  // 创建B对象，输出：A的无参构造器 → B的无参构造器
  ```



##### super关键字的用途

1. 调用父类构造器：`super(参数)`，必须是子类构造器的第一条语句；
2. 调用父类方法：`super.方法名(参数)`，用于子类重写父类方法后，仍需调用父类原逻辑。



##### `super`调用父类构造器的规则

1. 必须使用`super`关键字调用父类构造器，直接写父类构造器名会编译报错；
2. `super(参数)`必须是子类构造器的**第一条语句**（不能在其他代码后调用）；
3. 若父类无无参构造器，子类必须显式调用父类带参构造器（否则编译报错）。



##### 方法重写（Override）

- 定义：子类定义与父类 “方法名、参数列表、返回值类型” 完全一致的方法，覆盖父类方法的实现。

  ```java
  public class Circle extends GeometricObject {
    private double radius;
    
    // 重写父类toString方法
    @Override // 注解：标记重写，编译时校验规则
    public String toString() {
      // 调用父类toString方法，追加子类特有信息
      return super.toString() + "\n半径：" + radius;
    }
  }
  ```

方法重写的注意事项

1. 私有方法不可重写：父类`private`方法子类无法访问，即使子类定义同名方法，也视为新增方法（非重写）；
2. 静态方法不可重写：子类定义与父类同名、同参数的静态方法，本质是 “隐藏父类方法”（通过子类名调用子类方法，父类名调用父类方法），而非重写（重写依赖动态绑定）；
3. 注解`@Override`：建议添加，编译时自动校验重写规则（如方法名、参数列表是否一致），避免误写。

方法重写（Override）与重载（Overload）的区别

| 维度     | 方法重写（Override）             | 方法重载（Overload）                           |
| -------- | -------------------------------- | ---------------------------------------------- |
| 适用场景 | 子类与父类之间                   | 同一类中（或子类与父类之间）                   |
| 核心要求 | 方法名、参数列表、返回值完全一致 | 方法名相同，参数列表（个数 / 类型 / 顺序）不同 |
| 访问权限 | 子类方法不能削弱父类方法权限     | 无限制                                         |
| 绑定时机 | 运行时绑定（动态绑定）           | 编译时绑定（静态绑定）                         |
| 核心目的 | 扩展父类方法逻辑                 | 实现同一功能的不同参数版本                     |



##### Object类与toString方法

Object类是 Java 所有类的根类：若类未显式声明父类，默认继承Object类。
toString()方法：
默认实现：返回getClass().getName() + "@" + Integer.toHexString(hashCode())（如Loan@15037e5），无实际意义；
重写建议：返回对象的核心属性信息，便于调试与打印。



##### Polymorphism

- 定义：父类引用可以指向子类对象（“向上转型”），实现 “一个接口，多种实现”。

- 核心优势：编写通用代码，适配所有子类对象（如方法参数为父类类型，可接收任意子类对象）。

- 示例

  ```java
  public class PolymorphismDemo {
    public static void main(String[] args) {
      // 父类Object引用指向不同子类对象（多态）
      m(new GraduateStudent()); // 输出"Student"（继承Student的toString）
      m(new Student()); // 输出"Student"
      m(new Person()); // 输出"Person"
      m(new Object()); // 输出"java.lang.Object@xxx"（默认toString）
    }
    // 方法参数为Object类型（父类），接收所有子类对象
    public static void m(Object x) {
      System.out.println(x.toString()); // 动态绑定：调用实际对象的toString
    }
  }
  ```



##### 动态绑定（Dynamic Binding）

- 定义：多态场景下，调用重写方法时，JVM 在**运行时**根据 “实际对象类型”（而非引用类型）执行对应子类的方法实现。
- 执行流程：
  1. 若对象是类`C1`的实例（`C1`是`C2`的子类，`C2`是`C3`的子类，...，`Cn`是`Object`）；
  2. 调用方法时，JVM 依次在`C1`→`C2`→...→`Object`中查找方法实现；
  3. 找到第一个匹配的实现后执行，停止查找。
- 示例：`Object x = new Student(); x.toString()` → 执行`Student`类的`toString`方法（而非`Object`类）。



##### Generic Programming

核心思想：利用多态，编写一套代码适配多种子类对象，减少冗余。
示例：方法参数为Object类型（所有类的父类），可接收任意对象；调用toString方法时，通过动态绑定执行对应子类的实现，实现 “一次编写，多类适配”。



##### Casting Objects

- 向上转型（自动转型，安全）：

  - 语法：`父类 引用变量 = 子类对象`；
  - 原理：子类是父类的 “特例”，所有子类对象都可视为父类对象；
  - 示例：`Person p = new Student();`（`Student`是`Person`的子类）。

- 向下转型（显式转型，需谨慎）：

  - 语法：`子类 引用变量 = (子类)父类引用`；

  - 前提：父类引用实际指向的是子类对象（否则抛`ClassCastException`）；

    ```java
    Object o = new Student(); // 向上转型
    Student s = (Student)o; // 向下转型（合法，o实际是Student对象）
    
    Object o2 = new Person();
    Student s2 = (Student)o2; // 非法，o2实际是Person对象，抛异常
    ```



##### `instanceof`

- 功能：判断一个对象是否为指定类（或其子类）的实例，避免向下转型时的类型转换异常。

- 语法：`对象 instanceof 类名` → 返回`boolean`值。

  ```java
  Object myObject = new Circle();
  // 先判断类型，再转型（安全）
  if (myObject instanceof Circle) {
    Circle circle = (Circle)myObject;
    System.out.println("圆的直径：" + circle.getDiameter());
  }
  ```

- 注意：若对象为`null`，`instanceof`返回`false`。



##### `equals`方法

- 核心用途：比较两个对象的 “内容是否相等”（区别于`==`比较引用地址）

- 子类重写

  ```java
  public class Circle extends GeometricObject {
    private double radius;
    
    @Override
    public boolean equals(Object o) {
      if (this == o) return true; // 引用相同，直接返回true
      if (o == null || getClass() != o.getClass()) return false; // 非Circle对象，返回false
      Circle circle = (Circle)o;
      return Math.abs(radius - circle.radius) < 1e-6; // 比较半径（允许浮点误差）
    }
  }
  ```

- 注意：重写`equals`时需遵循 “自反性、对称性、传递性”。

`==`与`equals`的核心区别

| 运算符 / 方法 | 适用场景           | 比较内容                         |
| ------------- | ------------------ | -------------------------------- |
| `==`          | 基本类型、对象引用 | 基本类型的值；对象的引用地址     |
| `equals`      | 对象之间           | 默认：引用地址；重写后：对象内容 |



##### `ArrayList`类（动态对象集合）

- 核心优势：大小动态扩容，无需提前指定长度，支持便捷的增删改查操作（替代数组存储对象）。

- 泛型语法：`ArrayList<元素类型> 集合名 = new ArrayList<>()`，指定集合存储的元素类型（类型安全）。

- 核心方法示例：

  ```java
  // 创建存储String的ArrayList
  ArrayList<String> cities = new ArrayList<>();
  
  // 添加元素（末尾/指定位置）
  cities.add("北京");
  cities.add(1, "上海"); // 插入到索引1位置
  
  // 获取元素（通过索引）
  String city = cities.get(0); // 获取索引0的元素（北京）
  
  // 删除元素（通过索引/对象）
  cities.remove(1); // 删除索引1的元素（上海）
  cities.remove("北京"); // 删除对象"北京"
  
  // 获取集合大小
  int size = cities.size(); // 0
  ```

###### `ArrayList`与数组的区别与联系

| 操作         | 数组                          | `ArrayList`                                  |
| ------------ | ----------------------------- | -------------------------------------------- |
| 创建方式     | `String[] a = new String[10]` | `ArrayList<String> list = new ArrayList<>()` |
| 访问元素     | `a[index]`                    | `list.get(index)`                            |
| 修改元素     | `a[index] = "值"`             | `list.set(index, "值")`                      |
| 获取长度     | `a.length`（属性）            | `list.size()`（方法）                        |
| 添加元素     | 需手动扩容复制                | `list.add("值")`（自动扩容）                 |
| 删除元素     | 需手动移动元素                | `list.remove(index)`（自动调整）             |
| 清空所有元素 | 需手动赋值`null`              | `list.clear()`                               |

###### `ArrayList`与数组互转

1.数组转为`ArrayList`：

```java
String[] array = {"红", "绿", "蓝"};
ArrayList<String> list = new ArrayList<>(Arrays.asList(array));
```

2.`ArrayList`转为数组：

```java
String[] newArray = new String[list.size()];
list.toArray(newArray); // 将list元素复制到newArray
```

###### `ArrayList`的常用操作

```java
ArrayList<String> list = new ArrayList<>(Arrays.asList("红", "绿", "蓝"));
String max = Collections.max(list); // 按自然顺序获取最大值（"蓝"）
String min = Collections.min(list); // 按自然顺序获取最小值（"红"）
```

```java
ArrayList<Integer> list = new ArrayList<>(Arrays.asList(3, 5, 95, 4));
Collections.shuffle(list); // 随机打乱元素顺序
System.out.println(list); // 输出示例：[5, 3, 4, 95]
```



##### 访问权限对比表：

| 修饰符      | 同一类 | 同一包 | 不同包子类 | 不同包非子类 |
| ----------- | ------ | ------ | ---------- | ------------ |
| `private`   | ✔️      | ❌      | ❌          | ❌            |
| 默认        | ✔️      | ✔️      | ❌          | ❌            |
| `protected` | ✔️      | ✔️      | ✔️          | ❌            |
| `public`    | ✔️      | ✔️      | ✔️          | ✔️            |



##### 子类重写方法的访问权限规则

- 核心规则：子类重写父类方法时，访问权限不能 “削弱” 父类方法的权限（可增强或保持一致）。
- 合法示例：父类`protected`方法 → 子类`public`方法；
- 非法示例：父类`public`方法 → 子类`protected`方法（编译报错）。
- 原因：多态场景下，父类引用调用方法时，需保证子类实现的访问权限不低于父类（否则可能出现 “父类可访问，子类不可访问” 的矛盾）。



#####  `final` Modifier

- 修饰类：类不可被继承（如`final class Math`）；
- 修饰方法：方法不可被重写；
- 修饰变量：变量为常量（值不可修改）。



### Chatper12

![image-20251214170803943](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251214170803943.png)



异常处理的优势：
方法可将异常抛给调用者，无需在方法内处理或强制终止程序；
错误处理代码与业务逻辑分离，程序更易读、易维护；
支持多级异常传播，调用链上的任意层级可处理异常。



##### Java 与 C++ 异常处理核心区别

| 特性           | Java                                      | C++                               |
| -------------- | ----------------------------------------- | --------------------------------- |
| 抛出类型       | 仅可抛出对象（异常类实例）                | 可抛出任意类型（int、string 等）  |
| 捕获机制       | 可捕获 Exception 统一处理，无 “catch all” | 有 “catch (...)” 捕获所有类型异常 |
| 最终执行块     | 有`finally`块，必执行                     | 无`finally`块                     |
| 异常分类       | 受检异常（checked）+ 非受检异常           | 所有异常均为非受检异常            |
| 声明异常关键字 | `throws`（方法头声明）                    | `throw`（函数声明）               |
| 易用性         | 异常查找与处理更简单                      | 异常查找与处理较复杂              |



##### Exception Types

![image-20251214195214162](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251214195214162.png)

- 异常继承体系：

  ```
  java.lang.Throwable
  ```

  是所有异常 / 错误的根类，核心子类：

  1. `Error`（系统错误）：JVM 或系统级错误，程序无法恢复，无需捕获（如 OutOfMemoryError、StackOverflowError）；

  2. ```
     Exception
     ```

     （异常）：程序或外部环境导致，可捕获处理：

     - 受检异常（checked）：编译器强制要求处理（声明或捕获），如 IOException（文件操作）、ClassNotFoundException（类未找到）；

     - 非受检异常（unchecked）：

       ```
       RuntimeException
       ```

       及其子类，源于编程逻辑错误，无需强制处理，如：

       - NullPointerException（空指针）、IndexOutOfBoundsException（数组越界）、ArithmeticException（除零）。

- 非受检异常的特点：

  - 通常是逻辑错误，应在编码阶段修正，而非依赖异常处理；
  - 无需大量`try-catch`块，避免代码冗余。



##### Declaring, Throwing, and Catching Exceptions

声明异常（方法级）：方法可能抛出的受检异常，需在方法头用`throws`声明，告知调用者。

```java
// 声明可能抛出IOException（受检异常）
public static void readFile(String filePath) throws IOException {
  FileReader fr = new FileReader(filePath);
  // ... 读文件操作
}
```

抛出异常（代码级）：检测到错误时，用`throw`创建异常对象并抛出。

```java
public void setRadius(double newRadius) {
  if (newRadius < 0) {
    // 抛出非法参数异常，带自定义信息
    throw new IllegalArgumentException("半径不能为负数：" + newRadius);
  }
  this.radius = newRadius;
}
```

捕获异常（调用级）：`try`块包裹可能抛出异常的代码，`catch`块匹配并处理异常。

```java
public static void main(String[] args) {
  try {
    setRadius(-5.0); // 可能抛出IllegalArgumentException
  } catch (IllegalArgumentException ex) {
    // 处理异常：打印异常信息
    System.out.println("错误：" + ex.getMessage());
    ex.printStackTrace(); // 打印异常堆栈信息（调试用）
  }
}
```



##### 受检异常处理原则：

若方法调用了声明受检异常的方法，必须要么用`try-catch`捕获，要么在当前方法头声明抛出该异常。

当你的方法 A 调用了一个**声明抛出受检异常**的方法 B 时，编译器会要求你：

要么在方法 A 里用`try-catch`捕获并处理这个异常；

要么在方法 A 的方法头用`throws`声明 “我不处理，抛给调用我的上层方法处理”。

###### 场景 1：用 try-catch 捕获处理（自己扛）

如果调用了抛受检异常的方法，且你想在当前方法内处理这个异常，就用`try-catch`包裹调用逻辑。

**示例**：`FileReader`的构造方法声明抛出`FileNotFoundException`（受检异常），在调用时捕获处理：

```java
import java.io.FileReader;
import java.io.FileNotFoundException;
import java.io.IOException;

public class ExceptionDemo {
    // 方法内部捕获异常，无需在方法头声明throws
    public static void readFile() {
        try {
            // 调用声明了受检异常的方法：FileReader构造方法
            FileReader fr = new FileReader("test.txt"); 
            fr.close();
        } catch (FileNotFoundException e) { // 捕获具体的受检异常
            // 异常处理逻辑（比如提示用户文件不存在）
            System.out.println("文件不存在，请检查路径：" + e.getMessage());
        } catch (IOException e) { // 捕获close()抛出的IOException
            System.out.println("文件关闭失败：" + e.getMessage());
        }
    }

    public static void main(String[] args) {
        readFile(); // 调用readFile，无需处理异常（因为readFile已经捕获了）
    }
}
```

###### 场景 2：方法头声明 throws（甩出去）

如果当前方法不想处理这个异常，想把异常 “甩” 给调用当前方法的上层方法处理，就必须在方法头用`throws`声明该异常。

**示例**：不捕获异常，而是声明抛出，把处理责任交给上层：

```java
import java.io.FileReader;
import java.io.FileNotFoundException;
import java.io.IOException;

public class ExceptionDemo {
    // 方法头声明抛出受检异常，自己不处理
    public static void readFile() throws FileNotFoundException, IOException {
        FileReader fr = new FileReader("test.txt"); // 调用抛受检异常的方法
        fr.close();
    }

    public static void main(String[] args) {
        // 调用readFile（声明了throws），必须处理异常（要么catch，要么main也throws）
        try {
            readFile();
        } catch (FileNotFoundException e) {
            System.out.println("文件不存在：" + e.getMessage());
        } catch (IOException e) {
            System.out.println("IO错误：" + e.getMessage());
        }
    }
}
```



##### Rethrowing Exceptions

场景：`catch`块处理部分逻辑（如日志记录）后，将异常重新抛出，让上层调用者处理。

```java
public static void processFile(String filePath) throws IOException {
  try {
    FileReader fr = new FileReader(filePath);
    // ... 读文件
  } catch (FileNotFoundException ex) {
    // 记录日志（部分处理）
    System.err.println("文件未找到：" + filePath);
    throw ex; // 重抛异常，让上层处理
  }
}
```



##### The finally Clause

`finally`块紧跟`try-catch`后，无论是否抛出异常，必执行（用于释放资源）；

执行流程追踪：无异常、有异常、异常重抛等场景下，`finally`均执行。

```java
try {
  // 可能抛出异常的代码
} catch (异常类型 ex) {
  // 异常处理
} finally {
  // 必执行代码（释放资源，如关闭文件、连接）
}
```

核心用途：释放资源（文件流、数据库连接等），避免资源泄露。



Rethrow the exception and control is transferred to the caller



思考：

When should you use the try-catch block in the code? You should use it to deal with unexpected error conditions. Do not use it to deal with simple, expected situations. For example, the following code.

```java
// 不推荐：用异常处理空指针
try {
  System.out.println(refVar.toString());
} catch (NullPointerException ex) {
  System.out.println("refVar为空");
}

// 推荐：直接判断
if (refVar != null) {
  System.out.println(refVar.toString());
} else {
  System.out.println("refVar为空");
}
```



##### Defining Custom Exception Classes

定义自定义异常

Use the exception classes in the API whenever possible.Define custom exception classes if the predefined classes are not sufficient.Define custom exception classes by extending Exception or a subclass of Exception.

- 示例（自定义非法半径异常）：

  ```java
  // 自定义受检异常（继承Exception）
  public class InvalidRadiusException extends Exception {
    // 无参构造器
    public InvalidRadiusException() {
      super();
    }
  
    // 带异常信息的构造器
    public InvalidRadiusException(String message) {
      super(message);
    }
  
    // 带信息和原始异常的构造器（链式异常）
    public InvalidRadiusException(String message, Throwable cause) {
      super(message, cause);
    }
  }
  ```

- 使用自定义异常：

  ```java
  public void setRadius(double newRadius) throws InvalidRadiusException {
    if (newRadius < 0) {
      throw new InvalidRadiusException("非法半径：" + newRadius);
    }
    this.radius = newRadius;
  }
  
  // 调用者处理
  public static void main(String[] args) {
    Circle circle = new Circle();
    try {
      circle.setRadius(-3.0);
    } catch (InvalidRadiusException ex) {
      System.out.println("异常：" + ex.getMessage());
    }
  }
  ```



##### Assertions

语法：`assert 布尔表达式;` 或 `assert 布尔表达式 : 详细信息;`；

作用：程序内部正确性校验，默认禁用，运行时用`-ea`启用；

场景：替代假设条件，如`switch`的`default`分支校验。

定义：用于程序内部正确性校验的语句，假设布尔表达式为`true`，若为`false`则抛出`AssertionError`。

```java
// 基本形式：布尔表达式为false时抛出异常
assert i == 10;

// 带详细信息：异常信息包含表达式结果
assert sum > 0 : "总和不能为负：" + sum;
```

启用断言：默认禁用，运行时用

```
java -ea 类名
```

启用（-ea）

```bash
javac AssertionDemo.java
java -ea AssertionDemo
```

示例：

```java
public class AssertionDemo {
  public static void main(String[] args) {
    int sum = 0;
    for (int i = 0; i < 10; i++) {
      sum += i;
    }
    assert sum == 45 : "1-9求和应为45，实际为：" + sum;
    System.out.println("求和正确：" + sum);
  }
}
```

断言与异常的区别：

- 断言：用于程序内部逻辑校验，开发 / 测试阶段启用，生产环境禁用；
- 异常：用于处理运行时错误，生产环境必须生效。



##### The File Class

The filename is a string. The File class is a wrapper class for the file name and its directory path. 

- 功能：封装文件或目录的路径，操作其属性（存在性、类型、权限等），不处理文件内容读写。

- 核心构造器：

  ```java
  // 1. 路径字符串创建
  File file1 = new File("test.txt"); // 相对路径
  File file2 = new File("C:/book/test.txt"); // 绝对路径（Windows）
  File file3 = new File("/home/user/test.txt"); // 绝对路径（Linux/Mac）
  
  // 2. 父目录+子路径创建
  File parent = new File("C:/book");
  File file4 = new File(parent, "test.txt");
  ```

- 核心方法示例：

  ```java
  File file = new File("test.txt");
  System.out.println("是否存在：" + file.exists());
  System.out.println("是否为文件：" + file.isFile());
  System.out.println("是否为目录：" + file.isDirectory());
  System.out.println("绝对路径：" + file.getAbsolutePath());
  System.out.println("文件大小（字节）：" + file.length());
  System.out.println("最后修改时间：" + new Date(file.lastModified()));
  
  // 创建目录（多级目录用mkdirs()）
  File dir = new File("C:/book/chapter12");
  dir.mkdirs(); // 创建多级目录
  
  // 删除文件/目录（目录必须为空）
  file.delete();
  dir.delete();
  ```



实践：获取文件属性（跨平台）

- 程序名：TestFileClass

- 功能：获取文件的核心属性，兼容 Windows 和 Linux/Mac。

  ```java
  import java.io.File;
  import java.util.Date;
  
  public class TestFileClass {
    public static void main(String[] args) {
      // 相对路径：当前目录下的image/us.gif
      File file = new File("./image/us.gif");
      System.out.println("是否存在？" + file.exists());
      System.out.println("是否可读？" + file.canRead());
      System.out.println("是否可写？" + file.canWrite());
      System.out.println("是否为目录？" + file.isDirectory());
      System.out.println("是否为文件？" + file.isFile());
      System.out.println("是否为绝对路径？" + file.isAbsolute());
      System.out.println("是否隐藏？" + file.isHidden());
      System.out.println("绝对路径：" + file.getAbsolutePath());
      try {
        System.out.println("规范路径：" + file.getCanonicalPath()); // 去除冗余路径
      } catch (Exception e) {
        e.printStackTrace();
      }
      System.out.println("文件名：" + file.getName());
      System.out.println("路径：" + file.getPath());
      System.out.println("最后修改时间：" + new Date(file.lastModified()));
      System.out.println("路径分隔符：" + File.pathSeparator);
      System.out.println("名称分隔符：" + File.separator);
    }
  }
  ```



##### Text I/O

写文件（`PrintWriter`）

import java.io.PrintWriter;

- 核心工具：`PrintWriter`类，用于向文件写入字符串、数值等文本数据，支持自动刷新。

- 基本用法（手动关闭资源）：

  ```java
  import java.io.PrintWriter;
  import java.io.FileNotFoundException;
  
  public class WriteData {
    public static void main(String[] args) {
      PrintWriter out = null;
      try {
        // 创建PrintWriter对象，指定文件路径
        out = new PrintWriter("scores.txt");
        // 写数据（字符串、数值、换行）
        out.println("张三");
        out.println(95);
        out.println("李四");
        out.println(88);
        System.out.println("文件写入成功！");
      } catch (FileNotFoundException ex) {
        System.out.println("文件未找到：" + ex.getMessage());
      } finally {
        // 关闭资源（必执行）
        if (out != null) {
          out.close();
        }
      }
    }
  }
  ```

- try-with-resources试用资源（自动关闭资源，JDK7+）：

  ```java
  public class WriteDataWithAutoClose {
    public static void main(String[] args) {
      // 资源声明在try括号内，自动关闭，无需finally
      try (PrintWriter out = new PrintWriter("scores.txt")) {
        out.println("张三");
        out.println(95);
      } catch (FileNotFoundException ex) {
        System.out.println("文件未找到：" + ex.getMessage());
      }
    }
  }
  ```



读文件（`Scanner`）

import java.util.Scanner;

核心工具：`Scanner`类，从文件读取文本、数值数据，支持按分隔符拆分。

代码示例

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class ReadData {
  public static void main(String[] args) {
    try (Scanner in = new Scanner(new File("scores.txt"))) {
      // 循环读取文件内容
      while (in.hasNext()) {
        String name = in.next(); // 读字符串（空格/换行分隔）
        int score = in.nextInt(); // 读整数
        System.out.println("姓名：" + name + "，分数：" + score);
      }
    } catch (FileNotFoundException ex) {
      System.out.println("文件未找到：" + ex.getMessage());
    }
  }
}
```

输出结果

```plaintext
姓名：张三，分数：95
姓名：李四，分数：88
```

|      方法分类      | 方法签名                                   | 功能说明                                              | 适用场景                         | 注意事项                                                     |                     |
| :----------------: | ------------------------------------------ | ----------------------------------------------------- | -------------------------------- | ------------------------------------------------------------ | ------------------- |
| **文件读取初始化** | `Scanner(File source)`                     | 通过 File 对象创建 Scanner，读取文件内容              | 读取本地文件（路径 / File 对象） | 需处理`FileNotFoundException`；默认分隔符为空白符（空格、换行、制表符等） |                     |
|                    | `Scanner(File source, String charsetName)` | 指定字符编码读取文件（如 UTF-8、GBK）                 | 非默认编码文件读取               | 需处理`FileNotFoundException`和`UnsupportedEncodingException` |                     |
|                    | `Scanner(Path source)`                     | 通过 Path 对象（NIO）创建 Scanner，读取文件           | NIO 风格文件读取                 | Java 7 + 支持；需处理`IOException`                           |                     |
|                    | `Scanner(InputStream source)`              | 通过输入流读取文件（如 FileInputStream）              | 流方式文件读取                   | 流需手动关闭；默认编码由系统决定                             |                     |
|   **分隔符设置**   | `useDelimiter(String pattern)`             | 设置自定义分隔符（支持正则表达式）                    | 按指定字符 / 规则拆分数据        | 分隔符是正则（如`","`拆分 CSV，`"\                           | "` 拆分竖线分隔符） |
|                    | `useDelimiter(Pattern pattern)`            | 通过 Pattern 对象设置分隔符（更灵活的正则）           | 复杂分隔规则（如多字符分隔）     | 需导入`java.util.regex.Pattern`                              |                     |
|                    | `delimiter()`                              | 获取当前使用的分隔符 Pattern 对象                     | 验证 / 调试分隔符设置            | 返回值为 Pattern，需通过`pattern()`转字符串                  |                     |
|  **文本数据读取**  | `next()`                                   | 读取下一个分隔符分隔的字符串（不包含分隔符）          | 读取单个文本字段                 | 无数据时抛`NoSuchElementException`，建议先调用`hasNext()`判断 |                     |
|                    | `nextLine()`                               | 读取整行文本（忽略分隔符，直到换行符）                | 读取整行内容                     | 若先调用`nextInt()`等数值方法，需注意换行符残留问题          |                     |
|                    | `next(String pattern)`                     | 读取匹配指定正则的字符串                              | 精准匹配文本（如手机号）         | 不匹配时抛`InputMismatchException`                           |                     |
|  **数值数据读取**  | `nextInt()`                                | 读取下一个 int 类型数值                               | 读取整数                         | 非数值时抛`InputMismatchException`，需先判断`hasNextInt()`   |                     |
|                    | `nextLong()`                               | 读取下一个 long 类型数值                              | 读取长整数                       | 同上，需先判断`hasNextLong()`                                |                     |
|                    | `nextFloat()`                              | 读取下一个 float 类型数值                             | 读取单精度浮点数                 | 同上，需先判断`hasNextFloat()`                               |                     |
|                    | `nextDouble()`                             | 读取下一个 double 类型数值                            | 读取双精度浮点数                 | 同上，需先判断`hasNextDouble()`                              |                     |
|                    | `nextBigDecimal()`                         | 读取 BigDecimal 类型数值（高精度）                    | 金融 / 高精度数值读取            | Java 5 + 支持，需先判断`hasNextBigDecimal()`                 |                     |
|   **存在性判断**   | `hasNext()`                                | 判断是否还有下一个分隔符分隔的元素（文本 / 数值通用） | 循环读取前的非空判断             | 配合`next()`使用，避免异常                                   |                     |
|                    | `hasNextInt()`/`hasNextDouble()`等         | 判断下一个元素是否为对应数值类型                      | 数值读取前的类型校验             | 精准匹配数值类型，避免类型不匹配异常                         |                     |
|                    | `hasNext(String pattern)`                  | 判断下一个元素是否匹配指定正则                        | 文本读取前的规则校验             |                                                              |                     |
|    **资源关闭**    | `close()`                                  | 关闭 Scanner，释放文件资源                            | 读取完成后必须调用               | 未关闭可能导致文件句柄泄漏；实现`AutoCloseable`，可配合 try-with-resources |                     |



##### Reading Data from the Web

通过URL类创建网络地址对象，用openStream()获取输入流，结合Scanner读取网页内容。

```java
import java.net.URL;
import java.util.Scanner;

public class ReadFileFromURL {
  public static void main(String[] args) {
    try {
      // 创建URL对象（百度首页）
      URL url = new URL("https://www.baidu.com");
      // 打开输入流，创建Scanner读取
      try (Scanner in = new Scanner(url.openStream())) {
        // 逐行读取网页内容并打印
        while (in.hasNextLine()) {
          String line = in.nextLine();
          System.out.println(line);
        }
      }
    } catch (Exception ex) {
      ex.printStackTrace();
    }
  }
}
```



### Chatper13

![image-20251214205724320](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251214205724320.png)

##### 抽象类的核心特性与规则

1. 抽象方法必须在抽象类中：非抽象类不能包含抽象方法；
2. 抽象类不能实例化( instantiated)：`GeometricObject geo = new GeometricObject();`（编译报错），但可声明引用变量（`GeometricObject geo = new Circle(5.0);`）；
3. 无抽象方法的抽象类：仅禁止实例化，作为专门的父类（如限制子类类型）；
4. 抽象类的父类可为具体类：如`GeometricObject`继承自具体类`Object`；
5. 具体方法重写为抽象方法：子类需用`abstract`修饰，且子类必须为抽象类（罕见，用于失效父类方法实现）；
6. 抽象类作为数据类型：支持声明数组或引用，体现多态，如：

```java
GeometricObject[] geoArray = new GeometricObject[2];
geoArray[0] = new Circle(3.0);
geoArray[1] = new Rectangle(2.0, 3.0);
```



##### interface

An interface is a classlike construct that contains only **constants and abstract methods**. In many ways, an interface is similar to an abstract class, but the intent of an interface is to specify common behavior for objects. For example, you can specify that the objects are comparable, edible, cloneable using appropriate interfaces. 

定义：接口是跨类的行为规范，仅含`public static final`常量和`public abstract`方法（JDK8 前），用`interface`修饰。

核心语法（接口定义）：

```java
public interface Edible {
  // 抽象方法（默认public abstract，可省略）
  String howToEat();
  
  // 常量（默认public static final，可省略）
  int MAX_CALORIE = 1000;
}
```

接口的特性：

1. 无构造器，不能实例化；
2. 方法和常量的修饰符可省略（默认规则）；
3. 一个类可实现多个接口（`class A implements B, C`）。



##### The Comparable Interface

- `java.lang.Comparable`接口：定义对象的自然排序，含`compareTo(E o)`方法；
- 实现该接口的类（如`Integer`、`String`、`Date`）可通过`Arrays.sort()`排序；
- 自定义类实现`Comparable`，重写`compareTo`方法定义排序规则。

- 接口定义：

  ```java
  public interface Comparable<E> {
    // 返回值：负整数（当前对象小）、0（相等）、正整数（当前对象大）
    int compareTo(E o);
  }
  ```

- 系统类实现示例：

  ```java
  // Integer类实现Comparable，按数值大小排序
  System.out.println(new Integer(3).compareTo(new Integer(5)); // 输出-1（3<5）
  
  // String类实现Comparable，按Unicode值排序
  System.out.println("ABC".compareTo("ABE")); // 输出-2（'C' < 'E'）
  
  // Date类实现Comparable，按时间先后排序
  java.util.Date date1 = new java.util.Date(2025, 1, 1);
  java.util.Date date2 = new java.util.Date(2024, 1, 1);
  System.out.println(date1.compareTo(date2)); // 输出1（date1更新）
  ```

- 自定义类实现示例

  ```
  ComparableRectangle
  ```

  ```java
  public class ComparableRectangle extends Rectangle implements Comparable<ComparableRectangle> {
    public ComparableRectangle(double width, double height) {
      super(width, height);
    }
  
    @Override
    public int compareTo(ComparableRectangle o) {
      double area1 = getArea();
      double area2 = o.getArea();
      if (area1 < area2) return -1;
      else if (area1 == area2) return 0;
      else return 1;
    }
  }
  
  // 测试排序
  public class SortRectangles {
    public static void main(String[] args) {
      ComparableRectangle[] rects = {
        new ComparableRectangle(3, 4),
        new ComparableRectangle(1, 2),
        new ComparableRectangle(5, 5)
      };
      java.util.Arrays.sort(rects); // 按面积排序
      for (var rect : rects) {
        System.out.println("面积：" + rect.getArea());
      }
    }
  }
  ```



Each wrapper class overrides the **toString, equals, and hashCode methods** defined in the Object class. Since all the numeric wrapper classes and the Character class implement the Comparable interface, the compareTo method is implemented in these classes. 



The java.util.Arrays.sort(array) method requires that the elements in an array are instances of Comparable<E>. 



需要自然排序的核心类才会实现 Comparable，典型例子包括：
基本类型包装类：Integer、Long、Double、Character、Boolean 等；
字符串类：String；
日期 / 时间类：LocalDate、LocalTime、Date、Calendar 等；
数值相关类：BigInteger、BigDecimal。



##### The Cloneable Interfaces

- 标记接口（Marker Interface）：空接口，无方法，仅标记类可克隆，（可以用来标记，只要对象实现这个接口，再作为参数传给方法，只有实现这个接口的对象才能被正确这个方法）
- 实现`Cloneable`接口后，需**重写`Object`类的`clone()`方法**；
- 克隆类型：浅拷贝（复制对象引用）、深拷贝（复制对象及引用的对象）。

- 功能：标记类的对象可克隆，需结合`clone()`方法实现拷贝。

- 核心特性：

  1. 标记接口：无抽象方法，仅作为 “可克隆” 的标识；
  2. 需重写`Object`类的`clone()`方法（默认浅拷贝）；
  3. 克隆异常：`clone()`方法抛出`CloneNotSupportedException`（需捕获或声明）。

- 浅拷贝示例（复制对象，引用字段仍指向原对象）：

  ```java
  public class House implements Cloneable {
    private int id;
    private double area;
    private java.util.Date whenBuilt;
  
    public House(int id, double area) {
      this.id = id;
      this.area = area;
      this.whenBuilt = new java.util.Date();
    }
  
    // 浅拷贝（默认克隆实现）
    @Override
    public Object clone() throws CloneNotSupportedException {
      return super.clone();
    }
  }
  ```

- 深拷贝示例（复制对象及引用的Date对象）

  ```java
  @Override
  public Object clone() throws CloneNotSupportedException {
    // 先执行浅拷贝
    House clone = (House) super.clone();
    // 复制引用字段（深拷贝）
    clone.whenBuilt = (java.util.Date) this.whenBuilt.clone();
    return clone;
  }
  ```

  测试克隆：

  ```java
  public class TestClone {
    public static void main(String[] args) throws CloneNotSupportedException {
      House house1 = new House(1, 1750.50);
      House house2 = (House) house1.clone();
  
      System.out.println(house1 == house2); // false（不同对象）
      System.out.println(house1.equals(house2)); // true（内容相同）
    }
  }
  ```

浅拷贝 vs 深拷贝 核心对比（Shallow vs. Deep Copy）

| 维度         | 浅拷贝                            | 深拷贝                       |
| ------------ | --------------------------------- | ---------------------------- |
| 基本类型成员 | 复制值（独立）                    | 复制值（独立）               |
| 引用类型成员 | 复制引用（共享对象）              | 复制对象（创建新实例，独立） |
| 内存开销     | 小（仅复制引用）                  | 大（复制所有引用对象）       |
| 实现复杂度   | 简单（仅重写 clone）              | 复杂（需递归克隆 / 序列化）  |
| 数据独立性   | 弱（引用成员共享，易冲突）        | 强（完全独立，无冲突）       |
| 适用场景     | 无引用类型成员 / 无需独立引用对象 | 需完全独立的对象（如多线程   |



##### Interfaces vs. Abstract Classes

- 数据字段：抽象类无限制；接口仅`public static final`常量；
- 方法：抽象类可含抽象 / 具体方法；接口仅抽象方法（JDK8 前）；
- 构造器：抽象类有构造器；接口无；
- 继承：抽象类单继承；接口多实现；
- 关系：抽象类 “is-a”；接口 “has-a”。



A property that is shared by all the instances of the class should be declared as a static property. 



### Chatper15

![image-20251215154724548](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251215154724548.png)

event-driven programming（事件驱动编程）

##### Procedural vs. Event-Driven Programming

Procedural programming: executed in procedural order.
Event-driven programming: code is executed upon activation of events.



##### GUI 事件处理核心模型

- 三大组件关系：
  1. 事件源（Event Source）：产生事件的 GUI 组件（如按钮、文本框）；
  2. 事件（Event）：用户操作触发的信号（如点击事件`ActionEvent`、鼠标事件`MouseEvent`）；
  3. 事件处理器（Event Handler）：实现`EventHandler`接口的对象，通过`handle`方法响应事件。
- 核心流程：
  1. 为事件源注册处理器（如`button.setOnAction(handler)`）；
  2. 用户操作事件源，产生事件对象；
  3. JVM 自动调用处理器的`handle`方法，传入事件对象，执行响应逻辑。



##### Event Classes

![image-20251215160209851](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251215160209851.png)

事件对象的核心方法：

- `getSource()`：获取产生事件的事件源对象；
- 子类特有方法：如`MouseEvent.getX()`获取鼠标 X 坐标，`KeyEvent.getCode()`获取按键代码。

- Selected User Actions and Handlers

| 用户操作                | 事件源      | 事件类型    | 注册方法                                     |
| ----------------------- | ----------- | ----------- | -------------------------------------------- |
| 点击按钮                | Button      | ActionEvent | setOnAction(EventHandler<ActionEvent>)       |
| 文本框按回车            | TextField   | ActionEvent | setOnAction(EventHandler<ActionEvent>)       |
| 勾选 / 取消勾选单选按钮 | RadioButton | ActionEvent | setOnAction(EventHandler<ActionEvent>)       |
| 勾选 / 取消勾选复选框   | CheckBox    | ActionEvent | setOnAction(EventHandler<ActionEvent>)       |
| 选择下拉框选项          | ComboBox    | ActionEvent | setOnAction(EventHandler<ActionEvent>)       |
| 鼠标按下                | Node/Scene  | MouseEvent  | setOnMousePressed(EventHandler<MouseEvent>)  |
| 鼠标释放                | Node/Scene  | MouseEvent  | setOnMouseReleased(EventHandler<MouseEvent>) |
| 鼠标点击                | Node/Scene  | MouseEvent  | setOnMouseClicked(EventHandler<MouseEvent>)  |
| 鼠标进入组件            | Node/Scene  | MouseEvent  | setOnMouseEntered(EventHandler<MouseEvent>)  |
| 鼠标退出组件            | Node/Scene  | MouseEvent  | setOnMouseExited(EventHandler<MouseEvent>)   |
| 鼠标移动                | Node/Scene  | MouseEvent  | setOnMouseMoved(EventHandler<MouseEvent>)    |
| 鼠标拖拽                | Node/Scene  | MouseEvent  | setOnMouseDragged(EventHandler<MouseEvent>)  |
| 按键按下                | Node/Scene  | KeyEvent    | setOnKeyPressed(EventHandler<KeyEvent>)      |
| 按键释放                | Node/Scene  | KeyEvent    | setOnKeyReleased(EventHandler<KeyEvent>)     |
| 按键输入字符            | Node/Scene  | KeyEvent    | setOnKeyTyped(Event                          |



An inner class can be declared static. A static inner class can be accessed using the outer class name. A static inner class cannot access nonstatic members of the outer class



##### Inner Class Listeners

内部类事件处理器

- 定义：在 GUI 主类内部定义的事件处理器类，是外部类的成员。

- 核心优势：直接访问外部类的非私有属性和方法（如圆形对象`circle`），简化代码

  ```java
  public class ControlCircle extends Application {
    private Circle circle = new Circle(50);
  
    @Override
    public void start(Stage primaryStage) {
      // 内部类：放大处理器
      class EnlargeHandler implements EventHandler<ActionEvent> {
        @Override
        public void handle(ActionEvent e) {
          circle.setRadius(circle.getRadius() + 10);
        }
      }
  
      // 内部类：缩小处理器
      private class ShrinkHandler implements EventHandler<ActionEvent> {
        @Override
        public void handle(ActionEvent e) {
          if (circle.getRadius() > 10) {
            circle.setRadius(circle.getRadius() - 10);
          }
        }
      }
  
      // 注册处理器
      Button btEnlarge = new Button("Enlarge");
      Button btShrink = new Button("Shrink");
      btEnlarge.setOnAction(new EnlargeHandler());
      btShrink.setOnAction(new ShrinkHandler());
  
      // 布局与显示（省略，同前）
    }
  }
  ```



##### Anonymous Inner Classes Listeners

- 无类名，直接通过`new 接口名() { 实现方法 }`创建对象；
- 必须实现接口的所有抽象方法；
- 编译后生成`外部类名$n.class`（n 为匿名类序号）。

- 匿名内部类事件处理器

  ```java
  事件源.setOnXxx(new 事件接口() {
    @Override
    public void handle(事件类型 e) {
      // 处理逻辑
    }
  });
  ```

  示例（简化ControlCircle的按钮处理器）：

  ```java
  @Override
  public void start(Stage primaryStage) {
    // 圆形面板（省略）
  
    Button btEnlarge = new Button("Enlarge");
    Button btShrink = new Button("Shrink");
  
    // 匿名内部类：放大处理器
    btEnlarge.setOnAction(new EventHandler<ActionEvent>() {
      @Override
      public void handle(ActionEvent e) {
        circle.setRadius(circle.getRadius() + 10);
      }
    });
  
    // 匿名内部类：缩小处理器
    btShrink.setOnAction(new EventHandler<ActionEvent>() {
      @Override
      public void handle(ActionEvent e) {
        if (circle.getRadius() > 10) {
          circle.setRadius(circle.getRadius() - 10);
        }
      }
    });
  
    // 布局与显示（省略）
  }
  ```

  优势：无需定义独立类，代码更简洁；

  注意：匿名内部类不能重复使用，仅适用于单一场景。



##### Simplifying Event Handling Using Lambda Expressions

Lambda expression is a new feature in Java 8. Lambda expressions can be viewed as an anonymous method with a concise syntax.

Lambda 表达式简化事件处理

- 核心前提：`EventHandler<T>`是单一抽象方法接口（SAM），仅含`handle(T e)`方法，可被 Lambda 表达式简化。

- 语法规则：

  1. 无参数：`() -> 逻辑`；
  2. 单参数：可省略括号，`e -> 逻辑`；
  3. 多参数：`(e1, e2) -> 逻辑`；
  4. 逻辑多行：需用大括号和 return，`(e) -> { 逻辑1; 逻辑2; return 值; }`。

- 示例（用 Lambda 简化ControlCircle）：

  ```java
  @Override
  public void start(Stage primaryStage) {
    // 圆形面板（省略）
  
    Button btEnlarge = new Button("Enlarge");
    Button btShrink = new Button("Shrink");
  
    // Lambda表达式：放大处理器
    btEnlarge.setOnAction(e -> circle.setRadius(circle.getRadius() + 10));
  
    // Lambda表达式：缩小处理器（多行逻辑）
    btShrink.setOnAction(e -> {
      if (circle.getRadius() > 10) {
        circle.setRadius(circle.getRadius() - 10);
      }
    });
  
    // 布局与显示（省略）
  }
  ```



##### Java 内置函数式接口（SAM 接口）

| 接口类型            | 核心方法                 | 用途                                |
| ------------------- | ------------------------ | ----------------------------------- |
| `Function<T,R>`     | `R apply(T t)`           | 输入 T 类型参数，返回 R 类型结果    |
| `BiFunction<T,U,R>` | `R apply(T t, U u)`      | 输入 T、U 类型参数，返回 R 类型结果 |
| `Supplier<T>`       | `T get()`                | 无参数，返回 T 类型结果             |
| `Consumer<T>`       | `void accept(T t)`       | 输入 T 类型参数，无返回值           |
| `BiConsumer<T,U>`   | `void accept(T t, U u)`  | 输入 T、U 类型参数，无返回值        |
| `Predicate<T>`      | `boolean test(T t)`      | 输入 T 类型参数，返回布尔值         |
| `BiPredicate<T,U>`  | `boolean test(T t, U u)` | 输入 T、U 类型参数，返回布尔值      |

说明：`EventHandler<T>`本质是`Consumer<T>`的特例，专注于事件处理。



##### 鼠标事件处理（MouseEvent）

- 常见鼠标事件类型：点击（CLICKED）、按下（PRESSED）、释放（RELEASED）、移动（MOVED）、拖拽（DRAGGED）、进入组件（ENTERED）、退出组件（EXITED）。

- 核心方法（MouseEvent类）：

  - `getX()`/`getY()`：获取鼠标在事件源组件内的坐标；
  - `getSceneX()`/`getSceneY()`：获取鼠标在场景（Scene）中的坐标；
  - `getClickCount()`：获取鼠标点击次数（1 = 单击，2 = 双击）；
  - `getButton()`：获取点击的鼠标按键（LEFT/RIGHT/MIDDLE）；
  - `isShiftDown()`/`isControlDown()`：判断是否按住 Shift/Control 键。

- 示例（鼠标点击绘制圆形）：

  ```java
  import javafx.application.Application;
  import javafx.scene.Scene;
  import javafx.scene.layout.Pane;
  import javafx.scene.shape.Circle;
  import javafx.stage.Stage;
  import javafx.scene.input.MouseEvent;
  
  public class MouseEventDemo extends Application {
    @Override
    public void start(Stage primaryStage) {
      Pane pane = new Pane();
      Scene scene = new Scene(pane, 400, 300);
  
      // 鼠标点击事件：在点击位置绘制圆形
      pane.setOnMouseClicked(e -> {
        Circle circle = new Circle(e.getX(), e.getY(), 10);
        pane.getChildren().add(circle);
      });
  
      primaryStage.setTitle("MouseEventDemo");
      primaryStage.setScene(scene);
      primaryStage.show();
    }
  
    public static void main(String[] args) {
      launch(args);
    }
  }
  ```



##### 键盘事件处理（KeyEvent）

- 常见键盘事件类型：按键按下（KEY_PRESSED）、按键释放（KEY_RELEASED）、输入字符（KEY_TYPED）。

- 核心方法（KeyEvent类）：

  - `getCode()`：返回按键代码（如`KeyCode.UP`、`KeyCode.A`）；
  - `getCharacter()`：返回输入的字符（仅 KEY_TYPED 事件有效）；
  - `getText()`：返回按键的文本描述；
  - `isShiftDown()`/`isControlDown()`：判断是否按住辅助键。

- 示例（方向键控制圆形移动）：

  ```java
  import javafx.application.Application;
  import javafx.scene.Scene;
  import javafx.scene.layout.Pane;
  import javafx.scene.shape.Circle;
  import javafx.stage.Stage;
  import javafx.scene.input.KeyEvent;
  
  public class KeyEventDemo extends Application {
    private Circle circle = new Circle(200, 150, 20);
  
    @Override
    public void start(Stage primaryStage) {
      Pane pane = new Pane(circle);
      Scene scene = new Scene(pane, 400, 300);
  
      // 键盘按下事件：方向键移动圆形
      scene.setOnKeyPressed(e -> {
        double dx = 0, dy = 0;
        switch (e.getCode()) {
          case UP: dy = -5; break;
          case DOWN: dy = 5; break;
          case LEFT: dx = -5; break;
          case RIGHT: dx = 5; break;
        }
        circle.setCenterX(circle.getCenterX() + dx);
        circle.setCenterY(circle.getCenterY() + dy);
      });
  
      primaryStage.setTitle("KeyEventDemo");
      primaryStage.setScene(scene);
      primaryStage.show();
    }
  
    public static void main(String[] args) {
      launch(args);
    }
  }
  ```



##### Listeners for Observable Objects

- Observable 对象属性变更监听

  - 核心概念：Observable 对象的属性（如圆形的半径、位置）变更时，通知注册的监听器。

  - 实现步骤：

    1. 获取 Observable 属性（如`circle.radiusProperty()`）；
    2. 调用`addListener`方法注册`InvalidationListener`；
    3. 在`invalidated`方法中处理属性变更。

  - 示例（监听圆形半径变更）：

    ```java
    circle.radiusProperty().addListener((observable, oldValue, newValue) -> {
      System.out.println("半径从" + oldValue + "变更为" + newValue);
    });
    ```



##### JavaFX 动画基础

Animation

动画基类：`javafx.animation.Animation`，核心方法`play()`/`pause()`/`stop()`；

具体动画：

PathTransition：节点沿指定路径移动；

FadeTransition：节点透明度渐变；

Timeline：通过 KeyFrame 定义关键帧，实现复杂动画。 

核心属性：

cycleCount`：循环次数（`Animation.INDEFINITE`表示无限循环）；`

autoReverse`：是否反向循环；

rate`：动画速率（正数正向，负数反向）。

路径动画（PathTransition）：

```java
import javafx.animation.PathTransition;
import javafx.scene.shape.Circle;
import javafx.scene.shape.LineTo;
import javafx.scene.shape.MoveTo;
import javafx.scene.shape.Path;
import javafx.util.Duration;

// 创建路径（矩形路径）
Path path = new Path();
path.getElements().addAll(
  new MoveTo(50, 50),
  new LineTo(350, 50),
  new LineTo(350, 250),
  new LineTo(50, 250),
  new LineTo(50, 50)
);

// 创建圆形节点
Circle circle = new Circle(20);

// 路径动画
PathTransition pt = new PathTransition(Duration.seconds(4), path, circle);
pt.setCycleCount(Animation.INDEFINITE); // 无限循环
pt.setAutoReverse(true); // 反向循环
pt.play(); // 播放动画
```

淡入淡出动画（FadeTransition）：

```java
import javafx.animation.FadeTransition;
import javafx.scene.control.Button;
import javafx.util.Duration;

Button bt = new Button("Fade");
FadeTransition ft = new FadeTransition(Duration.seconds(2), bt);
ft.setFromValue(1.0); // 初始透明度（不透明）
ft.setToValue(0.0); // 目标透明度（透明）
ft.setCycleCount(2); // 循环2次
ft.setAutoReverse(true); // 反向（透明→不透明）
ft.play();
```

时间轴动画（Timeline）：

```java
import javafx.animation.KeyFrame;
import javafx.animation.Timeline;
import javafx.scene.shape.Rectangle;
import javafx.util.Duration;

Rectangle rect = new Rectangle(20, 20);
Timeline timeline = new Timeline(
  new KeyFrame(Duration.seconds(0), e -> rect.setX(0)), // 初始位置
  new KeyFrame(Duration.seconds(2), e -> rect.setX(300)) // 2秒后位置
);
timeline.setCycleCount(Animation.INDEFINITE);
timeline.setAutoReverse(true);
timeline.play();
```



### Chatper17

![image-20251215163237278](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251215163237278.png)

##### Java 的 I/O 处理机制

- File 类仅封装文件或路径的属性（如存在性、路径），不包含读写数据的方法。需通过专门的 I/O 类（如 PrintWriter、Scanner、FileInputStream 等）实现数据读写。

- 示例（文本 I/O）：

  java

  ```java
  // 文本写入
  PrintWriter output = new PrintWriter("temp.txt");
  output.println("Java 101");
  output.close();
  
  // 文本读取
  Scanner input = new Scanner(new File("temp.txt"));
  System.out.println(input.nextLine()); // 输出"Java 101"
  ```

  

##### 文本文件与二进制文件的核心差异

| 维度             | 文本文件                                       | 二进制文件                 |
| ---------------- | ---------------------------------------------- | -------------------------- |
| 存储形式         | 字符的编码形式（如 UTF-8、ASCII）              | 原始字节（二进制位序列）   |
| 可读性           | 人类可读（文本编辑器可打开）                   | 人类不可读（仅程序可解析） |
| 数据转换         | 需编码（写）/ 解码（读）                       | 无需转换，直接读写字节     |
| 效率             | 较低（转换耗时）                               | 较高（无转换过程）         |
| 示例（存储 199） | 存储字符 '1'（0x31）、'9'（0x39）、'9'（0x39） | 存储字0xC7（十进制 199）   |

Text I/O requires encoding/decoding (Unicode ↔ file-specific encoding);
Binary I/O no conversion (byte is copied directly).



##### Binary I/O Classes

![image-20251215163805560](C:\Users\chenz\AppData\Roaming\Typora\typora-user-images\image-20251215163805560.png)

##### InputStream 与 OutputStream 核心方法

- InputStream（输入字节流基类）核心方法

  | 方法签名             | 功能描述                                                    |
  | -------------------- | ----------------------------------------------------------- |
  | `int read()`         | 读取一个字节，返回字节的十进制值（0-255）；文件末尾返回 - 1 |
  | `int read(byte[] b)` | 读取字节到数组 b，返回实际读取的字节数；末尾返回 - 1        |
  | `void close()`       | 关闭流，释放资源（必须调用，否则可能导致资源泄露）          |

- OutputStream（输出字节流基类）核心方法

  | 方法签名               | 功能描述                             |
  | ---------------------- | ------------------------------------ |
  | `void write(int b)`    | 写入一个字节（取 int 参数的低 8 位） |
  | `void write(byte[] b)` | 写入字节数组 b 的所有字节            |
  | `void close()`         | 关闭流，释放资源                     |

  - 注意：字节流读写时，需手动关闭流（或用 try-with-resources 自动关闭）。



##### FileInputStream 与 FileOutputStream

- FileInputStream（文件输入字节流）

  - 功能：从文件读取字节，是二进制输入的基础类。

  - 构造器

    ```java
    // 1. 通过文件路径创建
    FileInputStream fis1 = new FileInputStream("data.dat");
    
    // 2. 通过File对象创建
    File file = new File("data.dat");
    FileInputStream fis2 = new FileInputStream(file);
    ```

  - 异常：文件不存在时抛出`FileNotFoundException`。

- FileOutputStream（文件输出字节流）

  - 功能：向文件写入字节，文件不存在则创建；存在则默认覆盖（append=false）。

  - 构造器

    ```java
    // 1. 覆盖写入
    FileOutputStream fos1 = new FileOutputStream("data.dat");
    
    // 2. 追加写入（append=true）
    FileOutputStream fos2 = new FileOutputStream("data.dat", true);
    
    // 3. 通过File对象创建
    File file = new File("data.dat");
    FileOutputStream fos3 = new FileOutputStream(file);
    ```

  - 示例（复制二进制文件）：

    ```java
    import java.io.FileInputStream;
    import java.io.FileOutputStream;
    import java.io.IOException;
    
    public class TestFileStream {
      public static void main(String[] args) throws IOException {
        // 源文件与目标文件
        FileInputStream fis = new FileInputStream("source.jpg");
        FileOutputStream fos = new FileOutputStream("target.jpg");
        
        int byteRead;
        // 逐字节读取并写入
        while ((byteRead = fis.read()) != -1) {
          fos.write(byteRead);
        }
        
        // 关闭流
        fis.close();
        fos.close();
        System.out.println("文件复制完成！");
      }
    }
    ```



##### FilterInputStream/FilterOutputStream

过滤流是用于特定用途的字节过滤流。基础的字节输入流仅提供读取字节的方法。若需读取整数、双精度浮点数或字符串，需通过过滤类封装字节输入流。使用过滤类可实现对整数、双精度浮点数和字符串的读取，而非直接处理字节和字符。FilterInputStream与FilterOutputStream是数据过滤的基础类。当需要处理原始数值类型时，应使用DatInputStream和DataOutputStream进行字节过滤。



##### DataInputStream/DataOutputStream（数据流）

- 功能：读写基本数据类型（int、long、double 等）和字符串，无需手动转换字节，简化二进制 I/O 操作。

- 构造器（需包装基础流）：

  ```java
  // 数据输入流
  DataInputStream dis = new DataInputStream(new FileInputStream("data.dat"));
  
  // 数据输出流
  DataOutputStream dos = new DataOutputStream(new FileOutputStream("data.dat"));
  ```

- 核心方法（读写基本类型）：

  ```java
  // 写入基本类型
  dos.writeInt(100); // 写入int（4字节）
  dos.writeDouble(3.14); // 写入double（8字节）
  dos.writeBoolean(true); // 写入boolean（1字节）
  
  // 读取基本类型（需与写入顺序一致）
  int num = dis.readInt();
  double pi = dis.readDouble();
  boolean flag = dis.readBoolean();
  ```

- 字符串读写（UTF-8 编码）：

  ```java
  // 写入字符串（UTF-8编码，长度前缀+字节）
  dos.writeUTF("Java二进制I/O");
  
  // 读取字符串
  String str = dis.readUTF();
  System.out.println(str); // 输出"Java二进制I/O"
  ```

- 关键注意：读取顺序必须与写入顺序完全一致，否则会导致数据解析错误。



##### 二进制 I/O 中的字符与字符串存储

- `writeChar(char c)`：写入字符的 2 字节 Unicode 编码（固定长度）；
- `writeChars(String s)`：写入字符串中每个字符的 2 字节 Unicode 编码；
- writeUTF(String s)：使用 UTF-8 编码写入字符串（可变长度，更高效）：
  - ASCII 字符（0x00-0x7F）：1 字节；
  - Unicode 字符（0x80-0x7FF）：2 字节；
  - 其他 Unicode 字符：3 字节。
- 优势：UTF-8 兼容 ASCII，存储英文时比 Unicode 更节省空间，是字符串二进制存储的首选方式。



##### 数据流使用的核心注意事项

1. 读写顺序与格式必须一致：例如用`writeInt()`写入的 int，必须用`readInt()`读取，且顺序与写入时相同；
2. 检测文件末尾：

- 避免直接读取到末尾（会抛出`EOFException`）；
- 用`available()`方法：`dis.available() == 0`表示无更多可读取字节（文件末尾）；



##### 缓冲流（BufferedInputStream/BufferedOutputStream）

- 核心优势：普通字节流逐字节读写，频繁访问磁盘；缓冲流先将数据读入内存缓冲区（或从缓冲区写入磁盘），批量处理，大幅提升 I/O 性能。

- 构造器：

  ```java
  // 缓冲输入流（默认缓冲区8192字节）
  BufferedInputStream bis = new BufferedInputStream(new FileInputStream("data.dat"));
  
  // 缓冲输出流（自定义缓冲区大小10240字节）
  BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("data.dat"), 10240);
  ```

- 示例（缓冲流复制大文件）：

  ```java
  import java.io.BufferedInputStream;
  import java.io.BufferedOutputStream;
  import java.io.FileInputStream;
  import java.io.FileOutputStream;
  import java.io.IOException;
  
  public class CopyFile {
    public static void main(String[] args) throws IOException {
      long start = System.currentTimeMillis();
      
      // 用缓冲流包装基础流
      try (BufferedInputStream bis = new BufferedInputStream(new FileInputStream("largeFile.zip"));
           BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("copyFile.zip"))) {
        
        byte[] buffer = new byte[8192];
        int bytesRead;
        // 批量读取字节到缓冲区
        while ((bytesRead = bis.read(buffer)) != -1) {
          bos.write(buffer, 0, bytesRead); // 批量写入缓冲区内容
        }
      }
      
      long end = System.currentTimeMillis();
      System.out.println("复制完成，耗时：" + (end - start) + "毫秒");
    }
  }
  ```

- 注意：缓冲流无新增方法，所有方法继承自 InputStream/OutputStream，仅优化性能。



##### 对象流（ObjectInputStream/ObjectOutputStream）

- 功能：读写对象（如自定义类实例、集合等），是 Java 对象持久化的核心工具。

- 构造器（包装基础流）：

  ```java
  // 对象输出流（序列化对象）
  ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("objects.dat"));
  
  // 对象输入流（反序列化对象）
  ObjectInputStream ois = new ObjectInputStream(new FileInputStream("objects.dat"));
  ```

- 序列化规则：

  1. 类必须实现`java.io.Serializable`接口（标记接口，无抽象方法，仅标识可序列化）；

  2. 非序列化字段：用`transient`关键字标记（如敏感信息、资源对象），静态字段默认不序列化；

     如果一个对象是可序列化的实例，但它包含不可序列化的实例数据字段，那么该对象可以被序列化吗？答案是否定的。要使对象能够被序列化，可以使用 transient 关键字标记这些数据字段，告诉 JVM 在将对象写入对象流时忽略这些字段。

  3. 示例（可序列化类）：

  ```java
  import java.io.Serializable;
  import java.util.Date;
  
  // 实现Serializable接口，可序列化
  public class User implements Serializable {
    private String username;
    private transient String password; // 非序列化字段
    private int age;
    private Date registerDate;
    private static String version = "1.0"; // 静态字段，不序列化
  
    // 构造器、getter/setter省略
  }
  ```

- 对象读写示例：

  ```java
  import java.io.*;
  import java.util.Date;
  
  public class TestObjectStream {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
      // 序列化：写入对象
      try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("user.dat"))) {
        User user = new User();
        user.setUsername("张三");
        user.setPassword("123456");
        user.setAge(25);
        user.setRegisterDate(new Date());
        oos.writeObject(user); // 序列化对象
        System.out.println("对象序列化完成！");
      }
  
      // 反序列化：读取对象
      try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("user.dat"))) {
        User user = (User) ois.readObject(); // 反序列化对象
        System.out.println("用户名：" + user.getUsername());
        System.out.println("密码：" + user.getPassword()); // 输出null（transient字段）
        System.out.println("年龄：" + user.getAge());
        System.out.println("注册日期：" + user.getRegisterDate());
      }
    }
  }
  ```



##### Serializing Arrays

- 规则：数组的所有元素可序列化，则数组可直接序列化（无需数组类实现 Serializable 接口）。

- 示例（序列化字符串数组和用户数组）：

  ```java
  // 序列化数组
  try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("arrays.dat"))) {
    String[] strArray = {"Java", "Python", "C++"};
    User[] userArray = {new User("张三", 25), new User("李四", 30)};
    oos.writeObject(strArray);
    oos.writeObject(userArray);
  }
  
  // 反序列化数组
  try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("arrays.dat"))) {
    String[] strArray = (String[]) ois.readObject();
    User[] userArray = (User[]) ois.readObject();
    System.out.println("字符串数组：" + Arrays.toString(strArray));
    for (User user : userArray) {
      System.out.println("用户：" + user.getUsername());
    }
  }
  ```



##### 随机访问文件（RandomAccessFile）

- 核心特性：突破顺序 I/O 限制，可在文件任意位置读写数据（如修改文件中间记录），适用于文件记录的增删改查。

- 构造器（指定读写模式）：

  ```java
  // 读写模式（rw）
  RandomAccessFile raf = new RandomAccessFile("records.dat", "rw");
  
  // 只读模式（r）
  RandomAccessFile rafRead = new RandomAccessFile("records.dat", "r");
  ```

- 核心概念：文件指针

  - 初始位置：0（文件开头）；
  - 读写操作后：指针自动后移（如读 int 后指针 + 4 字节）；
  - 定位指针：`seek(long pos)`（pos 为字节偏移量）。

- 核心方法：

  ```java
  // 定位指针到第10字节处
  raf.seek(10);
  
  // 获取当前指针位置
  long currentPos = raf.getFilePointer();
  
  // 获取文件长度（字节数）
  long fileLength = raf.length();
  
  // 读写基本类型（与Data流方法一致）
  raf.writeInt(100);
  int num = raf.readInt();
  ```

- 示例（随机修改文件数据）：

  ```java
  import java.io.RandomAccessFile;
  import java.io.IOException;
  
  public class TestRandomAccessFile {
    public static void main(String[] args) throws IOException {
      // 写入3个int值（100、200、300）
      try (RandomAccessFile raf = new RandomAccessFile("random.dat", "rw")) {
        raf.writeInt(100);
        raf.writeInt(200);
        raf.writeInt(300);
      }
  
      // 随机修改第二个int值（200→250）
      try (RandomAccessFile raf = new RandomAccessFile("random.dat", "rw")) {
        raf.seek(4); // 第二个int从第4字节开始（每个int4字节）
        raf.writeInt(250);
      }
  
      // 读取所有值
      try (RandomAccessFile raf = new RandomAccessFile("random.dat", "r")) {
        System.out.println(raf.readInt()); // 100
        System.out.println(raf.readInt()); // 250（已修改）
        System.out.println(raf.readInt()); // 300
      }
    }
  }
  ```



##### NIO 简介（拓展内容）

- 核心差异（传统 I/O vs NIO）：

  | 维度     | 传统 I/O                   | NIO                               |
  | -------- | -------------------------- | --------------------------------- |
  | 数据处理 | 面向流（逐字节）           | 面向缓冲（块级处理）              |
  | 读写模式 | 阻塞 I/O（读写时线程等待） | 非阻塞 I/O（线程可处理其他任务）  |
  | 核心组件 | 流（Stream）               | 通道（Channel）、缓冲区（Buffer） |
  | 性能     | 适合小数据量               | 适合大数据量、高并发              |

- 核心组件：

  1. Buffer：存储数据的缓冲区（如 ByteBuffer），数据读写必须通过缓冲区；
  2. Channel：双向通道（如 FileChannel），连接数据源与缓冲区，支持读写；
  3. Selector：多路复用器，支持一个线程管理多个通道，提升并发效率。

- 内存映射文件：将文件部分或全部映射到内存，直接操作内存即可修改文件，大幅提升大文件处理性能。



### Chatper19

Generics泛型

什么是泛型？

- 定义：泛型是 “类型参数化” 的能力 —— 定义类、接口或方法时使用 “类型占位符”（如 E、T），编译时用具体类型（如 String、Integer）替换，使同一组件适配多种类型。
- 示例：定义泛型栈`GenericStack<E>`，可实例化为`GenericStack<String>`（存储字符串）或`GenericStack<Integer>`（存储整数），无需重复编写多个类型专属的栈类。



##### 泛型与非泛型的对比（以 ArrayList 为例）

| 特性         | 非泛型 ArrayList（JDK1.5 前）                                | 泛型 ArrayList<E>（JDK1.5 后）                               |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 添加元素方法 | `add(Object o)`（接受任意类型）                              | `add(E o)`（仅接受 E 类型）                                  |
| 读取元素方法 | `get(int index) -> Object`（需转型）                         | `get(int index) -> E`（无需转型）                            |
| 类型检查     | 运行时（转型时抛异常）                                       | 编译时（添加错误类型直接报错）                               |
| 代码示例     | `list.add(123); String s = (String)list.get(0);`（运行时抛异常） | `list.add("abc"); String s = list.get(0);`（无转型，编译时校验） |



##### No Casting Needed

```java
ArrayList<Double> list = new ArrayList<>();
list.add(5.5); // 自动装箱为Double
list.add(3.0);
Double doubleObject = list.get(0); // 无转型
double d = list.get(1); // 自动拆箱为double
```



##### Declaring Generic Classes and Interfaces

- 泛型栈`GenericStack<E>`的 UML 图：含`push(E o)`、`pop()`、`peek()`等方法。

- 泛型类声明语法：`class 类名<类型占位符> { ... }`，类型占位符常用 E（Element）、T（Type）。

- 示例：泛型栈GenericStack<E>的完整实现：

  ```java
  import java.util.ArrayList;
  
  public class GenericStack<E> {
    private ArrayList<E> list = new ArrayList<>();
  
    // 获取栈大小
    public int getSize() {
      return list.size();
    }
  
    // 获取栈顶元素（不删除）
    public E peek() {
      return list.get(getSize() - 1);
    }
  
    // 入栈（添加元素到栈顶）
    public void push(E o) {
      list.add(o);
    }
  
    // 出栈（删除并返回栈顶元素）
    public E pop() {
      E o = list.get(getSize() - 1);
      list.remove(getSize() - 1);
      return o;
    }
  
    // 判断栈是否为空
    public boolean isEmpty() {
      return list.isEmpty();
    }
  }
  ```

- 使用示例：

  ```java
  // 存储字符串的栈
  GenericStack<String> strStack = new GenericStack<>();
  strStack.push("Java");
  String s = strStack.pop(); // 无需转型
  
  // 存储整数的栈
  GenericStack<Integer> intStack = new GenericStack<>();
  intStack.push(100);
  int i = intStack.pop(); // 自动拆箱
  ```



##### Generic Methods

- 定义：不依赖泛型类，单独声明的 “类型参数化方法”，可独立支持多种类型。

- 声明语法：`public static <类型占位符> 返回值类型 方法名(参数列表)`，类型占位符需在返回值前声明。

- 优势：

  1. 支持基本类型数组（自动装箱）：普通`print(Object[])`无法直接接收`int[]`，泛型方法`print(E[])`可自动适配；
  2. 类型安全：编译时校验数组元素类型；

  ```java
  // 泛型方法（支持任意类型数组）
  public static <E> void print(E[] list) {
    for (E elem : list) System.out.print(elem + " ");
    System.out.println();
  }
  
  // 普通方法（仅支持Object数组）
  public static void print(Object[] list) {
    for (Object elem : list) System.out.print(elem + " ");
    System.out.println();
  }
  ```



##### Bounded Generic Type

有界泛型类型

- 定义：限制类型参数的 “上限”（必须是指定类的子类或指定接口的实现类），语法为`<E extends 上限类型>`。
- 示例分析：
  1. 泛型上限：`E extends GeometricObject`表示 E 必须是`GeometricObject`的子类（如`Rectangle`、`Circle`）；
  2. 方法权限：因 E 是`GeometricObject`的子类，可直接调用`GeometricObject`的`getArea()`方法；
  3. 类型安全：若传入非`GeometricObject`子类（如`String`），编译报错。
- 应用场景：需要调用泛型类型的特定方法时，通过 “上限” 明确方法来源

```java
public static void main(String[] args) {
  Rectangle rectangle = new Rectangle(2, 2);
  Circle circle = new Circle(2);
  System.out.println("Same area? " + equalArea(rectangle, circle));
}

public static <E extends GeometricObject> boolean equalArea(E object1, E object2) {
  return object1.getArea() == object2.getArea();
}
```



##### 通配符（Wildcards）

- 作用：灵活处理泛型类型，解决 “泛型类型不兼容” 问题（如`ArrayList<Integer>`不能赋值给`ArrayList<Number>`）。

- 三种通配符：

  1. 无界通配符（?）：匹配任意类型（如`ArrayList<?>`），适用于仅读取、不修改的场景；
  2. 有界通配符（? extends T）：匹配 T 及其子类（如`? extends Number`匹配 Integer、Double），仅支持读取（不能添加元素，避免添加子类类型不兼容的元素）；
  3. 下界通配符（? super T）：匹配 T 及其父类（如`? super Integer`匹配 Integer、Number、Object），支持添加 T 类型元素。

  ```java
  // 无界通配符：打印任意类型的ArrayList
  public static void printList(ArrayList<?> list) {
    for (Object elem : list) System.out.print(elem + " ");
  }
  
  // 有界通配符：计算数字列表的总和
  public static double sum(ArrayList<? extends Number> list) {
    double total = 0;
    for (Number num : list) total += num.doubleValue();
    return total;
  }
  
  // 下界通配符：添加整数到列表
  public static void addIntegers(ArrayList<? super Integer> list) {
    list.add(10); // 可添加Integer类型
  }
  ```



##### Erasure and Restrictions on Generics

- 类型擦除与泛型限制
  - 类型擦除：Java 泛型是 “编译时特性”—— 编译器编译泛型代码时，会擦除类型占位符（如 E、T），替换为 “上限类型”（无上限则为 Object），生成与原始类型兼容的字节码。
  - 目的：保证泛型代码与 JDK1.5 前的遗留代码（原始类型）向后兼容。
  - 示例：
    - 泛型类`GenericStack<E>`编译后，E 被擦除为 Object，`push(E o)`变为`push(Object o)`；
    - 有界泛型`E extends GeometricObject`编译后，E 被擦除为`GeometricObject`。



##### 重要特性（泛型的运行时表现）

- 核心事实：同一泛型类的所有实例（无论指定何种具体类型），运行时共享同一个类文件。

  ```java
  GenericStack<String> strStack = new GenericStack<>();
  GenericStack<Integer> intStack = new GenericStack<>();
  System.out.println(strStack.getClass() == intStack.getClass()); // 输出true
  ```

- 原因：类型擦除后，`GenericStack<String>`和`GenericStack<Integer>`均退化为`GenericStack`类，无运行时泛型信息。



##### 泛型的限制（源于类型擦除）

1. 不能创建泛型类型的实例：

   ```
   new E()
   ```

   编译报错（运行时 E 已被擦除为 Object，无法确定具体类型）；

   - 解决方案：通过反射创建实例（`(E) Class.forName(className).newInstance()`）；

2. 不能创建泛型数组：

   ```
   new E[10]
   ```

   编译报错（避免类型转换异常）；

   - 解决方案：使用`ArrayList<E>`替代泛型数组，或创建`Object`数组后转型（`(E[]) new Object[10]`）；

3. 泛型参数不能用于静态上下文：静态字段 / 方法不能使用类的泛型参数（如

   ```
   private static E data;
   ```

   编译报错）；

   - 原因：静态成员属于类，而泛型参数是实例层面的（不同实例可能指定不同类型）；

4. 异常类不能是泛型：

   ```
   class MyException<E> extends Exception { ... }
   ```

   编译报错；

   - 原因：异常处理依赖运行时类型信息，而泛型类型已被擦除。



> 本文档会持续更新，最新版戳 ➜ [GitHub 仓库]([veda-chen/Java-](https://github.com/veda-chen/Java-))
