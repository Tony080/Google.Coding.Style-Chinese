# Google Java Coding Style Guide - Google Java编程规范指南
译者：[Tony-Hu](https://github.com/Tony-Hu/)<br>
转载请注明出处。<br>
欢迎PR。 - Pull Request is welcomed!<br>
# 目录
1. [简介](#1-简介)<br>
1.1. [文档术语](#11-文档术语)<br>
1.2. [指南声明](#12-指南声明)<br>
2. [源码文件基础守则](#2-源码文件基础守则)<br>
2.1. [文件名](#21-文件名)<br>
2.2. [文件编码：UTF-8](#22-文件编码utf-8)<br>
2.3. [特殊字符](#23-特殊字符)<br>
2.3.1. [白空格字符](#231-白空格字符whitespace-characters)<br>
2.3.2. [特殊转义序列](#232-特殊转义序列)<br>
2.3.3. [非ASCII字符](#233-非ascii字符)<br>
3. [源文件结构](#3-源文件结构)<br>
3.1. [如果包含许可或版权信息，应显示](#31-如果包含许可或版权信息应显示)<br>
3.2. [所处的包的声明](#32-所处的包的声明)<br>
3.3. [导包声明](#33-导包声明)<br>
3.3.1. [禁止通配符导入](#331-禁止通配符导入)<br>
3.3.2. [不允许自动换行](#332-不允许自动换行)<br>
3.3.3. [顺序与空格](#333-顺序与空格)<br>
3.3.4. [禁止静态导入类](#334-禁止静态导入类)<br>
3.4. [类声明](#34-类声明)<br>
3.4.1. [有且仅有一个顶层类声明](#341-有且仅有一个顶层类声明)<br>
3.4.2. [类内容的顺序](#342-类内容的顺序)<br>
3.4.2.1. [重载：不要分割开](#3421-重载不要分割开)<br>
4. [格式](#4-格式)<br>
4.1. [大括号](#41-大括号)<br>
4.1.1. [可用可不用的时候必用大括号](#411-可用可不用的时候必用大括号)<br>
4.1.2. [非空语句块：使用K&R风格](#412-非空语句块使用kr风格)<br>
4.1.3. [空语句块：有可能被简化](#413-空语句块有可能被简化)<br>
4.2. [区块缩进：+2空格](#42-区块缩进2空格)<br>
4.3. [每行仅一条语句](#43-每行仅一条语句)<br>
4.4. [每行限制：100个字符](#44-每行限制100个字符)<br>
4.5. [换行](#45-换行)<br>
4.5.1. [在何处换行](#451-在何处换行)<br>

	//TODO

## 1. 简介
此文档旨在**完整**的定义Google对于Java源码的编程规范。当且仅当Java源码完全遵守本文档时，此源码才被称为Google风格(*Google Style*).<br>
<br>
与其他(Google)的编程规范一样，本文档不仅阐述了因审美引起的格式问题，同时也阐述了其他形式的公约以及编程标准。
但是，本文档仅专注于我们普遍遵守的**强制规范**(hard-and-fast rules)，并避免给出界定模糊的*建议*（对人或编译工具来说）。

### 1.1 文档术语
本文档中，除非特意指明，否则一般遵守下列表述：<br>
1. *类*(class)：指一个普通类，枚举类，接口或者注解(如``@interface``)
2. *成员*(memeber)：指嵌套类，类变量(field)，方法或构造函数。也即，除初始化函数(initializers)和注释外的所有类中的顶级内容。
3. *注释*(comment)：总是指*实现用*(implementation)注释<sup>[[1]](#comment1)</sup>。本文档使用更常用的短语"Javadoc"代替“文档用注释”(documentation comment)短语。<br>

其他文档术语将在本文档中陆续出现。
### 1.2 指南声明
本文档中的示例代码是**非规范化**(non-normative)的。即，示例代码是遵循Google风格的，但这并不表示这是*唯一*的表达方式。示例代码中可选的格式优化不应该被归于强制规范(，所以并未归入此文档中)。

## 2. 源码文件基础守则
### 2.1 文件名
源码文件名由区分大小写的顶层类名([仅有1个](#341-有且仅有一个顶层类声明))，和``.java``后缀构成。
### 2.2 文件编码：UTF-8
源码的编码格式为**UTF-8**。
### 2.3 特殊字符
#### 2.3.1 白空格字符(Whitespace characters)
除换行符外，**ASCII的横向空格字符(0x20)** 是在源码文件中唯一出现的白空格字符。这也就意味着：<br>
1. 所有其他的位于字符或字符串中的白空格字符应当转义。
2. 制表符(Tab)**不能**用于缩进。
#### 2.3.2 特殊转义序列
若任意字符中包含[特殊转义序列](http://docs.oracle.com/javase/tutorial/java/data/characters.html)(``\b``，``\t``，``\n``，``\f``，``\r``，``\"``，``\'``和``\\``)，则应直接使用该序列而非使用其八进制形式(如``\012``)或其Unicode转义(如``\u000a``)。
#### 2.3.3 非ASCII字符
对于余下的非ASCII字符，可使用实际Unicode字符(如``∞``)或等效Unicode转义(如``\u221e``)表示。尽管(本文档)强烈不推荐在字符串和注释外出现Unicode转义，(实际中)如何取舍仅取决于哪个更容易阅读和容易理解。<br>
*Tip：在使用Unicode转义，或直接使用Unicode字符时，添加解释性的注释会很有帮助。*<br>
示例：<br>
<table>
  <tbody><tr>
    <th>示例</th>
    <th>评论</th>
  </tr>

  <tr>
    <td><code class="prettyprint lang-java prettyprinted" style=""><span class="typ">String</span><span class="pln"> unitAbbrev </span><span class="pun">=</span><span class="pln"> </span><span class="str">"μs"</span><span class="pun">;</span></code></td>
    <td>最佳：无需注释也很清晰明了。</td>
  </tr>

  <tr>
    <td><code class="prettyprint lang-java prettyprinted" style=""><span class="typ">String</span><span class="pln"> unitAbbrev </span><span class="pun">=</span><span class="pln"> </span><span class="str">"\u03bcs"</span><span class="pun">;</span><span class="pln"> </span><span class="com">// "μs"</span></code></td>
    <td>可行，但是没有理由这样做。</td>
  </tr>

  <tr>
    <td><code class="prettyprint lang-java prettyprinted" style=""><span class="typ">String</span><span class="pln"> unitAbbrev </span><span class="pun">=</span><span class="pln"> </span><span class="str">"\u03bcs"</span><span class="pun">;</span><span class="pln"> </span><span class="com">// Greek letter mu, "s"</span></code></td>
    <td>可行，但是很别扭，而且容易出错。</td>
  </tr>

  <tr>
    <td><code class="badcode">String unitAbbrev = "\u03bcs";</code></td>
    <td>较差：读代码的人不知道这是什么。</td>
  </tr>

  <tr>
     <td><code class="prettyprint lang-java prettyprinted" style=""><span class="kwd">return</span><span class="pln"> </span><span class="str">'\ufeff'</span><span class="pln"> </span><span class="pun">+</span><span class="pln"> content</span><span class="pun">;</span><span class="pln"> </span><span class="com">// byte order mark</span></code></td>
     <td>好：对不可打印的字符使用转义，并进行必要的注释。</td>
  </tr>
</tbody></table>

***Tip**：永远不要因为害怕程序不能正确处理非ASCII字符而降低源码可读性。如果程序未能正确处理非ASCII字符，那么该程序是**损坏的**并应着手**修复***。<br>
## 3. 源文件结构
一个源文件应**按照顺序**，包含以下内容：<br>
1. 如果包含许可或版权信息，应显示<br>
2. 所处的包的声明(Package statement)<br>
3. 导包声明(import statements)<br>
4. 有且仅有1个顶层的类<br>

**仅使用一个空行**去分割以上出现的内容。

### 3.1 如果包含许可或版权信息，应显示
若文件中包含许可或版权信息，应在此处显示。<br>
### 3.2 所处的包的声明
所处的包声明**不允许自动换行**。该声明不受每行字符限制(见4.4，每行限制100个字符)。<br>
### 3.3 导包声明
#### 3.3.1 禁止通配符导入
(Google Style)**不使用通配符导入**，无论是在静态导入中，或其他(非静态)导入。<br>
#### 3.3.2 不允许自动换行
导包声明**不允许自动换行**。该声明不受每行字符限制(见4.4，每行限制100个字符)。<br>
#### 3.3.3 顺序与空格
导入顺序遵循以下原则：
1. 所有静态导入在同一区块<br>
2. 所有非静态导入在同一区块<br>

如果静态导入和非静态导入同时出现，使用一个空行分割两个区块。其他导包声明之间无空格。<br>
每个区块的导包语句按照名字的ASCII顺序排序。(**注意**：这并不意味着整个导包语句都按照ASCII顺序排序，因为(在ASCII表中)'.'出现在';'前)<br>
#### 3.3.4 禁止静态导入类
静态导入不可用于静态嵌套类。静态嵌套类由普通导入语句导入。
### 3.4 类声明
#### 3.4.1 有且仅有一个顶层类声明
每个顶层类都处在(以他类命名的)源文件顶层。<br>
#### 3.4.2 类内容的顺序
如何排列你的类成员与初始化函数是一件很容易学习的事情。但是，排列的方法不止一种；不同的类有不同的内容排序方法。<br>
重要的是，每个类都应使用**某种逻辑排序**，这样代码维护者在被(审阅代码时)问到的话就可以有充足的理由解释清楚。例如，新的方法不仅仅处于习惯性的放在类的末尾，放在末尾意味着此种顺序产生了“按日期添加”的非逻辑排序。
##### 3.4.2.1 重载：不要分割开
当一个类有多个构造函数，或多个方法重名时，他们应该一个接一个的挨个卸下来，中间不能有任何其他代码(private方法也不行)。
# 4. 格式
**文档术语**：*块状结构*(block-like constructs)指类的主体，方法或构造函数。注意，在4.8.3.1节 数组初始化声明(array initializers)中，数组初始化声明可以被选择性的视为块状结构。
## 4.1 大括号
### 4.1.1 可用可不用的时候必用大括号
在``if``, ``else``, ``for``, ``do``和``while``语句中，即便无内部语句或只有一句，也必须使用大括号。
### 4.1.2 非空语句块：使用K&R风格
对于*非空*语句块和块状结构，使用Kernighan and Ritchie风格([埃及括号(Egyptian brackets)](http://www.codinghorror.com/blog/2012/07/new-programming-jargon.html))的大括号：
- 左大括号前不换行。
- 左大括号后换行。
- 右大括号前换行。
- 仅当结束一段声明、函数、构造函数、非匿名类时，右大括号后才换行。比如，当右大括号后有``else``或逗号时，右大括号后就不换行。<br>
例子：
```java
return () -> {
  while (condition()) {
    method();
  }
};

return new MyClass() {
  @Override public void method() {
    if (condition()) {
      try {
        something();
      } catch (ProblemException e) {
        recover();
      }
    } else if (otherCondition()) {
      somethingElse();
    } else {
      lastThing();
    }
  }
};
```
枚举类有几个例外，详情参见4.8.1节 枚举类
### 4.1.3 空语句块：有可能被简化
空语句块或块状结构可以使用K&R风格(在4.1.2节中)、除此之外，**除非**该空语句块是多段语句块的一部分(如``if/else``或``try/catch/finally``)，空语句块的左右大括号也可以不加字符，不加换行的紧挨在一起(``{}``)。<br>
例子：
```java
  // 可以接受
  void doNothing() {}

  // 同样可以接受
  void doNothingElse() {
  }
```
```java
  // 不可接受：多段语句块中不允许存在简化过的空语句块
  try {
    doSomething();
  } catch (Exception e) {}
```
## 4.2 区块缩进：+2空格
每当新增一个新的区块或块状结构时，缩进+2空格。当该区块结束后，缩进回到之前的缩进水平(即-2空格)。缩进区域对于所处区块的所有代码和注释都均适用。(见4.1.2节 [非空语句块：使用K&R风格](#412-非空语句块使用kr风格))
## 4.3 每行仅一条语句
每个语句结束后都应换行。
## 4.4 每行限制：100个字符
Java源码每行限制100个字符。“字符”是指任何一个Unicode码位。除以下特殊情况外，任何一行超过了(100个字符后)都必须换行，详情参见4.5节 换行。
*每个Unicode码位算作一个字符，无论该字符显示出来(相较一般)更宽或更窄。例如，如果使用[全角字符](https://en.wikipedia.org/wiki/Halfwidth_and_fullwidth_forms)，你可能需要在到达100个字符限制前提早换行。*<br>
**例外**：<br>
1. 当情况不允许时(例如，Javadoc中出现的长URL，或者一个很长的JSNI(JavaScript Native Interface)方法引用)。
2. ``package``和``import``声明(见3.2节 [所处包的声明](#32-所处的包的声明)和3.3节 [导包声明](#33-导包声明))。
3. 注释中可能需要粘贴到shell中的命令。
## 4.5 换行
**文档术语**：当代码可以合法占据一行，但却分割成若干行时，此行为成为*换行*。<br>
并没有全面的，确定性的公式定义每种情况下如何*准确*的换行。很多情况下，对于同一行代码，都会存在若干种合理的分割方法。<br>
***注意**：尽管一般情况下换行是为了防止超出每行的字符限制，但有时候尽管并未超出此限制，作者也会处于谨慎将代码分割成多行。*<br>
***Tip**：(将原本的代码块)提炼成一个方法或一个局部变量可免除换行的苦恼。*<br>
### 4.5.1 在何处换行
### 译注
<p id="comment1"><a href="#11-文档术语">[1]</a>实现用注释是指：如<code>/* A comment */</code>或<code>// Another comment</code>。而文档用注释/Javadoc则是指<code>/** This is a javadoc */</code>。具体可以参看<a href="http://www.oracle.com/technetwork/java/javase/documentation/codeconventions-141999.html">Oracle的文档</a></p>
