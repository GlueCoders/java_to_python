---
title: Variables
date: 2018-04-15
categories: basics python
published: true
---

Coming from Java background we have accustomed to writing variable as follows :

```
int x = 0;
String name = "name"
int[] numbers = new int[5]
```  

But in Python type is not mentioned while declaring variable, it is inferred implicitly. Also *there is no final keyword* in Python. Below are the examples of basic python types:  
```
number = 10
floating_number = 10.10
string = "hi there"
flag = True
list_numbers = [1, 2, 3, 4, 5, 6]

print(number)  # 10
print(floating_number)  # 10.10
print(string)  # hi there
print(flag)  # True
print(list_numbers)  # [1, 2, 3, 4, 5, 6]
```  

As you can see its just name and then assignment operator with value, no type definition at all.  To determine type one can use `type()` method and to check whether a variable belongs to a particular type `isinstance()` can be used as shown below.  
```
print(type(number))  # <class 'int'>
print(type(floating_number))  # <class 'float'>
print(type(string))  # <class 'str'>
print(type(flag))  # <class 'bool'>
print(type(list_numbers))  # <class 'list'>

print(isinstance(flag, bool))  # True
print(isinstance(list_numbers, list))  # True
print(isinstance(number, int))  # True
print(isinstance(floating_number, float))  # True
print(isinstance(string, str))  # True
```

Here bool, int, list, str and float are Python types (equivalent to Java classes).
