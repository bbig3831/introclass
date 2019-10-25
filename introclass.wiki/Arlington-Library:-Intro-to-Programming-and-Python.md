Python is a high-level scripting language for general purpose programming. 

Notable organizations that use Python: Google, Wikipedia, Yahoo!, CERN, NASA. The lessons below will start from the very beginning of computer programming and walk step by step through some basic programming concepts while giving students the knowledge needed to create basic programs. We'll be covering the following topics (or as many as we can get through in the time we have):
* Numerical Operators
* Data Types
* Variables
* User Input
* Comparator Operations
* Logical Operators
* Loops
* Modules

These will all be building to our final exercise where we'll create a basic Rock-Paper-Scissors game using the concepts we've learned in class.

## 1. Our first Python script

In order to write our script we'll need a code editor to work in. Open the link below in a separate tab:

[Replit Python](https://repl.it/languages/python)

On the left hand side of the page, you'll see your scripting window. This is where we'll be writing and running Python code. On the right side, you'll see the output console. When running your script, any output or messages from the script will be displayed in this output console.

For our first script, enter the following text in the scripting window:

`print("Hello World!")`

Once entered, press the "Run" button at the top of the page. Do you see anything in the output console?

Congratulations, you've just run your first program!

Here we see our first example of a __function__, which in Python can be recognized by the (). In programming a function is a piece of code that the programmer gives information to and the function then does something specific with that information. In this case, the information that the 'print' function takes is the text between the parentheses and the function prints that text out to the console. Displaying information to the console is the most basic way of giving information to a user. It is also very useful when programming to be able to see what your code is doing at different steps in the program. 

### 1.1 Exercise
Can you change your script to have it print your name? Make sure to note the quotation marks around the text 'Hello World!' in the example above.

## 2. Numeric operations
Numeric operations are operations that take numbers as inputs and output new numbers. Python supports basic and more complex numeric operations, a few of these are listed below as examples.

```
print(1 + 1)  # Addition
print(1 - 1)  # Subtraction
print(1 * 10) # Multiplication
print(10 / 2) # Division
print(2 ** 2) # Exponentiation (raising to a power)
print(int(10 / 3)) # Return only integer component
```
Notice here when using the print function that we're not using quotation marks. That's because, rather that Python treating '1 + 1' as text, we want it to treat it as code and evaluate it. Try running the code below and looking at the output:

`print("1 + 1")`

In this code Python treats '1 + 1' as text so rather than performing the math it simply prints out the text.

Although not a numeric operation, the '+' can also be used to connect text together, as in the example below:

`print("Hello " + "World!")`

The plus sign tells Python to connect the two individual pieces of text into one piece, and then the 'print' function prints that combined text to the console.

### 2.1. Comments
Another thing that's shown in the sample code above is something called a __comment__. Comments are text inside  your script that are ignored by Python when running the script. These are useful because they can be used to add notes or explanations to your script without having to change the way the script runs. In Python, the __#__ indicates a comment, and everything following a __#__ on a line of code will be ignored when you run your script. 

The __#__ can also be used to remove code from your script without deleting it forever. By putting a __#__ at the beginning of a line of code, it will be ignored when you run your program. For this course, I would recommend rather than deleting code after an exercise, you simply comment the code out using the __#__ at the start of the line. That way, if you want to look back at earlier exercises all of your code will still be there.

### 2.2. Exercise
Can you print the sum total (addition) of all numbers from 1 to 10?

## 3. Data types
Sometimes we want to display more than just a number, we want to have some text to describe it. Let's say we want the text "Total:" to print in front of our sum. Let's try running the code below:

`print("Total: " + (1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10))`

What do you see?

The code above didn't work because the text "Total" is a different data type than the number 55. "Total" is a __string__ (text) and 55 is an __integer__ (number). When Python tries to add these two values together it can't combine these two data types and so it raises an error. While Python is very relaxed about data types, it's still important to know the different data types and what they represent. The list below shows some of the basic data types:

```
"Hello World!" # this is a string
'Hello World!' # this is also a string, Python can handle both single and double quotes
1 # this is an integer, which is a whole number
2018 # this is also an integer
1.0 # this is a floating point number, which is different from an integer because it can have a decimal portion
3.14159265 # this is also a floating point number
True # this is a boolean (True/False)
```

We saw above in the numeric operations the int() function, which converts data into the __integer__ type. In programming, this conversion is called 'casting' and it allows us to convert from one data type into another. Similar functions exist for different data types:

```
str()   # Cast data to the string type
int()   # Cast data to the integer type
float() # Cast data to the floating point type
bool()  # Cast data to the boolean type
```
Casting doesn't always work (for instance, casting "Hello World!" to an __int__ doesn't exactly make sense) but in general Python is pretty smart about casting so feel free to try it out if you want to convert between data types.

