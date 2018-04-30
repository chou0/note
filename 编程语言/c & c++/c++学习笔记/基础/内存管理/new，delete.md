* new 和 malloc 是一样的，都是在堆上申请内存
delete 与 free 是一样的，释放堆上的内存

* ==但是 new 和 delete 是操作符，而 malloc 和 free 是函数==
```
new返回的是 对象指针 
例：
class example{
};

example *a = new example(); //在堆上申请的内存
example a；//类对象在 栈上 
```
* new 先分配好内存后调用构造函数
* delete 先调用析构函数再释放内存