
необходимо реализовать функцию, которая:
=========================================
* на вход получает список, содержащий int элементы, в произвольной последовательности
* возвращает строку содержащую элементы списка через запятую, при этом
* следующие друг за другом элементы заменяются "-"

пример доктест скрипта для функции (предположим, что вы назвалии ее foo):
-------------------------------------------------------------------------

``` python
    doctest:
    >>> l = [10,7,8,9,1,2,3,5,99]
    >>> print(foo(l))
    '1-3,5,7-10,99'
    >>> l = [10,7,8,9,9,9,7,8,1,2,3,5,99]
    >>> print(foo(l))
    '1-3,5,7-10,99'
    >>> print(foo(range(10)))
    '0-10'
```