---
title: Class Methods
date: 2018-04-29
categories: class python
published: true
---  

Name, `class methods` is confusing, but keep in mind that they are not static or instance methods. Basically Python has three type of methods:  

1. Instance methods - methods which receives `self` implcitly as first parameter
2. Static methods  - methods decorated with @staticmethod
3. Class methods  - methods decorated with @classmethod and receives `class` implicitly as first parameter  


First lets see how class methods are written and invoked.  

```
class Number:

    def __init__(self, value):
        self._value = value
    
    # this is decorator for denoting classmethod,
    # cls is the Class type
    @classmethod
    def negative_number_init(cls, value):
        # this invokes __init__ method
        return cls(-value)

    @classmethod
    def string_format_init(cls, value):
        return cls(int(value))

    def __str__(self):
        return str(self._value)


num1 = Number(2)
print(num1)

# class method being invoked here
num2 = Number.negative_number_init(2)
print(num2)

num3 = Number.string_format_init('2')
print(num3)  
```  

At first glance classmethod will look like a static method, but actually those two are very different. Classmethod receives `class` as a parameter implicitly whereas staticmethod doesn't. Classmethods are generally used as substitute for overloaded constructors or you can call them as factory methods.  
Classmethods also play nicely when it comes to inheritance, more on this later. For more information you can refer these links:
1. [Classmethods vs Staticmethods](https://stackoverflow.com/questions/12179271/meaning-of-classmethod-and-staticmethod-for-beginner)
2. [Usecases for classmethods](https://stackoverflow.com/questions/5738470/whats-an-example-use-case-for-a-python-classmethod)














