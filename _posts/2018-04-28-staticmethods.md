In Python, classes can have static methods. However there is no real concept for static variables, it can be achieved but that is more advanced than the current scope.  

```
class DateFormatter:
    
    # This is to tell that method is a static one
    @staticmethod
    def format(date_str, format_pattern):
        print('Applying format pattern ' + format_pattern + ' to date arg' + date_str)

    @staticmethod
    def default_format(date_str):
        print('Applying default format pattern to date arg ' + date_str)


# Static methods are called on Class 
DateFormatter.format("280042018", "ddMMyyyy")
DateFormatter.default_format("28-04-2018")

d1 = DateFormatter()
# Static methods can be called from instance too
d1.default_format("28-04-2018")

```  

`@staticmethod` is the way to tell that a method is static. Static methods can be called as `Class.method()` or on the instance as well. Note there is no `self` paramter in the static methods definition.
