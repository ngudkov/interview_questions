
Вопросы по python3.6+:
=========================================

1. Что бы вы изменили в этом коде? Есть ли в коде ошибки, если да то какие?
```python
# function than do some stuff
def isNone(Arg):
    if Arg:
        return False
    return True
```
2. Что выведет следующий код:
```python
print(1==True==2)
```
3. Что выведет python3 при выпонении данного кода
```python
l = [1,2,3,4,4,4,]
a = [x for x in l]
b = (x for x in l)
c = {x for x in d}

print(a)
print(b)
print(c)
```
4. Что выведет следующий код:

```python
def f(*args, **kwargs):
    print(args, kwargs)

f(*[1, 2, 3])
```

5. Что выведет следущий код:

```python
a = dict(one=1, two=2, three=3)
keys = a.keys()
a['four']=4
print(keys)
```

3. Что произойдет в результате выполнения следующего кода:

```python
t = (1, 2, [30, 40])
t[2] += [50, 60]
```
  1. t принимает значение (1, 2, [30, 40, 50, 60])
  2. возбуждается исключение TypeError с сообщением о том, что объект ‘tuple’ не поддерживает присваивание.
  3. Ни то, ни другое
  4. И то, и другое