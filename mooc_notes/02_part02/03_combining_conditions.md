# Combining Conditions

## Logical Operators

You can combine conditions with the logical operators and and or. The operator and specifies that all the given conditions must be true at the same time. The operator or specifies that at least one of the given conditions must be true.

For example, the condition number >= 5 and number <= 8 determines that number must simultaneously be at least 5 and at most 8. That is, it must be between 5 and 8.

```py
number = int(input("Please type in a number: "))
if number >= 5 and number <= 8:
    print("The number is between 5 and 8")
```

Meanwhile, the condition number < 5 or number > 8 determines that number must be either less than
5 or greater than 8. That is, it must not be within the range of 5 to 8.

```py
number = int(input("Please type in a number: "))
if number < 5 or number > 8:
    print("The number is not within the range of 5 to 8")
```

The following truth table contains the behaviour of these operators in different situations:

| a     | b     | a and b | a or b |
|-------|-------|---------|--------|
| False | False | False   | False  |
| True  | False | False   | True   |
| False | True  | False   | True   |
| True  | True  | True    | True   |

Sometimes it is necessary to know if something is not true. The operator not negates a condition:

| a     | not a |
|-------|-------|
| True  | False |
| False | True  |

The above example with the range of 5 to 8 excluded could also be programmed like this:

```py
number = int(input("Please type in a number: "))
if not (number >= 5 and number <= 8):
    print("The number is not within the range of 5 to 8")
```

Especially in programming, logical operators are often called Boolean operators.

## Combining and chaining conditions

The following program asks the user to type in four numbers. It then works out which of the four is the greatest, with the help of some conditions:

```py
n1 = int(input("Number 1: "))
n2 = int(input("Number 2: "))
n3 = int(input("Number 3: "))
n4 = int(input("Number 4: "))

if n1 > n2 and n1 > n3 and n1 > n4:
    greatest = n1
elif n2 > n3 and n2 > n4:
    greatest = n2
elif n3 > n4:
    greatest = n3
else:
    greatest = n4

print(f" {greatest} is the greatest of the numbers.")
```

In the above example the first condition n1 > n2 and n1 > n3 and n1 > n4 is true only if all three conditions within are true.

## Nested Conditionals

Conditional statements can also be nested within other conditional statements. For example, the following program checks whether a number is above zero, and then whether it is odd or even:

```py
number = int(input("Please type in a number: "))

if number > 0:
    if number % 2 == 0:
        print("The number is even")
    else:
        print("The number is odd")
else:
    print("The number is negative or zero")
```

Some examples of how this program behaves:

```
Please type in a number: >> 3
The number is odd

Please type in a number: >> 18
The number is even

Please type in a number: >> -4
The number is negative or zero
```

With nested conditional statements it is crucial to get the indentations right. Indentations determine which branches are linked together. For example, an if branch and an else branch with the same amount of whitespace are determined to be branches of the same conditional statement.

The same result can often be achieved using either nested conditional statements or conditions combined with logical operators. The example below is functionally no different from the example above, in the sense that it will print out the exactly same things with the same inputs:


```py
number = int(input("Please type in a number: "))

if number > 0 and number % 2 == 0:
    print("The number is even")
elif number > 0 and number % 2 != 0:
    print("The number is odd")
else:
    print("The number is negative or zero")
```

Neither approach is intrinsically better than the other, but in different situations one or the other may seem more logical. In this particular example most people tend to find the first version with nesting to be more intuitive.