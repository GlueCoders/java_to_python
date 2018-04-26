---
title: Introduction to Classes
date: 2018-04-21
categories: class python
published: true
---

Python has similar concept of classes as Java does, although there are many differences between both language implemenations. Let's first see how classes are written in Python:  

```
# Class Definition
class Car:

    # Constructor, self is like `this` of Java which is
    #the first parameter for every instance method
    def __init__(self):
        # self. is how parameters are defined, there is no separate declaration as in Java
        self.make = 'default'
        self.status = 'Neutral'

    # Instance Method
    def stop(self):
        self.status = 'Braking'
        print('Applying Brakes')

    # toString() override
    def __str__(self):
        return 'Make: ' + self.make + ' Status: ' + self.status

#This is equivalent to new Car() in Java
car = Car()

#This will invoke __str__ method on car
print(car)  # prints Make: default Status: Neutral
car.stop()  # prints Applying Brakes
print(car)  # prints Make: default Status: Braking
```  

#### Instance Methods  

Every instance method i.e. non static or class methods(more on this later) have `self` as first parameter; `self` acts as `this` parameter. When invoking instance method we don't have to provide `self` parameter, it is passed implicitly.  
```
# self is passed implicitly
def stop(self):
        self.status = 'Braking'
        print('Applying Brakes')

car = Car()
car.stop()  # prints Applying Brakes
```  
  
#### Constructor  

Constructor is defined by `__init__` function. In Python classes there can be only one constructor. The first parameter is always `self` as told above for instance methods, apart from that constructor can take parameters which can be stored at instance level.  

```
class Car:

    def __init__(self, make, model):
        self.make = make
        self.model = model

car = Car('Audi', 'A3')
```  

`self.make` and `self.model` are the instance properties. All the instance properties should be initialized in constructor to avoid errors at runtime.  

