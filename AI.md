# C++入门复习资料（变量、运算符、流程控制）  
**适用对象**：C++新学员（已学变量，用VSCode编译器）  
**编写说明**：整合聊天记录核心知识点，含案例代码、通俗解释、总结练习，语言浅显，适合复习。  


## 一、变量（Variable）  
**核心概念**：变量是内存中“贴标签的盒子”，用于存储数据（数字、文字等），可随时修改内容。  


### 1.1 变量的声明与初始化  
**语法**：`类型 变量名 = 初始值;`（声明同时赋值）  
**常用类型**：`int`（整数）、`double`（双精度浮点数）、`char`（单个字符）、`string`（字符串，需`#include <string>`）  

#### 案例1.1：整数变量（int）  
```cpp
#include <iostream>
using namespace std;
int main() {
    int age = 18; // 声明int变量age，初始化为18
    cout << "我的年龄是：" << age << endl; // 输出：我的年龄是：18
    return 0;
}
```  

#### 案例1.2：浮点数变量（double）  
```cpp
#include <iostream>
using namespace std;
int main() {
    double price = 19.99; // double变量price，初始化为19.99
    cout << "这本书的价格是：$" << price << endl; // 输出：这本书的价格是：$19.99
    return 0;
}
```  

#### 案例1.3：字符变量（char）  
```cpp
#include <iostream>
using namespace std;
int main() {
    char grade = 'A'; // char变量grade，初始化为'A'（单引号）
    cout << "我这次考试得了：" << grade << endl; // 输出：我这次考试得了：A
    return 0;
}
```  

#### 案例1.4：字符串变量（string）  
```cpp
#include <iostream>
#include <string> // 需包含string头文件
using namespace std;
int main() {
    string name = "小明"; // string变量name，初始化为"小明"（双引号）
    cout << "你好，" << name << "！" << endl; // 输出：你好，小明！
    return 0;
}
```  


### 1.2 变量的赋值  
**语法**：`变量名 = 新值;`（声明后修改值）  

#### 案例2.1：整数重新赋值  
```cpp
#include <iostream>
using namespace std;
int main() {
    int score = 85; 
    cout << "第一次测验成绩：" << score << endl; // 输出：85
    score = 92; // 重新赋值
    cout << "第二次测验成绩：" << score << endl; // 输出：92
    return 0;
}
```  

#### 案例2.2：计算后赋值  
```cpp
#include <iostream>
using namespace std;
int main() {
    int a = 10, b = 20;
    int sum = a + b; // 计算a+b，赋值给sum
    cout << a << " + " << b << " = " << sum << endl; // 输出：10 + 20 = 30
    sum = sum + 5; // sum累加5
    cout << "加上5之后：" << sum << endl; // 输出：35
    return 0;
}
```  

#### 案例2.3：交换两个变量（借助临时变量）  
```cpp
#include <iostream>
using namespace std;
int main() {
    int x = 5, y = 10;
    int temp = x; // 临时保存x
    x = y; y = temp; // 交换
    cout << "交换后: x=" << x << ", y=" << y << endl; // 输出：x=10, y=5
    return 0;
}
```  


### 1.3 变量的类型  
**常用类型对比**：  
| 类型    | 用途                  | 示例               |  
|---------|-----------------------|--------------------|  
| `int`   | 整数                  | `int age=20;`       |  
| `double`| 双精度浮点数（小数）  | `double pi=3.14;`   |  
| `float` | 单精度浮点数（精度低）| `float f=2.7f;`（`f`后缀） |  
| `char`  | 单个字符              | `char c='A';`       |  
| `bool`  | 布尔值（true/false）  | `bool flag=true;`   |  
| `string`| 字符串（文本）        | `string s="Hello";` |  

#### 案例3.1：float与double精度差异  
```cpp
#include <iostream>
#include <iomanip> // 控制输出格式
using namespace std;
int main() {
    float f_pi = 3.1415926535f; 
    double d_pi = 3.1415926535;
    cout << fixed << setprecision(10); // 固定小数点，保留10位小数
    cout << "float pi: " << f_pi << endl;  // 输出：3.1415927410（精度低）
    cout << "double pi: " << d_pi << endl; // 输出：3.1415926535（精度高）
    return 0;
}
```  

