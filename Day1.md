# Java — Conditional Statements & `for` Loop

## Python → Java Concept Mapping

This README covers the **same concepts learned in Python**, but implemented using Java.

The goal is not simply to translate Python syntax.

The goal is to understand:

> **What does Python do, and what Java mechanism performs the same job?**

---

# 1. Python `for` Loop → Java `for` Loop

### Python

```python
for i in range(1, 6):
    print(i)
```

### Java

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

### Major Difference

Python:

```python
range(1, 6)
```

creates the sequence:

```text
1 2 3 4 5
```

Java does not have a direct equivalent of Python's `range()` for a traditional `for` loop.

Instead Java explicitly defines:

```java
for (initialization; condition; update)
```

### Java Syntax

```java
for (initialization; condition; update) {
    // logic
}
```

Example:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

---

# 2. Trace Java `for` Loop

Code:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

Execution:

```text
1. int i = 1
2. i <= 5 → true
3. print 1
4. i++
5. i = 2

6. i <= 5 → true
7. print 2
8. i++

...

17. i = 6
18. i <= 5 → false
19. loop ends
```

### Visual

```text
initialization
      ↓
   i = 1
      ↓
  condition
      ↓
   true?
   /   \
 yes    no
  ↓      ↓
body    stop
  ↓
update
  ↓
condition
```

---

# 3. Java Conditional Statements

### Python

```python
if x > 0:
    print("Positive")

elif x < 0:
    print("Negative")

else:
    print("Zero")
```

### Java

```java
if (x > 0) {
    System.out.println("Positive");
}
else if (x < 0) {
    System.out.println("Negative");
}
else {
    System.out.println("Zero");
}
```

### Difference

Python:

```text
elif
```

Java:

```text
else if
```

Python uses indentation.

Java uses:

```text
{}
```

for blocks.

---

# 4. Java Variables

Python:

```python
x = 10
```

Java:

```java
int x = 10;
```

Java requires a data type.

Common types:

```java
int
long
float
double
char
boolean
String
```

Example:

```java
int age = 21;
double price = 99.50;
char grade = 'A';
boolean active = true;
String name = "Daya";
```

This is one of the biggest differences between Python and Java.

---

# 5. Java Input

Python:

```python
num = int(input())
```

Java commonly uses `Scanner`:

```java
Scanner sc = new Scanner(System.in);

int num = sc.nextInt();
```

Complete example:

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int num = sc.nextInt();

        System.out.println(num);
    }
}
```

### Python

```python
input()
```

### Java

```java
sc.nextInt()
sc.nextDouble()
sc.next()
sc.nextLine()
```

---

# 6. Python `print()` → Java `System.out.println()`

Python:

```python
print("Hello")
```

Java:

```java
System.out.println("Hello");
```

Without a new line:

```java
System.out.print("Hello");
```

---

# 7. Problem 1 — Display -10 to -1

### Python

```python
for i in range(-10, 0):
    print(i)
```

### Java

```java
for (int i = -10; i <= -1; i++) {
    System.out.println(i);
}
```

### Trace

```text
i = -10
 ↓
-10 <= -1 → true
 ↓
print -10
 ↓
i++
 ↓
-9
 ↓
...
 ↓
-1
 ↓
i becomes 0
 ↓
0 <= -1 → false
 ↓
stop
```

---

# 8. Problem 2 — Print `Done` After Loop

### Java

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

System.out.println("Done");
```

### Output

```text
0
1
2
3
4
Done
```

The position of the statement matters.

```java
for (...) {
    ...
}

System.out.println("Done");
```

`Done` is outside the loop.

---

# 9. Problem 3 — Multiplication Table

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int num = sc.nextInt();

        for (int i = 1; i <= 10; i++) {
            System.out.println(num + " x " + i + " = " + (num * i));
        }
    }
}
```

### Input

```text
5
```

### Trace

```text
i = 1 → 5 × 1 = 5
i = 2 → 5 × 2 = 10
i = 3 → 5 × 3 = 15
...
i = 10 → 5 × 10 = 50
```

---

# 10. Problem 4 — Cube of Every Number

### Python

```python
cube = i ** 3
```

### Java

Java does not use Python's `**` operator.

For integer powers, simply use multiplication:

```java
int cube = i * i * i;
```

### Java Code

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        for (int i = 1; i <= n; i++) {

            int cube = i * i * i;

            System.out.println(
                "Current Number is : " + i +
                " and the cube is " + cube
            );
        }
    }
}
```

