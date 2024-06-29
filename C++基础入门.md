C++基础入门

## 1 C++初识

### 1.1 第一个C++程序hello world

```c++
#include<iostream>
using namespace std;

int main()
{
    cout <<"Hello World"<< endl;
	
	system("pause");

	return 0;
}
```

基础框架：

```c++
#include<iostream>
using namespace std;//使所有std名字都可用，不必再加上std::前缀

int main()
{
	
	system("pause");

	return 0;
}
```

### 1.2 注释

单行注释//

多行注释/*    */

```c++
#include<iostream>
using namespace std;

//单行注释

/*多行注释
main是一个程序的入口
每个程序都必须有且只有一个*/

int main1()
{
	
	system("pause");

	return 0;
}
```

### 1.3 变量

作用：给一段指定的内存空间起名，方便操作这段内存

语法：**数据类型    变量 = 变量初始值**；

变量的定义包括一个基本数据类型（base type）和一组声明符，类型修饰符（*或&）是声明符的一部分。

**在C++中，不同的变量类型之间唯一的区别就是所占内存的大小**

一个字节是8bit

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//变量创建的语法：数据类型 变量名=变量初始值;
    //变量的定义
    
	int a =10;

	cout <<"a="<< a << endl;

	system("pause");

	return 0;
}
```

### 1.4 常量

作用：用于记录程序中不可更改的数据

C++定义常量两种方式

1. **#define** 宏常量：**#define 常量名 常量值**
   - **通常在文件上方定义**，表示一个常量
2. **const** 修饰的变量：**const  数据类型 常量名 = 常量值**
   - **通常在变量定义前加关键字const**，修饰该变量为常量，不可修改

示例：

```c++
#include<iostream>
using namespace std;

//常量的定义方式
//1.#define 宏常量
//2.const修饰的变量

//1、#define 宏变量(C++中尽量不要使用宏定义)
#define Day 7

int main(){

	cout <<"一周总共有:"<< Day <<"天"<< endl;

	//2、const修饰的变量
	const int month=12;
	//month=24;//错误，const修饰的变量也称为常量

	cout <<"一年总共有："<< month <<"个月"<< endl;

	system("pause");

	return 0;
}
```

### 1.5 关键字

**作用：关键字是C++预先保留的单词 （如：int，if，const等）**

- **在定义变量或者常量时候，不要使用关键字**

### 1.6 标识符命名规则

作用：C++规定给标识符（变量、常量）命名时，有一套自己的规则

- 标识符不能是关键字
- 标识符只能由字母、数字、下划线组成
- 第一个字符必须为字母或者下划线
- 标识符中的字母区分大小写

建议：给变量起名的时候，最好能做到见名知意

## 2 数据类型

C++规定在创建一个变量或者常量时，必须要指定出相应的数据类型，否则无法给变量分配内存

数据类型的存在意义：给变量分配合适的内存空间

### 2.1 整型

作用：整型变量表示的是**整数类型**的数据

C++中能够表示整型的类型有一下几种方式，区别在于所占用的内存空间不同：

| 数据类型              | 占用空间                                            | 取值范围     |
| --------------------- | --------------------------------------------------- | ------------ |
| short（短整型）       | 2字节                                               | -2^15~2^15-1 |
| int（整型）           | 4字节                                               | -2^31~2^31-1 |
| long（长整型）        | windows为4字节，Linux为4字节（32位），8字节（64位） | -2^31~2^31-1 |
| long long（长长整型） | 8字节                                               | -2^63~2^63-1 |

示例：

```c++
#include<iostream>
using namespace std;

int main(){

	//整型
	//1、短整型（-32768~32767)
	short num1 = 10;

	//2、整型
	int num2 = 10;  //int最常用

	//3、长整型
	long num3 = 10;

	//4、长长整型
	long long num4 = 10;

	cout << "num1=" << num1 << endl;
	cout << "num2=" << num2 << endl;
	cout << "num3=" << num3 << endl;
	cout << "num4=" << num4 << endl;

	system("pause");

	return 0;

}

```

### 2.2 sizeof关键字（运算符）

作用：利用sizeof关键字可以**统计数据类型所占内存大小**

语法：sizeof（数据类型/变量）

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//可以利用sizeof求出数据类型占用内存的大小
	short num1 = 10;
	cout << "short占用的内存空间为：" << sizeof(num1) << endl;

	int num2 = 10;
	cout << "int占用的内存空间为：" << sizeof(int) << endl;
	
	system("pause");

	return 0;
}
```

### 2.3 实型（浮点型）

作用：**表示小数**

浮点型变量分为两种：

 1、单精度float

 2、双精度double

两者的区别在于**表示的有效数字范围不同**。

| 数据类型 | 占用空间 | 有效数字范围    |
| -------- | -------- | --------------- |
| float    | 4字节    | 7位有效数字     |
| double   | 8字节    | 15-16位有效数字 |

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//1、单精度 float
	//2、双精度 double
	//默认情况下输出一个小数，会显示出6位有效数字
	float f1 = 3.1415926f; //float类型变量后不加f默认为双精度

	cout << "f1=" << f1 << endl;

	double d1 = 3.1415926;

	cout << "f1=" << f1 << endl;

	//统计float和double占用内存空间
	cout << "float占用的内存空间为：" << sizeof(float) << endl;//4字节
	cout << "double占用的内存空间为：" << sizeof(double) << endl;//8字节

	//科学计数法
	float f2 = 3e2;//3*10^2
	cout << "f2=" << f2 << endl;
	float f3 = 3e-2;//3*0.1^2
	cout << "f3=" << f3 << endl;

	system("pause");

	return 0;
}
```

### 2.4 字符型

作用:字符型变量用于**显示单个字符**

语法：**char   ch = ‘ a ’；**

注意1：在显示字符型变量时，**用单引号**将字符括起来，不要用双引号

注意2：单引号内只能是**一个字符**，不能是字符串

- C和C++中的字符变量中占用1个字节
- 字符变量并不是把字符本身放到内存中储存，而是将对应的ASCII编码放到存储单元

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//1、字符型变量创建方式
	char ch = 'a';
	cout << ch << endl;
	
	//2、字符型变量所占内存空间
	cout << "char字符型变量所占用的内存大小：" << sizeof(ch) << endl;
	
	//3、字符型变量常见错误

	//4、字符型变量对应的ASCII码
	cout << (int)ch << endl;//'a'=97  'A'=65

	system("pause");

	return 0;
}
```

ASCII码大致由以下两部分组成：

- ASCII非打印控制字符：ASCII表上的数字0-31分配给了控制字符，用于控制类似于打印机等一些设备
- ASCII打印控制字符：数字32-126分配给了能在键盘上找到的字符，当查看或打印文档时就会出现

### 2.5 转义字符

作用：用于表示一些**不能显示出来的ASCII字符**

现阶段我们常用的转义字符有：\n   \ \    \t

- \n:换行（LF），将当前位置移到下一行开头
- \t:水平制表（HT）（跳到下一个TAB位置）
- \ \:表示一个反斜字符 “\”

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//换行符\n
	cout << "hello world\n";
	//反斜杠   
	cout << "\\" << endl;
	//水平制表符\t
	cout << "aaa\thelloworld" << endl;// \t占8个字符，用于可以整齐的输出数据

	system("pause");

	return 0;
}
```

### 2.6字符串型

作用：用于表示一串字符

本质：**是由字符char组成的数组，最后会有空指针表示字符串结束**

C++风格字符串：string  变量名= “字符串值”

C风格字符串：    char    变量名[ ]= "字符串值"

示例：

```c++
#include<iostream>
#include<string>
using namespace std;

int main()
{
	//1、C风格的字符串
	char str[] = "helloworld";//加上中括号，等号后面用双引号
	cout << str << endl;

	//2、C++风格的字符串
	string str2 = "helloworld";
	cout << str2 << endl;//包含一个头文件#include<string>
	system("pause");

	return 0;
}


int main()
{
	string line;
	while (getline(cin, line))//getline可以保留输入时的空白符
		cout << line << endl;
	

	system("pause");
	return 0;
}
```

```c++
#include<iostream>

int main()
{
	const char* name = "dai";
	char name2[4] = { 'd', 'a', 'i' , 0};
	std::cout << name2 << std::endl;

	std::cin.get();
}
```



### 2.7布尔类型bool

作用：布尔数据类型代表真或假

bool类型只有两个值：

- ture --- 真（本质是1）
- false --- 假（本质是0）

bool类型占1个字节大小

示例： 2.8数据的输入

作用：用于从键盘获取数据

关键字：cin

语法：cin>>变量

示例：

```c++
#include<iostream>
#include<string>
using namespace std;

