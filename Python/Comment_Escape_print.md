# COMMENTS

* ### Single Line Comments  
To add a single line comment add '#' before line.
  
```python 
# This is comment line and below line will execute
print ("I will run")

``` 
To add a mutilple lines comment add ``` before  and end of the line.
  


```python 
''' This is comment line and below line will execute
this line is also comment.
This is also commented
'''
print ("I will run")
```

* ### ESCAPE SEQUENCE Characters

  To insert a chars that cannot be used in string. To do this (\\) escape character is used.

```python
print("the words in quotes will be printed with quotes \" Apple \" ")
```

* ### Print

  Syntax : print(objects,sep=separator, end=end, file=file, flush=flush)

1. object : Any object or objects will be converted to string before printed.
2. sep : Specify any special seperator. default is space( ).  optional
3. end: To specify what to print at end of the line.
4. file : An object with a write method.  optional

```python
>>> print("Python ", 7 , 1.1, sep = ' $ ' )
Python  $ 7 $ 1.1
>>> print("Python", 7 , 1.1)
Python 7 1.1
>>> print("Python ", 7 , 1.1, sep = ' $ ' )
Python  $ 7 $ 1.1
>>> print("Python ", 7 , 1.1, sep = ' $ ' , end = ' *******\n')
Python  $ 7 $ 1.1 *******
>>>
```
