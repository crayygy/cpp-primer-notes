## C++ Primer 第五版 学习笔记
### 第一章 开始
#### 1.1节

##### ex1.1
```
	$ cc proj1.cc
	$ ./a.out
``` 
##### ex1.2
On Windows:

```
	$ echo %ERRORLEVEL%
```

On Linux and Unix:

```
	$ echo $?
```
在windows中，返回的值是`-1`， 但是在Linux与Unix中，返回`255`


#### 1.2节
```
	#include<iostream>
	int main(){
		std::cout << "Enter two numbers:" << std::endl;
		int v1 = 0, v2 = 0;
		std::cin >> v1 >> v2;
		std::cout << "The sum of " << v1 << " and " << v2 << " is " << v1 + v2 << std::endl;
		return 0;
	}
```

其实也可以写成这样，稍微省事一点：
	
	#include<iostream>
	using namespace std;
	int main(){
		cout << "Enter two numbers:" << endl;
		int v1 = 0, v2 = 0;
		cin >> v1 >> v2;
		cout << "The sum of " << v1 << " and " << v2 << " is " << v1 + v2 << endl;
		return 0;
	}
即使用`namespace`来省略掉每次的`std`。可见第3.1节

在这里，新手一定要注意的一个问题是: `务必要确定你的分号逗号等等一切符号，都是在英文状态下输入，否则会报一些奇奇怪怪的错误`


##### ex1.3

		#include<iostream>
		int main(){
			std::cout <<"Hello world." << std::endl;
			return 0;
		}

##### ex1.4

```
	#include<iostream>
	int main(){
		std::cout << "Enter two numbers:" << std::endl;
		int v1 = 0, v2 = 0;
		std::cin >> v1 >> v2;
		std::cout << "The product of " << v1 << " and " << v2 << " is " << v1 * v2 << std::endl;
		return 0;
	}
```

##### ex1.5
```
	#include<iostream>
	int main(){
		std::cout << "Enter two numbers:" << std::endl;
		int v1 = 0, v2 = 0;
		std::cin >> v1 >> v2;
		std::cout << "The product of ";
		std::cout << v1 ;
		std::cout << " and ";
		std::cout << v2; 
		std::cout << " is "
		std::cout << v1 * v2;
		std::cout << std::endl;
		return 0;
	}
```
##### ex1.6

```
	std::cout << "The sum of " << v1;
			  << " and " << v2;
			  << " is " << v1 + v2;
```

此语句不合法，分号`;`意味着当前行的语句结束，对于第二句的操作而言，`<<`操作符没有操作对象，因此会报错。

可修正为：

```
	std::cout << "The sum of " << v1
			  << " and " << v2
			  << " is " << v1 + v2;	
```

##### ex1.7
请自行尝试

##### ex1.8

```
	std::cout << "/*"; // 合法
```
```
	std::cout << "*/"; // 合法
```
```
	std::cout << /* "*/" */ ; // 不合法
```
```
	std::cout << /* "*/" /* "/*" */; // 合法
```
报错信息为

```
prog1.cc:5:22: warning: missing terminating '"' character [-Winvalid-pp-token]
                std::cout << /* "*/" */;
                                   ^
prog1.cc:5:22: error: expected expression
1 warning and 1 error generated.
```
改正方法很简单，添加一个引号即可：

```
	std::cout << "/*";
	std::cout << "*/";
	std::cout << /* "*/" */";
	std::cout << /* "*/" /* "/*" */;
```

#### ex1.9

```c++
	#include <iostream>
	int main(int argc, const char * argv[]) {
    int sum = 0, val = 50;
    while (val <= 100) {
        sum += val;
        ++val;
    }
    std::cout<< "Sum of 50 to 100 inclusive is " << sum << std::endl;
    return 0;
}
```