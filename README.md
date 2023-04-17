## SWEN20003: object-oriented Software development

[TOC]



### Lecture 1-2: Introduction to Java

#### How java is compiled and interpreted:

![Screenshot from 2023-04-16 15-24-01](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 15-24-01.png)

Java compiler convert **java source** (file with .java) code to **byte-code** (file with .class)

**Interpreter(JVM)** on any target platform interprets the byte-code

#### Java is platform-independent and portable

#### object oriented

Java is an Object Oriented Programming (OOP) language

Common programming constructs are: Classes, Objects, Methods etc.

#### Basic Java

```java
import java.lang.*;
public class HelloWorld{
    public static void main(String args[]){
        System.out.println("HelloWorld");
        return;
    }
}
```

##### comments in Java:

Java supports 3 types of comments:

- /* */ - Usually used from multi-line comments, similar to C.
- // - Used for single line comments.
- /** */ - Documentation comments, will learn more later.

##### import packages:

In Java, classes are grouped into packages

```java
import java.lang.*
```

Serves the same purpose as the #include statement used in C. Is used to import additional classes

##### Identifiers:

definition: A name that uniquely identifies a program element such as a class, object, variable, method.

Java identifier rules:

- must not start with a digit
- all the characters must be letters, digits, or the underscore symbol
- can theoretically be of any length
- are case-sensitive: Rate, rate, and RATE are different variables

Java identifier conventions:

- variables, methods, and objects: start with a lower case letter, indicate ”word” boundaries with an uppercase letter, and restrict the remaining characters to digits and lowercase letters (e.g. ``topSpeed``, ``bankRate``, ``timeOfArrival``)
- classes: start with an upper case letter and, otherwise, adhere to the rules
  above (e.g. ``PrintDemo``,`` HelloWorld``)

Identifiers that have a predefined meaning in Java, such as keywords and reserved words, must not be used as as identifiers in your programs: e.g. ``public``, ``class``, ``void``, ``static``

##### Data Types:

![Screenshot from 2023-04-16 15-36-50](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 15-36-50.png)

![Screenshot from 2023-04-16 15-37-24](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 15-37-24.png)

Floating point numbers:

- float type has single-precision.
- double type has double-precision.
- Generally, floating point numbers are treated as double-precision numbers. To force them to be in single precision we must append f or F to the number: e.g. float a = 2.3F; double b = 6.7;

##### Variables:

definition: Refers to information that is stored in program memory that can be changed; a variable has a memory location and an identifier.

Variables must be declared and initialised before use.

```
<type> <variable name> = <initial value>
```

Assignment operator is used to change the value of a variable.

```
<variable name> = <other variable name> OR <value> OR <expression>
```

Java variables are classified into three categories:

- instance variables

- > static (or class) variables: A property or attribute that is unique to each instance (object) of a class.

- > local variables: Variables defined inside a Java method.

##### Constants:

Definition: A value that does not change during the execution of the program; also called “READ” only values.

- Constants are declared with the Java key word ``final``.
- By convention upper case letters are used for defining constants.
- Data type must be explicitly specified when defining constants; this is not
  required in C.

##### Operators and Expressions:

Bit-wise Operators:

![Screenshot from 2023-04-16 15-57-00](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 15-57-00.png)



Conditional Operators:

```java
x = (a > b) ? a:b;
//this is equivalent to the if statement below
if(a>b){
x=a;
}else{
x=b;
}
```

##### Mathematical Functions:

Java supports mathematical functions such as cos, sin, log using the ``Math`` class, defined in the ``java.lang ``package.

```java
Math.method_name()
```

##### Flow of Control:

Definition: Refers to branching and looping mechanisms in the Java language.

The ``switch`` statement:

```java
switch (Controlling_Expression){
	case Case_Label_1:
		Statement_Sequence_1;
        break;
    case Case_Label_1:
		Statement_Sequence_1;
        break;
    default:
        Default_Statement Sequence;
        break;
}
```

Java supports ``while``statement and ``do-while`` statement 



### Lecture 3-5: Classes and Objects

