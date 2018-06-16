# Google Java Coding Style
# 目录
//TODO

## 1. 简介
此文档旨在**完整**的定义Google对于Java源码的编程规范。当且仅当Java源码完全遵守本文档时，此源码才被称为Google风格(*Google Style*).<br>
<br>
与其他（Google）的编程规范一样，本文档不仅阐述了因审美引起的格式问题，同时也阐述了其他形式的公约以及编程标准。
但是，本文档仅专注于我们普遍遵守的**强制规范**(hard-and-fast rules)，并避免给出界定模糊的*建议*（对人或编译工具来说）。

### 1.1 文档术语
本文档中，除非特意指明，否则一般遵守下列表述：<br>
1. *类*(class)：指一个普通类，枚举类，接口或者注解（如``@interface``）
2. *成员*（memeber）：指嵌套类，类变量(field)，方法或构造函数。也即，除初始化函数(initializers)和注释外的所有类中的顶级内容。
3. *注释*（comment）：总是指*实现用*(implementation)注释<sup>[1]</sup>。本文档使用更常用的短语"Javadoc"代替“文档用注释”(documentation comment)短语。