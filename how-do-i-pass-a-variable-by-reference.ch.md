# 如何通过引用传递变量？

```python 
class PassByReference:
    def __init__(self):
        self.variable = 'Original'
        self.change(self.variable)
        print(self.variable)

    def change(self, var):
        var = 'Changed'
pBR = PassByReference() # 'Original'
```

其实想问的是它这个类里面，在 `__init__` 方法初始化的时候，调用了 `change()` 方法，如何将改变 `__init__`里面的 `self.variable` 这里变量的值，但是显然这种方式是行不通的，如果要通过引用，我们可以使用下面这种改造方式


```python 
class PassByReference:
    def __init__(self):
        self.variable = {name: 'Original'}
        self.change(self.variable)
        print(self.variable)

    def change(self, var):
        var.name = 'Changed'
pBR = PassByReference() # {name: 'Changed'}
```

但是我们需要更加深入的了解到底是怎么回事

参数通过赋值传递。其背后的理由是双重的：

传入的参数实际上是对对象的引用（但引用是通过值传递的）
有些数据类型是可变的，但有些则不是
所以：

如果将可变对象传递给方法，则该方法将获得对该对象的引用，并且可以对其进行突变，但是如果您将该引用重新绑定到该方法中，则外部作用域对此一无所知完成后，外部参考仍将指向原始对象。

如果将不可变对象传递给方法，则仍然无法重新绑定外部引用，甚至无法使对象发生突变

# 列表-可变类型

我们尝试改变列表里面数据

```python
def try_to_change_list_contents(the_list):
    print('got', the_list)
    the_list.append('four')
    print('changed to', the_list)

outer_list = ['one', 'two', 'three']

print('before, outer_list =', outer_list)
try_to_change_list_contents(outer_list)
print('after, outer_list =', outer_list)
```

输出

```python
before, outer_list = ['one', 'two', 'three']
got ['one', 'two', 'three']
changed to ['one', 'two', 'three', 'four']
after, outer_list = ['one', 'two', 'three', 'four']
```

由于传入的参数是对的引用outer_list，而不是其副本，因此我们可以使用变异列表方法对其进行更改，并使更改反映在外部作用域中。

# 现在让我们看看当尝试更改作为参数传入的引用时会发生什么：

```python
def try_to_change_list_reference(the_list):
    print('got', the_list)
    the_list = ['and', 'we', 'can', 'not', 'lie']
    print('set to', the_list)

outer_list = ['we', 'like', 'proper', 'English']

print('before, outer_list =', outer_list)
try_to_change_list_reference(outer_list)
print('after, outer_list =', outer_list)
```
输出
```python
before, outer_list = ['we', 'like', 'proper', 'English']
got ['we', 'like', 'proper', 'English']
set to ['and', 'we', 'can', 'not', 'lie']
after, outer_list = ['we', 'like', 'proper', 'English']
```

由于the_list参数是通过值传递的，因此为其分配新列表不会影响方法外部的代码。该the_list是副本outer_list的参考，我们不得不the_list指向一个新的列表，但没有办法改变outer_list的值


# 字符串-不可变的类型
它是不可变的，因此我们无能为力，无法更改字符串的内容
现在，让我们尝试更改参考
```python
def try_to_change_string_reference(the_string):
    print('got', the_string)
    the_string = 'In a kingdom by the sea'
    print('set to', the_string)

outer_string = 'It was many and many a year ago'

print('before, outer_string =', outer_string)
try_to_change_string_reference(outer_string)
print('after, outer_string =', outer_string)
```

输出

```python
before, outer_string = It was many and many a year ago
got It was many and many a year ago
set to In a kingdom by the sea
after, outer_string = It was many and many a year ago
```

同样，由于the_string参数是通过值传递的，因此为其分配新的字符串不会影响方法外部的代码。该the_string是副本outer_string的参考，我们不得不the_string指向一个新的字符串，但没有办法改变，outer_string

# 我们如何解决这个问题？

可以返回新值。这不会改变事物传递的方式，但是可以让您获得想要的信息：

```python
def return_a_whole_new_string(the_string):
    new_string = something_to_do_with_the_old_string(the_string)
    return new_string

# then you could call it like
my_string = return_a_whole_new_string(my_string)
```

如果您确实想避免使用返回值，则可以创建一个类来保存您的值，并将其传递给函数或使用现有的类，例如列表

```python 
def use_a_wrapper_to_simulate_pass_by_reference(stuff_to_change):
    new_string = something_to_do_with_the_old_string(stuff_to_change[0])
    stuff_to_change[0] = new_string

# then you could call it like
wrapper = [my_string]
use_a_wrapper_to_simulate_pass_by_reference(wrapper)

do_something_with(wrapper[0])
```

# 更多内容请参考

[how-do-i-pass-a-variable-by-reference](https://stackoverflow.com/questions/986006/how-do-i-pass-a-variable-by-reference)