Knowing this, we can alter our code from above:

`print("Total: " + str(1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10))`

What do you see now as your output? This code converts the sum to a __string__ and then combines it with the "Total: " string to give us our output. Since the sum is now a string Python has no problem combining it with the string "Total"

### 3.1. Error Messages

When we ran the first line of code in this section we saw the following error message:

```
Traceback (most recent call last):
  File "python", line 1, in <module>
TypeError: cannot concatenate 'str' and 'int' objects
```

Error messages in Python can be very helpful for determining what's going wrong in your code. In the message above we see that the error message tells us the line where the error occurred (in this case line 1), and a general description of the error (in this case "cannot concatenate 'str' and 'int' objects"). When you're first starting out with programming you'll likely make a lot of small mistakes, so understanding error messages and using them to help fix your code is an important skill to have.

## 4. Variables

A variable is a way to store information to make it easier to access or manipulate in the future. In Python, variables are defined using the equal sign:

`x = "Hello World!"`

Now the text "Hello World!" is stored in the variable x. Because of that, whenever we want to use the text "Hello World!" we can use x instead. Let's try that using the print function:

`x = "Hello World!"`

`print(x)`

As expected, we see "Hello World!" print to the console. A problem with the code above is, the variable name 'x' isn't very descriptive. When naming variables, using a descriptive name is important. That will allow you to keep track of your variables easier when coding. With this in mind we can re-write the code above:

`hello_world = "Hello World!"`

`print(hello_world)`

### 4.1. Data Types

Variables can store any data types, for example:

```
str_var = "Test Text"
float_var = 1.0
int_var = 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10
bool_var = False
```

Variables can be used exactly the same as the value they store. In the following code, what do we expect to see printed out?

```
x = 10
print(x + 5)
```

### 4.2. Exercise
Given the code below and everything we've learned so far, can you use the two variables below and have your script output the text "Total : 55"

```
str_var = "Total : "
int_var = (1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10)
```
Remember that in order to combine two things they have to be of the same data type, so it may be necessary to convert, or cast your data to a different type.

## 5. User Input

So far we've simply run our scripts as is with no user input, but in reality we're going to want our scripts/programs to be able to take use input from the user and respond to what they've input. In Python, the simplest way of prompting a user for input looks like the code below:

```
user_input = raw_input("Please enter a number: ")
print("The user entered: " + user_input)
```

Running this code you'll see that the text "Please enter a number: " is displayed and the console is waiting for user input. After typing your input and pressing enter, the second line of the script is executed and the input is printed out. The 'raw_input' function is a new type of function in that not only does it take input from the user, after it runs it returns information to the user. In this case, 'raw_input' displays the input text to the user, and it stores the information returned, in this case the user input, in the 'user_input' variable as a string. 

### 5.1. Example
For this example, we'll prompt the user to enter a number, add 10 to it, and then output the results. Based on how we've done things :

```
user_input = raw_input("Please enter a number: ")
print("The user's number plus 10 is: " + str(int(user_input) + 10))
```

This code does exactly what we expect it to do, but it's kind of hard to read, so now, for an exercise, we'll re-write this code using variables.

```
user_input = raw_input("Please enter a number: ") # Prompt the user for a number

user_input_int = int(user_input) # Convert the input string into an integer

user_input_new = user_input_int + 10 # Add 10 to the input

user_input_string = str(user_input_new) # Convert the final value to a string for printing

print("The user's number plus 10 is: " + user_input_string) # Print the output
```

This code does the same thing as our code above but it much more readable and much easier to edit. Writing your code in a way that's readable is very important, as it makes it easier to debug and easier for others to understand.

