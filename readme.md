1. vector<vector<int>> ans<m, vector<int> n>;

2. string s; char c = s.charAt(i); auto ch = s[i];

3. 哈希表 unordered_map<int, int> map;

4. set容器unordered_set<int> set;

5. set.count(num)成员num的数量

6. vector容器vector<int> vec;

7. const修饰指针，常量指针const int *可以修改指针的指向，不可以修改指针的值，指针常量int * const可以修改指针的值，不可以修改指针的指向，常量指针常量const int * const不可以修改指针的指向和值

8. 

9. 代码区，全局区，栈区，堆区：

10. 代码区：共享，只读，存放二进制代码，由操作系统管理

11. 全局区：全局变量，静态变量，常量（const修饰全局变量和字符串常量），由操作系统释放

12. 栈区：局部变量，形参，由编译器管理开辟和释放，不要返回局部变量地址，栈区数据在函数执行完自动释放

13. 堆区：由程序员管理开辟和释放，程序员不释放操作系统释放，利用new关键字开辟内存，delete释放内存，new返回数据类型的指针，int * a = new int(10); delete a; int* b = new int[10]; delete[] b;

14. 函数体内变量为局部变量，函数体外变量为全局变量，static静态变量，双引号为字符串常量，const修饰全局变量为全局常量，const修饰局部变量为局部常量

15. 

16. 引用：给变量起别名 int a = 0; int &b = a;不可以int &b;

17. 引用一旦初始化不可以修改int a=0; int c=0; int &b=a; 不可以int &b=c; 但可以赋值int b=c;

18. 引用做函数形参，实参同形参一起变化，引用传递，地址传递，值传递

19. 不要返回局部变量的引用

20. 函数的调用可以作为左值，这里是说函数内定义静态变量，然后返回静态变量的引用，此时函数可以被赋值，即int &a = test(); test() = 10;此时a==10

21. 引用的本质是指针常量，即int& a=b;等价于int* const a = &b;

22. 常量引用，用来修饰形参，防止误操作，可以const int& a=10;

23. 

24. 函数默认参数，形参如果有默认值，这个位置从左到右都必须有默认值，此时实参可以传可以不传

25. 函数声明和实现只能有一个有默认参数

26. 函数占位参数void test(int a, int)，占位参数可以有默认参数void test(int a, int = 10)

27. 函数重载：可以让函数名相同，提高复用性

28. 函数重载满足条件：1、同一作用域下（都在main函数外，全局作用域），2、函数名称相同，3、参数类型不同，个数不同或顺序不同。传入参数不同调用不同

29. 返回值类型不同不可以作为函数重载条件

30. 函数重装注意事项：1、引用作为重载条件，变量做实参，调用int &a这样的形参，常量作为形参，调用const int &a这样的形参 2、函数重载碰到默认参数，出现二义性（歧义），应避免这种情况，即实参可以传到两个不同的函数中

31. 

32. 封装，继承和多态

33. 类和对象，万物皆对象，对象有属性和行为

34. 封装意义：1、将属性和行为作为**整体**。2、将属性和行为加以**权限**控制

35. 类的属性即成员属性或成员变量，通过类的对象访问(对象.成员变量)

36. 类的行为即成员方法或成员函数，通过类的对象访问(对象.成员函数)

37. 类的访问权限：

38. 公共权限public，类外类内都可以访问

39. 保护权限protected，类内可以访问，类外不可以访问

40. 私有权限private，类内可以访问，类外不可以访问（默认private）

41. struct和class默认访问权限不同，struct默认为公共权限，class默认为私有权限

42. 成员属性权限设置为私有，可以自己控制读和写，对于写权限，我们可以检测数据有效性

43. 在类中可以让另一个类作为成员函数

44. #pragma once防止头文件重复包含

45. 构造函数和析构函数：

46. 构造函数用于成员属性赋值和初始化。没有返回值也不写void。函数名与类名相同。构造函数可以有参数，因此可以发生重载。

47. 析构函数用于对象销毁。没有返回值也不写void。函数名与类名相同，在名称前加~。析构函数不可以有参数，因此不可以发生重载。