All programming languages support four basic concepts:

- Calculation: constants, variables, operators, expressions
- Selection: if-else, switch, ?
- Iteration: while, do, for
- Abstraction: The process of creating self-contained units of software that allows the solution to be parameterized and therefore more general purpose

Note: Abstraction is the fundamental concept that differentiates procedural programming language such as C from OOP language such as Java, C++

Abstraction in procedural languages is provided through ``functions`` or ``procedures``

Abstraction in OOP language is provided through an Abstract Data Type, which contains data and functions that operate on data (In Java a Class is an implementation on an ADT)

#### Classes: 

> Definitions: Fundamental unit of abstraction in Object Oriented Programming. Represents an “entity” that is part of a problem.

- A generalisation of a real world entity
- Represents a template for things that have common properties
- Contains attributes and methods
- Defines a new data type



##### Define A class:

```java
<visibility modifier> class <ClassName>{
    
    <attribute declarations>;
    <visibility modifier> <type> <variable name>;
        
    <method declarations>;
    <visibility modifier> <void or typeReturned> myMethod(parameter list){
        statement;
    }
}
```



Using a class: we need to compile ``.java`` file first and then we can use ``.class``  file as a derived data type in Java program

```java
<className> variableName; 
```

Since we are not create an object, this variable is simply references to class objects.

Currently they point to nothing, hence ``null reference``

> null: The Java keyword for “no object here”. Null objects can’t be “accessed” to get variables or methods, or used in any way.



##### Getter, Setter and Constructors:

- Generally initialising/updating/accessing instance variables is done by defining specific methods for each purpose.
- These methods are called ``Accessor``/``Mutator  ``methods or informally as ``Getter``/``Setter`` methods.
- IDE support automatic code generation for getters and setters;



Constructors:

```java
Circle aCircle = new Circle();
```

- Constructors are methods and used to initialise objects.
- Constructors have the same name as the class
- Constructors cannot return values
- A class can have one or more constructors, each with a different set of parameters (called overloading; we’ll cover this later)



Method Overloading:

Methods have the same name; are distinguished by their signature:

- number of arguments
- type of arguments
- position of arguments

Any method can be overloaded (Constructors or other methods).

Method Overloading: This is a form of polymorphism (same method – different behaviour).

> Method Overloading: Ability to define methods with the same name but with different signatures (argument types and/or numbers).



##### Static attributes and methods

Defining Static variables:  Static attributes are shared between objects (only one copy)

difference between instance variable and static variable:

- Instance variables: One copy per object. e.g. ``centreX``, ``centreY``, radius (centre and radius in the circle)
- Static variables: One copy per class. e.g. ``numCircles`` (total number of circle objects created)



Using Static Methods:

- Static methods can only call other static methods
- Static methods can only access static data.
- Static methods cannot refer to Java keywords such as, this or super (will be introduced later) - because they are related to objects (class instances).
- Do not make all methods and attributes in your classes static; if you do that you may end up writing procedural programs using Java as opposed to good OO programs



##### Standard Methods in Java:

Standard Methods ``equals`` : It is useful to be able to compare if two objects are equal	

Standard Methods ``toString``: The ``toString`` method which returns a String representation of an object
is the way to go

Standard Methods``copy`` : Creates a separate copy of the object sent as input. The copy constructor should create an object that is a separate, independent object, but with the instance variables set so that it is an exact copy of the argument object.

Note: In case some of the instance variables are references to other objects, a new object with the same state must be created using its copy constructor - deep copy

#### Objects:

> Definition: A specific, concrete example of a class

- An instance of a class
- Contain state, or dynamic information

Object are ``null`` until they are instantiated(to create an object of a class):

```java
Circle circle_1 = new Circle()
```

> new: Directs the JVM to allocate memory for an object, or instantiate it



#### Object Oriented Features:

- Data Abstraction

  > Data Abstraction: The technique of creating new data types that are well suited to an application by defining new classes