int main()
{
	//1、整型
	int a = 0;
	cout << "请给整型变量a赋值" << endl;
	cin >> a;
	cout << "整型变量a=" << a << endl;

	//2、浮点型
	//3、字符型
	//4、字符串型
	string str = "hello";
	cout << "请给字符串str赋值" << endl;
	cin >> str;
	cout << "字符串str=" << str << endl;
	//5、布尔型

	system("pause");

	return 0;
}
```

## 3 运算符

作用：用于执行代码运算

### 3.1 算数运算符

作用：用于处理四则运算

| 运算符 | 术语         | 示例      | 结果    |
| ------ | ------------ | --------- | ------- |
| +      | 正号         | +3        | 3       |
| -      | 负号         | -3        | -3      |
| +      | 加           | 10+3      | 13      |
| _      | 减           | 10-5      | 5       |
| *      | 乘           | 10*5      | 50      |
| /      | 除           | 10/5      | 2       |
| %      | 取模（取余） | 10%3      | 1       |
| ++     | 前置递增     | a=2;b=++a | a=3;b=3 |
| ++     | 后置递增     | a=2;b=a++ | a=3;b=2 |
| --     | 前置递减     | a=2;b=--a | a=1;b=1 |
| --     | 后置递减     | a=2;b=a-- | a=1;b=2 |

注意：

- 整数与整数相除结果一定是整数，不保留小数部分
- 除数不可以为零
- 取模运算的本质就是两数相除求余数
- 两个小数是不可以做取模运算的
- 前置递增，先让变量+1，然后进行表达式的运算
- 后者递增，先进行表达式计算，后让变量+1

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//1、前置递增
	int a = 10;
	++a;//让变量加一
	cout << "a=" << a << endl;

	//2、后置递增
	int b = 10;
	b++;//让变量加一
	cout << "b=" << b << endl;
	
	//3、前置和后置的区别
	//前置递增 先让变量+1 然后进行表达式的运算
	int a2 = 10;
	int b2 = ++a2 * 10;
	cout << "a2=" << a2 << endl;
	cout << "b2=" << b2 << endl;
	
	//后者递增 先进行表达式计算 后让变量+1
	int a3 = 10;
	int b3 = a3++ * 10;
	cout << "a3=" << a3 << endl;
	cout << "b3=" << b3 << endl;
	
	system("pause");

	return 0;
}
```

### 3.2 赋值运算符

作用：用于将表达式的值赋给变量

赋值运算符包括以下几个符号：

| 运算符 | 术语   | 示例      | 结果     |
| ------ | ------ | --------- | -------- |
| =      | 赋值   | a=2;b=3   | a=2;b=3; |
| +=     | 加等于 | a=2;a+=2  | a=2;     |
| -=     | 减等于 | a=5;a-=2  | a=3;     |
| *=     | 乘等于 | a=2;a*=2  | a=4;     |
| ;/=    | 除等于 | a=4;a/=2; | a=2;     |
| %=     | 模等于 | a=3;a%2;  | a=1;     |

### 3.3 比较运算符

作用：用于表达式的比较，并返回一个真值或假值

比较运算符有一下符号：

| 运算符 | 术语     | 示例  | 结果 |
| ------ | -------- | ----- | ---- |
| ==     | 相等于   | 4==3  | 0    |
| \|=    | 不等于   | 4\|=3 | 1    |
| <      | 小于     | 4<3   | 0    |
| >      | 大于     | 4>3   | 1    |
| <=     | 小于等于 | 4<=3  | 0    |
| >=     | 大于等于 | 4>=3  | 1    |

### 3.4 逻辑运算符

作用：用于根据表达式的值返回真值或者假值

逻辑运算符有以下符号：

| 运算符 | 术语 | 示例   | 结果 |
| ------ | ---- | ------ | ---- |
| ！     | 非   | !a     |      |
| &&     | 与   | a&&b   |      |
| \|\|   | 或   | a\|\|b |      |

## 4 程序流程结构

C/C++支持最基本的三种程序运行结构：顺序结构、选择结构、循环结构

- 顺序结构：程序按照顺序执行，不发生跳转
- 选择结构：依据条件是否满足，有选择的执行相应功能
- 循环结构：依据条件是否满足，循环多次执行某段代码

### 4.1 选择结构

#### 4.1.1 if语句

作用：执行满足条件的语句

if语句的三种形式

- 单行格式if语句
- 多行格式if语句
- 多条件的if语句

1、单行格式if语句：if(条件){条件满足执行的语句}

示例:

```c++
#include<iostream>
using namespace std;

int main()
{
	//选择结构、单行if语句
	//用户输入分数，如果分数大于600分，视为考上一本大学，在屏幕上输出

	int score = 0;
	cout << "请输入一个分数" << endl;
	cin >> score;
	cout << "您输入的分数为" << score << endl;
	if (score > 600) {
		cout << "恭喜您考上了一本大学" << endl;
	}

	system("pause");

	return 0;
}
```

注意：if条件后面不要加分号

2、多行格式if语句：**if**(条件){条件满足执行的语句}**else**{条件不满足执行的语句}；

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//选择结构、多行if语句
	//用户输入分数，如果分数大于600分，视为考上一本大学，在屏幕上输出
	//如果分数小于等于600，打印未考上一本大学

	int score = 0;
	cout << "请输入考试分数" << endl;
	cin >> score;
	cout << "您输入的考试分数为" << score << endl;
	if (score > 600) {
		cout << "恭喜你考上一本大学" << endl;
	}
	else {
		cout << "很遗憾，您未考上一本大学" << endl;
	}

	system("pause");

	return 0;
}
```

3、多条件if语句：**if**(条件1){满足条件1执行的语句}**else if**(条件2){满足条件2执行的语句}...**else**{都不满足执行的语句}

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//选择结构、多行if语句
	//用户输入分数，如果分数大于600分，视为考上一本大学，在屏幕上输出
	//如果分数大于500，视为考上二本大学，屏幕输出
	//如果分数大于400，视为考上三本大学，屏幕输出
	//小于等于400，视为未考上大学，屏幕输出

	int score = 0;
	cout << "请输入考试分数" << endl;
	cin >> score;
	cout << "您输入的考试分数为" << score << endl;
	if (score > 600) {
		cout << "恭喜你考上一本大学" << endl;
	}
	else if (score > 500) {
		cout << "恭喜您考上二本大学" << endl;
	}
	else if (score > 400) {
		cout << "恭喜您考上三本大学" << endl;
	}
	else {
		cout << "很遗憾你没考上大学" << endl;
	}
	system("pause");

	return 0;
}
```

**嵌套if语句：**在if语句中可以嵌套使用if语句，达到精确的条件判断

案例需求：

- 提示用户输入一个高考分数，根据分数做如下判断
- 分数如果大于600分视为考上一本，大于500分考上二本，大于400分考上三本，其余视为未考上本科
- 在一本分数中，大于700分，考入北大，大于650分，考入清华，大于600考入人大

代码：

```c++
#include<iostream>
using namespace std;

int main()
{ 
	int score = 0;
	cout << "请输入考试分数" << endl;
	cin >> score;
	cout << "您输入的考试分数为" << score << endl;
	if (score > 600) {
		cout << "恭喜你考上一本大学" << endl;
		if (score > 700) {
			cout << "您能考入北京大学" << endl;
		}
		else if (score > 650) {
			cout << "您能考入清华大学" << endl;
		}
		else {
			cout << "您能考入人民大学" << endl;
		}
	}
	else if (score > 500) {
		cout << "恭喜您考上二本大学" << endl;
	}
	else if (score > 400) {
		cout << "恭喜您考上三本大学" << endl;
	}
	else {
		cout << "很遗憾你没考上大学" << endl;
	}
	system("pause");

	return 0;
}
```

练习案例：三只小猪称重

有三只小猪ABC，请分别输入ABC的体重，并且判断哪只小猪最重

```c++
#include<iostream>
using namespace std;

int main()
{
	int A = 0; int B = 0; int C = 0;
	cout << "请输入3只小猪的体重" << endl;
	cin >> A >> B >> C;
	cout << "您输入的3只小猪ABC的体重分别为" << A << "," << B << "," << C;
	if (A > B) {
		if (A > C) {
			cout << "其中最重的为小猪A"<< endl;
		}
		else {
			cout << "其中最重的为小猪C" << endl;
		}
	}
	else {
		if (C > B) {
			cout << "其中最重的为小猪C"  << endl;
		}
		else {
			cout << "其中最重的为小猪B" << endl;
		}
	}

	system("pause");

	return 0;
}
```

#### 4.1.2 三目运算符

作用：通过三目运算符实现简单的判断

