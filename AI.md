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

# C++运算符与循环进阶补充（含大量实例）  
**适用对象**：已掌握基础变量、运算符、流程控制的学员  
**目标**：通过实用案例深化理解，覆盖易错点与进阶用法  


## 一、运算符进阶补充  
### 1.1 三元运算符（条件运算符 `?:`）  
**语法**：`条件表达式 ? 表达式1 : 表达式2`  
**作用**：简化简单的 `if-else` 逻辑（条件为真返回表达式1，假返回表达式2）。  


#### **案例1.1：判断奇偶数（替代if-else）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 17;
    // 三元运算符：num%2==0 ? "偶数" : "奇数"
    string result = (num % 2 == 0) ? "偶数" : "奇数"; 
    cout << num << "是" << result << endl; // 输出：17是奇数

    // 直接在cout中使用
    cout << "20是" << ((20%2==0)?"偶数":"奇数") << endl; // 输出：20是偶数
    return 0;
}
```  


#### **案例1.2：求两数最大值**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 15, b = 23;
    int max = (a > b) ? a : b; // a>b为真则返回a，否则返回b
    cout << "最大值：" << max << endl; // 输出：23

    // 扩展到三个数
    int c = 18;
    int max3 = (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c); 
    cout << "三个数最大值：" << max3 << endl; // 输出：23
    return 0;
}
```  


#### **案例1.3：根据分数返回等级（替代if-else if）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int score = 85;
    string level = (score >= 90) ? "优秀" : 
                   (score >= 80) ? "良好" : 
                   (score >= 60) ? "及格" : "不及格"; 
    cout << "等级：" << level << endl; // 输出：良好
    return 0;
}
```  


### 1.2 位运算符（Bitwise Operators）  
**作用**：直接操作二进制位（效率高，常用于底层开发、嵌入式），新手了解即可。  
**常用位运算符**：  
| 运算符 | 名称       | 示例       | 说明（二进制操作）               |  
|--------|------------|------------|----------------------------------|  
| `&`    | 按位与     | `a & b`    | 同为1则1（如 `1010 & 1100 = 1000`）|  
| `|`    | 按位或     | `a | b`    | 有1则1（如 `1010 | 1100 = 1110`）  |  
| `^`    | 按位异或   | `a ^ b`    | 不同为1（如 `1010 ^ 1100 = 0110`）|  
| `~`    | 按位取反   | `~a`       | 0变1，1变0（如 `~1010 = 0101`）   |  
| `<<`   | 左移       | `a << n`   | 各二进制位左移n位（如 `3<<1=6`）   |  
| `>>`   | 右移       | `a >> n`   | 各二进制位右移n位（如 `8>>1=4`）   |  


#### **案例2.1：用 `&` 判断奇偶数（比 `%` 更快）**  
原理：奇数的二进制末位是1，`a & 1 = 1`；偶数末位是0，`a & 1 = 0`。  
```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 17; // 二进制：10001
    if (num & 1) { // 10001 & 00001 = 00001（非0，真）
        cout << num << "是奇数" << endl; // 输出：17是奇数
    }

    num = 20; // 二进制：10100
    if (!(num & 1)) { // 10100 & 00001 = 00000（假，取反后真）
        cout << num << "是偶数" << endl; // 输出：20是偶数
    }
    return 0;
}
```  


#### **案例2.2：用 `<<` 快速计算2的幂**  
原理：左移n位 = 乘以2ⁿ（如 `3<<2 = 3×2²=12`）。  
```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 5;
    cout << "2^3 = " << (1 << 3) << endl; // 1<<3=8（2³=8）
    cout << "5×4 = " << (5 << 2) << endl; // 5<<2=20（5×2²=20）
    cout << "10×8 = " << (10 << 3) << endl; // 10<<3=80（10×2³=80）
    return 0;
}
```  


#### **案例2.3：用 `^` 交换两个变量（无需临时变量）**  
原理：`a^b^b = a`（异或两次回到原数）。  
```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 5; // 二进制：0101
    int y = 10; // 二进制：1010

    x = x ^ y; // x=0101^1010=1111（15）
    y = x ^ y; // y=1111^1010=0101（5，原x）
    x = x ^ y; // x=1111^0101=1010（10，原y）

    cout << "交换后：x=" << x << ", y=" << y << endl; // 输出：x=10, y=5
    return 0;
}
```  


### 1.3 运算符优先级与结合性（避坑指南）  
**常见问题**：表达式不加括号导致的计算顺序错误（如 `a + b * c` 先算乘法）。  
**记忆口诀**：括号优先，单目（++、--、!）高于算术，算术高于比较，比较高于逻辑，赋值最低。  


#### **案例3.1：优先级错误示例（不加括号）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 2, b = 3, c = 4;
    // 错误预期：(a + b) * c → 5*4=20；实际因优先级先算b*c → 2+12=14
    int result = a + b * c; 
    cout << "a + b * c = " << result << endl; // 输出：14（而非20）

    // 正确写法（加括号明确顺序）
    result = (a + b) * c; 
    cout << "(a + b) * c = " << result << endl; // 输出：20
    return 0;
}
```  


