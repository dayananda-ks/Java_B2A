# Java — Loops

## Python → Java

This README implements the same loop concepts using Java.

The focus is understanding **what Java uses instead of Python's techniques**.

---

# 1. Python `while` → Java `while`

### Python

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

### Java

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

### Java Syntax

```java
while (condition) {
    // logic
}
```

The algorithm is identical.

Only the syntax changes.

---

# 2. `while` Loop Trace

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

Trace:

```text
i = 1

1 <= 5 → true
print 1
i++

2 <= 5 → true
print 2
i++

...

5 <= 5 → true
print 5
i++

6 <= 5 → false
stop
```

---

# 3. Java `break`

Python:

```python
if num == 0:
    break
```

Java:

```java
if (num == 0) {
    break;
}
```

`break` behaves almost identically.

It immediately terminates the nearest loop.

---

# 4. Java `continue`

Python:

```python
if num < 0:
    continue
```

Java:

```java
if (num < 0) {
    continue;
}
```

It skips the current iteration.

---

# 5. `break` vs `continue`

```text
break
 ↓
exit loop completely

continue
 ↓
skip current iteration
 ↓
next iteration
```

---

# 6. Java Input

Java commonly uses `Scanner`.

```java
import java.util.Scanner;
```

Create scanner:

```java
Scanner sc = new Scanner(System.in);
```

Integer:

```java
int num = sc.nextInt();
```

Double:

```java
double value = sc.nextDouble();
```

String:

```java
String name = sc.next();
```

Complete line:

```java
String name = sc.nextLine();
```

---

# 7. Problem 1 — While Loop

```java
public class Main {

    public static void main(String[] args) {

        int i = 1;

        while (i <= 5) {

            System.out.println(i);

            i++;
        }
    }
}
```

Output:

```text
1
2
3
4
5
```

---

# 8. Problem 2 — Skip Negative, Stop at Zero

Python:

```python
for num in numbers:

    if num < 0:
        continue

    if num == 0:
        break

    print(num)
```

Java:

```java
public class Main {

    public static void main(String[] args) {

        int[] numbers = {10, -5, 20, -3, 30, 0, 40};

        for (int num : numbers) {

            if (num < 0) {
                continue;
            }

            if (num == 0) {
                break;
            }

            System.out.println(num);
        }
    }
}
```

### Java Technique Used

```java
for (int num : numbers)
```

is Java's **enhanced `for` loop**, also called the **for-each loop**.

It is useful when we want each element but don't need the index.

### Trace

```text
10  → print
-5  → continue
20  → print
-3  → continue
30  → print
0   → break
40  → never processed
```

Output:

```text
10
20
30
```

---

# 9. Problem 3 — Keep Asking Until Negative

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int total = 0;

        while (true) {

            int num = sc.nextInt();

            if (num < 0) {
                break;
            }

            total += num;
        }

        System.out.println("Sum = " + total);
    }
}
```

### Example

Input:

```text
10
20
30
-5
```

Trace:

```text
total = 0

10 → total = 10
20 → total = 30
30 → total = 60
-5 → break
```

Output:

```text
Sum = 60
```

### Pattern

```java
while (true) {

    input;

    if (stopCondition) {
        break;
    }

    process;
}
```

This is a **sentinel-controlled loop**.

---

# 10. Problem 4 — Ask for Name Until `END`

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        while (true) {

            String name = sc.next();

            if (name.equals("END")) {
                break;
            }

            System.out.println(name);
        }

        System.out.println("I am done.");
    }
}
```

### Important Java Difference

Do not normally compare Java strings using:

```java
name == "END"
```

Use:

```java
name.equals("END")
```

because `String` is an object and `.equals()` checks the string contents.

---

# 11. Problem 5 — Test Average

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        double total = 0;
        int count = 0;

        while (true) {

            double grade = sc.nextDouble();

            if (grade < 0) {
                break;
            }

            total += grade;
            count++;
        }

        if (count > 0) {

            double average = total / count;

            System.out.println("Average = " + average);

            if (average >= 90) {
                System.out.println("A");
            }
            else if (average >= 80) {
                System.out.println("B");
            }
            else if (average >= 70) {
                System.out.println("C");
            }
            else if (average >= 60) {
                System.out.println("D");
            }
            else {
                System.out.println("F");
            }

        }
        else {
            System.out.println("No grades entered.");
        }
    }
}
```

### Example

Input:

```text
90
80
70
-1
```

Trace:

```text
total = 0
count = 0

