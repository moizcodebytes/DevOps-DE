## Type Casting

The conversion of one data type to another type is called as casting.

#### Explicit Type Casting

The conversion which is done by developer as per requirement using Python's built in functions like int(),float(),hex(),oct(),str().

```python
>>> x = 12
>>> type(x)
<class 'int'>
>>> y = str(12)  ## Casting to str from int
>>> type(y)
<class 'str'>
>>>

```


#### Implicit Type Casting

Python automatically converts the type to higher order data type.

``` python
>>> x = 5
>>> type(x)
<class 'int'>
>>> y = 9.9
>>> type(y)
<class 'float'>
>>> z = x + y
>>> z
14.9
>>> type(z)
<class 'float'>
>>>

```

## User Input 

To take the input from user during execution of program we can input() function . By default it takes the value as string.

syntax : var1 = input()

we can add a print statement inside the input.

syntax : var1 = input("please enter the name")


```python
>>> x = input()
5
>>> type(x)
<class 'str'>
>>> x
'5'
>>>
>>> name = input("please enter your name ")
please enter your name  Jack
>>> name
' Jack'
>>> type(name)
<class 'str'>
>>>
```

To get the value as int/float we type cast it.

``` python
>>> name = input("please enter your number :")
please enter your number :maa
>>> x = input("please enter your number :")
please enter your number :10
>>> type(10)
<class 'int'>
>>> x = int(input("please enter your number :"))
please enter your number :10
>>> type(x)
<class 'int'>
>>>

```

Exercise at [Calculator](./Programs/Exercise_1.py)