48. 构造和析构都是必须有的实现，如果我们不提供，编译器会提供一个空实现的构造和析构。

49. 无参构造，有参构造，拷贝构造，拷贝构造函数的参数为常量引用即 const Person & p

50. **括号法**：Person p1; //默认或者无参构造函数 Person p2(10); //有参构造函数 Person p3(p2); //拷贝构造函数

51. 不要用括号法进行无参构造，Person p(); 否则编译器识别为函数声明

52. **显示法**：Person p1; //默认或者无参构造函数 Person p2=Person(10); //有参构造函数 Person p2=Person(p2); //拷贝构造函数

53. 匿名对象即Person(10)，执行完系统回收匿名对象，不要用拷贝构造函数初始化匿名对象

54. **隐式转换法**：Person p2 = 10; //有参构造 Person p3 = p2; //拷贝构造

55. 拷贝构造函数调用时机：1、使用创建好的对象初始化新对象；2、值传递给函数参数传值；3、值方式返回局部对象

56. 如果用户不定义，c++提供默认构造，有参构造和拷贝构造（值拷贝）

57. 如果用户定义有参构造，c++不再提供无参构造但是会提供默认拷贝构造

58. 如果用户定义拷贝构造，c++不再提供其他构造

59. 深拷贝与浅拷贝：浅拷贝：简单的拷贝，使用编译器默认的拷贝构造实现浅拷贝，深拷贝：在堆区申请空间拷贝

60. 析构函数作用，将堆区开辟的数据释放，为避免野指针，将指针指向空

61. 浅拷贝带来的问题是堆区的内存重复释放，用深拷贝解决，自己实现拷贝构造函数，在堆区申请空间拷贝，而不是编译器默认的拷贝构造函数来拷贝

62. 初始化列表：构造函数Person(int a, int b) : a1(a), b1(b), c1(c) {}

63. 当其他类对象作为本类成员，先构造其他类对象，析构相反

64. 静态成员函数通过对象访问或类名访问，Person p; p.func(); Person::func(); 所有对象共享同一个函数

65. 静态成员函数只能访问静态成员变量，静态成员变量要在类内声明static int a; 类外初始化int Person::a; 静态成员函数同样有访问权限

66. 成员变量和成员函数分开存储

67. 空对象占用空间内存为1字节，为了区分空对象占内存的位置

68. 非静态成员变量属于类对象上，静态成员变量不属于类对象上，非静态成员函数和静态成员函数不属于类对象上

69. this指针指向被调用的成员函数所属的对象，隐含在每一个非静态成员函数中，用途：1、当形参和成员变量同名时，可用this指针区分 2、在类的非静态成员函数中返回对象本身，可使用return *this，链式编程思想

70. this指针的本质时指针常量，指针指向不可以修改，值可以修改，类似引用

71. 空指针访问成员函数：应注意成员函数中是否有成员变量，如果有成员变量，应在成员变量前加入if(this == NULL) return;

72. 常函数：成员函数后加const，常函数内不可以修改成员属性，声明成员属性时加mutable关键字后可以修改

73. 常对象：声明对象前加const，只能调用常函数

74. 成员函数后加const本质是使this指针指向的值也不可以修改

75. 友元是为了让函数或类访问另一个类中的私有成员

76. 全局函数做友元：全局函数中放到类里面，并在前面加friend

77. 类做友元：当前类放到被访问私有成员的类中，并在前面加friend

78. 类外写成员函数和成员变量，即类：：成员，new什么样的数据类型，就返回什么样数据类型的指针

79. 成员函数做友元：当前类成员函数放到被访问私有成员的类中，并在前面加当前类名和friend即friend 当前类名：：成员函数

80. 运算符重载：实现自定义数据类型相加，operator+运算符，可以由成员函数重载和全局函数重载，运算符重载也可以发生函数重载

81. ```c++
    class Person{
    public:
        Person operator+(person &p){
            Person temp;
            temp->a = this->a + p->a;
            return temp;
        }//成员函数重载
        int a;
    }
    Person operator+(person &p1, person &p2){
        Person temp;
        temp->a = p1->a + p2->a;
        return temp;
    }//全局函数重载
    Person p1;
    Person p2;
    Person p3;
    p3= p1 + p2;//等价于p3 = p1.operator+(p2);
    ```

