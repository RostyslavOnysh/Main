# The Java String class :

represents character strings. All string literals in Java programs, such as "hello world", are implemented as instances of this class.
Strings are constant; their values cannot be changed after they are created.
Because String objects are immutable, they can be shared. For example:
```java
                String str1 = "hello";
                String str2 = "world";
                String str3 = str1 + " " + str2;
 ```
In this example, str1 and str2 are string literals, and str3 is created by concatenating str1, a space character, and str2. The result is a new string object that represents the concatenation.

Here are some of the key methods of the String class:

* *length():* Returns the length of the string.

* *charAt(int index):* Returns the character at the specified index.

* *substring(int beginIndex):* Returns a substring that begins at the specified index and extends to the end of the string.

* *substring(int beginIndex, int endIndex):* Returns a substring that begins at the specified beginIndex and extends to the character at index endIndex - 1.

* *indexOf(String str):* Returns the index within the string of the first occurrence of the specified substring.

* *lastIndexOf(String str):* Returns the index within the string of the last occurrence of the specified substring.

* *startsWith(String prefix):* Tests if the string starts with the specified prefix.

* *endsWith(String suffix):* Tests if the string ends with the specified suffix.

* *contains(CharSequence s):* Returns true if and only if this string contains the specified sequence of char values.

* *equals(Object anObject):* Compares this string to the specified object.

* *equalsIgnoreCase(String anotherString):* Compares this String to another String, ignoring case considerations.

* *compareTo(String anotherString):* Compares two strings lexicographically.

* *LowerCase():* Converts all of the characters in this String to lower case using the rules of the default locale.

* *toUpperCase():* Converts all of the characters in this String to upper case using the rules of the default locale.

* *trim():* Returns a copy of the string, with leading and trailing whitespace omitted.

* *split(String regex):* Splits this string around matches of the given regular expression.

* *getBytes():* Encodes this String into a sequence of bytes using the platform's default charset.
