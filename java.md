## Java

This cheat sheet is a crash course for Java beginners and help review the basic syntax of the Java language.

### #Getting started

```java
public class Hello {
  // main method
  public static void main(String[] args)
  {
    // Output: Hello, world!
    System.out.println("Hello, world!");
  }
}
```

```
compiling and running
$ javac Hello.java
$ java Hello
Hello, world!
```

### variables

```java
int num = 5;
float floatNum = 5.99f;
char letter = 'D';
boolean bool = true;
String site = "quickref.me";
```

### Primitive data types

| Data Type | Size   | Default | Range         |
| --------- | ------ | ------- | ------------- |
| byte      | 1 byte | 0       | -128 to 127   |
| short     | 2 byte | 0       | -215 to 215-1 |
| int       | 4 byte | 0       | -231 to 231-1 |
| long      | 8 byte | 0       | -263 to 263-1 |
| float     | 4 byte | 0.0f    | N/A           |
| double    | 8 byte | 0.0d    | N/A           |
| char      | 2 byte | \u0000  | 0 to 65535    |
| boolean   | N/A    | false   | true / false  |

### Type Casting

```java
// Widening
// byte<short<int<long<float<double
int i = 10;
long l = i;               // 10

// Narrowing
double d = 10.02;
long l = (long)d;         // 10

String.valueOf(10);       // "10"
Integer.parseInt("10");   // 10
Double.parseDouble("10"); // 10.0
```

### User Input

```java
Scanner in = new Scanner(System.in);
String str = in.nextLine();
System.out.println(str);

int num = in.nextInt();
System.out.println(num);
```

## Java Strings

### Basic

```java
String str1 = "value";
String str2 = new String("value");
String str3 = String.valueOf(123);
```

### concatenation

```java
String s = 3 + "str" + 3;     // 3str3
String s = 3 + 3 + "str";     // 6str
String s = "3" + 3 + "str";   // 33str
String s = "3" + "3" + "23";  // 3323
String s = "" + 3 + 3 + "23"; // 3323
String s = 3 + 3 + 23;        // 29
```

### StringBuilder

StringBuilder sb = new StringBuilder(10);

```
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
|   |   |   |   |   |   |   |   |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8  9
```

sb.append("QuickRef");

```
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| Q | u | i | c | k | R | e | f |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```

sb.delete(5, 9);

```
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| Q | u | i | c | k |   |   |   |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```

sb.insert(0, "My ");

```
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| M | y |   | Q | u | i | c | k |   |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```

sb.append("!");

```
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
| M | y |   | Q | u | i | c | k | ! |
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
0   1   2   3   4   5   6   7   8   9
```

### Comparison

```java
String s1 = new String("QuickRef");
String s2 = new String("QuickRef");

s1 == s2          // false
s1.equals(s2)     // true

"AB".equalsIgnoreCase("ab")  // true
```

### manipulation

```java
String str = "Abcd";

str.toUpperCase();     // ABCD
str.toLowerCase();     // abcd
str.concat("#");       // Abcd#
str.replace("b", "-"); // A-cd

"  abc ".trim();       // abc
"ab".toCharArray();    // {'a', 'b'}
```

### information

```java
String str = "abcd";

str.charAt(2);       // c
str.indexOf("a")     // 0
str.indexOf("z")     // -1
str.length();        // 4
str.toString();      // abcd
str.substring(2);    // cd
str.substring(2,3);  // c
str.contains("c");   // true
str.endsWith("d");   // true
str.startsWith("a"); // true
str.isEmpty();       // false

```

### immutable

```java
String str = "hello";
str.concat("world");

// Outputs: hello
System.out.println(str);

```

---

```java
String str = "hello";
String concat = str.concat("world");

// Outputs: helloworld
System.out.println(concat);
```

Once created cannot be modified, any modification creates a new String

## Java Arrays

### Declare

```java
int[] a1;
int[] a2 = {1, 2, 3};
int[] a3 = new int[]{1, 2, 3};

int[] a4 = new int[3];
a4[0] = 1;
a4[2] = 2;
a4[3] = 3;
```

### modify

```java
int[] a = {1, 2, 3};
System.out.println(a[0]); // 1

a[0] = 9;
System.out.println(a[0]); // 9

System.out.println(a.length); // 3
```

### Loop (Read & Modify)