82. 左移运算符重载：全局函数重载，重载左移运算符配合友元可以实现自定义数据类型

83. ```c++
    class Person{
    public:
        int a;
    }
    ostream& operator<<(ostream& cout, person &p){
    	cout << p.a << " " << p.b;
        return cout;
    }//左移运算符重载
    Person p;
    p.a = 1;
    p.b = 2;
    cout << p << endl;
    ```

84. 递增运算符重载：前置递增返回引用，后置递增返回值

85. 赋值运算符重载：编译器提供浅拷贝的赋值，我们采用赋值运算符重载，先判断是否有属性在堆区，如果有先释放，然后自己开辟空间进行拷贝，返回对象自身*this

86. 关系运算符重载：对两个自定义数据类型比大小

87. 函数调用运算符重载：仿函数

88. ```c++
    class MyPrint()
    {
    Public:
    	void operator()(string test)
    	{
    		cout << test << endl;
    	}
    }
    class MyAdd()
    {
    public:
    	int operator()(int a, int b) //仿函数很灵活，参数和返回类型都可以不同
    	{
    		return a + b;
    	}
    }
    MyPrint myPrint;
    myPrint("hello world!");//重载了小括号之后，让对象使用重载后的小括号，使用起来类似函数调用，称为仿函数
    MyAdd myadd;
    int ans = myadd(100, 100);
    //匿名函数对象MyAdd()(100, 100)
    cout << MyAdd()(100, 100) << endl;//MyAdd()为匿名对象，当前行执行完立即被释放，后面小括号使用的是重载函数调用运算符
    ```

89. 父类中所有非静态成员属性都会被子类继承下去，包括私有属性

90. 父类和子类构造顺序：父类先构造，子类后构造，析构相反

91. 访问父类同名成员需要在成员前加作用域，子类不用

92. 继承同名静态成员：通过类名访问：Son::Base::m_A; 通过对象访问Son a; a.Base::m_A;

93. 一个类可以继承多个类，不建议使用，父类中出现同名成员，加作用域区分

94. 菱形继承：两个派生类继承同一个基类，某个类继承两个派生类，菱形继承导致数据两份，资源浪费，利用虚继承解决菱形继承 class Sheep :virtual public Animal {}; Animal类变成虚基类，孙子类只继承一份数据，两个派生类继承两个虚基类指针vbstr，指向虚基类表格vbtable，通过偏移量相加得到同一个数据

95. 多态：静态多态：函数重载和运算符重载 动态多态：派生类和虚函数实现运行时多态

96. 地址早绑定：编译阶段确定函数地址，在基类的成员函数前加virtual 为虚函数，实现地址晚绑定：在运行阶段确定函数地址

97. 动态多态满足条件：1、有继承关系 2、子类重写（返回类型，函数名，参数都相同）父类虚函数

98. 动态多态使用：父类的指针或者引用指向子类对象

99. 动态多态原理：虚函数指针指向虚函数表，虚函数表记录虚函数入口地址，当子类重写父类虚函数，虚函数表记录子类虚函数入口地址，当父类指针或引用指向子类对象时，发生多态，实现子类函数的调用

100. 多态优点：1、代码组织结构清晰，2、可读性强，3、利于前期和后期拓展与维护

101. 开闭原则：对扩展开放，对修改关闭

102. 在多态中，父类虚函数无意义，重在子类重写的内容，因此可以将虚函数改为纯虚函数 virtual 返回类型 函数名(参数) = 0

103. 当类中有纯虚函数，这个类也称抽象类，抽象类特点：1、无法实例化对象，2、子类必须重写抽象类纯虚函数，否则也为抽象类

104. 父类名 * 指针名 = new 子类名，在堆区开辟了内存，创建了父类指针指向子类对象

105. 虚析构和纯虚析构，都可以解决父类指针释放子类对象时释放不干净的问题，都需要具体函数实现，如果纯虚析构，该类属于抽象类，无法实例化对象

