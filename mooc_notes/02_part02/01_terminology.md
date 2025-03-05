# Programming terminology

In the first part of this course we didn't pay much attention to terminology, so let's have a look at some central concepts in programming.

## Statement

A statement is a part of the program which executes something. It often, but not always, refers to a single command.

For example, print("Hi!") is a statement which prints out a line of text. Likewise, number = 2 is a statement which assigns a value to a variable.

A statement can also be more complicated. It can, for instance, contain other statements. The following statement spans three lines:

```py
if name == "Anna":
    print("Hi!")
    number = 2
```

In the above case there are two statements (a print statement and an assignment statement) within a conditional statement.

## Block

A block is a group of consecutive statements that are at the same level in the structure of the program. For example, the block of a conditional statement contains those statements which are executed only if the condition is true.

```py
if age > 17:
    # beginning of the conditional block
    print("You are of age!")
    age = age + 1
    print("You are now one year older...")
    # end of the conditional block

print("This here belongs to another block")
```

In Python blocks are expressed by indenting all code in the block by the same amount of whitespace.

NB: the main block of a Python program must always be at the leftmost edge of the file, without indentation:

```py
# this program will not work because it is not written at the leftmost egde of the file
  print("hello world")
  print("this program is not very good...")
```

## Expression

An expression is a bit of code that results in a determined data type. When the program is executed, the expression is evaluated so that it has a value that can then be used in the program.

All expressions have a type, they can be assigned to variables:

```py
# the variable x is assigned the value of the expression 1 + 2
x = 1 + 2
```

Simple expressions can be assembled together to form more complicated expressions, for example with arithmetic operations:

```py
# the variable y is assigned the value of the expression '3 times x plus x squared'
y = 3 * x + x**2
```

## Function

A function executes some functionality. Functions can also take one or more arguments, which are data that can be fed to and processed by the function. Arguments are sometimes also referred to as parameters. There is a technical distinction between an argument and a parameter, but the words are often used interchangeably. For now it should suffice to remember that both terms refer to the idea of some data passed to the function.

A function is executed when it is called. That is, when the function (and its arguments, if any) is mentioned in the code. The following statement calls the print function with the argument "this is an argument":

```py
print("this is an argument")
```

Another function you've already used often is the input function, which asks the user for input. The argument of this function is the message that is shown to the user:

```py
name = input("Please type in your name: ")
```

In this case the function also returns a value. After the function has been executed, the section of code where it was called is replaced by the value it returns; it is another expression that has now been evaluated. The function input returns a string value containing whatever the user typed in at the prompt. The value a function returns is often stored in a variable so that it can be used in the program later on.

## Data type

Data type refers to the characteristics of any value present in the program. In the following bit of code the data type of the variable name is string or str, and the data type of the variable result is integer or int:

```py
name = "Anna"
result = 100
```

You can use the function type to find out the data type of any expression. An example of its use:

```py
print(type("Anna"))
print(type(100))
```

```
Sample output
<class 'str'>
<class 'int'>
```

## Syntax

Similarly to natural languages, the syntax of a programming language determines how the code of a program should be written. Each programming language has its own specific syntax.

The syntax of Python specifies, among other things, that the first line of an if statement should end in a colon character, and the block of the statement should be indented:

```py
if name == "Anna":
    print("Hi!")
```

If the syntactic rules of the programming language are not followed, there will be an error:

```py
if name == "Anna"
    print("Hi!")
```

```
  File "test.py", line 1
    if name == "Anna"
                    ^
SyntaxError: invalid syntax
```

## Debugging

If the syntax of the program is correct but the program still doesn't function as intended, there is a bug in the program.

Bugs manifest in different ways. Some bugs cause an error during execution. For example, the following program

```py
x = 10
y = 0
result = x / y

print(f"{x} divided by {y} is {result}")
```

causes this error:

```
Sample output
ZeroDivisionError: integer division or modulo by zero on line 3
```

The problem here is mathematical in nature: division by zero is not allowed, and this halts the execution of the program.

Errors during execution are usually rather easy to fix, because the error message states the line of code causing the error. Of course the actual reason for the bug might be somewhere quite different than the line of code causing the error.

Sometimes a bug in the program is revealed because the result the code produces is wrong. Discovering and locating this type of bug can be challenging. In the programming exercises on this course the tests are usually intended to reveal bugs of this type. Before a bug can be fixed, its cause must first be located.

