
# Strings in Java

1. **String Class**: In Java, a `String` is an immutable sequence of characters. Once a `String` object is created, its value cannot be changed. This immutability makes strings safer to use in multi-threaded environments:
   ```java
   String str = "Hello, World!";
   // str = "New String"; // This creates a new String object
   ```

2. **String Concatenation**: You can concatenate strings using the `+` operator or the `concat()` method. The `StringBuilder` class is recommended for frequent modifications to improve performance:
   ```java
   String greeting = "Hello, " + "World!"; // Using + operator
   String fullGreeting = "Hello, ".concat("World!"); // Using concat()
   ```

3. **String Methods**: The `String` class provides various methods for manipulating strings, including:
   - `length()`: Returns the length of the string.
   - `charAt(int index)`: Returns the character at the specified index.
   - `substring(int start, int end)`: Extracts a substring from the string.
   - `toUpperCase()`, `toLowerCase()`: Converts the string to upper or lower case.
   ```java
   String text = "Java Programming";
   int length = text.length(); // 16
   char firstChar = text.charAt(0); // 'J'
   String sub = text.substring(0, 4); // "Java"
   ```

4. **String Comparison**: Strings can be compared using the `equals()` method or the `compareTo()` method. The `==` operator compares object references, not the content:
   ```java
   String str1 = "Java";
   String str2 = "Java";
   boolean areEqual = str1.equals(str2); // true
   int comparison = str1.compareTo("Java"); // 0 (equal)
   ```

5. **String Formatting**: The `String.format()` method and `printf()` function allow formatted output. This is useful for creating strings with variable values or specific formatting:
   ```java
   String name = "Alice";
   int age = 30;
   String formattedString = String.format("%s is %d years old.", name, age);
   System.out.println(formattedString); // Outputs: Alice is 30 years old.
   ```
