# Google Java Coding Style Guide - Google Java编程规范指南
# 目录
1. [简介](#1-简介)<br>
	1.1 [文档术语](#11-文档术语)<br>
	1.2 [指南声明](#12-指南声明)<br>
2. [源码文件基础守则](#2-源码文件基础守则)<br>
	2.1 [文件名](#21-文件名)<br>
	2.2 [文件编码：UTF-8](#22-文件编码：UTF-8)<br>
	2.3 [特殊字符](#23-特殊字符)<br>
		2.3.1 [白空格字符](#231-白空格字符(Whitespace characters))<br>
		2.3.2 [特殊转义序列](#232-特殊转义序列)<br>
		2.3.3 [非ASCII字符](#233-非ASCII字符)<br>
	
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
源码文件名由区分大小写的顶层类名(仅有1个//TODO 稍后添加链接)，和``.java``后缀构成。
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
<p class="tip">Tip：</p>
### 译注
<p id="comment1">[1]实现用注释是指：如<code>/* A comment */</code>或<code>// Another comment</code>。而文档用注释/Javadoc则是指<code>/** This is a javadoc */</code>。具体可以参看<a href="http://www.oracle.com/technetwork/java/javase/documentation/codeconventions-141999.html">Oracle的文档</a></p>