**语法：表达式1 ?  表达式2 ：表达式3**

**解释：**

**如果表达式1的值为真，执行表达式2，并返回表达式2的结果；**

**如果表达式1的值为假，执行表达式3，并返回表达式3的结果；**

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//三目运算符
	//创建变量a、b、c，将a和b做比较，将变量大的赋值给c
	int a = 10; int b = 20; int c = 0;
	c = (a > b ? a : b);
	cout << "c=" << c << endl;
	//在C++中三目运算符返回的是变量，可以继续赋值
	(a > b ? a : b) = 100;
	cout << "a=" << a << endl;
	cout << "b=" << b << endl;
	system("pause");

	return 0;
}
```

#### 4.1.3 switch语句

作用：执行多条件分支语句

语法：

switch（表达式）//只能是整型或者字符型

{

​          case 结果1：执行语句；break；

​          case 结果2：执行语句；break；

​          case 结果3：执行语句；break；

​          .........

​          default:执行语句；break；

}

案例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//switch语句
	//给电影打分10~9：经典；8~7：非常好；6~5：一般；5以下：烂片
	int score = 0;
	cout << "请您为电影打分" << endl;
	cin >> score;
	cout << "您打的分数是" << score << endl;
	//根据用户的打分来提示用户最后的结果
	switch (score) {
	case 10:cout << "您认为是经典电影" << endl; break;//退出当前分支
	case 9:cout << "您认为是经典电影" << endl; break;
	case 8:cout << "您认为电影非常好" << endl; break;
	case 7:cout << "您认为电影非常好" << endl; break;
	case 6:cout << "您认为电影一般" << endl; break;
	case 5:cout << "您认为电影一般" << endl; break;
	default:cout << "您认为这是一部烂片" << endl; break;
	}

	system("pause");

	return 0;
}
```

if和switch区别？

switch缺点，判断时的表达式只能是整型或者字符型，不可以是一个区间

switch优点，结构清晰，执行效率高

### 4.2 循环结构

#### 4.2.1 while循环语句

作用：满足循环条件，执行循环语句

语法：while(循环条件){循环语句}

解释：只要循环条件结果为真，就执行循环语句

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//while循环
	//在屏幕中打印0~9这10个数字
	int num = 0;
	while (num <= 9) {
		cout << num << endl;
		num++;
	}

	system("pause");

	return 0;
}
```

while循环练习案例：猜数字

案例描述：系统随机生成1到100之间的数字，玩家进行猜测，如果猜错，提示玩家数字过大或过小，如果猜对则恭喜玩家胜利，并退出游戏。

代码：

```c++
#include<iostream>
using namespace std;
//time系统时间头文件包含
#include<ctime>

int main()
{
	//添加随机数种子 作用利用当前系统的时间生成随机数，防止每次随机数都一样
	srand((unsigned int)time(NULL));

	//系统生产随机数
	int num = rand() % 100 + 1;   //rand()%100+1生成0+1~99+1个随机数
	cout << "请输入猜测数字：" << endl;
	int val = 0;
	//判断玩家猜测的结果
	while (1) {
		cin >> val;
		if (val < num) {
			cout << "您猜的值过小了，请重新输入" << endl;
		}
		else if(val>num) {
			cout << "您猜的值过大了，请重新输入" << endl;
		}
		else {
			cout << "游戏胜利！" << endl;
			break;//break，可以利用该关键字来退出当前循环
		}
	}
	
	system("pause");

	return 0;
}
```

#### 4.2.2 do while循环语句

作用：满足循环条件，执行循环语句

语法：do{循环语句}while(循环条件);

注意：与while的区别在于do while会先执行一次循环，再判断循环条件

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//do while循环
	//在屏幕中打印0~9这10个数字
	int num = 0;
	do {
		cout << num << endl;
		num++;
	} while (num < 10);
	system("pause");

	return 0;
}
```

练习案例：水仙花数

案例描述：水仙花数是指一个3位数，它的没个位上的数字的3次幂之和等于它本身

例如：1^3+5^3+3^3=153

利用do...while语句，求出所有3位数中的水仙花数

代码：

```c++
#include<iostream>
using namespace std;

int main()
{
	int num = 100;
	do {
		int a = 0; int b = 0; int c = 0;
		a = num % 10;//获取个位   对数字取模于10可以取到个位
		b = num / 10 % 10;//获取十位   先整除于10，得到两位数，在取模于10，得到十位
		c = num / 100;//获取百位  直接整除于100，获取百位
		if (a * a * a + b * b * b + c * c * c == num) {
			cout << num << endl;
		}
		num++;
	} while (num < 1000);

	system("pause");
	return 0;
}
```

#### 4.2.3 for循环语句

作用：满足循环条件，执行循环语句

语法：for(起始表达式；条件表达式；末尾循环体){循环语句；}

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//for循环：在屏幕上打印数字0~9
	for (int i = 0; i < 10; i++) {
		cout << i << endl;
	}

	system("pause");
	return 0;
}
```

注意：for循环中的表达式，要用分号进行分离

总结：while，do...while，for都是开发中常用的循环语句，for循环结构比较清晰，比较常用

**练习案例：敲桌子**

案例描述：从1开始到数字100，如果数字个位含有7，或者数字十位含有7，或者数字是7的倍数，我们打印敲桌子，其余数字直接打印输出。

```c++
#include<iostream>
using namespace std;

int main()
{
	for (int num = 1; num <= 100; num++) {
		int a = 0; int b = 0; int c = 0;
		a = num % 10;//	取个位
		b = num / 10;//取十位
		c = num % 7;//7的倍数取模于7=0
		if (a == 7 || b == 7||!c) {
			cout << "敲桌子" << endl;
		}
		else { cout << num << endl; }
	}

	system("pause");
	return 0;
}
```

#### 4.2.4嵌套循环

作用：在循环体中再嵌套一层循环，解决一些实际问题

例如我们如果想在屏幕中打印如下图片，就需要利用嵌套循环

![image-20230718213057016](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20230718213057016.png)

代码：

```c++
#include<iostream>
using namespace std;

int main()
{
	
	for (int i = 0; i < 10; i++) {
		for (int j = 0; j < 10; j++) {
			cout << "* ";
		}
		cout << endl;
	}

	system("pause");
	return 0;
}
```

练习案例：乘法口诀表

案例描述：利用嵌套循环实现九九乘法表

![image-20230718214028359](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20230718214028359.png)

代码：

```c++
#include<iostream>
using namespace std;

int main()
{

	for (int i = 1; i < 10; i++) {
		for (int j = 1; j <=i; j++) {
			
		    cout << j << "*" << i<< "=" << i * j << " ";
		}
		cout << endl;
	}

	system("pause");
	return 0;
}
```

### 4.3 跳转语句

#### 4.3.1 break语句

作用：用于跳出选择结构或者循环结构

break使用的时机：

- 出现在switch条件语句中，作用是终止case并跳出switch
- 出现在循环语句中，作用是跳出当前的循环语句
- 出现在嵌套环中，跳出最近的内层循环语句

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//break的使用时机
	//1、出现在switch语句中
	/*cout << "请选择副本难度" << endl;
	cout << "普通" << endl;
	cout << "中等" << endl;
	cout << "困难" << endl;

	int select = 0;//创造选择结果
	cin >> select;
	switch (select) {
	case 1:cout << "您选择的是普通难度" << endl; break;
	case 2:cout << "您选择的是中等难度" << endl; break;
	case 3:cout << "您选择的是困难难度" << endl; break;
	default:break;
	}*/

	//2、出现在循环语句中
	/*for (int i = 0; i < 10; i++) {
		if (i ==5) {
			break;
		}
		cout << i << endl;
	}*/
	//3、出现在嵌套循环语句中
		for (int i = 0; i < 10; i++) {
			for (int j = 0; j < 10; j++) {
				if (j == 5) {
					break;//退出内层循环
				}
				cout << "* ";
			}
			cout << endl;
		}
		system("pause");
		return 0;
}
```

#### 4.3.2 continue语句

作用：在循环语句中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//continue语句
	for (int i = 0; i <= 100; i++) {
		if (i % 2 == 0) {
			continue;//可以筛选条件，执行到此就不再向下执行，执行下一次循环
		}
			cout << i << endl;
	}
	system("pause");
	return 0;
}
```

**注意：continue并不会使整个循环终止，而break会跳出循环**

4.3.3 goto语句（**尽量别写**）

作用：可以无条件跳转语句

语法：goto 标记；

解释：如果标记的名称存在，执行到goto语句时，会跳转到标记的位置

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//goto语句：尽量别写
	cout << "1、。。。" << endl;
	cout << "2、。。。" << endl;
	goto FLAG;
	cout << "3、。。。" << endl;
	cout << "4、。。。" << endl;
	FLAG:
	cout << "5、。。。" << endl;
	cout << "6、。。。" << endl;
	cout << "7、。。。" << endl;
	system("pause");
	return 0;
}
```