90 → total = 90, count = 1
80 → total = 170, count = 2
70 → total = 240, count = 3
-1 → break
```

Average:

```text
240 / 3 = 80
```

Grade:

```text
B
```

---

# 12. Problem 6 — Series

Series:

```text
105 98 91 ... 7
```

Difference:

```text
-7
```

### Java

```java
public class Main {

    public static void main(String[] args) {

        int i = 105;

        while (i >= 7) {

            System.out.println(i);

            i -= 7;
        }
    }
}
```

### Trace

```text
105
 ↓ -7
98
 ↓ -7
91
 ↓ -7
84
 ↓
...
 ↓
7
 ↓ -7
0
```

At `0`:

```text
0 >= 7 → false
```

Loop stops.

---

# 13. Problem 7 — Difference of Odd and Even Sums

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int oddSum = 0;
        int evenSum = 0;

        int i = 1;

        while (i <= n) {

            oddSum += 2 * i - 1;

            evenSum += 2 * i;

            i++;
        }

        int difference = oddSum - evenSum;

        System.out.println("Difference = " + difference);
    }
}
```

For:

```text
n = 3
```

```text
Odd:
1 + 3 + 5 = 9

Even:
2 + 4 + 6 = 12

Difference:
9 - 12 = -3
```

---

# 14. Problem 8 — Numbers Between Range

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int start = sc.nextInt();
        int end = sc.nextInt();

        while (start <= end) {

            System.out.println(start);

            start++;
        }
    }
}
```

Input:

```text
5 10
```

Output:

```text
5
6
7
8
9
10
```

---

# 15. Problem 9 — Sum Until Zero

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int total = 0;

        while (true) {

            int num = sc.nextInt();

            if (num == 0) {
                break;
            }

            total += num;
        }

        System.out.println("Sum = " + total);
    }
}
```

### Pattern

```text
0 = sentinel
```

The loop continues until:

```java
num == 0
```

---

# 16. Problem 10 — Count Positive and Negative

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int positiveCount = 0;
        int negativeCount = 0;

        while (true) {

            int num = sc.nextInt();

            if (num == 0) {
                break;
            }

            if (num > 0) {
                positiveCount++;
            }
            else {
                negativeCount++;
            }
        }

        System.out.println("Positive numbers = " + positiveCount);
        System.out.println("Negative numbers = " + negativeCount);
    }
}
```

### Example

Input:

```text
10
-5
20
-3
7
0
```

Trace:

```text
10  → positive = 1
-5  → negative = 1
20  → positive = 2
-3  → negative = 2
7   → positive = 3
0   → stop
```

Output:

```text
Positive numbers = 3
Negative numbers = 2
```

---

# 17. Problem 11 — Largest and Smallest

Java does not have Python's:

```python
largest = None
```

Instead, a simple technique is to initialize the first input as both largest and smallest.

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int num = sc.nextInt();

        int largest = num;
        int smallest = num;

        int i = 1;

        while (i < n) {

            num = sc.nextInt();

            if (num > largest) {
                largest = num;
            }

            if (num < smallest) {
                smallest = num;
            }

            i++;
        }

        System.out.println("Largest = " + largest);
        System.out.println("Smallest = " + smallest);
    }
}
```

### Example

```text
5
10
25
3
40
15
```

Trace:

```text
Initial:
largest = 10
smallest = 10

25 → largest = 25
3  → smallest = 3
40 → largest = 40
15 → no change
```

Final:

```text
Largest = 40
Smallest = 3
```

---

# 18. Problem 12 — `2 22 222...`

### Java

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int value = 0;

        int i = 1;

        while (i <= n) {

            value = value * 10 + 2;

            System.out.println(value);

            i++;
        }
    }
}
```

### Trace

```text
value = 0

0 × 10 + 2 = 2
2 × 10 + 2 = 22
22 × 10 + 2 = 222
222 × 10 + 2 = 2222
```

---

# 19. Problem 13 — Natural Even Numbers Starting From N

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int count = sc.nextInt();

        if (n % 2 != 0) {
            n++;
        }

        int i = 0;

        while (i < count) {

            System.out.println(n);

            n += 2;

            i++;
        }
    }
}
```

Example:

```text
n = 5
count = 5
```

First even number:

```text
6
```

Output:

```text
6
8
10
12
14
```

---

# 20. Problem 14 — Swap Without Third Variable

One arithmetic technique:

```java
int a = 10;
int b = 20;

a = a + b;
b = a - b;
a = a - b;
```

### Trace

Initial:

```text
a = 10
b = 20
```

