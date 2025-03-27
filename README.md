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
  To declare an array, define the variable type with square brackets:
  ```java
  String[] cars;
  String[] cars = {"Volvo", "Tesla"};
  int[] myNum = {10, 20, 30, 40};

  // Slicing 
  cars[0]

  // Slide and change 
  cars[0] = "Opel";

  // Length of array 
  cars.length

  // Loop through array in two fashions. Fashion 1:
  String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
  for (int i = 0; i < cars.length; i++) {
    System.out.println(cars[i]);
  }

  // Fashion 2:
  String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
  for (String i : cars) {
    System.out.println(i);
  }

  // Ofc. You can also do multile dim array 
  int[][] myNumbers = { {1, 2, 3, 4}, {5, 6, 7} };
  ```

  ### Java Methods 
  So method is a function inside a class just like in Python. In java, they provide you will some pre-defined methods that easy to use e.g. `System.out.println()`. To create your own method:
  ```java
  public class Main {
      static void myMethod() {
          // code to be executed
      }
  }
  ```
  __`static`__ means that the method belongs to thte Main class and not an object ofthe Main class.

  __`void`__ means that this method does not havea reutrn value 


  #### Method overloading
  Remember the decorator `@overloading` in python? This is where it came from. With method overloading, multiple methods can have the same name with differetn parameters:
  ```java
  int myMethod(int x)
  float myMethod(float x)
  double myMethod(double x, double y)

  // Here is a humble example:
  static int plusMethod(int x, int y) {
    return x + y;
  }

  static double plusMethod(double x, double y) {
    return x + y;
  }

  public static void main(String[] args) {
    int myNum1 = plusMethod(8, 5);
    double myNum2 = plusMethod(4.3, 6.26);
    System.out.println("int: " + myNum1);
    System.out.println("double: " + myNum2);
  }
  ```

  #### Recursion
  This is not really different from Python. But I feel an example is needed. 
  ```java 
  public static int sum(int k) {
      if (k > 0) {
        return k + sum(k - 1);
      } else {
        return 0;
      }
    }
  ```

  ### Java Classes 
  To create an instance, use the defined class as the type.
  ```java 
  public class Main {
    int x = 5;

    public static void main(String[] args) {
      Main myObj = new Main();
      System.out.println(myObj.x);
    }
  }
  ```
  `static` is used for class method. `public` can only be accessed by instance. 
  ```java 
  public class Main {
    // Static method
    static void myStaticMethod() {
      System.out.println("Static methods can be called without creating objects");
    }

    // Public method
    public void myPublicMethod() {
      System.out.println("Public methods must be called by creating objects");
    }

    // Main method
    public static void main(String[] args) {
      myStaticMethod(); // Call the static method
      // myPublicMethod(); This would compile an error

      Main myObj = new Main(); // Create an object of Main
      myObj.myPublicMethod(); // Call the public method on the object
    }
  }
  ```
  #### Constructor 
  ```java 
  // Create a Main class
  public class Main {
    int x;  // Create a class attribute

    // Create a class constructor for the Main class
    public Main() {
      x = 5;  // Set the initial value for the class attribute x
    }

    // You can also add parameters 
    public Main(int y) {
      x = y 
    }
  ```
  Note that the constructor name must match the class name, and it cannot have a return type (like void).

  Also note that the constructor is called when the object is created.

  All classes have constructors by default: if you do not create a class constructor yourself, Java creates one for you. However, then you are not able to set initial values for object attributes.

  #### Modifiers 
  We divided modifiers into two groups:
  - Access modifiers 
  - Non-Access modifiers 

  Here are the one for access modifiers:
  - For Classes 
    - `public` - The class is accessible by any other class 
    - `default` - The class is accisible by class in the same package. This is when you don't specify a modifier
  - For attributes, methods, and constructors 
    - `public` - The code is accessible for all classes 
    - `private` - The code is only accesible within the declared class 
    - `default` - The code is only accessible in the same package. This is used when you don't specify a modifier.
    - `protected` - The code is accessible in the same package and subclasses.

  Here are the one for Non-access modifiers:
  - For Classes:
    - `final` - The class cannot be inherited by other classes
    - `abstract` - The class cannot be used to create object. To access an abstract class, it must be inherited from another class.
  - For attributes and methods:
    - `final` - attribute cannot be overriden or modified 
    - `static` - attributes belong to the class not the object 
    - `abstract` - Can only be used in an abstract class, and can only be used on methods. The method does not have a body, for example abstract void run();. The body is provided by the subclass (inherited from).
    - `transient` - Attributes and methods are skipped when serializing the object containing them
    - `synchronized` - Methods can only be accessed by one thread at a time
    - `volatile` - 	The value of an attribute is not cached thread-locally, and is always read from the "main memory"

  #### Java Encapsulation 
  The meaning of __Encapsulation__, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:

  - declare class variables/attributes as `private`
  - provide public `get` and `set` methods to access and update the value of a private variable

  This is the same as the `@property` then `@name_method.getter` decorators in python. Here is the syntax:
  ```java
  public class Person {
    private String name; // private = restricted access

    // Getter
    public String getName() {
      return name;
    }

    // Setter
    public void setName(String newName) {
      this.name = newName;
    }
  }
  ```

  #### __`Package and API`__ (Hightlight for the importance)
  So in Java, it is similar to python that a package is a folder that groups together related classes. Each file is called a module in python. In java, each file contains exactly one class (I don't know why). There are two types of packages:
  - Built-in Packages (packages from the Java API)
    - Here is the link to all built-in packages: https://docs.oracle.com/javase/8/docs/api/.
  - User-defined Packages (create your own packages)

  To import things, do this 
  ```java 
  import package.name.Class;   // Import a single class
  import package.name.*;   // Import the whole package

  // Import everything in the packages 
  import java.util.*;

  // -> Here java.util is a class
  ```
  To create a package, use the `package` keyword. 
  ```java 
  // MyPackageClass.java 

  package mypack;
  class MyPackageClass {
    public static void main(String[] args) {
      System.out.println("This is my package!");
    }
  }
  ```
  Now you can just compile it using `C:\Users\Your Name>javac MyPackageClass.java`. Then you can compile the package `C:\Users\Your Name>javac -d . MyPackageClass.java`. The `-d` here is to specify the destination.
  The package name should be written in lowercase

  #### Java Inheritence 
  ```java 
  // To inheritence from a clas s
  class Car extends Vehicle {}
  ```
  ```java
  // Here is how to do the famous polymorphism 
  class Animal {
    public void animalSound() {
      System.out.println("The animal makes a sound");
    }
  }

  class Pig extends Animal {
    public void animalSound() {
      System.out.println("The pig says: wee wee");
    }
  }

  class Dog extends Animal {
    public void animalSound() {
      System.out.println("The dog says: bow wow");
    }
  }
  ```
  #### Java inner classes 
  The idea here is nested classes. So classes that are defined within a class. So you will need to create an object of the outer class first to create an object of the inner class. 
  ```java
  class OuterClass {
    int x = 10;

    class InnerClass {
      int y = 5;
    }
  }

  public class Main {
    public static void main(String[] args) {
      OuterClass myOuter = new OuterClass();
      OuterClass.InnerClass myInner = myOuter.new InnerClass();
      System.out.println(myInner.y + myOuter.x);
    }
  }
  ```
  Here is where thing get interested. The inner class can use the modifier like `private` or `protected`. 
  - `private` is when you don't want the outside objects to access the inner class. 
  - `static` make your inner class available without even creating an outer instance first. 

  Note that the inner class can always access attributes and methods from the outer classes. 

  #### Interface 
  An interface is a completely "abstract class" that is used to group related methods with empty bodies. So you don't need to do the `abstract MyClass` thingy anymore. Python does not have this. Here is the syntax:

  ```java
  // interface
  interface Animal {
    public void animalSound(); // interface method (does not have a body)
    public void run(); // interface method (does not have a body)
  }

  // Pig "implements" the Animal interface
  class Pig implements Animal {
    public void animalSound() {
      // The body of animalSound() is provided here
      System.out.println("The pig says: wee wee");
    }
    public void sleep() {
      // The body of sleep() is provided here
      System.out.println("Zzz");
    }
  }
  ```

  The only thing that you need to note here is that different from abstract class, an interface cannot contain a constructor (as it cannot be used to create objects).