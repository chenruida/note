# Java 基础知识

## JVM、JDK和JRE的关系

- JVM :运行java程序的虚拟机 各个系统都有自己的虚拟机 Windows jvm 和 Linux jvm等
- JRE：Java runtime environment java程序运行环境 **包括 jvm**和各种类库
- JDK: Java Development Kit   java程序开发工具包 **包括 JRE**和开发使用的工具

## Javac 和 java

- javac classname.java 编译程序 编译得到 classname.class 
- java classname 运行程序

## 编译器

- 对于byte/short/char三种类型，如果右侧赋值没有超过范围，那么javac编译器将会自动隐含为我们补上一个（byte)(short)(char)
  - 如果没有超过左侧的范围，强转
  - 如果超过，报错
- 使用表达式时，所有的byte型. short型和char型将被提升到int型
- **编译器的常量优化**：在给变量进行赋值时，如果右侧表达式全是常量，没有任何变量，那么编译器javac将会先对常量表达式运算

## switch

匹配哪一个case就从哪一个位置向下执行，直到遇到break或者整体结束为止。

## IDEA 
### 项目目录
Project

Module

<<<<<<< HEAD
Package(英文小写，.,数字)
=======
Package(英文小写数字)
>>>>>>> e83f4da48de1d1d0c78c8b8c24c7326e8f9a9c1f
### 快捷键

|       快捷键       |                  功能                  |
| :----------------: | :------------------------------------: |
|     Alt+Enter      |          导入包，自动修正代码          |
|       Ctrl+Y       |            删除光标所在的行            |
|       Ctrl+D       | 复制光标所在行的内容，插入光标位置下面 |
|      Alt+Ins       |              自动生成代码              |
| Alt+Shift+上下箭头 |             移动当前代码行             |
<<<<<<< HEAD
=======
|       .fori        |                遍历元素                |

## 重载

- 只改变参数的类型和顺序

## 数组

特点

- 引用类型         所有的引用类型变量，都可以赋值为null值。但是代表其中什么都没有。
- 数组长度在程序运行期间不可改变

初始化方式：

- 动态初始化（指定长度） 数据类型[] 数组名称 = new 数据类型[数组长度]；
- 静态初始化（指定内容）
- 可以拆分成两个部分，但是静态出
- 数组必须new初始化才能使用其中的元素，如果只是赋值一个null,没有new创建，那么将会发生空指针异常 NullPointException

元素获取

- 直接打印室得到数组对应的，内存地址哈希值

赋值

- 默认值
  - 整数 0
  - 浮点 0.0
  - 字符类型 ‘/u0000’
  - 布尔类型 false
  - 引用类型 null
- 静态初始化其实也有一个默认值过程，只不过系统马上将默认值替换为了大括号中的具体数值。

方法

- array.length   获取数组长度

内存图

![](.\picture\数组内存.jpg)



## java内存

Java的内存划分为5个部分

1. ==栈(stack): 存放得我都是方法中的局部变量。==
   - 局部变量：方法的参数，或者方法中的变量
   - 作用域：一旦超出作用域，立刻从栈内存中消失
   - ==方法一定要在栈中运行==
2. ==堆（Heap）:凡是new 出来的东西，都在堆当中。==
   - 堆内存里的东西都有一个地址值：16进制
   - 堆内存中的数据都有默认值
3. 方法去（Method Area）:存储class相关信息，包含方法的信息
4. 本地方法栈（Native Method Stack）:与操作系统相关
5. 寄存器(pc Register):与内存相关

## 面向对象

当需要实现一个功能时，不关系具体的步骤，而是找到一个具有该功能的对象，实现该功能

三大特征

- 封装
  - 方法就是一种封装
  - private也是一种封装，将需要保护的成员变量进行修饰
- 继承
- 多态

使用

- 导包 import包名称.类名

标准类组成部分：

1. 成员变量都要使用private关键字修饰
2. 为每一个成员变量编写一对 getter/setter方法
3. 编写一个无参数的构造方法
4. 编写一个全参数的构造方法

## Scanner 类

java.lang包下的内容不要导包，其他都需要import语句。

## 匿名对象

- 只有右边的对象，没有左边的名字和赋值运算符

- new 类名称（）;

- 只能使用唯一的一次
- 使用建议：如果确定有一个对象只需要使用唯一的一次，就可以用匿名对象。

## ArrayList 

- 可变大小

- 从JDK 1.7+开始，右侧的尖括号内部可以不写内容，但是<>本身还是要写的

- 对于arraylist 直接打印不是地址值，而是内容。

- 如果是空的，则为[]

- 泛型只能是引用类型，不能是基本类型

  - 存储基本类型，必须使用基本类型的包装类

    - | 基本类型 |    包装类     |
      | :------: | :-----------: |
      |   byte   |     Byte      |
      |  short   |     Short     |
      |   int    |  ==Integer==  |
      |   long   |     Long      |
      |  float   |     Float     |
      |  double  |    Double     |
      |   char   | ==Character== |
      | boolean  |    Boolean    |

- 从JDK1.5 支持自动装箱，自动拆箱

常用方法

1. 添加元素 public boolean add(E e);
2. 获取元素 public E get(int index)
3. 删除元素 public E remove( int index);
4. 获取大小 public int size();

## 字符串

特点：

- 字符串的内容永不改变
- 因为不可改变，所以可以共享使用
- 字符串效果上相当于char[]字符数组，但是底层原理是byte[]字节数组。

创建方法：

1. String() 创建一个空白字符串，不含任何内容
2. String(char[] array),根据字符数组的内容，来创建对应的字符串
3. String(byte[] array)，根据字节数据的内容，来创建对应的字符串

字符串常量池