- Encapsulation

  > **Encapsulation**: The ability to group data (attributes) and methods that manipulate the data to a single entity though defining a class.

  A class encapsulates data and the methods that operate on the data into an single unit

  This method of encapsulation is unique to OOP language and not provided by the procedural programming paradigm

- Information Hiding

  > **Information Hiding**: Ability to “hide” the details of a class from the outside world.

  > **Access Control**: Preventing an outside class from manipulating the properties of another class in undesired ways.

  Visibility Modifiers:

  - public: Keyword when applied to a class, method or attribute makes it
    available/visible everywhere (within the class and outside the class).
  - private: Keyword when applied to a method or attribute of a class, makes them
    only visible within that class. Private methods and attributes are not visible within
    sub-classes, and are not inherited.
  - protected: Keyword when applied to a method or attribute of a class, makes them
    only visible within that class, subclasses and also within all classes that are in the
    same package as that class. They are also visible to subclasses in other packages.

  Java provides control over the visibility (access) of variables and methods
  through visibility modifiers:

  - This allows to safely seal data within the capsule of the class
  - Helps in protecting against accidental or wrong usage
  - Enables to provide access to the object through a clean interface

  > **Mutable**: A class that contains public mutator methods or other public methods that can change the instance variables is called a mutable class, and its objects are called mutable objects.

  > **Immutable**: A class that contains no methods (other than constructors) that change any of the instance variables is called an immutable class, and its objects are called immutable objects.

- Delegation

  - A class can delegate its responsibilities to other classes

  - An object can invoke methods in other objects through containership

  - This is an Association relationship between the classes

- Inheritance

- Polymorphism

  > Polymorphism: Ability to process objects differently depending on their data type or class.

#### Introducing Java Packages:

> Package: Allows to group classes and interfaces (will be introduced later) into bundles, that can then be handled together using an accepted naming convention.

Why would you group classes into packages:

- Works similar to libraries in C; can be developed, packaged, imported and used by other Java programs/classes.
- Allows reuse, rather than rewriting classes, you can use existing classes by importing them.
- It is another level of Encapsulation.



Creating Java packages:  To place a class in a package, the first statement in the Java class must be
the package statement with the following syntax

```
package <directory_name_1>.<directory_name_2>;
```



##### Wrapper Class

> Primitive: A unit of information that contains only data, and has no attributes or methods

Since primitive data types don't have attributes and methods, java provides "wrapper" classes for primitive

> Wrapper: A class that gives extra functionality to primitives like int, and lets them behave like objects

![Screenshot from 2023-04-16 17-10-58](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 17-10-58.png)



Automatic Boxing/Unboxing:

> **(Un)Boxing:** The process of converting a primitive to/from its equivalent wrapper class



### Lecture 6: Software Tools

#### Version Control: Git

Software Version Control: A systematic way to manage concurrent versions of software artefacts
- documents, source code, data etc

Why we need software version control?

- As an individual, version control allows you to keep a version of the software saved, so that you can revert back to the previous version if necessary.
- In a team software development setting, version control allows developers to write and test code locally before including that to code base



![Screenshot from 2023-04-16 17-16-23](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 17-16-23.png)

![Screenshot from 2023-04-16 17-17-13](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 17-17-13.png)

![Screenshot from 2023-04-16 17-17-45](/home/charles/Pictures/Screenshots/Screenshot from 2023-04-16 17-17-45.png)

#### Build Management with Maven

build management/automation tools aim to automate the process of building (compiling) software

Maven is a popular software build management tool. Maven simplifies the process to build software by automatically importing the required libraries and dependencies from external repositories.



#### BAGEL: (Basic Academic Graphical Engine Library)

##### ``update`` method:

about 60 times per second, Bagel:

- Clears the window of images, leaving a uniform colour
- Checks for keyboard or mouse input
- Call the update method

##### ``Image`` class:

- Creates an Image object and call the ``draw()`` method
- An image can be drawn on the screen
- The draw() method should be called from the ``update()`` method
- ``Window`` class contains static methods to work with the display window

##### ``Input`` class:

- Passed as an argument to the ``update()`` method
- Can be used to work with the keyboard and mouse
- Has method to check key press and mouse click event



### Lecture 7: Array and Strings

> Array: A sequence of elements of the same type arranged in order in memory

##### Declaration:

```
basetype[] varName;\\ OR
basetype varName[];
```

- Array is data type, similar to data types you create by defining
- Array are references
- Manipulating one reference affects all references

##### Array Methods:

- Indexing
- Length: ``intArray.length``
- Equality: ``Arrays.equals(arr1,arr2)``
- Resizing: Arrays are fixed length, resizing requires creating a new array
- Sorting: ``Arrays.sort(n1)`` in ascending order
- Printing: ``System.out.println(Arrays.toString(n1))``



##### Strings

> String: A Java class made up of a sequence of characters.

- String is an class and a data type
- Strings store sequences of characters
- String are immutable, once created, they cannot be modified, only replaced
- Every String operation returns a new String
- Java string are almost identical to Python, except you can't use single quotes
- newline character ``"\n"``, tab character``"\t"``, quotation mark ``"\""``

String Operations: You can use ``+``and  ``+=`` to append/concatenate two strings

##### String Methods:

- Length: ``<string variable>.length()``

- Upper\Lower case: `.toUpperCase()`

- Split: `.split(token)`

- Check `.contains("target string or char")`

- Find sub-string location: `.indexOf(token)`

- Sub-string: `.substring(2,7)`

  

### Lecture 8: Input and Output

##### Input: 

> Command Line Argument: Information or data provided to a program when it is executed, accessible through the `args` variable.

`args` is a variable that stores command line arguments

##### Scanner

```java
import java.util.Scanner;
Scanner scanner = new Scanner(System.in); //stream/pipe receive data from Stdin
```

Note: Only ever create one Scanner for each program, or bad things happen

```java
String s = scanner.nextLine(); //read nextLine until a "return" or newline character
boolean b = scanner.nextBoolean();
int i = scanner.nextInt();
double d = scanner.nextDouble();
```

```java
scanner.hasNext(); //return true if there is any input to be read
scanner.hasNextXXX(); // Returns true if the next "token" matches XXX
```

##### Reading files:

```java
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

try(BufferedReader br = new BufferedReader(new FileReader("test.txt"))){
    while((text=br.readLine())!= null){
        
    }
} catch (Exception e){
    e.printStackTrace(); 
}

//Works the same as BufferedReader, but allow us to parse the text
//Smaller buffer size(internal memory), slower, works on smaller files
public class ReadFile2 {
	public static void main(String[] args) {
		try (Scanner file = new Scanner(new FileReader("test.txt"))) {
			while (file.hasNextLine()) {
				System.out.println(file.nextLine());
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```

This Line one create two objects:

- `FileReader` - a low level file for simple character reading
- `BufferedReader`- A higher level file that permits reading Strings, not just characters

`try/catch` exception handling statement



##### Output:

```java
import java.io.FileWriter;
import java.io.PrintWriter;
import java.io.IOException;

try(PrintWriter pw = new PrintWriter(new FileWriter("testOut.txt"))){
    pw.println("Hello World");
    pw.format("My least favourite device is %s and its price is $%d","iPhone", 100000);
}catch (IOExceotion e){
    e.printStackTrace();
}
```

Creates two objects:

- `FileWriter` - a low level file for simple character output, used to create
- `PrintWriter` - A higher level file that allows more sophisticated formatting



### Lecture 9-10: Inheritance and Polymorphism

> Inheritance: A form of abstraction that permits “generalisation” of similar attributes/methods of classes; analogous to passing genetics on to your children.

> Superclass: The “parent” or “base” class in the inheritance relationship; provides general information to its “child” classes.

> Subclass: The “child” or “derived” class in the inheritance relationship; inherits common attributes and methods from the “parent” class.

- Define comon attributes and methods in Superclass (base class)

- Subclass automatically contains all (public/protected) instance

- additional methods and/or instance variables can be defined in the subclass

- Inheritance allows code to be reused

- Subclass should be more specific version of a super class

  

