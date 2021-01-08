## Chapter Eight

#### 运算符重载
```cpp
operatorop(argument-list)
operator+()
operator*()
```

> 运算符左侧的对象是调用对象，运算符右侧的对象是作为参数被传递的对象。

#### 自定义类型转换
在C++ 中，接受一个参数的构造函数为将类型与该参数相同的值转换为类提供了蓝图。
下面的构造函数用于将double类型的值转换为自定义Stonewt类型：
```cpp
Stonewt(double lbs);  // template for double-to-Stonewt conversion

Stonewt myCat;  // create a Stonewt object
myCat = 19.6;   // use Stonewt(double) to convert 19.6 to Stonewt
```

> 只有接受一个参数的构造函数才能作为转换函数。
> **然而：**如果第二个参数提供默认值，也可以作为转换函数。

```cpp
Stonewt(int stn, double lbs = 0);  // int-to-Stonewt conversion
```

##### explicit
> 注：
> 将构造函数用于自动类型转换似乎是一项不错的特性，然而，并非总是合乎需要的，有时候会导致意外的转换。
> 因此，C++ 新增了关键字`explicit`，用于关闭这种自动特性
```cpp
explicit Stonewt(double lbs);
```
> 这将关闭上述示例中介绍的隐式转换，但仍然允许显示转换，即强制类型转换。

#### 类型转换函数
```cpp
operator typeName();
```
* 转换函数必须是类方法
* 转换函数不能指定返回类型
* 转换函数不能有参数

例如，转换为double类型的函数的原型如下：
```cpp
operator double();
```

#### C++ 11
在C++ 98 中，关键字explicit 不能用于转换函数，但在C++11 中消除了这种限制，因此，在C++ 11 中，可将转换运算符神明为显式的：
```cpp
class Stonewt
{
    ...
    // conversion functions
    explicit operator int() const;
    explicit operator double() const;
}
```