- 程序当中直接写上的双引号字符串，就在字符串常量池中
  - 基本类型，==比较的是值
  - 引用类型，==比较的是地址
- 在堆当中

![](.\picture\字符串内存.png)

方法

- public boolean equals(object obj)参数可以是任何对象，只有参数是一个字符串并且内容相同的，才能true
  - 任何对象都能被equal接受
  - 一个常量一个变量，推荐把常亮放在前面，避免空指针
  - 区分大小写，只有英文区分大小写
- public String concat(String str):拼接字符串
- public char charAt(int index):获取指定索引位置的的那个字符
- public int indexOf(String str):查找参数字符串在本字符串当中首次出现的索引值，没有返回-1值
- 截取方法
  - public String substring(int index),从参数位置一直到字符串末尾，返回新字符串
  - public String substring(int begin,int end),截取从begin开始，一直到end结束
- 转换
  - public char[] toCharArray()，拆分成字符数组
  - public byte[] getBytes(),获得当前字符串底层的字节数组
  - public String replace(CharSequence oldString,CharSequence newString);
- 分割方法
  - public String[] split(String regex)按照参数规则，将字符串切分为若干个部分
  - 规则 ：正则表达式，如果用"."切分，要用“//.”

## 静态方法

关键字 static

- 可以用于对象计数器
- 静态方法不能访问非静态
  - 因为在内存当中，现有的静态内容，后有的非静态内容
- 静态方法不能用this关键字
- 方法区中有一块单独的静态区

![](.\picture\静态成员内存.jpg)

## 数组工具类 Arrays

与数组相关的工具类，提供了大量静态方法，用来实现数组常见的操作

- public static String toString(数组):将参数数组变成字符串（按照默认格式：【元素1，元素2。。。】）
- public static void sort(数组)：按照默认升序（从小到大）对数组的元素进行排序
  - 如果是数值，sort默认按照升序从小到大
  - 如果是字符串，sort默认按照字母升序
  - 如果是自定义类，需要Comparable或者Comparator接口的支持

## 数学工具类 Math

- abs 绝对值
- ceil 向上取整
- floor 向下取证
- round 四舍五入

## 继承

- 继承是多态的前提，若果没有继承，就没有多态

- 继承主要解决的问题：==共性抽取==

格式

- public class 子类名称 ==extend 父类名称==｛｝

访问特点：在父子类的继承关系中，如果成员变量重名，则创建子类对象时，访问有两种方式：

- 直接通过子类对象访问成员变量
  - 等号左边是谁，就优先用谁，没有则向上找
- 间接通过成员方法访问成员变量
  - 该方法属于谁，就优先用谁，没有则向上找
  - 成员变量的值优先在方法所在的类中找，找到就取出，

区分子类方法中重名的三种变量：

- 方法内的局部变量，直接写成员变量名
- 本类的成员变量： this.成员变量名
- 父类的成员变量： super.成员变量名

成员方法的访问特点：

- 在父子的继承关系当中，创建子类对象，访问成员方法的规则：
  - 创建的对象是谁，就优先用谁，没有则向上找

覆盖重写：

- Override,方法的名称一样，参数列表也一样

- 特点：创建的是子类对象，则优先用子类方法

- 注意事项

  - 必须保证父子类的名称相同，参数列表也相同
  - @Override：写在方法前面，用来监测是否正确覆写
  - 子类方法的返回值，必须小于等于父类方法的返回值范围
    - java.lang.Object是所有类的父类
  - 子类方法的权限必须大于等于方法的权限修饰符
    - public>protected>(default)>private

- 使用场景：

  - 对于已经投入使用的类，尽量不要修改，推荐定义一个新的类，来重复利用其中共性内容，并且添加心得功能

  - super.show(); 把父类的方法重复利用
  

构造方法：
  - 子类构造方法当中有一个默认隐含的“super()”调用，所以一定是先执行父类构造，再执行子类构造
  - 子类构造可以通过super关键字来调用父类重载构造
  - super的父类构造调用，必须是子类构造方法的第一句；不能调用多次super构造
  - 子类必须调用父类构造方法，不写则默认super();写了则用写的指定的super调用，super只能有一个，还必须是第一个

Java继承三个重要特征：

- Java是单继承的
- Java可以多级继承
- 父类唯一，一个父类可以拥有多个子类

抽象方法和抽象类

- 抽象方法，就是加上abstract关键字，然后去掉大括号，直接分号结束
- 抽象方法所在的类，必须是抽象类才行。在class之前写上abstract即可
- 用法
  - 不能直接new
  - 不许用一个子类来继承抽象父类
  - 必须覆盖重写所有的抽象方法

- 注意事项
  - 抽象类不能创建对象
  - 抽象类中，可以有构造方，是供子类创建对象时，初始化父类成员使用的。
  - 抽象类，不一定包含抽象方法，但是有抽象方法的类必定是抽象类，其目的是不想调用者创建该类对象

## 接口和多态

接口就是多个类的公共规范

接口一种引用数据类型，最重要的内容就是抽象方法

关键字：interface

可包含的内容：

- 常量
- 抽象方法
- 默认方法 （java8）
- 静态方法（java8）
- 私有方法（java9）

使用步骤：

1. 接口不能直接使用，必须有一个“实现类”来“实现”该接口
   - public class 类型 implements 接口名称｛｝
2. 接口的实现类必须覆盖重写（实现）接口中所有的抽象方法。
   - 实现：去电abstract关键字，驾驶方法体大括号
3. 创建实现类的对象，进行使用

- 如果实现类并没有覆盖重写接口中的所有抽象方，纳闷这个实现类必须是抽象类

默认方法

