<h2> Постановка задачи </h2>

Для задачи ниже:

    Есть два списка разной длины. В первом содержатся ключи, а во втором значения. Напишите функцию, которая создаёт из этих ключей и значений словарь. Если ключу не хватило значения, в словаре должно быть значение None. Значения, которым не хватило ключей, нужно игнорировать.
    Напишите с использованием пакета Py.test и модуля hypothesis тесты, которые проверяли бы работу этой программы.

Для проверки с помощью гипотез вам потребуется использовать стратегии (strategies). Примеры их использования смотри в официальной документации: https://hypothesis.readthedocs.io/

<h3> Текст программы: </h3>

```python
list_keys = [1, 2, 3]
list_values = ['one', 'two']

list_keys_ = [1, 2, 3]
list_values_ = ['one', 'two']

l1 = [1, 2, 3]
l2 = ['a','b']


# ------------------------------------------

def dict_from_keys_and_values(k, v):
    if len(k) > len(v):
      [v.append(None) for j in range(1, len(k) - len(v) + 1)]
    return dict(map(lambda key, value: (key, value), k, v))


print(' Result#1:', dict_from_keys_and_values(list_keys, list_values))
print(' Result#2:', dict_from_keys_and_values(list_keys_, list_values_))
print(' Result#3:', dict_from_keys_and_values(l1, l2))
```
<h3> Текст программы модуля для тестирования: </h3>

```python
import pytest
import hypothesis.strategies as st
from hypothesis import given
import main

def testing_fun1():
    assert main.dict_from_keys_and_values([1, 2, '3'], ['Py', '0', 'None']) == {1: 'Py', 2: '0', '3': 'None'},'1'

@given(st.sets(st.integers()), st.sets(st.integers()))
def test_fill_itegers(keys, values):
    keys = list(keys)
    values = list(values)
    dictionary =  main.dict_from_keys_and_values(keys, values)

    if len(keys) < len(values):
        values = values[0:len(keys):]
    if len(values) < len(keys):
        for i in range(len(keys) - len(values)):
            values.append(None)

    assert list(dictionary.keys()) == keys
    assert list(dictionary.values()) == values
```
