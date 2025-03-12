# Project
#include <iostream>
#include <string>   //字符串类
#include <cmath>
#include <iomanip>  //包含 定义了控制符（Manipulators）对象
#include <chrono>   //用于处理时间和日期的库

//不推荐：
//#include <cstdio>   //包含头文件以使用 getchar()
//#include <conio.h>  // 包含头文件以使用 getch() 和 getche()

using namespace std;

/*
//setfill(w)
//设填充字符为 w

//setprecision(n)
//设显示小数精度为 n 位

//setw(m)
//设域宽为 m 个字符

//setiosflags(ios::fixed)
//固定的浮点数显示

//setiosflags(ios::scientific)
//浮点数采用科学计数法表示

//setiosflags(ios::right)
//右对齐

//setiosflags(ios::left)
//左对齐

//setiosflags(ios::skipws)
//忽略前导空白

//setiosflags(ios::lowercase)
//十六进制小写输出

//setiosflags(ios::uppercase)
//十六进制大写输出

//setiosflags(ios::showpoint)
//强制显示小数点符号

//setiosflags(ios::showpos)
//强制显示符号
*/

/*
//显示类型转换
//1. static_cast<>
//(1) 基本数据类型之间的转换，如把 int 类型转换为 char 类型等
//(2) 把任何类型的表达式转换为 void 类型
//(3) 把空指针转换为目标类型的指针
//(4) 用于类层次结构中 基类 和 子类 之间指针或引用的转换，在进行上行转换（把子类的指针或引用转换成基类类型）是安全的
//注意：
// static_cast<> 不能转换数据的 const 、 volatile 等特性（可变）

//2. const_cast<>
//用来修改类型的 const 或 volatile 属性，除了 const 或 volatile 修饰之外，原来的数据值和数据类型都是不变的

//3. dynamic_cast<>
//动态强制转换，只能用来转换指针和引用；它能把一种类型的指针或引用转换成另一种类型的指针或引用
//该操作符用于运行时检查类型转换是否安全，但只能在多态转换时合法，即该类型至少具有一个虚拟方法
//语法与 static_cast<> 相同，但 dynamic_cast<> 主要用于类层次间上行和下行转换，以及类之间的交叉转换
//在进行类层次间进行上行转换时效果和 static_cast<> 相同；下行转换时具有类型检查的功能，比 static_cast<> 更安全
// dynamic_cast<> 所完成的类型转换是在程序运行时刻实现的，而其他类型的强制转换在编译时就完成了

//4. reinterpret_cast<>
//重解释强制转换；能够完成互不相关的数据类型之间的转换，如将整型转换成指针，或把一个指针转换成与之不相关的另一种类型的指针
// reinterpret_cast<> 其实是按强制转换所指定的类型对要转换数据对应的内存区域进行重新定义
*/

/*
//字符串类
//定义字符串有以下几种方式：
//string s1;
      s1 = "hello"; //第一种方式——先定义字符串变量，再为字符串变量赋值
//string s2 = "hello"; //第二种方式——用“=”符号为字符串变量赋值
//string s3("hello"); //第三种方式——调用“()”运算符为字符串变量赋值
//string s4(6,'a'); //第四种方式——有两个参数，“6”表示用6个字符“a”去初始化 s4，初始化后 s4 的值为“aaaaaa”
*/

/*
//setw(n);
//“ n ”是输出数据占用屏幕宽度的字符个数；默认情况下，输出数据右对齐
//若输出数据比 n 小，则左边留空
*/

/*  用法：
//typedef type newname
// type 是已存在的数据类型， newname 是为 type 指定的新类型名
//新类型名 newname 并未取代原来的类型 type，即 type 和 newname 在程序中都是可用的
例：
typedef double apple_price
apple_price a,b;
double x,y; // a、b 均为 double 类型，同时 double 也能继续使用
*/

/*
指针：内存单元的地址，指针指向一个内存单元
变量的指针就是“变量的地址”，变量的指针指向一个变量对应的内存单元
指针变量就是地址变量，地址（指针）也是数据，可以保存在一个变量中。保存地址（指针）数据的变量称为指针变量

举例：
int *pi;                 // pi 是指向 int 的指针
int **pc;                // pc 是指向 int 指针的指针
int *pA[10];             // pA 是指向 int 的指针数组
int (*f)(int,char)       // f 是指向具有两个参数的函数的指针
int *f(int);             // f 是一个函数，返回一个指向 int 的指针
*/