- 格式：public default 返回值类型 方法名称（参数列表）｛方法体｝
- 可以解决接口升级的问题

静态方法

- public static 返回值类型 方法名称（参数列表）｛方法体｝
- 接口名称直接调用

私有方法

- 抽取一个共有方法
- 普通私有方法
  - private 返回值类型 方法名称（参数列表）
- 静态私有方法
  - private static 返回值类型 方法名称（参数列表）

“成员变量“（常量）

- 必须使用 public static final 关键字修饰
  - 一旦使用final关键字，说明不可改变
  - 不写也照样是这样
- 必须赋值
- 大写，多个字母下划线 MAX_NUMBER

注意：

1. 接口是没有静态代码块或者构造方法的
2. 一个类的直接父类是唯一的，但是一个类可以实现多个接口
3. 如果实现类所实现的多个接口中，存在重复方法，实现一次即可
4. 对多个接口当中冲突方法一定要覆盖重写
5. 接口的默认方法和父类的方法冲突，优先使用父类的方法

接口的继承

- 接口与接口之间是多继承的
- 多个父接口当中的抽象方法如果重复，没关系
- 多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写【而且带着default关键字】

## 多态

- extends继承或者implements实现，是多态性的前提
- 一个对象有用多种形态，这就是对象的多态性
- 代码中体现多态性，其实就是弗雷引用指向子类对象
- 格式：
  - 父类名称 对象名=new 子类名称();
  - 接口名称 对象名 = new 实现类名称();
- 好处： 无论右边new 的对象类型，调用方法都不会变
- 弊端：无法使用子类的特有内容
- 对象向上转型
  - 即多态写法 
  - 向上转型一定是安全的
- 向下转型
  - 格式：子类名称 对象名 = （子类名称）父类对象
  - 含义将父类对象，==还原==成为本来的子类对象
  - 必须保证对象在创建时，就是猫，才能向下转型成猫，否则报错
    - 判断方法 instanceof

接口可以作为成员对象，参数和返回值

## 修饰符

final

1. 修饰一个类
   
   - 不能有子类，所有的成员方法不能进行覆盖重写
2. 修饰一个方法
   
   - 这个方法是最终方法，不能覆盖重写
3. 修饰局部变量
   - 一次赋值，终生不变
     - 基本类型，值不改变
     - 引用类型，地址值不改变


修饰成员变量

|              | public | protected | default | private |
| :----------: | :----: | :-------: | :-----: | :-----: |
|     同类     |   √    |     √     |    √    |    √    |
|     同包     |   √    |     √     |    √    |    ×    |
|  不同包子类  |   √    |     √     |    ×    |    ×    |
| 不同包非子类 |   √    |     ×     |    ×    |    ×    |

成员内部类

- 内用外，随便用。外用内需要内部类对象
  - 外部类名称。内部类名称    对象名 =  new 外部类名称（）.new 内部类名称（）;
- 如果希望访问所在方法的局部变量，那么这个局部变量不许是（有效final的）

## 匿名内部类

若果接口的实现类（或者父类的子类）只使用唯一的一次

那么这种情况下就可以湖绿掉该类的定义，而改为使用【匿名内部类】

定义格式：

- 接口名称 对象名 = new 接口名（） ｛覆盖重写所有的抽象方法｝

解析：

- new 代表创建对象的动作
- 接口名称就是匿名内部类的内容
- ｛。。。｝这才是内部类的内容

注意事项：

- 匿名内部类，在创建对象，只能使用唯一一次
  - 如果想多次创建对象，且方法一样就要使用实现类
- 匿名对象，在调用方式时，只能调用一次
- 匿名内部类时忽略了实现类、子类



## Object 类

- equal方法
  - 基本类型比较值
  - 引用类型比较地址
  - 如果要比较其他需要复写方法，注意多态无法使用子类的特有方法，所有需要向下转型
  - objects.equal（）可以防止空指针
- toString方法
  - 打印对象的信息
    - 重写前打印包名@地址值
    - 重写后打印 属性值

## 日期类

- Date类
  - java.util.Date 表示日期和时间的类
  - 精确到毫秒，毫秒值可以对时间和日期进行计算
  - 获取当前日期到时间原点之间经历的多少毫秒（1970.01.01 00：00：00）
  - 中国在东八区，所以时间原点在（1970.01.01 08：00：00）
  - 
- DateFaormat
  - java.text.DataFormat
  - String format() 按照指定的模式，把Data日期，格式化微符合模式的字符串
  - SimpleDateFormat() parse（string source） 把符合模式的字符串，解析为Date日期
- Calender
  - 抽象类

## system 类

获取系统相关信息或系统级操作

- currentTimeMillis 获取当前时间
- arraycopy(Object src,int srcPos,Object dest,int destPos，int length) 将数组中指定的数据拷贝到另一个数组中
  - srcpos 原数组起始位置
  - destPos 目标数组元素的起始位置
  - length 要复制的数组元素的数量

- StringBuilder类
  - 字符串缓冲区，可以提高字符串的操作效率（看成一个长度可以变化的字符串）
  - 底层也是一个数组，但是没有被final、修饰，可以改变成长度
  - append 返回this,因此无需接收返回值
  - reverse(); 反转内容
  - tostring ()；将缓冲区转为字符串

## 包装类

基本类型的引用类

- 装箱 基本类型数据，包装到包装类中
  - Integer(int value) 构造一个新分配的Integer对象，它表示指定的int
  - Integer（String s）构造一个新分配的Integer对象，它表示String 参数所指示的int值，传递的字符串，必须是基本类型的字符串
  - Static Interge valueOf(int i)返回一个表示指定的int值得Integer实例
  - static Integer valueOf(string i)
