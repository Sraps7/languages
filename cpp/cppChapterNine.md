## Chapter Nine

#### 特殊成员函数
C++ 自动提供下面这些成员函数：
1. 默认构造函数， 如果没有定义构造函数
2. 默认析构函数， 如果没有定义
3. 复制构造函数， 如果没有定义
4. 赋值运算符， 如果没有定义
5. 地址运算符， 如果没有定义
> 更准确地说，编译器将生成上述最后三个函数的定义——如果程序使用对象的方式要求这样做：例如，如果将一个对象赋给另一个对象，编译器将提供赋值运算符的定义。
> 隐式地址运算符返回调用对象的地址，即this指针的值。
> **此外**，C++11 提供了另外两个特殊成员函数：移动构造函数和移动赋值运算符，这将在之后进行介绍。


