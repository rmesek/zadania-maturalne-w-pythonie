# Zadania maturalne w Pythonie

Wykorzystano materiały z [www.programiz.com](https://www.programiz.com/python-programming/), [www.w3schools.com](https://www.w3schools.com/python/), [stackabuse.com](https://stackabuse.com), [geeksforgeeks.org](https://www.geeksforgeeks.org/).

## Wczytywanie danych

------

### Obsługa pliku z danymi

#### Otwieranie pliku do odczytu

```python
f = open(r'nazwa_pliku.txt', 'r')
```



#### Wczytywanie całego pliku

nazwa_pliku.txt

```
1 2 3
4 5 6
7 8 9
```



```python
data = f.read()

print(type(data))

print(data)
```

Wyjście

```
<class 'str'>
1 2 3
4 5 6
7 8 9
```



#### Wczytywanie pliku jako wiersze

nazwa_pliku.txt

```
1100 0
100101 0
111101 0
```



```python
data = f.readlines()

print(data)
```

Wyjście

```
['1100 0\n', '100101 0\n', '111101 0']
```



#### Wczytywanie n linijek

nazwa_pliku.txt

```
1100 0
100101 0
111101 0
```



```python
N = 3

lines = []

for i in range(N):
    lines.append(f.readline().strip())

print(lines)
```

Wyjście

```
['1100 0', '100101 0', '111101 0']
```



#### Rozdzielanie danych w linijce

nazwa_pliku.txt

```
1100 0 36
100101 3 49
111101 1 81
```



```python
N = 3

data = []

for i in range(N):
    data.append( f.readline().strip().split() )

print(data)
```

Wyjście

```
[['1100', '0', '36'], ['100101', '3', '49'], ['111101', '1', '81']]
```



#### Rozdzielanie danych do zmiennych

nazwa_pliku.txt

```
1100 0 36
100101 3 49
111101 1 81
```



```python
N = 3

data = []

for i in range(N):
     a, b, c = f.readline().strip().split()
     print(a, b, c)
```

Wyjście

```
1100 0 36
100101 3 49
111101 1 81
```



#### Rozdzielanie danych to tablic

nazwa_pliku.txt

```
1100 0 36
100101 3 49
111101 1 81
```



```python
N = 3

a, b, c = [None for x in range(N)], [None for x in range(N)], [None for x in range(N)]

for i in range(N):
     a[i], b[i], c[i] = f.readline().strip().split(' ')
     
print(a, b, c)

for i in range(N):
    print(a[i], b[i], c[i])
```

Wyjście

```
['1100', '100101', '111101'] ['0', '3', '1'] ['36', '49', '81']
1100 0 36
100101 3 49
111101 1 81
```



#### Powrót na początek pliku z użyciem "seek"

nazwa_pliku.txt

```
1st line
2nd line
3rd line
```



```python
print(f.readline().strip())
print(f.readline().strip())

f.seek(0) # file. seek(offset(not lines)[, whence])

print(f.readline().strip())
```

Wyjście

```
1st line
2nd line
1st line
```



#### Zamykanie pliku po zakończeniu pracy

```python
f.close()
```



## Zapisywanie danych

------

### Obsługa pliku z wyjściem

#### Tworzenie pliku wyjścia

```python
out = open(r'nazwa_pliku.txt', 'w')
```



#### Zapisywanie do pliku

```python
zmienna = 12

out.write(str(zmienna) + '\n')
```

nazwa_pliku.txt

```
12

```



#### Zamykanie pliku po zakończeniu pracy

```python
out.close()
```



## Wypisywanie danych

------

### Użycie "print"

#### Wypisywanie bez znaku nowego wiersza

```python
print("A") # print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
print("B", end='')
print("C")
```

Wyjście

```
A
BC
```

#### 

#### Wypisywanie wielu zmiennych

```python
a = "i have"
b = 5
c = "moners"
```



```python
print(a)
print(b)
print(c)
```

Wyjście

```
i have
5
moners
```



```python
print(a, end='')
print(b, end='')
print(c, end='')
```

Wyjście

```
i have5moners
```



```python
print()
print(a, str(b), c, sep='')
print('\n')
print(a, str(b), c)
```

Wyjście

```

i have5moners


i have 5 moners
```



#### Wypisywanie wielu linijek, formatowany tekst

```python
a = """This is the first line of my text 
this is the next line."""

b = "This is the first line of my text \nthis is the next line."

c = "This 'is' the first line of my text \nthis is the next line."

d = "This \"is\" the first line of my text \nthis is the next line."

print(a)

print()
print(b)

print()
print(c)

print()
print(d)
```

Wyjście

```
This is the first line of my text 
this is the next line.

This is the first line of my text 
this is the next line.

This 'is' the first line of my text 
this is the next line.

This "is" the first line of my text 
this is the next line.
```



#### Łamanie długiego ciągu znaków

```python
a = """This is the first line of my text \
this is the same line.
This is next line."""

b = "This is the first line of my text \
this is the same line."

print(a)
print()
print(b)
```

Wyjście

```
This is the first line of my text this is the same line.
This is next line.

This is the first line of my text this is the same line.
```



### Formatowanie przy użyciu "str.format()"

#### Szczególne formatowanie

```python
my_name = "eric"
my_drink = "WATER"
print("Hello, {name}. I drink {drink}.".format(name = my_name.capitalize(),
                                               drink = my_drink.lower() ))
```

Wyjście

```
Hello, Eric. I drink water.
```



#### Użycie ze słownikiem

```python
person = {'name': 'Eric', 'age': 74}
print("Hello, {name}. You are {age}.".format(name=person['name'], age=person['age']))

print("Hello, {name}. You are {age}.".format(**person)) # trick with "**"
```

Wyjście

```
Hello, Eric. You are 74.
Hello, Eric. You are 74.
```



#### Wypisywanie n miejsc po przecinku

```python
a = 12.12345
b = 4

print("i have {:.2f} and {} moners".format(a, b))
print("i have {:.2f} and {} moners".format(b, a))
print("i have {1:.2f} and {0} moners".format(a, b)) # custom place with {n}
```

Wyjście

```
i have 12.12 and 4 moners
i have 4.00 and 12.12345 moners
i have 4.00 and 12.12345 moners
```



## Tablice

------

### Operacje na listach ([docs.python.org](https://docs.python.org/3.6/library/stdtypes.html#sequence-types-list-tuple-range))

#### Tworzenie pustej tablicy o danym rozmiarze

```python
SIZE = 1_000

array = [None for x in range(SIZE)]
```



#### Sprawdzanie rozmiaru

```python
a = [1, 2, 3]

print(len(a))
```

Wyjście

```
3
```



#### Sprawdzanie czy element znajduje się w liście

```python
a = [1, 3, 4]
if 3 in a:
    print('3 was found')
    
if 5 not in a:
    print('5 was not found')
```

Wyjście

```
3 was found
5 was not found
```



#### Dodawanie elementu na koniec listy

```python
a = [1, 2, 3]

a.append(4)

print(a)
```

Wyjście

```
[1, 2, 3, 4]
```



#### Usuwanie elementu z końca listy

```python
a = [1, 2, 3, 4]

print("Poped a ", a.pop())

print(a)
```

Wyjście

```
[1, 2, 3]
```



#### Dodawanie elementu na n-tej pozycji

```python
a = [1, 3, 4]

a.insert(1, 2)

print(a)
```

Wyjście

```
[1, 2, 3, 4]
```



#### Usuwanie elementy z n-tej pozycji

```python
a = [1, 2, 3, 4]

del a[1]

print(a)
```

Wyjście

```
[1, 3, 4]
```



#### Odwracanie tablicy

```python
a = [1, 2, 3, 4]

b = a[::-1]

print(a)

a.reverse()

print(a)

print(b)
```

Wyjście

```
[1, 2, 3, 4]
[4, 3, 2, 1]
[4, 3, 2, 1]
```



#### Wybieranie elementów z listy

```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(a[1:4]) # list[start:stop:step]

print(a[::2]) # n-th element

print(a[-4:-2])

print(a[-2::]) # last n elements in order

print(a[:-3:-1]) # last n elements reversed
```

Wyjście

```
[2, 3, 4]
[1, 3, 5, 7, 9]
[7, 8]
[9, 10]
[10, 9]
```



#### Kopiowanie tablicy

```python
a = [1, 2, 3]

#b = a # Wrong, same lists
b = a.copy() # Diffrent lists

b.append(1)

print('a: ' + str(a))
print('b: ' + str(b))
```

Wyjście

```
a: [1, 2, 3]
b: [1, 2, 3, 1]
```



#### Usuwanie duplikatów BEZ zachowania kolejności

```python
a = [2, 3, 3, 2, 5, 4, 4, 6]

b = list( set(a) )

print(b)
```

Wyjście

```
[2, 3, 4, 5, 6]
```



#### Usuwanie duplikatów z zachowaniem kolejności

```python
from collections import OrderedDict

a = [2, 3, 3, 2, 5, 4, 4, 6]

b = list(OrderedDict.fromkeys(a))

print(b)
```

Python 3.6+

```python
a = [2, 3, 3, 2, 5, 4, 4, 6]

b = list(dict.fromkeys(a))

print(b)
```

Wyjście

```
[2, 3, 5, 4, 6]
```



#### Sortowanie

```python
a = [3, 1, 4, 2]

print(sorted(a)) # sorted(iterable, key=None, reverse=False)

print(a)

a.sort() # list.sort(reverse=True|False, key=myFunc) 

print(a)
```

Wyjście

```
[4, 3, 2, 1]
[3, 1, 4, 2]
[1, 2, 3, 4]
```



#### Sortowanie cd.

```python
# A function that returns the length of the value:
def myFunc(e):
  return len(e)

cars = ['Ford', 'Mitsubishi', 'BMW', 'VW']

cars.sort(reverse=True, key=myFunc)

print(cars)
```

Wyjście

```
['Mitsubishi', 'Ford', 'BMW', 'VW']
```



### Słowniki ([docs.python.org](https://docs.python.org/3.6/library/stdtypes.html#mapping-types-dict))

#### Wybieranie elementy poprzez klucz

```python
thisdict =	{
  "brand": "Ford",
  "electric": False,
  "year": 1964,
  "colors": ["red", "white", "blue"]
} 

print(thisdict["brand"])
```

Wyjście

```
Ford
```



#### Dodatkowe sposoby na stworzenie słownika

```python
numbers = dict(x=5, y=0)
print('numbers =', numbers)
print(type(numbers))

empty = dict()
print('empty =', empty)
print(type(empty))

# keyword argument is not passed
numbers1 = dict([('x', 5), ('y', -5)])
print('numbers1 =',numbers1)

# keyword argument is also passed
numbers2 = dict([('x', 5), ('y', -5)], z=8)
print('numbers2 =',numbers2)

# zip() creates an iterable in Python 3
numbers3 = dict(dict(zip(['x', 'y', 'z'], [1, 2, 3])))
print('numbers3 =',numbers3)
```

Wyjście

```
numbers = {'x': 5, 'y': 0}
<class 'dict'>
empty = {}
<class 'dict'>
numbers1 = {'x': 5, 'y': -5}
numbers2 = {'x': 5, 'y': -5, 'z': 8}
numbers3 = {'x': 1, 'y': 2, 'z': 3}
```



#### Szukanie klucza przez wartość

```python
thisdict =	{
  "brand": "Ford",
  "model": "white",
  "year": 1964,
  "colors": "white"
} 

for key, value in thisdict.items():
    if value == "white":
        print(key)
```

Wyjście

```
model
colors
```



#### Sortowanie słownika po wartości

```python
# A function that returns the 'year' value:
def myFunc(e):
  return e['year']

cars = [
  {'car': 'Ford', 'year': 2005},
  {'car': 'Mitsubishi', 'year': 2000},
  {'car': 'BMW', 'year': 2019},
  {'car': 'VW', 'year': 2011}
]

cars.sort(key=myFunc) 

print(cars)
```

Wyjście

```
[{'car': 'Mitsubishi', 'year': 2000}, {'car': 'Ford', 'year': 2005}, {'car': 'VW', 'year': 2011}, {'car': 'BMW', 'year': 2019}]
```



## Operacje (metody) na ciągach znaków "str"

------

### Wbudowane operacje na typie "str" ([docs.python.org](https://docs.python.org/3.6/library/stdtypes.html#text-sequence-type-str))

#### Użycie cudzysłowu

```
'allows embedded "double" quotes'
"allows embedded 'single' quotes"
'''Three single quotes''', """Three double quotes"""
```



#### Specjalne znaki

```
\'		Single Quote
\\		Backslash
\n		New Line
\r		Carriage Return
\t		Tab
\b		Backspace
\ooo 	Octal value
\xhh 	Hex value
```



#### Małe i wielkie litery

```python
str_1 = "nAmE"

print( str_1.capitalize() )

print( str_1.lower() )

print( str_1.upper() )

print( str_1.swapcase() )
```

Wyjście

```
Name
name
NAME
NaMe
```



#### Ilość wystąpień podciągu

```python
str_1 = "Python is awesome, isn't it?"

sub_str = "is"
print( str_1.count(sub_str) ) # str.count(sub[, start[, end]])

# count after first 'i' and before the last 'i'
print( str_1.count('i', 8, 25) )
```

Wyjście

```
2
1
```



#### Sprawdzanie czy zaczyna się na ciąg znaków

```python
text = "Python is easy to learn."

result = text.startswith('is easy') # str.startswith(prefix[, start[, end]])
# returns False
print(result)

result = text.startswith('Python is ')
# returns True
print(result)

result = text.startswith('Python is easy to learn.')
# returns True
print(result)

```

Wyjście

```
False
True
True
```



#### Sprawdzanie czy kończy się na ciąg znaków

```python
text = "Python is easy to learn."

result = text.endswith('to learn') # str.endswith(suffix[, start[, end]])
# returns False
print(result)

result = text.endswith('to learn.')
# returns True
print(result)

ends_list = ['is eas1', 'is easy']
result = text.endswith(tuple(ends_list), 0, 14)
# returns True
print(result)
```

Wyjście

```
False
True
True
```



#### Szukanie podciągu

```python
quote = 'Do small things with great love'

# tHings
print(quote.find('h')) # str.find(sub[, start[, end]] ); returns '-1' if not found

# witH
print(quote.rfind('h')) # str.rfind()

# Substring is searched in 'hings with great love'
print(quote.find('small things', 10))

# Substring is searched in ' small things with great love' 
print(quote.find('small things', 2))

# Substring is searched in 'hings with great lov'
print(quote.find('o small ', 10, -1))

# Substring is searched in 'll things with'
print(quote.find('things ', 6, 20))
```

Wyjście

```
10
19
-1
3
-1
9
```



#### Sprawdzanie czy ciąg zawiera jedynie znaki alfanumeryczne

```python
name = "M234onica"
print(name.isalnum())

# contains whitespace
name = "M3onica Gell22er "
print(name.isalnum())

name = "Mo3nicaGell22er"
print(name.isalnum())

name = "133"
print(name.isalnum())
```

Wyjście

```
True
False
True
True
```



#### Sprawdzanie czy ciąg zawiera jedynie litery

```python
name = "Monica"
print(name.isalpha())

# contains whitespace
name = "Monica Geller"
print(name.isalpha())

# contains number
name = "Mo3nicaGell22er"
print(name.isalpha())
```

Wyjście

```
True
False
False
```



#### Sprawdzanie czy ciąg zawiera jedynie cyfry

```python
s = "28212"
print(s.isdecimal())

# contains alphabets
s = "32ladk3"
print(s.isdecimal())

# contains alphabets and spaces
s = "Mo3 nicaG el l22er"
print(s.isdecimal())

#s = '²3455'
s = '\u00B23455'
print(s.isdecimal())

# s = '½'
s = '\u00BD'
print(s.isdecimal())
```

Wyjście

```
True
False
False
False
False
```



#### Sprawdzanie czy ciąg znaków składa się tylko z małych/wielkich liter

```python
s = 'this is good'
print(s.islower())

s = 'th!s is a1so g00d'
print(s.islower())

s = 'this is Not good'
print(s.islower())

# example string
string = "THIS IS GOOD!"
print(string.isupper());

# numbers in place of alphabets
string = "THIS IS ALSO G00D!"
print(string.isupper());

# lowercase string
string = "THIS IS not GOOD!"
print(string.isupper());
```

Wyjście

```
True
True
False
True
True
False
```



#### Sprawdzanie czy ciąg składa się tylko z białych znaków

```python
s = '   \t'
print(s.isspace())

s = ' a '
print(s.isspace())

s = ''
print(s.isspace())
```

Wyjście

```
True
False
False
```



#### Łączenie ciągów znaków

```python
# .join() with lists
numList = ['1', '2', '3', '4']
separator = ', '
print(separator.join(numList))

# .join() with tuples
numTuple = ('1', '2', '3', '4')
print(separator.join(numTuple))

s1 = 'abc'
s2 = '123'

# each element of s2 is separated by s1
# '1'+ 'abc'+ '2'+ 'abc'+ '3'
print('s1.join(s2):', s1.join(s2))

# each element of s1 is separated by s2
# 'a'+ '123'+ 'b'+ '123'+ 'b'
print('s2.join(s1):', s2.join(s1))

# .join() with sets
test = {'2', '1', '3'}
s = ', '
print(s.join(test))

test = {'Python', 'Java', 'Ruby'}
s = '->->'
print(s.join(test))

# .join() with dictionaries
test = {'mat': 1, 'that': 2}
s = '->'

# joins the keys only
print(s.join(test))
```

Wyjście

```
1, 2, 3, 4
1, 2, 3, 4
s1.join(s2): 1abc2abc3
s2.join(s1): a123b123c
2, 1, 3
Ruby->->Python->->Java
mat->that
```



#### Usuwanie poprzedzających i następujących znaków niedrukowanych np. "\n"

```python
string = '  xoxo love xoxo   '

# Leading and trailing whitespaces are removed
print(string.strip()) # string.strip([chars])

# Leading whitespaces are removed
print(string.lstrip())

# Trailing whitespaces are removed
print(string.rstrip())

# All <whitespace>,x,o,e characters in the left
# and right of string are removed
print(string.strip(' xoe'))

# Argument doesn't contain space
# No characters are removed.
print(string.strip('stx'))

string = 'android is awesome'
print(string.strip('an'))
```

Wyjście

```
xoxo love xoxo
xoxo love xoxo   
  xoxo love xoxo
lov
  xoxo love xoxo   
droid is awesome
```



#### Zamienianie podciągu znaków

```python
song = 'cold, cold heart'

# replacing 'cold' with 'hurt'
print(song.replace('cold', 'hurt')) # str.replace(old, new [, count]) 

song = 'Let it be, let it be, let it be, let it be'

# replacing only two occurences of 'let'
print(song.replace('let', "don't let", 2))
```

Wyjście

```
hurt, hurt heart
Let it be, don't let it be, don't let it be, let it be
```



#### Rozdzielanie ciągu znaków

```python
text= 'Love thy neighbor'

# splits at space
print(text.split()) # str.split([separator [, maxsplit]]); str.rsplit([...])

grocery = 'Milk, Chicken, Bread'

# splits at ','
print(grocery.split(', '))

# Splitting at ':'
print(grocery.split(':'))
```

Wyjście

```
['Love', 'thy', 'neighbor']
['Milk', 'Chicken', 'Bread']
['Milk, Chicken, Bread']
```



#### Rozdzielanie linijek

```python
grocery = 'Milk\nChicken\r\nBread\rButter'

print(grocery.splitlines()) # str.splitlines([keepends])
print(grocery.splitlines(True))

grocery = 'Milk Chicken Bread Butter'
print(grocery.splitlines())
```

Wyjście

```
['Milk', 'Chicken', 'Bread', 'Butter']
['Milk\n', 'Chicken\r\n', 'Bread\r', 'Butter']
['Milk Chicken Bread Butter']
```



#### Dosłowny ciąg znaków (raw string)

```python
a = R"""This is the first line of my text \
this is the next line."""

b = R"This is the first line of my text \nthis is the next line."

print(a)
print()
print(b)
```

Wyjście

```
This is the first line of my text \
this is the next line.

This is the first line of my text \nthis is the next line.
```



## Przydatne funkcje

------

### Funkcje wbudowane i dodatkowe operacje ([docs.python.org](https://docs.python.org/3.6/library/functions.html)) 

#### Dzielenie całkowite

```python
print(7 // 3) # x // y
```

Wyjście

```
2
```



#### Modulo (reszta z dzielenia)

```python
print(7 % 3) # x % y
```

Wyjście

```
1
```



#### Potęgowanie

```python
print(2 ** 3) # x ** y
```

Wyjście

```
8
```



#### Operacje logiczne

```python
print(False or True) # x or y
print(False and True) # x and y
print(not False) # not x
```

Wyjście

```
True
False
True
```



#### Porównywanie

```python
print (2 < 3) # < strictly less than; TRUE
print (3 <= 3) # <= less than or equal; TRUE
print(2 < 3) # > strictly greater than; TRUE
print(2 >= 3) # >= greater than or equal; FALSE
print('6' == str(6)) # == equal; TRUE
print('' != None) # != not equal; TRUE
print('6' is 6) # is object identity; FALSE
print(type(6) is not type(7)) # is not negated object identity; FALSE
```

Wyjście

```
True
True
True
False
True
True
False
False
```



#### Zaokrąglanie liczby 

```python
print( round(1.1) ) # round(number, ndigits)

print( round(1.5) ) # round-to-even

print( round(1.7) )

print( round(2.1) )

print( round(2.5) ) # round-to-even

print( round(2.7) )
```

Wyjście

```
1
2
2
2
2
3
```



#### Sprawdzanie czy wszystkie iterowane elementy są prawdziwe

```python
# all values true
l = [1, 3, 4, 5]
print(all(l))

# all values false
l = [0, False]
print(all(l))

# one false value
l = [1, 3, 4, 0]
print(all(l))

# one true value
l = [0, False, 5]
print(all(l))

# empty iterable
l = []
print(all(l))
```

Wyjście

```
True
False
False
False
True
```



#### Wartość bezwzględna

```python
# random integer
integer = -20
print('Absolute value of -20 is:', abs(integer))

#random floating number
floating = -30.33
print('Absolute value of -30.33 is:', abs(floating))
```

Wyjście

```
Absolute value of -20 is: 20
Absolute value of -30.33 is: 30.33
```



#### Zamiana na format "ascii"

```python
normalText = 'Python is interesting'
print(ascii(normalText))

otherText = 'Pythön is interesting'
print(ascii(otherText))

print('Pyth\xf6n is interesting')
```

Wyjście

```
'Python is interesting'
'Pyth\xf6n is interesting'
Pythön is interesting
```



#### Binarna reprezentacja liczby całkowitej

```python
number = 5
print('The binary equivalent of 5 is:', bin(number))
```

Wyjście

```
The binary equivalent of 5 is: 0b101
```



#### Zamiana na typ "bool"

```python
test = []
print(test,'is',bool(test))

test = [0]
print(test,'is',bool(test))

test = 0.0
print(test,'is',bool(test))

test = None
print(test,'is',bool(test))

test = True
print(test,'is',bool(test))

test = 'Easy string'
print(test,'is',bool(test))
```

Wyjście

```
[] is False
[0] is True
0.0 is False
None is False
True is True
Easy string is True
```



#### Zamiana liczby całkowitej na znak zgodnie z unicode

```python
print(chr(97))
print(chr(65))
print(chr(1200))
```

Wyjście

```
a
A
Ұ
```



#### Dzielenie z resztą

```python
print('divmod(3, 8) = ', divmod(3, 8))
print('divmod(5, 5) = ', divmod(5, 5))
print('divmod(-1, 3) = ', divmod(-1, 3))

# divmod() with Floats
print('divmod(8.0, 3) = ', divmod(8.0, 3))
print('divmod(3, 8.0) = ', divmod(3, 8.0))
print('divmod(7.5, 2.5) = ', divmod(7.5, 2.5))
print('divmod(2.6, 0.5) = ', divmod(2.6, 0.5))
```

Wyjście

```
divmod(3, 8) =  (0, 3)
divmod(5, 5) =  (1, 0)
divmod(-1, 3) =  (-1, 2)
divmod(8.0, 3) =  (2.0, 2.0)
divmod(3, 8.0) =  (0.0, 3.0)
divmod(7.5, 2.5) =  (3.0, 0.0)
divmod(2.6, 0.5) =  (5.0, 0.10000000000000009)
```



#### Dodawanie licznika do iterowanego typu

```python
grocery = ['bread', 'milk', 'butter']
enumerateGrocery = enumerate(grocery)

print(type(enumerateGrocery))

# converting to list
print(list(enumerateGrocery))

# changing the default counter
enumerateGrocery = enumerate(grocery, 10)
print(list(enumerateGrocery))

print('\n')
for count, item in enumerate(grocery):
  print(count, item)
```

Wyjście

```
<class 'enumerate'>
[(0, 'bread'), (1, 'milk'), (2, 'butter')]
[(10, 'bread'), (11, 'milk'), (12, 'butter')]


0 bread
1 milk
2 butter
```



#### Zmienne globalne

```python
c = 0 # global variable

def add():
    global c
    c = c + 2 # increment by 2
    print("Inside add():", c)

add()
print("In main:", c)
```

Wyjście

```
Inside add(): 2
In main: 2
```



#### Pomoc z użyciem "help()"

```python
help(list) # help([...])
```

```python
from math import *
help('math.pow')
```



#### Zamiana liczby całkowitej na szesnastkową

```python
number = 435
print(number, 'in hex =', hex(number))

number = 0
print(number, 'in hex =', hex(number))

number = -34
print(number, 'in hex =', hex(number))

returnType = type(hex(number))
print('Return type from hex() is', returnType)
```

Wyjście

```
435 in hex = 0x1b3
0 in hex = 0x0
-34 in hex = -0x22
Return type from hex() is <class 'str'>
```



#### Zamiana liczby zmiennoprzecinkowej na szesnastkową

```python
number = 2.5
print(number, 'in hex =', float.hex(number))

number = 0.0
print(number, 'in hex =', float.hex(number))

number = 10.5
print(number, 'in hex =', float.hex(number))
```

Wyjście

```
2.5 in hex = 0x1.4000000000000p+1
0.0 in hex = 0x0.0p+0
10.5 in hex = 0x1.5000000000000p+3
```



#### Wprowadzanie danych z użyciem "input"

```python
# get input from user

inputString = input()

print('The inputted string is: ', inputString)

inputString = input('Enter a string: ')

print('The inputted string is: ', inputString)
```

Wyjście

```
Python is interesting.
The inputted string is:  Python is interesting.
Enter a string: Python is interesting.
The inputted string is:  Python is interesting.
```



#### Konwersja na liczbę całkowitą

```python
# integer
print("int(123) is:", int(123))

# float
print("int(123.23) is:", int(123.23))
print("int(123.9) is:", int(123.9))

# string
print("int('123') is:", int('123'))
```

Wyjście

```
int(123) is: 123
int(123.23) is: 123
int(123.9) is: 123
int('123') is: 123
```



```python
# binary 0b or 0B
print("For 1010, int is:", int('1010', 2)) # int(x=0, base=10); base = 2-36
print("For 0b1010, int is:", int('0b1010', 2))

# octal 0o or 0O
print("For 12, int is:", int('12', 8))
print("For 0o12, int is:", int('0o12', 8))

# hexadecimal
print("For A, int is:", int('A', 16))
print("For 0xA, int is:", int('0xA', 16))
```

Wyjście

```
For 1010, int is: 10
For 0b1010, int is: 10
For 12, int is: 10
For 0o12, int is: 10
For A, int is: 10
For 0xA, int is: 10
```



#### Zwracanie długości obiektu

```python
testList = []
print(testList, 'length is', len(testList))

testList = [1, 2, 3]
print(testList, 'length is', len(testList))

testTuple = (1, 2, 3)
print(testTuple, 'length is', len(testTuple))

testRange = range(1, 10)
print('Length of', testRange, 'is', len(testRange))
```

Wyjście

```
[] length is 0
[1, 2, 3] length is 3
(1, 2, 3) length is 3
Length of range(1, 10) is 9
```



```python
testString = ''
print('Length of', testString, 'is', len(testString))

testString = 'Python'
print('Length of', testString, 'is', len(testString))

testSet = {1, 2, 3}
print(testSet, 'length is', len(testSet))

# Empty Set
testSet = set()
print(testSet, 'length is', len(testSet))

testDict = {1: 'one', 2: 'two'}
print(testDict, 'length is', len(testDict))

testDict = {}
print(testDict, 'length is', len(testDict))
```

Wyjście

```
Length of  is 0
Length of Python is 6
{1, 2, 3} length is 3
set() length is 0
{1: 'one', 2: 'two'} length is 2
{} length is 0
```



#### Zamiana na listę

```python
# empty list
print(list())

# vowel string
vowel_string = 'aeiou'
print(list(vowel_string))

# vowel tuple
vowel_tuple = ('a', 'e', 'i', 'o', 'u')
print(list(vowel_tuple))

# vowel list
vowel_list = ['a', 'e', 'i', 'o', 'u']
print(list(vowel_list))
```

Wyjście

```
[]
['a', 'e', 'i', 'o', 'u']
['a', 'e', 'i', 'o', 'u']
['a', 'e', 'i', 'o', 'u']
```



#### Zwracanie największego elementu

```python
number = [3, 2, 8, 5, 10, 6]
largest_number = max(number); # max(iterable, *iterables, key, default)

print("The largest number is:", largest_number)
```

Wyjście

```
The largest number is: 10
```



```python
languages = ["Python", "C Programming", "Java", "JavaScript"]
largest_string = max(languages) # ordered alphabetically
longest_string = max(languages, key = lambda k: len(k))

print("The largest string is:", largest_string)
print("The longest string is:", longest_string)
```

Wyjście

```
The largest string is: Python
The longest string is: C Programming
```



#### Zwracanie najmniejszego elementu

```python
square = {2: 4, 3: 9, -1: 1, -2: 4}

# the smallest key
key1 = min(square)
print("The smallest key:", key1)    # -2

# the key whose value is the smallest
key2 = min(square, key = lambda k: square[k])

print("The key with the smallest value:", key2)    # -1

# getting the smallest value
print("The smallest value:", square[key2])    # 1
```

Wyjście

```
The smallest key: -2
The key with the smallest value: -1
The smallest value: 1
```



#### Zamiana liczby całkowitej na ósemkową

```python
# decimal to octal
print('oct(10) is:', oct(10))

# binary to octal
print('oct(0b101) is:', oct(0b101))

# hexadecimal to octal
print('oct(0XA) is:', oct(0XA))
```

Wyjście

```
oct(10) is: 0o12
oct(0b101) is: 0o5
oct(0XA) is: 0o12
```



#### Zwracanie liczby całkowitej reprezentującej znak unicode

```python
print(ord('5'))    # 53
print(ord('A'))    # 65
print(ord('$'))    # 36
```

Wyjście

```
53
65
36
```



#### Tworzenie ciągu liczb całkowitych

```python
# empty range
print(list(range(0))) # range(start, stop[, step])

# using range(stop)
print(list(range(10)))

# using range(start, stop)
print(list(range(1, 10)))

start = 2
stop = -14
step = -2

print(list(range(start, stop, step)))

# value constraint not met
print(list(range(start, 14, step)))
```

Wyjście

```
[]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
[2, 0, -2, -4, -6, -8, -10, -12]
[]
```



#### Łączenie list

```python
print( list(zip([1, 2, 3], ['a', 'b', 'c'])) )
```

Wyjście

```
[(1, 'a'), (2, 'b'), (3, 'c')]
```



#### Odwracanie ciągu

```python
# for string
seq_string = 'Python'
print(seq_string[::-1])
print(list(reversed(seq_string)))

# for tuple
seq_tuple = ('P', 'y', 't', 'h', 'o', 'n')
print(list(reversed(seq_tuple)))

# for range
seq_range = range(5, 9)
print(list(reversed(seq_range)))

# for list
seq_list = [1, 2, 4, 3, 5]
print(list(reversed(seq_list)))
```

Wyjście

```
nohtyP
['n', 'o', 'h', 't', 'y', 'P']
['n', 'o', 'h', 't', 'y', 'P']
[8, 7, 6, 5]
[5, 3, 4, 2, 1]
```



#### Sortowanie

```python
# vowels list
py_list = ['e', 'a', 'u', 'o', 'i']
print(sorted(py_list)) # sorted(iterable, key=None, reverse=False)

# string
py_string = 'Python'
print(sorted(py_string))

# vowels tuple
py_tuple = ('e', 'a', 'u', 'o', 'i')
print(sorted(py_tuple))

# set
py_set = {'e', 'a', 'u', 'o', 'i'}
print(sorted(py_set, reverse=True))

# dictionary
py_dict = {'e': 1, 'a': 2, 'u': 3, 'o': 4, 'i': 5}
print(sorted(py_dict, reverse=True))
```

Wyjście

```
['a', 'e', 'i', 'o', 'u']
['P', 'h', 'n', 'o', 't', 'y']
['a', 'e', 'i', 'o', 'u']
['u', 'o', 'i', 'e', 'a']
['u', 'o', 'i', 'e', 'a']
```



```python
# take the second element for sort
def take_second(elem):
    return elem[1]


# random list
random = [(2, 2), (3, 4), (4, 1), (1, 3)]

# sort list with key
sorted_list = sorted(random, key=take_second)

# print list
print('Sorted list:', sorted_list)
```

Wyjście

```
Sorted list: [(4, 1), (2, 2), (1, 3), (3, 4)]
```



#### Operacja na każdym iterowanym elemencie "map"

```python
def calculateSquare(n):
    return n*n


numbers = (1, 2, 3, 4)
result = map(calculateSquare, numbers) # map(function, iterable, ...)
print(result)

# converting map object to list
numbersSquare = list(result)
print(numbersSquare)
```

Wyjście

```
<map object at 0x00000180EF1D4AC8>
[1, 4, 9, 16]
```



#### Użycie "lambda" z "map"

```python
numbers = (1, 2, 3, 4)
result = map(lambda x: x*x, numbers)
print(result)

# converting map object to set
numbersSquare = set(result)
print(numbersSquare)

num1 = [4, 5, 6]
num2 = [5, 6, 7]

result = map(lambda n1, n2: n1+n2, num1, num2)
print(list(result))
```

Wyjście

```
<map object at 0x000001EE137F4B88>
{16, 1, 4, 9}
[9, 11, 13]
```



#### Zamiana obiektu na ciąg znaków "string"

```python
result = str(10) # str(object, encoding='utf-8', errors='strict[/ignore]')
print(result)

# bytes
b = bytes('pythön', encoding='utf-8')

print(str(b, encoding='ascii', errors='ignore'))
```

Wyjście

```
10
pythn
```



#### Sumowanie iterowanego obiektu

```python
numbers = [2.5, 3, 4, -5]

# start parameter is not provided
numbers_sum = sum(numbers)
print(numbers_sum)

# start = 10
numbers_sum = sum(numbers, 10)
print(numbers_sum)
```

Wyjście

```
4.5
14.5
```



#### Konwersja na typ "iterator" i wypisywanie kolejnego elementu

```python
import itertools as it

iterator1 = iter([1, 2, 3, 4])

next(iterator1) # 1

iterator1, iterator2 = it.tee(iterator1, 2)

print( list(iterator1) ) # 2, 3, 4

print( list(iterator1) ) # iterator1 is now exhausted.

print( list(iterator2) ) # iterator2 works independently of iterator1
```

Wyjście

```
[2, 3, 4]
[]
[2, 3, 4]
```



#### Zwracanie typu obiektu

```python
numbers_list = [1, 2]
print(type(numbers_list))

numbers_dict = {1: 'one', 2: 'two'}
print(type(numbers_dict))

class Foo:
    a = 0

foo = Foo()
print(type(foo))
```

Wyjście

```
<class 'list'>
<class 'dict'>
<class '__main__.Foo'>
```



### Moduł  "math" ([docs.python.org](https://docs.python.org/3.6/library/math.html))

#### Importowanie modułu

```python
import math
print( math.sqrt(4) )
```

Wyjście

```
2.0
```



#### Importowanie wszystkich funkcji z modułu

```python
from math import *
print( sqrt(4) )
```

Wyjście

```
2.0
```



#### Importowanie konkretnej funkcji z modułu

```python
from math import sqrt
```

Wyjście

```
2.0
```



#### Wartość pi i e

```python
from math import pi, e

print(pi)

print(e)
```

Wyjście

```
3.141592653589793
2.718281828459045
```



#### Zaokrąglanie do góry do liczby całkowitej

```python
from math import ceil

print( ceil(3.0) )

print( ceil(3.1) )

print( ceil(3.8) )
```

Wyjście

```
3
4
4
```



#### Zaokrąglanie w dół do liczby całkowitej

```python
from math import floor

print( floor(3.0) )

print( floor(3.1) )

print( floor(3.8) )
```

Wyjście

```
3
3
3
```



#### Silnia

```python
from math import factorial

print( factorial(0) )

print( factorial(2) )

print( factorial(3) )
```

Wyjście

```
1
2
6
```



#### Reszta z dzielenia (większa precyzja niż "%")

```python
from math import *

print( fmod(7, 3) )

print( fmod(6, 3) )

print( fmod(-7, 3) )
```

Wyjście

```
1.0
0.0
-1.0
```



#### Największy wspólny dzielnik

```python
from math import *

print( gcd(12, 9) )

print( gcd(2, 3) )

print( gcd(2, 2) )

print( gcd(1, 0) )

print( gcd(0, 0) )
```

Wyjście

```
3
1
2
1
0
```



#### Sumowanie iterowanego obiektu (większa precyzja niż "sum()")

```python
from math import *

numbers = [2.5, 3, 4, -5]

numbers_sum = fsum(numbers)
print(numbers_sum)
```

Wyjście

```
4.5
```



#### Sprawdzanie czy liczba jest różna od "inf" i "nan"

```python
from math import *

num_1 = 41.8

num_2 = nan

num_3 = inf

print( isfinite(num_1) )

print( isfinite(num_2) )

print( isfinite(num_3) )
```

Wyjście

```
True
False
False
```



#### Sprawdzanie czy liczba jest +/- nieskończonością "inf"

```python
from math import *

num_1 = inf # math.inf

num_2 = 999_999_999

print( isinf(num_1) )

print( num_1 > num_2 )

print( isinf(num_2) )
```

Wyjście

```
True
True
False
```



#### Sprawdzanie czy liczba jest "nan"

```python
from math import *

num_1 = nan # math.nan

num_2 = 999_999_999

print( isnan(num_1) )

print( num_1 > num_2 )

print( num_1 <= num_2 )

print( isnan(num_2) )
```

Wyjście

```
True
False
False
False
```



#### Zwracanie części ułamkowej i całkowitej

```python
from math import *

print( modf(2.1) )

print( modf(0.99) )

print( modf(9) )

print( modf(9.0) )
```

Wyjście

```
(0.10000000000000009, 2.0)
(0.99, 0.0)
(0.0, 9.0)
(0.0, 9.0)
```



#### Zwracanie części całkowitej

```python
from math import *

print( trunc(2.1) )

print( trunc(0.99) )

print( trunc(9) )

print( trunc(9.0) )
```

Wyjście

```
2
0
9
9
```



#### Obliczanie logarytmu

```python
from math import *

print( log(4, 2) ) # log(x[, b]); b (defaults to e)

print( log(2, 4) )

print( log(3**0.5, 3) )

print( log(3, 3**0.5) )
```

Wyjście

```
2.0
0.5
0.4999999999999999
2.0000000000000004
```



#### Obliczanie potęgi

```python
from math import *

print( pow(0, 1) )

print( pow(0, 0) )

print( pow(1, 0) )

print( pow(2, 4) )

print( pow(3, 1/2) )

print( pow(27, 1/3) )
```

Wyjście

```
0.0
1.0
1.0
16.0
1.7320508075688772
3.0
```



#### Obliczanie pierwiastka kwadratowego

```python
from math import *

print( sqrt(0) )

print( sqrt(1) )

print( sqrt(2) )

print( sqrt(4) )
```

Wyjście

```
0.0
1.0
1.4142135623730951
2.0
```



#### Zamiana ze stopni na radiany

```python
from math import *

print( radians(180) )

print( radians(90) )

print( radians(30) )
```

Wyjście

```
3.141592653589793
1.5707963267948966
0.5235987755982988
```



#### Zamiana z radianów na stopnie

```python
from math import *

print( degrees(pi) )

print( degrees(pi/2) )

print( degrees(pi/6) )
```

Wyjście

```
180.0
90.0
29.999999999999996
```



#### Obliczanie sinusa (rad)

```python
from math import *

print( sin(-pi) )

print( sin(0) )

print( sin(pi) )

print( sin(pi/6) )

print( sin(pi/2) )

print( sin(2*pi) )
```

Wyjście

```
-1.2246467991473532e-16
0.0
1.2246467991473532e-16
0.49999999999999994
1.0
-2.4492935982947064e-16
```



#### Obliczanie cosinusa (rad)

```python
from math import *

print( cos(-pi) )

print( cos(0) )

print( cos(pi) )

print( cos(pi/6) )

print( cos(pi/2) )

print( cos(2*pi) )
```

Wyjście

```
-1.0
1.0
-1.0
0.8660254037844387
6.123233995736766e-17
1.0
```



#### Obliczanie tangensa (rad)

```python
from math import *

print( tan(-pi) )

print( tan(0) )

print( tan(pi) )

print( tan(pi/4) )

print( tan(pi/6) )

print( tan(pi/2) ) # !
```

Wyjście

```
1.2246467991473532e-16
0.0
-1.2246467991473532e-16
0.9999999999999999
0.5773502691896257
1.633123935319537e+16
```



### Operacje na liczbach zmiennoprzecinkowych z modułem "decimal" ([docs.python.org](https://docs.python.org/3.6/library/decimal.html))

#### Importowanie modułu

```python
from decimal import *
print( getcontext() )
```

Wyjście

```
Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999, capitals=1, clamp=0, flags=[], traps=[InvalidOperation, DivisionByZero, Overflow])
```



#### Operacje na liczbach i ustawianie precyzji

```python
from decimal import *

print( 0.1 + 0.2 )

print( Decimal('0.1') + Decimal('0.2') )

getcontext().prec = 50

print( Decimal('1') / Decimal('7') )

getcontext().prec = 4

print( Decimal('1') / Decimal('7') )

getcontext().prec = 28

print( Decimal('0.1') * Decimal('0.9') )

print( Decimal('0.1') * Decimal('0.90') )
```

Wyjście

```
0.30000000000000004
0.3
0.14285714285714285714285714285714285714285714285714
0.1429
0.09
0.090
```



#### Zaokrąglanie

```
ROUND_CEILING 	- always round upwards towards infinity

ROUND_DOWN 		- always round toward zero

ROUND_FLOOR 	- always round down towards negative infinity

ROUND_HALF_DOWN - rounds away from zero if the last significant digit is greater than or equal to 5, otherwise toward zero

ROUND_HALF_EVEN - like ROUND_HALF_DOWN except that if the value is 5 then the preceding digit is examined; even values cause the result to be rounded down and odd digits cause the result to be rounded up.

ROUND_HALF_UP 	- like ROUND_HALF_DOWN except if the last significant digit is 5 the value is rounded away from zero

ROUND_UP 		- round away from zero

ROUND_05UP 		- round away from zero if the last digit is 0 or 5, otherwise towards zero
```

```python
from decimal import *

getcontext().prec = 2

print( Decimal('0.15').quantize( Decimal('0.1') ) )

print( Decimal('0.25').quantize( Decimal('0.1') ) )

print( Decimal('-0.15').quantize( Decimal('0.1') ) )

print( Decimal('-0.25').quantize( Decimal('0.1') ) )

print()
getcontext().rounding = ROUND_HALF_UP

print( Decimal('0.15').quantize( Decimal('0.1') ) )

print( Decimal('0.25').quantize( Decimal('0.1') ) )

print( Decimal('-0.15').quantize( Decimal('0.1') ) )

print( Decimal('-0.25').quantize( Decimal('0.1') ) )
```

Wyjście

```
0.2
0.2
-0.2
-0.2

0.2
0.3
-0.2
-0.3
```



### Operacje na ułamkach z modułem "fractions" ([docs.python.org](https://docs.python.org/3.6/library/fractions.html))

#### Importowanie modułu

```python
from fractions import Fraction

print( Fraction(16, -10) )

print( Fraction(123) )

print( Fraction() )

print( Fraction('3/7') )

print( Fraction(' -3/7 ') )

print( Fraction('1.414213 \t\n') )

print( Fraction('-.125') )

print( Fraction('7e-6') )

print( Fraction(2.25) )

print( Fraction(1.1) )

from decimal import Decimal
print( Fraction(Decimal('1.1')) )
```

Wyjście

```
-8/5
123
0
3/7
-3/7
1414213/1000000
-1/8
7/1000000
9/4
2476979795053773/2251799813685248
11/10
```



### Liczby pseudolosowe z  modułem "random" ([docs.python.org](https://docs.python.org/3.6/library/random.html))

#### Importowanie modułu

```python
import random
```



#### Ustawianie nasiona "seed"

```python
import random

random.seed(1) # random.seed() -> the current system time is used. If randomness sources are provided by the operating system, they are used instead of the system time 

print(random.randint(1, 1_000_000))
```

Wyjście

```
140892
```



#### Losowa liczba z przedziału, odpowiednik "range()"

```python
from random import *

print( randrange(1, 11) )  # random.randrange(start, stop[, step])

print( randrange(1, 10, 2) ) # random odd from 1 to 9

print( randrange(2, 11, 2) ) # random even from 2 to 10
```

Przykładowe wyjście

```
5
7
6
```



#### Losowa liczba całkowita z przedziału

```python
from random import *

print( randint(1, 10) )  # random int from 1 to 10

print( randint(100, 1000) ) # random int from 100 to 1000
```

Przykładowe wyjście

```
7
805
```



#### Losowa liczba zmiennoprzecinkowa z przedziału

```python
import random

print(random.uniform(2.1, 6.5)) 
```

Przykładowe wyjście

```
3.5074262511600964
```



#### Losowa liczba z przedziału [0.0, 1.0)

```python
from random import *

print( random() )

print( random() )
```

Przykładowe wyjście

```
0.9624721742829768
0.02406206377438813
```



#### Losowy element z listy

```python
from random import *

my_list = ['a', 52, 12.4, 'b']

print( choice(my_list) )

print( choice(my_list) )
```

Przykładowe wyjście

```
a
52
```



#### Losowe elementy z listy

```python
from random import *

my_list = ['apple', 'banana', 'cherry']

print( choices(my_list, k = 10) ) # random.choices(population, weights=None, k=1)

print( choices(my_list, weights = [10, 1, 1], k = 10) )
```

Przykładowe wyjście

```
['banana', 'cherry', 'apple', 'apple', 'cherry', 'banana', 'banana', 'apple', 'cherry', 'apple']
['apple', 'cherry', 'apple', 'banana', 'apple', 'apple', 'cherry', 'apple', 'banana', 'apple']
```



#### Losowe elementy z listy bez powtórzeń

```python
import random

mylist = ["apple", "banana", "cherry"]

print(random.sample(mylist, k=2)) 
```

Przykładowe wyjście

```
['cherry', 'apple']
```



#### Losowa kolejność / przetasowanie listy

```python
import random

mylist = ["apple", "banana", "cherry"]
random.shuffle(mylist)

print(mylist) 
```

Przykładowe wyjście

```
['cherry', 'apple', 'banana']
```



### Moduł "itertools" ([docs.python.org](https://docs.python.org/3.6/library/itertools.html))

#### Importowanie modułu

```python
import itertools
```



#### Nieskończony iterator "count()"

```python
import itertools as it

a = it.count(0) # itertools.count(start=0[, step=1])

print( list(it.islice(a, 10)) ) # 10 first elements of infinite
```

Wyjście

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```



#### Nieskończony iterator "cycle()"

```python
import itertools as it

a = it.cycle([-1, 1]) # itertools.cycle(iterable)

print( list(it.islice(a, 10)) ) # 10 first elements of infinite
```

Wyjście

```
[-1, 1, -1, 1, -1, 1, -1, 1, -1, 1]
```



#### Nieskończony iterator "repeat()"

```python
import itertools as it

a = it.repeat('apple') # itertools.repeat(object[, times])

print( list(it.islice(a, 4)) ) # 4 first elements of infinite
```

Wyjście

```
['apple', 'apple', 'apple', 'apple']
```



#### Wypisywanie kolejnego elementu iteratora

```python
import itertools as it

a = it.count(0)

print( next(a) )
print( next(a) )
```

Wyjście

```
0
1
```



#### Wypisywanie n elementów iteratora

```python
import itertools as it

a = it.cycle([-1, 0, 1])

print( list(it.islice(a, 0, 4)) ) # itertools.islice(iterable, start, stop[, step])

print( list(it.islice(a, 0, 2)) )
```

Wyjście

```
[-1, 0, 1, -1]
[0, 1]
```



#### Generator i funkcja

```python
def evens():
    """Generate even integers, starting with 0."""
    n = 0
    while True:
        yield n
        n += 2

evens = evens()
result = list(next(evens) for _ in range(5))

print(result)

print(next(evens))
```

Wyjście

```
[0, 2, 4, 6, 8]
10
```



#### Kombinacje

```python
import itertools as it

a = it.combinations([1, 2, 3], 2) # itertools.combinations(iterable, r); r = length

b = it.combinations('ABCD', 2)

print( list(a) )

print( list(b) )
```

Wyjście

```
[(1, 2), (1, 3), (2, 3)]
[('A', 'B'), ('A', 'C'), ('A', 'D'), ('B', 'C'), ('B', 'D'), ('C', 'D')]
```



#### Kombinacje z powtórzeniami

```python
import itertools as it

a = it.combinations_with_replacement([1, 2], 2) # itertools.combinations_with_replacement(iterable, r); r = length

print( list(a) )
```

Wyjście

```
[(1, 1), (1, 2), (2, 2)]
```



#### Permutacje

```python
import itertools as it

a = it.permutations('abc') # itertools.permutations(iterable, r=None); r = length

print( list(a) )
```

Wyjście

```
[('a', 'b', 'c'), ('a', 'c', 'b'), ('b', 'a', 'c'), ('b', 'c', 'a'), ('c', 'a', 'b'), ('c', 'b', 'a')]
```



#### Dodawanie kolejnych elementów

```python
import itertools as it

a = it.accumulate(it.count(1)) # itertools.accumulate(iterable[, func])
# 1 + 2 + 3 + 4 + 5 + ...
print( list(next(a) for _ in range(5)) )
```

Wyjście

```
[1, 3, 6, 10, 15]
```



#### Łączenie elementów

```python
import itertools as it

a = ['abc']

b = 'def'

c = [1, 2, 3]

d = it.chain(a, b, c) # chain(*iterables)

print( list(d) )
```

Wyjście

```
['abc', 'd', 'e', 'f', 1, 2, 3]
```



#### Wybieranie elementów "compress()"

```python
import itertools as it

a = it.compress('ABCDEF', [1,0,1,0,1,1]) # (d[0] if s[0]), (d[1] if s[1])

print( list(a) )
```

Wyjście

```
['A', 'C', 'E', 'F']
```



#### Wypisywanie dopóki warunek jest spełniony

```python
import itertools as it

a = it.takewhile(lambda x: x < 3, [0, 1, 2, 3, 4])  # 0, 1, 2

print( list(a) )
```

Wyjście

```
[0, 1, 2]
```



#### Pomijanie aż warunek jest spełniony

```python
import itertools as it

a = it.dropwhile(lambda x: x < 3, [0, 1, 2, 3, 4])  # 3, 4

print( list(a) )
```

Wyjście

```
[3, 4]
```



#### Filtrowanie elementów które nie spełniają warunku

```python
import itertools as it

a = it.filterfalse(lambda x: x <= 0, [0, 1, -1, 2, -2])

print( list(a) )
```

Wyjście

```
[1, 2]
```



#### Grupowanie elementów

```python
import itertools as it

data = [{'name': 'Alan', 'age': 34},
        {'name': 'Catherine', 'age': 34},
        {'name': 'Betsy', 'age': 29},
        {'name': 'David', 'age': 33}]

grouped_data = it.groupby(data, key=lambda x: x['age'])
for key, grp in grouped_data:
    print('{}: {}'.format(key, list(grp)))
```

Wyjście

```
34: [{'name': 'Alan', 'age': 34}, {'name': 'Catherine', 'age': 34}]
29: [{'name': 'Betsy', 'age': 29}]
33: [{'name': 'David', 'age': 33}]
```



#### Obliczanie wartości funkcji dla elementów iterowanego obiektu

```python
import itertools as it

a = it.starmap(pow, [(2,5), (3,2), (10,3)]) # itertools.starmap(function, iterable)

# 32 9 1000

print( list(a) )
```

Wyjście

```
[32, 9, 1000]
```



#### Tworzenie niezależnej kopii iteratora

```python
import itertools as it

iterator1, iterator2 = it.tee([1, 2, 3, 4, 5], 2) # itertools.tee(iterable, n=2)

print( list(iterator1) )

print( list(iterator1) ) # iterator1 is now exhausted.

print( list(iterator2) ) # iterator2 works independently of iterator1
```

Wyjście

```
[1, 2, 3, 4, 5]
[]
[1, 2, 3, 4, 5]
```



#### Łączenie iterowanego obiektu z wypełnieniem

```python
import itertools as it
x = [1, 2, 3, 4, 5]
y = ['a', 'b', 'c']

print( list(zip(x, y)) )

print( list(it.zip_longest(x, y)) ) # itertools.zip_longest(*iterables, fillvalue=None)
```

Wyjście

```
[(1, 'a'), (2, 'b'), (3, 'c')]
[(1, 'a'), (2, 'b'), (3, 'c'), (4, None), (5, None)]
```



### Moduł  "datetime" ([docs.python.org](https://docs.python.org/3.6/library/datetime.html))

#### Importowanie modułu

```python
import datetime
```



#### Uzyskiwanie aktualnej daty

```python
import datetime

x = datetime.datetime.now()

print(x.year)
```

Przykładowe wyjście

```
2021
```



#### Wpisywanie daty

```python
import datetime

x = datetime.datetime(2020, 5, 17)

print(x) 
```

Wyjście

```
2020-05-17 00:00:00
```



#### Różnica między datami

```python
from datetime import datetime

a = datetime(2020, 1, 1)

b = datetime(2021, 1, 1)

print(a)
print(b)
print()
print( a-b )
```

Wyjście

```
2020-01-01 00:00:00
2021-01-01 00:00:00

-366 days, 0:00:00
```



#### Różnica w czasie

```python
from datetime import datetime, timedelta

a = datetime(2020, 1, 1)

print(a)
print()

print( a + timedelta(hours=30) ) # datetime.timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, minutes=0, hours=0, weeks=0)

print( timedelta(hours=30) * 3 )

td = timedelta(hours=1) - timedelta(minutes = 33)

print( td.seconds // 60, 'minutes' )
```

Wyjście

```
2020-01-01 00:00:00

2020-01-02 06:00:00
3 days, 18:00:00
27 minutes
```



## Wybrane algorytmy

------

#### Największa wspólna wielokrotność i najmniejszy wspólny dzielnik

```python
# Python program to find the L.C.M. of two input number

# This function computes GCD 
def compute_gcd(x, y):

   while(y):
       x, y = y, x % y
   return x

# This function computes LCM
def compute_lcm(x, y):
   lcm = (x*y)//compute_gcd(x,y)
   return lcm

num1 = 54
num2 = 24 

print("The G.C.D. is", compute_gcd(num1, num2))
print("The L.C.M. is", compute_lcm(num1, num2))
```

Wyjście

```
The G.C.D. is 6
The L.C.M. is 216
```



#### Sortowanie bąbelkowe

```python
def bubble_sort(nums):
    # We set swapped to True so the loop looks runs at least once
    swapped = True
    while swapped:
        swapped = False
        for i in range(len(nums) - 1):
            if nums[i] > nums[i + 1]:
                # Swap the elements
                nums[i], nums[i + 1] = nums[i + 1], nums[i]
                # Set the flag to True so we'll loop again
                swapped = True


# Verify it works
random_list_of_nums = [5, 2, 1, 8, 4]
bubble_sort(random_list_of_nums)
print(random_list_of_nums)
```

Wyjście

```
[1, 2, 4, 5, 8]
```



#### Sortowanie przez wybór

```python
def selection_sort(nums):
    # This value of i corresponds to how many values were sorted
    for i in range(len(nums)):
        # We assume that the first item of the unsorted segment is the smallest
        lowest_value_index = i
        # This loop iterates over the unsorted items
        for j in range(i + 1, len(nums)):
            if nums[j] < nums[lowest_value_index]:
                lowest_value_index = j
        # Swap values of the lowest unsorted element with the first unsorted
        # element
        nums[i], nums[lowest_value_index] = nums[lowest_value_index], nums[i]


# Verify it works
random_list_of_nums = [12, 8, 3, 20, 11]
selection_sort(random_list_of_nums)
print(random_list_of_nums)
```

Wyjście

```
[3, 8, 11, 12, 20]
```



#### Sortowanie przez wstawianie

```python
def insertion_sort(nums):
    # Start on the second element as we assume the first element is sorted
    for i in range(1, len(nums)):
        item_to_insert = nums[i]
        # And keep a reference of the index of the previous element
        j = i - 1
        # Move all items of the sorted segment forward if they are larger than
        # the item to insert
        while j >= 0 and nums[j] > item_to_insert:
            nums[j + 1] = nums[j]
            j -= 1
        # Insert the item
        nums[j + 1] = item_to_insert


# Verify it works
random_list_of_nums = [9, 1, 15, 28, 6]
insertion_sort(random_list_of_nums)
print(random_list_of_nums)
```

Wyjście

```
[1, 6, 9, 15, 28]
```



#### Sortowanie przez kopcowanie

```python
def heapify(nums, heap_size, root_index):
    # Assume the index of the largest element is the root index
    largest = root_index
    left_child = (2 * root_index) + 1
    right_child = (2 * root_index) + 2

    # If the left child of the root is a valid index, and the element is greater
    # than the current largest element, then update the largest element
    if left_child < heap_size and nums[left_child] > nums[largest]:
        largest = left_child

    # Do the same for the right child of the root
    if right_child < heap_size and nums[right_child] > nums[largest]:
        largest = right_child

    # If the largest element is no longer the root element, swap them
    if largest != root_index:
        nums[root_index], nums[largest] = nums[largest], nums[root_index]
        # Heapify the new root element to ensure it's the largest
        heapify(nums, heap_size, largest)


def heap_sort(nums):
    n = len(nums)

    # Create a Max Heap from the list
    # The 2nd argument of range means we stop at the element before -1 i.e.
    # the first element of the list.
    # The 3rd argument of range means we iterate backwards, reducing the count
    # of i by 1
    for i in range(n, -1, -1):
        heapify(nums, n, i)

    # Move the root of the max heap to the end of
    for i in range(n - 1, 0, -1):
        nums[i], nums[0] = nums[0], nums[i]
        heapify(nums, i, 0)


# Verify it works
random_list_of_nums = [35, 12, 43, 8, 51]
heap_sort(random_list_of_nums)
print(random_list_of_nums)
```

Wyjście

```
[8, 12, 35, 43, 51]
```



#### Sortowanie przez scalanie

```python
def merge(left_list, right_list):
    sorted_list = []
    left_list_index = right_list_index = 0

    # We use the list lengths often, so its handy to make variables
    left_list_length, right_list_length = len(left_list), len(right_list)

    for _ in range(left_list_length + right_list_length):
        if left_list_index < left_list_length and right_list_index < right_list_length:
            # We check which value from the start of each list is smaller
            # If the item at the beginning of the left list is smaller, add it
            # to the sorted list
            if left_list[left_list_index] <= right_list[right_list_index]:
                sorted_list.append(left_list[left_list_index])
                left_list_index += 1
            # If the item at the beginning of the right list is smaller, add it
            # to the sorted list
            else:
                sorted_list.append(right_list[right_list_index])
                right_list_index += 1

        # If we've reached the end of the of the left list, add the elements
        # from the right list
        elif left_list_index == left_list_length:
            sorted_list.append(right_list[right_list_index])
            right_list_index += 1
        # If we've reached the end of the of the right list, add the elements
        # from the left list
        elif right_list_index == right_list_length:
            sorted_list.append(left_list[left_list_index])
            left_list_index += 1

    return sorted_list


def merge_sort(nums):
    # If the list is a single element, return it
    if len(nums) <= 1:
        return nums

    # Use floor division to get midpoint, indices must be integers
    mid = len(nums) // 2

    # Sort and merge each half
    left_list = merge_sort(nums[:mid])
    right_list = merge_sort(nums[mid:])

    # Merge the sorted lists into a new one
    return merge(left_list, right_list)


# Verify it works
random_list_of_nums = [120, 45, 68, 250, 176]
random_list_of_nums = merge_sort(random_list_of_nums)
print(random_list_of_nums)
```

Wyjście

```
[45, 68, 120, 176, 250]
```



#### Sortowanie "quicksort"

```python
# There are different ways to do a Quick Sort partition, this implements the
# Hoare partition scheme. Tony Hoare also created the Quick Sort algorithm.
def partition(array, start, end):
    pivot = array[start]
    low = start + 1
    high = end

    while True:
        # If the current value we're looking at is larger than the pivot
        # it's in the right place (right side of pivot) and we can move left,
        # to the next element.
        # We also need to make sure we haven't surpassed the low pointer, since that
        # indicates we have already moved all the elements to their correct side of the pivot
        while low <= high and array[high] >= pivot:
            high = high - 1

        # Opposite process of the one above
        while low <= high and array[low] <= pivot:
            low = low + 1

        # We either found a value for both high and low that is out of order
        # or low is higher than high, in which case we exit the loop
        if low <= high:
            array[low], array[high] = array[high], array[low]
            # The loop continues
        else:
            # We exit out of the loop
            break

    array[start], array[high] = array[high], array[start]

    return high

def quick_sort(array, start, end):
    if start >= end:
        return

    p = partition(array, start, end)
    quick_sort(array, start, p-1)
    quick_sort(array, p+1, end)

array = [29,99,27,41,66,28,44,78,87,19,31,76,58,88,83,97,12,21,44]

quick_sort(array, 0, len(array) - 1)
print(array)
```

Wyjście

```
[12, 19, 21, 27, 28, 29, 31, 41, 44, 44, 58, 66, 76, 78, 83, 87, 88, 97, 99]
```



#### Proste sprawdzanie czy liczba jest pierwsza

```python
# Program to check if a number is prime or not

num = 407

# To take input from the user
#num = int(input("Enter a number: "))

# prime numbers are greater than 1
if num > 1:
   # check for factors
   for i in range(2,num): # range(2,int(num**0.5) + 1)
       if (num % i) == 0:
           print(num,"is not a prime number")
           print(i,"times",num//i,"is",num)
           break
   else:
       print(num,"is a prime number")
       
# if input number is less than
# or equal to 1, it is not prime
else:
   print(num,"is not a prime number")
```

Wyjście

```
407 is not a prime number
11 times 37 is 407
```



#### Liczby pierwsze z przedziału

```python
# Python program to display all the prime numbers within an interval

lower = 900
upper = 1000

print("Prime numbers between", lower, "and", upper, "are:")

for num in range(lower, upper + 1):
   # all prime numbers are greater than 1
   p = True
   if num > 1:
      for i in range(2, int(num**0.5) + 1):
         if (num % i) == 0:
            p = False
            break
   if p:
      print(num, end=", ")
```

Wyjście

```
Prime numbers between 900 and 1000 are:
907, 911, 919, 929, 937, 941, 947, 953, 967, 971, 977, 983, 991, 997,
```



#### Wyszukiwanie binarne

```python
def binarySearch(array, x, low, high):
    # Repeat until the pointers low and high meet each other
    while low <= high:
        mid = low + (high - low)//2
        if array[mid] == x:
            return mid
        elif array[mid] < x:
            low = mid + 1
        else:
            high = mid - 1
    return -1

array = [3, 4, 5, 6, 7, 8, 9]
x = 4
result = binarySearch(array, x, 0, len(array)-1)

if result != -1:
    print("Element is present at index " + str(result))
else:
    print("Not found")
```

Wyjście

```
Element is present at index 1
```



#### Sprawdzanie czy wyrazy są palindromami

```python
# Program to check if a string is palindrome or not
my_str = 'aIbohPhoBiA'

# make it suitable for caseless comparison
my_str = my_str.casefold()

# reverse the string
rev_str = reversed(my_str)

# check if the string is equal to its reverse
if list(my_str) == list(rev_str):
   print("The string is a palindrome.")
else:
   print("The string is not a palindrome.")
```

Wyjście

```
The string is a palindrome.
```



#### Wyszukiwanie wzorca w tekście

```python
# Returns true if s1 is substring of s2
def isSubstring(s1, s2):
    M = len(s1)
    N = len(s2)
 
    # A loop to slide pat[] one by one
    for i in range(N - M + 1):
 
        # For current index i,
        # check for pattern match
        for j in range(M):
            if (s2[i + j] != s1[j]):
                break
             
        if j + 1 == M :
            return i
 
    return -1
 
# Driver Code
s1 = "for"
s2 = "geeksforgeeks"
res = isSubstring(s1, s2)
if res == -1 :
    print("Not present")
else:
    print("Present at index " + str(res)
```

Wyjście

```
Present at index 5
```



#### Schemat Hornera - Szybkie obliczanie wartości wielomianu

```python
# returns value of poly[0]x(n-1)
# + poly[1]x(n-2) + .. + poly[n-1]
def horner(poly, n, x):
    # Initialize result
    result = poly[0] 
  
    # Evaluate value of polynomial
    # using Horner's method
    for i in range(1, n):
        result = result*x + poly[i]
    return result
  
# Driver program to
# test above function.
 
# Let us evaluate value of
# 2x3 - 6x2 + 2x - 1 for x = 3
poly = [2, -6, 2, -1]
x = 3
n = len(poly)
 
print("Value of polynomial is " , horner(poly, n, x))
```

Wyjście

```
Value of polynomial is  5
```



#### Szyfr cezara

```python
#A python program to illustrate Caesar Cipher Technique
def encrypt(text,s):
    result = ""
 
    # traverse text
    for i in range(len(text)):
        char = text[i]
 
        # Encrypt uppercase characters
        if (char.isupper()):
            result += chr((ord(char) + s-65) % 26 + 65)
 
        # Encrypt lowercase characters
        else:
            result += chr((ord(char) + s - 97) % 26 + 97)
 
    return result
 
#check the above function
text = "ATTACKATONCE"
s = 4
print "Text  : " + text
print "Shift : " + str(s)
print "Cipher: " + encrypt(text,s)
```

Wyjście

```
Text  : ATTACKATONCE
Shift : 4
Cipher: EXXEGOEXSRGI
```



#### Działania na ułamkach

```python
def NWD(a, b):
    if b == 0:
        return a
    else:
        return NWD(b, a % b)

def dodaj(l1, m1, l2, m2):
    m = m1 * m2
    l1 = l1 * (m / m1)
    l2 = l2 * (m / m2)
    l = int(l1 + l2)
    return l, m

def odejmij(l1, m1, l2, m2):
    m = m1 * m2
    l1 = l1 * (m / m1)
    l2 = l2 * (m / m2)
    l = int(l1 - l2)
    return l, m

def mnozenie(l1, m1, l2, m2):
    l = int(l1 * l2)
    m = int(m1 * m2)
    return l, m

def dzielenie(l1, m1, l2, m2):
    l = int(l1 * m2)
    m = int(m1 * l2)
    return l, m

def skroc(l, m):
    d = NWD(l, m)
    l = int(l/d)
    m = int(m/d)
    return l, m

l, m = dzielenie(1,3,1,3)
print(skroc(l, m))
```

Wyjście

```
(1, 1)
```



#### Rozkładanie liczby na czynniki

```python
# A function to print all prime factors of 
# a given number n
def primeFactors(n):
    factors = []
    # Print the number of two's that divide n
    while n % 2 == 0:
        factors.append(2)
        n = n // 2
    # n must be odd at this point
    # so a skip of 2 ( i = i + 2) can be used
    for i in range(3,int(n**0.5)+1,2):
        # while i divides n , print i ad divide n
        while n % i == 0:
            factors.append(i)
            n = n // i
    # Condition if n is a prime
    # number greater than 2
    if n > 2:
        factors.append(n)
    return factors
          
# Driver Program to test above function
n = 315
print(primeFactors(n))
```

Wyjście

```
[3, 3, 5, 7]
```



#### Sprawdzanie czy liczba jest doskonała

```python
# Returns true if n is perfect
def isPerfect( n ):
    # To store sum of divisors
    sum = 1
    # Find all divisors and add them
    i = 2
    while i * i <= n:
        if n % i == 0:
            sum = sum + i + n/i
        i += 1
    # If sum of divisors is equal to
    # n, then n is a perfect number
    return (True if sum == n and n!=1 else False)
 
# Driver program
print("Below are all perfect numbers till 10000")
n = 2
for n in range (10000):
    if isPerfect (n):
        print(n , " is a perfect number")
```

Wyjście

```
Below are all perfect numbers till 10000
6  is a perfect number
28  is a perfect number
496  is a perfect number
8128  is a perfect number
```



#### Ciąg Fibonacciego iteracyjnie

```python
def fib(n):
    if n==1 or n==2:
        return 1
    teraz = 1
    poprzednia = 1
    for i in range(3, n+1):
        temp = teraz
        teraz = teraz + poprzednia
        poprzednia = temp
    return teraz

for i in range(1, 11):
    print(fib(i), end=", ")
```

####  Wyjście

```
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 
```



#### Wyznaczanie pierwiastka arytmetycznego - metoda Newtona - Raphsona

```python
eps = 0.000001

def pierwiastek(P, eps):
    a = 1.
    b = P

    while(abs(a-b) >= eps):
        a = (a+b)/2.
        b = P/a
        
    return a

print("{:.6f}".format(pierwiastek(2, eps)))
```

Wyjście

```
1.414214
```



#### Zamiana systemów liczbowych [2-9]

```python
def zamiana(n, podstawa, podstawa2):
    dec = 0
    for i in range(len(n)):
        # zamieniemy na system dziesiętny, używamy schematu hornera
        # aby obliczyć np. 1*2^3 + 0*2^2 + 1*2^1 + 1*2^0
        dec = dec*podstawa + int(n[i])
    m = ""
    i = 0
    while dec > 0:
        # zmieniamy z systemu dziesiętnego na wybraną podstawę
        m += str(dec % podstawa2)
        dec = dec // 8
    return m[::-1]

print(zamiana("1011", 2, 8)) # DEC 11 | OCT 13
```

Wyjście

```
13
```



#### Potęgowanie szybkie

```python
def potega(a, n):
    w = 1
    while n > 0:
        if n%2 == 1: # jeśli bit jest = 1
            w *= a
        a *= a
        n //= 2 # skrócenie o jeden bit
    return w

print(potega(2, 4))
```

Wyjście

```
16
```



#### Znajdowanie miejsca zerowego metodą połowienia przedziałów

```python
def f(x):
    return x*(x*(x-3)+2)-6

def polowienie_przedzialow(a, b, epsilon):
    if (f(a) == 0.):
        return a
    if (f(b) == 0.):
        return b

    while (b-a > epsilon):
        srodek = (a+b)/2

        if (f(srodek) == 0.0):
            return srodek

        if (f(a)*f(srodek)<0):
            b = srodek
        else:
            a = srodek
    return (a+b)/2


def REKURENCYJNE_polowienie_przedzialow(a, b, epsilon):
    if (f(a) == 0.):
        return a
    if (f(b) == 0.):
        return b
    
    srodek = (a+b)/2
    if (b-a <= epsilon):
        return srodek
    
    if( f(a)*f(srodek) < 0 ):
        return REKURENCYJNE_polowienie_przedzialow(a, b, epsilon)
    
    return polowienie_przedzialow(srodek, b, epsilon)

a, b, epsilon = -10, 10, 0.00001
print("{:.5f}".format( polowienie_przedzialow(a, b, epsilon) ))
print("{:.5f}".format( REKURENCYJNE_polowienie_przedzialow(a, b, epsilon) ))
```

Wyjście

```
3.00000
3.00000
```



#### Całkowanie numeryczne - metoda trapezów

```python
def f(x):
    # funkcja zawsze przyjmuje wartosci dodatnie
    # więc można pominąć wartosć bezwzględną
    return x*x+x+2;

def Pole(a, b, n):
    h = (b-a)/n # wysokość trapezów
    S = 0.0
    podstawa_a = f(a)

    for i in range(1, n+1):
        podstawa_b = f(a+h*i)
        S += (podstawa_a + podstawa_b)
        podstawa_a = podstawa_b

    return S*0.5*h

a, b, n = 0, 10, 1000

print("{:.2f}".format( Pole(a, b, n) ))
```

Wyjście

```
403.33
```



#### Całkowanie numeryczne - metoda prostokątów

```python
def f(x):
    # funkcja zawsze przyjmuje wartosci dodatnie
    # więc można pominąć wartosć bezwzględną
    return x*x+x+2;

def Pole(a, b, n):
    x = (b-a)/n
    S = 0.0
    srodek = a+(b-a)/(2.0*n)

    for i in range(n):
        S += f(srodek)
        srodek += x
    return S*x

a, b, n = 0, 10, 1000

print("{:.2f}".format( Pole(a, b, n) ))
```

Wyjście

```
403.33
```



#### Sprawdzanie czy wyrazy są anagramami

```python
def areAnagram(str1, str2):
    # Get lengths of both strings
    n1 = len(str1)
    n2 = len(str2)
    # If lenght of both strings is not same, then
    # they cannot be anagram
    if n1 != n2:
        return 0
    # Sort both strings
    str1 = sorted(str1)
    str2 = sorted(str2)
    # Compare sorted strings
    for i in range(0, n1):
        if str1[i] != str2[i]:
            return 0
    return 1

# Driver code
str1 = "test"
str2 = "ttes"
  
# Function Call
if areAnagram(str1, str2):
    print("The two strings are anagram of each other")
else:
    print("The two strings are not anagram of each other")
```

Wyjście

```
The two strings are anagram of each other
```



#### Sortowanie leksykograficzne

```python
def klucz(x):
    return (x[0], -x[1])

studenci = [
    ["Kowalski", 3.12],
    ["Kasprowicz", 4.40],
    ["Nowak", 6.00],
    ["Kosak", 5.44],
    ["Nasiadka", 5.32],
    ["Nowicki", 3.44],
    ["Kanigowski", 4.00],
    ["Danusiak", 4.00],
    ["Dworznik", 4.20],
    ["Kaspro", 3.00],
    ["Kasprowicz", 4.00],
    ["Kasprowicz", 3.10],
    ["Danusiak", 2.00],
    ["Danusiak", 2.14]
    ]

print(sorted(studenci, key=klucz))
```

Wyjście

```
[['Danusiak', 4.0], ['Danusiak', 2.14], ['Danusiak', 2.0], ['Dworznik', 4.2], ['Kanigowski', 4.0], ['Kaspro', 3.0], ['Kasprowicz', 4.4], ['Kasprowicz', 4.0], ['Kasprowicz', 3.1], ['Kosak', 5.44], ['Kowalski', 3.12], ['Nasiadka', 5.32], ['Nowak', 6.0], ['Nowicki', 3.44]]
```



#### Sprawdzanie warunku trójkąta

```python
def trojkat(a, b, c):
    return a>0 and b>0 and c>0 \
           and a+b>c and a+c>b and b+c>a

print(trojkat(10, 1, 1))
print(trojkat(10, 1, 10))
```

Wyjście

```
False
True
```



#### Szyfr przestawieniowy

```python
def kodowanie(napis):
    napis = list(napis)

    for i in range(0, len(napis)-1, 2): # przesuwamy o dwa znaki
        temp = napis[i]
        napis[i] = napis[i+1]
        napis[i+1] = temp

    wynik = ""
    for znak in napis:
        wynik += znak

    return wynik

print(kodowanie("alamakota")) # lamakatoa
print(kodowanie("lamakatoa")) # alamakota
```

Wyjście

```
lamakatoa
alamakota
```



#### Sprawdzanie czy dwa odcinki przecinają się

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y


# Given three colinear points p, q, r, the function checks if
# point q lies on line segment 'pr'
def onSegment(p, q, r):
    if (
        (q.x <= max(p.x, r.x))
        and (q.x >= min(p.x, r.x))
        and (q.y <= max(p.y, r.y))
        and (q.y >= min(p.y, r.y))
    ):
        return True
    return False


def orientation(p, q, r):
    # to find the orientation of an ordered triplet (p,q,r)
    # function returns the following values:
    # 0 : Colinear points
    # 1 : Clockwise points
    # 2 : Counterclockwise

    # See https://www.geeksforgeeks.org/orientation-3-ordered-points/amp/
    # for details of below formula.

    val = (float(q.y - p.y) * (r.x - q.x)) - (float(q.x - p.x) * (r.y - q.y))
    if val > 0:

        # Clockwise orientation
        return 1
    elif val < 0:

        # Counterclockwise orientation
        return 2
    else:

        # Colinear orientation
        return 0


# The main function that returns true if
# the line segment 'p1q1' and 'p2q2' intersect.
def doIntersect(p1, q1, p2, q2):

    # Find the 4 orientations required for
    # the general and special cases
    o1 = orientation(p1, q1, p2)
    o2 = orientation(p1, q1, q2)
    o3 = orientation(p2, q2, p1)
    o4 = orientation(p2, q2, q1)

    # General case
    if (o1 != o2) and (o3 != o4):
        return True

    # Special Cases

    # p1 , q1 and p2 are colinear and p2 lies on segment p1q1
    if (o1 == 0) and onSegment(p1, p2, q1):
        return True

    # p1 , q1 and q2 are colinear and q2 lies on segment p1q1
    if (o2 == 0) and onSegment(p1, q2, q1):
        return True

    # p2 , q2 and p1 are colinear and p1 lies on segment p2q2
    if (o3 == 0) and onSegment(p2, p1, q2):
        return True

    # p2 , q2 and q1 are colinear and q1 lies on segment p2q2
    if (o4 == 0) and onSegment(p2, q1, q2):
        return True

    # If none of the cases
    return False


# Driver program to test above functions:
p1 = Point(1, 1)
q1 = Point(10, 1)
p2 = Point(1, 2)
q2 = Point(10, 2)

if doIntersect(p1, q1, p2, q2):
    print("Yes")
else:
    print("No")

p1 = Point(10, 0)
q1 = Point(0, 10)
p2 = Point(0, 0)
q2 = Point(10, 10)

if doIntersect(p1, q1, p2, q2):
    print("Yes")
else:
    print("No")

p1 = Point(-5, -5)
q1 = Point(0, 0)
p2 = Point(1, 1)
q2 = Point(10, 10)

if doIntersect(p1, q1, p2, q2):
    print("Yes")
else:
    print("No")
```

Wyjście

```
No
Yes
No
```

#### Wydawanie reszty metodą zachłanną

#### Jednoczesne znajdowanie największego i najmniejszego elementu w zbiorze: algorytm naiwny i optymalny

#### Kody znaków o zmiennej długości, np. alfabet Morse'a, kod Huffmana

#### Szyfr z kluczem jawnym (RSA)

#### Wykorzystanie algorytmów szyfrowania, np. w podpisie elektronicznym

#### Badanie położenia punktów względem prostej

#### Badanie przynależności punktu do odcinka

#### Przynależność punktu do obszaru

#### Konstrukcje rekurencyjne: drzewo binarne, dywan Sierpińskiego, płatek Kocha