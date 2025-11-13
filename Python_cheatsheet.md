# PYTHON

## TABLE OF CONTENTS
1. Dictionaries
2. Strings
3. Arrays
4. Lists


## DICTIONARIES

- Dictionaries are used to store data values in key:value pairs.
- A dictionary is a collection which is ordered*, changeable and do not allow duplicates.

**NOTE:**
- As of Python version 3.7, dictionaries are ordered. In Python 3.6 and earlier, dictionaries are unordered.
- Dictionaries are written with curly brackets, and have keys and values:

- Example:
``` Python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
print(thisdict)
```

**Dictionary Items**
- Dictionary items are ordered, changeable, and do not allow duplicates.
- Dictionary items are presented in key:value pairs, and can be referred to by using the key name.
- Example:
``` Python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
print(thisdict["brand"])
```
**Output: Ford**


## Ordered or Unordered?

- As of Python version 3.7, dictionaries are ordered. In Python 3.6 and earlier, dictionaries are unordered.
- When we say that dictionaries are ordered, it means that the items have a defined order, and that order will not change.

- Unordered means that the items do not have a defined order, you cannot refer to an item by using an index.
 
## Changeable

- Dictionaries are changeable, meaning that we can change, add or remove items after the dictionary has been created.

## Duplicates Not Allowed

- Dictionaries cannot have two items with the same key:
``` python
 thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964,
  "year": 2020
}
print(thisdict) 
**Output: {'brand': 'Ford', 'model': 'Mustang', 'year': 2020}**
```

## The dict() Constructor

- It is also possible to use the dict() constructor to make a dictionary.

Using the dict() method to make a dictionary:
```python
thisdict = dict(name = "John", age = 36, country = "Norway")
print(thisdict)
**Output: {'name': 'John', 'age': 36, 'country': 'Norway'}**
```
# Accessing Items

- You can access the items of a dictionary by referring to its key name, inside square brackets:

- Example:
```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
x = thisdict["model"]
```

**The get() method**
- You can also use the get() method to access a dictionary item.

- Example:
```python 
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
x = thisdict.get("model")
print(x)
```
**Output: Mustang**

**Get Keys**

- The keys() method will return a list of all the keys in the dictionary.

Get a list of the keys:
```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
x = thisdict.keys() 
print(x)
```
**Output: dict_keys(['brand', 'model', 'year'])**
- The list of the keys is a view of the dictionary, meaning that any changes done to the dictionary will be reflected in the keys list.

## Change Values

- You can change the value of a specific item by referring to its key name:

- Example:
 Change the "year" to 2018:
 ```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict["year"] = 2018
print(thisdict)
```
**Output: {'brand': 'Ford', 'model': 'Mustang', 'year': 2018}**

**Update Dictionary**
- The update() method will update the dictionary with the items from the given argument.
- The argument must be a dictionary, or an iterable object with key:value pairs.

Example:Update the "year" of the car by using the update() method:
```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.update({"year": 2020}) 
print(thisdict)
```
**Output: {'brand': 'Ford', 'model': 'Mustang', 'year': 2020}**

**Removing Items**
- There are several methods to remove items from a dictionary:

- Example: 
The pop() method removes the item with the specified key name:
```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.pop("model")
print(thisdict) 
```
**Output: {'brand': 'Ford', 'year': 1964}**

- PopItem():
The popitem() method removes the last inserted item (in versions before 3.7, a random item is removed instead):

- Example:
```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.popitem()
print(thisdict)
```

**Output: {'brand': 'Ford', 'model': 'Mustang'}**

- del()
The del keyword removes the item with the specified key name:
```python
thisdict =	{
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
    }
del thisdict["model"]
print(thisdict)
```
**Output: {'brand': 'Ford', 'year': 1964}**

- clear()
The clear() method empties the dictionary:
```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.clear()
print(thisdict) 
```

**Loop Dictionaries**
- You can loop through a dictionary by using a for loop.
- When looping through a dictionary, the return value are the keys of the dictionary, but there are methods to return the values as well.

- Example:
```python
for x in thisdict:
  print(x)
  ```
- values()
You can also use the values() method to return values of a dictionary:
```python
for x in thisdict.values():
  print(x) 
```