## 5 数组

### 5.1概述

所谓数组，就是一个集合，里面存放了相同类型的数据元素

特点1：数组中的**每个元素都是相同的数据类型**

特点2：数组是由**连续的内存位置组成的**

### 5.2一维数组

#### 5.2.1 一维数组的定义方式

一维数组定义的三种方式：

1.数据类型   数组名[数组长度];

2.数据类型   数组名[数组长度]={值1，值2，...};

3.数据类型   数组名[ ]={值1，值2，...};

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//数组
	//1.数据类型   数组名[数组长度];
	int arr[5];
	arr[0] = 10; arr[1] = 20; arr[2] = 30; arr[3] = 40; arr[4] = 50;
	cout << arr[0] << endl;//数组元素的下标是从零开始索引的
	cout << arr[1] << endl;
	cout << arr[2] << endl;
	cout << arr[3] << endl;
	cout << arr[4] << endl;
	//2.数据类型   数组名[数组长度]={值1，值2，...};
	int arr2[5] = { 10,20,30,40,50 };//如果初始化数据时，没有全部填写完，会用0来填补
	for (int i = 0; i < 5; i++) {
		cout << arr2[i] << endl;
	}
	//3.数据类型   数组名[ ]={值1，值2，...};
	int arr3[] = { 90,80,70,60,50,40,30,20,10 };
	for (int i = 0; i < 9; i++) {
		cout << arr3[i] << endl;
	}

	system("pause");
	return 0;
}
```

总结1：数组名的命名规范与变量名命名规范一致，不要和变量重名

总结2：数组中下标是从0开始索引

#### 5.2.2 一维数组组名

一维数组名称的用途：

- 可以统计整个数组在内存中的长度    sizeof(arr)
- 可以获取数组在内存中的首地址        cout<<arr<<endl;

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	cout << sizeof(arr) << endl;
	cout << sizeof(arr[0]) << endl;
	cout << sizeof(arr) / sizeof(arr[0]) << endl;
	cout << (int)arr << endl;
	cout << &arr[0] << endl;
	cout << &arr[1] << endl;
	
	system("pause");
	return 0;
}
```

注意：数组名是一个常量，不可以赋值

**练习案例1：**五只小猪称体重

**案例描述：**在一个数组中记录了五只小猪的体重，如：int arr[5]={300,350,200,400,250};找出并打印最重的小猪体重。

代码：

```c++
int arr[5] = { 300,350,200,400,250 };
	int max = 0;
	for (int i = 0; i < 5; i++) {
		if (arr[i] > max) {
			max = arr[i];
		}
	}
	cout << max << endl;

	system("pause");
	return 0;
```

练习案例2：倒叙排列

#### 5.2.3 冒泡排序

作用：最常用的排序算法，对数组内元素进行排序

1、比较相邻的元素，如果第一个比第二个大，就交换他们

2、对每一对相邻元素做同样的工作，执行完毕后找到一个最大值

3、重复以上步骤，每次比较次数-1，直到不需要比较

示例：将数组{4,2,8,0,5,7,1,3,9}做升序排列

```c++
#include<iostream>
using namespace std;

int main()
{
	int arr[9] = {4,2,8,0,5,7,1,3,9 };
	cout << "排序前:" << endl;
	for (int i = 0; i < 9; i++) {
		cout << arr[i] << " ";
	}
	cout << endl;
	//开始冒泡排序
	//排序的总轮数=元素个数-1；
	for (int i = 0; i < 9 - 1; i++) {
		//内层循环对比次数=元素个数-当前轮数-1
		for (int j = 0; j < 9 - i - 1; j++) {
			if (arr[j] > arr[j + 1]) {
				int temp = 0;
				temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
	cout << "冒泡排序后：" << endl;
	for (int i = 0; i < 9; i++) {
		cout << arr[i] << " ";
	}
	cout << endl;

	system("pause");
	return 0;
}
```

**总结：排序的总轮数=元素个数-1；内层循环对比次数=元素个数-当前轮数-1**

### 5.3二维数组

二维数组就是在一维数组上，多加一个维度。

#### 5.3.1二维数组定义方式

二维数组定义的四种方式：

1.数据类型   数组名[行数] [列数];

2.数据类型   数组名[行数] [列数]={{数据1，数据2}，{数据3，数据4}};

3.数据类型   数组名[行数] [列数]={数据1，数据2，数据3，数据4}；

4.数据类型   数组名[] [列数]={数据1，数据2，数据3，数据4}；

建议：以上4种方式，**利用第二种定义方式更加直观，提高代码的可读性。**

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//二维数组的定义方式
	int arr[2][3];
	arr[0][0] = 1;
	arr[0][1] = 2;
	arr[0][2] = 3;
	arr[1][0] = 4;
	arr[1][1] = 5;
	arr[1][2] = 6;
	//外层循环打印行数，内层循环打印列数
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 3; j++) {
			cout << arr[i][j] << endl;
		}
	}

	int arr2[2][3] = {
		{1,2,3},
		{4,5,6}
	};//这种定义方式非常直观，可读性很高
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 3; j++) {
			cout << arr2[i][j] << " ";
		}
		cout << endl;
	}

	int arr3[2][3] = { 2,2,2,4,5,6 };
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 3; j++) {
			cout << arr3[i][j] << " ";
		}
		cout << endl;
	}

	system("pause");
	return 0;
}
```

#### 5.3.2二维数组数组名

- 查看二维数组所占内存空间
- 获取二维数组首地址

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	//二维数组名用途
	//可以查看占用的内存空间大小
	int arr[2][3] = {
		{1,2,3},
		{4,5,6}
	};
	cout << "二维数组占用的内存空间：" << sizeof(arr) << endl;
	cout << "二维数组第一行占用的内存空间：" << sizeof(arr[0]) << endl;
	cout << "二维数组第一个元素占用的内存空间：" << sizeof(arr[0][0]) << endl;
	cout << "二维数组行数为：" << sizeof(arr) / sizeof(arr[0]) << endl;
	cout << "二维数组列数为：" << sizeof(arr[0]) / sizeof(arr[0][0]) << endl;
	
	//可以查看二维数组的首地址
	cout << "二维数组的首地址为：" << (int)arr << endl;
	cout << "二维数组的第一行首地址为：" << (int)arr[0] << endl;
	cout << "二维数组的第二行首地址为：" << (int)arr[1] << endl;
	cout << "二维数组的第一个元素的地址为：" << (int)&arr[0][0] << endl;

	system("pause");
	return 0;
}
```

#### 5.3.3二维数组应用案例

**考试成绩统计：**

案例描述：有三名同学，再一次考试中的成绩如下表，请分别输出三名同学的总成绩

|      | 语文 | 数学 | 英语 |
| ---- | ---- | ---- | ---- |
| 张三 | 100  | 100  | 100  |
| 李四 | 90   | 50   | 100  |
| 王五 | 60   | 70   | 80   |

代码：

```c++
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int arr[3][3] = {
		{100,100,100},
		{90,50,100},
		{60,70,80}
	};
	string names[3] = { "张三","李四","王五" };
	for (int i = 0; i < 3; i++) {
		int sum = 0;
		for (int j = 0; j < 3; j++) {
			sum += arr[i][j];
		}
		cout <<names[i]<<"的总分为：" << sum << endl;
	}
	system("pause");
	return 0;
}#include<iostream>
using namespace std;

int main()
{
	int arr[3][3] = {
		{100,100,100},
		{90,50,100},
		{60,70,80}
	};
	for (int i = 0; i < 3; i++) {
		int sum = 0;
		for (int j = 0; j < 3; j++) {
			sum += arr[i][j];
		}
		cout << sum << endl;
	}
	system("pause");
	return 0;
}
```

注意学习字符串数组的定义。

### 数组大小

```c++
class Entity
{
pubilc:
    static const int exampleSize = 5//提前设置数组的大小
    int example[exampleSize];
    
    Entity()
    {
        for(int i = 0;i < exampleSize; i++)
            example[i] = 2;
    }
    
}
```

### 标准库数组std::array

```c++
#include<array>

class Entity
{
pubilc:
    std::array<int,5> another;
    
    Entity()
    {
        for(int i = 0;i < another.size(); i++)
            example[i] = 2;
    }
    
}
```



## 6 函数

### 6.1 概述

作用：将一段经常使用的代码封装起来，减少重复代码

一个较大的程序，一般分为若干程序块，每个模块实现特定的功能。

