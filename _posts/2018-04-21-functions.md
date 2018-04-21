---
title: Functions
date: 2018-04-21
categories: basics python
published: true
---

In Python functions start with `def` keyword followed by function name and the paranthesized list of parameters. The statements that form the body of the function start at the next line and must be intended.  

```
def add(x, y):
    return x + y

print(add(3, 4))
```  

Here a function `add` is declared and it returns the result by adding two numbers. Function can also just be a bunch of statements without having a return statement, in this it will by default return a `None` value.  

```
def make_sandwich(bread, veggies, meat, sauces):
    print('Preparing you a sandwich with bread of your choice: ' + bread)
    print('Adding ' + str(veggies))
    print('Loaded with ' + meat)
    print('Delicious sauces: ' + str(sauces))

make_sandwich('multigrain', ['tomato', 'cucumber'], 'chicken', ['mayo', 'sweet onion'])
```  

Optionally we can also specify types for the arguments and return value as shown below:  

```
def add(x: int, y: int) -> int:
    return x + y
```  

#### Default Argument Values  

Functions can have default values for its arguments, so that if those parameters are not being passed by the caller the default values will be used.  
As shown below the `make_sandwich` function has a value defined for all the parameters. If the caller does not provide any one of the values then the default value is used.  

```
def make_sandwich(bread='multigrain', veggies=None, meat='chicken', sauces=None):
    print('Preparing you a sandwich with bread of your choice: ' + bread)
    print('Adding ' + str(veggies))
    print('Loaded with ' + meat)
    print('Delicious sauces: ' + str(sauces))


make_sandwich('multigrain', ['tomato', 'cucumber'], 'chicken', ['mayo', 'sweet onion'])
make_sandwich()
make_sandwich('wheat', ['olives', 'jalapeno'])
make_sandwich('wheat', ['olives', 'jalapeno'], 'bacon')
```  

**Important** The default value is evaluated only once. So if the default value is a mutable object such as list, dictionary or some instance of class the result will be quite different than expected.  

```
def add_to_list(arg, list=[]):
    list.append(arg)
    return list

print(add_to_list(1))
print(add_to_list(2))
print(add_to_list(3))
```  
This prints following :  
```
[1]
[1, 2]
[1, 2, 3]
```

Not quite what is expected at first glance. To avoid this the mutable values should always be initialized to `None` as default value, this is shown in `make_sandwich` function.  

####  Keyword Arguments  

While calling function argument names can also be specified as shown below:  
```
def make_sandwich(bread, veggies, meat, sauces):
    print('Preparing you a sandwich with bread of your choice: ' + bread)
    print('Adding ' + str(veggies))
    print('Loaded with ' + meat)
    print('Delicious sauces: ' + str(sauces))


make_sandwich(bread='multigrain', veggies=['tomato', 'cucumber'], meat='chicken', sauces=['mayo', 'sweet onion'])
make_sandwich(veggies=['tomato', 'cucumber'], bread='multigrain', sauces=['mayo', 'sweet onion'], meat='chicken')
make_sandwich('multigrain', ['tomato', 'cucumber'], sauces=['mayo', 'sweet onion'], meat='chicken')

```  

The order of arguments doesn't matter if all are being passed as keyword arguments. If positional arguments(arguments without any keyword, like value as in `multigrain` in last invocation) are present, then keyword arguments should follow them.  

#### Varargs  

In Python we have two vararg types, one is of tuple type and other is dict. Tuple is just like a List only it can have unrelated things in one collection, and Dict is basically a Map.  

```
#Tuple/List type vararg
def friends(student_name, *friends):
    print(student_name + ' has following friends: ')
    for friend in friends:
        print(friend)

#John, Alex and Jean goes in friends parameter
friends('Paul', 'John', 'Alex', 'Jean')

#prints following
#Paul has following friends: 
#John
#Alex
#Jean
```
#Dict type vararg
def report_card(student_name, **subjects_marks):
    print('Student ' + student_name + ' has following marks')
    for subject in subjects_marks:
        print(subject + ': ' + str(subjects_marks[subject]))

# marks for maths, english and science goes in subjects_marks
report_card('Paul', maths=90, english=70, science=100)

#Prints following
#Student Paul has following marks
#maths: 90
#english: 70
#science: 100

```  


#### Unpacking varargs into arguments 

The reverse situation can also appear when a function needs two arguments and we have those arguments as part of a list or a dictionary. Follow through some examples below:  

```
def add(x: int, y: int) -> int:
    return x + y


numbers = [1, 2]
#Add expects two arguments and the numbers list is unpacked using * operator
print(add(*numbers))

print(add(3, 4))
```

For dictionary types ** operator is used to unpack.  
```
def make_sandwich(bread, veggies, meat, sauces):
    print('Preparing you a sandwich with bread of your choice: ' + bread)
    print('Adding ' + str(veggies))
    print('Loaded with ' + meat)
    print('Delicious sauces: ' + str(sauces))


order = {'bread': 'multigrain', 'veggies': ['tomato', 'cucumber'], 'meat': 'chicken', 'sauces': ['mayo', 'sweet onion']}
#Unpacking order dict to match make_sandwich parameters
make_sandwich(**order)
```  