### Important Python → Java

```text
Python          Java
------------------------------
i ** 3          i * i * i
```

For general powers Java can use:

```java
Math.pow(a, b)
```

but it returns a `double`.

---

# 11. Problem 5 — Odd Index Positions

Python:

```python
numbers = [10, 20, 30, 40, 50, 60]

for i in range(1, len(numbers), 2):
    print(numbers[i])
```

Java arrays:

```java
int[] numbers = {10, 20, 30, 40, 50, 60};

for (int i = 1; i < numbers.length; i += 2) {
    System.out.println(numbers[i]);
}
```

### Trace

```text
Index:   0   1   2   3   4   5
Value:  10  20  30  40  50  60
             ↑       ↑       ↑
             1       3       5
```

Output:

```text
20
40
60
```

### Python → Java

```text
len(numbers)
       ↓
numbers.length
```

and:

```text
range(1, len(numbers), 2)
       ↓
i = 1
i < numbers.length
i += 2
```

---

# 12. Problem 6 — Multiplication Table

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        for (int i = 1; i <= 10; i++) {
            System.out.println(n + " x " + i + " = " + (n * i));
        }
    }
}
```

---

# 13. Problem 7 — Sum of Natural Numbers

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int total = 0;

        for (int i = 1; i <= n; i++) {
            total = total + i;
        }

        System.out.println("Sum = " + total);
    }
}
```

### Trace for `n = 5`

```text
total = 0

i = 1
total = 0 + 1
      = 1

i = 2
total = 1 + 2
      = 3

i = 3
total = 3 + 3
      = 6

i = 4
total = 6 + 4
      = 10

i = 5
total = 10 + 5
      = 15
```

This is the **accumulator pattern**.

```java
int total = 0;

for (...) {
    total += value;
}
```

---

# 14. Problem 8 — FizzBuzz

### Java

```java
public class Main {

    public static void main(String[] args) {

        for (int i = 1; i <= 50; i++) {

            if (i % 3 == 0 && i % 5 == 0) {
                System.out.println("FizzBuzz");
            }
            else if (i % 3 == 0) {
                System.out.println("Fizz");
            }
            else if (i % 5 == 0) {
                System.out.println("Buzz");
            }
            else {
                System.out.println(i);
            }
        }
    }
}
```

### Why check FizzBuzz first?

For `15`:

```text
15 % 3 == 0 → true
15 % 5 == 0 → true
```

Therefore:

```text
FizzBuzz
```

If we checked `i % 3 == 0` first, `15` would become only:

```text
Fizz
```

---

# 15. Problem 9 — Reverse Array

Python:

```python
for i in range(len(numbers) - 1, -1, -1):
    print(numbers[i])
```

Java:

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int i = numbers.length - 1; i >= 0; i--) {
    System.out.println(numbers[i]);
}
```

### Trace

```text
numbers.length = 5

starting index:
5 - 1 = 4
```

Then:

```text
i = 4 → 50
i = 3 → 40
i = 2 → 30
i = 1 → 20
i = 0 → 10
```

---

# 16. Problem 10 — Odd or Even

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int num = sc.nextInt();

        if (num % 2 == 0) {
            System.out.println("Even");
        }
        else {
            System.out.println("Odd");
        }
    }
}
```

### Core technique

```java
num % 2 == 0
```

means:

```text
number divided by 2 has remainder 0
```

Therefore the number is even.

---

# 17. Problem 11 — Even or Odd

Same technique:

```java
if (n % 2 == 0) {
    System.out.println("Even");
}
else {
    System.out.println("Odd");
}
```

---

# 18. Problem 12 — Positive / Negative / Zero

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int num = sc.nextInt();

        if (num > 0) {
            System.out.println("Positive");
        }
        else if (num < 0) {
            System.out.println("Negative");
        }
        else {
            System.out.println("Zero");
        }
    }
}
```

### Trace

For:

```text
num = -5
```

```text
-5 > 0
 ↓
false

-5 < 0
 ↓
true

