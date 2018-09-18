---
published: false
---
---
title: Inheritance
date: 2018-09-18
categories: class python
published: true
---

When it comes to inheritance Python is bit different from Java. Firstly there is no `interface` keyword in Python, to define contracts a module named [Abstract Base Classes](https://docs.python.org/3/library/abc.html#module-abc "Abstract Base Classes") is used. Secondly Python supports multiple inheritance. For now lets look at how inheritance basics.  Below is a class `Parent` which has each of instance, class and static methods. We will extend this class and see how inheritance works.  

```
class Parent:

    def __init__(self):
        self.attr_1 = 1
        print('Parent init method')

    def normal_method(self):
        print('Parent normal method')

    @classmethod
    def class_method(cls):
        print('Parent class method')

    @staticmethod
    def static_method():
        print('Parent static method')
```  


### Simple extending class, no overriding methods  

Here we just extend the class and do not override any of the methods. As you will see that when we invoke the methods on child instance the parent methods are called even for `__init__ (constructor)` method.   

```
#To extend write the base class name in parantheses as shown below
class ChildNotOverriding(Parent):
    pass
    
# Parents methods being invoked through child instance
child_not_overiding = ChildNotOverriding()
>> Parent init method 

child_not_overiding.static_method()
>> Parent static method

child_not_overiding.class_method()
>> Parent class method

child_not_overiding.normal_method()
>> Parent self method

```  

This shows that even the static and class methods are inherited by the child classes{TBC}.  