106. 父类指针指向子类对象，delete父类指针时，不会走子类析构函数，子类创建在堆区数据无法释放，造成内存泄漏，解决方法在父类析构函数前加virtual变成虚析构，在后面加=0变成纯虚析构，但需要代码实现，类内声明，在类外实现

107. 

108. 文本操作：文本文件，二进制文件

109. ofstream写操作、ifstream读操作、fstream读写操作

110. 1、包含头文件#include<fstream> 2、创建流对象 oftream ofs; 3、打开文件ofs.open("文件路径"，打开方式); 4、写数据ofs<<"写入的数据"; 5、关闭文件ofs.close();

111. 打开方式：1、ios::in读文件 2、ios::out写文件 3、ios::ate文件尾读文件 4、ios::app文件尾写文件 5、ios::trunc先删除，再创建 6、ios::binary二进制方式 7、二进制写文件ios::binary | ios::in

112. 

113. 泛型编程和STL技术

114. 模板：函数模板（建立一个通用函数，返回类型和参数用虚拟类型T代表）和类模板

115. ```c++
     template<typename T> //template声明创建模板，typename表面后面是数据类型，可用class，T通用数据类型，通常为大写字母
     //函数声明或定义
     mySwap(a,b);//自动类型推导
     mySwap<int>(a,b)//显示指定类型
     ```

116. 函数模板注意事项：1、自动类型推导，必须推导一致数据类型T 2、模板必须确定T数据类型

117. 普通函数和函数模板：1、普通函数调用时可以发生隐式类型转换 2、函数模板使用自动类型推导不会发生隐式类型转换 3、函数模板用显示指定类型，可以发生隐式类型转换（隐式类型转换：把char字符的ascii码值自动转成int）

118. 普通函数和函数模板调用规则：1、优先调用普通函数 2、强制调用函数模板，使用空模板参数列表，即函数名<>(参数) 3、函数模板可以发生重载 4、如果函数模板可以更好的匹配（普通函数需要隐式类型转换时），优先调用函数模板。普通函数和函数模板尽量不要同时出现

119. 某些特定数据类型，需要具体化方式做特殊实现，1、运算符重载 2、具体化Person实现代码，即template<> 返回类型 函数名(参数类型 参数名)，当数据类型为Person时指向这个函数，否则自动类型推导

120. 学习模板是为了在STL中运用系统提供的模板

121. 类模板：template<class NameType, class AgeType>，后面紧跟类

122. 类模板与函数模板区别：1、类模板没有自动类型推导Person p(“孙悟空”， 1000); 会报错，只能用显示指定类型Person<string,int> p(“孙悟空”， 1000); 2、类模板在模板参数列表中可以有默认参数template<class NameType, class AgeType=int>

123. 普通类成员函数一开始创建，类模板成员函数在调用时创建（即用T表示类来创建对象），类1中，T  类2对象; 类1外，类1名<类2名> 类1对象;

124. 类模板对象做函数参数：Person<string,int> p(“孙悟空”， 1000); 

125. 1、指定传入类型：直接显示对象数据类型，传入函数参数的时候Person<string,int>& p，最常用

126. 2、参数模板化：将对象中的参数作为模板来传递 ，传入函数参数的时候Person<T1, T2>& p 

127. 3、整个类模板化：将这个对象类型模板化传递，传入函数参数的时候T& p 

128. 类模板与继承：父类是类模板的时候，子类在声明时，要指出父类T的类型，否则编译器无法分配内存，要想灵活指出父类T的类型，子类需成为类模板

129. 类模板构造函数和成员函数类外实现：

130. ```c++
     template<class T1, class T2>
     Person<T1, T2>::Person(T1 name, T2 age){
     	//函数实现
     }
     template<class T1, class T2>
     void Person<T1, T2>::showPerson(){
         //函数实现
     }
     ```

131. 类模板分文件编写：正常情况下，分文件.h里面写类模板声明，分文件.cpp里面写类模板实现，主文件调用分文件.h，会报错，这是因为类模板成员函数在调用时创建，只调用.h文件，主文件无法知道成员函数，解决方法1，改为调用分文件.cpp，解决方法2，将.h文件与.cpp文件写到一起，后缀改为.hpp文件

132. 类模板与友元：全局函数类内实现和类外实现

