---
title: Private Variables
date: 2018-04-28
categories: class python
published: true
---

In Python there is no concept of access modifiers. There is no keywords like protected, private and public. So how do we encapsulate data, how do we stop anyone from modifying data that we have in our classes.  

#### Underscore convention  

In Python prefixing `_` to a variable in a class, means that this variable is supposed to be private. It is just a convention and really does not stops anyone from modifying it.  

```
class Student:

    def __init__(self, name):
        # _ convention used, though still this is accessible
        self._name = name

    def print(self):
        print(self._name)


paul = Student('paul')
paul.print()  # prints paul

# _ is just a convention, allows modification like any other attribute
paul._name = 'logan'
paul.print()  # prints logan
```  

There is no real way of stopping someone from accessing and modifying instance variables but there is a way to advise more strongly to stay away from private variables (underscored variables). 

#### Getters and Setters


In Python @property decorator works like a getter in Java. Lets see it in action:  

```
class Student:

    def __init__(self, name):
        self._name = name

    def print(self):
        print(self._name)
    
    # Declares that name is a property, internally class is using self._name
    @property
    def name(self):
        return self._name

    # Setter for name
    @name.setter
    def name(self, value):
        self._name = value


paul = Student('paul')
paul.print()  # prints paul
# This actually calls name(self,value) method
paul.name = 'logan'
paul.print() # prints logan
paul._name = 'paul' # This will still work
```   

In above program, `@property` advises that name should be used to access the value from Student class. If `student.name` is used to get the value it actually calls that `name(self)` method since it is decorated by `@property` annotation. Similarly whenever value is set using `student.name` then `name(self, value)` is invoked because it is decoarated with `name.setter`.  
To avoid setting property, one can remove the setter and then following will happen:  

```
>> paul = Student('paul')
>> paul.name = 'logan'
   AttributeError: can't set attribute
```  

Though paul._name will still be available for modification. I encourage to go through this link (stackoverflow-python_private_variables)[https://stackoverflow.com/questions/1641219/does-python-have-private-variables-in-classes] for inquisitive folks out there.