/*
1.常量指针
指针所指的对象是常量，指针本身是变量
const char *p = "Hello";   //定义了一个指针变量 pc
p[2] = 't';                //错误，修改了变量
p = "wang";                //正确

2.指针常量
指针本身是常量，它所指向的对象是变量。
char *const p = "Hello";  //定义 p 是常量指针，*p 是字符串常量
p[2] = 't';               //正确
p = "wang";               //错误。不能修改 p，让它指向其他字符串的内存地址

3.指向常量的常指针
指针是常量，指针所指的对象也是常量
const char *const pc = "apple";  //定义 pc 为指向字符常量的常量指针，即指针 pc 为常量，
                                 //它所指向的对象 *pc 也是常量，都不允许修改
pc[2] = 't';                     //错误，不能修改 *pc 的内容
pc = "wang";                     //错误，不能修改 pc 的内容

4. const、指针与变量赋值
const 对指针与变量之间的相互赋值具有一定影响，在使用时需注意以下问题：
① 不能将非 const 对象的指针指向一个常量对象，否则将引起编译错误
    int *pi;           //定义 pi 是指针
    const int i1 = 9;  //定义 i1 是常量
    pi = &i1;          //错误
② const 对象的地址只能赋给指向 const 对象的指针，但指向 const 对象的指针可以被赋予一个非 const 对象的地址
    const int *pi;     //定义 pi 是指针，*pi 是字符串常量
    int i1 = 9;        //定义 i1 是整型变量
    pi = &i1;          //常量指针 pi 指向变量 i1
    *pi = Q;           //错误，不能通过 *pi 修改 i1，因为 *pi 是常量    
*/

/*
void 指针
同类型的指针进行比较或相互赋值时才有意义，一种类型的指针不能被初始化或赋值为其他类型对象的地址

空指针 void*
它表示与它相关的值是个地址，但该地址的数据类型是未知的。两个 void* 指针可以相互赋值、比较相等与否
只能显式地将一个 void* 指针转换成某种数据类型的指针（但函数指针不能赋给 void* 型的指针），其他操作都是不允许的

void* 指针最重要的用途：作为函数的参数，向函数传递一个类型可变的对象
另一种用途是从函数返回一个五类型的对象，在使用时再将它显式转换成适当的类型
*/

/*
引用
引用是隐式的指针。引用是某个对象（即变量）的别名，即某个对象的替代名称

格式：
int i = 9;
int &ir = i;  //定义 ir 为 i 的别名

以下三种定义完全相同：
int& ir = i;
int & ir = i;
int &ir = i;

注意：
1. ① 不能建立引用的引用
   ② 可以建立指针的引用，但不能创建指向引用的指针
2. 在变量声明时出现的 & 才是引用运算符（包括函数参数声明和函数返回类型的声明），其他地方出现的 & 都是地址操作符
3. 引用在定义时必须初始化。 int &ir; 语句是错误的
4. 引用在初始化时只能绑定左值，不能绑定常量值
5. 可以为一个变量指定多个引用
6. 引用一旦初始化，其值就不能改变，即不能再做别的变量的引用
    int r1 = 10;
    int r2 = 20;
    int &p = r1;
    p = r2;
   这段代码中，p 为变量 r1 的引用，当 p=r2 执行时，并不是把 p 指向了变量 r2，而是将 r1 的值更新为20
7. 引用与指针的区别：
    ①指针必须通过引用运算符“ * ”来访问它所指向的内存单元
      引用不需要
    ②指针是一个变量，可以对它重新赋值，让它指向另外的地址
      引用必须在定义时初始化，且定义后不能作为其他变量的引用
    ③指针变量要另外去开辟内存单元，其内容是地址
      引用变量不是一个独立的变量，不单独占内存空间
8. 当用 & 运算符获取一个引用地址时，实际取出的是引用对应的变量的地址
9. 数组不能定义引用，因为数组是一组数据，无法定义其别名
*/

/*
 new 运算符常用格式：
1：<指针变量> = new <数据类型>
2：<指针变量> = new <数据类型>(<值>)
3：<指针变量> = new <数据类型>[<表达式>]
4：<指针变量> = new <数据类型>[<表达式1>][<表达式2>]

 delete 运算符常用格式：
1：delete <指针变量>
2：delete[] <指针变量>

注意：
使用 new 运算符动态申请空间，不是每次都能申请成功的。为了保证程序执行正确，使用时要测试是否成功
*/

double calculatePi(int iterations) { //计算圆周率的函数
    double a = 1.0;
    double b = 1.0 / sqrt(2);
    double t = 1.0 / 4.0;
    double p = 1.0;

    for (int i = 0; i < iterations; i++) {
        double a_next = (a + b) / 2.0;
        double b_next = sqrt(a * b);
        double t_next = t - p * pow((a - a_next), 2);
        a = a_next;
        b = b_next;
        t = t_next;
        p *= 2; // p_n  

    }
    double pi = (a + b) * (a + b) / (4 * t);
    return pi; // 计算 pi  
}