133. 类内实现friend void 函数名(类名<T1, T2> p){函数实现}

134. 类外实现需要在类内函数声明中加空模板参数列表friend void 函数名<>(类名<T1, T2> p)， 类外void 函数名(类名<T1, T2> p){函数实现}前加template<class T1, class T2>，此外还需要在类前面声明类模板和全局函数，即template<class T1, class T2> class Person; template<class T1, class T2> void 函数名(类名<T1, T2> p){函数实现}，放弃吧

135. 

136. STL：C++面向对象和泛型编程思想，为了提高复用性，进一步，诞生了标准模板库STL，包括容器、算法、迭代器，容器和算法之间通过迭代器无缝连接，STL代码采用类模板和函数模板

137. STL六大组件：容器、算法、迭代器、仿函数、适配器、空间配置器

138. 容器：各种数据结构，vector、list、deque、set、map

139. 算法：各种算法，sort、find、copy、for_each

140. 迭代器：容器和算法的胶合剂

141. 仿函数：函数小括号重载，作为算法策略

142. 适配器：修饰容器、仿函数、迭代器接口的东西，使用难且不广泛

143. 空间配置器：负责空间配置与管理

144. 容器：

145. 常见的数据结构：数组、链表、数、栈、队列、集合、映射表

146. 序列式容器：每个元素有固定位置，强调值的排序

147. 关联式容器：二叉树结构，各元素之间没有严格顺序关系

148. 算法：质变算法：拷贝、替换、删除；非质变算法：查找、计数、遍历、寻找极值

149. 迭代器：算法要通过迭代器访问容器中的元素，每个容器都有自己的专属迭代器，使用类似指针，输入迭代器，输出迭代器，前向迭代器，双向迭代器，随机访问迭代器，常用的为双向迭代器和随机访问迭代器

150. vector、for_each、vector<int>::iterator容器算法迭代器

151. ```c++
     vector<int> v;
     vector<int>::iterator itBegin = v.begin()；//起始迭代器，指向容器中第一个元素
     vector<int>::iterator itEnd = v.end()；//结束迭代器，指向容器中最后一个元素的下一个位置
     //第一种遍历方式
     for(vector<int>::iterator it = v.begin(); it!=v.end(); it++){
     	//cout << *it << endl;
     }
     //第二种遍历方式
     void myPrint (int val) {
         cout << val << endl;
     }
     for_each(v.begin(), v.end(), myPrint);
     
     //容器嵌套
     for(vector<vector<int>>::iterator it = v.begin(); it!=v.end(); it++){
         for(vector<int>::iterator vit = *it.begin(); vit!=*it.end(); vit++){
         	cout << *vit << " ";
         }
         cout << endl;
     }
     ```

152. string容器：string是一个类，类内部封装了**char***，是一个**char***型的容器

153. string类封装了很多成员方法：find，copy，delete，replace，insert

154. string构造：默认构造、c语言构造、n个元素构造、拷贝构造

155. string赋值：等号赋值、assign赋值

156. string字符串拼接：+=拼接、append拼接

157. string查找find、替换replace、比较compare、存取[]和.at()、插入insert、删除erase、子串获取substr

158. ```c++
     //string的构造函数
     string s1;//默认构造
     const char* str = "hello";
     string s2(str);//c语言风格
     string s3(s2);//拷贝构造
     string s4(10, 'a');
     //string赋值操作
     string s1;
     s1 = "hello";
     string s2;
     s2 = s1;
     string s3;
     s3 = 'h';
     string s4;
     s4.assign("hello");
     string s5;
     s5.assign("hello", 3);
     string s6;
     s6.assign(s5);
     string s7;
     s7.assign(10, 'a');
     //string字符串拼接
     s1 += " world";
     s2 += '!';
     s1 += s2;
     s1.append("I love");
     s1.append("play game", 3);
     s1.append(s2);
     s1.append(s2, 1, 2);//从第一个位置截取两个元素加到s1
     //string字符串查找和替换
     //查找
     string s1 = "abcdef";
     int pos = s1.find("de");//pos返回为3，即d的索引，没有找到返回-1
     pos = s1.rfind("de"); //rfind从右往左查找
     //替换
     s1.replace(1, 3, "11111"); //从1号位置起，3个字符替换为"11111"
     //string字符串比较
     int output = s1.compare(s2);//相等输出为0，不等输出不为0
     //string字符存取
     string s = "hello";
     char c1 = s[0]; 
     char c2 = s.at(1); //读取
     s[0] = 'e'; //写入
     s.at(1) = 'h';
     //string插入和删除
     string s = "hello";
     s.insert(1, "111"); //索引为1处插入"111"
     s.erase(1, 3);      //索引为1处删除3个字符
     //string子串获取
     string s = "abcdef";
     string sub = s.substr(1, 3); //索引1开始截取3个赋值给sub 
     ```

