# Google CPP Coding Style Guide - Google C++编程规范指南
译者：[Emily-Tang](https://github.com/Emilylulu)<br>
转载请注明出处。<br>
欢迎PR。 - Pull Request is welcomed!<br>
# 目录
[背景](#1-背景)<br>
1. [头文件](#1-头文件)<br>
1.1 [Self-contained 头文件](#)<br>
1.2 [``#define`` 保护](#12)<br>
1.3 [前置声明(Forward Declarations)](#13)<br>
1.4 [内联函数(inline function)](#14)<br>
## 1. 头文件
总的来说，每一个``.cc``文件都会有一个相关联的``.h``文件。但还是有些常见的例外，比如，单元测试代码和只包含main()函数的``.cc``文件。
正确使用头文件可以使代码在可读性、文件大小和性能上大大提升。
下面的规则可以引导你规避使用头文件时遇到的陷阱。
### 1.1 Self-contained 头文件