#### Inheriting Attributes and Methods

```java
//define super class
public class Piece{
  private int currRow;
  private int currCol;
  public int getCurrRow(){
    return currRow;
  }
  public void setCurrentRow(){
    
  }
}

//define subclass
public class Rook extends Piece{
  public void move(int Row, int toColumn){
    
  }
  public boolean isValidMove(int toRow, int toCol){
    
  }
}
```

> extends: Indicates one class inherits from another

> super: Invokes a constructor in the parent class

```java
//invoke super in sub-class constructor methods
public class Rook extends Piece{
  public Rook(int currRow, int currCol){
    super(currRow, currCol);
    //Any other operation
  }
}
```

- Super constructor may only be used within a subclass constructor
- Must be the first statement in the subclass constructor (if used)



#### Inheriting and Overriding Methods

- When a method is defined only in the parent class, it gets called regardless of the type of object created
- When a method with same signature is defined both in the parent class and the child class, which method executes purely depends on the type of objects as opposed to the type of reference
- In the latter case, the child class method Overrides the method in the parent class
- Annotation `@Overrides` can be used in code to indicate that the method is overriding method in the parent class.

> Overriding: Declaring a method that exists in a superclass again in a subclass, with the same signature. Methods can only be overriden by subclasses.



> Overloading: Declaring multiple methods with the same name, but differing method signatures. Superclass methods can be overloaded in subclasses.

Why we need Override?

- Subclasses can extend functionality from a parent
- Subclasses can override/change functionality of a parent
- Makes the subclass behaviour available when using references of the superclass type
- Defines a general "interface" in a superclass, with specific behaviour implemented in the subclass

Note: Override cannot change return type



#### Inheritance and Information Hiding

Note: `Private` method cannot be overridden. If the sub-class has private method `isValidMove` will not override the parent method

if you dont want subclasses to override a method, you can use `final`

> final: Indicates that an attribute, method, or class can only be assigned, declared or defined once.



#### Access Control

Child classes cannot call `private` method, and cannot access `private` attributes of parent classes

Child classes can call `protected` method, and can access `protected` attributes of parent classes

##### Privacy Leaks

Defining attributes as protected allows updating them directly from child classes. However, this should be avoided because it results in privacy leaks. The attributes of the parent class should be accessed via public or protected methods in the parent class.



Methods in the parent class that are only used by subclasses should be defined as `protected`



When overriding a method, a child class cannot further restrict the visibility of an overriden method. When overriding:

- a `public` method in the parent class must remain `public` in the child class
- a `protected` method in the parent class can remain `protected` in the derived or can be made `public`
- a `private` method in the parent class cannot be overridden 



You only need to define one common variable in the superclass. Please do not do the shadowing

> Shadowing: When two or more variables are declared with the same name in overlapping scopes; for example, in both a subclass and superclass. The variable accessed will depend on the reference type rather than the object.



##### Privacy Revisited

> public: Keyword when applied to a class, method or attribute makes it available/visible everywhere (within the class and outside the class).

> private: Keyword when applied to a method or attribute of a class, makes them only visible within that class. Private methods and attributes are not visible within subclasses, and are not inherited.

> protected: Keyword when applied to a method or attribute of a class, makes them only visible within that class, subclasses and also within all classes that are in the same package as that class. They are also visible to subclasses in other packages.

![Screenshot 2023-04-17 at 11.58.54 am](/Users/charles/Library/Application Support/typora-user-images/Screenshot 2023-04-17 at 11.58.54 am.png)

#### The Object Class

Every class in Java implicitly inherits from the Object class

> getClass: Returns an object of type Class that represents the details of the calling object’s class.

> instanceof: An operator that gives true if an object A is an instance of the same class as object B, or a class that inherits from B.

```java
return new Rook() instanceof Piece;
```

> Upcasting: When an object of a child class is assigned to a variable of an ancestor class.

```java
Piece p = new Rook(2,3);
```

> Downcasting: When an object of an ancestor class is assigned to a variable of a child class. Only makes sense if the underlying object is actually of that class. Why?