159. vector容器：与数组区别，数组为静态空间，vector可以动态拓展

160. vector容器的迭代器是支持随机访问的迭代器

161. vector构造函数：默认构造、通过区间构造v2(v1.begin(), v1.end())、n个元素构造、拷贝构造

162. vector赋值操作：L1 = L2; L1.assign(L2.begin(), L2.end()); L1.assign(数量，元素)，L1.swap(L2)，等号赋值、assign赋值

163. vector容量和大小：empty()判断是否为空 capacity()容量 size()元素个数 resize()重新指定长度，用0填充新位置，也可以用重载指定新位置的值，超出部分会删除，其中容量大小大于size

164. vector插入和删除：push_back(元素)、pop_back()、v1.insert(v1.begin()，元素)、v1.insert(v1.begin()，数量，元素)、erase(v1.begin())、erase(v1.begin(), v1.end())、clear()

165. vector数据存取：v1[索引]和v1.at(索引)、v1.front()、v1.back()

166. vector互换容器：v1.swap(v2)

167. vector预留空间：v1.reserve(长度)，不用多次动态拓展

168. deque容器：双端数组，与vertor区别，vector不擅长头部插入删除，vector访问元素更快，deque内部有中控器，擅长头部插入删除，但访问较慢

169. deque构造,，赋值同vector，默认构造、通过区间构造v2(v1.begin(), v1.end())、n个元素构造、拷贝构造，等号赋值、assign赋值

170. deque无容量，大小与vector一样，empty()判断是否为空  size()元素个数 resize()重新指定长度，用0填充新位置，也可以用重载指定新位置的值，超出部分会删除

171. deque插入和删除，push_back(元素)、pop_back()、push_front(元素)、pop_front()、相比vector多了头插头删，v1.insert(v1.begin()，元素)、v1.insert(v1.begin()，数量，元素)、erase(v1.begin())、erase(v1.begin(), v1.end())、clear()

172. deque数据存取：同vector，v1[索引]和v1.at(索引)、v1.front()、v1.back()

173. stack容器：栈，先进后出，默认构造，拷贝构造，等号赋值，push(元素)，pop()，top()，empty()，size()

174. queue容器：队列，先进先出，默认构造，拷贝构造，等号赋值，push(元素)，pop()，back()，front()，empty()，size()

175. list容器：链表，由一系列结点组成，结点包括数据域和指针域，容器遍历速度慢，插入删除方便，占用空间大，STL提供的链表为双向循环链表，不会造成内存浪费，插入删除不会造成原有迭代器的失效

176. list构造：默认构造、通过区间构造v2(v1.begin(), v1.end())、n个元素构造、拷贝构造

177. 容器前加const，迭代器要用const_iterator，即const list<int> L; list<int>::const_iterator it = L.begin();

178. list赋值和交换：L1 = L2; L1.assign(L2.begin(), L2.end()); L1.assign(数量，元素)，L1.swap(L2)

179. list容器大小：empty()判断是否为空  size()元素个数 resize()重新指定长度，用0填充新位置，也可以用重载指定新位置的值，超出部分会删除

180. list容器插入和删除：push_back(元素)、pop_back()、push_front(元素)、pop_front()、相比vector多了头插头删，v1.insert(v1.begin()，元素)、v1.insert(v1.begin()，数量，元素)、v1.insert(v1.begin(), v2.begin(), v2.end())、erase(v1.begin())、erase(v1.begin(), v1.end())、clear()，remove(元素)