Negative
```

---

# 19. Problem 13 — Greatest of Three Numbers

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();
        int c = sc.nextInt();

        if (a >= b && a >= c) {
            System.out.println(a);
        }
        else if (b >= a && b >= c) {
            System.out.println(b);
        }
        else {
            System.out.println(c);
        }
    }
}
```

### Techniques

```text
comparison
+
logical AND
+
if / else if / else
```

---

# 20. Problem 14 — Leap Year

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int year = sc.nextInt();

        if (year % 400 == 0) {
            System.out.println("Leap Year");
        }
        else if (year % 100 == 0) {
            System.out.println("Not a Leap Year");
        }
        else if (year % 4 == 0) {
            System.out.println("Leap Year");
        }
        else {
            System.out.println("Not a Leap Year");
        }
    }
}
```

### Examples

```text
2024 → Leap Year
2000 → Leap Year
1900 → Not a Leap Year
2023 → Not a Leap Year
```

---

# 21. Problem 15 — Print 1 to N Without Loop

Python uses recursion:

```python
def print_numbers(n):

    if n == 0:
        return

    print_numbers(n - 1)
    print(n)
```

Java equivalent:

```java
import java.util.Scanner;

public class Main {

    static void printNumbers(int n) {

        if (n == 0) {
            return;
        }

        printNumbers(n - 1);

        System.out.println(n);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        printNumbers(n);
    }
}
```

### Trace for `n = 3`

Calls:

```text
printNumbers(3)
    ↓
printNumbers(2)
    ↓
printNumbers(1)
    ↓
printNumbers(0)
    ↓
return
```

Returning:

```text
print 1
print 2
print 3
```

Output:

```text
1
2
3
```

---

# 22. Problem 16 — Print N to 1 Without Loop

```java
import java.util.Scanner;

public class Main {

    static void printNumbers(int n) {

        if (n == 0) {
            return;
        }

        System.out.println(n);

        printNumbers(n - 1);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        printNumbers(n);
    }
}
```

### Trace

For `n = 3`:

```text
print 3
 ↓
printNumbers(2)

print 2
 ↓
printNumbers(1)

print 1
 ↓
printNumbers(0)

return
```

---

# 23. Problem 17 — Multiplication Table

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        for (int i = 1; i <= 10; i++) {
            System.out.println(n * i);
        }
    }
}
```

---

# 24. Problem 18 — Reverse Coding / Digit Extraction

A very important DSA technique:

```java
digit = n % 10;
n = n / 10;
```

Example:

```text
n = 1234
```

### Iteration 1

```text
1234 % 10 = 4
1234 / 10 = 123
```

### Iteration 2

```text
123 % 10 = 3
123 / 10 = 12
```

### Iteration 3

```text
12 % 10 = 2
12 / 10 = 1
```

### Iteration 4

```text
1 % 10 = 1
1 / 10 = 0
```

Digits:

```text
4 3 2 1
```

### Java Example

```java
int n = 1234;

while (n > 0) {

    int digit = n % 10;

    System.out.println(digit);

    n = n / 10;
}
```

---

# 25. Problem 19 — Calculator

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();

        char operator = sc.next().charAt(0);

        if (operator == '+') {
            System.out.println(a + b);
        }
        else if (operator == '-') {
            System.out.println(a - b);
        }
        else if (operator == '*') {
            System.out.println(a * b);
        }
        else if (operator == '/') {
            System.out.println(a / b);
        }
        else {
            System.out.println("Invalid operator");
        }
    }
}
```

### Important Java Concept

Python:

```python
operator = input()
```

Java:

```java
char operator = sc.next().charAt(0);
```

`next()` gets a String.

`charAt(0)` gets its first character.

---

# 26. Problem 20 — Taking Input

### Integer

```java
int n = sc.nextInt();
```

### Double

```java
double n = sc.nextDouble();
```

### String without spaces

```java
String name = sc.next();
```

### Complete line

```java
String line = sc.nextLine();
```

### Important Difference

```java
next()
```

reads one token.

Example:

```text
Hello
```

`nextLine()` reads the complete line.

Example:

```text
Hello Daya
```

---

# 27. Multiple Inputs

Input:

```text
10 20
```

Java:

```java
Scanner sc = new Scanner(System.in);