#### **案例3.2：自增自减的复杂表达式（不推荐，但需理解）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 3, b = 5;
    int c = a++ + b--; // 先取a=3、b=5计算，再a+1=4、b-1=4
    cout << "c=" << c << ", a=" << a << ", b=" << b << endl; // 输出：c=8, a=4, b=4

    int d = ++a * (b--); // 先a+1=5，取b=4计算，再b-1=3 → 5*4=20
    cout << "d=" << d << ", a=" << a << ", b=" << b << endl; // 输出：d=20, a=5, b=3
    return 0;
}
```  


## 二、循环进阶补充  
### 2.1 嵌套循环：打印图形（三角形、菱形）  
**核心**：外层循环控制行数，内层循环控制每行的字符/空格。  


#### **案例1.1：打印直角三角形（*）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int rows = 5; // 5行
    for (int i = 1; i <= rows; i++) { // 外层：行数1~5
        for (int j = 1; j <= i; j++) { // 内层：每行j个*
            cout << "* ";
        }
        cout << endl; // 换行
    }
    /* 输出：
    * 
    * * 
    * * * 
    * * * * 
    * * * * * 
    */
    return 0;
}
```  


#### **案例1.2：打印倒直角三角形**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int rows = 4;
    for (int i = rows; i >= 1; i--) { // 外层：行数4~1
        for (int j = 1; j <= i; j++) { // 内层：每行i个*
            cout << "* ";
        }
        cout << endl;
    }
    /* 输出：
    * * * * 
    * * * 
    * * 
    * 
    */
    return 0;
}
```  


#### **案例1.3：打印空心正方形**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int size = 4; // 边长4
    for (int i = 0; i < size; i++) { // 外层：行0~3
        for (int j = 0; j < size; j++) { // 内层：列0~3
            // 第一行/最后一行，或第一列/最后一列 → 打印*，否则空格
            if (i == 0 || i == size-1 || j == 0 || j == size-1) {
                cout << "* ";
            } else {
                cout << "  "; // 两个空格（与*对齐）
            }
        }
        cout << endl;
    }
    /* 输出：
    * * * * 
    *     * 
    *     * 
    * * * * 
    */
    return 0;
}
```  


### 2.2 范围for循环（Range-based for Loop，C++11+）  
**语法**：`for (元素类型 变量 : 数组/容器) { ... }`  
**作用**：遍历数组或容器（如`string`）的每个元素，无需关心索引。  


#### **案例2.1：遍历数组求和**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {1, 2, 3, 4, 5}; // 数组
    int sum = 0;
    for (int num : arr) { // 依次取arr中的每个元素赋给num
        sum += num;
    }
    cout << "数组和：" << sum << endl; // 输出：15
    return 0;
}
```  


#### **案例2.2：遍历字符串统计元音字母**  
```cpp
#include <iostream>
#include <string>
#include <cctype> // 含tolower()函数（转小写）
using namespace std;

int main() {
    string s = "Hello World";
    int vowelCount = 0;
    for (char c : s) { // 遍历每个字符
        c = tolower(c); // 转小写（统一判断）
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            vowelCount++;
        }
    }
    cout << "元音字母个数：" << vowelCount << endl; // 输出：3（e, o, o）
    return 0;
}
```  


#### **案例2.3：修改数组元素（需引用&）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {1, 2, 3, 4};
    // 用引用&修改元素（否则是拷贝，原数组不变）
    for (int &num : arr) { 
        num *= 2; // 每个元素乘2
    }
    // 输出修改后的数组
    for (int num : arr) {
        cout << num << " "; // 输出：2 4 6 8
    }
    return 0;
}
```  


### 2.3 循环中的累加、累乘与阶乘  
**核心**：用循环变量作为“计数器”，累加器/累乘器存储结果。  