```java
int[] arr = {1, 2, 3};
for (int i=0; i < arr.length; i++) {
    arr[i] = arr[i] * 2;
    System.out.print(arr[i] + " ");
}
// Outputs: 2 4 6
```

### Loop (Read)

```java
String[] arr = {"a", "b", "c"};
for (int a: arr) {
    System.out.print(a + " ");
}
// Outputs: a b c
```

### multidimensional Arrays

```java
int[][] matrix = { {1, 2, 3}, {4, 5} };

int x = matrix[1][0];  // 4
// [[1, 2, 3], [4, 5]]
Arrays.deepToString(matrix)

for (int i = 0; i < a.length; ++i) {
  for(int j = 0; j < a[i].length; ++j) {
    System.out.println(a[i][j]);
  }
}
// Outputs: 1 2 3 4 5 6 7
```

### sort

```java
char[] chars = {'b', 'a', 'c'};
Arrays.sort(chars);

// [a, b, c]
Arrays.toString(chars);
```

---

## Java Conditional

| Operators |
| --------- | ---------- | --- | --- |
| +         | -          | \*  | /   |
| %         | =          | ++  | >=  |
| !         | ==         | !=  | >   |
| <         | <=         | &&  |     |
| ?:        | instanceof | --  |
| ~         | <<         | >>  | >>> |
| &         | ^          |

### if else

```java
int k = 15;
if (k > 20) {
  System.out.println(1);
} else if (k > 10) {
  System.out.println(2);
} else {
  System.out.println(3);
}
```

### switch

```java
int month = 3;
String str;
switch (month) {
  case 1:
    str = "January";
    break;
  case 2:
    str = "February";
    break;
  case 3:
    str = "March";
    break;
  default:
    str = "Some other month";
    break;
}

// Outputs: Result March
System.out.println("Result " + str);
```

### ternary operator

```java
int a = 10;
int b = 20;
int max = (a > b) ? a : b;

// Outputs: 20
System.out.println(max);
```

## Java loops

### for loop

```java
for (int i = 0; i < 10; i++) {
  System.out.print(i);
}
// Outputs: 0123456789

```

---

```java
for (int i = 0,j = 0; i < 3; i++,j--) {
  System.out.print(j + "|" + i + " ");
}
// Outputs: 0|0 -1|1 -2|2

```

### Enhanced For loop

```java
int[] numbers = {1,2,3,4,5};

for (int number: numbers) {
  System.out.print(number);
}
// Outputs: 12345
```

Used to loop around array's or List's

### while loop

```java
int count = 0;

while (count < 5) {
  System.out.print(count);
  count++;
}
// Outputs: 01234
```

### Do While Loop

```java
int count = 0;

do {
  System.out.print(count);
  count++;
} while (count < 5);
// Outputs: 01234
```

### continue statement

```java
for (int i = 0; i < 5; i++) {
  if (i == 3) {
    continue;
  }
  System.out.print(i);
}
// Outputs: 01245
```

### break statement

```java
for (int i = 0; i < 5; i++) {
  System.out.print(i);
  if (i == 3) {
    break;
  }
}
// Outputs: 0123
```

**most imp**

# JCF(Java collection Framework):

1. List Interface
   Ordered collection (also known as a sequence).

- ArrayList: Resizable array implementation.

```java
List<String> list = new ArrayList<>();
list.add("Element");
list.get(0);
list.size();
list.remove(0);
```

- LinkedList: Doubly-linked list implementation.

```java
List<String> list = new LinkedList<>();
list.add("Element");
list.get(0);
list.size();
list.remove(0);
```

2. Set Interface
   Collection that cannot contain duplicate elements.

- HashSet: Hash table implementation.

```java
Set<String> set = new HashSet<>();
set.add("Element");
set.contains("Element");
set.size();
set.remove("Element");
```

- LinkedHashSet: Hash table and linked list implementation (orders elements by insertion order).

```java
Set<String> set = new LinkedHashSet<>();
set.add("Element");
set.contains("Element");
set.size();
set.remove("Element");
```

- TreeSet: Red-black tree implementation (orders elements based on their values).

```java
Set<String> set = new TreeSet<>();
set.add("Element");
set.contains("Element");
set.size();
set.remove("Element");
```

3. Queue Interface
   Collection designed for holding elements prior to processing.

- LinkedList (also implements Queue interface):

