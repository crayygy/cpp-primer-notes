## C++ Primer 第五版 学习笔记
### 第一章 开始
#### 1.1节

##### ex1.1
```bash
	$ cc proj1.cc
	$ ./a.out
``` 
##### ex1.2
On Windows:

```bash
	$ echo %ERRORLEVEL%
```

On Linux and Unix:

```bash
	$ echo $?
```
在windows中，返回的值是`-1`， 但是在Linux与Unix中，返回`255`


#### 1.2节
```c++
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
```c++	
	#include<iostream>
	using namespace std;
	int main(){
		cout << "Enter two numbers:" << endl;
		int v1 = 0, v2 = 0;
		cin >> v1 >> v2;
		cout << "The sum of " << v1 << " and " << v2 << " is " << v1 + v2 << endl;
		return 0;
	}
```
即使用`namespace`来省略掉每次的`std`。可见第3.1节

在这里，新手一定要注意的一个问题是: `务必要确定你的分号逗号等等一切符号，都是在英文状态下输入，否则会报一些奇奇怪怪的错误`


##### ex1.3
```c++
		#include<iostream>
		int main(){
			std::cout <<"Hello world." << std::endl;
			return 0;
		}
```

##### ex1.4

```c++
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
```c++
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

```c++
	std::cout << "The sum of " << v1;
			  << " and " << v2;
			  << " is " << v1 + v2;
```

此语句不合法，分号`;`意味着当前行的语句结束，对于第二句的操作而言，`<<`操作符没有操作对象，因此会报错。

可修正为：

```c++
	std::cout << "The sum of " << v1
			  << " and " << v2
			  << " is " << v1 + v2;	
```

##### ex1.7
请自行尝试

##### ex1.8

```c++
	std::cout << "/*"; // 合法
```
```c++
	std::cout << "*/"; // 合法
```
```c++
	std::cout << /* "*/" */ ; // 不合法
```
```c++
	std::cout << /* "*/" /* "/*" */; // 合法
```
报错信息为

```bash
prog1.cc:5:22: warning: missing terminating '"' character [-Winvalid-pp-token]
                std::cout << /* "*/" */;
                                   ^
prog1.cc:5:22: error: expected expression
1 warning and 1 error generated.
```
改正方法很简单，添加一个引号即可：

```c++
	std::cout << "/*";
	std::cout << "*/";
	std::cout << /* "*/" */";
	std::cout << /* "*/" /* "/*" */;
```

#### ex1.9

```c++
	#include <iostream>
	int main() {
	    int sum = 0, val = 50;
	    while (val <= 100) {
	        sum += val;
	        ++val;
	    }
	    std::cout<< "Sum of 50 to 100 inclusive is " << sum << std::endl;
	    return 0;
	}
```

#### ex1.10 

```c++
	#include <iostream>
	int main(int argc, const char * argv[]) {
	    int val = 10;
	    while (val >= 0) {
	        std::cout << val << std::endl;    
	        --val;
	    }
	    return 0;
	}
```

#### ex1.11
```c++
	#include <iostream>
	int main() {
		int min = 0, max = 0;
		std::cout << "Input two numbers:"<<std::endl;
		std::cin >>min>>max;
		if(min > max){
			std::swap(min, max);
		}
		while(min < max){
			std::cout << min <<std::endl;
			++min;
		}
		return 0;
	}
```

#### ex1.12
```c++
	int sum = 0;
	for (int i = -100; i <= 100; ++i){
		sum += i;
	}
```
从-100一直累加到100，故最终`sum=0`， 可以使用`std::cout<<sum;`来获取值。

#### ex1.13
```c++
	int sum = 0;
	for (int i = 50; i <= 100; ++i){
		sum += i;
	}
```
```c++
	for (int i = 10; i >= 0; --i){
		std::cout << i <<std::endl;
	}
```
```c++
	int min = 0, max = 0;
	if (min > max){
		std::swap(min, max);
	}
	std::cin >> min >> max;
	for (current = min; current != max; ++current ){
		std::cout << current<< std::endl;
	}
```

#### ex1.14
对比 for循环 和 while循环 的优缺点：
在stackoverflow上有一个类似的[问题](http://stackoverflow.com/questions/2950931/for-vs-while-in-c-programming)，可以提供参考。

在这里提供一些我的个人看法：
	
	在进行无限循环时，使用while(1)来进行循环；
	在进行计数时，使用for(int i=0; i<=100; ++i)类似格式；
	另外还有一种循环do{} while 循环，在进行循环条件判断时，先执行一次操作。
	
	推荐在除了需要死循环外的其它情况下，使用for循环，因为它看起来更加的简洁明了。
	
#### ex1.15
编译器的常见错误信息，请自行尝试。