### 5.2. Exercise
Prompt the user to enter the year they were born and print out the age they were at the end of 2017. Remember, the data from the raw_input() function is a string so in order to use mathematical operations you'll have to cast the input to a number (see Section 3).

## 6. Comparator operations
Now that we have input from the users, we have to be able to interpret it and have our code act accordingly. For this we have to check the input against what we expect to be input, and for this we'll use comparators. Comparator operations are used to compare numbers or data, and all of them are evaluated as either True or False. Some of these comparators are listed below:

The '==' checks to see if the two values are equal to each other
```
x = 3 # Set the value of the variable x to 3
print(x == 3) # This evaluates as True because x is equal to 3
print(x == 4) # This evaluates as False because x is not equal to 4
```
This also can be used to compare strings to each other:
```
x = "Hello" # Set the value of the variable x to "Hello"
print(x == "Hello") # This evaluates as True because "Hello" is equal to "Hello"
print(x == "Hello!") # This evaluates to False because the second "Hello!" has an additional exclamation point
```
The '>' checks to see if the left value is greater than the right value
```
x = 4 # Set the value of the variable x to 4
print(x > 3) # This evaluates as True because x is greater than 3
print(x > 5) # This evaluates as False because x is not greater than 5
```
The '<' checks to see if the left value is less than the right value
```
x = 4 # Set the value of the variable x to 4
print(x < 5) # This evaluates as True because x is less than 5
print(x < 3) # This evaluates as False because x is not less than 3
```
The '>=' checks to see if the left value is greater than or equal to the right value
```
x = 4 # Set the value of the variable x to 4
print(x > 4) # This evaluates as False because x is not greater than 4
print(x >= 4) # This evaluates as True because x is greater than or equal to 4
```

The '>=' checks to see if the left value is less than or equal to the right value
```
x = 4 # Set the value of the variable x to 4
print(x < 4) # This evaluates as False because x is not less than 4
print(x <= 4) # This evaluates as True because x is less than or equal to 4
```

Finally, the 'not' operator reverses a comparator, for instance:
```
x = 2 # Set the value of the variable x to 2
print(x == 2) # This evaluates to True because x is equal to 2
print(not x == 2) # This evaluates as False because the 'not' operator switches the True to False
```

Try printing a few of the above statements to get a feel for how these operators work.

### 6.1. Exercise
Prompt the user to enter the number 10. Print out whether or not the user input is equal to 10. Test your script by entering '10' and also entering '5'. Does the script show the correct output?

```
user_input = raw_input("Please enter the number 10: ") # Prompt the user to enter number 10
print(user_input ?? 10)
```

## 7. Logical Operators
Now that we have user input and comparators we can use these to check the user input and change the behavior of our script. In order to do that we'll use what's called an __if statement__:

```
user_input = raw_input("Please enter the number 10: ")
if int(user_input) == 10:
    print("Correct Input")
```

In this case, the if statement checks to see if the value of 'user_input' is equal to '10'. If that's True, it runs the code underneath the 'if' statement and prints 'Correct Input'. If not, it executes the code under the 'else' statement and prints 'Incorrect Input'. 

Note the colons at the end of the 'if' line. This is to tell Python that the next lines are part of the 'if' statement. The indentations also indicate that the indented lines are part of the 'if' statement that contains them. An example of this code being incorrectly formatted is:

```
user_input = raw_input("Please enter the number 10: ")
if int(user_input) == 10:
print("Correct Input")
```

Running this code will cause an error because the 'print' function isn't indented properly.

The 'if' statement also has a counterpart called the 'else' statement, an example of which can be seen below.

```
user_input = raw_input("Please enter the number 10: ")
if int(user_input) == 10:
    print("Correct Input")
else:
    print("Incorrect Input")
```
Running the code above, what do you see?

The 'else' statement runs if the 'if' statement is not met. In the code above, the user input is checked to see if it equals '10'. If it doesn't, the code under the 'else' statement is run, and the program prints 'Incorrect Input'.

### 7.1. Exercise
Prompt the user to enter a number greater than 10. Add an 'if' statement to check that the number entered is actually greater than 10. Print output messages for the cases where the input number is greater than 10 and not greater than 10.