#### 案例3.2：bool类型用法  
```cpp
#include <iostream>
using namespace std;
int main() {
    bool isRaining = true;
    cout << "下雨了吗？" << (isRaining ? "是" : "否") << endl; // 输出：是
    return 0;
}
```  

#### 案例3.3：string拼接（含类型转换）  
```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string name = "张三";
    int age = 20;
    string info = name + "的年龄是" + to_string(age) + "岁。"; 
    // to_string(age)将int转为string，拼接结果："张三的年龄是20岁。"
    cout << info << endl; 
    return 0;
}
```  


### 1.4 变量的命名规则  
**规则**：  
- 只能含字母、数字、下划线（`_`），不能以数字开头；  
- 区分大小写（`myVar`≠`myvar`）；  
- 不能用关键字（如`int`、`class`）；  
- 见名知意（如`studentCount`优于`sc`）。  

#### 案例4.1：合法命名示例  
```cpp
int student_count = 30; // 下划线分隔，有意义
double accountBalance = 1500.75; // 驼峰命名法（首字母小写，后续单词首字母大写）
```  


### 1.5 变量的作用域（初步）  
**局部变量**：函数内部声明（如`main`函数内），仅在函数内有效，函数结束销毁。  

#### 案例5.1：局部变量生命周期  
```cpp
#include <iostream>
using namespace std;
void func() {
    int local = 100; // 仅在func内可见
    cout << "func内：" << local << endl;
}
int main() {
    int local = 50; // 仅在main内可见
    cout << "main内：" << local << endl; 
    func(); 
    // cout << local_in_func << endl; // 错误：main访问不到func的变量
    return 0;
}
```  


### 变量总结  
- **三要素**：类型（如`int`）、名字（如`age`）、值（如`18`）；  
- **操作**：声明（`int a;`）、初始化（`int a=5;`）、赋值（`a=10;`）；  
- **练习**：模仿案例敲代码，尝试修改变量值观察输出。  


## 二、运算符（Operators）  
**核心概念**：对变量进行计算、比较、逻辑判断的符号，分4类。  


### 2.1 算术运算符（+、-、*、/、%、++、--）  
**案例1.1：四则运算**  
```cpp
int a=10, b=3;
cout << a/b << endl; // 整数除法：3（舍去小数）
double c=10.0, d=3.0;
cout << c/d << endl; // 浮点数除法：3.33333
```  

**案例1.2：取余（%）判断奇偶**  
```cpp
int num=17;
if (num%2 == 0) cout << "偶数"; else cout << "奇数"; // 输出：奇数
```  

**案例1.3：自增（++）前置vs后置**  
```cpp
int x=5;
cout << x++ << endl; // 后置：先输出5，x变为6
cout << ++x << endl; // 前置：x先变为7，输出7
```  


### 2.2 赋值运算符（=、+=、-=、*=等）  
**案例2.1：复合赋值简化代码**  
```cpp
int x=10;
x += 5; // 等价于x=x+5 → x=15
x *= 2; // 等价于x=x*2 → x=30
```  


### 2.3 比较运算符（==、!=、>、<、>=、<=）  
**结果**：`bool`类型（`true`/`false`，输出用1/0表示）。  

**案例3.1：成绩等级判断**  
```cpp
int score=85;
if (score>=90) cout << "优秀";
else if (score>=80) cout << "良好"; // 输出：良好
```  


### 2.4 逻辑运算符（&&、||、!）  
**案例4.1：逻辑与（&&）判断网吧准入**  
```cpp
int age=20; bool hasID=true;
bool canEnter = (age>=18) && hasID; // true（能进入）
```  

**案例4.2：短路求值特性**  
```cpp
int a=5, b=10;
bool res = (a>10) && (++b>5); // a>10为假，右边++b不执行，b仍为10
```  


### 运算符总结  
- **算术**：数学计算；**赋值**：存值（`+=`简化代码）；  
- **比较**：判断大小（结果true/false）；**逻辑**：组合条件（`&&`且、`||`或、`!`非）；  
- **练习**：写简易计算器（输入两数+运算符，计算结果）。  


## 三、流程控制（Control Flow）  
**核心概念**：让程序“做选择”（条件语句）或“重复做事”（循环语句）。  


