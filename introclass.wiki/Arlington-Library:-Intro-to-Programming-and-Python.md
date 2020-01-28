The URL for the course syllabus is : https://github.com/bbig3831/introclass/wiki/Arlington-Library:-Intro-to-Programming-and-Python

Python is a high-level scripting language for general purpose programming. Notable organizations that use Python include Google, Wikipedia, Yahoo!, CERN, NASA. You can use Python for anything from data analysis or machine learning to web development or game development. The sky's the limit!

In the introductory course, we'll start out with some simple concepts and work towards building an interactive Rock-Paper-Scissors game.

If you have detailed questions about how certain things work, please consult the Python documentation, which has extensive detail on how any given data type, function, or module works. (Link to documentation: https://docs.python.org/3.7/).

## 1. Our first Python script

In order to write our script we'll need a code editor to work in. Open the link below in a separate tab:

[Repli.t Python](https://repl.it/languages/python3) - https://repl.it/languages/python3

On the left hand side of the page, you'll see your editor window. This is where we'll be writing and running Python code. On the right side, you'll see a Python console. When running your script, any output or messages from the script will be displayed in this output console. Repl.it is a code editor with __syntax highlighting__; this means that different data types will have different colors. The colors of syntax highlighting may vary across editors, although it will always be internally consistent.

For our first script, type the following text in the scripting window:

```python
print("Hello World!")
```

> **What do you think this will do? Think about it before pressing the "Run" button at the top of the page.**

Congratulations, you've just run your first program!

What do you see in the output console? Does it match what you expected?

Here we see our first example of a __function__, which in Python can be recognized by the parentheses `()`. In programming a function is a piece of code that the programmer gives information to and the function then does something specific with that information.

In this case, the `print` function takes the text inside the parentheses as the input; the function prints that text out to the console. Displaying information to the console is one way of giving information to a user. It is also very useful since you can see what your code is doing at different steps in the program.

The text `"Hello World!"` is an example of a **string** data type. You can identify strings in Python by the surrounding single (`'`) or double (`"`) quotes.

> Does the `print()` have to take strings as inputs? Or can it take other inputs? How would you check?

### 1.1 Exercise
Can you change your script to have it print `Welcome to the Rock-Paper-Scissors game!`? Make sure to note the quotation marks around the text `'Hello World!'` in the example above.

## 2. Getting user input
If we're trying to build an interactive game, we'll probably want to ask the user for some information, such as their name and their choice of rock, paper, or scissors.

```python
print('Welcome to the Rock-Paper-Scissors game!')
player = input("What's your name? ")
print(f'Welcome, {player}!')
```

Here we see another example of a **function** in Python: the `input` function. The `input` function prompts the user for an input and then stores that value as a **string**.

We're also seeing our first example of a variable, `player`. A **variable** is a way of storing information to make it easier to access or manipulate in the future. In Python, variables are assigned with the `=` sign.

What do you notice about the last line above? Python 3 introduced a method of string formatting called **f-string formatting** that allows us to use variables directly in a string. The following lines all do the same thing.

```python
# Using f-string formatting
print(f'Welcome, {player}')
# Using  the format() method
print('Welcome, {player}'.format(player=player))
# Using % formatting
print('Welcome, %s' % player)
```

You might notice some lines that start with `#`. These are **comments**. In computer programming, we can use **comments** to explain what's going on, which makes our code easier to read. Good comments will make your code more readable to other people...including your future self!

### 2.1 Exercise

Can you change your script so that it prompts the user for a roll (i.e. rock/paper/scissors)? Store the response in a variable named `roll`.

## 3. Logical operators

At this point, our script should look similar to this:
```python
print('Welcome to the Rock-Paper-Scissors game!')
player = input("What's your name? ")
print(f'Welcome, {player}!')
roll = input('Choose your roll (rock/paper/scissors): ')
```

We've asked the user for input that we might want to use later on. But how do we know it's good input? What if the user had entered `Lizard`? Or `5`?

By using **logical operators**, we can validate that we can use what was entered. One such operator is `==`, which checks equality. Try the following on your command line:

```python
a = 5
b = 5
c = 6
a == b
a == c
```

Let's ammend our program to check the user input.

```python
print('Welcome to the Rock-Paper-Scissors game!')
player = input("What's your name? ")
print(f'Welcome, {player}!')
roll = input('Choose your roll (rock/paper/scissors): ')
print(roll == 'rock')
print(roll == 'paper')
print(roll == 'scissors')
```

We could write this on one line with an `or` operator.
```python
print(roll == 'rock' or roll == 'paper' or roll == 'scissors')
```

By combining these logical operators with a **conditional statement**, also called an `if-else` clause, we can change the behavior of our program based on a logical condition.

```python
if roll == 'rock' or roll == 'paper' or roll == 'scissors':
    print('Input is good!')
else:
    print('Input is not good!')
```

### 3.1 Exercise

Using the not-equals operator `!=` and the `and` operator, change the `if-else` clause to check if the input is **NOT** good.

## 4. Lists

In Python, **lists** are incredibly powerful data structures. A **list** is an ordered and changeable group of data denoted by square brackets `[...]`. It would be a good idea to store our roll options in a list and assign them to a variable.

```python
roll_options = ['rock', 'paper', 'scissors']
```

Lists are indexed using **integers**, starting with 0.

```python
roll_options[0]
roll_options[1]
roll_options[2]
```

If we put the `roll_options` variable at the start of our program, we can continue using it.

```python
roll_options = ['rock', 'paper', 'scissors']

print(f'Welcome to the {'-'.join(roll_options)} game!')
player = input("What's your name? ")
print(f'Welcome, {player}!')
roll = input(f"Choose your roll ({'/'.join(roll_options)}): ")
```

> You should notice we're using a new `join()` function with our list. How do you think this works?

We can also use the `in` operator to check whether something exists in a list. This is useful for checking our user's input.

```python
if roll in roll_options:
    print('Input is good!')
else:
    print('Input is bad!')
```

### 4.1 Exercise

Using the `not` operator, change the code above so that it checks whether the input is bad.

## 5. Errors

What happens when you run the following line of code?

```python
print('Total: ' + 10)
```

You should get something that looks like this:

```
Traceback (most recent call last):
  File "python", line 1, in <module>
TypeError: cannot concatenate 'str' and 'int' objects
```

Error messages in Python can be very helpful for determining what's going wrong in your code. In the message above we see that the error message tells us the line where the error occurred (in this case line 1), and a general description of the error (in this case `cannot concatenate 'str' and 'int' objects`). When you're first starting out with programming, you'll likely make a lot of small mistakes, so understanding error messages and using them to help fix your code is an important skill to have.

## 6. Importing modules

So far, our rock-paper-scissors game is looking pretty good. We have:
1. Welcomed the user to the game.
2. Asked for their name and their roll.
3. Checked whether the input was valid.

Next, we probably want to generate the computer's roll. To make things interesting, we'll want the roll to be random. Thankfully, Python has a built-in module called `random` for working with random numbers. A **module** in Python is a set of similar functions or objects generally used for similar or related purposes.

We can import the `random` module at the beginning of our script with the following line:

```python
import random
```

That's it! Very easy to do.

We can index lists in Python with **integers** (e.g. 0, 1, 100, etc.), so we could use this approach to pick the computer's roll. The `random` module has a `randint` function that genrates a random integer, which we'll use for this purpose.

```python
rand_pick = random.randint(0, 2)
computer_roll = roll_options[rand_pick]
```

However, there's actually an even easier way to do this with the `random.choice()` function!

```python
computer_roll = random.choice(roll_options)
```

### 6.1 Exercise

Take a look at the Python documentation for the `random` module. Is there something you think you could use for one of your coding projects?

Documentation: https://docs.python.org/3.7/library/random.html

## 7. Dictionaries

Now that we've got the user's roll and the computer's roll, we'll probably want to compare the two rolls to see who wins. The first step to doing that is constructing a **dictionary**. In Python, a **dictionary** is similar to a list, since it's unordered and changeable, but dictionaries also have formal indexes or **keys**. A dictionary is often referred to as containing **key-value** pairs. Dictionaries can be recognized by their curly brackets `{...}`.

Let's put together a dictionary where the key is a roll (e.g. rock, paper, or scissors) and the value is the roll that it beats.

```python
rules = {
    # Rock beats scissors
    'rock':'scissors',
    # Paper beats rock
    'paper':'rock',
    # Scissors beats paper
    'scissors':'paper'
}
```

Unlike lists, which have integer indexes, we can use the string indexes for dictionaries to access their contents.

```python
print('Here are the rules:')
print(f"  * Rock beats {rules['rock']}.")
print(f"  * Paper beats {rules['paper']}.")
print(f"  * Scissors beats {rules['scissors']}.")
```

## 8. For loops

There is a principle in programming called DRY: "Don't Repeat Yourself". If you look at the last few lines of code we wrote in the previous section, you should notice there is a lot of repitition. How can we get rid of this and make our code cleaner and simpler?

One of the more useful constructs in programming is a **loop**. One type of loop is a **for loop**. A **for loop** is a loop that executes certain steps a set number of times. In Python, **for loops** are written with the following syntax:

```python
# For numbers 1 to 10
for i in range(1, 11):
    # Do something here
    pass
```

The great thing about for loops in Python is that they work with not only with numbers - like we saw with the `range()` function - but also with objects like lists or dictionaries. Let's see what we can do with our `rules` dictionary. There are a few ways to do this.

```python
print('Here are the rules:')
# Using keys()
for key in rules.keys():
    print(f"  * {key} beats {rules[key]}.")

# Using items()
for key, value in rules.items():
    print(f"  * {key} beats {value}.")

# Using the rolls list
for roll in roll_options:
    print(f"  * {roll} beats {rules[roll]}.")
```

### 8.1 Exercise

Try writing a for loop that asks for our user's roll multiple times. This is will let our users play more than one round of rock-paper-scissors.

## 9. Functions

We've already seen a few examples of functions in the course so far. `input()` took input from the user, `print()` printed strings to the command line, and `random.choice()` selected a random value from a given list.

But one of the main benefits of programming is the ability to *write your own functions*. Even the functions above didn't exist at some point; someone had to write them.

Functions in Python are written with the following syntax:

```python
def my_function(input1):
    """
    This is where I say what the function does
    """
    # Write a whole bunch of stuff for this function to do
    pass
```

Since we've gotten the rolls from our user and the computer, we'll want to write a function to compare those two and decide which one wins.

```python
def compare_rolls(roll1, roll2):
    """
    This functions compares roll1 to roll2 to see which one wins

    :param roll1: The first roll
    :param roll2: The second roll
    :returns: String inidicating whether roll1 wins, loses, or ties
    """
    if rules[roll1] == roll2:
        outcome = 'win'
    elif roll1 == roll2:
        outcome = 'tie'
    else:
        outcome = 'lose'
    return outcome
```

### 9.1 Exercise

Write a function `print_header()` to print our welcome statement and the rules for the game. Hint: the function will not need any inputs and will not return anything.

## 10. Bringing it all together

Now it's time to bring everything we've learned together.

```python
import random

# Define rolls
roll_options = ['rock', 'paper', 'scissors']
# Define rules
rules = {
    'rock':'scissors',
    'paper':'rock',
    'scissors':'paper'
}

def print_header():
    """This functions prints the game header"""
    print('-------------------------------')
    print('Welcome to Rock-Paper-Scissors!\n')
    print('Here are the rules:')
    for key, value in rules.items():
        print(f"  * {key.title()} beats {value}.")

    print()

def compare_rolls(roll1, roll2):
    """
    This functions compares roll1 to roll2 to see which one wins

    :param roll1: The first roll
    :param roll2: The second roll
    :returns: String inidicating whether roll1 wins, loses, or ties
    """
    if rules[roll1] == roll2:
        outcome = 'win'
    elif roll1 == roll2:
        outcome = 'tie'
    else:
        outcome = 'lose'
    return outcome

def game_loop(player):
    print(f'Welcome, {player}!')
    # Play 5 games
    for i in range(1,6):
        print(f'Round {i}')
        player_roll = input(f"Choose your roll ({'/'.join(roll_options)}): ")
        computer_roll = random.choice(roll_options)
        outcome = compare_rolls(player_roll, computer_roll)
        print(f'{player} threw {player_roll}')
        print(f'The computer threw {computer_roll}')
        print(f'{player} {outcome}s!')
        print()

    print('Ending game...thanks for playing!')

if __name__ == '__main__':
    print_header()
    player = input("What's your name? ")
    game_loop(player)
```

The only new thing that we'll run into here is the line `if __name__ == '__main__':`. This line is telling us what to do if we run our program as a script. This is important, because we can also import the functions we've written into other programs we write.

Congratulations! You've written a complete program that plays several games of rock-paper-scissors with the user. If you're interested, here are some other ways you can improve our program:
* Add error handling to make sure the user inputs a valid choice.
* Let the player pick the number of games they want to play.
* Let the player type `quit` to quit the game.
* Add a scoreboard to keep track of who won how many games.=

https://github.com/bbig3831/introclass/wiki/Arlington-Library:-Intro-to-Programming-and-Python
