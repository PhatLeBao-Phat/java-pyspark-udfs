# java-pyspark-udfs
This is a note on Java introduction and how to write spark User-Defined-Functions (UDFs) in Java to speed up processing.

## 1. Java Introduction for Python beginner 👓
Java is a popular programming language, created in 1995. It is owned by Oracle, and more than 3 billion devices run Java.
### 1. Install
```java
// Check if you have java installed and in PATH or not 
C:\Users\Your Name>java -version

// To Compile your code 
C:\Users\Your Name>javac Main.java

// To run 
C:\Users\Your Name>java Main
```
### 2. Syntax
First you need to declare a package.
```java
package com.marcusbiel.javacourse.lesson1
```
Here are some tips:
- the package serves as the high-level description that reflects the internal structure of your entire program. Therefore, pick the one related to your project business.
- This is not import. 

Note that every line of code that runs in Java __must be__ inside a `class`. The name of the java file __must match__ the class name. Also, every Java program __must contain__ the `main()` method. 
```java
// This is importing 
import com.marcusbiel.lesson1.car 
import static org.junit.Assert.*

public static void main(String[] args) {
  System.out.println("Hello World");
}
```
Note that `;` is used to mark the end of each statement. 

#### Java Output/ Print 
```java
// This is a method btw, so need to be inside a class still
System.out.println("Hello World!");
System.output.print("I will print on the same line.");
```

#### Java Variables 
Java types are very similar to Python types.

| Java Type  | Description |
|------------|-------------|
| `String`   | Stores text, such as `"Hello"`. String values are surrounded by double quotes. |
| `int`      | Stores integers (whole numbers) without decimals, such as `123` or `-123`. |
| `long`     | Stores whole numbers from `-9223372036854775808` to `9223372036854775807`. |
| `double`   | Stores decimal numbers. Typically used for floating-point calculations like `19.99` or `-3.14159`. |
| `float`    | Stores fractional numbers (smaller precision than `double`, allowing 7 vs 16 decimals in `double`), such as `3.4f`. Requires `f` or `F` suffix. |
| `char`     | Stores a single character, such as `'A'` or `'z'`. Enclosed in single quotes. |
| `boolean`  | Stores `true` or `false` values. Useful for conditional logic. |
| `byte`     | Stores very small integers from `-128` to `127`. Saves memory in large arrays. |
| `short`    | Stores small integers from `-32,768` to `32,767`. |
| `Object`   | The root class for all non-primitive (reference) types in Java. Can store any object. |
| `Array`    | A container object that holds a fixed number of values of a single type. |
| `List`     | An interface that represents an ordered collection. Implemented by classes like `ArrayList`. |
| `Map`      | An object that maps keys to values. Example: `HashMap`, `TreeMap`. |
| `Set`      | A collection that contains no duplicate elements. Example: `HashSet`. |


To declare a var, you do:
```java
// type variableName = value;
String name = "John"
```
If you don't want other to overwrite exsiting values. This is probably similar to __CONST__, then do this 
```java 
final int myNum = 15;
myNum = 20; // will throw an error: cannot asisgn a value to a final variable 
```

#### Java Type Casting 
__Widening Casting__ (automatically) - converting a smaller type to a larger type size:

``byte`` -> `short` -> `char` -> `int` -> `long` -> `float` -> `double`

__Narrowing Casting (manually)__ - converting a larger type to a smaller size type

`double` -> `float` -> `long` -> `int` -> `char` -> `short` -> `byte`
```java 
// Here is an example 
public class Main {
  public static void main(String[] args) {
    int myInt = 9;
    double myDouble = myInt; // Automatic casting: int to double

// Narrow casting on the other hand need to be done manually
public class Main {
  public static void main(String[] args) {
    double myDouble = 9.78d;
    int myInt = (int) myDouble; // Manual casting: double to int

    System.out.println(myDouble);   // Outputs 9.78
    System.out.println(myInt);      // Outputs 9
  }
}
```
#### String operation 
```java 
// Concat two string 
System.out.println(firstName.concat(lastName)); 

// Special characters. Just escape like python. Nothing fancy
String txt = "We are the so-called \"Vikings\" from the north.";
```

#### Jave Math class
Providing many methods that allows you to perform mathematical tasks on numbers.
```java 
Math.max(5, 10);
.sqrt()
.abs()
.min()
.random()
int randomNum = (int)(Math.random() * 101);  // 0 to 100 + manual casting 
```

#### Boolean 
Yep. In java, they are `true` vs `false`. The rest is just like Python. By the rest, I meant the boolean operators. 

#### The if statement 
```java 
if (condition1) {
  // block of code to be executed if condition1 is true
} else if (condition2) {
  // block of code to be executed if the condition1 is false and condition2 is true
} else {
  // block of code to be executed if the condition1 is false and condition2 is false
}

// This is the magic here. Very JavaScript syntax-alike 
// where you can do a short-hand sort of like a pipeline op
variable = (condition) ? expressionTrue :  expressionFalse; 

// Switch statement. Let focus on this one as its not in Python.
// This is like a CASE WHEN in SQL
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

#### While Loop 
```java 
while (condition) {
  // code block to be executed
}

// Here is a variant where it will do first then check the condition.
do {
  // code block to be executed
}
while (condition);
```
#### For Loop
The `For` loop is fundamentally different. So for you Python novices, here is where to pay attention. 
```java
for (statement 1; statement 2; statement 3) {
  // code block to be executed
}
// Statement 1 is executed (one time) before the execution of the code block. 
// Statement 2 defines the condition for executing the code block.
// Statement 3 is executed (everytime) after the code block has been executed. 
```
```java 
// Here is a humble example 
for (int i = 0; i < 5; i++) {
  System.out.println(i);
}
```
Then you have the famous `For-Each` Loop. This is fundamentally the same as Python For loop.
```java
for (type variableName : arrayName) {
  // code block to be executed
}
```
#### Break and continue 
Just same old thing as python. Not thing changed. So `continue` for skip iteration and `break` for breaking the loop. 

#### Java Array 