#### **案例3.1：计算1~n的累加和**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 10;
    int sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += i; // 累加：sum = 1+2+...+10
    }
    cout << "1+2+...+10 = " << sum << endl; // 输出：55
    return 0;
}
```  


#### **案例3.2：计算n的阶乘（n! = 1×2×...×n）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 5;
    long long factorial = 1; // 用long long防溢出（5!=120，10!=3628800）
    for (int i = 1; i <= n; i++) {
        factorial *= i; // 累乘：1×2×3×4×5
    }
    cout << n << "! = " << factorial << endl; // 输出：5! = 120
    return 0;
}
```  


#### **案例3.3：计算1! + 2! + 3! + ... + n!**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 3;
    long long total = 0;
    long long fact = 1; // 存储当前数的阶乘
    for (int i = 1; i <= n; i++) {
        fact *= i; // 计算i!
        total += fact; // 累加到总和
    }
    cout << "1!+2!+3! = " << total << endl; // 1!+2!+3! = 1+2+6=9
    return 0;
}
```  


### 2.4 循环变量作用域与无限循环  
#### **案例4.1：for循环变量作用域（C++11+）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 0; i < 3; i++) { // i的作用域仅在for循环内
        cout << i << " "; // 输出：0 1 2
    }
    // cout << i << endl; // 错误：i未定义（作用域已结束）

    int j = 0;
    while (j < 3) { // j的作用域是整个main函数
        cout << j << " "; // 输出：0 1 2
        j++;
    }
    cout << j << endl; // 输出：3（j在循环外仍可见）
    return 0;
}
```  


#### **案例4.2：无限循环与break（如服务器监听）**  
```cpp
#include <iostream>
using namespace std;

int main() {
    int count = 0;
    while (true) { // 无限循环（条件恒真）
        count++;
        cout << "运行中...（第" << count << "次）" << endl;
        if (count >= 3) { // 模拟3次后停止
            break; // 跳出循环
        }
    }
    cout << "循环结束" << endl;
    return 0;
}
```  


## 三、综合实例：简易学生成绩管理系统  
**功能**：输入5个学生成绩，计算平均分、最高分、最低分，统计及格人数。  
**用到的知识**：循环（for）、条件（if）、变量、运算符。  

```cpp
#include <iostream>
#include <climits> // 含INT_MAX（最大整数）、INT_MIN（最小整数）
using namespace std;

int main() {
    const int NUM_STUDENTS = 5;
    int scores[NUM_STUDENTS];
    int sum = 0, maxScore = INT_MIN, minScore = INT_MAX, passCount = 0;

    // 输入成绩
    for (int i = 0; i < NUM_STUDENTS; i++) {
        cout << "输入第" << (i+1) << "个学生成绩：";
        cin >> scores[i];
        sum += scores[i]; // 累加求和

        // 更新最高分、最低分
        if (scores[i] > maxScore) maxScore = scores[i];
        if (scores[i] < minScore) minScore = scores[i];

        // 统计及格人数（≥60）
        if (scores[i] >= 60) passCount++;
    }

    // 计算平均分（转double避免整数除法）
    double avg = static_cast<double>(sum) / NUM_STUDENTS;

    // 输出结果
    cout << "\n===== 成绩统计 =====" << endl;
    cout << "平均分：" << avg << endl;
    cout << "最高分：" << maxScore << endl;
    cout << "最低分：" << minScore << endl;
    cout << "及格人数：" << passCount << "/" << NUM_STUDENTS << endl;

    return 0;
}
```  


## 四、总结与练习  
### 运算符进阶重点  
- **三元运算符**：简化`if-else`，如`max = (a>b)?a:b`；  
- **位运算符**：`&`判断奇偶、`<<`算幂、`^`交换变量（了解即可）；  
- **优先级**：不确定时加括号，避免`a + b * c`式错误。  


### 循环进阶重点  
- **嵌套循环**：打印图形（行数+列数控制）；  
- **范围for循环**：遍历数组/字符串（`for (auto x : 容器)`）；  
- **累加累乘**：用循环变量+累加器实现（如阶乘、数列和）。  


### 练习任务  
1. 用嵌套循环打印**等腰三角形**（上三角*，居中对齐）；  
2. 用范围for循环统计字符串中**数字字符**的个数；  
3. 计算**斐波那契数列**前10项（1,1,2,3,5,8...，用循环实现）；  
4. 用`while`循环实现“猜数字游戏”（随机数生成+用户输入+提示大小）。  

**提示**：多动手敲代码，用`cout`打印中间变量（如循环中的`i`、`sum`）观察变化，理解执行流程！