int a = sc.nextInt();
int b = sc.nextInt();
```

Trace:

```text
Input
 ↓
10 20
 ↓
nextInt() → 10
nextInt() → 20
```

---

# 28. Multiple Lines

Input:

```text
10
20
30
```

Java:

```java
int a = sc.nextInt();
int b = sc.nextInt();
int c = sc.nextInt();
```

The scanner reads whitespace-separated values.

---

# 29. Problem — Swap Two Numbers

Python:

```python
a, b = b, a
```

Python uses:

> Multiple assignment / tuple unpacking

Java does not have this syntax.

Java normally uses a temporary variable.

```java
int a = 10;
int b = 20;

int temp = a;
a = b;
b = temp;
```

### Trace

Initial:

```text
a = 10
b = 20
```

Step 1:

```text
temp = a
temp = 10
```

Step 2:

```text
a = b
a = 20
```

Step 3:

```text
b = temp
b = 10
```

Final:

```text
a = 20
b = 10
```

### Java Technique

```text
temporary variable
```

This is the standard beginner-friendly swapping technique.

---

# 30. Python → Java Cheat Sheet

| Python | Java |
|---|---|
| `x = 10` | `int x = 10;` |
| `input()` | `Scanner` methods |
| `int(input())` | `sc.nextInt()` |
| `float(input())` | `sc.nextDouble()` |
| `print()` | `System.out.println()` |
| `if` | `if` |
| `elif` | `else if` |
| `else` | `else` |
| `and` | `&&` |
| `or` | `||` |
| `not` | `!` |
| `range()` | `for` initialization/condition/update |
| `len(list)` | `array.length` |
| `list[index]` | `array[index]` |
| `**` | multiplication / `Math.pow()` |
| `%` | `%` |
| `//` | integer division with integer operands |
| `+=` | `+=` |
| `-=` | `-=` |
| `i += 2` | `i += 2` |
| `i -= 1` | `i--` |
| `True` | `true` |
| `False` | `false` |
| `None` | `null` |
| `def` | method declaration |
| recursion | recursion |
| list | `ArrayList` / array |
| tuple unpacking | temporary variable / other explicit techniques |

---

# 31. Python `range()` vs Java `for`

This is one of the most important concepts from this lesson.

### Python

```python
for i in range(1, 11):
    print(i)
```

Think:

```text
start = 1
stop = 11
step = 1
```

Generated values:

```text
1 2 3 4 5 6 7 8 9 10
```

### Java

```java
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
```

Think:

```text
initialization → int i = 1
condition      → i <= 10
update         → i++
```

### Direct Mental Conversion

Whenever you see:

```python
range(start, stop, step)
```

think:

```java
for (int i = start; i < stop; i += step)
```

For example:

```python
range(1, 10, 2)
```

becomes approximately:

```java
for (int i = 1; i < 10; i += 2)
```

---

# 32. Python Reverse `range()` vs Java

Python:

```python
range(10, 0, -1)
```

Java:

```java
for (int i = 10; i > 0; i--) {
    System.out.println(i);
}
```

Mental conversion:

```text
Python
range(start, stop, -1)

Java
i = start
i > stop
i--
```

---

# 33. Python List vs Java Array

### Python

```python
numbers = [10, 20, 30, 40]
```

Python lists are dynamic.

You can do:

```python
numbers.append(50)
```

### Java Array

```java
int[] numbers = {10, 20, 30, 40};
```

Java arrays have fixed size.

```java
numbers[0]
numbers[1]
```

### Java Dynamic Collection

For a Python-list-like dynamic structure, Java commonly uses:

```java
ArrayList<Integer>
```

Example:

```java
import java.util.ArrayList;

ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

---

# 34. Python `len()` vs Java `.length`

Python:

```python
len(numbers)
```

Java array:

```java
numbers.length
```

Important:

```java
numbers.length
```

is a property.

For `ArrayList`:

```java
numbers.size()
```

So:

```text
Python list       → len(list)
Java array        → array.length
Java ArrayList    → list.size()
```

---

# 35. Python `and` vs Java `&&`

Python:

```python
if age >= 18 and age <= 60:
    print("Valid")
```

Java:

```java
if (age >= 18 && age <= 60) {
    System.out.println("Valid");
}
```

### Mapping

```text
Python       Java