- 在包装类中取出基本类型的数据（包装类 ->基本类型数据）
  - int  intValue()以 int类型返回该Integer的值
- 自动拆、装箱

## Collection 集合

java中提供的一种容器，可以用来存储多个数据

与数组的区别

- 数组长度固定，集合长度可变
- 数组存储的是同一类型的元素，可以存储几倍数据类型值。集合存储的是对象，而且对象的类型可以不一致。

类型

- Vector
- ArratList
- LinkedList
- TreeSet
- HashSet
- LinkedHashSet

![](.\picture\集合框架.jpg)

### 迭代器

再取出元素之前。判断集合中有没有元素，如果有，就把这个元素取出，继续判断，如果还有就再取出，一直到把集合中所有元素取出

两个常用的方法：

- hasNext()如果荣有元素可以叠戴，则返回true
- E next() 返回迭代的下一个元素

迭代器是一个接口无法直接使用，需要使用接口的实现类对象，获取实现类的方式比较特殊

collection接口中有一个方法，角iterator(),这个方法返回的就是迭代器的实现类对象

- Iterator<E> iterator() 返回在此 collection的元素上进行迭代的迭代器

使用步骤

1. 使用结合中的方法iterator()获取迭代器的实现类对象，使用Iterator接口接受
2. 使用Iterator接口中的方法hanNext判断还有没有下一个元素
3. 使用Iterator接口中的方法next取出集合中的下一个元素

使用while循环

### 增强for

增强for 是JDK1.5以后出来的一个高级for循环，专门用来遍历数组和集合。他的内部原理其实是歌Iterator迭代器。

==所以在遍历的过程中，不能对集合中的元素进行增删操作==。

格式：

for(元素的数据类型 变量：Collection集合or数组)｛

｝

## 泛型

泛型是一种未知的数据类型，当我们不知道什么数据类型的时候，可以使用泛型

E：未知的数据类型

创建集合对象时，就会确定泛型的数据类型

集合不适用泛型，默认类型就是Object类型，可以存储任意类型的数据

好处：

- 避免了类型转换的麻烦，存储的是什么类型，取出的就是什么类型
- 把运行期间异常，提升到了编译期

弊端：

- 泛型是什么类型，就只能存储什么类型

含有泛型的方法

修饰符<泛型>返回值类型 方法名（参数列表（使用泛型））｛

方法体｝

接口使用泛型：

1. 定义接口的实现类，指定接口的泛型
2. 接口使用什么泛型，实现类就使用什么泛型，类跟着接口走

泛型通配符

- 不知道使用什么类型来接收的时候，此时可以使用？，？表示未知通配符
- 此时只能接受数据，不能输入数据
- 不能创建对象使用，定义时不能使用
- 只能作为方法的参数使用

泛型没有继承概念，所以用？代表object

泛型的上限限定：？ extends E 代表使用的泛型只能是E类型的子类/本身

泛型的下限限定：？ super E 代表使用的泛型只能是E类型的父类/本身

## 数据结构

### ArrayList

底层是数组结构，特点是增删慢，查找快

### LinkedList

- 底层是一个链表结构：查询慢，增删快
- 里面包含了大量操作首位元素的方法

### Vector

### HashSet

- 哈希值：是一个十进制的整数，由系统随机给出（就是对象的地址值，是一个逻辑地址，是模拟出来的地址，不是数据实际存储的地址）
  - public native int hashcode()
    - native 代表该方法调用的是本地操作系统的方法
- 哈希表结构
  - JDK1.8之前 哈希表=数组+链表
  - JDK1.8之后 哈希表=数组+链表 和 哈希表=数组+红黑树（提高查询速度）
- 存储自定义类型元素
  - 需要重写hashcode和equals方法

### LinkHashSet

- 底层是哈希表（哈希表+链表）：多一条链表（记录元素的存储顺序），保证元素有序

## 可变参数

- JDK1.5 之后出现的新特性

- 当方法的参数列表数据类型已经确定，但是参数的个数不确定，就可以使用可变参数

- 使用格式：定义方法是时使用

- 修饰符：返回值类型 方法名（数据类型  ...变量名）

- 可变参数原理：
  - 可变参数底层就是一个数组，根据传递参数个数不同，会创建不同长度的数组，来存储这些参数

- 传递参数个数，可以是0个

注意事项：

- 一个方法的采纳数列表，只能有一个可变参数
- 如果方法的参数有多个，那么可变参数必须写在参数列表的末尾

## Map集合

特点：

- 是一个双列集合，一个元素包含两个值
- 元素是孤立存在的，key和value的数据类型可以相同，也可以不同
- 一个键对应一个值

实现类

- HashMap集合的特点
  - HashMap集合底层是哈希表：查询的速度特别的快。
  - 是一个无序的集合，存储元素和取出的顺序有可能不一致
- LinkeHashMap
  - 底层是哈希表+链表（保证迭代的顺序）
  - 有序的集合，存储元素和取出元素的顺序是一致的

常用方法

- v put(key,value)
- V get(key)
- remove

遍历

1. 使用Map集合中的方法keySet(),把Map集合所有的key取出来，存储的一个set集合中
2. 编列set集合，获取Map集合中的每一个key
3. 通过Map集合中的方法get(key),通过key找的value

Entry

- 映射项，在Map接口中有一个内部接口Entry
- 当Map集合一创建，纳闷就会在Map集合中创建一个Entry对象，用来记录键与值

![](.\picture\entry.jpg)

存储自定义对象

- 作为key的元素，必须重写hashCode方法和euqals方法，以保证key唯一

## jdk9 新特性

里面增加了一个静态方法of,可以给集合一次性添加多个元素

static<E> list<E> of (E... element)

使用前提：