- keys()
You can use the keys() method to return the keys of a dictionary:

```python
for x in thisdict.keys():
  print(x) 
```
- keys() and values()
- Loop through both keys and values, by using the items() method:
```python
for x, y in thisdict.items():
  print(x, y) 
```

## Copy a Dictionary

- You cannot copy a dictionary simply by typing dict2 = dict1, because: dict2 will only be a reference to dict1, and changes made in dict1 will automatically also be made in dict2.

- copy()
There are ways to make a copy, one way is to use the built-in Dictionary method copy().
 Make a copy of a dictionary with the copy() method:
 ```python
thisdict =	{
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
mydict = thisdict.copy()
print(mydict)
```

- dict()
Another way to make a copy is to use the built-in function dict().
Make a copy of a dictionary with the dict() function:
```python
thisdict =	{
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
    }
mydict = dict(thisdict)
print(mydict)
```
**Output: {'brand': 'Ford', 'model': 'Mustang', 'year': 1964}**

## Nested Dictionaries
- A dictionary can contain dictionaries, this is called nested dictionaries.
- Create a dictionary that contains three dictionaries:
```python
myfamily = {
    "child1": {
        "name": "Emil",
        "year": 2004
    },
    "child2": {
        "name": "Tobias",
        "year": 2007
    },
    "child3": {
        "name": "Linus",
        "year": 2011
    }
    }
print(myfamily)
```
**Output: {'child1': {'name': 'Emil', 'year': 2004}, 'child2': {'name': 'Tobias', 'year': 2007}, 'child3': {'name': 'Linus', 'year': 2011}}**

- You can also create a dictionary that contains dictionaries, by nesting three dictionaries into one:
```python
child1 = {
    "name": "Emil",
    "year": 2004
}
child2 = {
    "name": "Tobias",
    "year": 2007
}
child3 = {
    "name": "Linus",
    "year": 2011
}
myfamily = {
    "child1": child1,
    "child2": child2,
    "child3": child3
    }
print(myfamily)
```
**Output: {'child1': {'name': 'Emil', 'year': 2004}, 'child2': {'name': 'Tobias', 'year': 2007}, 'child3': {'name': 'Linus', 'year': 2011}}**

## Access Items in Nested Dictionaries

- To access items from a nested dictionary, you use the name of the dictionaries, starting with the outer dictionary:

- Print the name of child 2:
print(myfamily["child2"]["name"]) 
**Output: Tobias**

## Loop Through Nested Dictionaries

- You can loop through a dictionary by using the items() method like this:

Loop through the keys and values of all nested dictionaries:
```python
for x, obj in myfamily.items():
  print(x)
  for y in obj:
    print(y + ':', obj[y])
 ```

Output: child1
name: Emil
year: 2004
child2
name: Tobias
year: 2007
child3
name: Linus
year: 2011 

## Dictionary Methods Summary:

- Python has a set of built-in methods that you can use on dictionaries.

| **Method**      | **Description** |
|------------------|-----------------|
| `clear()`        | Removes all the elements from the dictionary |
| `copy()`         | Returns a copy of the dictionary |
| `fromkeys()`     | Returns a dictionary with the specified keys and value |
| `get()`          | Returns the value of the specified key |
| `items()`        | Returns a list containing a tuple for each key-value pair |
| `keys()`         | Returns a list containing the dictionary's keys |
| `pop()`          | Removes the element with the specified key |
| `popitem()`      | Removes the last inserted key-value pair |
| `setdefault()`   | Returns the value of the specified key. If the key does not exist, inserts the key with the specified value |
| `update()`       | Updates the dictionary with the specified key-value pairs |
| `values()`       | Returns a list of all the values in the dictionary |
  
# STRINGS

- Strings in python are surrounded by either single quotation marks, or double quotation marks.
- 'hello' is the same as "hello".
- You can display a string literal with the print() function:
Example: 
print("Hello")
print('Hello')

**Quotes Inside Quotes**

- You can use quotes inside a string, as long as they don't match the quotes surrounding the string:
Example:
```python
print("It's alright")
print("He is called 'Johnny'")
print('He is called "Johnny"')
```
**Multiline Strings**
- You can assign a multiline string to a variable by using three quotes:
Example:
```python
a = """Lorem ipsum dolor sit amet,
consectetur adipiscing elit,
sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua."""
print(a)
```
```
**Output: Lorem ipsum dolor sit amet,
consectetur adipiscing elit,
sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua.**
```
**Strings are Arrays**

