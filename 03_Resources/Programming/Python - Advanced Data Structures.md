---
type: Generic
status: in-progress
started: 2026-05-10
finished:
tags:
  - generic
  - python
  - language
MOCs:
  - "[[Python MOC]]"
---
# Overview 

Learning about various DS like **defaultdict, Counter, Heapq, Deque, namedtuple**

# Data Structures

## 1. defaultdict - subclass of dict

### why we need this??
In python dictionaries if we try to access/modify keys that are not present we get *KeyError Exceptions*. We can avoid this by using the .setdefault('missing key','default key') or .get('missing key','default key')) methods but it is verbose so defaultdict provides a more pythonic way to handle it.

### Understanding the working of defaultdict
- it overrides the `.__missing__()` 
- it adds a .default_factory ,a writable variable that gets intialised when instantiated
the *default_factory* will take the first variable passed to `defaultdict.__init__()`. The argument passed if is callable then it will be executed when we are trying to modify/access any missing key.

```python

from collections import defaultdict

# default_factory is set to list
d = defaultdict(list)

print(d.default_factory)
# <class 'list'>

# Accessing a missing key automatically calls list()
d["fruits"].append("apple")
d["fruits"].append("banana")

print(d)
# defaultdict(<class 'list'>, {'fruits': ['apple', 'banana']})
```


We can also pass custom callable/function in defaultdict

```python
from collections import defaultdict

def default_value():
    return "Not Found"

d = defaultdict(default_value)

print(d["missing"])
# Not Found
```


#### Common prog. problems that can be solved using defaultdict
1. Grouping the items in a collection
2. Counting the items in a collection
3. Accumulating the values in a collection


## 2. Counter - pythonic way to count objects

It is also a subclass of python's dict. It helps in counting hashable objects efficiently.

#### what do you mean by hashable objects?
- have a fixed value
- returns a hashvalue after using hash()
- Immutable
- Can be used as a dict key or set element
- examples : int, str, tuple (non examples :  list, dict, set)

```python
from collections import Counter

a=Counter("hello")

print(a)
#Counter({'l': 2, 'h': 1, 'e': 1, 'o': 1})

a.update("World")

print(a)
#Counter({'l': 3, 'o': 2, 'h': 1, 'e': 1, 'W': 1, 'r': 1, 'd': 1})
```

### .most_common()
This methods helps in listing group of objects based on their frequency.
if no argument is passed it returns all elements in descending order of frequency. If argument passed 'n' then it shows the top 'n' elements with most frequency. ==It return in tuples==

```python
from collections import Counter

a=Counter(["ram", "radha", "shyam", "ram", "ram", "rahul","rahul"])

print(a)
#Counter({'ram': 3, 'rahul': 2, 'radha': 1, 'shyam': 1})

print(a.most_common())
#[('ram', 3), ('rahul', 2), ('radha', 1), ('shyam', 1)]

print(a.most_common(2))
#[('ram', 3), ('rahul', 2)]

```

If there is a tie in frequency then it returns in order of how they appeared.

### .elements()
It restores original elements according to count i.e repeats the element as many times it appears

```python
from collections import Counter

c = Counter({
    "a": 3,
    "b": 2,
    "c": 1
})
list(c.elements())
#['a', 'a', 'a', 'b', 'b', 'c']


Counter("mississippi").elements()
# m i i i i s s s s p p
```

### python doesn't have Multiset. We can use Counter as multiset.
```python
from collections import Counter

ms = Counter()

# insert elements
ms[1] += 1
ms[1] += 1
ms[2] += 1

print(ms)
#Counter({1: 2, 2: 1})
```
## 3. heapq - priority Queue

It is just the python version of C++ Priority Queue.It returns the smallest element when poped. By default python doesn't provide Max Heap( i.e returning the largest element when popped). but we can manufacture a max heap by inserting values with a negative sign.

```python
import heapq

arr = [4, 1, 7, 3, 8]

heapq.heapify(arr) # O(n)
print(arr)
#[1, 3, 7, 4, 8] -> doesn't sort it just puts it in heap with smallest element at root/top

heapq.heappush(arr, 2)
print(arr)
#[1, 3, 2, 4, 8, 7]

x = heapq.heappop(arr)
print(x)
#1

print(arr[0]) # also returns the smallest element at the top/root
```

```python
import heapq

pq = []

heapq.heappush(pq, 5)
heapq.heappush(pq, 1)
heapq.heappush(pq, 3)

while pq:
    print(heapq.heappop(pq))
    
1
3
5
```
## 4. deque

Double-Ended-Deque same as C++ Deque
```python
from collections import deque

dq=deque()

dq.append(1)
dq.append(2)
dq.append(3) #--> appends RIGHT
dq.appendleft(10) #--> appends LEFT

dq.pop() #--> pops form RIGHT
dq.popleft() #--> pops form LEFT

print(dq)
```
## 5. namedtuple

it is a subclass of tuple. It enables you to access elements using names as well as indexes i.e (`person[0] , person.name`)

```python
from collections import namedtuple

Person = namedtuple("Person", ["name", "age", "city"])
# "Person" → class name
# ["name", "age", "city"] → field names

p1 = Person("Jay", 22, "Hyderabad")  
  
print(p1)
# Person(name='Jay', age=22, city='Hyderabad')
```

### Why use namedtuple instead of tuples??
- tuples don't support names so it may create confusion while accessing using indexes.
- namedtuple is immutable simillar to tuple 
- Uses less memory than classes
### Useful Methods
#### `_fields

Returns field names.
```python
print(Student._fields) # ('name', 'age', 'branch')
```
#### `_make(iterable)`

Creates object from iterable.
```python
data = ["Jay", 22, "CSE"]

s = Student._make(data)

print(s)
#Student(name='Jay', age=22, branch='CSE')
```

#### `_replace()`
Creates modified copy.
```python
s2 = s._replace(age=23)

print(s2)
#Student(name='Jay', age=23, branch='CSE')
```