​	当即和中存储的元素的个数已经确定，不在改变时使用

注意：

1. of方法只适用于List接口，set接口，map接口，不适用于接口类的实现
2. of方法的返回值是一个不能改变的集合，集合不能在使用add,put方法添加元素，会抛出异常
3. set接口和map接口在调用of方法时，不能有重复的语速，否则抛出异常

## 异常

Exception 编译期异常，进行编译（写代码）java程序出现的问题

RuntimeException 运行期异常，Java程序运行过程中出现的问题

Error:异常就相当于程序得了一个小毛病，把异常处理掉，程序可以继续执行



### throw关键字

作用：

- 可以使用throw关键字在指定的方法中抛出指定的异常，让方法的调用者处理

使用格式：

- throw new xxxException（“异常产生的原因”）

注意：

1. throw关键字必须写在方法的声明处
2. throw关键字后面new的对象必须是Exception的子类对象
3. throw关键字抛出指定的异常对象，我们就必须处理这个异常对象
   1. throw关键字后面创建的是RuntimeException或者是RuntimeException的子类对象，我们可以不处理，默认交给JVM处理（打印异常对象，中断程序）
   2. throw关键字后面创建的是编译异常（写代码的时候报错），我们必须处理这个异常，要么throws，要么try。。。catch

非空判断

Objects.RequireNonNull(obj,string);

### try...catch

格式：

​	try{

可能产生异常的代码}catch（定义一个异常变量，用来接收try中抛出的异常对象）｛

异常的处理逻辑，接受异常对象之后，怎么处理异常对象，一般工作中，会把异常的信息记录到一个日志中｝

...catch(异常类名 变量名)｛｝

注意：

1. try中可能会抛出多个异常对象，纳闷就可以使用多个catch来处理这些异常对象
2. 如果try中产生异常，纳闷就会执行catch中的异常处理逻辑，执行完毕catch中的处理逻辑，继续执行try....catch之后的代码，若果try中没有异常，就不执行catch中异常的处理逻辑，执行完try中的代码，继续执行try...catch之后的代码

### Throwable类中3个异常处理的方法

- String getMessage()返回此throwable的简单信息
- String toString() 返回此throwable的详细信息
- void printStackTrace()  JVM打印异常对象，默认此方法，打印的异常信息是最全面的

### finally

无论是否出现异常都会执行

1. finally不能单独使用，必须和try一起使用
2. finally一般用于资源释放（资源回收），无论程勋是否出现异常，最后都要资源释放（IO）

## 注意事项

多个异常如何处理

1. 多个异常分别处理

2. 多个异常一次捕获，多次处理

   1. catch里面定义的异常变量，若果有子父类关系，那么子类的异常变量必须写在上边，不然就会报错

3. 多个异常一次捕获一次处理



如果finally中中有return语句，永远返回finally中的结果，避免该情况。因此一般不要在finally中写return语句



子父类异常

- 父类异常什么样，子类异常就什么样

### 自定义异常

格式：

public class xxxException wxtends Exception | RuntimeException{

添加一个空参数的构造方法

添加一个带异常信息的构造方法

}

注意：

- 自定义异常类一般都是以Exception结尾，说明该留是一个异常类
- 自定义异常类，必须继承Exception或者RuntimeException
  - 继承Exception:那么自定义异常类就是一个编译器异常，如果方法内部抛出了编译器异常，那就必须处理这个异常，要么throws，要么try...catch
  - 继承RuntimeException:那么自定义长类就是一个运行期异常，无需处理，交给虚拟机处理

## 多线程

并发：至两个或多个时间在同一时间段内发生，交替执行

并行：至两个或多个时间在同一时刻发生，同时发生

进程：指一个内存中运行的应用程序

线程：

- 分时调动，所有线程轮流使用CPU的使用权，平均分配每个线程占用CPU的时间
- 抢占式调度，优先让优先级搞得线程使用CPU，如果线程优先级相同，那么会随机选择一个（线程随机性），Java使用该调动方法

主线程：执行主方法（main）的线程执行从main方法开始，从上到下依次执行

### 创建线程类

1. 创建Thread类的子类
   - Java.lang.Thread类：是描述线程的类，我们想要实现多线程程序，就必须继承Thread类
   - 实现步骤：
     1. 创建一个Thread类的子类
     2. 在Thread类的子类中重写Thread类中的run方法，设置线程任务（开启线程要作什么？）
     3. 创建Thread类的子类对象
     4. 调用Thread类的方法start方法，开启新的线程，执行run方法
   - 常用方法
     - String getName() 返回该线程的名称
     - static Thread currentThread() 返回对当前正在执行的线程对象的引用
     - static sleep（long millis）
2. ==实现Runnable接口的而实现。重写run方法==
   - 实现步骤：
     1. 创建一个Runnable接口的实现类
     2. 在实现类中重写Runnable接口的run方法，设置线程任务
     3. 创建一个Runnable接口的实现类对象
     4. 创建Thread类对象，构造方法中传递Runnable接口的实现类对象
     5. 调用Thread类中的start方法，开启新的线程执行run
3. 两种方法的区别，也就是Runnable接口创建多线程程序的好处：
   1. 避免了单继承的局限性
      - 一个类只能继承一个类，类继承了Thread类就不能继承其他类
      - 实现了Runnnable接口，还可以继承其他的类，实现其他的接口
   2. 增强了程序的扩展性，降低程序的耦合性（解耦）
      - 实现了Runnable接口的方式，把设置线程任务和开启新线程进行了分解（解耦）
      - 实现类中，重写了run方法:用来设置线程任务
      - 创建Thread类对象，调用start方法：用来开启新线程
4. 匿名内部类方式实现线程的创建

