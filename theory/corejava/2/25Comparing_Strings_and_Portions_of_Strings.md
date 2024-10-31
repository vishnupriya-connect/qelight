
# Comparing Strings and Portions of Strings in Java

1. **Using `equals()` Method**: The `equals()` method compares the content of two strings for equality. It returns `true` if the strings have the same sequence of characters, and `false` otherwise. This method is case-sensitive:
   ```java
   String str1 = "Hello";
   String str2 = "Hello";
   boolean isEqual = str1.equals(str2); // true
   ```

2. **Using `equalsIgnoreCase()` Method**: If you want to compare two strings while ignoring case differences, use the `equalsIgnoreCase()` method. This is useful when you want to perform a case-insensitive comparison:
   ```java
   String str1 = "hello";
   String str2 = "HELLO";
   boolean isEqualIgnoreCase = str1.equalsIgnoreCase(str2); // true
   ```

3. **Using `compareTo()` Method**: The `compareTo()` method compares two strings lexicographically. It returns:
   - A negative integer if the first string is less than the second.
   - Zero if both strings are equal.
   - A positive integer if the first string is greater than the second:
   ```java
   String str1 = "apple";
   String str2 = "banana";
   int comparisonResult = str1.compareTo(str2); // Negative value
   ```

4. **Comparing Portions of Strings**: To compare portions of strings, you can use the `substring(int beginIndex, int endIndex)` method to extract substrings and then compare them using `equals()` or `compareTo()`:
   ```java
   String str = "Hello, World!";
   String subStr1 = str.substring(0, 5); // "Hello"
   String subStr2 = "Hello";
   boolean isEqualSub = subStr1.equals(subStr2); // true
   ```

5. **Using `regionMatches()` Method**: The `regionMatches()` method allows you to compare a specific region of one string with a region of another string. This method can perform case-sensitive or case-insensitive comparisons:
   ```java
   String str1 = "Hello, World!";
   String str2 = "world";
   boolean regionMatch = str1.regionMatches(7, str2, 0, 5); // true (case-sensitive)
   boolean regionMatchIgnoreCase = str1.regionMatches(true, 7, str2, 0, 5); // true (case-insensitive)
   ```
