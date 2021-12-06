# Pythonisms



### Iterators

In this example, we use the magic method dunder __iter__ to allow us to loop over our own implementation of a linked list data structure as well as being able to use list comprehension it and convert it to a list.

Example Code:

```python
  def __iter__(self):
    def generator():
      current = self.head
      while current:
        yield current.data
        current = current.next
    return generator()
```


### Decorators

In this example, we 2 decoraters in order to delay the execution of a provided function as well ass add some sarcasm to it.

```python
from functools import wraps
from time import sleep

def procrastinate(func):
  @wraps(func)
  def wrapper(*args, **kwargs):
    """
    Wrapper wraps the stuff
    """
    sleep(3)
    return func(*args, **kwargs)
  return wrapper

def sarcastic_decorator(func):
  @wraps(func)
  def wrapper(*args, **kwargs):
    output =  func(*args, **kwargs)
    return f'Oh Sure, "{output}" sounds like a great book title'
  return wrapper


@procrastinate
@sarcastic_decorator
def say(text):
  """ 
  Say says the things
  """
  return text
```
And when this function is called, it will first wait for 3 seconds and then after that execute the given code:

```python
# call the function
print(say("Dario thinks he is awesome."))

# output wait for 3 seconds
# then output print(say("Dario thinks he is awesome."))
```



### Dunder methods to make our code more readable

In this code, we use dunder __str__ to visualize our linked list implmentation in a string

```python
  def __str__(self):
    current = self.head
    output = []
    while current:
        output.append(f"{{{current.data}}}")
        current = current.next
```

To call use this method, we simply do:
```python
print(str(linked_list))

# output will be "{5}->{2}->{25}" for example
```




[Open Pull Request](https://github.com/MusaabShalaldeh/pythonisms/pulls)