### 7.2. Logical Operators Continued
The 'if' statement allows us to check if a certain condition is true and have the correct code run accordingly, but what if we want to check multiple conditions at the same time? The most basic way would be to have two 'if' statements:

```
if 1 == 1:
    if 2 == 2:
        print("Both True")
```
This is useful but can be hard to follow, especially if checking more than a couple conditions. To help us, Python has additional operators that we can use, specifically the 'and' and 'or' operators.

The 'and' operator checks multiple conditions and evaluates as true only if all of the conditions are true, for example:

```
if 1 == 1 and 2 == 2:
    print("Both True") # Because 1 equals 1 and 2 equals 2, this statement will print

if 1 == 1 and 2 == 3:
    print("Both True") # Because 1 equals 1 but 2 does not equal 3, this statement will not print
```

If both 'a' and 'b' equal True, the program will print the text 'Both True'. However, if either 'a' or 'b' do not equal true, the print function will not be called. The 'and' function can be changed as many times as needed, and will evaluate as long as all checks evaluate to True.

```
if a == True and b == True and c == True and d == True:
    print("All True")
```

The 'or' operator is used in the same way but it evaluates as true if any of it's conditions are true.

```
if 1 == 1 or 2 == 2:
    print("One True") # Because 1 equals 1 and 2 equals 2, this statement will print

if 1 == 1 or 2 == 3:
    print("One True") # Because 1 equals 1, this statement will print because only one of the conditions need to be true

if 1 == 2 or 2 == 3:
    print("One True") # Because neither 1 equals 2 not 2 equals 3, this statement will not print
```

### 7.3. Exercise
Prompt the user to enter either 'Rock', 'Paper', or 'Scissors'. Add a statement that checks to see if the user has entered one of those three values. If the user entered one of the three values print 'Correct Input', otherwise print 'Incorrect Input'.

## 8. Loops
Loops are an important part of programming. A loop is a way to run the same section of code multiple times, either a set number of times or until a certain condition is met. The loop that runs until a condition is met is called a 'while' loop, and it looks like this:

```
user_input = ""
while not int(user_input) == 10:
    user_input = raw_input("Enter the number 10 to stop the loop: ")
```

Try running the above code and try entering values other than 10. What do you see? Now try entering 10 and see what happens. The code within the loop, in this case the prompt for user to input the number 10, runs until the user inputs the number 10, at which point the loop stops. 'While' loops are for when you want to repeat a section of code an unknown number of times, only stopping when a certain condition is met.

### 8.1. Exercise
Create a while loop that runs until a user enters the text 'Quit'. Inside the loop prompt the user with text similar to "Type 'Quit' to exit: ".

### 8.2. For Loops
Let's say that rather than looping until a condition happens, we know that we actually just want to run the code a set number of times. Technically, we can do that with a 'while' loop, and it would look something like this:

```
counter = 1 # Set a variable to an initial value to start counting from
while counter < 6: # Loop while our counter is less than our end value
    print(counter)
    counter = counter + 1 # Each loop, add one to our counter
```

Running this code, we see the counter print from 1 to 5. At the end of the last loop, counter gets incremented to 6, so when it checks the condition for the loop it's no longer true so the loop exits. While this is obviously possible to do with 'while' loops, there is a specific loop for this called a 'for' loop, which looks like this:

```
for counter in range(1,6):
    print(counter)
```

Running this loop we see that this loop prints the numbers 1 through 5 just like the while loop, but this time instead of us having to define counter and then add one to it each time, the for loop takes care of that for us. The 'range' function defines the start and end values of the counter, and one thing to be aware of is that just like we saw in our 'while' loop example, the loop stops when the counter gets to 6 meaning the loop only occurs 5 times. This is kind of counter-intuitive but we'll learn later that there's a good reason for it to function this way.

### 8.3. Exercise
Earlier in the lesson we added all of the numbers from 1 to 10 and got the number 55. Can you use a for loop to accomplish the same thing? Below is some code to get you started:

```
total = 0
for counter in range(1,11):
    # Add your code here
```

Remember that similar to our sample 'while' loop, the value in counter starts at 1 and increments by one each loop.

