# Getting Started

Computer programs consist of commands, each command instructing the computer to take some action. A computer executes these commands one by one. Among other things, commands can be used to perform calculations, compare things in the computer's memory, cause changes in how the program functions, relay messages or ask for information from the program's user.

Let's begin programming by getting familiar with the `print` command, which prints text. In this context, printing essentially means that the program will show some text on the screen.

The following program will print the line "Hi there!":

```py
print("Hi there!")
```

When the program is run, it produces this:

```
Hi there!
```

The program will not work unless the code is written exactly as it is above. For example, trying to run the print command without the quotation marks, like so

```
print(Hi there)
```

will not print out the message, but instead causes an error:

```
File "", line 1
  print(Hi there!)
                   ^
SyntaxError: invalid syntax
```

In summary, if you want to print text, the text must all be encased in quotation marks or Python will not interpret it correctly.

## A program of multiple commands

Multiple commands written in succession will be executed in order from first to last. For example this program

```py
print("Welcome to Introduction to Programming!")
print("First we will practice using the print command.")
print("This program prints three lines of text on the screen.")
```

prints the following lines on the screen:

```
Sample output
Welcome to Introduction to Programming!
First we will practice using the print command.
This program prints three lines of text on the screen.
```

## Arithmetic Operations

You can also put arithmetic operations inside a `print` command. Running it will then print out the result of the operation. For example, the following program

```py
print(2 + 5)
print(3 * 3)
print(2 + 2 * 10)
```

prints out these lines:

```
Sample output
7
9
22
```

Notice the lack of quotation marks around the arithmetic operations above. Quotation marks are used to signify strings. In the context of programming, strings are sequences of characters. They can consist of letters, numbers and any other types of characters, such as punctuation. Strings aren't just words as we commonly understand them, but instead a single string can be as long as multiple complete sentences. Strings are usually printed out exactly as they are written. Thus, the following two commands produce two quite different results:

```py
print(2 + 2 * 10)
print("2 + 2 * 10")
```

This program prints out:

```
22
2 + 2 * 10
```

With the second line of code, Python does not calculate the result of the operation, but instead prints out the operation itself, as a string. So, strings are printed out just as they are written, without any reference to their contents.

## Commenting

Any line beginning with the pound sign `#`, also known as a hash or a number sign, is a comment. This means that any text on that line following the `#` symbol will not in any way affect how the program functions. Python will simply ignore it.

Comments are used for explaining how a program works, to both the programmer themselves, and others reading the program code. In this program a comment explains the calculation performed in the code:

```py
print("Hours in a year:")
# there are 365 days in a year and 24 hours in each day
print(365*24)
```

When the program is run, the comment will not be visible to the user:

```
Hours in a year:
8760
```

Short comments can also be added to the end of a line:

```py
print("Hours in a year:")
print(365*24) # 365 days, 24 hours in each day
```