### 线程安全问题

多线程访问了共享数据，会产生线程安全问题

解决方法：让一个线程在访问共享数据的时候，无论是否是去了cpu的执行权，让其他的线程只能等待。

### 线程同步

1. 同步代码块
   1. synchronized(同步锁)｛可能出现问题的代码块（访问了共享数据的代码）｝
   2. 注意：
      1. 通过代码块的锁对象，可以使用任意的对象
      2. 但是必须保证多个线程使用的锁对象是同一个
      3. 锁对象作用：把代码块锁住，只让线程在同步代码块中执行
   3. 原理：
      1. 使用了一个锁对象，这个锁对象叫做同步锁，也叫对象锁，也叫对象监视器
2. 同步方法
   1. 定义一个方法 方法加入限定关键字 synchronized
   2. 方法：
      1. 把访问了共享数据的代码抽取出来，放到一个方法中
      2. 在方法上添加synchronized修饰符
   3. 静态同步方法：
      1. 静态的同步方法锁对象，不能是this。
      2. 静态方法的锁对象是本类的class属性--》class文件对象（反射）
3. 锁机制（Lock锁）
   1. java.util.concurrent.locks
   2. 方法：
      1. void lock()
      2. void unlock()
   3. 使用步骤：
      1. 在成员位置创建一个Reentrantlock对象
      2. 在可能出现安全问题的代码前调用lock接口中的方法lock获取锁
      3. 在可能会出现安全问题的代码后调用lock接口中方法unlock释放锁

## 线程的状态

![](.\picture\线程状态.jpg)

### 无限等待（waiting）

一个正在无限期等待另一个线程执行一个特别的（唤醒）动作的线程处于之一状态

object.wait(锁对象)

object.notify(唤醒) 

### 等待唤醒机制

多个线程在处理同一个资源，但是处理的动作（线程的任务）却不相同

为什么要处理线程间的通信：

- 多个线程并发执行时，在默认情况下CPU时随机切换线程的，但当我们需要多个线程来共同完成一件任务，并且我们希望他们有规律的执行，那么多线程之间需要一些协调通信，以此来帮我们达到多线程共同操作一份数据

### 线程池

- 就是一个集合(LinkedList<Thread>)
- 当程序第一次启动的时候，创建多个线程，保存到一个集合中
- Thread t = linked.removeFist(); Thread t = list.removed(0);
- list.add(t); linked.addLast(t);
- Jdk1.5之后已经

#### 用法

java.util.concurrent.Executor:线程池的工厂类，用来生成线程池

Executors类中的静态方法：

​	static ExecutorService newFixedThreadPool(int nThreads) 创建一个可重用固定线程数的线程池

ExecutorService 接口，返回的时ExecutorService 接口的实现类对象，我们可以使用ExecutorService 接口接受

使用步骤：

1. 使用线程工厂类Executors里面提供的静态方法newFixedThreadPool是生产一个指定线程数量的线程池
2. 创建一个类，实现Runnable接口，重写run方法，设置线程任务
3. 调用ExecutorService中的方法submit ，传递线程任务（实现类），开启线程，执行run方法
4. 调用ExecutorService中的方法shutdown销毁线程池（不建议执行）

## 函数式表达式（JDK1.8)

只要能获取到结果，不在乎中间过程

格式：

```
(一些参数)->{代码}
```

（）接口中抽象方法的参数列表，没有参数，就空着；有参数就写出参数，多个参数使用逗号分隔

简化书写：

1. 小括号内参数的类型可以省略
2. 如果小括号内有且仅有一个参，则小括号可以省略
3. 如果大括号内有且仅有一个语句，无论是否有返回值，都可以省略大括号、return关键字机语句分号

## File类

### 构造方法

### 方法

1. 获取
   1. long length() 文件的大小，文件夹和无效文件都返回0
2. 判断
   1. exists() 是否存在
   2. isDirectory() 是否为目录
   3. isFile() 是否为文件
3. 删除和创建
   1. cerateNewFile() 创建一个新的空文件
   2. delete() 删除此File的文件或目录
   3. mkdir() 创建由此File表示的目录
   4. mkdirs() 创建由此File表示的目录,包括任何必须但不存在的父目录

### 目录遍历

1. String list()
   1. 
2. File[] listFiles()

注意:

1. list方法和listFiles方法遍历的是构造方法中给出的目录
2. 如果构造方法中给出的路径不存在或者不是一个目录，就会抛出空指针
3. 能够获取隐藏文件



## 递归

自己调用自己

注意事项：

1. 递归分位两类，直接递归和简介递归
2. 递归一定要油条剪子限定，能够保证递归停下来
3. 递归次数不能太多
4. 构造方法，禁止递归



## IO

### 字节流

java.io.OutputStream:字节输出流

定义了一些子类共性的成员方法：

- public void close():关闭此输出流并释放与此流相关联的任何系统资源
- public void flush():刷新此输出流并强制任何缓冲的输出字节被写出
- public void write(byte[] b)：将b.length字节从指定的字节数组写入此输出流
- public void write(byte[] b, int off,int len):从指定的字节数组写入len字节，从偏移量off开始输出到此输出流。
- public abstract void write(int b):将指定的字节输出流





java.io.FileOutputStream extends OutputStream

FileOutputStream:文件字节输出流

- 作用：把内存中的数据写入到硬盘的文件中

- 构造方法：
  - FileOutputStream(String name,boolean append)创建一个向具有指定名称的文件中写入数据的输出文件流
  - FileOutputStream(File file,boolean append)创建一个向指定File对象标识的文件中写入数据的文件输入流

#### 字节输出流的使用步骤：