// 循环（迭代）
int Fibonacci(int n) { //计算斐波那契数列的函数
    if (n < 0) {
        throw invalid_argument("n不能是负数");
    }
    if (n == 0) return 0;
    if (n == 1) return 1;

    int a = 0, b = 1, c;
    for (int i = 2; i <= n; ++i) {
        c = a + b;
        a = b;
        b = c;
    }
    return b;
}

// 递归
int fibonacci(int n) { //计算斐波那契数列的函数
    if (n < 0) {
        throw invalid_argument("n不能是负数");
    }
    if (n == 0) return 0;
    if (n == 1 || n == 2) return 1;
    return fibonacci(n - 1) + fibonacci(n - 2); // 递归调用
}


//通项公式
long long fibonacci_General(int n) {
    if (n < 0) {
        throw invalid_argument("n不能是负数");
    }

    double a = sqrt(5);
    double b = (1.0 + a) / 2.0; // 黄金分割数  
    double c = (1.0 - a) / 2.0; // 黄金分割数的负根  
    long long f = static_cast<long long>((pow(b, n) - pow(c, n)) / a); // 用静态转换将结果转换为long long  
    return f;
}

double calculateE(void) { //利用泰勒级数求自然常数 e
    int i = 1;
    double  e = 1.0, t = 1.0, v = 1.0;
    while (t > 1e-15)
    {
        e += t;
        i++;
        v = v * i;
        t = 1.0 / v;
    }
    
    cout << setprecision(17) << "e≈" << e << endl;
    return e;
}

struct Date
{
    int year;   //年
    int month;  //月
    int day;    //日

    Date(int y, int m, int d) :year(y), month(m), day(d) {}
};

bool LeapYear(int year) { //检测闰年
    return ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0));
}

bool RightDate(const Date& date) {
    if (date.month < 1 || date.month > 12) {
        return false; // 月份无效  
    }

    int daysInMonth;
    switch (date.month) {
    case 1: case 3: case 5: case 7: case 8: case 10: case 12:
        daysInMonth = 31;
        break;
    case 4: case 6: case 9: case 11:
        daysInMonth = 30;
        break;
    case 2:
        daysInMonth = LeapYear(date.year) ? 29 : 28; // 闰年2月29天  
        break;
    default:
        return false; // 其他情况不可能到达  
    }

    return date.day >= 1 && date.day <= daysInMonth; // 检查日期 
}

struct Student
{
    int number;    //学号
    string name;   //姓名
    string sex;    //性别

    Student(int n, string nm, string s) :number(n), name(nm), sex(s) {}
};

int main() {
    
    /*
    //创建一个 Date 类型的对象
    Date date(0, 0, 0);

    cout << "请输入年份：";
    cin >> date.year;
    cout << "请输入月份：";
    cin >> date.month;
    cout << "请输入日期：";
    cin >> date.day;

    // 检查日期的有效性  
    if (!RightDate(date)) {
        cout << "日期无效！" << endl;
        return 0;
    }

    cout << "您输入的日期是：" << date.year << "年" << date.month << "月" << date.day << "日" << endl;
    return 0;
    */

    /*
    // 创建一个 Student 类型的对象
    Student student(0, "", "");  //初始化
    
    cout << "请输入学号：";
    cin >> student.number;
    
    cout << "请输入姓名：";   
    cin.ignore();  // 清空换行符影响
    getline(cin, student.name);

    cout << "请输入性别：";
    getline(cin, student.sex);

    cout << "学号：" << student.number << endl;
    cout << "姓名：" << student.name << endl;
    cout << "性别：" << student.sex << endl;
    */

    //calculateE(); //输出 e 的值
    
    /*
    int x = 34;
    cout << hex << 17 << " " << x << " " << 18 << endl; // hex 指十六进制
    cout << 17 << " " << oct << x << " " << 18 << endl; // oct 指八进制
    cout << dec << 17 << " " << x << " " << 18 << endl; // dec 指十进制
    return 0;
    */

    /*
    //输出圆周率的配置（迭代次数）
    int iterations = 10; // 可以根据需要调整迭代次数
    double pi = calculatePi(iterations);
    
    cout << fixed << setprecision(15);
    cout << "pi ≈ " << pi << endl; // 输出 pi 的值
    return 0;
    */

    /*
    int n;
    cout << "请输入n（斐波那契数列的项索引）：";
    cin >> n;

    try {
        long long result = fibonacci_General(n); // 将结果类型更改为long long  
        cout << "斐波那契数列的第 " << n << " 项是: " << result << endl;
    }
    catch (const invalid_argument& e) {
        cout << e.what() << endl;
    }
    return 0;
    */
}