After:

```java
a = a + b;
```

```text
a = 30
b = 20
```

After:

```java
b = a - b;
```

```text
a = 30
b = 10
```

After:

```java
a = a - b;
```

```text
a = 20
b = 10
```

Swapped.

### Important

For production Java code, this arithmetic trick is generally less readable than a temporary variable. It can also overflow for large integers.

---

# 21. Problem 15 — Password With 3 Attempts

Python:

```python
while attempts < 3:
```

Java:

```java
while (attempts < 3) {
```

### Complete Java Code

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String currPassword = "python123";

        int attempts = 0;

        boolean correct = false;

        while (attempts < 3) {

            System.out.print("Enter password: ");

            String password = sc.next();

            if (password.equals(currPassword)) {

                System.out.println("Password correct. Access granted.");

                correct = true;

                break;
            }

            attempts++;

            System.out.println("Wrong password.");
        }

        if (!correct) {
            System.out.println("Account locked.");
        }
    }
}
```

---

# 22. Password Trace — Correct

Suppose:

```text
currPassword = python123
```

Input:

```text
python123
```

Comparison:

```java
password.equals(currPassword)
```

Result:

```text
true
```

Then:

```text
Access granted
   ↓
correct = true
   ↓
break
   ↓
loop ends
```

Since:

```text
correct = true
```

we do not print:

```text
Account locked
```

---

# 23. Password Trace — Three Wrong Attempts

Input:

```text
abc
xyz
hello
```

Initial:

```text
attempts = 0
```

First:

```text
abc
 ↓
wrong
 ↓
attempts = 1
```

Second:

```text
xyz
 ↓
wrong
 ↓
attempts = 2
```

Third:

```text
hello
 ↓
wrong
 ↓
attempts = 3
```

Condition:

```java
attempts < 3
```

becomes:

```text
3 < 3
 ↓
false
```

Loop ends.

```text
correct = false
```

Therefore:

```text
Account locked.
```

---

# 24. Python `while...else` → Java Technique

Python has:

```python
while condition:
    ...
else:
    ...
```

Java does **not** have `while...else`.

Python:

```python
while attempts < 3:

    if correct:
        break

else:
    print("Locked")
```

Java can use a boolean flag:

```java
boolean correct = false;

while (attempts < 3) {

    if (password.equals(currPassword)) {

        correct = true;

        break;
    }

    attempts++;
}

if (!correct) {
    System.out.println("Account locked.");
}
```

### Technique

```text
Python
while...else

        ↓

Java
boolean flag
+
break
+
if
```

This is an important Python → Java conversion.

---

# 25. Python `for` → Java `for`

Python:

```python
for i in range(1, 10):
    print(i)
