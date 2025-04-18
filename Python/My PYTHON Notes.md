### Functions
```ruby
x = 5
print(type(x))  # <class 'int'>
```

## Sequences & Collections
### Tuples (immutable)
```ruby
t = (1, 2, "three", 'four')
# t[0] = 5  # Error: tuples are immutable
```

### Lists (mutable)
```ruby
lst = [1, 2, 3]
lst.append(4)         # [1, 2, 3, 4]
lst[0] = 0            # [0, 2, 3, 4]
```

### Dictionaries (unordered key-value pairs)
```ruby
d = {"name": "Alice", "email": "a@example.com"}
d["age"] = 30
print(d["name"])  # Alice
```

## Indexing, Slicing, and Iteration
```ruby
x = [10, 20, 30, 40, 50]
print(x[0])        # 10
print(x[-1])       # 50
print(x[1:4])      # [20, 30, 40]
print(x[:3])       # [10, 20, 30]
print(x[3:])       # [40, 50]
```

### String Slicing
```ruby
s = "Python"
print(s[0])      # 'P'
print(s[-1])     # 'n'
print(s[1:4])    # 'yth'
```

## List and Tuple Operations
```ruby
a = [1, 2]
b = [3, 4]
print(a + b)         # [1, 2, 3, 4]
print(a * 2)         # [1, 2, 1, 2]
print(2 in a)        # True
```

## Looping over Sequences
```ruby
for item in [1, 2, 3]:
    print(item)
```

## String Methods
```ruby
s = "first last"
parts = s.split(" ")
print(parts)       # ['first', 'last']
print(parts[0])    # 'first'
print(parts[-1])   # 'last'
```

### Dictionaries
```ruby
person = {"name": "Bob", "email": "bob@email.com"}
person["age"] = 42
for key in person:
    print(key, person[key])
for value in person.values():
    print(value)
for k, v in person.items():
    print(k, v)
```

## Unpacking
```ruby
t = ("Anna", "Smith", "anna@email.com")
first, last, email = t
print(first)  # Anna
```

## String Formatting
```ruby
name, price, qty = "Alice", 2.5, 3
print("Name: {}, Price: {:.2f}, Qty: {}".format(name, price, qty))
# f-string (Python 3.6+)
print(f"Name: {name}, Price: {price:.2f}, Qty: {qty}")
```

## Dates and Times
```ruby
import time
from datetime import datetime, timedelta
now = time.time()  # seconds since epoch
dt = datetime.fromtimestamp(now)
print(dt.year, dt.month, dt.day)
```

##  Timedelta
```ruby
delta = timedelta(days=100)
future = dt + delta
```

##  Functions
```ruby
def function_name(a, b, c):
    return a + b + c
print(function_name(1, 2, 3))  # 6
```

## Default Arguments
```ruby
def greet(name="World"):
    print(f"Hello, {name}!")
greet()
greet("Alice")
```

## Arbitrary Arguments
```ruby
def total(*args):
    return sum(args)
def show_info(**kwargs):
    for k, v in kwargs.items():
        print(k, v)
```

## Lambda Functions
```ruby
square = lambda x: x * x
print(square(4))  # 16
add = lambda a, b: a + b
print(add(2, 3))  # 5
```

## List Comprehensions
```ruby
evens = [x for x in range(10) if x % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8]
```

## Classes
```ruby
class Person:
    school = "School of Info"  # Class variable

    def set_name(self, name):
        self.name = name
    def set_location(self, location):
        self.location = location
p = Person()
p.set_name("Alice")
print(p.name)  # Alice
```

## Map and Functional Programming
```ruby
a = [1, 4, 5]
b = [2, 3, 5]
result = map(min, a, b)
print(list(result))  # [1, 3, 5]
```
