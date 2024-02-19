Python `collections` 模块提供了一些额外的数据结构，这些数据结构不同于内置的数据类型（如列表、元组、字典等），并且对于特定的问题或需求提供了更高效的实现
1. **Counter（计数器）：**
    
    - 用于计算可迭代对象中元素的出现次数。返回一个字典，其中键是元素，值是该元素在可迭代对象中出现的次数。
    
    
    ``` python 
    from collections import Counter  
    my_list = [1, 2, 3, 1, 2, 3, 4, 5, 1] 
    counter = Counter(my_list) 
    print(counter)  # 输出: Counter({1: 3, 2: 2, 3: 2, 4: 1, 5: 1})
    ```
    
2. **DefaultDict（默认字典）：**
    
    - 是字典的子类，允许指定默认值。当访问不存在的键时，返回默认值而不是引发 `KeyError`。默认值可以是任何可调用对象（如函数）。

    
    ``` python 
    from collections import defaultdict 
    my_dict = defaultdict(int) 
    my_dict['a'] += 1
	my_dict['b'] += 2 
    print(my_dict['c'])  # 输出: 0
```

    
3. **NamedTuple（命名元组）：**
    
    - 是一个工厂函数，用于创建具有字段名称的元组类。提供了具名字段，使得元组更易读、维护和使用。
    
    ``` python
    from collections import namedtuple  
    Point = namedtuple('Point', ['x', 'y']) 
    p = Point(1, 2) 
    print(p.x, p.y)```
    
4. **Deque（双端队列）：**
    
    - 是一个双端队列，支持在两端高效地进行插入和删除操作。相比于列表，在队列的两端插入和删除元素的时间复杂度都是 O(1)。
    
    
    ``` python 
from collections import deque  
my_deque = deque([1, 2, 3]) 
my_deque.append(4) 
my_deque.appendleft(0) 
print(my_deque)
```
    
5. **OrderedDict（有序字典）：**
    
    - 是字典的子类，维护了插入元素的顺序。从Python 3.7开始，字典本身也保持插入顺序，因此 `OrderedDict` 的用途相对减少。
6. **ChainMap：**
    
    - 用于将多个字典或映射链接在一起，形成一个逻辑上的映射。对于查找操作，会按照链的顺序查找，直到找到为止。
7. **UserDict：**
    
    - 是一个字典的包装类，允许用户定义自己的字典类。通过继承 `UserDict`，用户可以方便地定义自定义字典行为。
8. **Heapq（堆队列）：**
    
    - 提供了堆队列算法的实现，用于在可变序列上实现堆的常见操作，如插入、弹出最小值等。