Programming jargon refers to discovering the causes of bugs as debugging. It is an extremely important skill in any programmer's toolbox. Professional programmers often spend more time debugging than writing fresh code.

A simple yet effective way of debugging a program is adding debugging print statements to your code. Verifying the results of your code with print commands gives a quick confirmation the code does what you want it to do.

The following is an attempt to solve one of the exercises from the previous section:

```py
hourly_wage = float(input("Hourly wage: "))
hours = int(input("Hours worked: "))
day = input("Day of the week: ")

daily_wages = hourly_wage * hours
if day == "sunday":
    daily_wages * 2

print(f"Daily wages: {daily_wages} euros")
```

The program doesn't work quite right. Executing the tests prints out the following:

```
FAIL: PythonEditorTest: test_sunday_1

With input 20.0,6,Sunday correct wage 240.0 is not found in output Daily wages: 120.0 euros
```

When debugging the exercises on this course, the first step is often checking how the program behaves with the input specified in the test that failed. Indeed the result isn't what was expected:

```
Daily wages: 120.0 euros
```

Debugging usually means running the program multiple times. It can come in handy to temporarily "hard-code" the problematic input, instead of asking the user for input each time. In this case hard-coding could look like this:

```py
# hourly_wage = float(input("Hourly wage: "))
# hours = int(input("Hours worked: "))
# day = input("Day of the week: ")
hourly_wage = 20.0
hours = 6
day = "Sunday"

daily_wages = hourly_wage * hours
if day == "sunday":
    daily_wages * 2

print(f"Daily wages: {daily_wages} euros")
```

The next step could be adding debugging print statements. The problematic part of the code is in the section dealing with Sundays, so let's add print commands before and after the line that should double the daily wages on Sundays:

```py
# ...

daily_wages = hourly_wage * hours
if day == "sunday":
    print("wages before:", daily_wages)
    daily_wages * 2
    print("wages after doubling:", daily_wages)

print(f"Daily wages: {daily_wages} euros")
```

Running the code now reveals nothing - the debugging print statements aren't printed at all. It seems that the contents of the if block are never executed, so there must be a problem with the conditional statement. Let's try printing out the value of the Boolean expression:

```py
daily_wages = hourly_wage * hours
print("condition:", day == "sunday")
if day == "sunday":
    print("wages before:", daily_wages)
    daily_wages * 2
    print("wages after doubling:", daily_wages)

print(f"Daily wages: {daily_wages} euros")
```

Indeed, the value is False, so the contents of the if block are never executed:

```
Sample output
condition:  False
Daily wages: 120.0 euros
```

The issue must then lie within the condition of the if statement. As in so many situations in programming, the case of letters matters also in comparisons. Notice how the "sunday" in the Boolean expression has not been capitalized, but in the input it was. Let's fix this (in both the print command and the if statement):

```py
# ...

daily_wages = hourly_wage * hours
print("condition:", day == "Sunday")
if day == "Sunday":
    print("wages before:", daily_wages)
    daily_wages * 2
    print("wages after doubling:", daily_wages)

print(f"Daily wages: {daily_wages} euros")
```

Running this prints out the following:

```
Sample output
condition: True
wages before: 120
wages after doubling: 120
Daily wages: 120.0 euros
```

It seems the value stored in daily_wages is correct at first: hourly_wage = 20.0 and hours = 6, and 20.0 * 6 = 120.0. The command which is supposed to double the figure doesn't do so, however, so there must be a problem with the command. And indeed the command

```py
daily_wages * 2
```

does double the value, but it doesn't store the new value anywhere. Let's change it so it also stores the new value:

```py
daily_wages *= 2
```

Running the program again reveals that the printout at the end is now also correct:

```
condition: True
wages before: 120
wages after doubling: 240
Daily wages: 240.0 euros
```

When the program has been fixed, remember to remove all debugging print statements and other code added for debugging purposes.

This example was quite simple, and in such a short program one could probably figure out the bugs just by reading the code carefully. However, using debugging print statements is often a quick way to get a feeling for where the problem might lie. Print statements can be used to figure out which parts of the program seem to work correctly, so bug tracking efforts can be concentrated on the sections of code which are the most likely culprits.

Debugging print statements are only one tool for debugging programs. We will come back to this subject later on during this course. You should now get into the habit of using debugging print statements to look for mistakes in your code. Programming professionals cannot get by without using them, so it is a very useful tool for beginners as well.