- Like many other popular programming languages, strings in Python are arrays of unicode characters.
- However, Python does not have a character data type, a single character is simply a string with a length of 1.
- Square brackets can be used to access elements of the string.
Example:
Get the character at position 1 (remember that the first character has the position 0):
```python
a = "Hello, World!"
print(a[1])
```

**Looping Through a String**

- Since strings are arrays, we can loop through the characters in a string, with a for loop.
Example
- Loop through the letters in the word "banana":
```python
for x in "banana":
  print(x)
```

**String Length**
- To get the length of a string, use the len() function.
Example:
```python
a = "Hello, World!"
print(len(a))
```
**Output: 13**

**Check String**
- To check if a certain phrase or character is present in a string, we can use the
in keyword.
Example:
```python
txt = "The best things in life are free!"
print("free" in txt)
```
**Output: True**
- To check if a certain phrase or character is NOT present in a string, we can use the not in keyword.
Example:
```python
txt = "The best things in life are free!"
print("expensive" not in txt)
```
**Output: True**

**Slicing Strings**
- You can return a range of characters by using the slice syntax.
Example:
Get the characters from position 2 to position 5 (not included):
```python
b = "Hello, World!"
print(b[2:5])
```
**Output: llo**

- Slice from the start:
Example:
Get the characters from the start to position 5 (not included):
```python
b = "Hello, World!"
print(b[:5])
```
**Output: Hello**

- Slice to the end:
Example:
Get the characters from position 2, and all the way to the end:
```python
b = "Hello, World!"
print(b[2:])
```
**Output: llo, World!**

- Negative Indexing:
- Negative indexing means start from the end.
- -1 refers to the last character, -2 refers to the second last character, etc
Example:
Get the characters:
From position -5 to position -2 (not included):
```python
b = "Hello, World!"
print(b[-5:-2])
```
**Output: orl**

**Modify Strings**
- Strings are immutable, meaning that you cannot change parts of a string.
- But you can create a new string with the desired changes.
- Python has a set of built-in methods that you can use on strings.

- Replace String
Example:
- Change "H" to "J":
``` Python
a = "Hello, World!"
b = a.replace("H", "J")
print(b)
**Output: Jello, World!**
```
- Upper Case
Example:
- The upper() method returns the string in upper case:
```python
a = "Hello, World!"
print(a.upper())
```

- Lower Case
Example:
- The lower() method returns the string in lower case:
```python
a = "Hello, World!"
print(a.lower())
```

- Remove Whitespace

Whitespace is the space before and/or after the actual text, and very often you want to remove this space.
Example
- The strip() method removes any whitespace from the beginning or the end:
```python
a = " Hello, World! "
print(a.strip()) # returns "Hello, World!" 
```
- Split String

- The split() method returns a list where the text between the specified separator becomes the list items.
Example
- The split() method splits the string into substrings if it finds instances of the separator:
```python
a = "Hello, World!"
print(a.split(",")) # returns ['Hello', ' World!'] 
```

**String Concatenation**

- To concatenate, or combine, two strings you can use the + operator.
Example

Merge variable a with variable b into variable c:
```python
a = "Hello"
b = "World"
c = a + b
print(c)
```

**Format Strings**
- F-String was introduced in Python 3.6, and is now the preferred way of formatting strings.

- To specify a string as an f-string, simply put an f in front of the string literal, and add curly brackets {} as 
placeholders for variables and other operations.
- Example:
Create an f-string:
```python
age = 36
txt = f"My name is John, I am {age}"
print(txt)
```
**Output: My name is John, I am 36**

- Placeholders and Modifiers

A placeholder can contain variables, operations, functions, and modifiers to format the value.

- Example:
Add a placeholder for the price variable:
```python
price = 59
txt = f"The price is {price} dollars"
print(txt)
```
**Output: The price is 59 dollars**

- A placeholder can include a modifier to format the value.

