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
## Array
1. Declaring array  
	**The declaration of an array variable does not allocate any space in memory.**
	```java
	double[] mylist;	//or
	double mylist[];	//Allowed but not preferred
	//mylist is null

	mylist = new double[10];	
	//Does 2 things
	//1. create an array using new. **When array is created the elements are assgined the default value of 0 or \u0000 or false **
	//2. assigns the reference of the new array to mylist
	```
1. 输出比平均值大的数
	```java
	public static void main(String[] args){
		
		Scanner in = new Scanner(System.in);	
		int size = in.nextInt();
		int[] numbers = new int[size]；    
		// Initialise array; 数组初始化以后不能改变大小
		// 数组创建以后自动赋值0
		int[] numbers  = {1, 2, 3};		
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
1. Random shuffling
	```java
	for (int i=0; i<a.length; i++)
	{
		int j = (int)(Math.random() * a.length);
		temp = a[i];
		a[i] = a[j];
		a[j] = temp;
		System.out.println(Arrays.toString(a));
	}
	```
1. 数组的赋值
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
1. Copying Arrays
	- Use a loop to copy individual elements one by one
		```java
		int[] sourceArray = {1, 2, 3};
		int[] targetArray = new int[sourceArray.length];
		for (int i=0; i<sourceArray.length; i++)
			targetArray[i] = sourceArray[i];
		```
	- Use the static arraycopy method
		```java
		arraycopy(srcArray, srcPos, tarArray, tarPos, length);
		```
	- Use the clone method
1. Passing Arrays to Methods  
	When passing an array to a method, the reference of the array is passed to the method. Java uses pass-by-value to pass arguments to a method.
	- For an argument of a primitive type, the argument's value is passed.
	- For an argument of array type, the value of the argument is a reference to an array; this reference value is passed to the method.
1. Variable-length argument lists  
Java treats a variable-length parameter as an array.  
	```java
	public static void printSum(double... numbers)
	{
		if(numbers.length == 0)
		{
			System.out.println("No argument passed");
			return;
		}
		double result = 0;
		for ( double number : numbers)
			result += number;
		System.out.println(result);
	}
	```
1. Searching Arrays  
If an array is sorted, binary search is more efficient than linear search for finding an element in the array.  
- The linear search  
The linear search compares the key with each element in the array.
	```java
	public static int linearSearch(int[] list, int key)
	{
		for(int i=0; i<list.length; i++)
			if (key == list[i]) return i;
		return -1;
	}
	```
- The bianry search  
The elements in the array must already be ordered.
	```java
	public static int binarySearch(int[] list, int key)
	{
		int low = 0;
		int high = list.length - 1;

		while ( high >= low )
		{
			int middle = (low+high)/2;
			if (key<list[middle])
				high = middle - 1;
			else if (key == list[middle])
				return middle;
			else
				low = middle + 1;
		}
		return -low-1;
	}
	```

## Difference between stack and heap  
Arrays are objects in Java, the JVM stores the objects in the heap, which is used for dynamic mrmory allocation. Here are some difference between stack and heap.  
- Stack memory is used to store local variables and function call while heap memory is used to store objects in Java
- Size of stack memory is a lot lesser than the size of heap memory
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
## 类变量
```java
public class Display {
    private int value = 0;	
    private int limit = 0;
	private static int step = 1;
	//1. static是一个类（就是Display）变量。这个static表示的是可以在外面通过 Distplay.step来访问。可是value, limit就不行。
	// 同时可以用d1.step来访问。

    public Display(int limit)
    {
        this.limit = limit;
    }
	public static void f(){
	// 因为f是static所以不能访问任何value ++。你可以理解为如果你修改了value，那不知道这个value是哪个instance的。
	}

    public static void main(String[] args){
	// 2. main前面的static表明main函数不属于其它函数，属于Display这个类。
        Clock c = new Clock();
        c.start();
		f(); //合法的，因为f()是static
    }
}
```
## 顺序容器  
1.	 步骤  
a)	考虑功能 b)	考虑接口
2.	容器类 ArrayList<String> notes = new ArrayList<String>  
	容器类有两个类型。容器的类型（ArrayList）和元素的类型(String)。 
3.	例子

```java
import java.util.ArrayList;

public class Notebook {
    private ArrayList<String> notes = new ArrayList<String>();
    // 这是一个泛型类，是一种容器。表示notes是Arraylist这个类，同时里面存放的是String。

	// 注意这两个add。 Java里面没有预设值，只能利用方法重载实现。
    public void add(String s){ notes.add(s); }
    public void add(String s, int location){ notes.add(location, s); }

	// 以下这几个都是利用ArraryList自己的方法实现的。
    public int getSize(){return notes.size();}
    public String getNote(int index){ return notes.get(index); }
    public void removeNote(int index){ notes.remove(index); }

    public String[] list(){
        String[] temp = new String[notes.size()];
       // 注意String数组中的每一个元素都是指针。并不是真正的字符串类型
       // 所以他又加了以下的初始化语句，可是我觉得不需要，没加之前代码也是正常运行的。
       // 更正，是需要的。应该明白java数组里面存的是对象的引用，所以必须初始化才能用。
       // For-each循环对于int数组是没用的。因为每一个原酸
       for (int i=0; i<a.length; i++){ a[i]=””+i; }

// WAY1: Save ArrayList content to temp
        for (int i = 0; i < notes.size(); i++) { temp[i] = notes.get(i);}
// WAY2: Save ArrayList content to temp
        notes.toArray(temp); 
        return temp;}