181. list容器数据存取：v1.front()、v1.back()

182. vector容器的迭代器是双向迭代器

183. list容器反转和排序：L1.reverse()，sort(L1.begin(),L1.end())报错，应该用L1.sort()默认升序

184. 所有不支持随机访问迭代器的容器，不可以用标准算法 ，内部会提供成员函数算法

185. set容器：关联式容器，底层是二叉树，set不允许重复元素，multiset允许重复元素

186. set容器构造：set<int> s1; 默认构造，拷贝构造，赋值s1.insert(元素)，插入的时候自动排序，s1.size()，s1.empty()，s1.swap(s2)，s1.erase(s1.begin())，s1.erase(s1.begin()，s1.end())，s1.erase(元素)，s1.clear()

187. s1.find(元素)，返回该元素的迭代器，if(s1.find(元素)!=s1.end())说明找到该元素，s1.count(元素)，返回该元素个数

188. pair<set<int>::iterator, bool> ret = s1.insert(元素)，ret.second返回插入是否成功

189. pair对组创建，pair<类型1，类型2> p(值1，值2); pair<类型1, 类型2> p = make_pair<值1，值2>; 值1为p.first，值2为p.second

190. set容器排序：利用仿函数，改变排序规则，set<int, myCompare> p; 其中myCompare是类名，即仿函数数据类型，类里重载()运算符，仿函数中返回布尔类型

191. map容器：关联式容器，底层是二叉树，所有元素为pair，第一个元素为key键值，第二个元素value实值，插入的时候自动排序，map不允许重复key值，multimap允许重复key值

192. map容器构造和赋值：map<int, int> m; 默认构造，拷贝构造，m.insert(pair<int, int>(1, 10)); 赋值

193. map大小和交换：m.size(); m.swap(m2); m.empty()

194. map容器插入和删除：m.insert(pair<int, int>(1,10)); m.insert(make_pair(1,10)); m[1] = 10; 中括号不建议插入，用于访问，删除m.erase(m.begin())，m.erase(1)，1为key，按照key删除，m.erase(m.begin(), m.end())，m.clear()清空

195. map容器查找和统计：m.find(key)，返回该键对应元素的迭代器，if(m.find(元素)!=m.end())说明找到该元素，map<int, int>::iterator pos = m.find(1); `(*pose).first和pose->second`分别为键值和实值，`m.count(1)`返回键值为1的个数，只能是1为0，因为map不允许插入重复key的元素

196. map排序：利用仿函数，改变排序规则，set<int, myCompare> p; 其中myCompare是类名，即仿函数数据类型，类里重载()运算符，仿函数中返回布尔类型

197. 函数对象：重载函数调用操作符的类，其对象称为函数对象，函数对象使用重载的()时，叫做仿函数，函数对象本质是一个类

198. 1、函数对象可以和普通函数一样，有参数，有返回值

199. 2、函数对象可以有类的成员属性

200. 3、函数对象可以作为函数参数传递

201. 谓词：返回bool类型的仿函数，如果operator()接受一个参数，叫一元谓词，接受两个参数，叫二元谓词

202. find_if(v.begin(), v.end(), 谓词)，谓词返回真，find_if返回元素的叠加器

203. sort(v.begin(), v.end(), 谓词)，改变sort的返回策略,，实现从大到小

204. 内建函数对象，算术仿函数，关系仿函数，逻辑仿函数，用法和一般函数相同，使用内建函数对象，需要引入头文件`#include<functional>`

205. negate一元仿函数，negate<int>n; plus二元仿函数，plus<int>n; n(10, 10);

206. sort(v.begin(), v.end(), greater<int>())，改变sort的返回策略，实现从大到小，nice

207. transform(v.begin(), v.end(), v2.begin(), logical_not<bool>())，将v的元素取反后搬到v2中

208. 算法头文件<algorithm><functional><numeric>

209. for_each(v.begin(), v.end(), 普通函数/仿函数); 遍历容器，仿函数可以为匿名函数对象

210. transform(v.begin(), v.end(), v2.begin(), logical_not<bool>())，搬运容器到另一个容器中，将v的元素取反后搬到v2中，目标容器需要提前开辟空间，v2.resize(v.size())

