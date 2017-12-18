<h2> Постановка задачи </h2>




<h3> Текст программы: </h3>

```python
a = {'A':'N', 'B':'O', 'C':'P', 'D':'Q', 'E':'R', 'F':'S'}
a1 = {'G':'T', 'H':'U', 'I':'V', 'J':'W', 'K':'X', 'L':'Y', 'M':'Z'}

#NOPQRS
#TUVWXYZ

b = {'N':'A', 'O':'B', 'P':'C', 'Q':'D', 'R':'E', 'S':'F'} 
b1 = {'T':'G', 'U':'H', 'V':'I', 'W':'J', 'X':'K', 'Y':'L', 'Z':'M'}

#ABCDEF
#GHIJKLM

a.update(a1)
b.update(b1)
a.update(b) #capitalization dictionary


w = {'a':'n', 'b':'o', 'c':'p', 'd':'q', 'e':'r', 'f':'s'}
w1 = {'g':'t', 'h':'u', 'i':'v', 'j':'w', 'k':'x', 'l':'y', 'm':'z'}


v = {'n':'a', 'o':'b', 'p':'c', 'q':'d', 'r':'e', 's':'f'} 
v1 = {'t':'g', 'u':'h', 'v':'i', 'w':'j', 'x':'k', 'y':'l', 'z':'m'}


w.update(w1)
v.update(v1)
w.update(v) #lowercase dictionary

a.update(w) #full dictionary


def ROT13():
  
  print('What do You want to do? \n 1 - to decrypt (ROT13 -> EN) \n 2 - to encrypt (EN -> ROT13)  ')
  x = float(input('> Enter operation number: '))
  s = input('>> Enter the string: ')
  str = ''

  if x == 1:
    for item in s:
      if item in a.keys():
        str += a.get(item)
    print(">>> Decoding: ", str)
  else:      
    inv_a = {v:k for k, v in a.items()}
    for item in s:
      if item in inv_a.keys():
        str += inv_a.get(item)
    print('>>> Encoding: ', str)
  
  
ROT13()
```
<h3> Результат выполнения программы: </h3>

    What do You want to do? 
     1 - to decrypt (ROT13 -> EN) 
     2 - to encrypt (EN -> ROT13)  
    > Enter operation number:  1
    >> Enter the string:  Hello
    >>> Decoding:  Uryyb

