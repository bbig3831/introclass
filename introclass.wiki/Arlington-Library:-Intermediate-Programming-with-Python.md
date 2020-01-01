The URL for the course syllabus is: https://github.com/bbig3831/introclass/wiki/Arlington-Library:-Intermediate-Programming-with-Python

The purpose of this course is to build upon the concepts taught in the intro course and cover more advanced but still fundamental concepts in Python as well as programming in general. By the end of the class students will hopefully have enough knowledge to write basic programs as well as understand documentation enough to learn more on their own. The class will cover the following topics:
* Documentation
* Lists
* Dictionaries
* Exception Handling
* File Input/Output
* Operating System Functions
* User Defined Functions
* Pulling data from websites
* Advanced Example

These sections will contain basic snippets of code and some minor examples to show students how the code might look. At the end of the lesson, we'll go over some more in-depth examples to understand how these concepts can be combined to do some powerful things.

To follow along with the example code, you can use the following site:

[Replit Python](https://repl.it/languages/python3)

## 1. Python documentation
We discussed functions briefly in the previous course but they're worth revisiting now that we know a little more. Functions are pieces of code that take in data, called inputs, perform some function, and return data to the user, called outputs. Functions can be recognized by their parentheses and a couple functions we've used so far are:

```python
# Prompt the user to enter a number
user_input = raw_input("Enter a number")

# Generate a random number between 1 and 10
random_number = random.randint(1, 10)
```

In these functions, we can see the inputs (inside the parentheses), and the output stored in the variables `user_input` and `random_number` respectively. But how do we know what functions exist and what their inputs/outputs are? The answer is documentation.

The link below is the official documentation for the `random` module:

[Random documentation](https://docs.python.org/2/library/random.html)

And scrolling down, we can find our `randint` function:

```python
random.randint(a, b)
Return a random integer N such that a <= N <= b.
```

As we can see, this documentation shows the number of inputs expected as well as the output of the function. Looking through the rest of documentation we can see all of the other functions in the `random` module as well as descriptions of their inputs and outputs.

### 1.1 Optional inputs
Looking at some other functions on the `random` page we see sometimes the inputs to the functions are in brackets:

> random.randrange(start, stop[, step])
>
> Return a randomly selected element from range(start, stop, step). This is equivalent to choice(range(start, stop, step)), but doesn’t actually build a range object.


In this case, the `step` input is optional, and if none is given a default value is used. The default value is one in this case (it's not very well documented on the `random` site) but in other documentation it should be clear what the default value is in the documentation.

The Python website has documentation for all of its built in functionality, and in general external modules will have their own documentation to allow users to understand the functionality.

## 2. File input/output
Being able to read/write to a file is another fundamental skill in programming. The `open` function is the primary function used in reading from and writing to files. `open` takes in two arguments, the name of the file and the mode for which we're using the file, typically either read (`r`) or write (`w`), and returns a `file` object.

```python
# Open the file
f = open('test_file.txt', 'w')

# Display the file object
print(f)

# Write text into our file
f.write('This is our test text')

# Close the file
f.close()
```

This will write the text `This is our test text` to the file `test_file.txt` and save it. Once the file is written, we can access it again using the `open()` function. The snippet of code below shows a second way to read from a file. By using Python's **context manager**, we don't have to close the file when we're done with it.

```python
# Open the file
with open('test_file.txt', 'r') as f:
    # Read the file contents
    file_contents = f.read()

# Display the contents of the file
print(file_contents)
```
Running this, we see the text `This is our test text` displayed. This text was read from the file we created.

Information on how to read/write from files can be found on the Python website [here](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)

## 2.1 Operating system functions
Above we were able to create a file and write data to it, but how do we know where that data is saved? Python provides the ability to interact with our operating system, from simple things like listing the current working directory and the files in it to creating directories, moving files around, and running system commands. The code below prints the current working directory and the list of files in th
at directory

```python
# The os package is included with Python by default but isn't automatically imported, so we have to import it now
import os

# Print the current working directory
print(os.getcwd())

# Print the contents of the directory we're working in.
print(os.listdir())
```

In the list of items in the directory, we can see the test file we just created.

More information on user defined functions can be found on the Python website [here](https://docs.python.org/3/library/os.html)

## 2.2 Exercise

Using the `os` module, the `os.path.join()` function, and the context manager, write a Python script that opens up the `wine_reviews.txt` file in the `data` directory and stores it in a variable called `wine_data`. Try it yourself before checking the solution!

### Solution
```python
import os

# Set path variables
base_dir = os.getcwd()
data_file = os.path.join(base_dir,'data','wine_reviews.txt')

# Store wine data to variable
with open(data_file, 'r') as my_file:
    wine_data = my_file.read()

# Print first 100 characters
print(wine_data[0:100])
```

## 3. Lists
A list in Python is like a variable, but instead of storing a single value it stores multiple values. Lists are defined using the square brackets as seen below:

```python
# Define an empty list
test_list = []
```

In this case, since there's nothing inside the square brackets the list is empty. In order for the list to have values, we can add values when we define it:

```python
# Define a list pre-populated with values
test_list = ['a', 'b', 'c']
```

Now we have a list that contains the letters `a`, `b`, and `c`. To get information out of a list, you simply use the name of the list and the position in the list that we want. One important thing to understand about Python is that when referencing item's in a list, Python starts counting at zero rather than one.

```python
# Get the first item in the list
first_item = test_list[0]
second_item = test_list[1]

print(first_item)
print(second_item)
```

In order to determine the number of items in a list, we can use the `len` function:

```python
# Print the length of the list
print(len(test_list))
```

We see that the length of 3 is printed.

### 3.1 Altering Lists

Lists can be populated with data when they are created as we saw above, but it's also possible to add data to lists after they've been created. The list below shows a few **methods** that are useful for altering lists.

```python
test_list.append('d') # Add an item to the end of the list
test_list.remove('a') # Remove an item from the list
test_list.insert(0, 'a') # Insert an item into a list, where the first input is the index to insert the item
```

More information on lists can be found on the Python website [here](https://docs.python.org/3/tutorial/datastructures.html)

Notice that we referred to `append()`, `remove()`, and `insert()` as **methods**, not functions. What's the difference? In general, functions take some input and return an output. Inputs to functions, also called arguments, are data passed into the function that the function uses. Outputs are any data returned to the user once the function is complete.

Methods, however, act on **objects**, usually by either "getting" something from the object or "setting" something for the object. In the example above, we changed the `test_list` object by adding the letter `d`.

### 3.2 Lists and For Loops
For loops are a useful way to access data in a list in an ordered fashion. The code below steps through a list and prints out each item.

```python
# Loop through the items in a list, part two
for item in test_list:
    print(item)
```

Python is pretty smart, and it knows how to handle lists in a `for` loop when it sees one. This allows its syntax to be concise and easy to read.

### 3.3 Additional list functions
In addition to the functionality covered above, there are a couple more useful things to know with regards to lists:

The `in` operator determines whether an item is in a list:

```python
# Define a list pre-populated with values
test_list = ['a', 'b', 'c']

# Check if 'a' is in the list
if 'a' in test_list:
    print('Item is in list')
```

Another useful method for lists is the `index()` method. Given a list and a value, the `index()` method will give you the first index of that item in the list:

```python
# Define a list pre-populated with values
test_list = ['a', 'b', 'c']

# Get the index of 'b' in the list
print(test_list.index('b'))
```

Another function that we'll use later is the `split()` function. When called on a string, it splits the string into a list using the given separator. For example, if we have a comma separated string, we can use the code below to split it into a list object:

```python
# Define our comma separated string
comma_string = 'a,b,c'

# Split the string into a list
string_list = comma_string.split(',')

# Display the resulting list
print(string_list)
```

The `enumerate()` function allows us to access an item in a list as well as its index inside a `for` loop.

```python
test_list = ['a','b','c']
for idx, val in enumerate(test_list):
    print("Index {}: {}".format(idx, val))
```

## 3.4 Combining lists and files


Another useful function to know is the `readlines()` function. This returns a list where each item in the list is a single line in the file. We can use it in combination with a `for` list to examine the beginning of a file.

```python
# Open the file
with open('test_file.txt', 'r') as f:
    # Read the contents of the file into a list
    file_contents = f.readlines()

# Loop through the list of lines
for idx, line in enumerate(file_contents, start=1):
    # Print each line
    print(f"Line #{idx}: {line}")
```

Here we used a new feature in Python 3 called a **formatted string literal** to make our `print()` statement real clean. Read more about formatted string literals, or **f-strings**, here: https://docs.python.org/3/reference/lexical_analysis.html#formatted-string-literals

## 3.5 Sets

In Python, a `set` is a data type that is similar to a `list`, but it only stores **unique** items. Converting between the two is easy, and the following snippet will show the difference between the data structures.

```python
test_list = ['1','1','2','2','3','3']
test_set = set(test_list)
print(test_list)
print(test_set)
print(type(test_set))
print(list(test_set))
```

## 3.6 Exercise

Building on our exercise above to do two things:
1. Print the column headers for `wine_reviews.txt`.
2. Print the first 5 lines of `wine_reviews.txt` to show what the data looks like.

### Solution

```python
import os

# Set path variables
base_dir = os.getcwd()
data_file = os.path.join(base_dir,'data','wine_reviews.txt')

# Store wine data to variable
with open(data_file, 'r') as my_file:
    wine_data = my_file.readlines()

# Print headers
header_cols = wine_data[0].split('|')
for idx, col in enumerate(header_cols):
    print(f"Column {idx} - {col}")

# Print example lines - remember to skip the header!
for line in wine_data[1:10]:
    print(line)
```

## 4. Dictionaries
Lists are useful for storing multiple pieces of data in a specific order, but there are other ways to store multiple pieces of data that can be more useful. For example, imagine storing names and phone numbers for multiple people. Using lists, it may look something like this:

```python
nameList = ['Joe', 'Josephine', 'Jose']
phoneNumberList = ['111-111-1111', '222-222-2222', '333-333-3333']
```
In order to find Jose's phone number you would need to step through `nameList`, determine the index of `Jose`, then pull the item from `phoneNumberList` to determine the phone number. (Assuming they're in the same spot!) For situations like this, Python has a better data structure called a dictionary.

```python
# Define an empty dictionary
phoneNumberDict = {}

# Populate the dictionary with keys and values
phoneNumberDict['Joe'] = '111-111-1111'
phoneNumberDict['Josephine'] = '222-222-2222'
phoneNumberDict['Jose'] = '333-333-3333'
```

Dictionaries allow you relate data in what's called a key-value pair. What this means is a certain key (in this case the name) is associated with a certain value (in this case a phone number). If they are the same length, you can also create a dictionary from two lists by using the `zip()` and `dict()` functions.

```python
nameList = ['Joe', 'Josephine', 'Jose']
phoneNumberList = ['111-111-1111', '222-222-2222', '333-333-3333']
phoneNumberDict = dict(zip(nameList, phoneNumberList))
```

To access the data associated with a certain key, you use key indexes or the `get()` method.

```python
# Print the value associated with the key 'Joe' via indexing
print(phoneNumberDict['Joe'])
# Via the get() method
print(phoneNumberDict.get('Joe'))
```

The code above prints the value associated with the key `Joe`. The code below shows how to determine the all of the keys in a dictionary as well as their associated values.

```python
# Display all keys and values in a dictionary
for key in phoneNumberDict.keys():
    print(key + ':' + phoneNumberDict[key])

# Display all values in a dictionary
for val in phoneNumberDict.values():
    print(val)
```

However, Python is pretty smart and we can actually access both keys and values at the same time using the `items()` method.

```python
for key, val in phoneNumberDict.items():
    print(f"{key}: {val}")
```

More information on dictionaries can be found on the Python website [here](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)


## 5. Exception Handling
In the exercises we've worked so far, whenever we've come across an error our program has stopped completely and an error has been displayed. This can be frustrating as sometimes, an error doesn't necessarily mean the rest of the program can't run. Luckily, Python has functionality that allows for errors to be "caught" and handled accordingly. Below is an example of something called a try-catch or `try...except` statement:

```python
# Try statement
try:
    # This will cause an error because 'test_variable' is not defined
    print(test_variable)
# Catch the exception
except Exception as err:
    # Display the error
    print('Exception Caught')
    print(err)

# Display finished
print('Finished Script')
```

Running the code above, we see `Exception Caught` printed as well as the output of the error message. Finally, we see the text `Finished Script` printed, meaning that the code didn't stop when the exception occurred. This is a simple example of a try-catch statement but understanding how they work is essential for many coding tasks, especially in cases where you may be unsure of the data you're working with. When querying a website or reading a new file, `try...except` statements allow you to handle problems in the data without completely halting your script.

More information on error handling can be found on the Python website [here](https://docs.python.org/3/tutorial/errors.html)

## 5.1 Exercise

In the exercise for this section, we're going to read in the data file as before and then summarize some of the data. We'll combine what we've learned in previous sections and learn a new way of constructing dictionaries or lists, called a **comprehension**.

### Solution

```python
import os

# Set path variables
base_dir = os.getcwd()
data_file = os.path.join(base_dir,'data','wine_reviews.txt')

# Store wine data in a variable
try:
    with open(data_file, 'r') as my_file:
        wine_data = my_file.readlines()

except Exception as e:
    print("File was not found!")
    print(e)
    quit()

# Print headers
header_cols = wine_data[0].split('|')
for idx, col in enumerate(header_cols):
    print(f"Column {idx} - {col}")

# Group wine data by country
country_dict = {}
for line in wine_data[1:]:
    vals = line.split('|')
    country = vals[1]
    if not country_dict.get(country):
        country_dict[country] = []
        country_dict[country].append(vals[-2])
    else:
        country_dict[country].append(vals[-2])

# Get unique wine varietals using dictionary comprehension
country_dict = {country:list(set(wines)) for country, wines in country_dict.items()}

# Print summary
print("Summary of wine varieties")
for country, wines in country_dict.items():
    print(f"\nCountry: {country}")
    print('\t- '+','.join(wines))
```

## 6. User defined functions
We spoke briefly about functions in the previous course but they're worth revisiting as they are foundational in modern programming. A good way to understand how exactly functions work is to create one of our own. For simplicity, we'll create a function that adds two numbers together and gives the user the total. In Python we do this using the following syntax:

```python
# Define a new function
def addition(number_one, number_two):
    # Add the two inputs together
    total = number_one + number_two

    # Return the total
    return total
```

In the code above we see the input arguments, in this case `number_one` and `number_two`. The next line of code adds the two values together, and the third line returns the total value to the user. Now we can use this function as we would any other function:

```python
# Define a new function
def addition(number_one, number_two):
    # Add the two inputs together
    total = number_one + number_two

    # Return the total
    return total

# Call the new function
total = addition(5, 10)

# Print the total
print(total)
```

Running this code, what do we see? This function does exactly what the `+` symbol does but it allows us to see how functions are defined and how they work.

Functions can be as simple or complex as needed, and can take in as many arguments and return as many outputs as needed.

More information on user defined functions can be found on the Python website [here](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)

## 6.1 Exercise

For this exercise, let's try writing a function called `summarize_data()` so that we can summarize any column of data by another column.

### Solution

```python
import os

def summarize_data(data_set, groupby_col, grouped_col):
    summary_dict = {}
    for line in data_set[1:]:
        vals = line.split('|')
        groupby_key = vals[groupby_col]
        grouped_val = vals[grouped_col]
        if not summary_dict.get(groupby_key):
            summary_dict[groupby_key] = []
            summary_dict[groupby_key].append(grouped_val)
        else:
            summary_dict[groupby_key].append(grouped_val)
    summary_dict = {key: list(set(val)) for key, val in summary_dict.items()}
    return summary_dict

# Set path variables
base_dir = os.getcwd()
data_file = os.path.join(base_dir,'data','wine_reviews.txt')

# Store wine data in a variable
try:
    with open(data_file, 'r') as my_file:
        wine_data = my_file.readlines()

except Exception as e:
    print("File was not found!")
    print(e)
    quit()

# Print headers
header_cols = wine_data[0].split('|')
for idx, col in enumerate(header_cols):
    print(f"Column {idx} - {col}")

# Get columns to summarize
groupby_col = input("Which column do you want to group by? ")
grouped_col = input("Which column do you want to summarize? ")

# Summarize data
summary_dict = summarize_data(wine_data, int(groupby_col), int(grouped_col))

# Print summary
print("Summary")
for key, val_list in summary_dict.items():
    print(f"\nKey: {key}")
    print('\t- '+', '.join(val_list))
```

## 7. Pulling data from a website
Querying a website can be very complex but luckily Python has a module that makes it simple to do a basic query of a website. The module we'll be using is called the `requests` module, and the primary function we'll use is the `get` function:

```python
# Import the requests module
import requests

# Ping the website
response = requests.get("https://www.google.com")

# Display the response
print(response)
```
This response is a standard HTTP response, with `200` meaning the request was successful. If for some reason the request number was different we could find what different responses mean online but the response code isn't really what we want, we want the content of the site. We can get this using the `text` property of the response:

```python
# Print the contents of the website
print(response.text)
```
This displays the HTML representation of the website. This by itself isn't too useful to look at but it's a good example of how simple it can be to pull information from a website. In a later example we'll see how this can be used more effectively.

More information on the `requests` module can be found here.
http://docs.python-requests.org/en/master/user/quickstart/

## 7.1 Exercise

Instead of using the data we already have, let's try to write a function that retrieves our data from the internet.

```python
import os
import requests

def download_data(url, output_path):
    try:
        response = requests.get(url)
    except Exception as e:
        print('Error querying website: ' + str(e))
        quit()
    data = response.text
    with open(output_path, 'w') as myfile:
        myfile.write(data)

url = 'https://raw.githubusercontent.com/bbig3831/introclass/master/data/wine_reviews.txt'
output_path = os.path.join(os.getcwd(),'data','new_wine_data.txt')
download_data(url, output_path)
```

## 8. Advanced Example

This is an advanced example that combines everything we've learned to create an interactive query tool for users.

```python
import os
import requests

def download_data(url, output_path):
    """
    Utility function for downloading data
    :param url: URL for data to download
    :param output_path: Output file path for storing data
    """
    try:
        response = requests.get(url)
    except Exception as e:
        print('Error querying website: ' + str(e))
        quit()
    data = response.text
    with open(output_path, 'w') as myfile:
        myfile.write(data)

def read_data(output_path):
    """Read in wine data"""
    try:
        with open(output_path, 'r') as my_file:
            wine_data = my_file.readlines()

    except Exception as e:
        print("File was not found!")
        print(e)
        quit()
    return wine_data

def summarize_data(data_set, groupby_col, grouped_col):
    """
    Function for summarizing data
    """
    summary_dict = {}
    for line in data_set[1:]:
        vals = line.split('|')
        groupby_key = vals[groupby_col]
        grouped_val = vals[grouped_col]
        if not summary_dict.get(groupby_key):
            summary_dict[groupby_key] = []
            summary_dict[groupby_key].append(grouped_val)
        else:
            summary_dict[groupby_key].append(grouped_val)
    summary_dict = {key: list(set(val)) for key, val in summary_dict.items()}
    return summary_dict

def gameplay(data_path):
    # Read in data
    wine_data = read_data(data_path)
    while True:
        user_input = input("Keep playing or exit? (Type 'quit' to exit) ")
        if user_input.lower() == 'quit':
            quit()
        else:
            # Print headers
            header_cols = wine_data[0].split('|')
            for idx, col in enumerate(header_cols):
                print(f"Column {idx} - {col}")

            # Get columns to summarize
            groupby_col = input("Which column do you want to group by? ")
            grouped_col = input("Which column do you want to summarize? ")

            # Summarize data
            summary_dict = summarize_data(wine_data, int(groupby_col), int(grouped_col))

            # Print summary
            print("Summary")
            for key, val_list in summary_dict.items():
                print(f"\nKey: {key}")
                print('\t- '+', '.join(val_list))

url = 'https://raw.githubusercontent.com/bbig3831/introclass/master/data/wine_reviews.txt'
output_path = os.path.join(os.getcwd(),'new_wine_data.txt')
download_data(url, output_path)

gameplay(output_path)
```

The scripts we've written above provide some basic examples of how Python can be used to pull data from a website, write it to your computer, and provide some statistics about the data. The concepts outlined can be applied to all sorts of programming tasks. The links below contain some other examples of how Python can be used to complete all sorts of other tasks.

https://www.geeksforgeeks.org/python-programming-examples/

https://www.pythonforbeginners.com/code-snippets-source-code/python-code-examples
