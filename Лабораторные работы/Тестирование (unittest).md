<h2> Постановка задачи </h2>

Реализовать вычисление факториала так, чтобы вычисление происходило для случаев, когда пользователь ввел натуральное число от 0 до n (где, n — целое, натуральное число, помещающееся в переменную целого числа). 

Для всех других случаев функция должна поднимать исключение **TypeError** или **ValueError** 

Протестируйте работу этой функции с помощью *unittest**. 

Учтите ситуации, для которых должно подниматься исключения и найдите в документации модуля unittest как эту ситуацию обработать.

<h3> Текст программы: </h3>

```python
def fact(n):
    res = None
    try: 
        if type(n) is not int:
            raise TypeError 
        n = int(n)
    except (ValueError, TypeError) as e:
        print('Argument "{}" is not a number '.format(n))
    else: 
        if n < 0:
            print('Argument "{}" less than 0 '.format(n))
        elif n == 0:
            return 1
        else:
            res = n * fact(n-1)
            return res 

if __name__ == '__main__':
    unittest.main()
```

<h3> Текст программы модуля для тестирования: </h3>

```python
import unittest
import fact
    
    class TestFactorialMethods(unittest.TestCase):
    
        def test_normal_values(self):
            self.assertEqual(fact(0), 1)
            self.assertEqual(fact(5), 120)
            self.assertEqual(fact(10), 3628800)
            
        def test_vals_float_type(self):
            self.assertTrue(fact(0.5) is None)
            self.assertTrue(fact(7.12456789) is None)   
            
        def test_except_ValueError(self):            
            with self.assertRaises(ValueError):
                fact(-100)
                
        def test_except_TypeError(self):            
            with self.assertRaises(TypeError):
                fact('')
            with self.assertRaises(TypeError):
                fact([0,1,2,3,4,5])
            with self.assertRaises(TypeError):
                fact({'dog':'cat'})
                     
        def test_vals_bool_type(self):
            self.assertIsNone(fact(False), None)
            self.assertIsNone(fact(True), None)        
                
        def test_negative_values(self):
            self.assertEqual(fact(-1), None)
            self.assertEqual(fact(-10), None)
            self.assertEqual(fact(-100500), None)
                   
        def test_iter_objs(self):
            self.assertIs(fact([1,2,3]), None )
            self.assertIs(fact({2,3}), None )
            self.assertIs(fact('qwerty'), None )        
            self.assertIs(fact('10a'), None )   
```