    public static void main(String[] args){
        String[] a = new String[10]; // 这里初始化了一个String 可以查看是否和ArrayList的一样
        a[0] = "first"; a[1] = "second";

        Notebook nb = new Notebook();
        nb.add("First"); nb.add("Second");
        nb.add("Third", 1);
        nb.removeNote(1);
        String[] b = nb.list();
        for(String s: b) {System.out.println(s); }
    }
}
```

5.	for-each  
-	For-each对于 ArraryList<String>也是可以用的。打印出的是每个value。
-	for-each 如果是对指针for each，然后还有一个方法来进行setValue，那就可以改变value。奇怪为什么不能通过这个改变string的值？因为String数组存放的是指针。  
```java
import java.util.ArrayList;
class Value {
	private int i;
	public void set(int i){ this.i = i; }
	public int get() { return i; }
}
public class Notebook {
	public static void main(String[] args){
		Value[] a = new Value[10];
		for (int i=0; i<a.length; i++){
			a[i] = new Value();
			a[i].set(i);
		}
		for (Value v : a){
			System.out.println(v.get());
			v.set(0); // 利用for-each修改v的值
		}
		for (Value v:a){
			System.out.println(v.get());
		}
	}
}
```
## 集合容器(set)
1.	HashSet和 ArrayList类似。HasSet不会存放重复的值，也没有排序，和数学中的set的概念一致。
	```java
	// HashSet 表示的是没有排序的。并且没有重复的值，和数学的集合是一个概念。
	HashSet<String> a3 = new HashSet<String>();
	a3.add("first");
	a3.add("second");
	a3.add("first");
	System.out.println(a3); //可以直接输出。利用toString实现的。
	```
2.	类里面的toString输出的值 == print输出的值。我觉得有点类似__str__。
- 格式要求：  public String toString() {return ""+i+j;} //一定要这种格式。后面的i,j自己加。
- 例子
	```java
	class Value {
		private int i;
		private int j;
		public void set(int i, int j){
			this.i = i; 
			this.j  = j;}
		public int get() { return i; }
		public String toString() {return ""+i+j;}
	}
	public static void main(String[] args){
		Value a = new Value();
		a.set(1, 2);
		System.out.println(a); // 这样
	}
	```
3.	Hash表。类似于字典
- 一对一对应。一个是可以用switch实现
	```java
	switch(amount){ case 10: return “dime”;}
	```
- 例子
	```java
	public class Coin {
		private HashMap<Integer, String> coinnames = new HashMap<Integer, String>();
		public Coin(){
			coinnames.put(1, "penny");
			coinnames.put(10, "dime");
			coinnames.put(10, "TEN"); 
			// 注意这样的话只会保留这个，上面这个10被覆盖了。
			System.out.println(coinnames.keySet().size());
			System.out.println(coinnames);

			// 遍历hash表 
			for (Integer k: coinnames.keySet()){
				String s = coinnames.get(k);
				System.out.println(s);
			}
		}
		public String getName(int amount){
			if (coinnames.containsKey(amount)) // hash表有一个功能是查看是否有这个key
				return coinnames.get(amount);
			else
				return "Not Found";
		}
	}
	```
# 新的
## 多态变量  
- Java的对象变量是多态（现在可以放这个类型的变量，过一会儿可以放另外类型的变量），他们能保持不止一种类型的对象。有两个类型：
	- 声明类型or静态类型or字面上可以看的出来的类型（就是Item(item可以是cd or dvd)）
	- 动态类型：程序运行到这里管理的是什么类型的对象，那就是什么类型
- 向上造型：把子类的对象赋给父类的变量的时候。
## 造型cast
- 子类的对象可以赋值给父类的变量。Java中不存在对象对对象的赋值，而是两个对象的管理者去管理一个共同的对象。
	```java
	String s = "bye";  //这里是让s管理”bye”这个对象
	s = "Hello";     // 这里是让s管理Hello这个对象，内容是Hello。不是用hello的内容替换bye的内容
	```
- 父类的对象不可以赋值给子类的变量
	```java
	Item item = new Item("..", ".."); // Item 是父类
	CD cd = new CD("..", "..") ;      // CD是子类
	item = cd;                          // 子类对象赋值给父类变量
	CD cc = (CD) item;     		
	// 父类不能赋值给子类。这样不会报错，可是编译通不过不可以做强制造型转换。
	```

- 重写equals。因为写出来的东西都是继承至object。Object的equals如果没有重新写过的话，对比的是地址。我们如果想要对比content，需要重新写equals
	```java
	@Override // 这里说的是和父类的一模一样，签名函数参数表。也就是一定要用object
	public boolean equals(Object obj){
		CD cc = (CD) obj; 
		// 为什么要用cc，向下强制转换。因为obj没有artist。
		// ？ 为什么不是输入的时候直接用的CD obj? – 因为用了Override 
		return artist.equals(cc.artist); 
		// 对比两个是否相等，这里之只看，artist是否相等
	}
	```
- 抽象
	```java
	public abstract class Shape(){ 
	// 就是存在shape，可是真实你要用shape来做东西，是没有的。
	// 不能产生对象
		public abstract void draw(Graphics g);	
		// 没有{}. 如果有draw那子函数里面也一定会要有draw
	}
	```