```java
Piece robot = new WingedRobot();
WingedRobot plane = (WingedRobot) robot;
```



##### Polymorphism:

> Polymorphism: The ability to use objects or methods in many different ways; roughly means “multiple forms”.

Overloading: Same method with various forms depending on signature (Ad Hoc polymorphism)

Overriding: Same method with various forms depending on class (Subtype polymorphism)

Substitution: using subclasses in place of superclasses (Subtype polymorphism)

Generics: defining parametrised methods/classes (Parametric polymorphism, coming soon)



##### Abstract Classes

Some classes arent meant to be instantiated because they arent completely defined. Although they are nouns they do not correspond to a real-world entity but is only an abstraction to define a class of entities

> Abstract Class: A class that represents common attributes and methods of its subclasses, but that is missing some information specific to its subclasses. Cannot be instantiated.

> Concrete Class: Any class that is not abstract, and has well-defined, specific implementations for all actions it can take.

> abstract: Defines a class that is incomplete. Abstract classes are “general concepts”, rather than being fully realised/detailed.

```java
<visibility> abstract class <ClassName> {
	//Attributes and Methods go here
}
```



Abstract Methods:

> abstract: Defines a superclass method that is common to all subclasses, but has no implementation. Each subclass then provides its own implementation through overriding.

```java
<privacy> abstract <returnType> <methodName>(<arguments>);
```



Abstract classes are identical, except:

- May have abstract methods - abstract classes can have no abstract methods
- Classes with abstract methods must be abstract
- Cannot be instantiated
- Represent an incomplete concept, rather than a thing that is part of a problem



Type of Inheritance

- Single inheritance (only one super class)
- Multiple inheritance (several super classes)
-  Hierarchical inheritance (one super class, many sub classes) 
- Multi-Level inheritance (derived from a derived class) 
- Hybrid inheritance (more than two types)
- Multi-path inheritance (inheritance of some properties from two sources).

Note: Java does not support Multiple inheritance, and hence some other forms of inheritance that involves multiple inheritance, such as Multipath inheritance



### Lecture 11: Interfaces and Polymorphism

#### Interfaces

> Interface: Declares a set of constants and/or methods that define the behaviour of an object.

Interfaces are vague, distant relatives of abstract classes:

- Define an "abstract" entity, cannot be instantiated
- Can only contain constant and abstract method
- Defines behaviours/actions that are common across a number of classes
- A class can choose to "implement" an interface
- All interfaces represent a "can do" relationship
- Classes that implement an interface can do all the actions defined by the interface
- Interface names are generally called `<...>able`, and relate to an action, For example, classes that implement the `<Drivable>` interface can all be driven, because they implement the `drive()` method



##### Defining Interfaces:

```java
public interface Printable{
  int MAXIMUM_PIXEL_DENSITY = 1000;
  void print();
}
```

- Method never have any code
- All methods are implied to be abstract
- All attributes are implied to be static final
- All methods and attributes are implied to be public



> implements: Declares that a class implements all the functionality expected by an interface.



```java
public class Image implements Printable{
  public void print(){
    //<block of code to execute>
  }
}
```

- Contrete classes that implement an interface must implement all methods it defines
- Classes taht don't implement all methods must be abstract



> default: Indicates a standard implementation of a method, that can be overridden if the behaviour doesn’t match what is expected of the implementing class.

Classes can be "forced" to have an implementation of a method, that can then be overridden



##### Externd Interfaces

```java
public interface Digitsable extends Printable{
	public void digitise();
}
```

- Interfaces can be extended just like classes
- Forms the same "Is a" relationship
- Used to add additional, specific behaviour



##### Comparable Interfaces

A class that implements ``comparable<className>`

- Can be compared with objects of the same class
- Must implement `public int compareTo(<className> object)`
- Can therefore be sorted automatically



Classes can only inherit one class, but can implement multiple interfaces

Inheritance and interfaces works together to build very powerful abstractions that make creating solution much easier



#### Polymorphism







### Lecture 12: Revision-1



