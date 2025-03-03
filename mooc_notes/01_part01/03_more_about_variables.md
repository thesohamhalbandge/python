## More about variables

Variables are needed for various purposes in programming. You can use variables to store any information that will be needed later in the program's execution.

In Python programming variables are created like so:

`variable_name = ...`

Here `...` means the value stored in the variable.

For example, when you used the `input` command to read a string from the user, you stored the string in a variable and then used the variable later in your program:

```py
name = input("What is your name? ")
print("Hi, " + name)
```

```
What is your name? Ghosty
Hi, Ghosty
```

The value stored in a variable can also be defined using other variables:

```py
given_name = "Paul"
family_name = "Python"

name = given_name + " " + family_name

print(name)
```

```
Paul Python
```

Here the values stored in the three variables are not obtained from user input. They remain the same every time the program is executed. This is called `hard-coding` data into the program.

## Changing the value of a variable

As implied by the name variable, the value stored in a variable can change. In the previous section we noticed that the new value replaces the old one.

During the execution of the following program, the variable `word` will have three different values:

```PY
word = input("Please type in a word: ")
print(word)

word = input("And another word: ")
print(word)

word = "third"
print(word)
```

```
Please type in a word: >> first
first
And another word: >>second
second
third
```

The value stored in the variable changes each time the variable is assigned a new value.

The new value of a variable can be derived from its old value. In the following example the variable `word` is first assigned a value based on user input. Then it is assigned a new value, which is the old value with three exclamation marks added to the end.

```py
word = input("Please type in a word: ")
print(word)

word = word + "!!!"
print(word)
```

```
Please type in a word: test
test
test!!!
```

## Integers

Thus far, we have only stored strings in variables, but there are also many other types of information we will want to store and access later. Let's have a look at integers first. Integers are numbers that do not have a decimal or fractional part, such as -15, 0 and 1.

The following program creates the variable age, which contains an integer value.

```py
age = 24
print(age)
```

The program prints out just this:

```
24
```

Notice the lack of quotation marks here. In fact, if we were to add quotation marks around the number, this would mean our variable would no longer be an integer, but a string instead. A string can contain numbers, but it is processed differently.

So, why does it matter that variables have a type, when the following program still prints out the same thing twice?

```py
number1 = 100
number2 = "100"

print(number1)
print(number2)
```

```
100
100
```

Variable types matter because different operations affect different types of variables in different ways. Let's have a look at an example:

```py
number1 = 100
number2 = "100"

print(number1 + number1)
print(number2 + number2)
```

This prints out the following:

```
Sample output
200
100100
```

For integer values the + operator means addition, but for string values it means concatenation, or "stringing together".

Not all operators are available for all types of variables. While numbers can be divided using the division operator /, attempting to divide a string by a number causes an error:

```py
number = "100"
print(number / 2)
```

```
TypeError: unsupported operand type(s) for /: 'str' and 'int'
```

## Combining values when printing

Similarly, the following program will not work, because "The result is " and result are of two different types:

```py
result = 10 * 25
# the following line produces an error
print("The result is " + result)
```

The program does not print out anything, but instead throws an error:

```
TypeError: unsupported operand type(s) for +: 'str' and 'int'
```

Here, Python tells us that combining two different types of values will not work just like that. In this case, "The result is " is of type string, while the value stored in result is of type integer.

If we do want to print out a string and an integer in a single command, the integer can be cast as a string with the str function, and the two strings can then be combined normally. For example, this would work:

```py
result = 10 * 25
print("The result is " + str(result))
```

```
The result is 250
```

The print command also has built-in functionalities that support combining different types of values. The simplest way is to add a comma between the values. All the values will be printed out regardless of their type:

```py
result = 10 * 25
print("The result is", result)
```

```
The result is 250
```

Notice that there is an automatically added whitespace character between the values separated by a comma here.

## Printing with f-strings

What if we want to have more flexibility and control over what we print out? So called f-strings are another way of formatting printouts in Python. The syntax can initially look a bit confusing, but in the end f-strings are often the simplest way of formatting text.

With f-strings the previous example would look like this:

```py
result = 10 * 25
print(f"The result is {result}")
```

Let's break this apart. In the very beginning of the string we are printing out there is the character f. This tells Python that what follows is an f-string. Within the string, enclosed in curly brackets, is the variable name result. The value it contains becomes a part of the printed string. The printout is exactly the same as in the previous examples:

```
The result is 250
```

A single f-string can contain multiple variables. For example this code

```py
name = "Mark"
age = 37
city = "Palo Alto"
print(f"Hi {name}, you are {age} years old. You live in {city}.")
```

prints out this:

```
Hi Mark, you are 37 years old. You live in Palo Alto.
```

It is difficult to create a printout exactly like this using the comma notation in the print command. For example, this program

```py
name = "Mark"
age = 37
city = "Palo Alto"
print("Hi", name, ", you are", age, "years old. You live in", city, ".")
```

prints out the following:

```
Hi Mark , you are 37 years old. You live in Palo Alto .
```

Notice the automatically inserted whitespace between each comma-separated part of the printout. Preventing `print` from adding the extra spaces is technically possible, but not worth the trouble given that we can instead use f-strings.

In its simplicity the comma notation of the `print` command can often be useful, but it does sometimes cause more trouble than it's worth. F-strings are usually a more reliable option. In part 4 you will learn more about the handy features of f-strings when it comes to formatting printouts.

## Floating point numbers

Floating point number or float is a term you will come across often in programming. It refers to numbers with a decimal point. They can be used much in the same way as integer values.

This program calculates the mean of three floating point numbers:

```py
number1 = 2.5
number2 = -1.25
number3 = 3.62

mean = (number1 + number2 + number3) / 3
print(f"Mean: {mean}")
```

```
Mean: 1.6233333333333333
```