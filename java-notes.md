# Fundamental Programming Structures in Java
## New Project
路径，输入自己想要的名字 -> 找到src -> New -> Java Class -> Name 可能要用AbCd这样找到src -> New -> Java Class -> Name 可能要用AbCd这样
## Compiling and Running
```java
public class SampleExample  {
    public static void main(String[] args) { // To run code, need a main method
        System.out.println("Hello world");
    }
}
```
## Input and output
```java
import java.util.Scanner;
public class Hello {
    public static void main(String[] args){
        System.out.println("Something");
        Scanner in = new Scanner(System.in); // new创建一个对象
        System.out.println(“echo: ” + in.nextLine());
		// 1. connect two string, nextLine()读取line
		System.out.println("2+3="+(2+3));
		int a, b; 			// 2. 定义了两个int
		int a, b=0; 		// error. a not initialised.
		final amount = 100; // 3. 就和const一样
		int num = in.nextInt(); 	// 4. in.nextInt() 读取Int
		// 5. 变量名字（字母，下划线，数字）。只能字母和下划线开头
		// 定义了类型以后不能改变 

		boolean isPrime = ture;

		System.out.println("100+"+num+"="+(100+num));
		int amount=0, price=0;
		System.out.println("Enter amount");
		amount = in.nextInt();
		// height = in.nextDouble();
		// height = (int)heigh; 类型的强制转换

		System.out.println("Enter price");
		price = in.nextInt();
		System.out.println(String.format("The price: %d\nThe amount:%d\n", price,amount));
		// 6. Formated output
		// 输入的时候可以用 “23 44”。 只需要空格。
		System.out.printf("Sum: %.2f", sum); 	// 输出两位小数
    }
}
```
## 条件判断
### for-each
```java
//不能修改数组
for(<类型><变量>： <数组>){}
for (int k: data){
	if(k==x){found=true;} 
}
```
### 跳出for循环
```java
LABEL:
...
break/continue LABEL;
```
## 数组
```java
// 输出比平均值大的数
public static void main(String[] args){
	
	Scanner in = new Scanner(System.in);	
	int size = in.nextInt();
	int[] numbers = new int[size]；    
	// Initialise array; 数组初始化以后不能改变大小
	// 数组创建以后自动赋值0
	int[] numbers  = {1, 2, 3}		
	// 另外一种创建数组的方式
	double sum = 0;
	int cnt = 0;

	//  length遍历数组;
	for (int i=0; i< numbers.length; i++){	
		// length 访问数组大小
		int number = in.nextInt();
		numbers[i]= number;
		sum += number;
	}

	double avg = sum / size;
	for (int i=0; i<size; i++){	// 遍历
		if (numbers[i] > avg){
			System.out.println(numbers[i]);
		}
	}
}

```
### 数组的赋值
```java
Scanner in = new Scanner(System.in);
int[] a = new int[10];
int[] b = new int[10];
a[0] = 10;
b = a;		//把b的指针也指到a所指的数组了
b[0] = 20;	//修改了b也修改了a
System.out.println(a[0]); // 答案是 a[0]=20

//数组的复制 只能用遍历的方法。
```
## 包裹：每种基础类型都有对应的包裹类型
### 作用
- 定义变量
```java
Integer k = 10; // same as int k=10;
```
- MAX_VALUE/MIN_VALUE
```java
System.out.println(Integer.MAX_VALUE); 
```
- character
```java
isDigit();
isLetter();
...
```