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

```
# Prompt the user to enter a number
user_input = raw_input("Enter a number")

# Generate a random number between 1 and 10
random_number = random.randint(1, 10)
```

In these functions, we can see the inputs (inside the parentheses), and the output stored in the variables user_input and random_number respectively. But how do we know what functions exist and what their inputs/outputs are? The answer is documentation.

The link below is the official documentation for the random module:

[Random documentation](https://docs.python.org/2/library/random.html)

And scrolling down, we can find our randint function:

```
random.randint(a, b)
Return a random integer N such that a <= N <= b.
```

As we can see, this documentation shows the number of inputs expected as well as the output of the function. Looking through the rest of documentation we can see all of the other functions in the random module as well as descriptions of their inputs and outputs. 

### 1.1 Optional inputs
Looking at some other functions on the random page we see sometimes the inputs to the functions are in brackets:

```
random.randrange(start, stop[, step])
Return a randomly selected element from range(start, stop, step). This is equivalent to choice(range(start, stop, step)), but doesn’t actually build a range object.
```

In this case, the 'step' input is optional, and if none is given a default value is used. The default value is one in this case (it's not very well documented on the random site) but in other documentation it should be clear what the default value is in the documentation.

The Python website has documentation for all of it's built in functionality, and in general external modules will have their own documentation to allow users to understand the functionality provided with the module.

## 2. Lists 
A list in Python is like a variable, but instead of storing a single value it stores multiple values. Lists are defined using the square brackets as seen below:

```
# Define an empty list
test_list = []
```

In this case, since there's nothing inside the square brackets the list is empty. In order for the list to have values, we can add values when we define it:

```
# Define a list pre-populated with values
test_list = ['a', 'b', 'c']
```

Now we have a list that contains the letters 'a', 'b', and 'c'. To get information out of a list, you simply use the name of the list and the position in the list that we want. One important thing to understand about Python is that when referencing item's in a list, Python starts counting at zero rather than one. This means, to get the first item in our list, we use the code:

```
# Get the first item in the list
first_item = test_list[0]

print(first_item)
```

The number 0 in the square brackets indicate that we want the first item in the list. Some additional examples are shown below.

```
# Print values in the list
print(test_list[0]) # This will print 'a', because 'a' is the first item in the list
print(test_list[1]) # This will print 'b', because 'b' is the second item in the list
print(test_list[2]) # This will print 'c', because 'c' is the third item in the list
```

In order to determine the number of items in a list, we can use the 'len' function:

```
# Print the length of the list
print(len(test_list))
```

We see that the length of 3 is printed.

### 2.1 Altering Lists

Lists can be populated with data when they are created as we saw above, but it's also possible to add data to lists after they've been created. The list below shows a few functions that are useful for altering lists:

```
test_list.append('d') # Add an item to the end of the list
test_list.remove('a') # Remove an item from the list
test_list.insert(0, 'a') # Insert an item into a list, where the first input is the index to insert the item
```

More information on lists can be found on the Python website [here](https://docs.python.org/3/tutorial/datastructures.html)

### 2.2 Lists and For Loops
For loops are a useful way to access data in a list in an ordered fashion. The code below steps through a list and prints out each item:

```
# Loop through the items in a list
for i in range(len(test_list)):
    print(test_list[i])
```

We can see that running this code prints out the items in our list in order. One thing to note, for the range() function, if only one input is given, the first input is assumed to be zero. For loops can be used in a slightly simpler way with list using the syntax below:

```
# Loop through the items in a list, part two
for item in test_list:
    print(item)
```

This functions the same was as the loop above but is a little cleaner to work with.

### 2.3 Additional list functions
In addition to the functionality covered above, there are a couple more useful things to know with regards to lists:

The 'in' operator determines whether an item is in a list:

```
# Define a list pre-populated with values
test_list = ['a', 'b', 'c']

# Check if 'a' is in the list
if 'a' in test_list:
    print('Item is in list')
```
This allows us to quickly check whether or not an item is in a list.

Another useful function for lists is the 'index' function. Given a list and a value, the index function will give you the first index of that item in the list:

```
# Define a list pre-populated with values
test_list = ['a', 'b', 'c']

# Get the index of 'b' in the list
print(test_list.index('b'))
```

Finally, a function that we'll use later is the split function. When called on a string, it splits the string into a list using the given separator. For example, if we have a comma separated string, we can use the code below to split it into a list object:

```
# Import the string module
import string

# Define our comma separated string
comma_string = 'a,b,c'

# Split the string into a list
string_list = string.split(comma_string, ',')

# Display the resulting list
print(string_list)
```
This can be very helpful and is something we'll use in the exercises later.

## 3. Dictionaries
Lists are useful for storing multiple pieces of data in a specific order, but there are other ways to store multiple pieces of data that can be more useful. For example, imagine storing names and phone numbers for multiple people. Using lists, it may look something like this:

```
nameList = ['Joe', 'Josephine', 'Jose']
phoneNumberList = ['111-111-1111', '222-222-2222', '333-333-3333']
```
In order to find Jose's phone number you would need to step through nameList, determine the index of 'Jose', then pull the item from phoneNumberList to determine the phone number. For situations like this, Python has an easier solution called a dictionary:

```
# Define an empty dictionary
phoneNumberDict = {}

# Populate the dictionary with keys and values
phoneNumberDict['Joe'] = '111-111-1111'
phoneNumberDict['Josephine'] = '222-222-2222'
phoneNumberDict['Jose'] = '333-333-3333'
```

Dictionaries allow you relate data in what's called a key-value pair. What this means is a certain key (in this case the name) is associated with a certain value (in this case a phone number). To access the data associated with a certain key, you use the syntax below:

```
# Print the value associated with the key 'Joe'
print(phoneNumberDict['Joe'])
```

The code above prints the value associated with the key 'Joe'. The code below shows how to determine the all of the keys in a dictionary as well as their associated values.

```
# Display all keys and values in a dictionary
for key in phoneNumberDict.keys():
    print(key + ':' + phoneNumberDict[key])
```

In this case, phoneNumberDict.keys() returns a list of the keys in the dictionary and we step through it using the for loop. To loop through values, the code below can be used:

```
# Display all values in a dictionary
for val in phoneNumberDict.values():
    print(val)
```

More information on dictionaries can be found on the Python website [here](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

## 4. File input/output
Being able to read/write to a file is another fundamental skill in programming. The 'open' function is the primary function used in reading from and writing to files. 'open' takes in two arguments, the name of the file and the mode for which we're using the file, typically either read ('r') or write ('w'), and returns a 'file' object.

```
# Open the file
f = open('test_file.txt', 'w')

# Display the file object
print(f)

# Write text into our file
f.write('This is our test text')

# Close the file
f.close()
```

This will write the text 'This is our test text' to the file 'test_file.txt' and save it. Once the file is written, we can access it again using the open function. The snippet of code below shows a second way to read from a file. It's not as intuitive but doesn't require us to close the file when we're done with it:

```
# Open the file
with open('test_file.txt', 'r') as f:
    # Read the file contents
    file_contents = f.read()

# Display the contents of the file
print(file_contents)
```
Running this, we see the text 'This is our test text' displayed. This text was read from the file we created.

Another useful function to know is the 'readlines()' function. This returns a list where each item in the list is a single line in the file: 

```
# Open the file
with open('test_file.txt', 'r') as f:
    # Read the contents of the file into a list
    file_contents = f.readlines()

# Loop through the list of lines
for line in f.readlines():
    # Print each line
    print(line)
```

Information on how to read/write from files can be found on the Python website [here](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)

## 4.1 Operating system functions
Above we were able to create a file and write data to it, but how do we know where that data is saved? Python provides the ability to interact with our operating system, from simple things like listing the current working directory and the files in it to creating directories, moving files around, and running system commands. The code below prints the current working directory and the list of files in th
at directory

```
# The os package is included with Python by default but isn't automatically imported, so we have to import it now
import os

# Print the current working directory
print(os.getcwd())

# Print the contents of the directory we're working in. 
print(os.listdir())
```

In the list of items in the directory, we can see the test file we just created. 

More information on user defined functions can be found on the Python website [here](https://docs.python.org/3/library/os.html)

## 5. Exception Handling
In the exercises we've worked so far, whenever we've come across an error our program has stopped completely and an error has been displayed. This can be frustrating as sometimes, an error doesn't necessarily mean the rest of the program can't run. Luckily, Python has functionality that allows for errors to be 'caught' and handled accordingly. Below is an example of something called a try...except statement:

```
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

Running the code above, we see 'Exception Caught' printed as well as the output of the error message. Finally, we see the text 'Finished Script' printed, meaning that the code didn't stop when the exception occurred. This is a simple example of a try catch statement but understanding how they work is essential for many coding tasks, especially in cases where you may be unsure of the data you're working with. When querying a website or reading a new file, try...except statements allow you to handle problems in the data without completely halting your script. 

More information on error handling can be found on the Python website [here](https://docs.python.org/3/tutorial/errors.html)

## 6. User defined functions
We spoke briefly about functions in the previous course but they're worth revisiting as they are foundational in modern programming. 

As mentioned, a function can generally be recognized by parentheses as in the print() function or the input() function. To expand on how functions work, we can talk about inputs and outputs. Inputs to functions, also called arguments, are data passed in to the function that the function uses. Outputs are any data returned to the user once the function is complete. 

A good way to understand how exactly functions work is to create one of our own. For simplicity, we'll create a function that adds two numbers together and gives the user the total. In Python we do this using the following syntax:

```
# Define a new function
def addition(number_one, number_two):
    # Add the two inputs together
    total = number_one + number_two
    
    # Return the total
    return total
```

In the code above we see the input arguments, in this case 'number_one' and 'number_two'. The next line of code adds the two values together, and the third line returns the total value to the user. Now we can use this function as we would any other function:

```
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

Running this code, what do we see? This function does exactly what the '+' symbol does but it allows us to see how functions are defined and how they work. 

Functions can be as simple or complex as needed, and can take in as many arguments and return as many outputs as needed. 

More information on user defined functions can be found on the Python website [here](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)

## 7. Pulling data from a website
Querying a website can be very complex but luckily Python has a module that makes it simple to do a basic query of a website. The module we'll be using is called the 'requests' module, and the primary function we'll use is the 'get' function:

```
# Import the requests module
import requests

# Ping the website
response = requests.get("https://www.google.com")

# Display the response
print(response)
```
This response is a standard HTTP response, with 200 meaning the request was successful. If for some reason the request number was different we could find what different responses mean online but the response code isn't really what we want, we want the content of the site. We can get this using the 'text' property of the response:

```
# Print the contents of the website
print(response.text)
```
This displays the HTML representation of the website. This by itself isn't too useful to look at but it's a good example of how simple it can be to pull information from a website. In a later example we'll see how this can be used more effectively.

More information on the 'requests' module can be found [here]
http://docs.python-requests.org/en/master/user/quickstart/

## 8. Advanced Example
This section has a sample that uses the concepts we learned above to create some more complex scripts that could be useful.

Prior to the class I uploaded a text document with 2000 wine reviews to this website. We can use the 'requests' module to download that document and access the data inside, at which point we can do some simple exploration of the data:

```
import requests

# Query the site where the data is stored. In general when accessing external systems, a try statement is needed in case there are any unforseen issues with the external system
try:
    response = requests.get('https://raw.githubusercontent.com/jeheidrich/introclass/master/wine_reviews.txt')
except Exception as e:
    # If an error occurs, display the error
    print('Error querying website: ' + str(e))
    # Since we failed to load the data, there's no point in the script continuing so we use the 'quit' function to terminate the program
    quit()

# Get the text from the response
wine_data = response.text

# Write the data to a local file for later use
with open('wine_data.txt', 'w') as f:
    f.write(wine_data)

# The data is currently one long string. We could re-read the data by opening the file and using the 'readlines()' function but since we already have the data in 'wine_data' we can use the 'split()' function on the string. The '\n' is a newline character, like a return. Splitting with it will split the data into lines. Before we split into lines, there's an extra newline character at the end of the file that we want to get rid of which we'll use the 'strip()' function to do, which removes a specific character from the start and end of a string.
wine_data = wine_data.strip('\n')
wine_data = wine_data.split('\n')

# The first line in this dataset contains the column names, so we want to store that separately
headers = wine_data[0].split('|')

print(headers)
```

With the headers displayed, we can think about what kind of information we want to get from the data. A simple first step would be to count the number of wines in the set from the United States:

```
# Initialize our count variable
united_states_count = 0

# Loop through the rest of the data, starting at 1 instead of zero to skip the header line
for i in range(1, len(wine_data)):
    # Get the line from the data and split it into a list
    line = wine_data[i]

    split_line = line.split('|')

    # From the headers, we know that the country is the second item (index 1) in the list after the line number:
    country = split_line[1]

    # Check if country is United States
    if country == 'US':
        # If so, add to our counter
        united_states_count = united_states_count + 1

# Display the total number of wines
print("Total wines from the US: " + str(united_states_count))
```

If we wanted to quickly know which lines were from which country, we could create a dictionary to store that information:
```
# Initialize our dictionary
country_dict = {}

# Loop through the rest of the data, starting at 1 instead of zero to skip the header line
for i in range(1, len(wine_data)):
    # Get the line from the data and split it into a list
    line = wine_data[i]

    split_line = line.split('|')

    # From the headers, we know that the country is the second item (index 1) in the list after the line number:
    country = split_line[1]

    # Check to see if the country is already a key in the dictionary and if not, add it and add an empty list as it's value
    if not country in country_dict.keys():
        country_dict[country] = []

    # Append the row number to the country dictionary entry
    country_dict[country].append(i)

# Display all of the countries and the number of rows each country has
for k in country_dict.keys():
    print(k + ' : ' + str(len(country_dict[k])))
```

These custom scripts are useful, but there are a lot of similarities between the last two examples. When you start seeing patterns like that in coding, that's a good time to pause and think, 'Is there a way I can generalize this to make my life easier?' In this case, we can write a function that 'queries' the data for us and then just use that function:

```
# Query a given set of data
def query_data(data, headers, query_column_name, query_column_value, return_column_name):
    # Determine the column index of the query column and the return column
    query_column_idx = headers.index(query_column_name)
    return_column_idx = headers.index(return_column_name)

    # Initialize our empty return list
    return_list = []

    # Loop through the data
    for line in data:
        split_line = line.split('|')
        
        # Check if query column matches the query value
        if split_line[query_column_idx] == query_column_value:
            # If query column matches query value, add return column value to the return list
            return_list.append(split_line[return_column_idx])

    # Return the final list
    return return_list

# Query the data using our new function
nz_wine_types = query_data(wine_data, headers, 'country', 'New Zealand', 'variety')

# Display the results of the query
print(nz_wine_types)

# Query the data using our new function
greek_wineries = query_data(wine_data, headers, 'country', 'Greece', 'winery')

# Display the results of the query
print(greek_wineries)
```

The scripts above are some basic examples of how Python can be used to pull data from a website, write it to your computer, and provide some statistics about the data. The concepts outlined can be applied to all sorts of programming tasks. The links below contain some other examples of how Python can be used to complete all sorts of other tasks.

https://www.geeksforgeeks.org/python-programming-examples/

https://www.pythonforbeginners.com/code-snippets-source-code/python-code-examples