### 3.1 条件语句（if-else、switch-case）  
#### 3.1.1 if-else（灵活判断）  
**案例1.1：单分支if（及格判断）**  
```cpp
int score=75;
if (score>=60) cout << "及格了！"; // 输出：及格了！
```  

**案例1.2：多分支if-else if（成绩等级）**  
```cpp
int score=85;
if (score>=90) cout << "优秀";
else if (score>=80) cout << "良好"; // 输出：良好
```  

#### 3.1.2 switch-case（固定值选择）  
**案例2.1：菜单选择**  
```cpp
int choice;
cin >> choice;
switch(choice) {
    case 1: cout << "加法"; break;
    case 2: cout << "减法"; break;
    default: cout << "输入错误";
}
```  


### 3.2 循环语句（while、for、do-while）  
#### 3.2.1 while循环（先判断后执行）  
**案例3.1：累加1-100**  
```cpp
int sum=0, num=1;
while (num<=100) { sum += num; num++; }
cout << "总和：" << sum << endl; // 输出：5050
```  

#### 3.2.2 for循环（计数专用，简洁）  
**案例4.1：打印1-5**  
```cpp
for (int i=1; i<=5; i++) cout << i << " "; // 输出：1 2 3 4 5
```  

**案例4.2：九九乘法表（双重循环）**  
```cpp
for (int i=1; i<=9; i++) {
    for (int j=1; j<=i; j++) 
        cout << j<<"×"<<i<<"="<<i*j<<"\t"; 
    cout << endl;
}
```  

#### 3.2.3 do-while循环（先执行后判断）  
**案例5.1：猜数字游戏**  
```cpp
int secret=5, guess;
do {
    cin >> guess;
    if (guess<secret) cout << "太小";
} while (guess!=secret); // 猜对才停止
```  


### 3.3 循环控制（break、continue）  
- **break**：跳出整个循环；**continue**：跳过本次循环。  
**案例5.3：break找第一个偶数**  
```cpp
for (int i=1; i<=5; i++) {
    if (i%2==0) { cout << i; break; } // 输出：2（找到后停止）
}
```  


### 流程控制总结  
- **条件语句**：`if-else`（灵活）、`switch-case`（固定值）；  
- **循环语句**：`while`（通用）、`for`（计数）、`do-while`（至少执行一次）；  
- **练习**：写ATM机菜单（do-while+switch）、判断素数（循环检查除数）。  


## 四、重点代码解释  
### 4.1 `cout << fixed << setprecision(10);`  
- **作用**：控制浮点数输出格式。`fixed`用固定小数点形式，`setprecision(10)`保留10位小数（需`#include <iomanip>`）。  
- **示例**：输出π时，`fixed`避免科学计数法，`setprecision(10)`显示更多小数位对比`float`和`double`精度。  


### 4.2 `string info = fullName + "的年龄是" + to_string(age) + "岁。";`  
- **作用**：字符串拼接（含类型转换）。`to_string(age)`将`int`转为`string`，再用`+`拼接文字。  
- **示例**：`fullName="张三"`、`age=20` → 拼接结果：`"张三的年龄是20岁。"`。  


### 4.3 `string weekday;`  
- **作用**：声明字符串变量`weekday`（空盒子），用于存储星期几的文字（如“周一”）。  
- **场景**：配合`switch-case`，根据数字1-7给`weekday`赋值（如`case 3: weekday="周三";`）。  


### 4.4 `for (int i=0; str[i]!='\0'; i++) { length++; }`  
- **作用**：手动统计字符串长度（C风格字符串以`'\0'`结尾）。  
- **流程**：`i`从0开始，逐个字符检查，遇`'\0'`停止，`length`累计字符数（如`"Hello"`长度5）。  


## 五、复习建议  
1. **敲代码**：模仿所有案例，修改参数观察输出；  
2. **做练习**：变量计算器、成绩等级判断、猜数字游戏；  
3. **查错误**：故意写错变量名、漏写`break`，看编译器报错并修正；  
4. **画图辅助**：用“盒子”比喻变量，“流程图”梳理循环/条件逻辑。  

**加油！多动手，你很快就能独立写小程序啦！** 🚀