## 9. Modules
So far everything we've done has been using the basic functionality that the Python language provides, but one powerful thing about modern programming languages and Python in particular is that we can use code developed by other people to make our lives easier.

A common necessity in computer programming is generating random numbers, which are used in games, banking, security, and many other applications. Random number generation is complicated and uses some high level mathematics, but luckily other people have already created ways to do this and we can utilize their work.

To use a module in Python we have to import it:

`import random`

Now that we've imported the module, we can use all of the functionality inside it. The __random__ module has a function in it called randint. It takes two integers as inputs and returns a random integer between the two input integers. It should be noted that it can also return the input integers, so for example:

```
import random

random_number = random.randint(1, 10) # This will return a random integer from 1 to 10
```

As you can see above, to call the randint function we have to reference the module that contains it, in this case the __random__ module.

Python has countless modules available online that allow users to do everything from reading files to accessing the web to sending e-mails and more. When approaching a program, make sure to do some Googling to see if anyone has already solved the problem you're working on, it could save you a lot of time.

### 9.1 Example
We'll be using the randint function in our Rock Paper Scissors game in order to generate a random play from the computer. The code below shows how we can do this:

```
import random
random_number = random.randint(1,3) # Because we have 3 choices (rock, paper, or scissors), we want to generate a random number from 1 to 3

# Based on the random number we generated, define a variable called 'computer_choice' that has either rock, paper, or scissors
if random_number == 1:
    computer_choice = "Rock"
if random_number == 2:
    computer_choice = "Paper"
if random_number == 3:
    computer_choice = "Scissors"

print("The computer choice is " + computer_choice)
```

Try running the code above a few times. You'll see that when you run it multiple times you get different answers. This is due to the random module generating a different number each time the script is run.

## 10. Final Exercise - Rock Paper Scissors
For the final section of this class, we'll take everything we've learned and put it all together. Rock, Paper, Scissors is a simple game but it's a great example of how to take something simple and think about how to implement it programmatically.

For this exercise, I'll outline the different steps you'll need to take and then it'll be up to you to use what you've learned today to implement those steps.

### 10.1. Simple program
We'll start simple with a single game of RPS. For this you should:

* Welcome the user/introduce the game
* Prompt the user for their selection for the game (Rock, Paper, or Scissors)
* Randomly generate a computer's selection (this code can be taken directly from the 'Modules' section)
* Determine if the user won, lost, or tied
* Output the results of the match

```
# Welcome the user
print("Welcome to Rock, Paper Scissors!")

# Prompt the user for their choice
user_choice = raw_input("Enter Rock, Paper, or Scissors: ")

# Generate the computer's selection
import random
random_number = random.randint(1,3) # Because we have 3 choices (rock, paper, or scissors), we want to generate a random number from 1 to 3

# Based on the random number we generated, define a variable called 'computer_choice' that has either rock, paper, or scissors
if random_number == 1:
    computer_choice = "Rock"
if random_number == 2:
    computer_choice = "Paper"
if random_number == 3:
    computer_choice = "Scissors"
print("The computer choice is " + computer_choice)

# No matter what, if the two choices are the same the game is tied
if user_choice == computer_choice:
    print("Tie Game!")

# Check all scenarios and output the results
if user_choice == "Rock":
    if computer_choice == "Scissors":
        print("You won!")
    if computer_choice == "Paper":
        print("You lost!")
if user_choice == "Scissors":
    if computer_choice == "Paper":
        print("You won!")
    if computer_choice == "Rock":
        print("You lost!")
if user_choice == "Paper":
    if computer_choice == "Rock":
        print("You won!")
    if computer_choice == "Scissors":
        print("You lost!")
```

### 10.2. Adding a little complexity
To make the game a little easier for the user to play multiple times, for the next exercise we'll have the game repeat until the user wants to quit. To do this you'll use the code you've already created but you'll have to add a couple things:

* Create a 'while' loop that runs until the user enters a quit command
* Update your user prompt to indicate that the player can now quit with a 'quit' command