- A modifier is included by adding a colon : followed by a legal formatting type, like .2f which means fixed point number with 2 decimals:
- Example:
Display the price with 2 decimals:
```python
price = 59
txt = f"The price is {price:.2f} dollars"
print(txt)
```

- A placeholder can contain Python code, like math operations:
- Perform a math operation in the placeholder, and return the result:
```python
txt = f"The price is {20 * 59} dollars"
print(txt)
```

**Escape Character**
- To insert characters that are illegal in a string, use an escape character.
- An escape character is a backslash \ followed by the character you want to insert.

To fix this problem, use the escape character \":
Example:
- The escape character allows you to use double quotes when you normally would not be allowed:

```python
txt = "We are the so-called \"Vikings\" from the north."
print(txt)
```
**Output: We are the so-called "Vikings" from the north.**

**String Methods**
| **Method**            | **Description**                         | **Example**                          |
|------------------------|------------------------------------------|--------------------------------------|
| `upper()`              | Converts to uppercase                    | `"hello".upper()` → `"HELLO"`        |
| `lower()`              | Converts to lowercase                    | `"HELLO".lower()` → `"hello"`        |
| `title()`              | Capitalizes first letter of each word    | `"python guide".title()`             |
| `capitalize()`         | Capitalizes first character              | `"hello".capitalize()`               |
| `strip()`              | Removes whitespace                       | `" hi ".strip()`                     |
| `replace(old, new)`    | Replaces substring                       | `"hi".replace("h", "H")`             |
| `split(sep)`           | Splits string into list                  | `"a,b,c".split(",")`                 |
| `join(iterable)`       | Joins list into string                   | `",".join(['a','b','c'])`            |
| `startswith(sub)`      | Checks prefix                            | `"Python".startswith("Py")`          |
| `endswith(sub)`        | Checks suffix                            | `"file.txt".endswith(".txt")`        |
| `find(sub)`            | Returns index of substring               | `"hello".find("e")`                  |
| `count(sub)`           | Counts occurrences                       | `"banana".count("a")`                |

# ARRAYS

| **Method**   | **Description** |
|---------------|-----------------|
| `append()`    | Adds an element at the end of the list |
| `clear()`     | Removes all the elements from the list |
| `copy()`      | Returns a copy of the list |
| `count()`     | Returns the number of elements with the specified value |
| `extend()`    | Adds the elements of a list (or any iterable) to the end of the current list |
| `index()`     | Returns the index of the first element with the specified value |
| `insert()`    | Adds an element at the specified position |
| `pop()`       | Removes the element at the specified position |
| `remove()`    | Removes the first item with the specified value |
| `reverse()`   | Reverses the order of the list |
| `sort()`      | Sorts the list in ascending order by default |
**Note:**
- Python does not have built-in support for Arrays, but Python Lists can be used instead.
- Arrays are used to store multiple values in one single variable.
Example:
```python
a = [1, "Hello", [3.14, "world"]]
a.append(2)  # Add an integer to the end
print(a)
```

**Array Methods**

- Python has a set of built-in methods that you can use on lists/arrays.


# LIST
- Lists are used to store multiple items in a single variable.
- Lists are created using square brackets:
```python
thislist = ["apple", "banana", "cherry"]
print(thislist)
```
**Output: ['apple', 'banana', 'cherry']**

List Methods

Python has a set of built-in methods that you can use on lists.

| **Method** | **Description** |
|-------------|-----------------|
| `append()`  | Adds an element at the end of the list |
| `clear()`   | Removes all the elements from the list |
| `copy()`    | Returns a copy of the list |
| `count()`   | Returns the number of elements with the specified value |
| `extend()`  | Adds the elements of another list (or any iterable) to the end of the current list |
| `index()`   | Returns the index of the first element with the specified value |
| `insert()`  | Adds an element at the specified position |
| `pop()`     | Removes the element at the specified position |
| `remove()`  | Removes the item with the specified value |
| `reverse()` | Reverses the order of the list |
| `sort()`    | Sorts the list in ascending order by default |


References:
- https://www.w3schools.com/python/python_dictionaries.asp
- https://www.w3schools.com/python/python_strings.asp
- https://www.w3schools.com/python/python_lists.asp
- https://www.w3schools.com/python/python_arrays.asp
- https://www.youtube.com/watch?v=2IsF7DEtVjg

