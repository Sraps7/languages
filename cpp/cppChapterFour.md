## Chapter Four
****

通常，cout在显示bool值之前将它们转换为int，但`cout.setf(ios::boolahpha)`函数调用设置了一个标记，该标记命令cout显示true和false，而不是1和0.


##### 类型别名
C++为类型建立别名有两种方式：
* 使用预处理器
  ```cpp
  #define BYTE char     // preprocessor replaces BYTE with char
  ```
* 使用关键字typedef
  ```cpp
  typedef typeName aliasName;
  ```
> 通常，使用typedef更好

#### 函数
* 无返回值的函数
* 有返回值的函数
  
##### 无返回值的函数
```cpp
void functionName(parameterList)
{
    statement(s);
    return;         //optional
}
```

##### 有返回值的函数
```cpp
typeName functionName(parameterList)
{
    statement(s);
    return value;         // value is a type cast to type typeName
}
```
> C++ 对函数返回类型有一定的限制：
> **不能是数组**
> 但可以是其他任何类型：整数、浮点数、指针，甚至是结构或对象
> 可以把数组作为结构或对象的组成部分来返回

##### 函数原型
* 函数原型是一条语句，必须以分号结束
* 函数原型不要求提供变量名，有类型列表就足够了：
  ```cpp
  void cheers(int);
  ```
* 原型中的变量名相当于占位符，因此不必与函数定义中的变量名相同
* 括号为空与在括号内使用关键字void是等效的——意味着函数没有参数
* 如果不想指定参数列表，应当使用省略号，通常，仅当与接受可变参数的C函数（如printf）交互时才需要这样做：
  ```cpp
  void sya_bye(...);    // C++ abdication of responsibility
  ```

#### 指针与const
有两种方式将const用于指针：
* 指针指向一个常量对象，防止使用该指针修改所指向的值
* 将指针本身声明为常量，防止改变指针指向的位置

##### 指针指向一个常量对象
```cpp
int age = 39;
const int * pt = &age;
```
pt指向一个const int，因此不能使用pt来修改这个值
> 这是一件有点微妙的事情，pt的声明并不意味着它指向的值时间上真的是一个**常量**
> 而只是对pt而言，这个值是常量，我们可以直接通过变量名age来修改age的值，但是不能使用pt指针来修改它：
> ```cpp
> *pt = 20;    // INVALID
> age = 20;    // VALID
> ```

##### 指针的指向不可被修改
```cpp
int sloth = 3;
int * const finger = &sloth;     // a const pointer to int
```

> 通常，将指针作为函数参数来传递时，可以使用指向const的指针来保护数据：
> ```cpp
> void show_array(const double ar[], int n);
> ```
> 在该声明中，使用const意味着show_array()不能修改传递给它的数组中的值
> **只要只有一层间接关系，就可以使用这种技术**
> **但是，如果是指向指针的指针，则不能使用const**
> ```cpp
> const int** pp2;
> int* p1;
> pp2 = &p1;         // NOT ALLOWED
> ```

#### 函数指针
函数名本身即为函数的地址

##### 声明函数指针
假设现在有一个函数：
```cpp
double pam(int);  // prototype
```
对应的函数指针声明如下：
```cpp
double (*pf)(int);   // pf points to a function that takes one int argument and
                     // that returns type double
```
这与pam()声明类似，只是将pam替换成了(*pf)。由于pam是函数，因此(*pf)也是函数。
而如果(*pf)是函数，则pf就是函数指针

> **注意**：
> *pf必须用括号括起来。括号的优先级比`*`运算符高
> `*pf(int)`意味着pf()是一个返回值真的函数，而`(*pf)(int)`意味着pf是一个指向函数的指针：
> ```cpp
> double (*pf)(int);   // pf points to a function
> double *pf(int);     // pf() is a function
> ```

> 函数指针调用函数时，支持如下两种写法：
> ```cpp
> (*pf)(argument);
> pf(argument);
> ```
> 事实上，C++支持如下调用函数：
> ```cpp
> (*pam)(argument);
> ```




