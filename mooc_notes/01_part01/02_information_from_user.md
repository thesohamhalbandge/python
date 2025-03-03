# Information from the user

Input refers to any information a user gives to the program. Specifically, the Python command `input` reads in a line of input typed in by the user. It may also be used to display a message to the user, to prompt for specific input.

The following program reads in the name of the user with the `input` command. It then prints it out with the `print` command:

```py
name = input("What is your name? ")
print("Hi there, " + name)
```

The execution of this program could look like this:

```
What is your name? >> Paul Python
Hi there, Paul Python
```

What this program prints out is partially dependent on input from the user. That means the execution of the program could also look like this:

```
What is your name? >> Paula Programmer
Hi there, Paula Programmer
```

The word `name` in this program is a variable. In the context of programming, a variable is a location for storing some value, such as a string or a number. This value can be used later, and it can also be changed.

## Referencing a variable

A single variable can be referred to many times in a program:

```py
name = input("What is your name? ")

print("Hi, " + name + "!")
print(name + " is quite a nice name.")
```

If the user gives the name `Paul Python`, this program prints out the following:

```
What is your name? >> Paul Python
Hi, Paul Python!
Paul Python is quite a nice name.
```

Let's have a closer look at the way the `print` command is used above. Within the brackets of the command there is both text in quotation marks as well as variable names which refer to input from the user. These have been combined with a `+` operator, which concatenates two strings into a single string.

Strings and variables can be combined quite freely:

```py
name = input("What is your name? ")

print("Hi " + name + "! Let me make sure: your name is " + name + "?")
```

If the user gives the name `Ellen Example` this prints out

```
What is your name? >> Ellen Example
Hi Ellen Example! Let me make sure: your name is Ellen Example?
```

## More than one input

A program can ask for more than one input. Notice how below each input command stores the received value in a different variable.

```py
name = input("What is your name? ")
email = input("What is your email address? ")
nickname = input("What is your nickname? ")

print("Let's make sure we got this right")
print("Your name: " + name)
print("Your email address: " + email)
print("Your nickname: " + nickname)
```

The program could print out this, for example:

```
What is your name? >> Frances Fictitious
What is your email address? >> frances99@example.com
What is your nickname? >> Fran
Let's make sure we got this right
Your name: Frances Fictitious
Your email address: frances99@example.com
Your nickname: Fran
```

If the same variable is used to store more than one input, each new value will replace the previous one. For example:

```py
address = input("What is your address? ")
print("So you live at address " + address)

address = input("Please type in a new address: ")
print("Your address is now " + address)
```

An example execution of the program:

```
What is your address? >> Python Path 101, Flat 3D
So you live at address Python Path 101, Flat 3D
Please type in a new address: >> New Road 999
Your address is now New Road 999
```

This means that if the same variable is used to store two inputs in succession, there is no way to access the first input value after it has been replaced by the second:

```py
address = input("What is your address? ")
address = input("Please type in a new address: ")

print("Your address is now " + address)
```

An example of how the program's output might look like:

```
What is your address? Python Path 10
Please type in a new address: Programmer's Walk 23
Your address is now Programmer's Walk 23
```