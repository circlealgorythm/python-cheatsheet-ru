Комплексная шпаргалка по Python (Comprehensive Python Cheatsheet)
=================================================================
> [!NOTE]
> Это русскоязычная версия популярной шпаргалки по Python.
> **Оригинальный репозиторий и автор:** [gto76/python-cheatsheet](https://github.com/gto76/python-cheatsheet) (Jure Šorn).

<sup>[Скачать файл](https://raw.githubusercontent.com/circlealgorythm/python-cheatsheet-ru/main/README.md), [Форкнуть на GitHub](https://github.com/circlealgorythm/python-cheatsheet-ru) или [Оригинал gto76](https://github.com/gto76/python-cheatsheet).
</sup>

![Monty Python](web/image_888.jpeg)


Содержание (Contents)
---------------------
**&nbsp;&nbsp;&nbsp;** **1. Коллекции:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;** **[`List`](#list)**__,__ **[`Dictionary`](#dictionary)**__,__ **[`Set`](#set)**__,__ **[`Tuple`](#tuple)**__,__ **[`Range`](#range)**__,__ **[`Enumerate`](#enumerate)**__,__ **[`Iterator`](#iterator)**__,__ **[`Generator`](#generator)**__.__  
**&nbsp;&nbsp;&nbsp;** **2. Типы данных:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Type`](#type)**__,__ **[`String`](#string)**__,__ **[`Regular_Exp`](#regex)**__,__ **[`Format`](#format)**__,__ **[`Numbers`](#numbers-1)**__,__ **[`Combinatorics`](#combinatorics)**__,__ **[`Datetime`](#datetime)**__.__  
**&nbsp;&nbsp;&nbsp;** **3. Синтаксис:** **&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Function`](#function)**__,__ **[`Inline`](#inline)**__,__ **[`Import`](#import)**__,__ **[`Decorator`](#decorator)**__,__ **[`Class`](#class)**__,__ **[`Duck_Type`](#duck-types)**__,__ **[`Enum`](#enum)**__,__ **[`Except`](#exceptions)**__.__  
**&nbsp;&nbsp;&nbsp;** **4. Системные вызовы:** **&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Exit`](#exit)**__,__ **[`Print`](#print)**__,__ **[`Input`](#input)**__,__ **[`Command_Line_Arguments`](#arguments)**__,__ **[`Open`](#open)**__,__ **[`Path`](#paths)**__,__ **[`OS_Commands`](#os-commands)**__.__  
**&nbsp;&nbsp;&nbsp;** **5. Форматы данных:** **&nbsp;&nbsp;&nbsp;**  **[`JSON`](#json)**__,__ **[`Pickle`](#pickle)**__,__ **[`CSV`](#csv)**__,__ **[`SQLite`](#sqlite)**__,__ **[`Bytes`](#bytes)**__,__ **[`Struct`](#struct)**__,__ **[`Array`](#array)**__,__ **[`Memory_View`](#memory-view)**__,__ **[`Deque`](#deque)**__.__  
**&nbsp;&nbsp;&nbsp;** **6. Разное:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Operator`](#operator)**__,__ **[`Match_Statement`](#match-statement)**__,__ **[`Logging`](#logging)**__,__ **[`Introspection`](#introspection)**__,__ **[`Threads`](#threading)**__,__ **[`Asyncio`](#asyncio)**__.__  
**&nbsp;&nbsp;&nbsp;** **7. Pip-пакеты:** **&nbsp;&nbsp;&nbsp;**  **[`Progress_Bar`](#progress-bar)**__,__ **[`Plot`](#plot)**__,__ **[`Table`](#table)**__,__ **[`Console_App`](#console-app)**__,__ **[`GUI`](#gui-app)**__,__ **[`Scraping`](#scraping)**__,__ **[`Web`](#web-app)**__,__ **[`Profile`](#profiling)**__.__  
**&nbsp;&nbsp;&nbsp;** **8. Мультимедиа:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`NumPy`](#numpy)**__,__ **[`Image`](#image)**__,__ **[`Animation`](#animation)**__,__ **[`Audio`](#audio)**__,__ **[`Synthesizer`](#synthesizer)**__,__ **[`Pygame`](#pygame)**__,__ **[`Pandas`](#pandas)**__,__ **[`Plotly`](#plotly)**__.__


Main
----
```python
if __name__ == '__main__':      # Пропускает блок кода с отступом, если файл был импортирован как модуль.
    main()                      # Выполняет пользовательскую функцию `def main(): ...`.
```


List
----
```python
<list> = [<el>, <el>, ...]      # Создаёт новый объект списка. Например: `list_a = [1, 2, 3]`.
```

```python
<el>   = <list>[index]          # Первый индекс 0, последний -1. Также `<list>[i] = <el>`.
<list> = <list>[<slice>]        # Также <list>[от_включ : до_исключ : ±шаг].
```

```python
<list>.append(<el>)             # Добавляет элемент в конец. Или `<list> += [<el>]`.
<list>.extend(<coll>)           # Добавляет элементы коллекции в конец. Или `<list> += <coll>`.
```

```python
<list>.sort()                   # Сортирует по возрастанию на месте. Принимает `reverse=True`.
<list>.reverse()                # Разворачивает порядок элементов на месте. Сложность O(N).
<list> = sorted(<coll>)         # Возвращает новый отсортированный список. Принимает `reverse=True`.
<iter> = reversed(<list>)       # Возвращает обратный итератор. Также list(<iterator>).
```

```python
<el>  = max(<coll>)             # Возвращает наибольший элемент. Также min(<el>, <el>).
<num> = sum(<coll>)             # Возвращает сумму элементов. Также math.prod(<coll>).
```

```python
elementwise_sum  = [sum(pair) for pair in zip(list_a, list_b)]
sorted_by_second = sorted(<coll>, key=lambda pair: pair[1])
sorted_by_both   = sorted(<coll>, key=lambda p: (p[1], p[0]))
flatter_list     = list(itertools.chain.from_iterable(<list>))
```
* **Подробнее о sort(), sorted(), max() и min() см. раздел [Sortable](#sortable).**
* **Модуль [operator](#operator) содержит функцию itemgetter(), которая может заменить приведённые [лямбды](#lambda).**
* **В этом тексте используется термин «коллекция» вместо [iterable](#abstract-base-classes). Обоснование см. в [утиных типах](#iterable-duck-types).**

```python
<int> = len(<list/dict/set/…>)  # Возвращает количество элементов. Не принимает итераторы.
<int> = <list>.count(<el>)      # Считает количество вхождений. Также `if <el> in <coll>: ...`.
<int> = <list>.index(<el>)      # Возвращает индекс первого вхождения или вызывает ValueError.
<el>  = <list>.pop()            # Удаляет элемент с конца (или по указанному индексу).
<list>.insert(<int>, <el>)      # Вставляет элемент по индексу со сдвигом остальных элементов.
<list>.remove(<el>)             # Удаляет первое вхождение или вызывает ValueError.
<list>.clear()                  # Удаляет все элементы. Также доступно для dict и set.
```


Dictionary
----------
```python
<dict> = {key: val, key: val, ...}            # Используйте `<dict>[key]` для получения или присвоения значения.
```

```python
<view> = <dict>.keys()                        # Представление (view) ключей, отражающее все изменения словаря.
<view> = <dict>.values()                      # Представление значений, отражающее все изменения словаря.
<view> = <dict>.items()                       # Представление пар (кортежей). Каждый содержит ключ и значение.
```

```python
value  = <dict>.get(key, default=None)        # Возвращает аргумент 'default', если ключ отсутствует.
value  = <dict>.setdefault(key, default)      # Возвращает/записывает 'default', когда ключ отсутствует.
<dict> = collections.defaultdict(<type>)      # Словарь со значением по умолчанию `<type>()`.
```

```python
<dict> = dict(<collection>)                   # Создаёт словарь из коллекции пар ключ-значение.
<dict> = dict(zip(keys, values))              # Создаёт пары ключ-значение из двух коллекций.
<dict> = dict.fromkeys(keys [, value])        # Элементы получают значение None, если переданы только ключи.
```

```python
<dict>.update(<dict>)                         # Добавляет элементы в словарь. Переданный словарь имеет приоритет.
value = <dict>.pop(key)                       # Удаляет элемент или вызывает KeyError, если ключ не найден.
{k for k, v in <dict>.items() if v == 123}    # Возвращает множество ключей, значение которых равно 123.
{k: v for k, v in <dict>.items() if k in ks}  # Возвращает словарь элементов с указанными ключами.
```

### Counter
```python
>>> from collections import Counter
>>> counter = Counter(['blue', 'blue', 'red'])
>>> counter['yellow'] += 3
>>> print(counter.most_common())
[('yellow', 3), ('blue', 2), ('red', 1)]
```


Set
---
```python
<set> = {<el>, <el>, ...}           # Коллекция уникальных элементов. Также set(), set(<coll>).
```

```python
<set>.add(<el>)                     # Добавляет элемент во множество. То же, что `<set> |= {<el>}`.
<set>.update(<coll> [, ...])        # Добавляет элементы во множество. То же, что `<set> |= <set>`.
```

```python
<set> = <set>.union(<coll>)         # Возвращает объединение множеств. Также `<set> | <set>`.
<set> = <set>.intersection(<coll>)  # Возвращает пересечение элементов. Также `<set> & <set>`.
<set> = <set>.difference(<coll>)    # Возвращает разность множеств. Также `<set> - <set>`.
```

```python
<bool> = <set>.issuperset(<coll>)   # Возвращает False, если в коллекции есть уникальные элементы.
<bool> = <set>.issubset(<coll>)     # Является ли коллекция подмножеством? Также `<set> <= <set>`.
```

```python
<el> = <set>.pop()                  # Удаляет и возвращает случайный элемент. Вызывает KeyError, если пусто.
<set>.remove(<el>)                  # Удаляет элемент или вызывает KeyError, если он отсутствует.
<set>.discard(<el>)                 # То же, что remove(), но не вызывает ошибку при отсутствии элемента.
```

### Frozen Set
* **Frozenset — это неизменяемая (immutable) и хешируемая (hashable) версия обычного множества set.**
* **Это означает, что его можно использовать как ключ в dict или как элемент в set.**
```python
<frozenset> = frozenset(<collection>)
```


Tuple
-----
**Кортеж (Tuple) — это неизменяемый и хешируемый список.**
```python
<tuple> = ()                        # Возвращает пустой кортеж. Также tuple(), tuple(<coll>).
<tuple> = (<el>,)                   # Возвращает кортеж из одного элемента. Или `<tup.> = <el>,`.
<tuple> = (<el>, <el> [, ...])      # Возвращает кортеж. Или `<tuple> = <el>, <el> [, ...]`.
```

### Named Tuple
**Подкласс кортежа с именованными элементами (полями).**
```python
>>> import collections as co
>>> Point = co.namedtuple('Point', 'x y')
>>> p = Point(1, y=2)
>>> print(p)
Point(x=1, y=2)
>>> p.x, p[1]
(1, 2)
```


Range
-----
**Последовательность равномерно распределённых целых чисел.**
```python
<range> = range(stop)                # То есть range(до_исключ). Числа от 0 до `stop-1`.
<range> = range(start, stop)         # То есть range(от, до_исключ). От start до `stop-1`.
<range> = range(start, stop, step)   # То есть range(от_включ, до_исключ, ±шаг).
```

```python
>>> [i for i in range(3)]
[0, 1, 2]
```

### Enumerate
**Итератор, связывающий элементы коллекции с их числовыми индексами.**
```python
for i, el in enumerate(<coll>):
    print(f'Element {el} has index {i}.')
```


Iterator
--------
**Потенциально бесконечный поток элементов.**

```python
import itertools as it
```

```python
<iter> = iter(<coll>)                    # Итератор, возвращающий элементы переданной коллекции по одному.
<iter> = iter(<func>, to_exc)            # Вызывает `<func>()`, пока не вернётся значение 'to_exc'.
<iter> = (<expr> for <name> in <coll>)   # Например: `(i+1 for i in range(3))`. Вычисляется лениво.
<el>   = next(<iter> [, default])        # Вызывает StopIteration или возвращает 'default' в конце.
<list> = list(<iter>)                    # Возвращает список оставшихся элементов итератора.
```

```python
<iter> = it.count(start=0, step=1)       # Бесконечно возвращает обновлённый 'start'. Принимает float.
<iter> = it.repeat(<obj> [, times])      # Бесконечно повторяет элемент или 'times' раз.
<iter> = it.cycle(<coll>)                # Бесконечно циклически перебирает элементы. Принимает итераторы.
```

```python
<iter> = it.chain(<coll>, <coll>, ...)   # Возвращает по порядку каждый элемент каждой коллекции.
<iter> = it.chain.from_iterable(<coll>)  # Принимает коллекцию (итерируемый объект) коллекций.
<iter> = it.islice(<coll>, stop)         # Также принимает 'start' и 'step'. Аргументы могут быть None.
<iter> = it.product(<coll>, <coll>)      # То же, что и `((a, b) for a in arg_1 for b in arg_2)`.
```
* **Циклы for вызывают `'iter(<coll/iter>)'`, при этом для итератора возвращается он сам без изменений.**


Generator
---------
* **Любая функция, содержащая оператор yield, возвращает генератор.**
* **Генераторы и итераторы взаимозаменяемы (см. утиный тип [Iterator](#iterator-1)).**

```python
def count(start, step):
    while True:
        yield start
        start += step
```

```python
>>> counter = count(10, 2)
>>> next(counter), next(counter), next(counter)
(10, 12, 14)
```


Type
----
* **Все значения в Python являются объектами.**
* **Каждый объект принадлежит определённому типу.**
* **Термины «тип» (type) и «класс» (class) синонимичны.**

```python
<type> = type(<obj>)                   # Тип объекта. Также `<obj>.__class__`.
<bool> = isinstance(<obj>, <type>)     # Также `issubclass(type(<obj>), <type>)`.
```

```python
>>> type('a'), 'a'.__class__, str
(<class 'str'>, <class 'str'>, <class 'str'>)
```

#### Некоторые типы не имеют встроенных имён, поэтому их нужно импортировать:
```python
from types import FunctionType, MethodType, LambdaType, GeneratorType
```

### Abstract Base Classes
**Каждый абстрактный базовый класс (ABC) определяет набор виртуальных подклассов. Эти классы затем распознаются функциями isinstance() и issubclass() как [подклассы](#subclass) этого ABC, даже если они явно от него не наследовались. ABC также может динамически определять принадлежность класса (обычно проверяя наличие нужных методов). Например, ABC Iterable проверяет метод iter(), а Collection — методы iter(), contains() и len().**

```python
>>> from collections.abc import Iterable, Collection, Sequence
>>> isinstance([1, 2, 3], Iterable)
True
```

```text
+------------------+------------+------------+------------+
|                  |  Iterable  | Collection |  Sequence  |
+------------------+------------+------------+------------+
| list, range, str |    да      |    да      |    да      |
| dict, set        |    да      |    да      |            |
| iter             |    да      |            |            |
+------------------+------------+------------+------------+
```

```python
>>> from numbers import Number, Complex, Real, Rational, Integral
>>> isinstance(123, Number)
True
```

```text
+--------------------+---------+---------+--------+----------+----------+
|                    |  Number | Complex |  Real  | Rational | Integral |
+--------------------+---------+---------+--------+----------+----------+
| int                |   да    |   да    |   да   |   да     |   да     |
| fractions.Fraction |   да    |   да    |   да   |   да     |          |
| float              |   да    |   да    |   да   |          |          |
| complex            |   да    |   да    |        |          |          |
| decimal.Decimal    |   да    |         |        |          |          |
+--------------------+---------+---------+--------+----------+----------+
```


String
------
**Неизменяемая последовательность символов.**
```python
<str>  = 'abc'                       # Также "abc". Интерпретирует \n, \t, \x00-\xff и т.д.
```

```python
<str>  = <str>.strip()               # Удаляет пробельные символы с обоих концов строки.
<str>  = <str>.strip('<chars>')      # Удаляет указанные символы. Также lstrip/rstrip().
```

```python
<list> = <str>.split()               # Разбивает строку по одному или нескольким пробельным символам.
<list> = <str>.split(<str>)          # Разбивает по указанной строке. Также `maxsplit=<int>`.
<list> = <str>.splitlines()          # По [\n\r\f\v\x1c-\x1e\x85\u2028\u2029] и \r\n.
<str>  = <str>.join(<coll_of_str>)   # Объединяет элементы, используя строку в качестве разделителя.
```

```python
<bool> = <str> in <str>              # Возвращает True, если строка содержит подстроку.
<bool> = <str>.startswith(<str>)     # Принимает кортеж строк для проверки вариантов.
<int>  = <str>.find(<str>)           # Возвращает индекс первого совпадения или `-1`.
```

```python
<str>  = <str>.lower()               # Переводит в нижний регистр. Также upper/capitalize/title().
<str>  = <str>.casefold()            # Агрессивный lower(): переводит ẞ/ß в ss, Σ/ς в σ и т.д.
<str>  = <str>.replace(old, new)     # Заменяет вхождения old; удаляет old, если new равен ''.
<str>  = <str>.translate(table)      # Таблица создаётся через str.maketrans(<chr_to_str_dict>).
```

```python
<str>  = chr(<int>)                  # Преобразует целое число в соответствующий символ Unicode.
<int>  = ord(<str>)                  # Преобразует символ Unicode в его целочисленный код.
```
* **Используйте `'unicodedata.normalize("NFC", <str>)'` для строк вида `'Motörhead'` перед их сравнением, поскольку `'ö'` может храниться как один символ или как два.**
* **`'NFC'` преобразует составные символы в один символ, а `'NFD'` раскладывает их на два.**

```python
<bool> = <str>.isdecimal()           # Проверяет, что все символы [0-9]. Также [०-९], [٠-٩].
<bool> = <str>.isdigit()             # Проверяет на [²³¹…] и isdecimal(). Также [፩-፱].
<bool> = <str>.isnumeric()           # Проверяет на [¼½¾…] и isdigit(). Также [零〇一…].
<bool> = <str>.isalnum()             # Проверяет на [ABC…] и isnumeric(). Также [ªµº…].
<bool> = <str>.isprintable()         # Проверяет на [ !"#…], базовые эмодзи и isalnum().
<bool> = <str>.isspace()             # Проверяет на пробельные символы [ \t\n\r\f\v\x1c\x1d\x1e\x1f\x85…].
```


Regex
-----
**Функции для работы с регулярными выражениями.**

```python
import re
<str>   = re.sub(r'<regex>', new, text)  # Заменяет совпадения строкой 'new'.
<list>  = re.findall(r'<regex>', text)   # Возвращает все совпадения в виде списка строк.
<list>  = re.split(r'<regex>', text)     # Добавьте скобки вокруг regex, чтобы сохранить совпадения.
<Match> = re.search(r'<regex>', text)    # Находит первое совпадение с шаблоном или возвращает None.
<Match> = re.match(r'<regex>', text)     # Ищет совпадение только в начале строки 'text'.
<iter>  = re.finditer(r'<regex>', text)  # Возвращает все совпадения в виде объектов Match.
```

* **«Сырые» строки (raw string literals, `r'...'`) не интерпретируют escape-последовательности, позволяя использовать спецсимволы regex, вызывающие SyntaxWarning в обычных строках (начиная с 3.12).**
* **Аргумент `'new'` может быть функцией, принимающей объект Match и возвращающей строку.**
* **Параметр `'flags=re.IGNORECASE'` применим во всех перечисленных функциях.**
* **Параметр `'flags=re.MULTILINE'` заставляет `'^'` и `'$'` соответствовать началу/концу каждой строки текста.**
* **Параметр `'flags=re.DOTALL'` заставляет символ `'.'` соответствовать в том числе и `'\n'`.**
* **`'re.compile(r"<regex>")'` компилирует regex в объект Pattern с методами sub(), findall() и т.д.**

### Match Object
```python
<str>   = <Match>.group()                # Возвращает совпадение целиком. Также group(0).
<str>   = <Match>.group(1)               # Возвращает часть внутри первых круглых скобок.
<tuple> = <Match>.groups()               # Возвращает все группы в скобках как кортеж строк.
<int>   = <Match>.start()                # Возвращает начальный индекс всего совпадения.
<int>   = <Match>.end()                  # Возвращает конечный индекс совпадения плюс один.
```

### Special Sequences
```python
'\d' == '[0-9]'                          # Также [०-९…]. Соответствует десятичной цифре.
'\w' == '[a-zA-Z0-9_]'                   # Также [ª²³…]. Соответствует букве, цифре или знаку _.
'\s' == '[ \t\n\r\f\v]'                  # Также [\x1c-\x1f…]. Соответствует пробельным символам.
```
* **По умолчанию сопоставляются цифры и буквы из всех алфавитов, если не указан `'flags=re.ASCII'`. Этот флаг ограничивает совпадения первыми 128 символами Unicode (ASCII) и запрещает `'\s'` принимать управляющие символы `'\x1c'`, `'\x1d'`, `'\x1e'` и `'\x1f'`.**
* **Используйте заглавные буквы (`'\D'`, `'\W'`, `'\S'`) для отрицания.**


Format
------
**Механизмы форматирования строк.**
```perl
<str> = f'{<obj>}, {<obj>}'             # Внутри фигурных скобок можно писать выражения.
<str> = '{}, {}'.format(<obj>, <obj>)   # Или '{0}, {a}'.format(<obj>, a=<obj>).
<str> = '%s, %s' % (<obj>, <obj>)       # Устаревший метод (printf-стиль).
```

### Example
```python
>>> Person = collections.namedtuple('Person', 'name height')
>>> jean = Person('Jean-Luc', 187)
>>> f'{jean.name} is {jean.height / 100} meters tall.'
'Jean-Luc is 1.87 meters tall.'
```

### Options
```python
{<obj>:<10}                             # '<obj>     '.
{<obj>:^10}                             # '  <obj>   '.
{<obj>:>10}                             # '     <obj>'.
{<obj>:.<10}                            # '<obj>.....'.
{<obj>:0}                               # '<obj>'.
```
* **Объекты преобразуются в строки функцией format(), например `'format(<obj>, "<10")'`.**
* **Параметры можно формировать динамически во вложенных скобках: `f'{<obj>:{<str/int>}[…]}'`.**
* **Добавление `'='` к выражению выводит само выражение перед результатом: `f'{1+1=}'` вернёт `'1+1=2'`.**
* **Добавление `'!r'` к выражению сначала вызывает [repr()](#class) объекта и лишь затем format().**

### Strings
```python
{'abcde':10}                            # 'abcde     '.
{'abcde':10.3}                          # 'abc       '.
{'abcde':.3}                            # 'abc'.
{'abcde'!r:10}                          # "'abcde'   ".
```

### Numbers
```python
{123456:10}                             # '    123456'.
{123456:10,}                            # '   123,456'.
{123456:10_}                            # '   123_456'.
{123456:+10}                            # '   +123456'.
{123456:=+10}                           # '+   123456'.
```

### Floats
```python
{1.23456:10.3}                          # '      1.23'.
{1.23456:10.3f}                         # '     1.235'.
{1.23456:10.3e}                         # ' 1.235e+00'.
{1.23456:10.3%}                         # '  123.456%'.
```


#### Сравнение типов представления чисел (Comparison of presentation types):
```text
+---------------+---------------+---------------+---------------+---------------+
|               |  {<number>}   |   {<num>:f}   |   {<num>:e}   |   {<num>:%}   |
+---------------+---------------+---------------+---------------+---------------+
|   0.000056789 |   5.6789e-05  |    0.000057   |  5.678900e-05 |    0.005679%  |
|   0.00056789  |   0.00056789  |    0.000568   |  5.678900e-04 |    0.056789%  |
|   0.0056789   |   0.0056789   |    0.005679   |  5.678900e-03 |    0.567890%  |
|   0.056789    |   0.056789    |    0.056789   |  5.678900e-02 |    5.678900%  |
|   0.56789     |   0.56789     |    0.567890   |  5.678900e-01 |   56.789000%  |
|   5.6789      |   5.6789      |    5.678900   |  5.678900e+00 |  567.890000%  |
|  56.789       |  56.789       |   56.789000   |  5.678900e+01 | 5678.900000%  |
+---------------+---------------+---------------+---------------+---------------+
```

```text
+---------------+---------------+---------------+---------------+---------------+
|               |  {<float>:.2} |  {<num>:.2f}  |  {<num>:.2e}  |  {<num>:.2%}  |
+---------------+---------------+---------------+---------------+---------------+
|   0.000056789 |    5.7e-05    |      0.00     |    5.68e-05   |      0.01%    |
|   0.00056789  |    0.00057    |      0.00     |    5.68e-04   |      0.06%    |
|   0.0056789   |    0.0057     |      0.01     |    5.68e-03   |      0.57%    |
|   0.056789    |    0.057      |      0.06     |    5.68e-02   |      5.68%    |
|   0.56789     |    0.57       |      0.57     |    5.68e-01   |     56.79%    |
|   5.6789      |    5.7        |      5.68     |    5.68e+00   |    567.89%    |
|  56.789       |    5.7e+01    |     56.79     |    5.68e+01   |   5678.90%    |
+---------------+---------------+---------------+---------------+---------------+
```
* **`'{<num>:g}'` эквивалентно `'{<float>:.6}'`, но убирает `'.0'` и переключается на экспоненциальную запись, начиная с `'1e+06'`.**
* **При округлении половины (round half to even) выбирается значение с чётной последней цифрой: поэтому `'{6.5:.0f}'` даёт `'6'`, а `'{7.5:.0f}'` даёт `'8'`.**
* **Это правило действует только на числа, которые могут быть точно представлены типом float (`.5`, `.25`, …).**

### Ints
```python
{90:x}                                  # Преобразует 90 в шестнадцатеричное число '5a'.
{90:b}                                  # Преобразует 90 в двоичное число '1011010'.
{90:c}                                  # Преобразует 90 в символ Unicode 'Z'.
```


Numbers
-------
```python
<integer> = int(<float/str/bool>)             # Целое число. Отсекает дробную часть у float.
<float>   = float(<integer/str/bool>)         # 8-байтовое число с плавающей точкой. Также <fl>e±<int>.
<complex> = complex(real=0, imag=0)           # Комплексное число. Также <fl> ± <fl>j.
<Fract>   = fractions.Fraction(numr, denom)   # `<Fraction> = <Fraction> / <int>`.
<Decimal> = decimal.Decimal(<str/int/tup>)    # `Decimal((1, (2,), 3)) == -2000`.
```
* **`'int(<str>)'` и `'float(<str>)'` вызывают исключение ValueError, если строка некорректна.**
* **Объекты Decimal хранят числа абсолютно точно, в отличие от большинства float, где `'1.1 + 2.2 != 3.3'`.**
* **Числа с плавающей точкой следует сравнивать через: `'math.isclose(<float>, <float>, rel_tol=1e-9)'`.**
* **Точность операций Decimal задаётся через: `'decimal.getcontext().prec = <int>'`.**
* **Булевы значения bool можно использовать везде, где допустимы int, так как bool — подкласс int: `'True + 1 == 2'`.**

### Built-in
```python
<num> = abs(<num>)                            # Модуль числа: `abs(-50) == abs(50) == 50`.
<num> = pow(<num>, <num>)                     # Возведение в степень: `pow(3, 4) == 3 ** 4 == 81`.
<num> = round(<num> [, ndigits])              # Округление: `round(123.45, -1) == 120`.
<num> = min(<coll_of_nums>)                   # Минимум. Также `max(<num>, <num> [, ...])`.
<num> = sum(<coll_of_nums>)                   # Сумма элементов. Также `math.prod(<coll_of_nums>)`.
```

### Math
```python
import math as mt
<num> = mt.pi/inf/nan                         # `inf*0` и `nan+1` возвращают `nan`.
<num> = mt.sqrt/factorial(<num>)              # `sqrt(-1)` вызовет исключение ValueError.
<num> = mt.sin/cos/tan(<num>)                 # Также degrees, radians, asin и др.
<num> = mt.log/log10/log2(<num>)              # Log() может принимать аргумент 'base'.
```

### Statistics
```python
import statistics as st
<obj>  = st.mean/median(<coll>)               # Mode возвращает наиболее часто встречающийся элемент.
<num>  = st.variance/stdev(<coll>)            # Оценивает дисперсию / станд. отклонение по выборке.
<list> = st.quantiles(<coll>, n=4)            # Оценивает квартили (точки разбиения) по выборке.
```

### Random
```python
import random as rd
<num> = rd.random()                           # Случайное число float из полуинтервала [0, 1).
<num> = rd.randint/uniform(a, b)              # Случайное int/float из отрезка [a, b].
<num> = rd.gauss(mean, stdev)                 # Нормальное распределение. Также triangular(low, high, mode).
<obj> = rd.choice(<sequence>)                 # Случайный выбор без изменений. Также sample(p, n).
rd.shuffle(<list>)                            # Перемешивает на месте. Работает с любыми изменяемыми seq.
```

### Hex, Bin
```python
<int> = 0x<hex>                               # Например: `0xFf == 255`. Также 0b<bin>.
<int> = int('±<hex>', 16)                     # Также int('±0x<hex>/±0b<bin>', 0).
<str> = hex(<int>)                            # Возвращает '[-]0x<hex>'. Также bin().
```

### Bitwise
```python
<int> = <int> & <int>                         # Побитовое И: `0b1100 & 0b1010 == 0b1000`.
<int> = <int> | <int>                         # Побитовое ИЛИ: `0b1100 | 0b1010 == 0b1110`.
<int> = <int> ^ <int>                         # Побитовое исключающее ИЛИ (XOR): `0b1100 ^ 0b1010 == 0b0110`.
<int> = <int> << n_bits                       # Битовый сдвиг влево: `0b1111 << 4 == 0b11110000`.
<int> = ~<int>                                # Побитовое НЕ (инверсия): `~100 == -(100+1) == -101`.
```


Combinatorics
-------------
```python
import itertools as it
```

```python
>>> list(it.product('abc', repeat=2))        #   a  b  c
[('a', 'a'), ('a', 'b'), ('a', 'c'),         # a x  x  x
 ('b', 'a'), ('b', 'b'), ('b', 'c'),         # b x  x  x
 ('c', 'a'), ('c', 'b'), ('c', 'c')]         # c x  x  x
```

```python
>>> list(it.permutations('abc', 2))          #   a  b  c
[('a', 'b'), ('a', 'c'),                     # a .  x  x
 ('b', 'a'), ('b', 'c'),                     # b x  .  x
 ('c', 'a'), ('c', 'b')]                     # c x  x  .
```

```python
>>> list(it.combinations('abc', 2))          #   a  b  c
[('a', 'b'), ('a', 'c'),                     # a .  x  x
 ('b', 'c')                                  # b .  .  x
]                                            # c .  .  .
```


Datetime
--------
**Модуль для работы с объектами даты, времени и даты/времени.**

```python
# $ pip3 install python-dateutil
from datetime import *
import zoneinfo, dateutil.tz
```

```python
<D>  = date(year, month, day)               # Принимает корректные даты от 1 до 9999 года н.э.
<T>  = time(hour=0, minute=0, second=0)     # Принимает `microsecond=0, tzinfo=None, fold=0`.
<DT> = datetime(year, month, day, hour=0)   # Принимает `minute=0, second=0, microsecond=0, …`.
<TD> = timedelta(weeks=0, days=0, hours=0)  # Принимает `minutes=0, seconds=0, microseconds=0`.
```
* **Объекты времени и даты с заданной таймзоной называются осведомлёнными (_aware_), а без неё — наивными (_naive_). Наивные объекты считаются находящимися в системном часовом поясе.**
* **`'fold=1'` обозначает второй проход при переводе стрелок часов назад (обычно на 1 час).**
* **Timedelta нормализует аргументы к ±дням, секундам (< 86 400) и микросекундам (< 1M). Метод str() возвращает `'[±D, ]H:MM:SS[.…]'`, а total_seconds() — количество секунд числом float.**
* **Используйте `'<D/DT>.weekday()'` для получения дня недели числом (понедельник — 0).**

### Now
```python
<D/DTn> = D/DT.today()                      # Текущая локальная дата или наивный DT. Также DT.now().
<DTa>   = DT.now(<tzinfo>)                  # Осведомлённый DT для текущего времени в переданной зоне.
```
* **Для извлечения времени используйте `'<DTn>.time()'`, `'<DTa>.time()'` или `'<DTa>.timetz()'`.**

### Timezone
```python
<tzinfo> = timezone.utc                     # Всемирное координированное время (UTC). Лондон без DST.
<tzinfo> = timezone(<timedelta>)            # Часовой пояс с фиксированным смещением от UTC.
<tzinfo> = dateutil.tz.tzlocal()            # Локальный часовой пояс с динамическим смещением от UTC.
<tzinfo> = zoneinfo.ZoneInfo('<iana_key>')  # Зона 'Континент/Город' с динамическим смещением (IANA).
<DTa>    = <DT>.astimezone(<tzinfo>)        # Преобразует в переданный или локальный часовой пояс.
<Ta/DTa> = <T/DT>.replace(tzinfo=<tzinfo>)  # Заменяет объект таймзоны без конвертации времени.
```
* **Таймзоны, возвращаемые tzlocal(), ZoneInfo() и системная таймзона наивных объектов имеют смещение, изменяющееся во времени из-за перехода на летнее время (DST).**
* **Чтобы ZoneInfo() работал на Windows, выполните `'> pip3 install tzdata'`.**

### Encode
```python
<D/T/DT> = D/T/DT.fromisoformat(<str>)      # Создаёт объект из ISO-строки. Вызывает ValueError при ошибке.
<DT>     = DT.strptime(<str>, '<format>')   # Наивный или осведомлённый datetime из строки по формату.
<D/DTn>  = D/DT.fromordinal(<int>)          # Дата или DT по количеству дней с 1 января 1 года н.э.
<DTn>    = DT.fromtimestamp(<float>)        # Локальный наивный DT из секунд с начала эпохи Unix.
<DTa>    = DT.fromtimestamp(<float>, <tz>)  # Осведомлённый datetime из секунд с начала эпохи Unix.
```
* **ISO-строки имеют вид: `'YYYY-MM-DD'`, `'HH:MM:SS.mmmuuu[±HH:MM]'` или оба вместе через произвольный символ. Все части после часов опциональны.**
* **Python использует эпоху Unix: `'1970-01-01 00:00 UTC'`, `'1970-01-01 01:00 CET'`, ...**

### Decode
```python
<str>    = <D/T/DT>.isoformat(sep='T')      # Также `timespec='auto/hours/minutes/seconds/…'`.
<str>    = <D/T/DT>.strftime('<format>')    # Возвращает строковое представление по заданному формату.
<int>    = <D/DT>.toordinal()               # Количество дней с 1 января 1 года, без учёта времени и зоны.
<float>  = <DTn>.timestamp()                # Секунды с начала эпохи Unix для наивного DT.
<float>  = <DTa>.timestamp()                # Секунды с начала эпохи Unix для осведомлённого DT.
```

### Format
```python
>>> dta = datetime.strptime('2025-08-14 23:39:00.00 +0200', '%Y-%m-%d %H:%M:%S.%f %z')
>>> dta.strftime("%dth of %B '%y (%a), %I:%M %p %Z")
"14th of August '25 (Thu), 11:39 PM UTC+02:00"
```
* **`'%z'` принимает `'±HH[:]MM'` и возвращает `'±HHMM'` или пустую строку, если объект наивный.**
* **`'%Z'` принимает `'UTC'`, `'GMT'` или локальный код зоны и возвращает название таймзоны, `'UTC[±HH:MM]'` (если безымянная) или пустую строку, если объект наивный.**

### Arithmetics
```python
<bool>  =  <D/DTn>  >  <D/DTn>              # Игнорирует скачки времени (атрибут fold). Также `==`.
<bool>  =  <DTa>    >  <DTa>                # Игнорирует скачки, если объекты разделяют один tzinfo.
<TD>    =  <D/DTn>  -  <D/DTn>              # Игнорирует скачки. Для точной дельты переведите в UTC.
<TD>    =  <DTa>    -  <DTa>                # Игнорирует скачки, если разделяют один объект tzinfo.
<D/DT>  =  <D/DT>   ±  <TD>                 # Полученный datetime может попасть в несуществующий час.
<TD>    =  <TD>     ±  <TD>                 # Также `<TD> = abs(<TD>)`, `<num> = <TD> / <TD>`.
```


Function
--------
**Независимый блок кода, возвращающий значение при вызове.**

```python
def my_func(<nondefault_args>): ...                   # Например: `my_func(x, y):`.
def my_func(<default_args>): ...                      # Например: `my_func(x=0, y=0):`.
def my_func(<nondef_args>, <def_args>): ...           # Например: `my_func(x, y=0):`.
```
* **Функция возвращает None, если не встречает оператор `'return <object/expr>'`.**
* **Вызовите `'global <var_name>'` внутри функции перед присваиванием глобальной переменной.**
* **Значение аргумента по умолчанию вычисляется один раз при первом разборе функции.**
* **Любая модификация изменяемого аргумента по умолчанию сохраняется между вызовами функции!**

### Function Call

```python
<obj> = <func>(<positional_args>)                     # Например: `my_func(0, 0)`.
<obj> = <func>(<keyword_args>)                        # Например: `my_func(x=0, y=0)`.
<obj> = <func>(<pos_args>, <key_args>)                # Например: `my_func(0, y=0)`.
```


Splat
-----
**Оператор splat, т.е. `'*'`, распаковывает коллекцию в позиционные аргументы, а splatty-splat, т.е. `'**'`, распаковывает словарь в именованные (keyword) аргументы.**
```python
args, kwargs = (1, 2), {'z': 3}
func(*args, **kwargs)
```

#### Эквивалентно:
```python
func(1, 2, z=3)
```

### Inside Function Def
**Оператор `*` упаковывает ноль или более позиционных аргументов в кортеж, а `**` — именованные аргументы в словарь.**
```python
def add(*args):
    return sum(args)
```

```python
>>> add(1, 2, 3)
6
```

```text
+-------------------------+--------------+--------------+------------+
|                         | fn(x=1, y=2) |  fn(1, y=2)  |  fn(1, 2)  |
+-------------------------+--------------+--------------+------------+
| fn(x, *args, **kwargs): |     да       |     да       |    да      |
| fn(*args, y, **kwargs): |     да       |     да       |            |
| fn(*, x, **kwargs):     |     да       |              |            |
+-------------------------+--------------+--------------+------------+
```

### Collection Unpacking
```python
head, *body, tail = <collection>    # head или tail можно опустить.
```

### Inside Coll Literals
```python
<list>  = [*<coll> [, ...]]         # То же, что и `list(<coll>) [+ ...]`.
<tuple> = (*<coll>, [...])          # То же, что и `tuple(<coll>) [+ ...]`.
<set>   = {*<coll> [, ...]}         # То же, что и `set(<coll>) [| ...]`.
<dict>  = {**<dict> [, ...]}        # Последний словарь имеет приоритет. Также `|`.
```


Inline
------
### Lambda
```python
<func> = lambda: <return_val>                     # Однострочная анонимная функция.
<func> = lambda <arg> [, ...]: <return_val>       # Также допускает аргументы по умолчанию.
```

### Comprehensions
```python
<list> = [i+1 for i in range(5)]                  # Возвращает `[1, 2, 3, 4, 5]`.
<iter> = (i for i in range(10) if i > 5)          # Возвращает `iter([6, 7, 8, 9])`.
<set>  = {i+5 for i in range(5)}                  # Возвращает `{5, 6, 7, 8, 9}`.
<dict> = {i: i**2 for i in range(1, 4)}           # Возвращает `{1: 1, 2: 4, 3: 9}`.
```

```python
>>> [l+r for l in 'abc' for r in '123']           # Вложенный цикл указывается справа.
['a1', 'a2', 'a3', ..., 'c3']
```

### Map, Filter, Reduce
```python
from functools import reduce
```

```python
<iter> = map(lambda x: x + 1, range(5))           # Возвращает `iter([1, 2, 3, 4, 5])`.
<iter> = filter(lambda x: x > 5, range(10))       # Возвращает `iter([6, 7, 8, 9])`.
<obj>  = reduce(lambda out, x: out+x, range(5))   # Возвращает 10. Принимает 'initial'.
```

### Any, All
```python
<bool> = any(<collection>)                        # Истинен ли bool(<el>) хотя бы для одного элемента?
<bool> = all(<collection>)                        # Истинен ли для всех элементов (или если пусто)?
```

### Conditional Exp
```python
<obj> = <exp> if <condition> else <exp>           # Вычисляет только одно из выражений.
```

```python
>>> [i if i else 'zero' for i in (0, 1, 2)]       # `any(['', [], None])` возвращает False.
['zero', 1, 2]
```

### And, Or
```python
<obj> = <exp> and <exp> [and ...]                 # Возвращает первый ложный или последний объект.
<obj> = <exp> or <exp> [or ...]                   # Возвращает первый истинный или последний объект.
```

### Walrus Operator
```python
>>> [i for ch in '0123' if (i := int(ch))]        # Присваивает значение переменной прямо в выражении.
[1, 2, 3]
```

### Named Tuple, Enum, Dataclass
```python
from collections import namedtuple
Point = namedtuple('Point', 'x y')                # Создаёт подкласс кортежа.
point = Point(0, 0)                               # Возвращает экземпляр.

from enum import Enum
Direction = Enum('Direction', 'N E S W')          # Создаёт перечисление.
direction = Direction.N                           # Возвращает его элемент.

from dataclasses import make_dataclass
Player = make_dataclass('Player', ['p', 'd'])     # Создаёт обычный класс.
player = Player(point, direction)                 # Возвращает его экземпляр.
```


Import
------
**Механизм, делающий код из одного файла доступным в другом файле.**

```python
import <module>                      # Импортирует встроенный модуль или `<module>.py`.
import <package>                     # Встроенный пакет или `<package>/__init__.py`.
import <package>.<module>            # Модуль пакета или `<package>/<module>.py`.
from <pkg/mod>[.…] import <obj>      # Импортирует модуль, класс, функцию или переменную.
```
* **Пакет — это набор модулей, но он также может определять собственные функции, переменные и т.д. В файловой системе это папка со скриптами Python и опциональным файлом `__init__.py`.**
* **`'import <package>'` открывает доступ только к тем модулям, которые явно импортированы в `'__init__.py'`.**
* **Директория файла, переданного команде `python`, служит корнем для локальных импортов.**
* **Используйте относительные импорты `'from .[…][<pkg/mod>[.…]] import <obj>'`, если проект имеет разрозненные точки входа. Другой вариант — перенести код в папку `src`, добавить [`pyproject.toml`](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/#basic-information) в корень и выполнить `'$ pip3 install -e .'`.**


Closure
-------
**Замыкание (closure) в Python возникает, когда вложенная функция обращается к значениям внешней функции, и внешняя функция возвращает эту вложенную функцию (любое значение, используемое в нескольких вложенных функциях, становится общим).**

```python
def get_multiplier(a):
    def out(b):
        return a * b
    return out
```

```python
>>> mul_by_3 = get_multiplier(3)
>>> mul_by_3(10)
30
```

### Partial
**Partial трансформирует функцию, фиксируя часть (или все) её аргументов. Это полезно, когда функцию нужно передать в качестве аргумента, например `'collections.defaultdict(<func>)'`, `'iter(<func>, to_exc)'` и `'dataclasses.field(default_factory=<func>)'`.**

```python
def mul(a, b):
    return a * b
```

```python
>>> import functools as ft
>>> mul_by_3 = ft.partial(mul, 3)
>>> mul_by_3(10)
30
```

### Non-Local
**Если переменной присваивается значение внутри тела функции, она считается локальной переменной, если только не объявлена как `'global'` или `'nonlocal'` перед первым использованием.**

```python
def get_counter():
    i = 0
    def out():
        nonlocal i
        i += 1
        return i
    return out
```

```python
>>> counter = get_counter()
>>> counter(), counter(), counter()
(1, 2, 3)
```


Decorator
---------
**Декоратор принимает функцию, расширяет её поведение и возвращает результат. Им может быть любой вызываемый объект ([callable](#callable)), но обычно это функция, возвращающая [замыкание](#closure).**

```python
@decorator_name
def func_that_is_passed_to_dec():
    ...
```

### Debugger
**Печатает имя функции при каждом её вызове. Использует декоратор `'@wraps'` для переноса метаданных из func() в out(). Без него `'add.__name__'` вернуло бы `'out'`.**

```python
from functools import wraps

def debug(func):
    @wraps(func)
    def out(*args, **kwargs):
        print(func.__name__)
        return func(*args, **kwargs)
    return out

@debug
def add(x, y):
    return x + y
```

### Cache
**Кэширует результаты выполнения функции для повторного использования. Для очистки вызовите `'<func>.cache_clear()'`, либо используйте `'@lru_cache(maxsize=<int>)'`.**

```python
from functools import cache

@cache
def fibonacci(n):
    return n if n < 2 else fibonacci(n-2) + fibonacci(n-1)
```
* **Интерпретатор CPython по умолчанию ограничивает глубину рекурсии числом 3000.**
* **Чтобы увеличить этот лимит, выполните `'sys.setrecursionlimit(<int>)'`.**

### Debug with Args
**Декоратор, который выводит имя функции и опционально её результат.**
```python
from functools import wraps

def debug(print_result=False):
    def decorator(func):
        @wraps(func)
        def out(*args, **kwargs):
            print(func.__name__)
            res = func(*args, **kwargs)
            if print_result:
                print(res)
            return res
        return out
    return decorator

@debug(print_result=True)
def add(x, y):
    return x + y
```
* **Использование `'@debug'` без аргументов здесь не сработает, так как add() передастся в аргумент 'print_result'. Чтобы исправить это, укажите `'def debug(fn=None, *, ...)'` и `'return decorator(fn) if fn else decorator'` в конце.**


Class
-----
**Шаблон для создания пользовательских объектов.**

```python
class MyClass:
    def __init__(self, a):
        self.a = a
    def __str__(self):
        return str(self.a)
    def __repr__(self):
        class_name = self.__class__.__name__
        return f'{class_name}({self.a!r})'

    @classmethod
    def get_class_name(cls):
        return cls.__name__
```

```python
>>> obj = MyClass(1)
>>> obj.a, str(obj), repr(obj)
(1, '1', 'MyClass(1)')
```
* **Методы, имена которых начинаются и заканчиваются двумя подчёркиваниями, называются специальными (магическими) методами (dunder methods).**
* **Они вызываются при передаче объекта во встроенные функции или при использовании операторов. Например, `'print(a)'` вызывает `'a.__str__()'`, а `'a + b'` вызывает `'a.__add__(b)'`.**
* **Имена всех специальных методов, вызываемых операторами, см. в модуле [operator](#operator).**
* **Методы с декоратором `'@staticmethod'` не получают ни 'self', ни 'cls'.**
* **Результат метода str() должен быть понятным человеку, а repr() — однозначным.<br>Все вызовы str() перенаправляются в repr(), если определён только repr().**

#### Выражения, вызывающие метод str():
```python
f'{obj}'
str(obj)
print(obj)
```

#### Выражения, вызывающие метод repr():
```python
f'{obj!r}'
str/repr/print([obj])
str/repr/print({obj: obj})
str/repr/print(MyDataClass(obj))
```

### Subclass
* **Наследование позволяет классу расширять другой класс (подклассу расширять родителя) и наследовать все его методы и атрибуты.**
* **Подкласс может добавлять собственные методы и атрибуты или переопределять унаследованные.**

```python
class Person:
    def __init__(self, name):
        self.name = name
    def __repr__(self):
        return f'Person({self.name!r})'
    def __lt__(self, other):
        return self.name < other.name

class Employee(Person):
    def __init__(self, name, staff_num):
        super().__init__(name)
        self.staff_num = staff_num
    def __repr__(self):
        return f'Employee({self.name!r}, {self.staff_num})'
```

```python
>>> people = [Person('Bob'), Employee('Ann', 0)]
>>> sorted(people)
[Employee('Ann', 0), Person('Bob')]
```

### Type Annotations
**Используются статическими анализаторами типов, такими как [mypy](https://pypi.org/project/mypy/) и библиотеками вроде [Pydantic](https://pypi.org/project/pydantic/), однако они не форсируются интерпретатором CPython в рантайме. Для аннотации функции: `'def f(a: int = 0) -> int: ...'`.**
```python
from collections.abc import *

<name>: <type> [| ...] [= <obj>]
<name>: list/set/Iterable/Sequence[<type>] [= <obj>]
<name>: tuple/dict[<type>, ...] [= <obj>]
```

### Dataclass
**Использует переменные класса для автоматической генерации специальных методов init(), repr() и eq().**
```python
import dataclasses as dc
```

```python
@dc.dataclass(order=False, frozen=False)
class MyClass:
    <attr_name>: <type>
    <attr_name>: <type> = <obj>
    <attr_name>: list = dc.field(default_factory=list)
```
* **Объекты можно сделать [сортируемыми](#sortable) с `'order=True'` и неизменяемыми с `'frozen=True'`.**
* **Чтобы объект был [хешируемым](#hashable), все его атрибуты должны быть хешируемыми, а `'frozen'` должен быть установлен в `'True'`.**
* **Функция field() необходима, так как `'<attr_name>: list = []'` создала бы единый список, разделяемый всеми экземплярами. Аргумент 'default_factory' принимает любой вызываемый объект ([callable](#callable)).**
* **Для атрибутов и аргументов произвольного типа используйте `'<attr_name>: typing.Any'`.**

#### В одну строку (Inline):
```python
P = dc.make_dataclass('P', ['x', 'y'])
P = dc.make_dataclass('P', [('x', float), ('y', float)])
P = dc.make_dataclass('P', [('x', float, 0), ('y', float, 0)])
```

### Property
**Идиоматичный (pythonic) способ реализации геттеров и сеттеров.**
```python
class Person:
    @property
    def name(self):
        return ' '.join(self._name)

    @name.setter
    def name(self, value):
        self._name = value.split()
```

```python
>>> person = Person()
>>> person.name = '\t Guido  van Rossum \n'
>>> person.name
'Guido van Rossum'
```

### Slots
**Механизм, ограничивающий атрибуты объекта строго заданным кортежем (экономит память и ускоряет доступ).**

```python
class Point:
    __slots__ = ('x', 'y')
```

### Copy
```python
from copy import copy, deepcopy
<object> = copy/deepcopy(<object>)
```


Duck Types
----------
**Утиный тип (duck type) — это неявный интерфейс, определяемый набором специальных методов. Любой объект, обладающий всеми предписанными методами, считается представителем этого утиного типа («если нечто выглядит как утка и крякает как утка, то это утка»).**

### Comparable
* **Если метод eq() не переопределён, он возвращает `'id(self) == id(other)'`, что эквивалентно `'self is other'`. Это значит, что все пользовательские объекты по умолчанию сравниваются как неравные (поскольку id() возвращает уникальный адрес объекта в памяти).**
* **Метод eq() вызывается только у левого операнда, если только он не вернёт NotImplemented — в таком случае опрашивается правый объект. Если оба вернули NotImplemented, результат равен False.**
* **Метод ne() (вызываемый оператором `'!='`) автоматически работает для любого объекта, у которого определён eq().**

```python
class MyComparable:
    def __init__(self, a):
        self.a = a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
```

### Hashable
* **Хешируемому объекту требуются методы hash() и eq(), при этом его хеш-значение никогда не должно меняться во времени.**
* **Хешируемые объекты, которые сравниваются как равные, обязаны иметь одинаковое хеш-значение, поэтому дефолтный hash(), возвращающий `'id(self)'`, не подходит. Вот почему Python автоматически делает класс нехешируемым, если реализован только метод eq().**

```python
class MyHashable:
    def __init__(self, a):
        self._a = a
    @property
    def a(self):
        return self._a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
    def __hash__(self):
        return hash(self.a)
```

### Sortable
* **С декоратором 'total_ordering' достаточно определить eq() и один из методов lt(), gt(), le() или ge() (операторы <, >, <=, >=), а остальные будут сгенерированы автоматически.**
* **Встроенные функции sorted() и min() требуют только метод lt(), а max() — только gt(). Однако рекомендуется определять их все во избежание неожиданного поведения в других контекстах.**
* **При сравнении двух списков, строк или датаклассов их элементы сравниваются поочерёдно, пока не встретится пара неравных значений. Если все элементы равны, более короткая последовательность считается меньшей.**
* **Для сортировки строк в правильном алфавитном порядке используйте `'key=locale.strxfrm'` в sorted() после вызова `'locale.setlocale(locale.LC_COLLATE, "ru_RU.UTF-8")'` (или `"en_US.UTF-8"`).**

```python
from functools import total_ordering

@total_ordering
class MySortable:
    def __init__(self, a):
        self.a = a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
    def __lt__(self, other):
        if isinstance(other, type(self)):
            return self.a < other.a
        return NotImplemented
```

### Iterator
* **Любой объект со специальными методами next() и iter() является итератором.**
* **Next() должен возвращать следующий элемент или вызывать исключение StopIteration.**
* **Iter() должен возвращать сам итератор без изменений, т.е. аргумент 'self'.**
* **Любой объект с методом iter() может использоваться в цикле for.**
```python
class Counter:
    def __init__(self):
        self.i = 0
    def __next__(self):
        self.i += 1
        return self.i
    def __iter__(self):
        return self
```

```python
>>> counter = Counter()
>>> next(counter), next(counter), next(counter)
(1, 2, 3)
```

#### В Python существует множество различных объектов-итераторов:
* **Итераторы последовательностей, возвращаемые функцией [iter()](#iterator), такие как 'list\_iterator'.**
* **Объекты, возвращаемые модулем [itertools](#iterator), такие как count, repeat и cycle.**
* **Генераторы, возвращаемые функциями-генераторами ([functions](#generator)) и генераторными выражениями ([expressions](#comprehensions)).**
* **Файловые объекты, возвращаемые функцией [open()](#open), курсоры [SQLite](#sqlite) и др.**

### Callable
* **Все функции и классы имеют специальный метод call(), выполняемый при их вызове.**
* **Используйте `'callable(<obj>)'` или `'isinstance(<obj>, collections.abc.Callable)'` для проверки вызываемости и `'inspect.signature(<obj>)'` для получения сигнатуры аргументов.**
* **Когда в данном тексте в качестве аргумента указано `'<function>'`, на самом деле подразумевается `'<callable>'`.**
```python
class Counter:
    def __init__(self):
        self.i = 0
    def __call__(self, step):
        self.i += step
        return self.i
```

```python
>>> counter = Counter()
>>> counter(1), counter(1), counter(1)
(1, 2, 3)
```

### Context Manager
* **Конструкция with работает только с объектами, имеющими специальные методы enter() и exit().**
* **Enter() захватывает ресурс и опционально возвращает объект (файл, сокет, блокировку и т.д.).**
* **Exit() освобождает ресурс (закрывает файл, снимает блокировку и т.д.).**
* **Любое исключение внутри блока with передаётся в метод exit(). Exit() может подавить исключение, вернув истинное значение (True).**
```python
class MyOpen:
    def __init__(self, filename):
        self.filename = filename
    def __enter__(self):
        self.file = open(self.filename)
        return self.file
    def __exit__(self, exc_type, exception, traceback):
        self.file.close()
```

```python
>>> with open('test.txt', 'w') as file:
...     file.write('Hello World!')
>>> with MyOpen('test.txt') as file:
...     print(file.read())
Hello World!
```


Iterable Duck Types
-------------------
### Iterable
* **Единственный обязательный метод — iter(). Он должен возвращать итератор по элементам объекта.**
* **Специальный метод contains() автоматически работает для любого объекта с определённым iter().**
```python
class MyIterable:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
```

```python
>>> obj = MyIterable([1, 2, 3])
>>> [el for el in obj]
[1, 2, 3]
>>> 1 in obj
True
```

### Collection
* **Обязательные методы: iter() и len(). Len() возвращает длину коллекции.**
* **В данном тексте все итерируемые объекты называются «коллекциями», что терминологически упрощено. Термин _iterable_ звучит более абстрактно, чем _collection_. Единственный нюанс: читатель может подумать, что функция не принимает итераторы, хотя на самом деле итераторы — единственные встроенные объекты, которые являются итерируемыми (iterable), но не являются коллекциями (collection).**
```python
class MyCollection:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
    def __len__(self):
        return len(self.a)
```

### Sequence
* **Обязательные методы: len() и getitem(). Getitem() должен возвращать элемент по переданному индексу или вызывать IndexError (может также поддерживать отрицательные индексы и срезы).**
* **Iter() и contains() автоматически работают на любом объекте с определённым методом getitem().**
* **Reversed() автоматически работает на объектах с len() и getitem(). Возвращает обратный итератор.**
```python
class MySequence:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
    def __len__(self):
        return len(self.a)
    def __getitem__(self, i):
        return self.a[i]
    def __reversed__(self):
        return reversed(self.a)
```

#### Различия между глоссарием Python и абстрактными базовыми классами (ABC):
* **В [глоссарии](https://docs.python.org/3/glossary.html) Python итерируемый объект (iterable) определяется как любой объект с методами iter() или getitem(), а последовательность (sequence) — как любой объект с getitem() и len(). Термин _collection_ в глоссарии не определяется.**
* **Проверка через [ABC](#abstract-base-classes) `isinstance(..., Iterable)` проверяет наличие только iter(), а ABC Collection требует наличия iter(), contains() и len().**

### ABC Sequence
* **Более богатый интерфейс, чем базовая последовательность (которой нужны только len и getitem).**
* **Наследование от него автоматически генерирует методы iter(), contains(), reversed(), index() и count().**
* **В отличие от `'abc.Iterable'` и `'abc.Collection'`, он не является утиным типом (duck type). Выражение `'issubclass(MySequence, abc.Sequence)'` вернёт False, даже если у MySequence реализованы все методы, пока класс явно не унаследован. Однако он распознаёт list, tuple, range, str, bytes, bytearray, array, memoryview и deque как свои виртуальные подклассы.**
```python
from collections import abc

class MyAbcSequence(abc.Sequence):
    def __init__(self, a):
        self.a = a
    def __len__(self):
        return len(self.a)
    def __getitem__(self, i):
        return self.a[i]
```

#### Обязательные (REQ) и автоматически доступные (Yes) методы:
```text
+--------------+------------+------------+------------+--------------+
|              |  Iterable  | Collection |  Sequence  | abc.Sequence |
+--------------+------------+------------+------------+--------------+
| __iter__     |    REQ     |    REQ     |    Yes     |     Yes      |
| __contains__ |    Yes     |    Yes     |    Yes     |     Yes      |
| __len__      |            |    REQ     |    REQ     |     REQ      |
| __getitem__  |            |            |    REQ     |     REQ      |
| __reversed__ |            |            |    Yes     |     Yes      |
| index        |            |            |            |     Yes      |
| count        |            |            |            |     Yes      |
+--------------+------------+------------+------------+--------------+
```
* **Метод iter() обязателен, чтобы `'isinstance(<obj>, abc.Iterable)'` вернул True, однако любой объект с методом getitem() работает в любом месте, ожидающем iterable.**
* **Классы MutableSequence, Set, MutableSet, Mapping и MutableMapping также расширяемы. Используйте `'<abc>.__abstractmethods__'` для получения списка необходимых методов.**


Enum
----
**Класс именованных констант (элементов перечисления).**

```python
from enum import Enum, auto
```

```python
class MyEnum(Enum):
    <member_name> = auto()             # Инкремент последнего числового значения или 1.
    <member_name> = <value>            # Значения не обязаны быть уникальными/хешируемыми.
    <member_name> = <el>, <el>, ...    # Значение может быть коллекцией, например кортежем.
```
* **Методы получают элемент, у которого они были вызваны, в качестве аргумента 'self'.**
* **Попытка объявить элемент с именем зарезервированного ключевого слова вызовет SyntaxError.**

```python
<memb> = <enum>.<member_name>          # Доступ к элементу через атрибут перечисления.
<memb> = <enum>['<member_name>']       # Возвращает элемент или вызывает KeyError.
<memb> = <enum>(<value>)               # Возвращает элемент или вызывает ValueError.
<str>  = <member>.name                 # Возвращает имя элемента в виде строки.
<obj>  = <member>.value                # Значение не может быть пользовательской функцией.
```

```python
<list> = list(<enum>)                  # Возвращает список всех элементов перечисления.
<list> = <enum>._member_names_         # Возвращает список имён элементов.
<list> = [m.value for m in <enum>]     # Возвращает список значений элементов.
```

```python
<enum> = type(<member>)                # Возвращает тип enum. Также <memb>.__class__.
<iter> = itertools.cycle(<enum>)       # Бесконечный итератор по элементам перечисления.
<memb> = random.choice(list(<enum>))   # Случайный выбор одного из элементов enum.
```

### Inline
```python
Cutlery = Enum('Cutlery', 'FORK KNIFE SPOON')
Cutlery = Enum('Cutlery', ['FORK', 'KNIFE', 'SPOON'])
Cutlery = Enum('Cutlery', {'FORK': 1, 'KNIFE': 2, 'SPOON': 3})
```

#### Пользовательские функции не могут быть значениями напрямую, их нужно обернуть:
```python
import functools as ft
and_ = ft.partial(lambda l, r: l and r)
or_ = ft.partial(lambda l, r: l or r)
LogicOp = Enum('LogicOp', {'AND': and_, 'OR': or_})
```


Exceptions
----------
```python
try:
    <code>
except <exception>:
    <code>
```

### Full Try Statement
```python
try:
    <code_1>
except <exception_a>:
    <code_2_a>
except <exception_b>:
    <code_2_b>
else:
    <code_2_c>
finally:
    <code_3>
```
* **Код в блоке `'else'` выполняется только в том случае, если в блоке `'try'` не возникло исключений.**
* **Код в блоке `'finally'` выполняется всегда (за исключением аварийного прерывания сигналами).**
* **Все переменные, инициализированные в выполненных блоках, видны в последующих блоках и вне инструкции try (только функции и классы изолируют локальную область видимости).**
* **Для перехвата сигналов ОС используйте `'signal.signal(signal_number, my_handler_function)'`.**

### Catching Exceptions
```python
except <exception>: ...
except <exception> as <name>: ...
except (<exception>, ...) [as <name>]: ...
```
* **Блок except перехватывает все подклассы: например, `'OSError'` перехватывается через `'except Exception:'`.**
* **Используйте `'traceback.print_exc()'` для вывода полного стектрейса ошибки в поток stderr.**
* **Используйте `'print(<name>)'` для вывода сообщения об ошибке (её аргументов) в stdout.**
* **Используйте `'logging.exception(<str>)'` для логирования сообщения вместе со стектрейсом. Подробнее о настройке см. раздел [Logging](#logging).**
* **`'sys.exc_info()'` возвращает тип, объект и traceback перехваченного исключения в виде кортежа.**

### Raising Exceptions
```python
raise <exception>
raise <exception>()
raise <exception>(<obj> [, ...])
```

#### Повторный выброс перехваченного исключения (Re-raising):
```python
except <exception> [as <name>]:
    ...
    raise
```

### Exception Object
```python
arguments = <name>.args
exc_type  = <name>.__class__
filename  = <name>.__traceback__.tb_frame.f_code.co_filename
func_name = <name>.__traceback__.tb_frame.f_code.co_name
line_str  = linecache.getline(filename, <name>.__traceback__.tb_lineno)
trace_str = ''.join(traceback.format_tb(<name>.__traceback__))
error_msg = ''.join(traceback.format_exception(*sys.exc_info()))
```

### Built-in Exceptions
```text
BaseException
 +- SystemExit                  # Вызывается при вызове `sys.exit()`. См. раздел #Exit.
 +- KeyboardInterrupt           # Вызывается при нажатии клавиш прерывания (Ctrl+C).
 +- Exception                   # Базовый класс для всех пользовательских исключений.
      +- ArithmeticError        # Базовый класс для арифметических ошибок (ZeroDivisionError и др.).
      +- AssertionError         # Вызывается инструкцией `assert <exp>`, если выражение ложно.
      +- AttributeError         # Вызывается, если у объекта нет запрошенного атрибута или метода.
      +- EOFError               # Вызывается `input()`, если достигнут конец файла (EOF).
      +- LookupError            # Базовый класс для ошибок поиска элементов в коллекциях.
      |   +- IndexError         # Индекс последовательности (list/str) вышел за границы.
      |   +- KeyError           # Ключ словаря или элемент множества не найден.
      +- MemoryError            # Нехватка оперативной памяти (OOM).
      +- NameError              # Использовано несуществующее имя (переменная, функция, класс).
      |   +- UnboundLocalError  # Локальная переменная использована до её инициализации.
      +- OSError                # Системные ошибки (FileExistsError, TimeoutError). См. #Open.
      |   +- ConnectionError    # Ошибки сети/соединения (BrokenPipeError, ConnectionAbortedError).
      +- RuntimeError           # Ошибки времени выполнения, не подходящие под другие категории.
      |   +- NotImplementedEr…  # Вызывается в абстрактных методах или незавершённом коде.
      |   +- RecursionError     # Превышена максимальная глубина рекурсии (3000 по умолчанию).
      +- StopIteration          # Сигнализирует об окончании элементов итератора в next().
      +- TypeError              # Функция получила аргумент неподходящего типа.
      +- ValueError             # Аргумент верного типа, но содержит некорректное значение.
```

#### Исключения, вызываемые коллекциями:
```text
+-----------+------------+------------+------------+
|           |   <list>   |   <set>    |   <dict>   |
+-----------+------------+------------+------------+
| [i/key]   | IndexError |            |  KeyError  |
| .pop()    | IndexError |  KeyError  |  KeyError  |
| .remove() | ValueError |  KeyError  |            |
| .index()  | ValueError |            |            |
+-----------+------------+------------+------------+
```

#### Полезные встроенные исключения:
```python
raise TypeError('Function received argument of the wrong type!')
raise ValueError('Argument has right type but its value is off!')
raise RuntimeError('I am too lazy to define my own exception!')
```

### User-defined Exceptions
```python
class MyError(Exception): pass
class MyInputError(MyError): pass
```


Exit
----
**Завершает работу интерпретатора, вызывая исключение SystemExit.**
```python
import sys
sys.exit()                     # Завершает процесс с кодом возврата 0 (успех).
sys.exit(<int>)                # Завершает с переданным числовым кодом возврата.
sys.exit(<obj>)                # Выводит объект в stderr и завершает с кодом 1.
```


Print
-----
```python
print(<obj>, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```
* **Используйте `'file=sys.stderr'` или `'sys.stderr.write(<str>)'` для сообщений об ошибках.**
* **Потоки stdout и stderr буферизуют вывод до тех пор, пока не встретится символ `'\n'` или `'\r'`, буфер не достигнет 4096 символов, не будет передан `'flush=True'`, или программа не завершится.**

### Pretty Print
```python
from pprint import pprint
pprint(<collection>, width=80, depth=None, compact=False)
```
* **Каждый элемент выводится на отдельной строке, если длина коллекции превышает 'width' символов.**
* **Вложенные коллекции глубже `'depth=<int>'` отображаются как `'...'`.**


Input
-----
```python
<str> = input()
```
* **Считывает строку из пользовательского ввода или пайпа (завершающий символ перевода строки отсекается).**
* **Если передан строковый аргумент-подсказка, он выводится в stdout перед чтением ввода.**
* **Вызывает EOFError, если пользователь передал сигнал EOF (`Ctrl+D` в Linux/macOS, `Ctrl+Z`+`Enter` в Windows) или поток исчерпан.**


Arguments
---------
```python
import sys
scripts_path = sys.argv[0]
arguments    = sys.argv[1:]
```

### Argument Parser
```python
from argparse import ArgumentParser
p = ArgumentParser(description=<str>)                      # Также принимает строку 'usage'.
p.add_argument('-<chr>', '--<name>', action='store_true')  # Флаг-переключатель (по умолчанию False).
p.add_argument('-<chr>', '--<name>', type=<type>)          # Опция со значением (по умолчанию None).
p.add_argument('<name>', type=<type>, nargs=1)             # Обязательный первый позиционный аргумент.
p.add_argument('<name>', type=<type>, nargs='+')           # Обязательные остальные аргументы (1+).
p.add_argument('<name>', type=<type>, nargs='?')           # Необязательный аргумент (0 или 1). Также *.
args  = p.parse_args()                                     # Завершает процесс при ошибке парсинга.
<obj> = args.<name>                                        # Возвращает `<type>(<arg>)`.
```
* **Используйте `'help=<str>'` для описания аргумента в справке, вызываемой по `'-h'`.**
* **Используйте `'default=<obj>'` для установки значения по умолчанию.**


Open
----
**Открывает файл и возвращает соответствующий файловый объект.**

```python
<file> = open(<path>, mode='r', encoding=None, newline=None)
```
* **`'encoding=None'` означает платформозависимую системную кодировку. Рекомендуется всегда явно указывать `'encoding="utf-8"'`.**
* **`'newline=None'` преобразует любые окончания строк в `'\n'` при чтении, а при записи заменяет `'\n'` на системный разделитель ОС.**
* **`'newline=""'` отключает автоконвертацию, но разбивает строки по `'\n'`, `'\r'` и `'\r\n'`.**
* **`'newline="\r\n"'` разбивает ввод только по `'\r\n'` и преобразует все `'\n'` в `'\r\n'` при записи.**

### Modes
* **`'r'`  - Чтение текста из файла (по умолчанию).**
* **`'w'`  - Запись текста. Перезаписывает существующий файл.**
* **`'x'`  - Создание. Вызывает FileExistsError, если файл уже существует.**
* **`'a'`  - Дозапись в конец. Создаёт файл, если он не существует.**
* **`'w+'` - Чтение и запись с предварительной очисткой содержимого.**
* **`'r+'` - Чтение и запись с начала файла без удаления содержимого.**
* **`'a+'` - Чтение и дозапись в конец файла.**
* **`'rb'` - Чтение в виде [байтов](#bytes). Также `'wb'`, `'xb'` и т.д.**

### Exceptions
* **`'FileNotFoundError'` может возникнуть при открытии на чтение с `'r'` или `'r+'`.**
* **`'FileExistsError'` возникает при попытке записи в режиме `'x'`.**
* **`'IsADirectoryError'`, `'PermissionError'` могут возникнуть в любых режимах.**
* **Конструкция `'except OSError [as <name>]: …'` перехватывает все перечисленные исключения.**

### File Object
```python
<file>.seek(0)                    # Перемещает указатель в самое начало файла.
<file>.seek(offset)               # Смещает на 'offset' символов/байтов от начала.
<file>.seek(0, 2)                 # Перемещает текущую позицию в конец файла.
<b_file>.seek(±offset, origin)    # origin: 0 — начало, 1 — текущая позиция, 2 — конец.
```

```python
<obj>  = <file>.read(size=-1)     # Читает 'size' символов/байтов или всё до конца (EOF).
<obj>  = <file>.readline()        # Возвращает одну строку или пустую строку/байты на EOF.
<list> = <file>.readlines()       # Возвращает оставшиеся строки списком. Также list(<file>).
<obj>  = next(<file>)             # Возвращает строку с упреждающим чтением из буфера.
```

```python
<file>.write(<obj>)               # Записывает str или bytes в буфер записи.
<file>.writelines(<coll>)         # Записывает коллекцию строк или байтовых объектов.
<file>.flush()                    # Сбрасывает буфер записи на диск (каждые 4096/8192 байт).
<file>.close()                    # Закрывает файл со сбросом буфера.
```
* **Методы не добавляют и не удаляют завершающие переносы строк (включая writelines()).**

### Read Text from File
```python
def read_file(filename):
    with open(filename, encoding='utf-8') as file:
        return file.readlines()
```

### Write Text to File
```python
def write_to_file(filename, text):
    with open(filename, 'w', encoding='utf-8') as file:
        file.write(text)
```


Paths
-----
```python
import os, glob
from pathlib import Path
```

```python
<str>  = os.getcwd()                # Возвращает текущую рабочую директорию (CWD).
<str>  = os.path.join(<path>, ...)  # Объединяет пути с разделителем `os.sep`.
<str>  = os.path.realpath(<path>)   # Разрешает симлинки и вызывает `os.path.abspath()`.
```

```python
<str>  = os.path.basename(<path>)   # Возвращает имя файла или папки (последний компонент пути).
<str>  = os.path.dirname(<path>)    # Возвращает путь без его последнего компонента.
<tup.> = os.path.splitext(<path>)   # Отделяет расширение файла (по последней точке).
```

```python
<list> = os.listdir(path='.')       # Возвращает список имён файлов и папок в директории 'path'.
<list> = glob.glob('<pattern>')     # Находит пути, соответствующие шаблону поиска (wildcard).
```

```python
<bool> = os.path.exists(<path>)     # Проверяет существование пути. Также `<Path>.exists()`.
<bool> = os.path.isfile(<path>)     # Проверяет, является ли путь файлом. Также `<Path>.is_file()`.
<bool> = os.path.isdir(<path>)      # Проверяет, является ли путь папкой. Также `<Path>.is_dir()`.
```

```python
<stat> = os.stat(<path>)            # Объект метаданных. Также `<Path/DirEntry>.stat()`.
<num>  = <stat>.st_size/st_mtime/…  # Размер в байтах, время изменения и т.д.
```

### DirEntry
**В отличие от listdir(), функция scandir() возвращает объекты DirEntry, которые кэшируют вызовы isfile, isdir и (на Windows) stat, существенно ускоряя работу файловых операций.**

```python
<iter> = os.scandir(path='.')       # Возвращает итератор объектов DirEntry в директории.
<str>  = <DirEntry>.path            # Абсолютный путь, если аргумент 'path' был абсолютным.
<str>  = <DirEntry>.name            # Возвращает имя файла/папки в виде строки.
<file> = open(<DirEntry>)           # Открывает файл и возвращает файловый объект.
```

### Path Object
```python
<Path> = Path(<path> [, ...])       # Принимает строки, объекты Path и DirEntry.
<Path> = <path> / <path> [/ ...]    # Первый или второй аргумент должен быть Path.
<Path> = <Path>.resolve()           # Возвращает абсолютный путь с разрешением симлинков.
```

```python
<Path> = Path()                     # Текущая рабочая директория. Также `Path('.')`.
<Path> = Path.cwd()                 # Абсолютный CWD. Также `Path().resolve()`.
<Path> = Path.home()                # Абсолютный путь к домашней директории пользователя.
<Path> = Path(__file__)             # Используйте resolve() для абсолютного пути модуля.
```

```python
<Path> = <Path>.parent              # Возвращает путь без последнего компонента.
<str>  = <Path>.name                # Имя файла или папки.
<str>  = <Path>.suffix              # Расширение файла с точкой (например: .py).
<str>  = <Path>.stem                # Имя файла без расширения.
<tup.> = <Path>.parts               # Кортеж частей пути (начинается с '/' или 'C:\').
```

```python
<iter> = <Path>.iterdir()           # Возвращает содержимое папки в виде объектов Path.
<iter> = <Path>.glob('<patt>')      # Возвращает объекты Path, совпадающие с шаблоном.
```

```python
<str>  = str(<Path>)                # Возвращает путь в виде строки. Также `<Path>.as_uri()`.
<file> = open(<Path>)               # Также `<Path>.read_text/write_bytes/…(<args>)`.
```


OS Commands
-----------
```python
import os, shutil as sh
```

```python
os.chdir(<path>)               # Сменяет текущую рабочую директорию (CWD).
os.mkdir(<path>)               # Создаёт папку. Права доступа: `mode=0o777`.
os.makedirs(<path>)            # Создаёт всю цепочку папок пути. Также `exist_ok=False`.
```

```python
sh.copy(from, to)              # Копирует файл (аргумент 'to' может быть файлом или папкой).
sh.copy2(from, to)             # Копирует файл с сохранением времени создания и изменения.
sh.copytree(from, to)          # Рекурсивно копирует папку (аргумент 'to' не должен существовать).
```

```python
os.rename(from, to)            # Переименовывает или перемещает файл/папку 'from'.
os.replace(from, to)           # То же самое, но перезаписывает 'to' даже в Windows.
sh.move(from, to)              # `rename()`, перемещающий внутрь 'to', если 'to' — папка.
```

```python
os.remove(<path>)              # Удаляет файл. В корзину: `$ pip3 install send2trash`.
os.rmdir(<path>)               # Удаляет пустую папку. Вызывает OSError, если она не пуста.
sh.rmtree(<path>)              # Рекурсивно удаляет папку со всем её содержимым.
```
* **В качестве путей можно передавать строки, объекты Path или объекты DirEntry.**
* **Функции сообщают об ошибках через исключение OSError или его [подклассы](#exceptions-1).**


Shell Commands
--------------
```python
import os, subprocess as sp
```

```python
<int>  = os.system('<cmds>')    # Запускает команду в sh/cmd. Выводит результат в консоль.
<proc> = sp.run(<str/list>)     # Запуск подпроцесса. Параметры см. ниже в примерах.
<pipe> = os.popen('<cmds>')     # Выводит только stderr. Устаревает, начиная с 3.14.
<str>  = <pipe>.read()          # Возвращает объединённый stdout. Есть readline/s().
<int>  = <pipe>.close()         # Возвращает None, если код возврата команды был 0.
```

#### Отправляет "1+1" в калькулятор bc и перехватывает потоки stdout и stderr:
```python
>>> sp.run('bc', input='1+1\n', capture_output=True, text=True)
CompletedProcess(args='bc', returncode=0, stdout='2\n', stderr='')
```

#### Отправляет test.in в \`bc\` в стандартном режиме и сохраняет stdout в test.out:
```python
>>> if os.system('echo 1+1 > test.in') == 0:
...     with open('test.in') as in_, open('test.out', 'w') as out:
...         sp.run(shlex.split('bc -s'), stdin=in_, stdout=out)
...     print(open('test.out').read())
2
```


JSON
----
```python
import json
<str>  = json.dumps(<list/dict>)  # Преобразует коллекцию Python в JSON-строку.
<coll> = json.loads(<str>)        # Преобразует JSON-строку в коллекцию Python.
```

### Read Collection from JSON File
```python
def read_json_file(filename):
    with open(filename, encoding='utf-8') as file:
        return json.load(file)
```

### Write Collection to JSON File
```python
def write_to_json_file(filename, coll):
    with open(filename, 'w', encoding='utf-8') as file:
        json.dump(coll, file, ensure_ascii=False, indent=2)
```


Pickle
------
```python
import pickle
<bytes>  = pickle.dumps(<object>)  # Сериализует объект Python в бинарный объект bytes.
<object> = pickle.loads(<bytes>)   # Десериализует объект bytes обратно в объект Python.
```

### Read Object from Pickle File
```python
def read_pickle_file(filename):
    with open(filename, 'rb') as file:
        return pickle.load(file)
```

### Write Object to Pickle File
```python
def write_to_pickle_file(filename, an_object):
    with open(filename, 'wb') as file:
        pickle.dump(an_object, file)
```


CSV
---
**Текстовый формат для хранения табличных данных.**

```python
import csv
```

```python
<file> = open(<path>, newline='')              # Открывает файл для чтения.
<read> = csv.reader(<file>, 'excel')           # Также `delimiter=','`. См. параметры.
<list> = next(<read>)                          # Возвращает строку как список строк.
<list> = list(<read>)                          # Возвращает список всех оставшихся строк.
```
* **Для XML и бинарных файлов Excel (.xlsx, .xlsm, .xlsb) используйте библиотеку [Pandas](#file-formats).**
* **Для красивого вывода таблиц в консоль используйте библиотеки [Tabulate](#table) или PrettyTable.**
* **Reader может читать любой итератор или коллекцию строк, не только файлы.**

### Write
```python
<file>  = open(<path>, 'a', newline='')        # Открывает файл для записи.
<write> = csv.writer(<file>, 'excel')          # Также `delimiter=','`. См. параметры.
<write>.writerow(<collection>)                 # Кодирует объекты через `str(<obj>)`.
<write>.writerows(<coll_of_coll>)              # Дописывает строки в открытый файл.
```
* **Всегда передавайте `'newline=""'` в функцию open(), иначе переносы строк внутри закавыченных полей будут некорректно дублироваться (`\r\r\n`).**
* **Открывайте существующий файл с `'mode="a"'` для добавления записей или `'mode="w"'` для перезаписи.**

### Params
* **`'dialect'` - Базовый диалект со стандартными настройками. Строка или объект csv.Dialect.**
* **`'delimiter'` - Символ-разделитель колонок. Запятая, табуляция, точка с запятой и т.д.**
* **`'lineterminator'` - Символ окончания строки при записи. Reader распознаёт `'\n'`, `'\r'` и `'\r\n'`.**
* **`'quotechar'` - Символ кавычек для экранирования полей.**
* **`'escapechar'` - Символ экранирования кавычек. Может быть None, если doublequote=True.**
* **`'doublequote'` - Удваивать ли кавычки внутри полей вместо экранирования.**
* **`'quoting'` - Режим кавычек: 0: по необходимости, 1: все, 2: все кроме чисел, 3: без кавычек.**
* **`'skipinitialspace'` - Игнорировать ли пробел сразу после разделителя.**

### Dialects
```text
+------------------+--------------+--------------+--------------+
|                  |     excel    |   excel-tab  |     unix     |
+------------------+--------------+--------------+--------------+
| delimiter        |       ','    |      '\t'    |       ','    |
| lineterminator   |    '\r\n'    |    '\r\n'    |      '\n'    |
| quotechar        |       '"'    |       '"'    |       '"'    |
| escapechar       |      None    |      None    |      None    |
| doublequote      |      True    |      True    |      True    |
| quoting          |         0    |         0    |         1    |
| skipinitialspace |     False    |     False    |     False    |
+------------------+--------------+--------------+--------------+
```

### Read Rows from CSV File
```python
def read_csv_file(filename, **csv_params):
    with open(filename, encoding='utf-8', newline='') as file:
        return list(csv.reader(file, **csv_params))
```

### Write Rows to CSV File
```python
def write_to_csv_file(filename, rows, mode='w', **csv_params):
    with open(filename, mode, encoding='utf-8', newline='') as file:
        writer = csv.writer(file, **csv_params)
        writer.writerows(rows)
```


SQLite
------
**Встраиваемый бессерверный движок реляционных баз данных, хранящий каждую БД в отдельном файле.**

```python
import sqlite3
<con> = sqlite3.connect(<path>)        # Открывает файл БД или создаёт новый. Также ':memory:'.
<con>.close()                          # Закрывает соединение. Сбрасывает незафиксированные данные.
```

### Read
```python
<cursor> = <con>.execute('SELECT …')   # Может вызвать исключение из иерархии `sqlite3.Error`.
<tuple>  = <cursor>.fetchone()         # Возвращает следующую строку. То же, что `next(<cursor>)`.
<list>   = <cursor>.fetchall()         # Возвращает оставшиеся строки списком. Также `list(<cursor>)`.
```

### Write
```python
<con>.execute('INSERT …')              # Может вызвать исключение из иерархии `sqlite3.Error`.
<con>.commit()                         # Фиксирует все изменения с момента прошлого коммита.
<con>.rollback()                       # Откатывает изменения с момента последнего коммита.
```

#### Или через контекстный менеджер:
```python
with <con>:                            # Выходит из блока с commit() или rollback()
    <con>.execute('INSERT …')          # в зависимости от наличия исключений.
```

### Params
```python
<con>.execute(<sql>, <list/tuple>)     # Подставляет элементы вместо знаков '?'.
<con>.execute(<sql>, <dict/namedtup>)  # Подставляет значения по ключам `:<key>`.
<con>.executemany(<sql>, <colls>)      # Выполняет SQL-запрос для каждого набора параметров.
```
* **Поддерживает типы str, int, float, bytes, None и bool (хранятся как 1 или 0).**
* **Колонки не привязаны к конкретному типу данных, если таблица не создана в режиме STRICT.**

### Example
**Изменения в этом примере не сохранятся на диске, так как пропущен `'con.commit()'`!**
```python
>>> con = sqlite3.connect('test.db')
>>> con.execute('CREATE TABLE person (name TEXT, height INTEGER) STRICT')
>>> con.execute('INSERT INTO person VALUES (?, ?)', ('Jean-Luc', 187))
>>> con.execute('SELECT rowid, * FROM person').fetchall()
[(1, 'Jean-Luc', 187)]
```

### SQLAlchemy
**Популярная библиотека для работы с реляционными СУБД через сырой SQL, [построитель запросов](https://docs.sqlalchemy.org/en/latest/tutorial/data_select.html#the-select-sql-expression-construct) или [ORM](https://docs.sqlalchemy.org/en/latest/orm/quickstart.html#simple-select).**
```python
# $ pip3 install sqlalchemy
import sqlalchemy as sa
<eng> = sa.create_engine(<url>)        # URL: 'dialect://user:password@host/dbname'.
<con> = <eng>.connect()                # Создаёт новое соединение. Также `<con>.close()`.
<cur> = <con>.execute(sa.text(<sql>))  # Передайте dict в execute() для подстановки `:<key>`.
with <con>.begin(): ...                # Завершает блок транзакции автоматическим commit или rollback.
```

```text
+-----------------+--------------+----------------------------------+
| Драйвер/СУБД    | pip3 install |           Зависимости            |
+-----------------+--------------+----------------------------------+
| mysql           | mysqlclient  | www.pypi.org/project/mysqlclient |
| postgresql      | psycopg2     | www.pypi.org/project/psycopg2    |
| mssql           | pyodbc       | www.pypi.org/project/pyodbc      |
| oracle+oracledb | oracledb     | www.pypi.org/project/oracledb    |
+-----------------+--------------+----------------------------------+
```


Bytes
-----
**Неизменяемая последовательность отдельных байтов. Изменяемая версия называется bytearray.**

```python
<bytes> = b'<str>'                   # Принимает символы ASCII и шестнадцатеричные `\x00`..\xff.
<int>   = <bytes>[index]             # Возвращает байт в виде целого числа от 0 до 255.
<bytes> = <bytes>[<slice>]           # Возвращает срез bytes (даже если он из одного байта).
<bytes> = <bytes>.join(<coll>)       # Склеивает объекты bytes через байт-разделитель.
```

### Encode
```python
<bytes> = bytes(<ints>)              # Принимает коллекцию целых чисел от 0 до 255.
<bytes> = bytes(<str>, 'utf-8')      # Кодирует строку. То же, что `<str>.encode()`.
<bytes> = bytes.fromhex('<hex>')     # Шестнадцатеричные пары могут разделяться пробелами.
<bytes> = <int>.to_bytes(n_bytes)    # Принимает `byteorder='little', signed=True`.
```

### Decode
```python
<list>  = list(<bytes>)              # Возвращает список целых чисел от 0 до 255.
<str>   = str(<bytes>, 'utf-8')      # Возвращает строку. То же, что `<bytes>.decode()`.
<str>   = <bytes>.hex()              # Возвращает hex-пары, разделяемые `sep=<str>`.
<int>   = int.from_bytes(<bytes>)    # Принимает `byteorder='little', signed=True`.
```

### Read Bytes from File
```python
def read_bytes(filename):
    with open(filename, 'rb') as file:
        return file.read()
```

### Write Bytes to File
```python
def write_bytes(filename, bytes_obj):
    with open(filename, 'wb') as file:
        file.write(bytes_obj)
```


Struct
------
* **Выполняет преобразование между последовательностями чисел и упакованными бинарными данными bytes.**
* **По умолчанию используются системные размеры типов, порядок байтов и выравнивание.**

```python
from struct import pack, unpack

<bytes> = pack('<format>', <num>, ...)  # Упаковывает числа согласно формату.
<tuple> = unpack('<format>', <bytes>)   # Используйте `iter_unpack()` для поточной распаковки.
```

```python
>>> pack('>hhl', 1, 2, 3)
b'\x00\x01\x00\x02\x00\x00\x00\x03'
>>> unpack('bhh', b'\x01\x00\x02\x00\x03\x00')
(1, 2, 3)
```

### Format
#### Для стандартных размеров типов и ручного выравнивания строка формата начинается с:
* **`'='` - Системный порядок байтов (обычно little-endian).**
* **`'<'` - Прямой порядок байтов (little-endian, младший байт первый).**
* **`'>'` - Обратный порядок байтов (big-endian, также `'!'`).**

#### Помимо чисел, pack() и unpack() поддерживают байтовые строки (bytes):
* **`'c'` - Байт из одного символа. Для байта выравнивания используется `'x'`.**
* **`'<n>s'` - Байт-строка из n символов (порядок байтов не влияет).**

#### Целые числа. Беззнаковые типы пишутся заглавными буквами. Размеры (мин/стандарт в байтах) указаны в скобках:
* **`'b'` - char (1/1)**
* **`'h'` - short (2/2)**
* **`'i'` - int (2/4)**
* **`'l'` - long (4/4)**
* **`'q'` - long long (8/8)**

#### Числа с плавающей точкой (struct всегда использует стандартные размеры IEEE):
* **`'f'` - float (4/4)**
* **`'d'` - double (8/8)**


Array
-----
**Список, который может содержать только числа выбранного C-типа (минимальный оверхед памяти). Доступные типы и их размеры перечислены выше. Порядок байтов зависит от платформы, но байты элементов можно инвертировать методом `byteswap()`.**

```python
from array import array
```

```python
<array> = array('<ctype>' [, <coll>])  # Создаёт массив. Принимает коллекцию чисел.
<array> = array('<ctype>', <bytes>)    # Копирует переданные байты напрямую в память массива.
<array> = array('<ctype>', <array>)    # Воспринимает переданный массив как последовательность чисел.
<array>.fromfile(<file>, n_items)      # Дописывает содержимое файла в память массива.
```

```python
<bytes> = bytes(<array>)               # Возвращает копию памяти массива в виде объекта bytes.
<file>.write(<array>)                  # Записывает память массива напрямую в бинарный файл.
```


Memory View
-----------
**Объект-последовательность, ссылающийся на буфер памяти другого байтоподобного объекта без копирования. Порядок и число элементов можно менять срезами.**

```python
<mview> = memoryview(<bytes/array>)  # Возвращает изменяемый memoryview, если передан array.
<obj>   = <mview>[index]             # Возвращает int/float. Объект bytes, если формат 'c'.
<mview> = <mview>[<slice>]           # Возвращает memoryview с переупорядоченными элементами.
<mview> = <mview>.cast('<ctype>')    # Работает только между B/b/c и остальными типами.
<mview>.release()                    # Освобождает буфер памяти базового объекта.
```

```python
<bytes> = bytes(<mview>)             # Создаёт новый объект bytes. Также `bytearray()`.
<bytes> = <bytes>.join(<coll>)       # Склеивает memoryviews через байт-разделитель.
<array> = array('<ctype>', <mview>)  # Считывает mview как последовательность чисел.
<file>.write(<mview>)                # Записывает `bytes(<mview>)` в бинарный файл.
```

```python
<list>  = list(<mview>)              # Возвращает список int, float или объектов bytes.
<str>   = str(<mview>, 'utf-8')      # Воспринимает переданный memoryview как `bytes(<mview>)`.
<str>   = <mview>.hex()              # Возвращает hex-пары с разделителем `sep=<str>`.
```


Deque
-----
**Двусторонняя очередь с эффективным добавлением и удалением элементов с обоих концов за O(1).**

```python
from collections import deque
```

```python
<deque> = deque(<coll>)           # Передайте `maxlen=<int>` для ограничения размера.
<deque>.appendleft(<el>)          # Вытесняет последний элемент, если превышен maxlen.
<deque>.extendleft(<coll>)        # Добавляет элементы коллекции слева в обратном порядке.
<deque>.rotate(n=1)               # Сдвигает циклически элементы вправо (n шагов).
<el> = <deque>.popleft()          # Удаляет и возвращает первый (левый) элемент.
```


Operator
--------
**Модуль функций, реализующих операторы Python. Функции сгруппированы по возрастанию приоритета связывания.**
```python
import operator as op
```

```python
<bool> = op.not_(<obj>)                                    # or, and, not (or/and функций нет).
<bool> = op.eq/ne/lt/ge/is_/is_not/contains(<obj>, <obj>)  # ==, !=, <, >=, is, is not, in.
<obj>  = op.or_/xor/and_(<int/set>, <int/set>)             # |, ^, & (отсортированы по приоритету).
<int>  = op.lshift/rshift(<int>, <int>)                    # <<, >> (битовые сдвиги).
<obj>  = op.add/sub(<obj>, <obj>)                          # +, - (например, 'a' + 'b' == 'ab').
<obj>  = op.mul/truediv/floordiv/mod(<obj>, <obj>)         # *, /, //, % (вычисляются слева направо).
<num>  = op.neg/invert(<num>)                              # -, ~ (унарный минус и побитовое НЕ).
<num>  = op.pow(<num>, <num>)                              # ** (pow() принимает 3 аргумента).
<func> = op.itemgetter/attrgetter/methodcaller(<obj>, …)   # [i/key], .attr_name, .name(…).
```

```python
elementwise_sum  = map(op.add, list_a, list_b)
sorted_by_second = sorted(<coll>, key=op.itemgetter(1))
sorted_by_both   = sorted(<coll>, key=op.itemgetter(1, 0))
```
* **Большинство операторов вызывают одноимённый специальный метод объекта, а логические операторы опираются на функцию bool().**
* **Операторы `'and/or'` нельзя представить обычной функцией из-за механизма ленивого вычисления (short-circuiting).**
* **Сравнения можно объединять в цепочки: выражение `'x < y < z'` преобразуется в `'(x < y) and (y < z)'`.**


Match Statement
---------------
**Выполняет первый блок с совпавшим шаблоном (сопоставление с образцом / pattern matching, Python 3.10+).**

```python
match <obj/expr>:
    case <pattern> [if <cond>]:
        <code>
    ...
```

### Patterns
```python
<val_patt> = 1/'a'/True/None/math.pi     # Сопоставляет литерал или значение атрибута.
<cls_patt> = <type>()                    # Сопоставляет любой объект указанного типа (или ABC).
<wildcard> = _                           # Сопоставляет любой объект (универсальный шаблон case _).
<capture>  = <name>                      # Сопоставляет любой объект и связывает его с переменной name.
<as_patt>  = <pattern> as <name>         # Связывает совпадение с именем name. Также `<type>(<name>)`.
<or_patt>  = <pattern> | ...             # Совпадает, если подошёл любой из указанных шаблонов.
<seq_patt> = [<pattern>, ...]            # Сопоставляет последовательность. Все элементы должны подойти.
<map_patt> = {<val_patt>: <patt>, ...}   # Сопоставляет словарь при наличии соответствующих ключей.
<cls_patt> = <type>(<name>=<patt>, ...)  # Сопоставляет объект с совпадающими значениями атрибутов.
```
* **Шаблон последовательности может быть записан как список или как кортеж (в скобках или без).**
* **Используйте `'*<name>'` и `'**<name>'` в шаблонах последовательностей и словарей для сбора оставшихся элементов.**
* **Приоритет операторов: `'|'` > `'as'` > `','`. Например, `'[1, 2]'` сопоставляется выражением `'case 1|2, 2|3 as y if y == 2:'`.**
* **Все имена, связанные в сработавшем блоке case, а также переменные внутри его тела, видны и после инструкции match (только функция изолирует область видимости).**

### Example
```python
>>> from pathlib import Path
>>> match Path('/home/bwk/documents/README.md'):
...     case Path(
...         parts=['/', 'home', user, *_, name]
...     ) as p if p.is_file() and 'readme' in name.lower():
...         print(f"{name} is {user}'s readme file.")
README.md is bwk's readme file.
```


Logging
-------
```python
import logging as log
```

```python
log.basicConfig(filename=<path>)                # Настраивает корневой логгер (см. Setup).
log.debug/info/warning/error/critical(<str>)    # Отправляет сообщение в корневой логгер.
<Logger> = log.getLogger(__name__)              # Возвращает логгер с именем текущего модуля.
<Logger>.<level>(<str>)                         # Отправляет сообщение на выбранном уровне.
<Logger>.exception(<str>)                       # Метод `error()`, прикрепляющий стектрейс исключения.
```

### Setup
```python
log.basicConfig(
  filename=None,                                # При None выводит сообщения в stderr.
  filemode='a',                                 # Режим 'w' перезаписывает файл при старте.
  format='%(levelname)s:%(name)s:%(message)s',  # Параметр '%(asctime)s' добавляет дату/время.
  level=log.WARNING,                            # Игнорирует сообщения с более низким приоритетом.
  handlers=[log.StreamHandler(sys.stderr)]      # При указании 'filename' использует FileHandler.
)
```

```python
<Formatr> = log.Formatter('<format>')           # Форматирует сообщения по строке шаблона.
<Handler> = log.FileHandler(<path>, mode='a')   # Дописывает в файл логов. Также `encoding=None`.
<Handler>.setFormatter(<Formatter>)             # По умолчанию выводит «сырые» сообщения.
<Handler>.setLevel(<str/int>)                   # По умолчанию логирует все сообщения.
<Logger>.addHandler(<Handler>)                  # У логгера может быть несколько обработчиков.
<Logger>.setLevel(<str/int>)                    # Фильтр сообщений, отправляемых в обработчики.
<Logger>.propagate = <bool>                     # При False отключает передачу логов родителям.
```
* **Родительский логгер указывается в имени дочернего через точку: `'<parent_name>.<name>'`.**
* **Логгер наследует уровень от родителя, если он не переопределён через setLevel().**
* **В строке формата доступны: pathname, filename, funcName, lineno, thread и process.**
* **RotatingFileHandler выполняет ротацию файлов по параметрам 'maxBytes' и 'backupCount'.**
* **Объект с методом `'filter(<LogRecord>)'` можно подключить через addFilter(). При False сообщение отбрасывается.**
* **Сообщения из внешних библиотек передаются в корневые обработчики. Уровень логгера библиотеки задаётся через `'log.getLogger("<library>").setLevel(<str>)'`.**

#### Пример логгера, пишущего сообщения в файл и передающего их корневому обработчику:
```python
>>> logger = log.getLogger('my_module')
>>> handler = log.FileHandler('test.log', encoding='utf-8')
>>> format_str = '%(asctime)s %(levelname)s:%(name)s:%(message)s'
>>> handler.setFormatter(log.Formatter(format_str))
>>> logger.addHandler(handler)
>>> logger.setLevel('DEBUG')
>>> log.basicConfig()
>>> stream_handler = log.root.handlers[0]
>>> stream_handler.setLevel('WARNING')
>>> logger.critical('Missing config file.')
CRITICAL:my_module:Missing config file.
>>> print(open('test.log').read())
2023-02-07 23:21:01,430 CRITICAL:my_module:Missing config file.
```


Introspection
-------------
```python
<list> = dir()                       # Локальные имена объектов (включая функции и классы).
<dict> = vars()                      # Словарь локальных имён и их объектов. То же, что locals().
<dict> = globals()                   # Глобальные имена и их объекты. Например, __builtin__.
```

```python
<list> = dir(<obj>)                  # Имена атрибутов и методов объекта.
<dict> = vars(<obj>)                 # Словарь изменяемых атрибутов или `<obj>.__dict__`.
<bool> = hasattr(<obj>, '<name>')    # Проверяет наличие атрибута с указанным именем.
value  = getattr(<obj>, '<name>')    # Возвращает атрибут или вызывает AttributeError.
setattr(<obj>, '<name>', value)      # Устанавливает атрибут (только для объектов с `__dict__`).
delattr(<obj>, '<name>')             # Удаляет из `__dict__`. Также `del <obj>.<name>`.
```


Threading
---------
**Потоки — это функции, выполняющиеся конкурентно в одном адресном пространстве. Совместное изменение объектов требует синхронизации. Команда `'$ uv init --python 3.15t'` устанавливает интерпретатор без GIL (free-threaded), способный параллельно запускать потоки на нескольких ядрах процессора.**

```python
import threading as th, queue as qu
import concurrent.futures as cf
```

### Thread
```python
<Thread> = th.Thread(target=<func>)     # Используйте `args=<coll>` для позиционных аргументов.
<Thread>.start()                        # Запускает поток в фоновом режиме. Также `is_alive()`.
<Thread>.join()                         # Блокирует выполнение до завершения работы потока.
```
* **Используйте `'kwargs=<dict>'` для передачи именованных аргументов потоку.**
* **Используйте `'daemon=True'`, иначе процесс не завершится, пока поток активен.**

### Lock
```python
<lock> = th.Lock/RLock()                # RLock может повторно захватываться тем же потоком.
<lock>.acquire()                        # Ожидает/блокирует поток, пока блокировка не освободится.
<lock>.release()                        # Освобождает блокировку для других потоков.
```

#### Или через контекстный менеджер:
```python
with <lock>:                            # Захватывает блокировку вызовом метода acquire().
    ...                                 # Автоматически вызывает release(), даже при ошибке.
```

### Sync Objects
```python
<Semaphr> = th.Semaphore(value=1)       # Блокировка со счётчиком для `value` потоков.
<Event>   = th.Event()                  # Метод `<Event>.wait()` блокирует поток до вызова set().
<Barrier> = th.Barrier(parties)         # Wait() блокирует поток, пока его не вызовут parties раз.
```

### Queue
```python
<Queue> = qu.Queue(maxsize=0)           # Потокобезопасная очередь FIFO (первым зашёл — первым вышел).
<Queue>.put(<obj>)                      # Блокирует выполнение, если очередь заполнена (maxsize).
<Queue>.put_nowait(<obj>)               # Вызывает исключение `qu.Full`, если очередь полна.
<obj> = <Queue>.get()                   # Блокирует выполнение, пока очередь пуста.
<obj> = <Queue>.get_nowait()            # Вызывает исключение `qu.Empty`, если очередь пуста.
```

### Thread Executor
```python
<Exec> = cf.ThreadPoolExecutor()        # Или через менеджер контекста `with ThreadPoolExecutor() as <name>:`.
<iter> = <Exec>.map(<fn>, <args>, …)    # Многопоточный жадный map(). Сохраняет исходный порядок элементов.
<Futr> = <Exec>.submit(<fn>, <arg>, …)  # Ставит задачу в очередь на исполнение. Возвращает объект Future.
<Exec>.shutdown()                       # Ожидает завершения всех поставленных задач.
```

```python
<iter> = cf.as_completed(<Futrs>)       # `next(<iter>)` возвращает следующий завершившийся Future.
<obj>  = <Future>.result()              # Вызывает TimeoutError при указании `timeout=<fl>`.
<bool> = <Future>.done()                # Возвращает True, если функция завершила выполнение.
<bool> = <Future>.cancel()              # Возвращает False, если функция уже начала выполняться.
```
* **Map() и as\_completed() также принимают аргумент 'timeout'. Он вызывает _futures.TimeoutError_.**
* **Исключения, возникшие внутри потока, пробрасываются при вызове next() или Future.result(). Метод Future.exception() возвращает объект исключения или None.**
* **ProcessPoolExecutor обеспечивает настоящий параллелизм процессов, но: аргументы должны быть [сериализуемы через pickle](#pickle), очереди передаются через initargs/initializer, а точка запуска должна быть защищена блоком `'if __name__ == "__main__": …'`.**


Asyncio
-------
* **Корутины во многом похожи на потоки, но в отличие от потоков, они отдают управление только явно при вызове других корутин и потребляют значительно меньше памяти.**
* **Определение корутины начинается со слова `'async def'`, а её вызов — со слова `'await'`.**
* **Функция `'asyncio.run(<coroutine>)'` создаёт цикл событий и запускает главную корутину.**

```python
import asyncio as ac
```

```python
<coro> = <async_function>(<args>)        # Создаёт объект корутины при вызове async-функции.
<obj>  = await <coroutine>               # Запускает корутину. Возвращает результат или None.
<task> = ac.create_task(<coroutine>)     # Ставит корутину в планировщик. Обязательно сохраняйте задачу.
<obj>  = await <task>                    # Возвращает результат. Также `<task>.cancel()`.
```

```python
<coro> = ac.gather(<coro/task>, ...)     # Конкурентно запускает корутины. Возвращает список результатов.
<iter> = ac.as_completed(<coros/tasks>)  # `await next(<iter>)` возвращает очередной готовый результат.
<coro> = ac.wait(<tasks>)                # Принимает параметр `return_when=ac.FIRST_COMPLETED`.
```

#### Пример консольной игры: управление звёздочкой, избегающей приближающихся чисел:
```python
import asyncio as ac, collections as co, curses, curses.textpad, enum, random

P = co.namedtuple('P', 'x y')            # Позиция (координаты x и y).
D = enum.Enum('D', 'n e s w')            # Направление (север, восток, юг, запад).
W, H = 15, 7                             # Ширина и высота игрового поля.

def main(screen):
    curses.curs_set(0)                   # Скрывает курсор терминала.
    screen.nodelay(True)                 # Делает вызов getch() неблокирующим.
    ac.run(main_coroutine(screen))       # Запуск асинхронного цикла событий.

async def main_coroutine(scr):
    moves = ac.Queue()
    state = {'*': P(0, 0)} | dict.fromkeys(range(10), P(W//2, H//2))
    ai = [random_controller(id_, moves) for id_ in range(10)]
    mvc = [controller(scr, moves), model(moves, state), view(state, scr)]
    tasks = [ac.create_task(coro) for coro in ai + mvc]
    await ac.wait(tasks, return_when=ac.FIRST_COMPLETED)

async def random_controller(id_, moves):
    while True:
        d = random.choice(list(D))
        moves.put_nowait((id_, d))
        await ac.sleep(random.triangular(0.01, 0.65))

async def controller(scr, moves):
    while True:
        key_mappings = {258: D.s, 259: D.n, 260: D.w, 261: D.e}
        if d := key_mappings.get(scr.getch()):
            moves.put_nowait(('*', d))
        await ac.sleep(0.005)

async def model(moves, state):
    while state['*'] not in (state[id_] for id_ in range(10)):
        id_, d = await moves.get()
        dx, dy = (d == D.e) - (d == D.w), (d == D.s) - (d == D.n)
        state[id_] = P((state[id_].x + dx) % W, (state[id_].y + dy) % H)

async def view(state, scr):
    x, y = curses.COLS//2 - W//2, curses.LINES//2 - H//2
    while True:
        scr.erase()
        curses.textpad.rectangle(scr, y-1, x-1, y+H, x+W)
        for id_, p in state.items():
            dx, dy = p.x - state['*'].x + W//2, p.y - state['*'].y + H//2
            scr.addstr(y + (dy % H), x + (dx % W), str(id_))
        scr.refresh()
        await ac.sleep(0.005)

if __name__ == '__main__':
    curses.wrapper(main)
```
<br>


Libraries
=========

Progress Bar
------------
```python
# $ pip3 install tqdm
>>> import tqdm, time
>>> for el in tqdm.tqdm([1, 2, 3], desc='Обработка'):
...     time.sleep(1)
Обработка: 100%|████████████████████| 3/3 [00:03<00:00,  1.00s/it]
```


Plot
----
```python
# $ pip3 install matplotlib
import matplotlib.pyplot as plt

plt.plot/bar/scatter(x_data, y_data, label=None)  # Также принимает `plt.plot(y_data)`.
plt.legend()                                      # Добавляет легенду с метками данных.
plt.title/xlabel/ylabel(<str>)                    # Добавляет заголовок или подписи осей.
plt.show()                                        # Отображает график. Также `plt.savefig(<path>)`.
plt.clf()                                         # Очищает текущую фигуру (график).
```


Table
-----
#### Выводит CSV-таблицу в консоль:
```python
# $ pip3 install tabulate
import csv, tabulate
with open('test.csv', encoding='utf-8', newline='') as file:
    rows = list(csv.reader(file))
print(tabulate.tabulate(rows, headers='firstrow'))
```


Console App
-----------
#### Консольный файловый менеджер:
```python
# $ pip3 install windows-curses
import curses, os
from curses import A_REVERSE, KEY_UP, KEY_DOWN, KEY_LEFT, KEY_RIGHT

def main(screen):
    ch, first, selected, paths = 0, 0, 0, os.listdir()
    while ch != ord('q'):
        height, width = screen.getmaxyx()
        screen.erase()
        for y, filename in enumerate(paths[first : first+height]):
            color = A_REVERSE if filename == paths[selected] else 0
            screen.addnstr(y, 0, filename, width-1, color)
        ch = screen.getch()
        selected -= (ch == KEY_UP) and (selected > 0)
        selected += (ch == KEY_DOWN) and (selected < len(paths)-1)
        first -= (first > selected)
        first += (first < selected-(height-1))
        if ch in [KEY_LEFT, KEY_RIGHT, ord('\n')]:
            new_dir = '..' if ch == KEY_LEFT else paths[selected]
            if os.path.isdir(new_dir):
                os.chdir(new_dir)
                first, selected, paths = 0, 0, os.listdir()

if __name__ == '__main__':
    curses.wrapper(main)
```


GUI App
-------
#### Настольное приложение для конвертации массы в фунты:

```python
# $ pip3 install FreeSimpleGUI
import FreeSimpleGUI as sg

field = sg.Input(default_text='100', enable_events=True, key='QUANTITY')
menu = sg.Drop(['g', 'kg', 't'], 'kg', readonly=True, enable_events=True, k='UNIT')
text = sg.Text('is 220.462 lbs.', key='RESULT')
win = sg.Window('GUI App', [[field, menu], [text], [sg.Button('Close')]])

while True:
    event, values = win.read()
    if event in [sg.WIN_CLOSED, 'Close']:
        break
    try:
        quantity = float(values['QUANTITY'])
    except ValueError:
        continue
    unit = values['UNIT']
    lbs = quantity * {'g': 0.001, 'kg': 1, 't': 1000}[unit] / 0.45359237
    win['RESULT'].update(value=f'is {lbs:g} lbs.')
win.close()
```


Scraping
--------
#### Парсинг ссылки и логотипа Python со страницы Wikipedia:
```python
# $ pip3 install requests beautifulsoup4
import requests, bs4, os

get = lambda url: requests.get(url, headers={'User-Agent': 'cpc-bot'})
response = get('https://en.wikipedia.org/wiki/Python_(programming_language)')
document = bs4.BeautifulSoup(response.text, 'html.parser')
table = document.find('table', class_='infobox vevent')
python_url = table.find('th', string='Website').next_sibling.a['href']
logo_url = table.find('img')['src']
filename = os.path.basename(logo_url)
with open(filename, 'wb') as file:
    file.write(get(f'https:{logo_url}').content)
print(f'URL: {python_url}, logo: file://{os.path.abspath(filename)}')
```

### Selenium
**Библиотека для скрапинга веб-сайтов с динамическим JS-контентом.**
```python
# $ pip3 install selenium
from selenium import webdriver
```

```python
<Drv> = webdriver.Chrome/Firefox/Safari()      # Открывает браузер. Также `<Driver>.quit()`.
<Drv>.implicitly_wait(seconds)                 # Таймаут неявного ожидания для find_element/s().
<Drv>.get('<url>')                             # Блокирует до срабатывания события загрузки страницы.
<str> = <Drv>.page_source                      # Возвращает текущий HTML-код веб-страницы.
<El>  = <Drv/El>.find_element('xpath', <str>)  # Принимает '//<tag>[@<attr_name>="<val>"]…'.
<str> = <El>.get_attribute('<name>')           # Возвращает значение атрибута или свойства элемента.
<El>.click/clear()                             # Клик/очистка. Также `<El>.text` и `<El>.send_keys(<str>)`.
```

#### XPath — доступен в консоли браузера через `'$x("<xpath>")'`:
```python
<xpath>   = //<element>[/ or // <element>]     # Например: …/child, …//descendant, …/../sibling.
<xpath>   = //<el>/following-sibling::<el>     # Поиск соседнего элемента снизу. Также parent::.
<element> = <tag><conditions><index>           # Тег принимает */a/…. Для индекса [1/2/…].
<condit.> = [<sub_con> [and/or <sub_con>]]     # Для отрицания условия используйте not(<sub_con>).
<sub_con> = @<attr>[="<val>"]                  # `text()=` и `.=` соответствуют полному тексту.
<sub_con> = contains(@<attr>, "<val>")         # Содержит ли атрибут подстроку <val>?
<sub_con> = <element>                          # Содержит ли дочерний элемент? (или // для потомка).
```


Web App
-------
**Flask — минималистичный веб-фреймворк со встроенным WSGI/HTTP сервером. Если вам нужно просто открыть локальный HTML-файл в браузере, используйте `'webbrowser.open(<path>)'`.**
```python
# $ pip3 install flask
import flask as fl
```

```python
app = fl.Flask(__name__)                   # Создаёт объект веб-приложения.
app.run(host=None, port=None, debug=None)  # Либо консольная команда `$ flask --app FILE run`.
```
* **Запускает приложение на `'http://localhost:5000'`. Используйте `'host="0.0.0.0"'` для доступа из локальной сети.**
* **Для production используйте [WSGI-сервер](https://en.wikipedia.org/wiki/Web_Server_Gateway_Interface), например [Waitress](https://flask.palletsprojects.com/en/latest/deploying/waitress/) или Gunicorn, и HTTP-сервер [Nginx](https://flask.palletsprojects.com/en/latest/deploying/nginx/).**
* **Режим отладки (debug=True) автоматически перезагружает приложение при сохранении изменений и показывает трассировку ошибок прямо в браузере.**

### Serving Files
```python
@app.route('/img/<path:filename>')
def serve_file(filename):
    return fl.send_from_directory('DIRNAME', filename)
```

### Serving HTML
```python
@app.route('/<sport>')
def serve_html(sport):
    return fl.render_template_string('<h1>{{t}}</h1>', t=sport)
```
* **`'fl.render_template(filename, <kwargs>)'` рендерит шаблон из папки `'templates'`.**
* **`'fl.abort(<int>)'` возвращает код HTTP-ошибки, а `'return fl.redirect(<url>)'` выполняет редирект.**
* **`'fl.request.args[<str>]'` получает параметры из строки запроса (query string после знака '?').**
* **`'fl.session[<str>] = <obj>'` сохраняет данные сессии, а `'fl.session.clear()'` очищает их. Секретный ключ подписи сессионных cookie задаётся через `'app.secret_key = <str>'`.**

### Serving JSON
```python
@app.post('/<sport>/odds')
def serve_json(sport):
    team = fl.request.form['team']
    return {'team': team, 'odds': [2.09, 3.74, 3.68]}
```

#### Запуск приложения в отдельном потоке и отправка запроса к его REST API:
```python
# $ pip3 install requests
>>> import threading, requests
>>> threading.Thread(target=app.run, daemon=True).start()
>>> url = 'http://localhost:5000/football/odds'
>>> resp = requests.post(url, data={'team': 'Arsenal FC'})
>>> resp.json()
{'team': 'Arsenal FC', 'odds': [2.09, 3.74, 3.68]}
```


Profiling
---------

```python
from time import perf_counter
start_time = perf_counter()
...
seconds = perf_counter() - start_time
```

### Timing a Snippet
```python
>>> from timeit import timeit
>>> timeit('list(range(10_000))', number=1000, globals=globals())
0.19373
```

### Profiling by Line
```text
$ pip3 install line_profiler
$ echo '@profile
def main():
    a = list(range(10_000))
    b = set(range(10_000))
main()' > test.py
$ kernprof -lv test.py
Line #      Hits         Time  Per Hit   % Time  Line Contents
==============================================================
     1                                           @profile
     2                                           def main():
     3         1        253.4    253.4     32.2      a = list(range(10_000))
     4         1        534.1    534.1     67.8      b = set(range(10_000))
```

### Visualizations
```bash
$ apt install graphviz && pip3 install gprof2dot snakeviz  # На Windows установите graphviz.exe.
$ tail -n +2 test.py > test.tmp && mv test.tmp test.py     # Удаляет первую строку с @profile.
$ python3 -m cProfile -o test.prof test.py                 # Запуск трейсинг-профилировщика cProfile.
$ gprof2dot -f pstats test.prof | dot -T png -o test.png   # Генерирует граф вызовов (call graph).
$ xdg-open test.png                                        # Открывает сгенерированное изображение.
$ snakeviz test.prof                                       # Запускает интерактивный flame-граф в браузере.
```

### Sampling Profilers
```text
+--------------+-----------+-------------------------------+-----------+---------+
| pip3 install | Профиль   | Как запустить                 | Построчно | Вживую  |
+--------------+-----------+-------------------------------+-----------+---------+
| pyinstrument |    CPU    | pyinstrument test.py          |    Нет    |   Нет   |
| py-spy       |    CPU    | py-spy top -- python3 test.py |    Нет    |   Да    |
| scalene      | CPU & RAM | scalene test.py               |    Да     |   Нет   |
| memray       |    RAM    | memray run --live test.py     |    Да     |   Да    |
+--------------+-----------+-------------------------------+-----------+---------+
```


NumPy
-----
**Библиотека для эффективной работы с многомерными массивами. Может выполняться в сотни раз быстрее чистого кода Python.**

```python
# $ pip3 install numpy
import numpy as np
```

```python
<array> = np.array(<list/list_of_lists/…>)          # Массив NumPy. Принимает `dtype=np.int64`.
<array> = np.load(<path/file>)                      # Сохранение массива через np.save(<path>, <arr>).
```

```python
<array> = np.zeros/ones/empty(shape)                # shape: кортеж целых чисел (размеры осей).
<array> = np.arange(from, to_exc, ±step)            # Также np.linspace(start, stop, length).
<array> = np.random.randint(from, to_exc, shape)    # Также random.uniform(low, high, shape).
```

```python
<view>  = <array>.reshape(shape)                    # Также `<array>.shape = (<int>, [...])`.
<array> = <array>.flatten()                         # Возвращает одномерную копию. Также `<array>.ravel()`.
```

```python
<array> = np.abs/sqrt/log/copy(<array>)             # Возвращает новый массив той же формы.
<array> = <array>.sum/max/mean/argmax(axis)         # Агрегирует измерение по переданной оси.
<array> = np.apply_along_axis(<func>, axis, <arr>)  # Функция может возвращать скаляр или массив.
```

```python
<array> = np.concat(<arrays>, axis=0)               # Объединяет массивы вдоль первой оси (строк).
<array> = np.vstack/column_stack(<arrays>)          # 1D-массив рассматривается как строка/колонка.
<array> = np.tile/repeat(<arr>, <int/s> [, axis])   # Дублирует весь массив или повторяет элементы.
```
* **Shape (форма) — это кортеж размеров измерений. Изображение RGB 100x50 имеет форму `(50, 100, 3)`.**
* **Axis (ось) — индекс измерения. Самое левое измерение имеет индекс 0. Суммирование RGB-изображения по оси 2 вернёт полутоновое изображение формы `(50, 100)`.**

### Indexing
```perl
<object>   = <2d>[row_index, col_index]             # Или <3d>[<int>, <int>, <int>].
<1d_view>  = <2d>[row_index]                        # Или <3d>[<int>, <int>, <slice>].
<1d_view>  = <2d>[:, col_index]                     # Или <3d>[<int>, <slice>, <int>].
<2d_view>  = <2d>[row_i:to_exc, col_i:to_exc]       # Или <3d>[<int>, <slice>, <slice>].
```

```perl
<1d_array> = <2d>[row_indices, col_indices]         # Или <3d>[<int/1d>, <1d>, <1d>].
<2d_array> = <2d>[row_indices]                      # Или <3d>[<int/1d>, <1d>, <slice>].
<2d_array> = <2d>[:, col_indices]                   # Или <3d>[<int/1d>, <slice>, <1d>].
<2d_array> = <2d>[np.ix_(row_is, col_is)]           # Или <3d>[<int/1d/2d>, <2d>, <2d>].
```

```perl
<2d_bools> = <2d> > <el/1d/2d>                      # 1D-объект должен быть размером со строку.
<1/2d_arr> = <2d>[<2d/1d_bools>]                    # 1D-объект должен быть размером с колонку.
```
* **Символ `':'` возвращает срез всех индексов измерения. Если измерение пропущено, по умолчанию используется `':'`.**
* **Передача двух срезов (строка 4) работает так же, как передача среза и 1D-массива (строка 7).**
* **Python преобразует `'obj[i, j]'` в `'obj[(i, j)]'`. Это делает `'<2d>[row_i, col_i]'` и `'<2d>[row_indices]'` неотличимыми для NumPy, если передан кортеж из двух индексов.**
* **Вызов `'ix_([1, 2], [3, 4])'` возвращает `'[[1], [2]]'` и `'[[3, 4]]'`. Из-за правил broadcasting это эквивалентно индексации `'[[1, 1], [2, 2]]'` и `'[[3, 4], [3, 4]]'`.**
* **Любое значение, транслируемое (broadcastable) в форму выборки, может быть присвоено срезу.**

### Broadcasting
**Механизм автоматического выравнивания форм массивов при арифметических операциях.**
```python
array_a = np.array([0.1,  0.6,  0.8])               # Т.е. `array_a.shape == (3,)`.
array_b = np.array([[0.1], [0.6], [0.8]])           # Т.е. `array_b.shape == (3, 1)`.
```

#### 1. Если размерности массивов различаются по длине, более короткая форма дополняется единицами слева:
```python
array_a = np.array([[0.1,  0.6,  0.8]])             # Т.е. `array_a.shape == (1, 3)`.
array_b = np.array([[0.1], [0.6], [0.8]])           # Т.е. `array_b.shape == (3, 1)`.
```

#### 2. Измерения размером 1 растягиваются дублированием элементов:
```python
array_a = np.array([[0.1,  0.6,  0.8],              # Т.е. `array_a.shape == (3, 3)`.
                    [0.1,  0.6,  0.8],
                    [0.1,  0.6,  0.8]])

array_b = np.array([[0.1,  0.1,  0.1],              # Т.е. `array_b.shape == (3, 3)`.
                    [0.6,  0.6,  0.6],
                    [0.8,  0.8,  0.8]])
```

### Example
#### Для каждой точки возвращает индекс её ближайшего соседа (`[0.1, 0.6, 0.8] => [1, 2, 1]`):

```python
>>> print(points := np.array([0.1, 0.6, 0.8]))
[0.1  0.6  0.8]
>>> print(wrapped_points := points.reshape(3, 1))
[[0.1]
 [0.6]
 [0.8]]
>>> print(deltas := points - wrapped_points)
[[ 0.   0.5  0.7]
 [-0.5  0.   0.2]
 [-0.7 -0.2  0. ]]
>>> deltas[range(3), range(3)] = np.inf
>>> print(distances := np.abs(deltas))
[[inf  0.5  0.7]
 [0.5  inf  0.2]
 [0.7  0.2  inf]]
>>> print(distances.argmin(axis=1))
[1 2 1]
```


Image
-----
```python
# $ pip3 install pillow
from PIL import Image
```

```python
<Image> = Image.new('RGB', (width, heig))  # Создаёт холст. Также `color=<tuple_of_ints>`.
<Image> = Image.open(<path>)               # Автоматически определяет формат по содержимому.
<Image> = <Image>.convert('<mode>')        # Преобразует изображение в новый цветовой режим (см. Modes).
<Image>.save(<path>)                       # Качество для jpg: `quality=<int>`.
<Image>.show()                             # Открывает изображение в системной программе просмотра.
```

```python
<int/tup> = <Image>.getpixel((x, y))       # Возвращает цвет пикселя по координатам.
<ImgCore> = <Image>.getdata()              # Возвращает плоское представление значений пикселей.
<Image>.putpixel((x, y), <int/tuple>)      # Устанавливает цвет пикселя.
<Image>.putdata(<list/ImgCore>)            # Заполняет пиксели переданной последовательностью.
<Image>.paste(<Image>, (x, y))             # Вставляет другое изображение по координатам (x, y).
```

```python
<Image> = <Image>.filter(<Filter>)         # Принимает ImageFilter.BLUR/SHARPEN/FIND_EDGES/….
<Image> = <Enhance>.enhance(<float>)       # Например: `ImageEnhance.Contrast/Color/…(<Image>)`.
```

```python
<array> = numpy.array(<Image>)             # Преобразует изображение в 2D/3D-массив NumPy.
<Image> = Image.fromarray(<array>)         # Нормализация: np.uint8(<arr>.clip(0, 255)).
```

### Modes
* **`'L'` - Оттенки серого (8 бит). Каждый пиксель — целое число от 0 до 255.**
* **`'RGB'` - True color (24 бит). Каждый пиксель — кортеж из трёх чисел (R, G, B).**
* **`'RGBA'` - RGB с альфа-каналом прозрачности (четвёртое число кортежа).**
* **`'HSV'` - Hue, saturation, value (оттенок, насыщенность, яркость).**

### Examples
#### Создаёт PNG-изображение с градиентом спектра:
```python
W, H = 100, 100
n_pixels = W * H
hues = (255 * i/n_pixels for i in range(n_pixels))
img = Image.new('HSV', (W, H))
img.putdata([(int(h), 255, 255) for h in hues])
img.convert('RGB').save('test.png')
```

#### Добавляет шум к изображению PNG и отображает его:
```python
from random import randint
add_noise = lambda i: max(0, min(255, i + randint(-20, 20)))
img = Image.open('test.png').convert('HSV')
img.putdata([(add_noise(h), s, v) for h, s, v in img.getdata()])
img.show()
```

### Image Draw
```python
from PIL import ImageDraw
<Draw> = ImageDraw.Draw(<Image>)           # Объект для рисования 2D-графики на изображении.
<Draw>.point((x, y))                       # Рисует точку. Принимает `fill=<int/tuple/str>`.
<Draw>.line((x1, y1, x2, y2 [, ...]))      # Для сглаживания используйте `<Img>.resize((w, h))`.
<Draw>.arc((x1, y1, x2, y2), deg1, deg2)   # Рисует дугу эллипса по часовой стрелке.
<Draw>.rectangle((x1, y1, x2, y2))         # Также rounded_rectangle() и regular_polygon().
<Draw>.polygon((x1, y1, x2, y2, ...))      # Последняя точка автоматически замыкается с первой.
<Draw>.ellipse((x1, y1, x2, y2))           # Для вращения используйте `<Image>.rotate(deg)`.
<Draw>.text((x, y), <str>)                 # Принимает `font=ImageFont.truetype(path, size)`.
```
* **`'fill=<color>'` — основной цвет заливки фигуры.**
* **`'width=<int>'` — толщина линий или контура.**
* **`'outline=<color>'` — цвет контура фигуры.**
* **Цвет может быть числом, кортежем, `'#rrggbb[aa]'` или строковым именем цвета.**


Animation
---------
#### Создаёт GIF-анимацию прыгающего мяча:
```python
# $ pip3 install imageio
from PIL import Image, ImageDraw
import imageio

W, H, R = 126, 126, 10  # Ширина, высота, радиус.
frames = []
for velocity in range(1, 16):
    y = sum(range(velocity))
    frame = Image.new('L', (W, H))
    draw = ImageDraw.Draw(frame)
    draw.ellipse((W/2-R, y, W/2+R, y+2*R), fill='white')
    frames.append(frame)
frames += reversed(frames[1:-1])
imageio.mimsave('test.gif', frames, duration=0.03)
```


Audio
-----
```python
import wave
```

```python
<Wave>  = wave.open('<path>')               # Открывает указанный WAV-файл для чтения.
<int>   = <Wave>.getframerate()             # Частота дискретизации (фреймов/сэмплов в секунду).
<int>   = <Wave>.getnchannels()             # Количество каналов (1 — моно, 2 — стерео).
<int>   = <Wave>.getsampwidth()             # Глубина сэмпла в байтах (1, 2, 3 или 4).
<tuple> = <Wave>.getparams()                # Возвращает namedtuple со всеми параметрами.
<bytes> = <Wave>.readframes(<int>)          # Считывает фреймы (передайте -1 для чтения всех).
```

```python
<Wave> = wave.open('<path>', 'wb')          # Создаёт/перезаписывает WAV-файл для записи.
<Wave>.setframerate(<int>)                  # 44100 (CD) или 48000 (видео).
<Wave>.setnchannels(<int>)                  # 1 — моно, 2 — стерео.
<Wave>.setsampwidth(<int>)                  # 2 байта (16 бит, CD) или 3 байта (24 бит, Hi-Res).
<Wave>.setparams(<tuple>)                   # Передаёт кортеж всех параметров аудиопотока.
<Wave>.writeframes(<bytes>)                 # Записывает сэмплы в аудиофайл.
```
* **Объект bytes содержит последовательность фреймов, каждый состоит из одного или нескольких сэмплов.**
* **В стереосигнале первый сэмпл фрейма относится к левому каналу, второй — к правому.**
* **Каждый сэмпл состоит из одного или нескольких байтов, числовое значение которых задаёт отклонение мембраны динамика в данный момент времени.**
* **При ширине в 1 байт числа беззнаковые (unsigned 0..255). При других размерах — знаковые (signed) с прямым порядком байтов (little-endian).**

### Sample Values
```text
+-----------+-----------+------+-----------+
| sampwidth |    min    | zero |    max    |
+-----------+-----------+------+-----------+
|     1     |         0 |  128 |       255 |
|     2     |    -32768 |    0 |     32767 |
|     3     |  -8388608 |    0 |   8388607 |
+-----------+-----------+------+-----------+
```

### Read Float Samples from WAV File
```python
def read_wav_file(filename):
    def get_int(bytes_obj):
        an_int = int.from_bytes(bytes_obj, 'little', signed=(p.sampwidth != 1))
        return an_int - (128 * (p.sampwidth == 1))
    with wave.open(filename) as file:
        p = file.getparams()
        frames = file.readframes(-1)
    samples_b = (frames[i : i + p.sampwidth] for i in range(0, len(frames), p.sampwidth))
    return [get_int(b) / pow(2, (p.sampwidth * 8) - 1) for b in samples_b], p
```

### Write Float Samples to WAV File
```python
def write_to_wav_file(filename, samples_f, p=None, nchannels=1, sampwidth=2, fs=44100):
    def get_bytes(a_float):
        a_float = max(-1, min(1 - 2e-16, a_float)) + (p.sampwidth == 1)
        a_float *= pow(2, (p.sampwidth * 8) - 1)
        return int(a_float).to_bytes(p.sampwidth, 'little', signed=(p.sampwidth != 1))
    if p is None:
        p = wave._wave_params(nchannels, sampwidth, fs, 0, 'NONE', 'not compressed')
    with wave.open(filename, 'wb') as file:
        file.setparams(p)
        file.writeframes(b''.join(get_bytes(f) for f in samples_f))
```

### Examples
#### Сохраняет синусоидальный сигнал частотой 440 Гц в моно-WAV файл:
```python
from math import sin, pi
get_sin = lambda i: sin(440 * pi*2 * i/44100) * 0.2
write_to_wav_file('test.wav', (get_sin(i) for i in range(100_000)))
```

#### Добавляет шум к WAV-файлу:
```python
from random import uniform
samples_f, prms = read_wav_file('test.wav')
samples_f = (f + uniform(-0.02, 0.02) for f in samples_f)
write_to_wav_file('test.wav', samples_f, p=prms)
```

### Audio Player
```python
# $ pip3 install nava
from nava import play
play('test.wav')
```

### Text to Speech
```python
# $ pip3 install piper-tts sounddevice
import os, piper, sounddevice
os.system('python3 -m piper.download_voices en_US-lessac-high')
voice = piper.PiperVoice.load('en_US-lessac-high.onnx')
for sentence in voice.synthesize('Sally sells seashells by the seashore.'):
    sounddevice.wait()
    sounddevice.play(sentence.audio_float_array, sentence.sample_rate)
sounddevice.wait()
```


Synthesizer
-----------
#### Воспроизведение мелодии Popcorn Гершона Кингсли:

```python
# $ pip3 install numpy sounddevice
import itertools as it, math, numpy as np, sounddevice

def play_notes(notes, bpm=132, fs=44100, volume=0.1):
    beat_len  = 60/bpm * fs
    get_pause = lambda beats: it.repeat(0, int(beats * beat_len))
    get_sinus = lambda hz, i: math.sin(hz * math.pi*2 * i/fs) * volume
    get_wave  = lambda hz, beats: (get_sinus(hz, i) for i in range(int(beats * beat_len)))
    get_hertz = lambda note: 440 * 2 ** ((int(note[:2]) - 69) / 12)
    get_beats = lambda note: 1/2 if '♩' in note else 1/4 if '♪' in note else 1
    get_samps = lambda n: get_wave(get_hertz(n), get_beats(n)) if n else get_pause(1/4)
    samples_f = it.chain(get_pause(1/2), *(get_samps(n) for n in notes.split(',')))
    sounddevice.play(np.fromiter(samples_f, np.float32), fs, blocking=True)

play_notes('83♩,81♪,,83♪,,78♪,,74♪,,78♪,,71♪,,,,83♪,,81♪,,83♪,,78♪,,74♪,,78♪,,71♪,,,,'
           '83♩,85♪,,86♪,,85♪,,86♪,,83♪,,85♩,83♪,,85♪,,81♪,,83♪,,81♪,,83♪,,79♪,,83♪,,,,')
```


Pygame
------
#### Открывает окно и рисует квадрат, перемещаемый стрелками клавиатуры:
```python
# $ pip3 install pygame
import pygame as pg

pg.init()
window = pg.display.set_mode((500, 500))
rect = pg.Rect(240, 240, 20, 20)
while not pg.event.get(pg.QUIT):
    for evt in pg.event.get(pg.KEYDOWN):
        dx = (evt.key == pg.K_RIGHT) - (evt.key == pg.K_LEFT)
        dy = (evt.key == pg.K_DOWN) - (evt.key == pg.K_UP)
        rect = rect.move((dx * 20, dy * 20))
    window.fill(pg.Color('black'))
    pg.draw.rect(window, pg.Color('white'), rect)
    pg.display.flip()
pg.quit()
```


### Rect
**Хранит координаты верхнего левого угла, ширину и высоту прямоугольника.**
```python
<Rect> = pg.Rect(x, y, width, height)        # Создаёт Rect. Отсекает дробную часть float.
<int>  = <Rect>.x/y/centerx/centery          # Также `top`, `right` и др. Допускает присваивание.
<tup.> = <Rect>.topleft/center               # Также `topright/bottomright/bottomleft/size`.
<Rect> = <Rect>.move((dx, dy))               # Метод move_ip() сдвигает прямоугольник на месте.
```

```python
<bool> = <Rect>.collidepoint((x, y))         # Возвращает True, если точка лежит внутри прямоугольника.
<bool> = <Rect>.colliderect(<Rect>)          # Возвращает True, если прямоугольники пересекаются.
<int>  = <Rect>.collidelist(<Rects>)         # Индекс первого пересекающегося Rect или -1.
<list> = <Rect>.collidelistall(<Rects>)      # Список индексов всех пересекающихся прямоугольников.
```

### Surface
**Хранит изображение или экранную поверхность окна.**

```python
<Surf> = pg.Surface((w, h))                  # Новая RGB-поверхность. RGBA при `flags=pg.SRCALPHA`.
<Surf> = pg.display.set_mode((w, h))         # Создаёт главное окно и возвращает его Surface.
<Surf> = pg.image.load(<path/file>)          # Загружает изображение. Также get_width/get_height().
<Surf> = <Surf>.subsurface(<Rect>)           # Создаёт новую поверхность из вырезанной области.
<view> = <Surf>.get_view()                   # Прямая запись в пиксели: `<view>.write(<array>)`.
```

```python
<Surf>.fill(color)                           # Кортеж RGB или объект pg.Color('<name/hex>').
<Surf>.set_at((x, y), color)                 # Устанавливает цвет пикселя. Чтение: `<Surf>.get_at()`.
<Surf>.blit(<Surf>, (x, y))                  # Отрисовывает переданную поверхность по координатам (x, y).
```

```python
<Surf> = tr.scale(<Surf>, (w, h))            # Масштабирование: `import pygame.transform as tr`.
<Surf> = tr.rotate(<Surf>, degrees)          # Поворачивает поверхность против часовой стрелки.
<Surf> = tr.flip(<Surf>, flip_x=True)        # Зеркальное отражение по оси Y. Также `flip_y=True`.
```

```python
line(<Surf>, color, (x1, y1), (x2, y2))      # Отрезок. Для рисования: `from pygame.draw import *`.
arc(<Surf>, color, <Rect>, rad1, rad2)       # Рисует дугу эллипса против часовой стрелки.
rect(<Surf>, color, <Rect>, width=0)         # Прямоугольник (width=0 — заливка). Также polygon().
circle(<Surf>, color, (x, y), radius)        # Окружность. Также ellipse(<Surf>, color, <Rect>).
```

```python
<Font> = pg.font.Font(<path/file>, size)     # Загружает TTF-шрифт. Pass None для системного шрифта.
<Surf> = <Font>.render(<str>, True, color)   # 4-м аргументом можно передать цвет фона.
```

### Sound
```python
<Sound> = pg.mixer.Sound(<path/file>)        # Принимает WAV-файл или массив целых чисел.
<Sound>.play/stop()                          # Воспроизведение/стоп. Зацикливание: `loops=-1`.
```

### Basic Mario Brothers Example
```python
import pygame as pg, dataclasses as dc, enum, io, itertools, random as r, urllib.request

W, H, D = 50, 50, enum.Enum('D', 'n e s w')  # Ширина, высота, направления (север, восток, юг, запад).

def main():
    def get_window():
        pg.init()
        return pg.display.set_mode((W*16, H*16))
    def get_images():
        url = 'https://gto76.github.io/python-cheatsheet/web/mario_bros.png'
        img = pg.image.load(io.BytesIO(urllib.request.urlopen(url).read()))
        return [img.subsurface(get_rect(x, 0)) for x in range(20)]
    def get_mario():
        Mario = dc.make_dataclass('Mario', ['rect', 'vx', 'vy', 'dir', 'img_i'])
        return Mario(get_rect(1, 1), 0, 0, D.e, itertools.cycle(range(3)))
    def get_tiles():
        is_border = lambda x, y: x in [0, W-1] or y in [0, H-1]
        borders = [(x, y) for x in range(W) for y in range(H) if is_border(x, y)]
        platforms = [(r.randint(1, W-2), r.randint(2, H-2)) for _ in range(200)]
        return [get_rect(x, y) for x, y in borders + platforms]
    def get_rect(x, y):
        return pg.Rect(x*16, y*16, 16, 16)
    run(get_window(), get_images(), get_mario(), get_tiles())

def run(window, images, mario, tiles):
    clock = pg.time.Clock()
    pressed = set()
    while not pg.event.get(pg.QUIT):
        clock.tick(28)
        pressed |= {e.key for e in pg.event.get(pg.KEYDOWN)}
        pressed -= {e.key for e in pg.event.get(pg.KEYUP)}
        update_velocity(mario, tiles, pressed)
        update_position(mario, tiles)
        draw(window, images, mario, tiles)
    pg.quit()

def update_velocity(mario, tiles, pressed):
    mario.vx += 2 * ((pg.K_RIGHT in pressed) - (pg.K_LEFT in pressed))
    mario.vx += (mario.vx < 0) - (mario.vx > 0)
    mario.vx = max(-4, min(4, mario.vx))
    mario.vy += 1 if is_airborne(mario, tiles) else (pg.K_UP in pressed) * -10

def update_position(mario, tiles):
    x, y = mario.rect.topleft
    steps = max(abs(mario.vx), abs(mario.vy))
    for _ in range(steps):
        bounds = get_boundaries(mario.rect, tiles)
        mario.vx, mario.vy = stop_on_collision(mario.vx, mario.vy, bounds)
        mario.rect.topleft = x, y = x + (mario.vx/steps), y + (mario.vy/steps)

def is_airborne(mario, tiles):
    return D.s not in get_boundaries(mario.rect, tiles)

def get_boundaries(rect, tiles):
    deltas = {D.n: (0, -1), D.e: (1, 0), D.s: (0, 1), D.w: (-1, 0)}
    return {d for d in D if rect.move(deltas[d]).collidelist(tiles) != -1}

def stop_on_collision(vx, vy, bounds):
    return (0 if (D.w in bounds and vx < 0) or (D.e in bounds and vx > 0) else vx,
            0 if (D.n in bounds and vy < 0) or (D.s in bounds and vy > 0) else vy)

def draw(window, images, mario, tiles):
    window.fill((85, 168, 255))
    mario.dir = mario.dir if mario.vx == 0 else D.w if mario.vx < 0 else D.e
    img_i = 4 if is_airborne(mario, tiles) else next(mario.img_i) if mario.vx else 6
    window.blit(images[img_i + ((mario.dir == D.w) * 9)], mario.rect)
    for tile in tiles:
        is_border = tile.x in [0, (W-1)*16] or tile.y in [0, (H-1)*16]
        window.blit(images[18 if is_border else 19], tile)
    pg.display.flip()

if __name__ == '__main__':
    main()
```


Pandas
------
**Библиотека для анализа и обработки структурированных данных. Примеры визуализации см. в разделе [Plotly](#plotly).**

```python
# $ pip3 install pandas matplotlib
import pandas as pd, matplotlib.pyplot as plt
```

### Series
**Именованный упорядоченный одномерный массив с индексами (ключами).**

```python
>>> s = pd.Series([1, 2], index=['x', 'y'], name='a'); s
x    1
y    2
Name: a, dtype: int64
```

```python
<S>  = pd.Series(<list>)                       # Возвращает Series. Индексы по умолчанию 0..N-1.
<S>  = pd.Series(<dict>)                       # Ключи словаря используются в качестве 'index'.
```

```python
<el> = <S>.loc[key]                            # Доступ по ключу/метке. Либо `<S>.iloc[i]` по номеру.
<S>  = <S>.loc[coll_of_keys]                   # Выборка по коллекции ключей. Или `<S>.iloc[coll_of_i]`.
<S>  = <S>.loc[from_key : to_key_inc]          # Срез по меткам включительно! Либо `<S>.iloc[...]`.
```

```python
<el> = <S>[key/i]                              # Или `<S>.<key>`.
<S>  = <S>[coll_of_keys/coll_of_i]             # Или `<S>[key/i : key/i]`.
<S>  = <S>[<S_of_bools>]                       # Или `<S>.loc/iloc[<S_of_bools>]`.
```

```python
<S>  = <S> > <el/S>                            # Возвращает Series булевых значений. Логика: &, |, ~.
<S>  = <S> + <el/S>                            # Элементы с несовпадающими ключами получают NaN.
```

```python
<S>  = <S>.head/describe/sort_values()         # Также `<S>.unique/value_counts/round/dropna()`.
<S>  = <S>.str.strip/lower/contains/replace()  # Векторизованные строковые операции.
<S>  = <S>.dt.year/month/day/hour              # pd.to_datetime(<S>) преобразует Series в даты.
<S>  = <S>.dt.to_period('y/m/d/h')             # Квантует даты в объекты Period.
```

```python
<S>.plot.line/area/bar/pie/hist()              # Генерирует график. Принимает аргумент `title=<str>`.
plt.show()                                     # Отображает график. Также `plt.savefig(<path>)`.
```
* **Используйте `'print(<S>.to_string())'` для полного вывода Series длиннее 60 строк.**
* **Используйте `'<S>.index'` для получения коллекции ключей и `'<S>.index = <coll>'` для их обновления.**
* **Передавайте в loc/iloc список или Series: `'<S>.loc[key_1, key_2]'` зарезервировано для MultiIndex.**
* **Pandas использует типы NumPy (например, `'np.int64'`). Если какому-либо элементу присвоено значение np.nan, тип Series автоматически повышается до `'float64'`. Для явной смены типа: `'<S>.astype(<str/type>)'`.**

#### Series — Агрегация, Трансформация, Отображение (Aggregate, Transform, Map):
```python
<el> = <S>.sum/max/mean/std/idxmax/count()     # Или: `<S>.agg(lambda <S>: <el>)`
<S>  = <S>.rank/diff/cumsum/ffill/interpol…()  # Или: `<S>.agg/transform(lambda <S>: <S>)`
<S>  = <S>.isna/fillna/isin([<el/coll>])       # Или: `<S>.agg/transform/map(lambda <el>: <el>)`
```

```text
+--------------+-------------+-------------+---------------+
|              |    'sum'    |   ['sum']   | {'s': 'sum'}  |
+--------------+-------------+-------------+---------------+
| s.apply(…)   |      3      |    sum  3   |     s  3      |
| s.agg(…)     |             |             |               |
+--------------+-------------+-------------+---------------+
```

```text
+--------------+-------------+-------------+---------------+
|              |    'rank'   |   ['rank']  | {'r': 'rank'} |
+--------------+-------------+-------------+---------------+
| s.apply(…)   |             |      rank   |               |
| s.agg(…)     |    x  1.0   |   x   1.0   |   r  x  1.0   |
|              |    y  2.0   |   y   2.0   |      y  2.0   |
+--------------+-------------+-------------+---------------+
```

### DataFrame
**Двумерная таблица с именованными строками (индексами) и столбцами (колонками).**

```python
>>> df = pd.DataFrame([[1, 2], [3, 4]], index=['a', 'b'], columns=['x', 'y']); df
   x  y
a  1  2
b  3  4
```

```python
<DF>   = pd.DataFrame(<list_of_rows>)          # Строки могут быть списками, словарями или Series.
<DF>   = pd.DataFrame(<dict_of_columns>)       # Столбцы могут быть списками, словарями или Series.
```

```python
<el>   = <DF>.loc[row_key, col_key]            # Либо: `<DF>.iloc[row_i, col_i]`
<S/DF> = <DF>.loc[row_key/s]                   # Либо: `<DF>.iloc[row_i/s]`
<S/DF> = <DF>.loc[:, col_key/s]                # Либо: `<DF>.iloc[:, col_i/s]`
<DF>   = <DF>.loc[row_bools, col_bools]        # Либо: `<DF>.iloc[row_bools, col_bools]`
```

```python
<S/DF> = <DF>[col_key/s]                       # Либо: `<DF>.<col_key>`
<DF>   = <DF>[<S_of_bools>]                    # Фильтрация строк: например, `df[df.x > 1]`.
<DF>   = <DF>[<DF_of_bools>]                   # Заменяет на NaN ячейки, где условие False.
```

```python
<DF>   = <DF> > <el/S/DF>                      # Возвращает DF булевых значений. Series трактуется как строка.
<DF>   = <DF> + <el/S/DF>                      # Ячейки с несовпадающими метками получают значение NaN.
```

```python
<DF>   = <DF>.set_index(col_key)               # Заменяет индексы строк значениями колонки.
<DF>   = <DF>.reset_index(drop=False)          # Сбрасывает индексы в отдельную колонку `index`.
<DF>   = <DF>.sort_index(ascending=True)       # Сортирует строки по индексам. Для колонок: `axis=1`.
<DF>   = <DF>.sort_values(col_key/s)           # Сортирует строки по значению колонки/колонок.
```

```python
<DF>   = <DF>.head/tail/sample(<int>)          # Возвращает первые, последние или случайные n строк.
<DF>   = <DF>.describe()                       # Статистика колонок. Также info(), corr(), shape.
<DF>   = <DF>.query('<query>')                 # Фильтрация строк запросом: `df.query('x > 1')`.
```

```python
<DF>.plot.line/area/bar/scatter(x=col_key, …)  # `y=col_key/s`. Также hist/box(column/by=col_k).
plt.show()                                     # Отображает график. Также `plt.savefig(<path>)`.
```

#### DataFrame — Слияние, Соединение, Конкатенация (Merge, Join, Concat):
```python
>>> df_2 = pd.DataFrame([[4, 5], [6, 7]], index=['b', 'c'], columns=['y', 'z']); df_2
   y  z
b  4  5
c  6  7
```

```text
+-----------------------+---------------+------------+------------+------------------------------------+
|                       |    'outer'    |   'inner'  |   'left'   |              Описание              |
+-----------------------+---------------+------------+------------+------------------------------------+
| df.merge(df_2,        |    x   y   z  | x   y   z  | x   y   z  | Слияние по колонке 'on' или        |
|          on='y',      | 0  1   2   .  | 3   4   5  | 1   2   .  | 'left_on/right_on', либо по общим  |
|          how=…)       | 1  3   4   5  |            | 3   4   5  | колонкам. По умолчанию 'inner'.   |
|                       | 2  .   6   7  |            |            |                                    |
+-----------------------+---------------+------------+------------+------------------------------------+
| df.join(df_2,         |    x yl yr  z |            | x yl yr  z | Соединение по индексам строк.      |
|         lsuffix='l',  | a  1  2  .  . | x yl yr  z | 1  2  .  . | По умолчанию 'left'.               |
|         rsuffix='r',  | b  3  4  4  5 | 3  4  4  5 | 3  4  4  5 | Если передан Series, он            |
|         how=…)        | c  .  .  6  7 |            |            | воспринимается как колонка.        |
+-----------------------+---------------+------------+------------+------------------------------------+
| pd.concat([df, df_2], |    x   y   z  |     y      |            | Добавляет строки снизу.            |
|           axis=0,     | a  1   2   .  |     2      |            | По умолчанию 'outer'.              |
|           join=…)     | b  3   4   .  |     4      |            | Series воспринимается как колонка. |
|                       | b  .   4   5  |     4      |            | Добавление строки:                 |
|                       | c  .   6   7  |     6      |            | pd.concat([df, DF([s])]).          |
+-----------------------+---------------+------------+------------+------------------------------------+
| pd.concat([df, df_2], |    x  y  y  z |            |            | Добавляет колонки справа.          |
|           axis=1,     | a  1  2  .  . | x  y  y  z |            | По умолчанию 'outer'.              |
|           join=…)     | b  3  4  4  5 | 3  4  4  5 |            | Series воспринимается как колонка. |
|                       | c  .  .  6  7 |            |            |                                    |
+-----------------------+---------------+------------+------------+------------------------------------+
```

#### DataFrame — Агрегация, Трансформация, Отображение:
```python
<S>  = <DF>.sum/max/mean/std/idxmax/count()    # Или: `<DF>.apply/agg(lambda <S>: <el>)`
<DF> = <DF>.rank/diff/cumsum/ffill/interpo…()  # Или: `<DF>.apply/agg/transform(lambda <S>: <S>)`
<DF> = <DF>.isna/fillna/isin([<el/coll>])      # Или: `<DF>.applymap(lambda <el>: <el>)`
```

```text
+-----------------+---------------+---------------+---------------+
|                 |     'sum'     |    ['sum']    | {'x': 'sum'}  |
+-----------------+---------------+---------------+---------------+
| df.apply(…)     |      x  4     |        x  y   |     x  4      |
| df.agg(…)       |      y  6     |   sum  4  6   |               |
+-----------------+---------------+---------------+---------------+
```

```text
+-----------------+---------------+---------------+---------------+
|                 |     'rank'    |    ['rank']   | {'x': 'rank'} |
+-----------------+---------------+---------------+---------------+
| df.apply(…)     |               |       x    y  |               |
| df.agg(…)       |       x    y  |    rank rank  |         x     |
| df.transform(…) |  a  1.0  1.0  |  a  1.0  1.0  |    a  1.0     |
|                 |  b  2.0  2.0  |  b  2.0  2.0  |    b  2.0     |
+-----------------+---------------+---------------+---------------+
```
* **Перечисленные методы обрабатывают колонки, если не передан аргумент `'axis=1'`. Исключения: `'<DF>.dropna()'`, `'<DF>.drop(row_key/s)'` и `'<DF>.rename(<dict/func>)'`.**
* **Колонки с мультииндексом требуют кортеж меток для обращения: `'<DF>.loc[row_key, (col_key_1, col_key_2)]'`.**

### Multi-Index
```python
<DF> = <DF>.loc[row_key_1]                     # Также `<DF>.loc[(slice(None), row_key_2), :]`.
<DF> = <DF>.loc[:, col_key_1]                  # То же, что `<DF>.xs(col_key_1, axis=1, level=0)`.
<DF> = <DF>.set_index(col_key/s)               # Перемещает колонку/колонки в индекс. Также `append=True`.
<DF> = <DF>.pivot_table(index=col_key/s)       # Сводная таблица: `columns=k/s, values=k/s, aggfunc='mean'`.
<S>  = <DF>.stack/unstack(level=-1)            # Переносит ключи колонок в индекс строк и наоборот.
```

### File Formats
```python
<S/DF> = pd.read_json/pickle(<path/url/file>)  # Также io.StringIO(<str>), io.BytesIO(<bytes>).
<DF>   = pd.read_csv/excel(<path/url/file>)    # Также `header/index_col/dtype/usecols/…=<obj>`.
<list> = pd.read_html(<path/url/file>)         # Вызывает ImportError, если на странице нет таблиц.
<S/DF> = pd.read_parquet/feather/hdf(<path…>)  # Функция read_hdf() принимает `key=<s/df_name>`.
<DF>   = pd.read_sql('<table/query>', <conn>)  # Соединение SQLite3 или SQLAlchemy. См. #SQLite.
```

```python
<DF>.to_json/csv/html/latex/parquet(<path>)    # Возвращает строку/байты, если путь опущен.
<DF>.to_pickle/excel/feather/hdf(<path>)       # Метод to_hdf() требует `key=<s/df_name>`.
<DF>.to_sql('<table_name>', <connection>)      # Режим перезаписи/дозаписи: `if_exists='fail/replace/append'`.
```
* **Зависимости: `'$ pip3 install "pandas[excel]" odfpy lxml pyarrow'`.**
* **Функции CSV используют те же диалекты, что и встроенный модуль csv (например, `'sep=","'`).**
* **Функция read\_csv() парсит даты только для колонок из списка `'parse_dates'`.**
* **Если аргумент 'parse_dates' содержит 'index\_col', создаётся DataFrame с DatetimeIndex. Его метод `'resample("y/m/d/h")'` позволяет выполнять временную передискретизацию.**

### GroupBy
**Объект для разделения строк датафрейма на группы по значению указанной колонки (split-apply-combine).**

```python
<GB> = <DF>.groupby(col_key/s)                 # Разбивает DF на группы по переданной колонке.
<DF> = <GB>.apply/filter(<func>)               # filter() отбрасывает группу, если func вернула False.
<DF> = <GB>.get_group(<el>)                    # Извлекает отдельную группу по значению ключа группировки.
<S>  = <GB>.size()                             # Количество элементов в каждой группе (Series).
<GB> = <GB>[col_key]                           # Группировка одной колонки. Все операции возвращают Series.
```

```python
<DF> = <GB>.sum/max/mean/std/idxmax/count()    # Или: `<GB>.agg(lambda <S>: <el>)`
<DF> = <GB>.rank/diff/cumsum/ffill()           # Или: `<GB>.transform(lambda <S>: <S>)`
<DF> = <GB>.fillna(<el>)                       # Или: `<GB>.transform(lambda <S>: <S>)`
```

#### Группирует строки и вычисляет суммы по колонкам:
```python
>>> df = pd.DataFrame([[1, 2, 3], [4, 5, 6], [7, 8, 6]], list('abc'), list('xyz'))
>>> gb = df.groupby('z'); gb.apply(print)
   x  y  z
a  1  2  3
   x  y  z
b  4  5  6
c  7  8  6
>>> gb.sum()
    x   y
z
3   1   2
6  11  13
```

### Rolling
**Объект для расчётов в скользящем окне (rolling window).**

```python
<RS/RDF/RGB> = <S/DF/GB>.rolling(win_size)     # Также `min_periods=None, center=False`.
<RS/RDF/RGB> = <RDF/RGB>[col_key/s]            # Также `<RDF/RGB>.<col_key>`, если ключ — строка.
<S/DF>       = <R>.mean/sum/max()              # Или: `<R>.apply/agg(lambda <S>: <el>)`
```


Plotly
------
```python
# $ pip3 install plotly kaleido pandas
import plotly.express as px, pandas as pd
```

```python
<Fig> = px.line(<DF> [, y=col_key/s [, x=col_key]])   # Также `px.line(y=<list> [, x=<list>])`.
<Fig>.update_layout(paper_bgcolor='#rrggbb')          # Также `margin=dict(t=0, r=0, b=0, l=0)`.
<Fig>.write_html/json/image('<path>')                 # Вызов `<Fig>.show()` открывает интерактивный график.
```

```python
<Fig> = px.area/bar/box(<DF>, x=col_key, y=col_keys)  # Также `color=col_key`. Все параметры опциональны.
<Fig> = px.scatter(<DF>, x=col_key, y=col_keys)       # Также `color/size/symbol=col_key`.
<Fig> = px.scatter_3d(<DF>, x=col_key, y=col_key, …)  # `z=col_key`. Также color, size, symbol.
<Fig> = px.histogram(<DF>, x=col_keys, y=col_key)     # Также color, nbins. Все параметры опциональны.
```

#### Линейный график смертности от COVID-19 на миллион человек по континентам:

![Covid Deaths](web/covid_deaths.png)
<div id="2a950764-39fc-416d-97fe-0a6226a3095f" class="plotly-graph-div" style="height:312px; width:914px;"></div>

```python
covid = pd.read_csv('https://raw.githubusercontent.com/owid/covid-19-data/8dde8ca49b'
                    '6e648c17dd420b2726ca0779402651/public/data/owid-covid-data.csv',
                    usecols=['iso_code', 'date', 'population', 'total_deaths'])
continents = pd.read_csv('https://gto76.github.io/python-cheatsheet/web/continents.csv',
                         usecols=['Three_Letter_Country_Code', 'Continent_Name'])
df = pd.merge(covid, continents, left_on='iso_code', right_on='Three_Letter_Country_Code')
df = df.groupby(['Continent_Name', 'date']).sum().reset_index()
df['Total Deaths per Million'] = df.total_deaths * 1e6 / df.population
df = df[df.date > '2020-03-14']
df = df.rename({'date': 'Date', 'Continent_Name': 'Continent'}, axis='columns')
px.line(df, x='Date', y='Total Deaths per Million', color='Continent')
```

#### Многоосевой линейный график случаев COVID-19 и динамики цен Bitcoin, Dow Jones и золота:

![Covid Cases](web/covid_cases.png)
<div id="e23ccacc-a456-478b-b467-7282a2165921" class="plotly-graph-div" style="height:285px; width:935px;"></div>

```python
# $ pip3 install pandas lxml selenium plotly
import pandas as pd, selenium.webdriver, io, plotly.graph_objects as go

def main():
    covid, (bitcoin, gold, dow) = get_covid_cases(), get_tickers()
    df = wrangle_data(covid, bitcoin, gold, dow)
    display_data(df)

def get_covid_cases():
    url = 'https://catalog.ourworldindata.org/garden/covid/latest/compact/compact.csv'
    df = pd.read_csv(url, parse_dates=['date'])
    df = df[df.country == 'World']
    s = df.set_index('date').total_cases
    return s.rename('Total Cases')

def get_tickers():
    with selenium.webdriver.Chrome() as driver:
        driver.implicitly_wait(10)
        symbols = {'Bitcoin': 'BTC-USD', 'Gold': 'GC=F', 'Dow Jones': '%5EDJI'}
        return [get_ticker(driver, name, symbol) for name, symbol in symbols.items()]

def get_ticker(driver, name, symbol):
    url = f'https://finance.yahoo.com/quote/{symbol}/history/'
    driver.get(url + '?period1=1579651200&period2=9999999999')
    if buttons := driver.find_elements('xpath', '//button[@name="reject"]'):
        buttons[0].click()
    html = io.StringIO(driver.page_source)
    dataframes = pd.read_html(html, parse_dates=['Date'])
    s = dataframes[0].set_index('Date').Open
    return s.rename(name)

def wrangle_data(covid, bitcoin, gold, dow):
    df = pd.concat([bitcoin, gold, dow], axis=1)  # Создаёт DF объединением колонок по датам.
    df = df.sort_index().interpolate()            # Сортирует по датам, интерполирует пропуски NaN.
    df = df.loc['2020-02-23':'2021-12-20']        # Оставляет срез строк за указанный период.
    df = (df / df.iloc[0]) * 100                  # Нормализует значения к первому дню в процентах.
    df = df.join(covid)                           # Добавляет колонку с количеством случаев COVID.
    return df.sort_values(df.index[-1], axis=1)   # Сортирует колонки по значению последнего дня.

def display_data(df):
    figure = go.Figure()
    for col_name in reversed(df.columns):
        yaxis = 'y1' if col_name == 'Total Cases' else 'y2'
        trace = go.Scatter(x=df.index, y=df[col_name], yaxis=yaxis, name=col_name)
        figure.add_trace(trace)
    figure.update_layout(
        width=944,
        height=423,
        yaxis1=dict(title='Total Cases', rangemode='tozero'),
        yaxis2=dict(title='%', rangemode='tozero', overlaying='y', side='right'),
        colorway=['#EF553B', '#636EFA', '#00CC96', '#FFA152'],
        legend=dict(x=1.08)
    )
    figure.show()

if __name__ == '__main__':
    main()
```


Appendix
--------
### Cython
**Библиотека, транслирующая и компилирующая Python-подобный код в C.**

```python
# $ pip3 install cython
import pyximport; pyximport.install()                # Модуль для прямого запуска Cython-скриптов.
import <cython_script>                               # Скрипт должен иметь расширение '.pyx'.
```

#### Все объявления `'cdef'` опциональны, но именно они обеспечивают кратное ускорение:
```python
cdef <type> <var_name> [= <obj/var>]                 # Переменная типа Python или C.
cdef <ctype> *<pointer_name> [= &<var>]              # Разыменование через `<pointer>[0]`.
cdef <ctype>[size] <array_name> [= <coll/array>]     # Также `<ctype>[:] <mview> = <array>`.
cdef <ctype> *<array_name> [= <coll/array/pointer>]  # Например: `<<ctype> *> malloc(n_bytes)`.
```

```python
cdef <type> <func_name>(<type> [*]<arg_name>): ...   # Без указания типа по умолчанию `object`.
```

```python
cdef class <class_name>:                             # Также `cdef struct <struct_name>:`.
    cdef public <type> [*]<attr_name>                # Также `... <ctype> [*]<field_name>`.
    def __init__(self, <type> <arg_name>):           # Также `cdef __dealloc__(self):`.
        self.<attr_name> = <arg_name>                # Также `... free(<array/pointer>)`.
```

### Virtual Environments
**Система изоляции зависимостей и библиотек под конкретный проект.**

```perl
$ python3 -m venv NAME         # Создаёт виртуальное окружение в текущей папке.
$ source NAME/bin/activate     # Активация в Linux/macOS. В Windows: `NAME\Scripts\activate`.
$ pip3 install LIBRARY         # Устанавливает библиотеку в активное виртуальное окружение.
$ python3 FILE                 # Запуск скрипта в активном виртуальном окружении.
$ deactivate                   # Деактивирует текущее виртуальное окружение.
```

### Basic Script Template
**Запуск скрипта: `'$ python3 FILE'` или `'$ chmod u+x FILE; ./FILE'`. Для автоматического входа в отладчик при необработанном исключении: `'$ python3 -m pdb -cc FILE'`.**
```python
#!/usr/bin/env python3
#
# Usage: .py
#

from sys import argv, exit
from collections import defaultdict, namedtuple
from dataclasses import make_dataclass
from enum import Enum
import functools as ft, itertools as it, operator as op, re


def main():
    pass


###
##  UTIL
#

def read_file(filename):
    with open(filename, encoding='utf-8') as file:
        return file.readlines()


if __name__ == '__main__':
    main()
```


Index
-----
* **Обычно достаточно стандартного поиска по странице: Ctrl+F / ⌘F.**
* **Поиск `'#<заголовок>'` на [веб-странице](https://gto76.github.io/python-cheatsheet/) ограничивает выборку только названиями разделов.**
* **Нажмите на символ `'🔗'` рядом с заголовком, чтобы скопировать прямую ссылку на раздел.**