1. 创建一个FileOutputStream对象,构造方法中传递写入数据的目的地
2. 调用FileOutputStream对象中的方法write,把数据写入到文件中
3. 释放资源

- 如果写的第一个自己是正数（0-127），那么显示的时候会查询ASCII表
- 如果写的第一个字节是负数，那么第一个字节和第二个字节，两个字节组成一个中文显示，查询系统默认码表（GBK）



#### 读取

java.io.InputStream:字节输入流

此抽象类是表示字节输入流的所有类的超类

定义了所有子类共性的方法：

​	int read() 从输入流中读取数据下一个字节

​	int read(byte[] b)从输入流中读取一定数量的字节，并将其存储在缓冲区数组b中

   void close() 关闭此输入流并释放与该流关联的所有系统资源。





java.io.FileInputStream extends InputStream

FileInputStream 文件自己输入流

构造方法：

### 字符流

java.io.Reade 字符输入流的超类，定义了一些公用的成员方法 

java.io.Writer 字符输出流的超类

### flush方法和close方法的区别

flush 刷新进去后还可以继续使用，close之后就不能继续使用了

### 异常处理

- 在jdk1.7之前使用try catch finally 处理流中的异常，需要将流对象提高作用域，但是又会带来空指针的问题

- 在jdk7中在try的后面可以增将一个(),在括号中可以定义一个流对象，那么这个流对象的作用域就在try中有效，try中的代码执行完毕，会自动把流对象释放，不用写finally。
- jdk9新特性 try 前面可以定义流对象 ，在try后面()中可以直接引入流对象的名称(变量名)

### Properties 集合

- 可以使用Properties集合中的方法store，把集合中的临时数据，持久化写入到硬盘中存储

- 可以使用Properties集合中的方法load，把硬盘中保存的文件(键值对),读取到集合中使用
- 

## 函数式接口

函数式接口在Java中是指：有且仅有一个抽象方法的接口。

只要确保接口中有且仅有一个抽象方法即可：

```java
修饰符 interface 接口名称 {
	public abstract 返回值类型 方法名称(可选参数信息);
		// 其他非抽象方法内容
}
```

由于接口当中抽象方法的public abstract 是可以省略的，所以定义一个函数式接口很简单：

```java
public interface MyFunctionalInterface {
	void myMethod();
}
```

### @FunctionalInterface注解

一旦使用该注解来定义接口，编译器将会强制检查该接口是否确实有且仅有一个抽象方法，否则将会报错。需要注
意的是，即使不使用该注解，只要满足函数式接口的定义，这仍然是一个函数式接口，使用起来都一样。

### 常用函数表达式接口

- Supplier接口

  - java.util.function.Supplier<T> 接口仅包含一个无参的方法： T get() 。用来获取一个泛型参数指定类型的对象数据。由于这是一个函数式接口，这也就意味着对应的Lambda表达式需要“对外提供”一个符合泛型类型的对象数据。
- Consumer接口

  - java.util.function.Consumer<T> 接口则正好与Supplier接口相反，它不是生产一个数据，而是消费一个数据，其数据类型由泛型决定。
  - Consumer 接口中包含抽象方法void accept(T t) ，意为消费一个指定泛型的数据
  - 如果一个方法的参数和返回值全都是Consumer 类型，那么就可以实现效果：消费数据的时候，首先做一个操作，然后再做一个操作，实现组合。而这个方法就是Consumer 接口中的default方法andThen 。
- Predicate接口

  - 有时候我们需要对某种类型的数据进行判断，从而得到一个boolean值结果。这时可以使用java.util.function.Predicate<T> 接口。
  - 抽象方法：test
  - 默认方法：and
    - 既然是条件判断，就会存在与、或、非三种常见的逻辑关系。其中将两个Predicate 条件使用“与”逻辑连接起来实现“并且”的效果时，可以使用default方法and 。
  - 默认方法：or
    - 与and 的“与”类似，默认方法or 实现逻辑关系中的“或”。
  - 默认方法：negate
    - 它是执行了test方法之后，对结果boolean值进行“!”取反
- Function接口
- 抽象方法：apply
    - Function 接口中最主要的抽象方法为： R apply(T t) ，根据类型T的参数获取类型R的结果。
  - 默认方法：andThen
    - Function 接口中有一个默认的andThen 方法，用来进行组合操作

## Stream流

#### 流式思想概述

当使用一个流的时候，通常包括三个基本步骤：获取一个数据源（source）→ 数据转换→执行操作获取想要的结
果，每次转换原有 Stream 对象不改变，返回一个新的 Stream 对象（可以有多次转换），这就允许对其操作可以
像链条一样排列，变成一个管道。

### 获取流

java.util.stream.Stream<T> 是Java 8新加入的最常用的流接口。（这并不是一个函数式接口。）
获取一个流非常简单，有以下几种常用的方式：

1. 所有的Collection 集合都可以通过stream 默认方法获取流；
2. Stream 接口的静态方法of 可以获取数组对应的流。

### 常用方法

方法可以被分成两种：

1. 延迟方法：返回值类型仍然是Stream 接口自身类型的方法，因此支持链式调用。（除了终结方法外，其余方法均为延迟方法。)
2. 终结方法：返回值类型不再是Stream 接口自身类型的方法，因此不再支持类似StringBuilder 那样的链式调用。本小节中，终结方法包括count 和forEach 方法。

- 逐一处理：forEach
  - void forEach(Consumer<? super T> action);
  - 该方法接收一个Consumer 接口函数，会将每一个流元素交给该函数进行处理。
- 过滤：filter
  - 可以通过filter 方法将一个流转换成另一个子集流。方法签名：Stream<T> filter(Predicate<? super T> predicate);