### 6.2 函数的定义

函数的定义一般主要有5个步骤：

1、返回值类型

2、函数名

3、参数列表

4、函数体语句

5、return 表达式

语法：

```c++
返回值类型 函数名 (参数列表)
{
    函数体语句
       return 表达式
}
```

### 6.3 函数的调用

功能：使用定义好的函数

语法：函数名 （参数）

示例：

```c++
#include<iostream>
using namespace std;

//函数的定义
int add(int num1, int num2) {
	int sum = num1 + num2;//num1和num2没有实际的值，只是一个形式上的参数，被称为形参。
	return sum;
}

int main()
{
	int a = 10; int b = 20;
	int c = add(a, b);//a，b有实际的值，被称为实际参数，或实参。
	//函数调用时，实参的值会传递给形参
	cout << c << endl;

	system("pause");
	return 0;
}
```

### 6.4 值传递

- 所谓值传递，就是函数调用时实参将数值传入给形参
- 值传递时，**如果形参发生改变，并不会影响实参**

示例：

```c++
#include<iostream>
using namespace std;

//值传递
//定义函数，定义一个两个数字交换的函数
//如果一个函数没有返回值，声明的时候可以写void

void swap(int num1, int num2) {
	cout << "交换前：" << endl;
	cout << "num1=" << num1 << endl;
	cout << "num2=" << num2 << endl;

	int temp = num1;
	num1 = num2;
	num2 = temp;

	cout << "交换后：" << endl;
	cout << "num1=" << num1 << endl;
	cout << "num1=" << num2 << endl;

//return；返回值不需要的时候，可以不写return
}

int main()
{
	int a = 10;
	int b = 20;

	cout << "a=" << a << endl;
	cout << "b=" << b << endl;
	//当值传递时，函数的形参发生改变，并不会影响实参
	swap(a, b);
	cout << "a=" << a << endl;
	cout << "b=" << b << endl;
	system("pause");
	return 0;
}
```

总结：值传递时，形参是修饰不了实参的。

### 6.5 函数的常见样式

常见的函数样式有4种

1、无参无返

2、有参无返

3、无参有返

4、有参有返

示例：

```c++
#include<iostream>
using namespace std;

//常见的函数样式有4种
//1、无参无返
void test01() {
	cout << "this is test01" << endl;
}
//2、有参无返
void test02(int a) {
	cout << "this is test02 a=" << a << endl;
}
//3、无参有返
int test03() {
	cout << "this is test03" << endl;
	return 1000;
}
//4、有参有返
int test04(int a) {
	cout << "this is test04 a=" << a << endl;
	return a;
}

int main()
{
	test01();//无参无返函数的调用
	test02(100);//有参无返函数的调用
	int num1 = test03();//无参有返函数的调用
	cout << "num1=" << num1 << endl;
	int num2 = test04(10000);//有参有返函数的调用
	cout << "num2=" << num2 << endl;
	system("pause");
	return 0;

```

### 6.6 函数的声明

作用：告诉编译器函数名称及如何调用函数，函数的实际主体可以单独定义。

- 函数的声明可以多次，但是函数的定义只能有一次

示例：

```c++
#include<iostream>
using namespace std;

//比较函数，实现两个整型的数字进行比较，返回较大的值
//函数的定义
int max(int a, int b) {
	return a > b ? a : b;
}
//函数的声明，声明可以写多次，但是定义只能有一次
int max(int a, int b);//提前告诉编译器函数的存在，可以利用函数的声明

int main()
{
	int a = 10; int b = 20;
	cout << max(a, b) << endl;
	system("pause");
	return 0;
}
```

### 6.7 函数的份文件编写

作用：让代码结构更加清晰

函数份文件编写一般有4个步骤

1.创建后缀名为.h的头文件

2.创建后缀名为.cpp的源文件

3.在头文件中写函数的声明

4.在源文件中写函数的定义

示例：

```c++
//.h头文件
   #include<iostream>
using namespace std;//头文件不要使用using声明
//函数的声明
void swap(int a, int b);
	
//.cpp的源文件
    #include"swap.h"

void swap(int a, int b) {
	int temp = a;
	a = b;
	b = temp;
	cout << "a=" << a << endl;
	cout << "b=" << b << endl;
}
//源程序
#include<iostream>
using namespace std;
#include"swap.h"
//函数的分文件编写
//实现两个数字的交换的函数


int main()
{
	int a = 10; int b = 20;
	swap(a, b);

	system("pause");
	return 0;
}

```

### 6.8头文件

**当预处理器（preprocessor)看到#include标记时会用指定的头文件的内容代替#include**

头文件保护符：#pragma once

**头文件方括号<>：表示绝对位置，头文件位于include的目录位置**

**头文件双引号“ ”：表示相对于main文件的位置，例如可以用“../头文件名”表示头文件处于main文件的上层目录中**；也可以用于include的目录位置， **所以其实可以在任何地方使用引号**



## 7 指针

### 7.1指针的基本概念

**指针的作用：**可以通过指针间接访问内存

- 内存编号是从0开始记录的，一般用十六进制数字表示
- 可以利用指针变量保存地址
- **指针只是一个存储着内存地址的整数**

### 7.2指针变量的定义和使用

指针变量定义语法：数据类型*指针变量名；

```c++
#include<iostream>
using namespace std;

int main()
{
	//定义一个指针
	int a = 10;
	//指针定义的语法：数据类型*指针变量名；
	int* p;
	//让指针记录变量a的地址
	p = &a;
	cout << "a的地址为：" << &a << endl;
	cout << "指针p=" << p << endl;

	//使用指针:可以通过解引用的方式来找到指针的内存
	//指针前加*代表解引用，找到指针指向的内存中的数据
	*p = 1000;
	cout << "a=" << a << endl;
	cout << "*p=" << *p << endl;

	system("pause");
	return 0;
}
```

### 7.3 指针所占内存空间

提问：指针也是种数据类型，那么这种数据类型占用多少 内存空间呢？

**在32位操作系统下，指针是占4个字节空间大小，不管是什么数据类型**
**在64位操作系统下，指针是占8个字节空间大小**

**指针的类型只是为了，解引用时分配地址，例如*ptr = 10，指针ptr须为整型。**

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int* p = &a;

	//在32位操作系统下，指针是占4个字节空间大小，不管是什么数据类型
	//在64位操作系统下，指针是占8个字节空间大小
	cout << "int*所占的内存空间为多少：" << sizeof(int*) << endl;
	cout << "int*所占的内存空间为多少：" << sizeof(float*) << endl;
	cout << "int*所占的内存空间为多少：" << sizeof(double*) << endl;
	cout << "int*所占的内存空间为多少：" << sizeof(char*) << endl;

	system("pause");
	return 0;
}
```

### 7.4 空指针和野指针

**空指针：**指针变量指向内存中编号为0的空间

**用途：**初始化指针变量

**注意：**空指针指向的内存是不可以访问的

**示例1：空指针**

```c++
#include<iostream>
using namespace std;

int main()
{
	//空指针用于给指针变量初始化
	int* p = NULL;
	
	//空指针是不可以进行访问的
	//0-255之间的内存编号是系统占用的，因此不可以访问。
	*p = 100;

	system("pause");
	return 0;
}
```

野指针：指针变量指向非法的内存空间

**示例2：野指针**

```c++
#include<iostream>
using namespace std;

int main()
{
	//野指针
	//在程序中，避免野指针
	int* p = (int*)0x1100;
	cout << *p << endl;

	system("pause");
	return 0;
}
```

### 7.5const修饰指针

const修饰指针有三种情况：

1.const修饰指针---常量指针

2.const修饰常量---指针常量

3.const即修饰指针，又修饰常量

### 7.6利用指针访问数组

示例：

```c++
#include<iostream>
using namespace std;

int main()
{
	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	int* p = arr;
	cout << *p << endl;
	p++;
	cout << *p << endl;
	int* p2 = arr;
	for (int i = 0; i < 10; i++) {
		cout << *p2 << endl;
		p2++;
	}//利用指针遍历数组

	system("pause");
	return 0;
}

```

### 7.7指针和函数

作用：利用指针作为函数的参数，可以改变实参的值。

```c++
#include<iostream>
using namespace std;

//地址
void swap(int* p1, int* p2) {
	int temp = *p1;
	*p1 = *p2;
	*p2 = temp;
}

int main()
{
	int a = 10, b = 20;
	cout << "a=" << a << endl
		<< "b=" << b << endl;
	swap(&a, &b);
	cout << "a=" << a << endl
		<< "b=" << b << endl;

	system("pause");
	return 0;
}