```

Java:

```java
for (int i = 1; i < 10; i++) {
    System.out.println(i);
}
```

---

# 26. Python `while True` → Java `while (true)`

Python:

```python
while True:
```

Java:

```java
while (true) {
```

Both create an intentional infinite loop.

Usually you then use:

```text
break
```

to terminate it.

---

# 27. Python `continue` → Java `continue`

Python:

```python
if num < 0:
    continue
```

Java:

```java
if (num < 0) {
    continue;
}
```

Same algorithm.

---

# 28. Python `break` → Java `break`

Python:

```python
if num == 0:
    break
```

Java:

```java
if (num == 0) {
    break;
}
```

Same behavior.

---

# 29. Python `+=` → Java `+=`

Python:

```python
total += num
```

Java:

```java
total += num;
```

Equivalent to:

```java
total = total + num;
```

---

# 30. Python Counter → Java Counter

Python:

```python
count = 0

count += 1
```

Java:

```java
int count = 0;

count++;
```

Both mean:

```text
increase by 1
```

Java also supports:

```java
count += 1;
```

---

# 31. Python `None` → Java `null`

Python:

```python
largest = None
```

Java reference types can use:

```java
Integer largest = null;
```

But for this problem, a better Java technique is:

```java
int first = sc.nextInt();

int largest = first;
int smallest = first;
```

This avoids unnecessary `null` handling.

---

# 32. Python String Comparison → Java

Python:

```python
if name == "END":
```

Java:

```java
if (name.equals("END")) {
```

Important:

```java
name == "END"
```

should not be used for normal content comparison.

Use:

```java
name.equals("END")
```

---

# 33. Python List → Java Array

Python:

```python
numbers = [10, 20, 30]
```

Java:

```java
int[] numbers = {10, 20, 30};
```

Python:

```python
len(numbers)
```

Java:

```java
numbers.length
```

---

# 34. Python List Loop → Java Enhanced For

Python:

```python
for num in numbers:
    print(num)
```

Java:

```java
for (int num : numbers) {
    System.out.println(num);
}
```

This is called:

> Enhanced `for` loop / for-each loop.

Use it when you need the elements but don't need the index.

---

# 35. Core Loop Patterns

## Pattern 1 — Condition-Controlled Loop

```java
int i = 1;

while (i <= n) {

    // logic

    i++;
}
```

---

## Pattern 2 — Sentinel-Controlled Loop

```java
while (true) {

    int num = sc.nextInt();

    if (num == 0) {
        break;
    }

    // process
}
```

---

## Pattern 3 — Accumulator

```java
int total = 0;

while (condition) {

    total += value;
}
```

---

## Pattern 4 — Counter

```java
int count = 0;

while (condition) {

    if (someCondition) {
        count++;
    }
}
```

---

## Pattern 5 — Maximum

```java
if (num > largest) {
    largest = num;
}
```

---

## Pattern 6 — Minimum

```java
if (num < smallest) {
    smallest = num;
}
```

---

## Pattern 7 — Skip

```java
if (condition) {
    continue;
}
```

---

## Pattern 8 — Stop

```java
if (condition) {
    break;
}
```

---

# 36. Loop Problem-Solving Framework

Whenever you receive a `while` loop problem, think:

```text
             PROBLEM
                ↓
       What should I initialize?
                ↓
       What keeps loop running?
                ↓
          What is input?
                ↓
       What is stop condition?
                ↓
        What is the processing?
                ↓
       What changes each iteration?
                ↓
             OUTPUT
```

---

# 37. Example — Convert English to Code

Problem:

> Keep accepting numbers until zero and calculate their sum.

### Step 1 — Identify accumulator

```java
int total = 0;
```

### Step 2 — Need repeated input

```java
while (true) {
```

### Step 3 — Read number

```java
int num = sc.nextInt();
```

### Step 4 — Identify stop condition

```java
if (num == 0) {
    break;
}
```

### Step 5 — Process

```java
total += num;
```

### Final

```java
int total = 0;

while (true) {

    int num = sc.nextInt();

    if (num == 0) {
        break;
    }

    total += num;
}

System.out.println(total);
```

This conversion process is more important than memorizing the final code.

---

# 38. Complete Concept Map

```text
LOOPS
│
├── for
│   ├── traditional for
│   └── enhanced for
│
└── while
    │
    ├── condition controlled
    ├── sentinel controlled
    ├── infinite + break
    │
    ├── break
    │   └── terminate loop
    │
    └── continue
        └── skip iteration


PROBLEM-SOLVING PATTERNS
│
├── Accumulator
│   └── total += value
│
├── Counter
│   └── count++
│
├── Maximum
│   └── largest
│
├── Minimum
│   └── smallest
│
├── Sentinel
│   └── stop value
│
└── Series
    └── previous → next
```

---

# 39. Python → Java Quick Reference

| Python | Java |
|---|---|
| `while condition:` | `while (condition) {}` |
| `while True:` | `while (true) {}` |
| `break` | `break;` |
| `continue` | `continue;` |
| `for i in range()` | traditional `for` |
| `for x in list` | enhanced `for` |
| `print()` | `System.out.println()` |
| `input()` | `Scanner` |
| `int(input())` | `sc.nextInt()` |
| `float(input())` | `sc.nextDouble()` |
| `input()` string | `sc.next()` |
| `len(array)` | `array.length` |
| `None` | `null` |
| `elif` | `else if` |
| `and` | `&&` |
| `or` | `||` |
| `not` | `!` |
| `True` | `true` |
| `False` | `false` |
| `+= 1` | `++` |
| `def` | method |
| `while...else` | flag + `if` |

---

# 40. Final Mental Model

The syntax between Python and Java changes, but the **algorithmic thinking remains the same**.

For example:

### Python

```python
while True:

    n = int(input())

    if n == 0:
        break

    total += n
```

### Java

```java
while (true) {

    int n = sc.nextInt();

    if (n == 0) {
        break;
    }

    total += n;
}
```

The algorithm is:

```text
READ
 ↓
CHECK STOP CONDITION
 ↓
IF STOP → BREAK
 ↓
PROCESS
 ↓
READ AGAIN
```

That algorithm works regardless of whether you write it in Python, Java, C++, or another language.

The goal is therefore:

> **Learn the programming pattern first, then learn how Java expresses that pattern.**