- 映射：map
  - 如果需要将流中的元素映射到另一个流中，可以使用map 方法。
  - <R> Stream<R> map(Function<? super T, ? extends R> mapper);
- 统计个数：count
  - long count();
  - 终结方法，不能再继续调用Stream流中的其他方法了
- 取用前几个：limit
  - Stream<T> limit(long maxSize);
- 跳过前几个：skip
  - Stream<T> skip(long n);
- 组合：concat
  - 如果有两个流，希望合并成为一个流，那么可以使用Stream 接口的静态方法concat ：
  - static <T> Stream<T> concat(Stream<? extends T> a, Stream<? extends T> b)

### 特点

- Stream流属于管道流，只能被消费（使用一次）
- 第一个Stream流调用完毕，数据就会流转到下一个Stream上，而这时第一个stream流已经关闭了

## 方法引用

通过对象名引用成员方法

- 前提是对象名是已经存在的，成员方法也是存在的就可以用对象名来引用成员方法

## Junit 单元测试

* 测试分类：
	1. 黑盒测试：不需要写代码，给输入值，看程序是否能够输出期望的值。
	2. 白盒测试：需要写代码的。关注程序具体的执行流程。

* Junit使用：白盒测试
	* 步骤：
		1. 定义一个测试类(测试用例)
			* 建议：
				* 测试类名：被测试的类名Test		CalculatorTest
				* 包名：xxx.xxx.xx.test		cn.itcast.test

		2. 定义测试方法：可以独立运行
			* 建议：
				* 方法名：test测试的方法名		testAdd()  
				* 返回值：void
				* 参数列表：空参

		3. 给方法加@Test
		4. 导入junit依赖环境

	* 判定结果：
		* 红色：失败
		* 绿色：成功
		* 一般我们会使用断言操作来处理结果
			* Assert.assertEquals(期望的结果,运算的结果);

	* 补充：
		* @Before:
			* 修饰的方法会在测试方法之前被自动执行
		* @After:
			* 修饰的方法会在测试方法执行之后自动被执行

## 反射

* 框架：半成品软件。可以在框架的基础上进行软件开发，简化编码
* 反射：将类的各个组成部分封装为其他对象，这就是反射机制
	* 好处：
		1. 可以在程序运行过程中，操作这些对象。
		2. 可以解耦，提高程序的可扩展性。

* 获取Class对象的方式：
	1. Class.forName("全类名")：将字节码文件加载进内存，返回Class对象
		* 多用于配置文件，将类名定义在配置文件中。读取文件，加载类
	2. 类名.class：通过类名的属性class获取
		* 多用于参数的传递
	3. 对象.getClass()：getClass()方法在Object类中定义着。
		* 多用于对象的获取字节码的方式

	* 结论：
		同一个字节码文件(*.class)在一次程序运行过程中，只会被加载一次，不论通过哪一种方式获取的Class对象都是同一个。

## 注解

* 定义：注解（Annotation），也叫元数据。一种代码级别的说明。它是JDK1.5及以后版本引入的一个特性，与类、接口、枚举是在同一个层次。它可以声明在包、类、字段、方法、局部变量、方法参数等的前面，用来对这些元素进行说明，注释。
* 概念描述：
	* JDK1.5之后的新特性
	* 说明程序的
	* 使用注解：@注解名称
* 作用分类：
  ①编写文档：通过代码里标识的注解生成文档【生成文档doc文档】
  ②代码分析：通过代码里标识的注解对代码进行分析【使用反射】
  ③编译检查：通过代码里标识的注解让编译器能够实现基本的编译检查【Override】

* JDK中预定义的一些注解
	* @Override	：检测被该注解标注的方法是否是继承自父类(接口)的
	* @Deprecated：该注解标注的内容，表示已过时
	* @SuppressWarnings：压制警告
		* 一般传递参数all  @SuppressWarnings("all")

* 自定义注解
	* 格式：
		元注解
		public @interface 注解名称{
			属性列表;
		}

	* 本质：==注解本质上就是一个接口，该接口默认继承Annotation接口==
		* public interface MyAnno extends java.lang.annotation.Annotation {}

	* 属性：接口中的抽象方法
		* 要求：
			1. 属性的返回值类型有下列取值
				* 基本数据类型
				* String
				* 枚举
				* 注解
				* 以上类型的数组

			2. 定义了属性，在使用时需要给属性赋值
				1. 如果定义属性时，使用default关键字给属性默认初始化值，则使用注解时，可以不进行属性的赋值。
				2. ==如果只有一个属性需要赋值，并且属性的名称是value，则value可以省略，直接定义值即可。==
				3. 数组赋值时，值使用{}包裹。如果数组中只有一个值，则{}可以省略
	
	* 元注解：用于描述注解的注解
		* @Target：描述注解能够作用的位置
			* ElementType取值：
				* TYPE：可以作用于类上
				* METHOD：可以作用于方法上
				* FIELD：可以作用于成员变量上
		* @Retention：描述注解被保留的阶段
			* @Retention(RetentionPolicy.RUNTIME)：当前被描述的注解，会保留到class字节码文件中，并被JVM读取到
		* @Documented：描述注解是否被抽取到api文档中
		* @Inherited：描述注解是否被子类继承

* 在程序使用(解析)注解：获取注解中定义的属性值
	1. 获取注解定义的位置的对象  （Class，Method,Field）
	2. 获取指定的注解
		* getAnnotation(Class)
		//其实就是在内存中生成了一个该注解接口的子类实现对象

	            public class ProImpl implements Pro{
	                public String className(){
	                    return "cn.itcast.annotation.Demo1";
	                }
	                public String methodName(){
	                    return "show";
	                }
	            }
	3. 调用注解中的抽象方法获取配置的属性值