```

总结：如果不想修改实参则用值传递，如果想修改实参，则用地址传递。

## 8 结构体

结构体属于用户自定义的数据类型，允许用户存储不同的数据类型。

### 8.1结构体定义和使用

注：**包含来自标准库文件时，应该用尖括号<>包围头文件，对于不属于标准库的头文件，则用双引号“”包围。**

注:**头文件一般不包括using声明**

类的头文件编写：

```c++
#ifndef SALES_DATA_H //头文件保护符
#define SALES_DATA_H //把一个名字设定为预处理变量
#include<string>
struct Sales_data
{
	std::string bookno;
	unsigned soldnum=0;
	double revenue = 0.0;
};//注意分号
#endif // !SALES_DATA_H

```

源文件编写：

```c++
#include<string>
#include<iostream>
#include"Sales_data.h"
using namespace std;

int main()
{
	Sales_data data1, data2;//struct省略，struct Sales_data data1, data2;
	double price = 0;
	cin >> data1.bookno >> data1.soldnum >> price;
	data1.revenue = price * data1.soldnum;
	cout << data1.bookno << " " << data1.soldnum << " " << data1.revenue << endl;
	cin >> data2.bookno >> data2.soldnum >> price;
	data2.revenue = price * data2.soldnum;
	cout << data2.bookno << " " << data2.soldnum << " " << data2.revenue << endl;

	if (data1.bookno == data2.bookno) {
		unsigned totalnum = data1.soldnum + data2.soldnum;
		double totalrevenve = data1.revenue + data2.revenue;
		if (totalnum != 0) {
			double averprice = totalrevenve / totalnum;
			cout << "totalnumber=" << totalnum << endl
				<< "totalrevenve=" << totalrevenve << endl
				<< "average price=" << averprice << endl;
		}
		else {
			cout << "no sales" << endl;
		}
	}
	else {
		cout << "wrong" << endl;
	}

	system("pause");
	return 0;
}
```

### 8.2结构体数组

**作用：**将自定义的结构体放入数组中方便维护

**语法：**struct  结构体名  数组名[元素个数]={{}，{}，{}}；

```c++
#include<iostream>
#include<string>
using namespace std;

struct Student
{
	string name;
	int age;
};

int main()
{
	struct Student arr[2] = {
		{"jack",22},{"jay",23}
	};
	for (int i = 0; i < 2; i++) {
		cout << "name:" << arr[i].name<<" " << "age:" << arr[i].age << endl;
	}

	system("pause");
	return 0;
}
```

### 8.3结构体指针

作用：通过指针访问结构体成员

利用操作符  ->  可以通过结构体指针访问结构体属性；

```c++
#include<iostream>
#include<string>
using namespace std;

struct Student
{
	string name;
	int age;
};

int main()
{
	Student s1 = { "Jack",18 };
	Student* p = &s1;
	cout << "name:" << p->name<<" " << "age:" << p->age << endl;
	
	system("pause");
	return 0;
}
```

### 8.4结构体作为函数参数

将结构体作为函数参数传递

传递方式:

- 值传递
- 地址传递

```c++
#include<iostream>
#include<string>
using namespace std;

struct Student
{
	string name;
	int age;
};

void printstudent(struct Student *p) {//struct可以
	cout << "name:" << p->name << " " << "age:" << p->age << endl;
}

int main()
{
	Student s1 = { "Jack",18 };
	printstudent(&s1);

	system("pause");
	return 0;
}
```

# C++核心编程

本阶段主要针对C++面向对象编程

## 1内存分区模型

C++在执行程序的时，内存大方向分为4个区域

- 代码区：存放函数体的二进制代码，由操作系统管理
- 全局区：存放全局变量、静态变量以及常量
- 栈区：由编译器自动分配，存放函数的参数值、局部变量等
- 堆区：由程序员分配和释放

### 1.1**程序运行前：**

c++程序运行前，分为全局区和代码区

代码区的特点是只读和共享

全局区中存放全局变量、静态变量以及常量

常量存放const修饰的全局常量 和 字符串常量

### 1.2**程序运行后**：

利用new关键字可以把内存开辟到堆区

指针的本质也是局部变量，保存在栈上，指针保存的的数据放在堆区。

**int *p  =  new  int(10);**

![image-20220302100615734](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220302100615734.png)

### 1.3 new操作符

c++利用**new操作符**在堆区开辟数据

堆区开辟的数据，可以利用**操作符delete**释放

语法：new 数据类型

new创建的数据，会返回改数据对应的类型的数据。

```c++
#include<iostream>
#include<string>
using namespace std;

int* fanc() {//int* 类型的函数
	int* p = new int(10);
	return p;
}

void test() {
	int* p = fanc();
	cout << *p << endl;
	cout << *p << endl;
	cout << *p << endl;
	delete p;//释放内存
}

void fan() {
	int* arr = new int[10];//new定义的int数组
	for (int i = 0; i < 10; i++) {
		arr[i] = 100 + i;
	}
	for (int j = 0; j < 10; j++) {
		cout << arr[j] << endl;
	}
    delete[] arr;
}

int main()
{
	test();
	fan();

	system("pause");
	return 0;
}

```

## 2引用

### 2.1引用的基本使用

作用：给对象起别名

语法：数据类型  &别名  = 原名

### 2.2引用的注意事项

- **引用必须初始化**
- **引用初始化以后，不可以改变**

### 2.3引用做函数参数

**作用：**函数传递时，可以利用引用的技术让形参修饰实参

**优点**：可以简化指针修改实参

```c++
#include<iostream>
#include<string>
using namespace std;

void swap(int* p1, int* p2) {
	int temp = *p1;
	*p1 = *p2;
	*p2 = temp;
}

void swap02(int& x, int& y) {
	int temp = x;
	x = y;
	y = temp;
}

int main()
{
	int a = 10, b = 20;
	swap(&a, &b);
	cout << "a=" << a <<endl << "b=" << b << endl;
	swap02(a, b);
	cout << "a=" << a << endl << "b=" << b << endl;

	system("pause");
	return 0;
}
```

### 2.4 引用做函数返回值

注意：**不要返回局部变量引用**

用法：函数调用作为左值

![image-20220302200239337](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220302200239337.png)

### 2.5引用的本质

**本质：应用的本质在C++内部实现一个指针常量**

![image-20220302200803005](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220302200803005.png)

结论：c++推荐使用引用技术，因为语法方便，引用本质是指针常量。

2.6 常量引用

作用：常量引用主要用来休书形参，防止误操作

在函数形参列表中，可以加const修饰形参，防止形参改变实参

![image-20220302201610567](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220302201610567.png)

## 3函数提高

### 3.1函数默认参数

在c++中，函数的形参列表中的形参是可以有默认值的。

语法：返回值类型  函数名  （参数= 默认值）{}

![image-20220303094448846](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220303094448846.png)

### 3.2函数占位参数

c++中函数的形参列表里可以有占位参数。用来做占位，调用函数时必须填补该位置。

语法： 返回值类型  函数名 （数据类型）{}

![image-20220303095432408](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220303095432408.png)

### 3.3函数重载

#### 3.3.1函数重载概述

**作用**：函数名可以调用，提高复用性

**函数重载满足条件**：

- 同一个作用域下
- 函数名称相同
- 函数参数类型不同 或者 个数不同 或者 顺序不同

注意：函数的返回值不可以作为函数重载的条件

![image-20220303101509339](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220303101509339.png)

![image-20220303101529302](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220303101529302.png)

## 4类和对象

c++面向对象的三大特性：封装、继承、多态

c++认为万事万物皆为对象，对象上有其属性和行为

### 4.1封装

#### 4.1.1封装的意义

封装的意义：

- 将属性和行为作为一个整体，表现生活中的事物
- 将属性和行为加以权限控制

语法：class  类名{   访问权限： 属性  /   行为}；

注：类中的属性和行为，统一称为成员

**属性称为成员属性，成员变量**

**行为称为成员函数，成员方法**

把客观事物封装成抽象的类，并且类可以把自己的数据和方法只让可信的类或者对象操作，对不可信的进行信息隐藏。关键字：public, protected, private。不写默认为 private。

- `public` 成员：可以被任意实体访问
- `protected` 成员：只允许被子类及本类的成员函数访问
- `private` 成员：只允许被本类的成员函数（作用域内）、友元类或友元函数访问

### 继承

示例1：设计一个圆，求圆的周长

```c++
#include<iostream>
#include<string>
using namespace std;
const double PI = 3.14;

class Circle {
public://访问权限，公共权限
	int r;//属性，半径
	double calcuateZC() {
		return 2 * PI * r;
	}//定义行为，一般为函数
};

