### Key Points on Object in Java

- **Creating an Object**: `Person john = new Person("John", 25);`
- **Accessing Object Members**: `john.greet(); // Access method; john.age = 26; // Access field`
- **Object References**: `Person anotherJohn = john; // Another reference to the same object`
- **Garbage Collection**: `System.gc(); // Request garbage collection (optional)`

### Key Points on Class in Java

- **Class Declaration**: `public class ClassName { /* fields and methods */ }`
- **Access Modifiers**: `public class PublicClass { } // Accessible everywhere`
- **Constructors**: `public ClassName() { /* constructor body */ }`
- **Static Members**: `public static int count = 0; // Shared across instances`

### Key Points on Inheritance in Java

- **Extending Classes**: `class SubClass extends SuperClass { /* additional fields and methods */ }`
- **Overriding Methods**: `@Override public void methodName() { /* new implementation */ }`
- **Using super Keyword**: `super.methodName(); // Calls superclass method`

### Key Points on Interface in Java

- **Declaring an Interface**: `public interface InterfaceName { void methodName(); }`
- **Implementing Interfaces**: `class ClassName implements InterfaceName { /* implementations */ }`
- **Multiple Inheritance with Interfaces**: `class ClassName implements Interface1, Interface2 { /* implementations */ }`
- **Default and Static Methods**: `default void defaultMethod() { /* default implementation */ }`

### Key Points on Package in Java

- **Creating a Package**: `package com.example.project;`
- **Importing Packages**: `import java.util.ArrayList;`
- **Access Modifiers with Packages**: `public class PublicClass { /* accessible in any package */ }`

### Key Points on Variables in Java

- **Variable Declaration and Initialization**: `int number = 5; // declaration and initialization`
- **Instance Variable**: `public int instanceVar; // each instance has its own copy`
- **Static Variable**: `public static int sharedVar = 10; // shared across all instances`
- **Local Variable**: `void myMethod() { int localVar = 20; } // accessible only in this method`
- **Parameter Variable**: `void myMethod(int param) { /* parameter used as input */ }`
- **Final Variable**: `final int MAX_VALUE = 100; // constant, cannot be changed`

### Key Points on Primitive Data Types in Java

- **Primitive Type Declaration**: `int age = 25; // declares a simple int variable`
- **Byte Type**: `byte smallNum = 10; // occupies 1 byte of memory`
- **Double Type**: `double pi = 3.14159; // floating-point, occupies 8 bytes`
- **Default Value**: `boolean flag; System.out.println(flag); // prints default 'false'`
- **Wrapper Class**: `Integer obj = Integer.valueOf(10); // wrapper for int`

### Key Points on Arrays in Java

- **Array Declaration and Initialization**: `int[] numbers = {1, 2, 3, 4, 5}; // initialize with values`
- **Accessing Array Elements**: `int firstNumber = numbers[0]; // accesses first element`
- **Array Length**: `int length = numbers.length; // gets the number of elements`
- **2D Array Declaration**: `int[][] matrix = new int[3][3]; // creates a 3x3 matrix`
- **2D Array Access**: `matrix[0][1] = 5; // assigns 5 to element in the first row, second column`

### Key Points on Assignment, Arithmetic, and Unary Operators in Java

- **Assignment Operator**: `int a = 5; // assigns 5 to a`
- **Compound Assignment**: `a += 5; // equivalent to a = a + 5`
- **Arithmetic Operator**: `int result = 10 + 5; // addition`
- **Unary Increment**: `int a = 5; a++; // increments a by 1`
- **Operator Precedence**: `int result = 5 + 2 * 3; // evaluates as 5 + (2 * 3)`

### Key Points on Equality, Relational, and Conditional Operators in Java

- **Equality Operator**: `boolean isEqual = (a == b); // checks if a equals b`
- **Relational Operator**: `boolean isGreater = (a > b); // checks if a is greater than b`
- **Logical AND**: `boolean isBothTrue = (a > 0) && (b > 0); // true if both are true`
- **Ternary Operator**: `int max = (a > b) ? a : b; // assigns larger of a or b to max`
- **Short-Circuiting**: `boolean result = (a > 0) && (b++ > 0); // b++ is evaluated only if a > 0`

### Key Points on Bitwise and Bit Shift Operators in Java

- **Bitwise AND**: `int result = a & b; // bitwise AND of a and b`
- **Bitwise OR**: `int result = a | b; // bitwise OR of a and b`
- **Left Shift**: `int result = a << 1; // shifts bits of a left by 1`
- **Right Shift**: `int result = a >> 1; // shifts bits of a right by 1`
- **Unsigned Right Shift**: `int result = a >>> 1; // shifts bits of a right by 1, fills leftmost with 0`

### Key Points on Expressions, Statements, and Blocks in Java

- **Expression**: `int sum = a + b * c; // evaluates to a single value`
- **Statement**: `int x = 5; // complete unit of execution`
- **Block**: `{ int y = 10; y++; } // group of statements with its own scope`
- **Expression Statement**: `x = y + z; // performs assignment and completes action`
- **Control Flow with Block**: `if (condition) { statement1; statement2; } // both statements execute if condition is true`

### Key Points on The if-then and if-then-else Statements in Java

- **if-then Statement**: `if (x > 0) { System.out.println("Positive"); } // executes if condition is true`
- **if-then-else Statement**: `if (x > 0) { System.out.println("Positive"); } else { System.out.println("Non-positive"); }`
- **Nested if Statements**: `if (x > 0) { if (y > 0) { System.out.println("Both positive"); } }`
- **else-if Ladder**:
  ```java
  if (x > 0) { System.out.println("Positive"); }
  else if (x < 0) { System.out.println("Negative"); }
  else { System.out.println("Zero"); }
  ```
- **Single-line if Statement**: if (x > 0) System.out.println("Positive");

### Key Points on The switch Statement in Java

- **Purpose of switch Statement**: `switch(day) { case 1: System.out.println("Monday"); break; } // multi-way branching based on 'day'`

- **Basic Syntax**:
  ```java
  switch (value) {
      case 1: System.out.println("One"); break;
      case 2: System.out.println("Two"); break;
      default: System.out.println("Other"); // default case if no match
  }
  ```
- **case and break Statements**: `case 1: System.out.println("One"); break; // break prevents fall-through to the next case`

- **default Case**: `default: System.out.println("Default case executed"); // executes if no other case matches`

- **Supported Data Types**: `switch (letter) { case 'A': System.out.println("A selected"); break; } // works with char, String, int, etc.`