```
# Welcome the user
print("Welcome to Rock, Paper Scissors!")

user_choice = ""

# Loop until the user enters quit
while not user_choice == "Quit":
    # Prompt the user for their choice
    user_choice = raw_input("Enter Rock, Paper, or Scissors, or enter Quit to quit the game: ")

    # Generate the computer's selection
    import random
    random_number = random.randint(1,3) # Because we have 3 choices (rock, paper, or scissors), we want to generate a random number from 1 to 3

    # Based on the random number we generated, define a variable called 'computer_choice' that has either rock, paper, or scissors
    if random_number == 1:
        computer_choice = "Rock"
    if random_number == 2:
        computer_choice = "Paper"
    if random_number == 3:
        computer_choice = "Scissors"
    print("The computer choice is " + computer_choice)
    
    # No matter what, if the two choices are the same the game is tied
    if user_choice == computer_choice:
        print("Tie Game!")

    # Check all scenarios and output the results
    if user_choice == "Rock":
        if computer_choice == "Scissors":
            print("You won!")
        if computer_choice == "Paper":
            print("You lost!")
    if user_choice == "Scissors":
        if computer_choice == "Paper":
            print("You won!")
        if computer_choice == "Rock":
            print("You lost!")
    if user_choice == "Paper":
        if computer_choice == "Rock":
            print("You won!")
        if computer_choice == "Scissors":
            print("You lost!")
```

### 10.3. Adding a scoreboard
Finally, it would be nice if the user could check their record to see how many games they've won, lost, or tied. To do this, we'll have to add a couple more things:

* Initialize the user's scores to zero
* Add logic to update the user scores after a game has been played
* Update your code to print the user scores after each game

```
# Initialize user's scores to zero
ties = 0
wins = 0
losses = 0

# Welcome the user
print("Welcome to Rock, Paper Scissors!")

user_choice = ""

# Loop until the user enters quit
while not user_choice == "Quit":
    # Prompt the user for their choice
    user_choice = raw_input("Enter Rock, Paper, or Scissors, or enter Quit to quit the game: ")

    # Generate the computer's selection
    import random
    random_number = random.randint(1,3) # Because we have 3 choices (rock, paper, or scissors), we want to generate a random number from 1 to 3

    # Based on the random number we generated, define a variable called 'computer_choice' that has either rock, paper, or scissors
    if random_number == 1:
        computer_choice = "Rock"
    if random_number == 2:
        computer_choice = "Paper"
    if random_number == 3:
        computer_choice = "Scissors"
    print("The computer choice is " + computer_choice)
    
    # No matter what, if the two choices are the same the game is tied
    if user_choice == computer_choice:
        print("Tie Game!")
        ties = ties + 1

    # Check all scenarios and output the results
    if user_choice == "Rock":
        if computer_choice == "Scissors":
            print("You won!")
            wins = wins + 1
        if computer_choice == "Paper":
            print("You lost!")
            losses = losses + 1
    if user_choice == "Scissors":
        if computer_choice == "Paper":
            print("You won!")
            wins = wins + 1
        if computer_choice == "Rock":
            print("You lost!")
            losses = losses + 1
    if user_choice == "Paper":
        if computer_choice == "Rock":
            print("You won!")
            wins = wins + 1
        if computer_choice == "Scissors":
            print("You lost!")
            losses = losses + 1

    # Display scores
    print("You've tied " + str(ties) + " games")
    print("You've won " + str(wins) + " games")
    print("You've lost " + str(losses) + " games")
```

https://github.com/jeheidrich/introclass/wiki/Arlington-Library:-Intro-to-Programming-and-Python

## 11. Other examples

This section shows some other examples of Python scripts doing some basic tasks that may be useful for beginning students.

### 11.1 Reading a file line by line
The script below opens a file, reads it line by line, and prints each line. Finally it closes the file.

```
# The open function takes the path to a file on your local computer and opens it. 
# In the line below, the "./" at the start indicates that the file is in the same directory as the script you're running.
# The "r" argument in the function indicates that we will be reading the file
f = open("./dataFile.txt", "r")

# The readline function reads the next line from the file. In this case since we just opened the file, it will read the first line and store it in the variable named "line" 
line = f.readline()

# The while loop below will continue looping as long as the variable "line" has a value in it. When we reach the end of the file, the readline function will return an empty value, stopping the loop
while line:
    # Print the line of the file
    print line
    
    # Read the next line of the file
    line = f.readline()

# Now that we're done, close the file
f.close()
```