int main()
{
	Circle c1;
	c1.r = 10;
	cout << "zhouchang:" << c1.calcuateZC() << endl;

	system("pause");
	return 0;
}
```

示例2：设计一个学生类，属性有姓名和学号，可以给姓名和学号赋值，可以显示学生的姓名和学号

```c++
#include<iostream>
#include<string>
using namespace std;

class Student {
public:
	string name;
	string ID;

	void SHUCHU() {
		cout << "NAME:" << name << "\t" << "ID:" << ID << endl;	
	}

	void SetNAME(string Iname) {
		name = Iname;
	}
	void SetID(string id) {
		ID = id;
	}
};

int main()
{
	Student S1;//实例化具体对象
	S1.ID = "1";
	S1.name = "jack";
	S1.SHUCHU();

	Student S2;
	S2.SetID("2");
	S2.SetNAME("jay");
	S2.SHUCHU();

	system("pause");
	return 0;
}
```

类在设计时，可以把属性和行为放在不同的权限下，加以控制

访问权限有三种：

1. public     公共权限     成员  类内可以访问，类外可以访问
2. protecte 保护权限     成员  类内可以访问，类外不可以访问
3. private    私有权限     成员  类内可以访问，类外不可以访问

#### 4.1.2 struct和calss的区别

在c++中struct和class唯一的区别就在于**默认的访问权限不同**

区别：

- struct**默认权限为公共**
- class**默认权限为私有**

#### 4.1.3成员属性设为私有

优点1：将所有成员属性设置为私有，可以自己控制读写权限

优点2：对于写权限，可以检测数据的有效性

```c++
#include<iostream>
#include<string>
using namespace std;

class Student {
public://公共接口
	//设置姓名
	void setname(string iname) {
		name = iname;
	}
	//获取姓名
	string getname() {
		return name;
	}
	//获取id
	int getid() {
		int ID = 0;
		return ID;
	}
	//设置分数
	void getscore(int iscore) {
		if (iscore < 0 || iscore>100) {//设置范围，检测数据有效性
			int score = 0;
			return;
		}
		score = iscore;
	}

private:
	string name;//可读可写
	string ID;//只读
	int score;//只写
};

int main()
{
	Student S1;
	S1.setname("jack");
	S1.getscore(100);
	cout << "name:" << S1.getname() << endl;
	
	system("pause");
	return 0;
}
```

### 4.2对象的初始化和清理

#### 4.2.1构造函数和析构函数

对象的初始化和清理也是两个非常重要的安全问题

c++利用了构造函数和析构函数解决上述问题，**这两个函数会被编译器自动调用。**

- 构造函数：**主要作用在于创建对象时为对象的成员属性赋值**，构造函数由编译器自动调用，无需手动调用。
- 析构函数：**主要作用在于对象销毁前系统自动调用**（实例对象在作用域结束后会被销毁），执行一些清理工作。



#### 4.2.2构造函数的分类及调用

**两种分类方式;**

按参数分：有参构造和无参构造

按类型分：普通构造和拷贝构造

**三种调用方式：**

括号法；

显示法；

隐式转换法；

```c++
#include<iostream>

class Entity
{
public:
	float X, Y;

	Entity()//无参构造函数
	{
		X = 0.0f;
		Y = 0.0f;
	}

	Entity(float x, float y)//有参构造函数
	{
		X = x;
		Y = y;
	}

	void Print()
	{
		std::cout << X << "," << Y << std::endl;
	}
};

class Log
{
private:
	Log(){}//将构造函数设置为隐私，则该类不可以被实例化。

public:
	static void Write() {

	}

};

int main()
{
	//Log l;
	Log::Write();
	Entity e(10.0f,5.0f);
	std::cout << e.X << std::endl;
	e.Print();
	std::cin.get();
}
```



#### 4.2.3拷贝构造函数的调用时机

c++中拷贝构造函数的调用时机通常有3种情况；

- 使用一个已经创建完毕的对象来初始化另一个对象
- 值传递的方式给函数参数传值
- 以值方式返回局部对象

```c++
class Person {
public:
	Person() {//构造函数
		cout << "wuchangouzhao" << endl;
	}
	Person(int age) {
		m_age = age;
		cout << "youcangouzhao" << endl;
	}
	Person(const Person& p) {
		m_age = p.m_age;
		cout << "kaobeigouzhao" << endl;
	}
	~Person() {
		cout << "xigouhanshu" << endl;
	}
	int m_age;
};

void test01() {//使用一个已经创建完毕的对象来初始化另一个对象
	Person p1(20);
	Person p2(p1);

	cout << p2.m_age << endl;
}

void temp(Person p) {

}

void test02() {//值传递的方式给函数参数传值
	Person p;
	temp(p);
}

Person temp2() {
	Person p1;
	return p1;
}

void test03() {//以值方式返回局部对象
	Person p1 = temp2();
}

int main()
{
	//test01();
	//test02();
	test03();
	system("pause");
	return 0;
}
```

#### 4.2.4构造函数调用规则

默认情况下，c++至少给一个类添加3个函数

1. 默认构造函数，无参，函数体为空
2. 默认析构函数，无参，函数体为空
3. 默认拷贝构造函数，对属性进行值拷贝

构造函数调用规则如下：

- **如果用户定义了有参构造函数，编译器不再提供默认无参构造，但会提供默认拷贝构造**
- **如果用户定义了拷贝构造函数，编译器不在提供其他构造函数**

#### 4.2.5深拷贝和浅拷贝

#### 4.2.6初始化列表

作用：初始化属性

语法：构造函数（）：属性1（值1），属性2（值2），...{ }

```c++
class Person {
public:
	Person(int a, int b, int c) :A(a),B(b),C(c){//初始化列表

	}

		int A, B, C;
};

