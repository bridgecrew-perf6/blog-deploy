---
title: CS61A_Learning
tags: Python
index_img: 
banner_img: https://s2.loli.net/2022/05/05/JRfjsecDUwEmgoS.png
---

# WEEK 1

The first  half week is mainly about how to use bash and how to use the OK system in website.

In the next half week, mostly it's about python basic knowledge.

### How to use git bash

* `ls`: list all files
* `cd <path>`: change the specified directory
* `mkdir <dir name>`: to create a directory
* `mv <source file><destination path>`: move a file
* `unzip <source file>` : to unzip a file
* `winpyt python`: to open the python edit space
### How to use the OK system
* `python ok -q <qustion>`: to test a specific question
* `python ok`: to test all the question
* `python ok -v`: to see how you did on all tests
* `python ok --local`: to test it locally

### Python arithmetic expressions

* Floating point division (`/`): divides the first number number by the second, evaluating to a number with a decimal point *even if the numbers divide evenly*.
* Floor division (`//`): divides the first number by the second and then rounds down, evaluating to an integer.
* Modulo (`%`): evaluates to the positive remainder left over from division.

```python
>>> 7 / 4
1.75
>>> (2 + 6) / 4
2.0
>>> 7 // 4        # Floor division (rounding down)
1
>>> 7 % 4         # Modulus (remainder of 7 // 4)
3
```



***

### The difference between Python and C++

when I learn C++, the `if` are like:

```c++
if(expression){
    <suite>;
    <suite>;
}else{
    <suite>;
}
```

But in Python it's more like:

```python
if <expression>:
    <suite>
elif <expression>:
    <suite>
else:
    <suite>
```

> Pay attention to the  `elif` .It's different to the C++.And the expression part don't need to have a `( )` But need have a`:`



The next it's the `while` difference:

C++:

```c++
while(expression){
    <suite>;
    <suite>;
}
```

In Python it's more like :

```python
while <expression>:
    <suite>
    <suite>
```

### About the function

It's pretty familiar with C++ about the function. In Python it's like this one:

```python
def <name>(<formal parameters>):
    
    return <return expression>
```

Here is a good example:

```python
from operator import add, mul

def square(x):
	    return mul(x, x)	
def sum_squares(x, y):
		return add(square(x), square(y))
	
result = sum_squares(5, 12)
```

------

In C++, we execute every codes by main function. It's easy to define any variables. But in Python , things become  a little bit unfamiliar.

```python
x=12
z=7
def f(y):
    x=3
    print(x,y,z)
f(7)
print(x)
```

The code above is equal to C++ code below:

```c++
#include<iostream>
using namespace std;
int x=12,z=7;
int f(int y){
	int x=3;
	cout<<x<<" "<<y<<" "<<z<<endl;
}
int main(){
	f(7);
	cout<<x;
	return 0;
}
```

In Python we introduce a new concept: **frame**. There are two kind of frame: local frame and global frame. Every variables shows in a function called : this variables is in a local frame. And every variables shows right in Python we call it was in global frame.

The most important things is : **when we try to find variables values we should follow the frame its in OR its up frame.**    :red_circle:





# week 2

####  **Print and None**

In the week Q&A video , some student ask one question about this topic.

```python
>>> print(print (1),print(2))
1
2
None None
```

None Indicates that **Nothing is Returned**: The special value None represents nothing in Python . A function that does not explicitly return a value will return None.

 ```python
 >>> def does_not_return_square(x):
     	x * x
         
 >>> does_not_return_square(4)    
 ```

when we run the code above, nothing displayed. Because **None is not displayed by the interpreter as the value of an expression.**

```python
>>> sixteen = does_not_return_square(4)
>>> sixteen + 4
```

If we run the code like above. The python will say:

> File "<stdin>", line 1, in <module>
> TypeError :  unsupported operand type(s) for +: 'NoneType' and 'int'

The reason why the Python can't add 4 to the sixteen because the None it's not means 0,but it means another Type.

#### Pure Functions & Non-Pure Functions

This part is easy, so I just copy the picture in class:

|                   Type                    |                             Img                              |
| :---------------------------------------: | :----------------------------------------------------------: |
|  **Pure Functions**: just return values   | ![image-20220506161307060](https://s2.loli.net/2022/05/07/2IZEUhOszglTqcP.png) |
| **Non-Pure Functions**: have side effects | ![image-20220506161320811](https://s2.loli.net/2022/05/07/3RnEKyYTFjiDSH1.png) |

So the very first question can be see like this:

![image-20220506161612929](https://s2.loli.net/2022/05/07/RsSkIx8toDC3Tbq.png)





#### Miscellaneous Python Features

##### Division:

When it comes to division, Python provides two infix operators: `/` and `//`. The former is normal division, so that it results in a *floating point*, or decimal value, even if the divisor evenly divides the dividend:

```python
>>> 5 / 4
1.25
>>> 8 / 4
2.0
```

The `//` operator, on the other hand, rounds the result down to an integer:

```python
>>> 5 // 4
1
>>> -5 // 4
-2
```

These two operators are shorthand for the `truediv` and `floordiv` functions.

```python
>>> from operator import truediv, floordiv
>>> truediv(5, 4)
1.25
>>> floordiv(5, 4)
1
```

##### Multiple Return Values:

It works like this:

```python
def operate(a, b):
    suma = a + b
    diff = a - b
    mul = a * b
    div = a / b
    return sum, diff, mul, div
```

And when we use it ,we do things like this:

```python
suma, diff, mul, div = operate(n1, n2)
```

##### Doctests:

When we wrote a function ,we should leave a text about this function to let us know how this function worked.

```python
#The file name is 01.py

def absolute_value(x):
    """Return the absolute value of X.

    >>> absolute_value(-3)
    3
    >>> absolute_value(0)
    0
    >>> absolute_value(3)
    3
    """
    if x < 0:
        return -x
    elif x == 0:
        return 0
    else:
        return x
```

when we run the command like this:

```shell
winpty python -m doctest 01.py
```

There is nothing come out, that's good. It means we passed all test. If we want to see more details, we use commands like this:

```shell
winpty python -m doctest -v 01.py
```

![image-20220603222442691](https://s2.loli.net/2022/06/03/jpKNyQAb7YBcEVq.png)

##### Default Arguments:

When we called a function ,the value we give might not be exactly the function needs.We can the function a default values. This is not an assignment statement. This is a place holder for a value.  Like this pieces below:

```python
def divide_exact(n, d=10):
    """Return the quotient and remainder of dividing N by D.

    >>> quotient, remainder = divide_exact(618, 10)
    >>> quotient
    61
    >>> remainder
    8
    """
    return floordiv(n, d), mod(n, d)
```

It says if there's no argument passed in to be bound to d then I'll bind ten to d.