211. find(v.begin(), v.end(), 元素) ，vector<int>::iterator it = find(v.begin(), v.end(), 元素) 查找元素，if(it == v.end())没找到，find查找指定元素，找到返回从左往右第一个满足条件的该元素迭代器，否则返回结束迭代器end()，如果不是int数据类型而是自己定义数据类型，要在自己设计的类里重载==

212. find_if(v.begin(), v.end(), 谓词)，其中谓词为一个函数对象，或者叫仿函数，这里用类名+()表示，称为匿名函数对象，类里使用operator()重载()，传入一个参数，对这个参数判断真假，作为查找判断条件，返回bool类型，find_if返回从左往右第一个满足条件的元素的迭代器，如果没找到返回结束迭代器end()

213. adjacent_find(v.begin(), v.end())查找相邻重复元素，如果找到返回相邻元素的第一个位置的迭代器

214. binary_search(v.begin(), v.end(), 元素)，查找到元素返回true，否则返回false，在无序序列中不可用

215. count(v.begin(), v.end(), 元素)，返回元素个数，如果不是int数据类型而是自己定义数据类型，要在自己设计的类里重载==

216. count_if(v.begin(), v.end(), 谓词)，其中谓词为一个函数对象，或者叫仿函数，这里用类名+()表示，称为匿名函数对象，类里使用operator()重载()，传入一个参数，对这个参数判断真假，作为查找判断条件，返回bool类型，count_if返回从左往右满足条件的元素的个数

217. sort(v.begin(), v.end(), 谓词)，其中谓词可填可不填，不填的话默认从小到大排序，填的话为二元谓词，为一个函数对象，或者叫仿函数，这里用类名+()表示，称为匿名函数对象，类里使用operator()重载()，传入两个个参数，对这两个参数比大小，如果大于返回真，则从大到小排序，也可以用内建函数对象greater<int>表示，

218. random_shuffle(v.begin(), v.end())，洗牌，运行完容器数据被打乱

219. merge(v1.begin(), v1.end(), v2.begin(), v2.end(), 目标容器起始迭代器v3.begin())，合并，其中v1v2容器必须有序，提前给目标容器分配空间，v3.resize(v1.resize() + v2.resize())，合并后容器仍为有序序列

220. reverse(v.begin(), v.end())，反转，反转元素的位置，运行完容器数据被反转

221. copy(v1.begin(), v1.end(), 目标容器起始迭代器v2.begin())，拷贝，直接用等号替代

222. replace(v1.begin(), v1.end(), 旧元素，新元素)，替换

223. replace_if(v1.begin(), v1.end(), 谓词，新元素)，其中谓词为一个函数对象，或者叫仿函数，这里用类名+()表示，称为匿名函数对象，类里使用operator()重载()，传入一个参数，对这个参数判断真假，作为查找判断条件，返回bool类型，替换满足条件的元素为新元素

224. swap(v1, v2)，互换，只能为同种类型容器

225. acccumulate(v1.begin(), v1.end(), 起始累加值)，计算区间内容器总和，属于小型算法，头文件为<numeric>

226. fill(v1.begin(), v1.end(), 待填充值)，将区间内容器元素填充为待填充值，属于小型算法，头文件为<numeric>

227. #include <bits/stdc++.h>万能头文件

228. set_intersection(v1.begin(), v1.end(), v2.begin(), v2.end(), 目标容器起始迭代器v3.begin())，交集，目标容器需要提前开辟空间，resize(小容器.size())，两个集合必须有序，返回交集最后一个元素的迭代器

229. set_union(v1.begin(), v1.end(), v2.begin(), v2.end(), 目标容器起始迭代器v3.begin())，并集，目标容器需要提前开辟空间，resize(大容器.size())，两个集合必须有序，返回并集最后一个元素的迭代器

230. set_difference(v1.begin(), v1.end(), v2.begin(), v2.end(), 目标容器起始迭代器v3.begin())，差集，目标容器需要提前开辟空间，resize(大容器.size())，两个集合必须有序，返回差集最后一个元素的迭代器
