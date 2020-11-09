# 模板总结
2020.11.9

1.函数重载的缺点：（1）重载的函数仅仅只是类型不同，代码的复用率包低，只要有新类型出现时，就需要增加相对应的函数

（2）代码的可维护性比较低，一个出现错误肯会导致所有的重载都会存在问题

由于函数重载存在的问题，引出了泛型编程

2.泛型编程：是指编写与类型无关的通用代码，时代码复用的一种手段，模板时泛型编程的基础

3.模板分为函数模板和类模板

4.函数模板：函数模板不是真正的函数，而是告诉给编译器生产代码的规则，函数模板代表了一个函数家族，该函数模板与其类型无关，在使用时被参数化，会根据实参类型产生特定的类型版本

5.函数模板的格式：template<typename /class T1，typename/class T2,.................,typename/class Tn>

注意：typename是用来定义模板参数关键字，也可以使用class，但是不能使用struct来代替class

6.函数模板的实例化：用不同类型的参数使用函数模板时，称其为模板的实例化

7.模板实例化分为：隐式实例化换热显式实例化

8.隐式实例化：让编译器根据实参推演模板参数的实际类型

注意：（1）当模板参数列表中只有一个T时，当你定义了两个类型不同的实参式就会发生编译错误，因为编译器无法确定此处到底该将T定义为哪种类型

解决方法：1.用户自己来进行强制转化 ，如add（a,int (b)）//将b类型强转为int

2.使用显式实例化

（2）在模板中，编译器一般不会进行类型的转换操作，因为一旦出现问题，编译器就会背锅

9.显式实例化：在函数名后加<T>,其中T为指定模板参数的实际类型，如add<int >(a,b),如果类型不匹配的话编译器会尝试进行隐式类型转换，如果无法转化成功编译器会报错

10.一个非模板函数可以和一个同名的函数模板同时存在，而且该函数模板还可以被实例化为这个非模板函数

11.对于非模板函数和同名函数模板，如果其他条件都相同，在调动时会优先调用非模板函数而不会从该模板产生出一个实例，如果模板可以产生一个具有更好匹配的函数，那么将选择模板

11.模板函数不允许自动类型的转化，但普通函数可以进行自动类型转换

12.类模板的定义格式：template<class T1，class T2,.................,class Tn>

13.注意：类模板中函数放在类外进行定义时，需要加模板参数列表

14. 类模板的实例化：类模板实例化与函数模板实例化不同，类模板实例化需要在类模板名字后跟<>然后将实例化的类型放在<>，类模板名字不是真正的类，而实例化的结果才是真正的类，如vector<int> s1//vector是类名，vector<int>才是类型