void test01() {
	Person p(10,20,30);
	cout << "A=" << p.A << endl << "B=" << p.B << endl
		<< "c=" << p.C << endl;
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```

#### 4.2.7类对象作为类成员

类中的成员可以是另一个类的对象，我们称该成员为对象成员

示例：

![image-20220305162329174](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220305162329174.png)

#### 4.2.8static

**类外的static**

static变量或函数表示在link到它实际的定义时，linker不会在这个编译单元.obj外面找它的定义。即是static变量和函数只在它所在的编译单元有效。

**注：尽量让全局函数和变量用static标记。**

局部的static变量，可以让变量的生命周期变为永久。



**类内的static**

**静态成员就是在成员变量或者成员函数前加上关键字static，称为静态成员。**

静态成员分为：

- 静态成员变量
  1. 所有对象共享同一份数据
  2. 在编译阶段分配内存
  3. **类内声明，类外初始化**
  
- 静态成员函数：不通过类的实例就可以调用（使用类名加范围解析运算符::就可以访问

  1. 所有对象共享一个函数

     2.**静态成员函数只能访问静态成员变量**（因为静态方法没有类实例，本质上在类里的每个非静态方法都会获得当前的类实例作为参数this指针）

静态成员变量：

```c++
class Person {
public:
	static int m_A;//类内声明

	//静态成员变量也有访问权限
private:
	static int m_B;
	
};

 int Person::m_A = 100;  //类外初始化
 int Person::m_B = 200;

void test01() {
	Person p1;
	cout << p1.m_A << endl;
	Person p2;
	p2.m_A = 200;
	cout << p1.m_A << endl;//共享同一份值
}

void test02() {
	//静态成员变量不属于任何一个对象，因为所有对象共享同一份数据
	//静态成员变量有两种访问方法
	//1,通过对象访问
	Person p1;
	cout << p1.m_A << endl;
	//2、通过类名进行访问
	cout << Person::m_A << endl;
}

int main()
{
	//test01();
	test02();

	system("pause");
	return 0;
}
```

#### 虚函数和纯虚函数

- 类里如果声明了虚函数，这个函数是实现的，哪怕是空实现，它的**作用就是为了能让这个函数在它的子类里面可以被覆盖（override）**，这样的话，编译器就可以使用后期绑定来达到多态了。纯虚函数只是一个接口，是个函数的声明而已（并不包括方法的实现），要留到子类里去实现。
- 虚函数在子类里面可以不重写；但**纯虚函数必须在子类实现才可以实例化子类。（只能实例化一个实现了所有纯虚函数的类）**
- 虚函数的类用于 “实作继承”，继承接口的同时也继承了父类的实现。纯虚函数关注的是接口的统一性，实现由子类完成。
- 带纯虚函数的类叫抽象类，这种类不能直接生成对象，而只有被继承，并重写其虚函数后，才能使用。抽象类被继承后，子类可以继续是抽象类，也可以是普通类。
- 虚基类是虚继承中的基类，具体见下文虚继承。



### 4.3c++对象模板和this指针

#### 4.3.1成员变量和成员函数分开存储

在c++中，类内的成员变量和成员函数分开存储

只有非静态成员变量才属于类的对象上

#### 4.3.2this指针概念

c++通过提供特殊的对象指针，this指针，解决上述问题，**this指针指向被调用的成员函数所属的对象**

**this指针是隐含每一个非静态函数内的一种指针**

this指针不需要定义，直接使用即可

this指针的用途：

- 当形参和成员变量重名时，可以用this指针来区分
- 在类的非静态成员函数中返回对象本身，可以使用return *this

```c++
class Person {
public:
	Person(int age) {
		m_age = age;
	}
	Person& addage(Person &p) {//Person&返回p2本身
		this->m_age += p.m_age;//this可以省略
		return *this;
	}

	int m_age;
}；
 
void test01() {
	Person p1(10);
	Person p2(10);
	p2.addage(p1).addage(p1).addage(p1);//this指p2
	cout << p2.m_age << endl;
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```

#### 4.3.3空指针访问成员函数

c++中空指针也能调用成员函数，但要注意有没有用到this指针

#### 4.3.4const修饰成员函数

**常函数：**

- 成员函数后加const，称为常函数
- 常函数不可以修改成员属性
- 成员属性声明时加关键字mutable后，在常函数中依然可以修改

**常对象：**

- 声明对象前加const称为常对象
- 常对象只能调用常函数

#### const

**作用:**

1. 修饰变量，说明该变量不可以被改变；
2. 修饰指针，分为指向常量的指针（pointer to const）和自身是常量的指针（常量指针，const pointer）；
3. 修饰引用，指向常量的引用（reference to const），用于形参类型，即避免了拷贝，又避免了函数对值的修改；
4. 修饰成员函数，说明该成员函数内不能修改成员变量。

#### const 的指针与引用

- 指针
  - 指向常量的指针（pointer to const）
  - 自身是常量的指针（常量指针，const pointer）
- 引用
  - 指向常量的引用（reference to const）
  - **没有 const reference，因为引用只是对象的别名，引用不是对象，不能用 const 修饰**

> （为了方便记忆可以想成）被 const 修饰（在 const 后面）的值不可改变，如下文使用例子中的 `p2`、`p3`

### 4.4友元

在c++中，**有些私有属性，也想让类外特殊的一些函数进行访问，**就需要用到友元技术。

友元的目的就是让一个函数或者类访问另一个类中的私有成员

友元的关键字：**friend**

友元的三种实现

- 全局函数做友元
- 类做友元
- 成员函数做友元

4.4.1全局函数做友元

![image-20220306154826890](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220306154826890.png)

#### 4.4.2类作友元

![image-20220306160830856](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220306160830856.png)

![image-20220306160901335](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220306160901335.png)

4.4.3成员函数做友元

![image-20220306162201436](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220306162201436.png)

### 4.5运算符重载

运算符重载：对原有的运算符重新进行定义，赋予其另一种功能，已适应不同的数据类型。

**注：运算符重载也可以发生函数重载**

#### 4.5.1加号运算符重载

作用：实现两个自定义数据类型的运算

```c++
#include<iostream>
#include<string>
using namespace std;

class Person {
public:
	//Person operator+(Person& p) {//成员函数重载加号
	//	Person temp;
	//	temp.m_a = this->m_a + p.m_a;
	//	temp.m_b = this->m_b + p.m_b;
	//  return temp;
	//}

	int m_a;
	int m_b;
};

Person operator+(Person& p1, Person& p2) {//全局函数重载加号
	Person temp;
	temp.m_a = p1.m_a + p2.m_a;
	temp.m_b = p1.m_b + p2.m_b;
	return temp;
}

Person operator+(Person& p1, int a) {//运算符重载也可以发生函数重载
	Person temp;
	temp.m_a = p1.m_a + a;
	temp.m_b = p1.m_b + a;
	return temp;
}

void test01() {
	Person p1, p2, p3,p4;
	p1.m_a = 10;
	p1.m_b = 10;
	p2.m_a = 10;
	p2.m_b = 10;
	p3 = p1 + p2;
	p4 = p1 + 100;
	cout << p3.m_a << endl;
	cout << p3.m_b << endl;
	cout << p4.m_a << endl;
	cout << p4.m_b << endl;
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```

#### 4.5.2左移运算符重载

#### 4.5.3递增运算符重载

#### 4.5.4赋值运算符重载

#### 4.5.5关系运算符重载

#### 4.5.6函数调用运算符重载

### 4.6继承

**继承是面向对象的三大特性之一**

有些类与类之间存在特殊关系，例如下图中：

![image-20220307105448865](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220307105448865.png)

我们发现，定义这些类的时，下级别的成员除了拥有上一级的共性，还有自己的特性。

这个时候我们可以利用继承技术，减少重复代码。

#### 4.6.1继承的基本语法

语法：class  子类：  继承方式  父类

子类  也称为  派生类

父类  也称为  基类

```c++
#include<iostream>
#include<string>
using namespace std;

class Basepage {
public:
	void header() {
		cout << "header" << endl;
	}
	void footer() {
		cout << "footer" << endl;
		cout << "---------------" << endl;
	}
	void left() {
		cout << "left" << endl;
	}
};

class java :public Basepage {
public:
	void content() {
		cout << "java" << endl;
	}
};

class python :public Basepage {
public:
	void content() {
		cout << "python" << endl;
	}
};

class cpp :public Basepage {
public:
	void content() {
		cout << "c++" << endl;
	}
};

void test01() {
	java ja;
	ja.header();
	ja.left();
	ja.content();
	ja.footer();
	python py;
	py.header();
	py.left();
	py.content();
	py.footer();
	cpp c;
	c.header();
	c.left();
	c.content();
	c.footer();
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```

#### 4.6.2继承方式

继承方式一共有三种

- 公共继承
- 保护继承
- 私有继承

#### 4.6.3继承中的对象模型

**父类中所有非静态的成员属性都会被子类继承**

#### 4.6.4继承中的构造和析构顺序

子类继承父类后，创建子类对象，也会调用父类的构造函数

继承中的构造和析构顺序如下：

**先构造父类，再构造子类，析构的顺序与构造的顺序相反**

#### 4.6.5继承同名成员处理方式

问题：当子类与父类出现同名的成员，如何通过子类对象，访问到子类或父类中的同名的数据？

- 访问子类同名成员  直接访问
- 访问父类同名成员  需要加作用域

#### 4.6.6继承同名静态成员处理方式

静态成员和非静态成员出现同名，处理方式一致

- 访问子类同名成员  直接访问
- 访问父类同名成员  需要加作用域



#### 4.6.7多继承语法

c++允许**一个类继承多个类**

语法：class  子类：继承方式  父类1，继承方式  父类2...

**c++实际开发中不建议用多继承**

#### 4.6.8菱形继承

菱形继承概念：

两个派生类继承同一个基类

又有某个类同时继承这两个派生类

这种继承被称为菱形继承，又称钻石继承

### 4.7多态

#### 4.7.1多态的基本概念

多态是C++面向对象三大特性之一

多态分为两类：

- 静态多态：函数重载和运算符重载属于静态多态，复用函数名
- 动态多态：派生类和虚函数实现运行时多态

静态多态和动态多态的区别：

- 静态多态的函数地址早绑定--编译阶段确定函数地址
- 动态多态的函数地址晚绑定--运行阶段确定函数地址

![image-20220408160315932](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\image-20220408160315932.png)

## 5文件操作

c++中对文件操作需要包含头文件`<fstream>`

文件类型分为两种:

1.**文本文件**文件以文本的ASCII码形式存储在计算机中

2.**二进制文件**-文件以文本的二进制形式村组在计算机中，用户一般不能直接读懂



操作文件的三大类：

1.ofstream：学操作

2.ifstream：读操作

3.fstream：读文件

### 5.1文本文件

#### 5.1.1写文件

写文件步骤如下：

1.包含头文件

`#include <fstream>`

2.创建流对象

`ofstream  ofs`

3.打开文件

`ofs.open("文件路径"，打开方式)`

4.写数据

`ofs<<"写入的数据"；`

5.关闭文件

`ofs.close(); ``

## Vector容器

vector就是一组类型相同的数据对象的集合。、

初始化方法

```c++
#include<iostream>
#include<vector>

using namespace std;

int main()
{
	//默认初始化 vector<类型名> 标识符
	vector<int> v1;
	vector<char> v2 = { 'a','b','c' };
	vector<char> v3{ 'a','b','c' };

	//直接初始化
	vector<int> v4(5); //创建了有5个元素的容器，类型都为short
	vector<long> v5(5, 100); //创建了有5个元素的容器，类型都是long，值都为100.
}
```