and    →     &&
or     →     ||
not    →     !
```

---

# 36. Python Indentation vs Java Braces

Python:

```python
if x > 0:
    print("Positive")
    print("Valid")
```

Indentation defines the block.

Java:

```java
if (x > 0) {
    System.out.println("Positive");
    System.out.println("Valid");
}
```

Braces define the block.

```text
Python → indentation
Java   → { }
```

---

# 37. Python `def` vs Java Method

Python:

```python
def add(a, b):
    return a + b
```

Java:

```java
static int add(int a, int b) {
    return a + b;
}
```

Java requires:

```text
return type
method name
parameters with types
```

---

# 38. Core Java Techniques Learned

## Technique 1 — Traditional `for` Loop

```java
for (int i = 1; i <= n; i++) {
    // logic
}
```

---

## Technique 2 — Reverse Loop

```java
for (int i = n; i >= 1; i--) {
    // logic
}
```

---

## Technique 3 — Accumulator

```java
int total = 0;

for (int i = 1; i <= n; i++) {
    total += i;
}
```

---

## Technique 4 — Conditional Decision

```java
if (condition) {
    
}
else if (condition) {
    
}
else {
    
}
```

---

## Technique 5 — Modulo

```java
n % 2
```

Used for:

```text
even / odd
divisibility
FizzBuzz
digit extraction
leap year
```

---

## Technique 6 — Array Indexing

```java
numbers[i]
```

---

## Technique 7 — Array Traversal

```java
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

---

## Technique 8 — Recursion

```java
static void solve(int n) {

    if (n == 0) {
        return;
    }

    solve(n - 1);
}
```

---

## Technique 9 — Temporary Variable

Used for swapping:

```java
int temp = a;
a = b;
b = temp;
```

---

# 39. Complete Concept Map

```text
Conditional Statements
│
├── if
├── else if
├── else
├── comparison operators
│   ├── >
│   ├── <
│   ├── >=
│   ├── <=
│   ├── ==
│   └── !=
│
└── logical operators
    ├── &&
    ├── ||
    └── !

Loops
│
└── for
    │
    ├── forward loop
    ├── reverse loop
    ├── counting
    ├── accumulation
    └── array traversal

Operators
│
├── arithmetic
│   ├── +
│   ├── -
│   ├── *
│   ├── /
│   └── %
│
└── assignment
    ├── =
    ├── +=
    ├── -=
    └── *=

Arrays
│
├── indexing
├── traversal
├── length
└── reverse traversal

Functions / Methods
│
├── parameters
├── return
├── recursion
└── base case

Input / Output
│
├── Scanner
├── nextInt()
├── nextDouble()
├── next()
├── nextLine()
└── System.out.println()
```

---

# 40. Most Important Mental Models

Do not memorize 20 separate programs.

Understand these patterns.

### Pattern 1 — Counting

```java
for (int i = 1; i <= n; i++) {
    
}
```

### Pattern 2 — Reverse Counting

```java
for (int i = n; i >= 1; i--) {
    
}
```

### Pattern 3 — Accumulation

```java
int result = 0;

for (int i = 1; i <= n; i++) {
    result += i;
}
```

### Pattern 4 — Condition

```java
if (condition) {
    
}
else {
    
}
```

### Pattern 5 — Divisibility

```java
if (n % k == 0) {
    
}
```

### Pattern 6 — Array Traversal

```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

### Pattern 7 — Recursion

```java
static void solve(int n) {

    if (baseCase) {
        return;
    }

    solve(smallerProblem);
}
```

---

# 41. Final Python → Java Mental Conversion

When you see this Python:

```python
for i in range(1, n + 1):

    if i % 2 == 0:
        total += i
```

Think in Java:

```java
for (int i = 1; i <= n; i++) {

    if (i % 2 == 0) {
        total += i;
    }
}
```

The **algorithm has not changed**.

Only the language syntax has changed.

This is the most important thing to understand.

```text
Python code
     ↓
Understand algorithm
     ↓
Identify variables
     ↓
Identify condition
     ↓
Identify loop
     ↓
Identify data structure
     ↓
Write same logic in Java
```

That is how you should learn Python and Java together for DSA.
