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
21.  引用的本质是指针常量，即int& a=b;等价于int* const a = &b;
22.  常量引用，用来修饰形参，防止误操作，可以const int& a=10;
23. 
24. 函数默认参数，形参如果有默认值，这个位置从左到右都必须有默认值，此时实参可以传可以不传
25. 