```java
Queue<String> queue = new LinkedList<>();
queue.add("Element");
queue.offer("Element"); // Similar to add but does not throw exception
queue.peek(); // Retrieves, but does not remove, the head of this queue
queue.poll(); // Retrieves and removes the head of this queue
```

- PriorityQueue: Priority heap implementation (orders elements based on their natural ordering or by a Comparator provided at queue construction time).

```java
Queue<String> queue = new PriorityQueue<>();
queue.add("Element");
queue.offer("Element");
queue.peek();
queue.poll();
```

4. Deque Interface
   Double-ended queue, supports element insertion and removal at both ends.

- ArrayDeque: Resizable array implementation of Deque.

```java
Deque<String> deque = new ArrayDeque<>();
deque.addFirst("Element");
deque.addLast("Element");
deque.offerFirst("Element");
deque.offerLast("Element");
deque.peekFirst();
deque.peekLast();
deque.pollFirst();
deque.pollLast();

```

5. Map Interface
   Object that maps keys to values; cannot contain duplicate keys.

- HashMap: Hash table implementation.

```java
Map<String, String> map = new HashMap<>();
map.put("key", "value");
map.get("key");
map.containsKey("key");
map.size();
map.remove("key");
```

- LinkedHashMap: Hash table and linked list implementation (orders elements by insertion order).

```java
Map<String, String> map = new LinkedHashMap<>();
map.put("key", "value");
map.get("key");
map.containsKey("key");
map.size();
map.remove("key");
```

- TreeMap: Red-black tree implementation (orders elements based on their natural ordering or by a Comparator provided at map construction time).

```java
Map<String, String> map = new TreeMap<>();
map.put("key", "value");
map.get("key");
map.containsKey("key");
map.size();
map.remove("key");
```

6. Stack Class
   Last-In-First-Out (LIFO) stack of objects.

````java
Stack<String> stack = new Stack<>();
stack.push("Element");
stack.peek(); // Looks at the object at the top of this stack without removing it
stack.pop(); // Removes the object at the top of this stack and returns that object
stack.isEmpty(); // Tests if this stack is empty
```
## Additional Methods and Tips

- Iteration over Collections:

```java
// Using Iterator
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}

// Using enhanced for-loop
for (String element : list) {
    System.out.println(element);
}
````

- sorting Lists:

```java
Collections.sort(list);
Collections.sort(list, Comparator.reverseOrder());
```

# Java Interview questions for Freshers

<details>
<summary>Is Java Platform Independent? Explain</summary>

Yes, Java is a Platform Independent language. Unlike many programming languages javac compiler compiles the program to form a bytecode or .class file. This file is independent of the software or hardware running but needs a JVM(Java Virtual Machine) file preinstalled in the operating system for further execution of the bytecode.

Although JVM is platform dependent, the bytecode can be created on any System and can be executed in any other system despite hardware or software being used which makes Java platform independent.

</details>

<details>
<summary>
Difference between JVM, JRE, and JDK.
</summary>
JVM: JVM also known as Java Virtual Machine is a part of JRE. JVM is a type of interpreter responsible for converting bytecode into machine-readable code. JVM itself is platform dependent but it interprets the bytecode which is the platform-independent reason why Java is platform-independent.

JRE: JRE stands for Java Runtime Environment, it is an installation package that provides an environment to run the Java program or application on any machine.

JDK: JDK stands for Java Development Kit which provides the environment to develop and execute Java programs. JDK is a package that includes two things Development Tools to provide an environment to develop your Java programs and, JRE to execute Java programs or applications.

</details>

<details>

<summary>What is JVM?</summary>
JVM stands for Java Virtual Machine it is a Java interpreter. It is responsible for loading, verifying, and executing the bytecode created in Java.

Although it is platform dependent which means the software of JVM is different for different Operating Systems it plays a vital role in making Java platform Independent.

</details>

<details>
<summary>What is JIT?</summary>
JIT stands for (Just-in-Time) compiler is a part of JRE(Java Runtime Environment), it is used for better performance of the Java applications during run-time. The use of JIT is mentioned in step by step process mentioned below:

- Source code is compiled with javac compiler to form bytecode
- Bytecode is further passed on to JVM
- JIT is a part of JVM, JIT is responsible for compiling bytecode into native machine code at run time.
- The JIT compiler is enabled throughout, while it gets activated when a method is invoked. For a compiled method, the JVM directly calls the compiled code, instead of interpreting it.
- As JVM calls the compiled code that increases the performance and speed of the execution.
</details>
