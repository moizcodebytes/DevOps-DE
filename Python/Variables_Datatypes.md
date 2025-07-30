* ## VARIABLES
Variable hold a value which can be called later in the program. Variable is a place holder in memory to store the value assigned to it.

```python
>>> a = 1
>>> x = 1.23
>>> Name = "JOHN"
>>> d = None

```

* ## DATATYPES
Datatypes specifies the type of value the variable holds.  
#### To get the type of variable

```python
>>> type(a)
<class 'int'>
>>> type(x)
<class 'float'>
>>> type(name)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'name' is not defined
>>> type(Name)
<class 'str'>
>>> type(d)
<class 'NoneType'>

```
Note : Variables are case sensitive

#### Types of Datatypes

1. Numeric : int, float,complex.
2. Text : str
3. Boolean : True or False
4. Sequenced data    
      List : A **Mutable** ordered collection of data with elements seperated by comma and enclosed in **square []** brackets.  [Lists](List)
   ``` python
    >>> list1 = ["John",25,3.5,["India","Hyderabad"]]
    >>> print(list1)
    ['John', 25, 3.5, ['India', 'Hyderabad']]
    >>> type(list1)
    <class 'list'>


   
   ```
      Tuple : A **Immutable** ordered collection of data with elements seperated by comma and enclosed in **paranthesis ()** . [Tuples](Tuple)
    ``` python
    >>> tuple1 = ("Cat",("lion","tiger"),("pigeon","parrot"))
    >>> print(tuple1)
    ('Cat', ('lion', 'tiger'), ('pigeon', 'parrot'))
    >>> type(tuple1)
    <class 'tuple'>

   ```
6. Mapped data     
       Dict : An unordered collection of data containing key:value pair  enclosed in **flower {}** brackets. [Dict](Dict)
    ``` python
    >>> dict1 = {"name" : "Hania","Age" : 34 , "Location" : ("India","hyderabad")}
    >>> dict1
    {'name': 'Hania', 'Age': 34, 'Location': ('India', 'hyderabad')}
    >>> type(dict1)
    <class 'dict'>
   ```
