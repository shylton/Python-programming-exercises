# 100+ Python challenging programming exercises for Python 3

## 1. Level description
### Level 1	Beginner 
Beginner means someone who has just gone through an introductory Python course. He can solve some problems with 1 or 2 Python classes or functions. Normally, the answers could directly be found in textbooks or online.

### Level 2	Intermediate 
Intermediate means someone who has just learned Python, but already has a relatively strong programming background from before. He should be able to solve problems which may involve 3 or 3 Python classes or functions. The answers cannot be directly be found in textbooks or online.

### Level 3	Advanced. 
He should use Python to solve more complex problem using more rich libraries functions and data structures and algorithms. He is supposed to solve the problem using several Python standard packages and advanced techniques.

----

## 2. Problem template

Question
Hints
Solution

----

## 3. Questions

### Question 1 - Level 1

Write a program which will find the numbers between 2000 and 3200 (both included) which are divisible by 7 but not a multiple of 5.
The numbers obtained should be printed in a comma-separated sequence on a single line.

Hints: 
Consider use range(#begin, #end) method

<details>
<summary>Show Solution</summary>

```python
# solution 1
l = []
for i in range(2000, 3201):
    if (i % 7 == 0) and (i % 5 != 0):
        l.append(str(i))

print(','.join(l))

# better solution. Uses less memory by not creating a list
for i in range(2000, 3201):
    if i % 7 == 0 and i % 5 != 0:
        print(i, end=', ')
print()  # print a newline
```
</details>


### Question 1b - Level 1

Question:
Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”.

Hints: 
Consider use range(#begin, #end) method

<details>
<summary>Show Solution</summary>

```python
for i in range(1, 101):
    if i % 3 == 0 and i % 5 == 0:
        print('FizzBuzz')
    elif i % 5 == 0:
        print('Buzz')
    elif i % 3 == 0:
        print('Fizz')
    else:
        print(i)
```
</details>

### Question 2 - Level 1

Write a function to compute the factorial of a given integer.
Suppose the following input is supplied to the program:
8
Then, the output should be:
40320

<details>
<summary>Show Solution</summary>

```python
# iterative solution
def factorial_iterative(integer):
    assert type(integer) == int and integer > -1, 'input must be a non ' \
                                                 'negative integer'

    if integer == 0 or integer == 1:
        return 1

    result = integer
    for i in range(integer - 1, 1, -1):
        result *= i

    return result


# recursive solution
def factorial_recursive(integer):
    assert type(integer) == int and integer > -1, 'input must be a non ' \
                                                 'negative integer'

    if integer == 0:
        return 1
    return integer * factorial_recursive(integer - 1)

# test the functions
for x in [0, 1, 2, 3, 4, 8, -1]:
    print(f'{x}! is', factorial_iterative(x), factorial_recursive(x))

```
</details>

### Question 3 - Level 1

With a given integer n, write a function to generate the dictionary with key = n and values = n*n for all from 1 to n inclusive. Then print the dictionary.
Suppose the following input is supplied to the program:
8
Then, the output should be:
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64}

Hints:
Consider use dict(), consider use the pprint module from the standard library

<details>
<summary>Show Solution</summary>

```python
# solution 1
n = int(input())
d = dict()
for i in range(1, n+1):
    d[i] = i*i

print(d)

# solution 2
from pprint import pprint

def squares_dict(integer):
    assert type(integer) == int and integer > -1, 'input must be a non ' \
                                                  'negative integer'
    return {i: i**2 for i in range(1, integer + 1)}

# test the function
pprint(squares_dict(20))
pprint(squares_dict('a'))
```
</details>

### Question 4 - Level 1

Write a program which accepts a sequence of comma-separated strings from console and generate a list and a tuple which contains every value.
Suppose the following input is supplied to the program:
34,67,bacon,spam,eggs,33
Then, the output should be:
['34', '67', 'bacon', 'spam', 'eggs', '33']
('34', '67', 'bacon', 'spam', 'eggs', '33')

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
tuple() method can convert list to tuple

<details>
<summary>Show Solution</summary>

```python
values = input('Type comma separated values without spaces,'
               ' then hit [ENTER] => ')
val_list = values.split(",")
val_tuple = tuple(val_list)
print(val_list)
print(val_tuple)
```
</details>

### Question 5 - Level 1

Define a class which has two methods:
get_string: to get a string from console input
print_string: to print the string in upper case
Also please include simple test function to test the class methods.

<details>
<summary>Show Solution</summary>

```python
class InputOutString:
    def __init__(self):
        self.string = ""

    def get_string(self):
        self.string = input('type the string then hit [ENTER] ')

    def print_string(self):
        print(self.string.upper())


str_obj = InputOutString()
str_obj.get_string()
str_obj.print_string()
```
</details>

### Question 6 - Level 2

Write a program that calculates and prints the value according to the given formula:
Q = Square root of [(2 * C * D)/H]
Following are the fixed values of C and H:
C is 50. H is 30.
D is the variable whose values should be input to your program in a comma-separated sequence.
Example
Let us assume the following comma separated input sequence is given to the program:
100,150,180
The output of the program should be:
18,22,24

Hints:
If the output received is in decimal form, it should be rounded off to its nearest value (for example, if the output received is 26.0, it should be printed as 26)
In case of input data being supplied to the question, it should be assumed to be a console input. 

<details>
<summary>Show Solution</summary>

```python
import math
c = 50
h = 30
values = []
items = [x for x in input().split(',')]
for d in items:
    values.append(str(int(round(math.sqrt(2*c*float(d)/h)))))

print(','.join(values))
```
</details>

### Question 7 - Level 2

Write a program which takes 2 numbers, i and j as input and generates a 2-dimensional array. The element value in the i-th row and j-th column of the array should be i*j.
Note: i=0,1 ... i-1; j=0,1 ... j-1.
Example. Suppose the following inputs are given to the program:
3,5
Then, the output of the program should be:
[[0, 0, 0, 0, 0], [0, 1, 2, 3, 4], [0, 2, 4, 6, 8]] 

<details>
<summary>Show Solution</summary>

```python
# solution 1
input_str = input('enter "rows,columns" then press [ENTER]: ')
dimensions = [int(x) for x in input_str.split(',')]
rowNum = dimensions[0]
colNum = dimensions[1]
multilist = [[0 for col in range(colNum)] for row in range(rowNum)]

for row in range(rowNum):
    for col in range(colNum):
        multilist[row][col]= row*col

print(multilist)

# better solution
from pprint import pprint
def gen_2d_array(rows, columns):
    """generates a 2d array where each element is row * column starting with
    0x0
    :param rows: the number of rows
    :param columns: the number of columns
    :return:
    """
    assert type(rows) == type(columns) == int, 'inputs must be integers'

    return [[row * col for col in range(columns)] for row in range(rows)]

pprint(gen_2d_array(5,5))
```
</details>

### Question 8 - Level 2

Write a program that accepts a comma separated sequence of words as input and prints the words in a comma-separated sequence after sorting them alphabetically.
Suppose the following input is supplied to the program:
without,hello,bag,world
Then, the output should be:
bag,hello,without,world

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
items = [x for x in input('enter comma separated list of words: ').split(',')]
items.sort()
print(','.join(items))
```
</details>

### Question 9 - Level 2

Write a program that accepts sequence of lines as input and prints the lines after making all characters in the sentence capitalized.
Suppose the following input is supplied to the program:
Hello world
Practice makes perfect
Then, the output should be:
HELLO WORLD
PRACTICE MAKES PERFECT

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
lines = []
while True:
    s = input()
    if s:
        lines.append(s.upper())
    else:
        break

for sentence in lines:
    print(sentence)
```
</details>

### Question 10 - Level 2

Write a program that accepts a sequence of whitespace separated words as input and prints the words sorted and without duplicates.
Suppose the following input is supplied to the program:
hello world and practice makes perfect and hello world again
Then, the output should be:
again and hello makes perfect practice world

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
Use set container to remove duplicated data automatically and then use sorted() to sort the data.

<details>
<summary>Show Solution</summary>

```python
s = input('enter space separated list => ')
print(sorted(set(s.split(' '))))
```
</details>

### Question 11 - Level 2

Write a program which accepts a sequence of comma separated 4 digit binary numbers as its input and then check whether they are divisible by 5 or not. The numbers that are divisible by 5 are to be printed in a comma separated sequence.
Example:
0100,0011,1010,1001
Then the output should be:
1010
Notes: Assume the data is input by console.

<details>
<summary>Show Solution</summary>

```python
value = []
items = [x for x in input().split(',')]
for p in items:
    intp = int(p, 2)
    if not intp % 5:
        value.append(p)

print(','.join(value))
```
</details>

### Question 12 - Level 2

Write a program that prints the comma separated list of numbers between 0 and 100 (inclusive) that has all even digits.

<details>
<summary>Show Solution</summary>

```python
def is_even(x):
    # using bitwise AND which is faster than modulo
    if int(x) & 1:
        return False
    else:
        return True

for i in range(101):
    if all(map(is_even, str(i))):
        print(i, end=', ')
print()
```
</details>

### Question 13 - Level 2

Write a program that accepts a sentence and calculate the number of letters and digits.
Suppose the following input is supplied to the program:
hello world! 123
Then, the output should be:
LETTERS 10
DIGITS 3

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
string = input('input => ')
dictio = {"DIGITS":0, "LETTERS":0}
for c in string:
    if c.isdigit():
        dictio["DIGITS"]+=1
    elif c.isalpha():
        dictio["LETTERS"]+=1

print("LETTERS", dictio["LETTERS"])
print("DIGITS", dictio["DIGITS"])
```
</details>

### Question 14 - Level 2

Write a program that accepts a sentence and calculate the number of upper case letters and lower case letters.
Suppose the following input is supplied to the program:
Hello world!
Then, the output should be:
UPPER CASE 1
LOWER CASE 9

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
string = input()
dictio ={"UPPER CASE":0, "LOWER CASE":0}
for c in string:
    if c.isupper():
        dictio["UPPER CASE"] += 1
    elif c.islower():
        dictio["LOWER CASE"] += 1

print("UPPER CASE", dictio["UPPER CASE"])
print("LOWER CASE", dictio["LOWER CASE"])
```
</details>

### Question 15 - Level 2

Question:
Write a program that computes the value of a+aa+aaa+aaaa with a given digit as the value of a.
Suppose the following input is supplied to the program:
9
Then, the output should be:
11106

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
a = input()
n1 = int( "%s" % a )
n2 = int( "%s%s" % (a,a) )
n3 = int( "%s%s%s" % (a,a,a) )
n4 = int( "%s%s%s%s" % (a,a,a,a) )
print(n1+n2+n3+n4)
```
</details>

### Question 16 - Level 2

Use a list comprehension to square each odd number in a list. 
Suppose the following list is supplied to the program:
[1,2,3,4,5,6,7,8,9]
Then, the output should be:
[1, 9, 25, 49, 81]

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
old_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
new_list = [x**2 for x in old_list if x % 2 != 0]
print(new_list)
```
</details>

### Question 17 - Level 2

Write a program that simulates a bank account ledger. The transaction log format is shown as following:
credit 100
debit 50

<details>
<summary>Show Solution</summary>

```python
def is_number(x):
    try:
        float(x)
        return True
    except ValueError:
        return False


class BankLedger:
    def __init__(self):
        self.balance = 0

    def credit(self, amount):
        if is_number(amount):
            self.balance += amount
        else:
            print('ERROR, input must be a number value')

    def debit(self, amount):
        if is_number(amount):
            if self.balance - amount < 0:
                print(f'Not enough balance to withdraw {amount}')
            else:
                self.balance -= amount
        else:
            print('ERROR, input must be a number value')

    def get_balance(self):
        print('Current Balance:', self.balance)

    def transaction(self):
        trans = input('type transaction => ').split(' ')
        # validate input
        if trans[0].lower() in ['exit', 'quit', 'end']:
            return False  # force exit
        if len(trans) != 2:
            print('usage: [debit/credit] [amount]')
            return True
        elif trans[0].lower() not in ['credit', 'c', 'debit', 'd']:
            print('first argument must be "credit" or "debit"')
            return True
        elif not is_number(trans[1]):
            print('second argument must be a number')
            return True
        elif float(trans[1]) < 0:
            print('second argument must be a positive number')
            return True
        else:
            if trans[0].lower() in ['credit', 'c']:
                self.credit(float(trans[1]))
            if trans[0].lower() in ['debit', 'd']:
                self.debit(float(trans[1]))
            return True

        print('this should not ever be printed!')


def main():
    my_acct = BankLedger()
    run = True
    print('usage: [debit/credit] [amount]')
    print('type "exit" to end program execution')
    # start loop, show current balance
    while run:
        my_acct.get_balance()  # print current balance
        run = my_acct.transaction()  # post a transaction / terminate program


# run the program
main()

```
</details>

### Question 18 - Level 3

Write a function to detect if a given string is a strong password.
Eight or more characters. Both upper and lowecase. One or more digits.

<details>
<summary>Show Solution</summary>

```python
import re

def strong_psw(psw, verbose=False):
    """ uses regex to determine if passed string is a strong password.
        Eight or more characters. Both upper and lowecase. One or more digits.
        source: https://automatetheboringstuff.com/2e/chapter7/
        @param psw: string to be checked
        @param verbose: boolean: True returns string on error
        @return boolean: True if psw is strong, False or error string otherwise

        >>> strong_psw('bob')
        False
        >>> strong_psw(1234)  # not string
        Traceback (most recent call last):
        ...
        ValueError: arg must be a string
        >>> strong_psw('AuntMary12345')
        True
        >>> strong_psw('nouppercasecharshere')
        False
        >>> print(strong_psw('1234567890', True))
        must have upper case letter

    """
    if type(psw) != str:
        raise ValueError('arg must be a string')

    # REFACTOR: these can be combined with lookahead, but cleaner this way
    psw_check1 = re.compile('.{8,}')    # 8 or more anything in length
    psw_check2 = re.compile('[A-Z]+')   # one or more upper case
    psw_check3 = re.compile('[a-z]+')   # one or more lower case
    psw_check4 = re.compile(r'\d+')     # one or more digits

    if verbose:
        if psw_check1.search(psw) is None:
            return 'password must be longer than 8'
        if psw_check2.search(psw) is None:
            return 'must have upper case letter'
        if psw_check3.search(psw) is None:
            return 'must have lower case letter'
        if psw_check4.search(psw) is None:
            return 'must have at least one digit'
        return True
    else:
        test = bool(psw_check1.search(psw)) and bool(psw_check2.search(psw)) \
            and bool(psw_check3.search(psw)) and bool(psw_check4.search(psw))
        return test
```
</details>

### Question 19 - Level 3

You are required to write a program to sort the (name, age, height) tuples by ascending order where name is string, age and height are numbers. The tuples are input by console. The sort criteria is:
1: Sort based on name;
2: Then sort based on age;
3: Then sort by score.
The priority is that name > age > score.
If the following tuples are given as input to the program:
Tom,19,80
John,20,90
Jony,17,91
Jony,17,93
Json,21,85
Then, the output of the program should be:
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
We use itemgetter to enable multiple sort keys.

<details>
<summary>Show Solution</summary>

```python
from operator import itemgetter, attrgetter

l = []
while True:
    s = input()
    if not s:
        break
    l.append(tuple(s.split(",")))

print(sorted(l, key=itemgetter(0,1,2)))
```
</details>

### Question 20
Level 3

Question:
Define a class with a generator which can iterate the numbers, which are divisible by 7, between a given range 0 and n.

Hints:
Consider use yield

<details>
<summary>Show Solution</summary>

```python
def putNumbers(n):
    i = 0
    while i<n:
        j=i
        i=i+1
        if j%7==0:
            yield j

for i in reverse(100):
    print(i)
```
</details>

### Question 21
Level 3

Question
A robot moves in a plane starting from the original point (0,0). The robot can move toward UP, DOWN, LEFT and RIGHT with a given steps. The trace of robot movement is shown as the following:
UP 5
DOWN 3
LEFT 3
RIGHT 2
¡­
The numbers after the direction are steps. Please write a program to compute the distance from current position after a sequence of movement and original point. If the distance is a float, then just print the nearest integer.
Example:
If the following tuples are given as input to the program:
UP 5
DOWN 3
LEFT 3
RIGHT 2
Then, the output of the program should be:
2

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
import math
pos = [0,0]
while True:
    s = input()
    if not s:
        break
    movement = s.split(" ")
    direction = movement[0]
    steps = int(movement[1])
    if direction=="UP":
        pos[0]+=steps
    elif direction=="DOWN":
        pos[0]-=steps
    elif direction=="LEFT":
        pos[1]-=steps
    elif direction=="RIGHT":
        pos[1]+=steps
    else:
        pass

print(int(round(math.sqrt(pos[1]**2+pos[0]**2))))
```
</details>

### Question 22
Level 3

Question:
Write a program to compute the frequency of the words from the input. The output should output after sorting the key alphanumerically. 
Suppose the following input is supplied to the program:
New to Python or choosing between Python 2 and Python 3? Read Python 2 or Python 3.
Then, the output should be:
2:2
3.:1
3?:1
New:1
Python:5
Read:1
and:1
between:1
choosing:1
or:2
to:1

Hints
In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
freq = {}   # frequency of words in text
line = input()
for word in line.split():
    freq[word] = freq.get(word,0)+1

words = freq.keys()
words.sort()

for w in words:
    print("%s:%d" % (w,freq[w]))
```
</details>

### Question 23
level 1

Question:
Write a method which can calculate square value of number

Hints:
Using the ** operator

<details>
<summary>Show Solution</summary>

```python
def square(num):
    return num ** 2

print(square(2))
print(square(3))
```
</details>

### Question 24
Level 1

Question:

Python has many built-in functions, and if you do not know how to use it, you can read document online or find some books. But Python has a built-in document function for every built-in functions.

Please write a program to print some Python built-in functions documents, such as abs(), int(), raw_input()

And add document for your own function
Hints:
The built-in document method is __doc__

<details>
<summary>Show Solution</summary>

```python
print(abs.__doc__)
print(int.__doc__)
print(input.__doc__)

def square(num):
    '''Return the square value of the input number.
    
    The input number must be integer.
    '''
    return num ** 2

print(square(2))
print(square.__doc__)
```
</details>
### Question 25
Level 1

Question:
Define a class, which have a class parameter and have a same instance parameter.

Hints:
Define a instance parameter, need add it in __init__ method
You can init a object with construct parameter or set the value later

<details>
<summary>Show Solution</summary>

```python
class Person:
    # Define the class parameter "name"
    name = "Person"
    
    def __init__(self, name = None):
        # self.name is the instance parameter
        self.name = name

jeffrey = Person("Jeffrey")
print("%s name is %s" % (Person.name, jeffrey.name))

nico = Person()
nico.name = "Nico"
print("%s name is %s" % (Person.name, nico.name))
```
</details>

### Question 26:
Define a function which can compute the sum of two numbers.

Hints:
Define a function with two numbers as arguments. You can compute the sum in the function and return the value.

<details>
<summary>Show Solution</summary>

```python
def SumFunction(number1, number2):
	return number1+number2

print(SumFunction(1,2))
```
</details>

### Question 27
Define a function that can convert a integer into a string and print it in console.

Hints:

Use str() to convert a number to string.

<details>
<summary>Show Solution</summary>

```python
def printValue(n):
    print(str(n))

printValue(3)
```
</details>

### Question 28
Define a function that can convert a integer into a string and print it in console.

Hints:

Use str() to convert a number to string.

<details>
<summary>Show Solution</summary>

```python
def printValue(n):
    print(str(n))

printValue(3)
```
</details>

### Question 29
Define a function that can receive two integral numbers in string form and compute their sum and then print it in console.

Hints:

Use int() to convert a string to integer.

<details>
<summary>Show Solution</summary>

```python
def printValue(s1,s2):
    print(int(s1)+int(s2))

printValue("3","4")
```
</details>

### Question 30
Define a function that can accept two strings as input and concatenate them and then print it in console.

Hints:

Use + to concatenate the strings

<details>
<summary>Show Solution</summary>

```python
def printValue(s1,s2):
    print(s1+s2)

printValue("3","4") #34
```
</details>

### Question 31
Define a function that can accept two strings as input and print the string with maximum length in console. If two strings have the same length, then the function should print al l strings line by line.

Hints:

Use len() function to get the length of a string

<details>
<summary>Show Solution</summary>

```python
def printValue(s1,s2):
    len1 = len(s1)
    len2 = len(s2)
    if len1>len2:
        print(s1)
    elif len2>len1:
        print(s2)
    else:
        print(s1)
        print(s2)
        
printValue("one","three")

```
</details>

### Question 32
Define a function that can accept an integer number as input and print the "It is an even number" if the number is even, otherwise print "It is an odd number".

Hints:

Use % operator to check if a number is even or odd.

<details>
<summary>Show Solution</summary>

```python
def checkValue(n):
    if n%2 == 0:
        print("It is an even number")
    else:
        print("It is an odd number")
        
checkValue(7)
```
</details>

### Question 33
Define a function which can print a dictionary where the keys are numbers between 1 and 3 (both included) and the values are square of keys.

Hints:

Use `dict[key]=value` pattern to put entry into a dictionary.
Use ** operator to get power of a number.

<details>
<summary>Show Solution</summary>

​```python
def printDict():
    d=dict()
    d[1]=1
    d[2]=2**2
    d[3]=3**2
    print(d)
        
printDict()
```

</details>

### Question 34
Define a function which can print a dictionary where the keys are numbers between 1 and 20 (both included) and the values are square of keys.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.
Use range() for loops.

<details>
<summary>Show Solution</summary>
```python
def printDict():
	d=dict()
	for i in range(1,21):
		d[i]=i**2
	print(d)

printDict()
```
</details>

### Question 35
Define a function which can generate a dictionary where the keys are numbers between 1 and 20 (both included) and the values are square of keys. The function should just print the values only.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.
Use range() for loops.
Use keys() to iterate keys in the dictionary. Also we can use item() to get key/value pairs.

<details>
<summary>Show Solution</summary>

```python
def printDict():
	d=dict()
	for i in range(1,21):
		d[i]=i**2
	for (k,v) in d.items():	
		print(v)

printDict()
```
</details>

### Question 36
Define a function which can generate a dictionary where the keys are numbers between 1 and 20 (both included) and the values are square of keys. The function should just print the keys only.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.
Use range() for loops.
Use keys() to iterate keys in the dictionary. Also we can use item() to get key/value pairs.

<details>
<summary>Show Solution</summary>

```python
def printDict():
	d=dict()
	for i in range(1,21):
		d[i]=i**2
	for k in d.keys():	
		print(k)

printDict()
```
</details>

### Question 37
Define a function which can generate and print a list where the values are square of numbers between 1 and 20 (both included).

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.

<details>
<summary>Show Solution</summary>

```python
def printList():
	li=list()
	for i in range(1,21):
		li.append(i**2)
	print(li)

printList()
```
</details>
### Question 38
Define a function which can generate a list where the values are square of numbers between 1 and 20 (both included). Then the function needs to print the first 5 elements in the list.

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use [n1:n2] to slice a list

<details>
<summary>Show Solution</summary>

```python
def printList():
	li=list()
	for i in range(1,21):
		li.append(i**2)
	print(li[:5])

printList()
```
</details>

### Question 39
Define a function which can generate a list where the values are square of numbers between 1 and 20 (both included). Then the function needs to print the last 5 elements in the list.

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use [n1:n2] to slice a list

<details>
<summary>Show Solution</summary>

```python
def printList():
	li=list()
	for i in range(1,21):
		li.append(i**2)
	print(li[-5:])

printList()
```
</details>
### Question 40
Define a function which can generate a list where the values are square of numbers between 1 and 20 (both included). Then the function needs to print all values except the first 5 elements in the list.

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use [n1:n2] to slice a list

<details>
<summary>Show Solution</summary>

```python
def printList():
	li=list()
	for i in range(1,21):
		li.append(i**2)
	print li[5:]

printList()
```
</details>

### Question 41
Define a function which can generate and print a tuple where the value are square of numbers between 1 and 20 (both included). 

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use tuple() to get a tuple from a list.

<details>
<summary>Show Solution</summary>

```python
def printTuple():
	li=list()
	for i in range(1,21):
		li.append(i**2)
	print(tuple(li))
		
printTuple()
```
</details>
### Question 42
With a given tuple (1,2,3,4,5,6,7,8,9,10), write a program to print the first half values in one line and the last half values in one line. 

Hints:

Use [n1:n2] notation to get a slice from a tuple.

<details>
<summary>Show Solution</summary>

```python
tp=(1,2,3,4,5,6,7,8,9,10)
tp1=tp[:5]
tp2=tp[5:]
print(tp1)
print(tp2)
```
</details>

### Question 43
Write a program to generate and print another tuple whose values are even numbers in the given tuple (1,2,3,4,5,6,7,8,9,10). 

Hints:

Use "for" to iterate the tuple
Use tuple() to generate a tuple from a list.

<details>
<summary>Show Solution</summary>

```python
tp=(1,2,3,4,5,6,7,8,9,10)
li=list()
for i in tp:
	if tp[i]%2==0:
		li.append(tp[i])

tp2=tuple(li)
print(tp2)
```
</details>

### Question 44
Write a program which accepts a string as input to print "Yes" if the string is "yes" or "YES" or "Yes", otherwise print "No". 

Hints:

Use if statement to judge condition.

<details>
<summary>Show Solution</summary>

```python
s= raw_input()
if s=="yes" or s=="YES" or s=="Yes":
    print "Yes"
else:
    print "No"
```
</details>

### Question 45
Write a program which can filter even numbers in a list by using filter function. The list is: [1,2,3,4,5,6,7,8,9,10].

Hints:

Use filter() to filter some elements in a list.
Use lambda to define anonymous functions.

<details>
<summary>Show Solution</summary>

```python
li = [1,2,3,4,5,6,7,8,9,10]
evenNumbers = filter(lambda x: x%2==0, li)
print(evenNumbers)
```
</details>

### Question 46
Write a program which can map() to make a list whose elements are square of elements in [1,2,3,4,5,6,7,8,9,10].

Hints
Use map() to generate a list.
Use lambda to define anonymous functions.

<details>
<summary>Show Solution</summary>

```python
li = [1,2,3,4,5,6,7,8,9,10]
squaredNumbers = map(lambda x: x**2, li)
print(squaredNumbers)
```
</details>

### Question 47
Write a program which can map() and filter() to make a list whose elements are square of even number in [1,2,3,4,5,6,7,8,9,10].

Hints
Use map() to generate a list.
Use filter() to filter elements of a list.
Use lambda to define anonymous functions.

<details>
<summary>Show Solution</summary>

```python
li = [1,2,3,4,5,6,7,8,9,10]
evenNumbers = map(lambda x: x**2, filter(lambda x: x%2==0, li))
print(evenNumbers)
```
</details>

### Question 48
Write a program which can filter() to make a list whose elements are even number between 1 and 20 (both included).

Hints:

Use filter() to filter elements of a list.
Use lambda to define anonymous functions.

<details>
<summary>Show Solution</summary>

```python
evenNumbers = filter(lambda x: x%2==0, range(1,21))
print(evenNumbers)
```
</details>

### Question 49
Write a program which can map() to make a list whose elements are square of numbers between 1 and 20 (both included).

Hints
Use map() to generate a list.
Use lambda to define anonymous functions.

<details>
<summary>Show Solution</summary>

```python
squaredNumbers = map(lambda x: x**2, range(1,21))
print(squaredNumbers)
```
</details>

### Question 50
Define a class named American which has a static method called printNationality.

Hints:
Use @staticmethod decorator to define class static method.

<details>
<summary>Show Solution</summary>

```python
class American(object):
    @staticmethod
    def printNationality():
        print("America")

anAmerican = American()
anAmerican.printNationality()
American.printNationality()
```
</details>

### Question 51
Define a class named American and its subclass NewYorker. 

Hints:

Use class Subclass(ParentClass) to define a subclass.

<details>
<summary>Show Solution</summary>

```python
class American(object):
    pass

class NewYorker(American):
    pass

anAmerican = American()
aNewYorker = NewYorker()
print(anAmerican)
print(aNewYorker)
```
</details>

### Question 52
Define a class named Circle which can be constructed by a radius. The Circle class has a method which can compute the area. 

Hints:

Use def methodName(self) to define a method.

<details>
<summary>Show Solution</summary>

```python
class Circle(object):
    def __init__(self, r):
        self.radius = r

    def area(self):
        return self.radius**2*3.14

aCircle = Circle(2)
print aCircle.area()
```
</details>

### Question 53
Define a class named Rectangle which can be constructed by a length and width. The Rectangle class has a method which can compute the area. 

Hints:

Use def methodName(self) to define a method.

<details>
<summary>Show Solution</summary>

```python
class Rectangle(object):
    def __init__(self, l, w):
        self.length = l
        self.width  = w

    def area(self):
        return self.length*self.width

aRectangle = Rectangle(2,10)
print(aRectangle.area())
```
</details>

### Question 54
Define a class named Shape and its subclass Square. The Square class has an init function which takes a length as argument. Both classes have a area function which can print the area of the shape where Shape's area is 0 by default.

Hints:

To override a method in super class, we can define a method with the same name in the super class.

<details>
<summary>Show Solution</summary>

```python
class Shape(object):
    def __init__(self):
        pass

    def area(self):
        return 0

class Square(Shape):
    def __init__(self, l):
        Shape.__init__(self)
        self.length = l

    def area(self):
        return self.length*self.length

aSquare= Square(3)
print(aSquare.area())
```
</details>

### Question 55
Please raise a RuntimeError exception.

Hints:

Use raise() to raise an exception.

<details>
<summary>Show Solution</summary>

```python
raise RuntimeError('something wrong')
```
</details>

### Question 56
Write a function to compute 5/0 and use try/except to catch the exceptions.

Hints:

Use try/except to catch exceptions.

<details>
<summary>Show Solution</summary>

```python
def throws():
    return 5/0

try:
    throws()
except ZeroDivisionError:
    print("division by zero!")
except Exception, err:
    print('Caught an exception')
finally:
    print('In finally block for cleanup')
```
</details>

### Question 57
Define a custom exception class which takes a string message as attribute.

Hints:

To define a custom exception, we need to define a class inherited from Exception.

<details>
<summary>Show Solution</summary>

```python
class MyError(Exception):
    """My own exception class

    Attributes:
        msg  -- explanation of the error
    """
    
    def __init__(self, msg):
        self.msg = msg

error = MyError("something wrong")
```
</details>

### Question 58
Assuming that we have some email addresses in the "username@companyname.com" format, please write program to print the user name of a given email address. Both user names and company names are composed of letters only.

Example:
If the following email address is given as input to the program:

john@google.com

Then, the output of the program should be:

john

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:

Use \w to match letters.

<details>
<summary>Show Solution</summary>

```python
import re
emailAddress = raw_input()
pat2 = "(\w+)@((\w+\.)+(com))"
r2 = re.match(pat2,emailAddress)
print(r2.group(1))
```
</details>

### Question 59
Assuming that we have some email addresses in the "username@companyname.com" format, please write program to print the company name of a given email address. Both user names and company names are composed of letters only.

Example:
If the following email address is given as input to the program:

john@google.com

Then, the output of the program should be:

google

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:

Use \w to match letters.

<details>
<summary>Show Solution</summary>

```python
import re
emailAddress = raw_input()
pat2 = "(\w+)@(\w+)\.(com)"
r2 = re.match(pat2,emailAddress)
print(r2.group(2))
```
</details>

### Question 60
Write a program which accepts a sequence of words separated by whitespace as input to print the words composed of digits only.

Example:
If the following words is given as input to the program:

2 cats and 3 dogs.

Then, the output of the program should be:

['2', '3']

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:

Use re.findall() to find all substring using regex.

<details>
<summary>Show Solution</summary>

```python
import re
s = raw_input()
print(re.findall("\d+",s))
```
</details>

### Question 61
Print a unicode string "hello world".

Hints:

Use u'strings' format to define unicode string.

<details>
<summary>Show Solution</summary>

```python
unicodeString = u"hello world!"
print(unicodeString)
```
</details>

### Question 62
Write a program to read an ASCII string and to convert it to a unicode string encoded by utf-8.

Hints:

Use unicode() function to convert.

<details>
<summary>Show Solution</summary>

```python
s = input()
u = unicode( s ,"utf-8")
print(u)
```
</details>

### Question 63

Write a special comment to indicate a Python source code file is in unicode.

Hints:

<details>
<summary>Show Solution</summary>

```python

# -*- coding: utf-8 -*-

#----------------------------------------#
```
</details>

### Question 64

Write a program to compute 1/2+2/3+3/4+...+n/n+1 with a given n input by console (n>0).

Example:
If the following n is given as input to the program:

5

Then, the output of the program should be:

3.55

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:
Use float() to convert an integer to a float

<details>
<summary>Show Solution</summary>

```python
n=int(input())
sum=0.0
for i in range(1,n+1):
    sum += float(float(i)/(i+1))
print(sum)
```
</details>

### Question 65

Write a program to compute:

f(n)=f(n-1)+100 when n>0
and f(0)=1

with a given n input by console (n>0).

Example:
If the following n is given as input to the program:

5

Then, the output of the program should be:

500

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:
We can define recursive function in Python.

<details>
<summary>Show Solution</summary>

```python
def f(n):
    if n==0:
        return 0
    else:
        return f(n-1)+100

n=int(input())
print(f(n))
```
</details>

### Question 66
The Fibonacci Sequence is computed based on the following formula:

f(n)=0 if n=0
f(n)=1 if n=1
f(n)=f(n-1)+f(n-2) if n>1

Please write a program to compute the value of f(n) with a given n input by console.

Example:
If the following n is given as input to the program:

7

Then, the output of the program should be:

13

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:
We can define recursive function in Python.


<details>
<summary>Show Solution</summary>

```python
def f(n):
    if n == 0: return 0
    elif n == 1: return 1
    else: return f(n-1)+f(n-2)

n=int(input())
print(f(n))
```
</details>

### Question 67
The Fibonacci Sequence is computed based on the following formula:

f(n)=0 if n=0
f(n)=1 if n=1
f(n)=f(n-1)+f(n-2) if n>1

Please write a program using list comprehension to print the Fibonacci Sequence in comma separated form with a given n input by console.

Example:
If the following n is given as input to the program:

7

Then, the output of the program should be:

0,1,1,2,3,5,8,13


Hints:
We can define recursive function in Python.
Use list comprehension to generate a list from an existing list.
Use string.join() to join a list of strings.

In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
def f(n):
    if n == 0: return 0
    elif n == 1: return 1
    else: return f(n-1)+f(n-2)

n=int(input())
values = [str(f(x)) for x in range(0, n+1)]
print(",".join(values))
```
</details>

### Question 68

Please write a program using generator to print the even numbers between 0 and n in comma separated form while n is input by console.

Example:
If the following n is given as input to the program:

10

Then, the output of the program should be:

0,2,4,6,8,10

Hints:
Use yield to produce the next value in generator.

In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
def EvenGenerator(n):
    i=0
    while i<=n:
        if i%2==0:
            yield i
        i+=1


n=int(input())
values = []
for i in EvenGenerator(n):
    values.append(str(i))

print(",".join(values))
```
</details>

### Question 69
Please write a program using generator to print the numbers which can be divisible by 5 and 7 between 0 and n in comma separated form while n is input by console.

Example:
If the following n is given as input to the program:

100

Then, the output of the program should be:

0,35,70

Hints:
Use yield to produce the next value in generator.

In case of input data being supplied to the question, it should be assumed to be a console input.

<details>
<summary>Show Solution</summary>

```python
def NumGenerator(n):
    for i in range(n+1):
        if i%5==0 and i%7==0:
            yield i

n=int(input())
values = []
for i in NumGenerator(n):
    values.append(str(i))

print(",".join(values))
```
</details>

### Question 70
Please write assert statements to verify that every number in the list [2,4,6,8] is even.

Hints:
Use "assert expression" to make assertion.

<details>
<summary>Show Solution</summary>

```python
li = [2,4,6,8]
for i in li:
    assert i%2==0
```
</details>

### Question 71
Please write a program which accepts basic mathematic expression from console and print the evaluation result.

Example:
If the following string is given as input to the program:

35+3

Then, the output of the program should be:

38

Hints:
Use eval() to evaluate an expression.


<details>
<summary>Show Solution</summary>

```python
expression = raw_input()
print(eval(expression))
```
</details>

### Question 72
Please write a binary search function which searches an item in a sorted list. The function should return the index of element to be searched in the list.

Hints:
Use if/elif to deal with conditions.

<details>
<summary>Show Solution</summary>

```python
import math
def bin_search(li, element):
    bottom = 0
    top = len(li)-1
    index = -1
    while top>=bottom and index==-1:
        mid = int(math.floor((top+bottom)/2.0))
        if li[mid]==element:
            index = mid
        elif li[mid]>element:
            top = mid-1
        else:
            bottom = mid+1

    return index

li=[2,5,7,9,11,17,222]
print(bin_search(li,11))
print(bin_search(li,12))
```
</details>

### Question 73
Please write a binary search function which searches an item in a sorted list. The function should return the index of element to be searched in the list.

Hints:
Use if/elif to deal with conditions.

<details>
<summary>Show Solution</summary>

```python
import math
def bin_search(li, element):
    bottom = 0
    top = len(li)-1
    index = -1
    while top>=bottom and index==-1:
        mid = int(math.floor((top+bottom)/2.0))
        if li[mid]==element:
            index = mid
        elif li[mid]>element:
            top = mid-1
        else:
            bottom = mid+1

    return index

li=[2,5,7,9,11,17,222]
print(bin_search(li,11))
print(bin_search(li,12))
```
</details>

### Question 74
Please generate a random float where the value is between 10 and 100 using Python math module.

Hints:
Use random.random() to generate a random float in [0,1].

<details>
<summary>Show Solution</summary>

```python
import random
print(random.random()*100)
```
</details>

### Question 75
Please generate a random float where the value is between 5 and 95 using Python math module.

Hints:
Use random.random() to generate a random float in [0,1].

<details>
<summary>Show Solution</summary>

```python
import random
print(random.random()*100-5)
```
</details>

### Question 76
Please write a program to output a random even number between 0 and 10 inclusive using random module and list comprehension.

Hints:
Use random.choice() to a random element from a list.

<details>
<summary>Show Solution</summary>

```python
import random
print(random.choice([i for i in range(11) if i%2==0]))
```
</details>

### Question 77
Please write a program to output a random number, which is divisible by 5 and 7, between 0 and 10 inclusive using random module and list comprehension.

Hints:
Use random.choice() to a random element from a list.

<details>
<summary>Show Solution</summary>

```python
import random
print(random.choice([i for i in range(201) if i%5==0 and i%7==0]))
```
</details>

### Question 78
Please write a program to generate a list with 5 random numbers between 100 and 200 inclusive.

Hints:
Use random.sample() to generate a list of random values.

<details>
<summary>Show Solution</summary>

```python
import random
print(random.sample(range(100), 5))
```
</details>

### Question 79
Please write a program to randomly generate a list with 5 even numbers between 100 and 200 inclusive.

Hints:
Use random.sample() to generate a list of random values.

<details>
<summary>Show Solution</summary>

```python
import random
print(random.sample([i for i in range(100,201) if i%2==0], 5))
```
</details>

### Question 80
Please write a program to randomly generate a list with 5 numbers, which are divisible by 5 and 7 , between 1 and 1000 inclusive.

Hints:
Use random.sample() to generate a list of random values.

<details>
<summary>Show Solution</summary>

```python
import random
print(random.sample([i for i in range(1,1001) if i%5==0 and i%7==0], 5))
```
</details>

### Question 81
Please write a program to randomly print a integer number between 7 and 15 inclusive.

Hints:
Use random.randrange() to a random integer in a given range.

<details>
<summary>Show Solution</summary>

```python
import random
print(random.randrange(7,16))
```
</details>

### Question 82
Please write a program to compress and decompress the string "hello world!hello world!hello world!hello world!".

Hints:
Use zlib.compress() and zlib.decompress() to compress and decompress a string.

<details>
<summary>Show Solution</summary>

```python
import zlib
s = b'hello world!hello world!hello world!hello world!'
t = zlib.compress(s)
print(t)
print(zlib.decompress(t))
```
</details>

### Question 83
Please write a program to print the running time of execution of "1+1" for 100 times.

Hints:
Use timeit() function to measure the running time.

<details>
<summary>Show Solution</summary>

```python
from timeit import Timer
t = Timer("for i in range(100):1+1")
print(t.timeit())
```
</details>

### Question 84
Please write a program to shuffle and print the list [3,6,7,8].

Hints:
Use shuffle() function to shuffle a list.

<details>
<summary>Show Solution</summary>

```python
from random import shuffle
li = [3,6,7,8]
shuffle(li)
print(li)
```
</details>

### Question 85
Please write a program to shuffle and print the list [3,6,7,8].

Hints:
Use shuffle() function to shuffle a list.

<details>
<summary>Show Solution</summary>

```python
from random import shuffle
li = [3,6,7,8]
shuffle(li)
print(li)
```
</details>

### Question 86
Please write a program to generate all sentences where subject is in ["I", "You"] and verb is in ["Play", "Love"] and the object is in ["Hockey","Football"].

Hints:
Use list[index] notation to get a element from a list.

<details>
<summary>Show Solution</summary>

```python
subjects=["I", "You"]
verbs=["Play", "Love"]
objects=["Hockey","Football"]
for i in range(len(subjects)):
    for j in range(len(verbs)):
        for k in range(len(objects)):
            sentence = "%s %s %s." % (subjects[i], verbs[j], objects[k])
            print(sentence)
```
</details>

### Question 87
Please write a program to print the list after removing delete even numbers in [5,6,77,45,22,12,24].

Hints:
Use list comprehension to delete a bunch of element from a list.

<details>
<summary>Show Solution</summary>

```python
li = [5,6,77,45,22,12,24]
li = [x for x in li if x%2!=0]
print(li)
```
</details>

### Question 88
By using list comprehension, please write a program to print the list after removing delete numbers which are divisible by 5 and 7 in [12,24,35,70,88,120,155].

Hints:
Use list comprehension to delete a bunch of element from a list.
<details>
<summary>Show Solution</summary>

```python 
li = [12,24,35,70,88,120,155]
li = [x for x in li if x%5!=0 and x%7!=0]
print(li)
```
</details>

### Question 89
By using list comprehension, please write a program to print the list after removing the 0th, 2nd, 4th,6th numbers in [12,24,35,70,88,120,155].

Hints:
Use list comprehension to delete a bunch of element from a list.
Use enumerate() to get (index, value) tuple.

<details>
<summary>Show Solution</summary>

```python
li = [12,24,35,70,88,120,155]
li = [x for (i,x) in enumerate(li) if i%2!=0]
print(li)
```
</details>

### Question 90
By using list comprehension, please write a program generate a 3*5*8 3D array whose each element is 0.

Hints:
Use list comprehension to make an array.

<details>
<summary>Show Solution</summary>

```python
array = [[ [0 for col in range(8)] for col in range(5)] for row in range(3)]
print(array)
```
</details>

### Question 91
By using list comprehension, please write a program to print the list after removing the 0th,4th,5th numbers in [12,24,35,70,88,120,155].

Hints:
Use list comprehension to delete a bunch of element from a list.
Use enumerate() to get (index, value) tuple.

<details>
<summary>Show Solution</summary>

```python
li = [12,24,35,70,88,120,155]
li = [x for (i,x) in enumerate(li) if i not in (0,4,5)]
print(li)
```
</details>

### Question 92
By using list comprehension, please write a program to print the list after removing the value 24 in [12,24,35,24,88,120,155].

Hints:
Use list's remove method to delete a value.

<details>
<summary>Show Solution</summary>

```python
li = [12,24,35,24,88,120,155]
li = [x for x in li if x!=24]
print(li)
```
</details>

### Question 93
With two given lists [1,3,6,78,35,55] and [12,24,35,24,88,120,155], write a program to make a list whose elements are intersection of the above given lists.

Hints:
Use set() and "&=" to do set intersection operation.

<details>
<summary>Show Solution</summary>

```python
set1=set([1,3,6,78,35,55])
set2=set([12,24,35,24,88,120,155])
set1 &= set2
li=list(set1)
print(li)
```
</details>

### Question 94
With a given list [12,24,35,24,88,120,155,88,120,155], write a program to print this list after removing all duplicate values with original order reserved.

Hints:
Use set() to store a number of values without duplicate.

<details>
<summary>Show Solution</summary>

```python
def removeDuplicate( li ):
    newli=[]
    seen = set()
    for item in li:
        if item not in seen:
            seen.add( item )
            newli.append(item)

    return newli

li=[12,24,35,24,88,120,155,88,120,155]
print(removeDuplicate(li))
```
</details>

### Question 95
Define a class Person and its two child classes: Male and Female. All classes have a method "getGender" which can print "Male" for Male class and "Female" for Female class.

Hints:
Use Subclass(Parentclass) to define a child class.

<details>
<summary>Show Solution</summary>

```python
class Person(object):
    def getGender( self ):
        return "Unknown"

class Male( Person ):
    def getGender( self ):
        return "Male"

class Female( Person ):
    def getGender( self ):
        return "Female"

aMale = Male()
aFemale= Female()
print(aMale.getGender())
print(aFemale.getGender())
```
</details>

### Question 96
Please write a program which count and print the numbers of each character in a string input by console.

Example:
If the following string is given as input to the program:

abcdefgabc

Then, the output of the program should be:

a,2
c,2
b,2
e,1
d,1
g,1
f,1

Hints:
Use dict to store key/value pairs.
Use dict.get() method to lookup a key with default value.

<details>
<summary>Show Solution</summary>

```python
dic = {}
s=raw_input()
for s in s:
    dic[s] = dic.get(s,0)+1
print('\n'.join(['%s,%s' % (k, v) for k, v in dic.items()]))
```
</details>

### Question 97
Please write a program which accepts a string from console and print it in reverse order.

Example:
If the following string is given as input to the program:

rise to vote sir

Then, the output of the program should be:

ris etov ot esir

Hints:
Use list[::-1] to iterate a list in a reverse order.

<details>
<summary>Show Solution</summary>

```python
s=raw_input()
s = s[::-1]
print(s)
```
</details>

### Question 98
Please write a program which accepts a string from console and print the characters that have even indexes.

Example:
If the following string is given as input to the program:

H1e2l3l4o5w6o7r8l9d

Then, the output of the program should be:

Helloworld

Hints:
Use list[::2] to iterate a list by step 2.

<details>
<summary>Show Solution</summary>

```python
s=raw_input()
s = s[::2]
print(s)
```
</details>

### Question 99
Please write a program which prints all permutations of [1,2,3]

Hints:
Use itertools.permutations() to get permutations of list.

<details>
<summary>Show Solution</summary>

```python
import itertools
print(list(itertools.permutations([1,2,3])))
```
</details>

### Question 100
Write a program to solve a classic ancient Chinese puzzle: 
We count 35 heads and 94 legs among the chickens and rabbits in a farm. How many rabbits and how many chickens do we have?

Hint:
Use for loop to iterate all possible solutions.

<details>
<summary>Show Solution</summary>

```python
def solve(numheads,numlegs):
    ns='No solutions!'
    for i in range(numheads+1):
        j=numheads-i
        if 2*i+4*j==numlegs:
            return i,j
    return ns,ns

numheads=35
numlegs=94
solutions=solve(numheads,numlegs)
print(solutions)
```
</details>

