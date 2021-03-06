# Python

| #    | contents                                    |
| ---- | ------------------------------------------- |
| 1    | [PEP](#1-peppython-enhancement-proposals) |
| 2    | [Lambda Function](#2-lambda-function)       |
| 3    | [List Comprehension](#3-list-comprehension) |
| 4    | [range()](#4-range)                       |
| 5    | [enumerate()](#5-enumerate)               |
| 6    | [divmod()](#6-divmod)                     |
| 7    | [print()](#7-print)                       |
| 8    | [string formatting](#8-string-formatting)   |
| 9    | [pass](#9-pass)                             |
| 10   | [locals()](#10-locals)                    |



----



## 1. PEP(Python Enhancement Proposals) 

[PEP 8](https://www.python.org/dev/peps/pep-0008/): Style Guide for Python Code

 #### 1) Python은 snake_case 지향

​	 c.f. Java에서는 camelCase 지향

#### 2) slicing에서 parameter가 생략되었을 때, colon 사이의 공간도 생략해야 함

```python
# correct
example[lower::step]

# wrong
example[lower : : upper]
```

#### 3)  = sign에서 띄어쓰기를 하지 않는 경우: keyword argument, unannotated function parameter

- keyword argument란

  ```python
  def func(a, b)
  
  # positional argument
  func(1, 2)
  
  # keyword argument
  func(b=2, a=1)
  ```

* unannotated function이란

  ```python
  # annotated function
  def func(par1: int, par2: 1/2, par3: 'this is annotation') -> bool
  
  # unannotated function
  def func(par1, par2, par3) -> bool
  ```

- = sign에서 띄어쓰기를 하지 않는 경우

  ```python
  # correct
  def complex(real, imag=0.0):
      return magic(r=real, i=imag)
  
  # wrong
  def complex(real, imag=0.0):
      return magic(r = real, i = imag)
  ```



## 2. [Lambda Function](https://wikidocs.net/22804)

#### 이름이 없는 함수 생성 가능

#### > 간결한 코드, 메모리 절약 (1번만 사용될 함수에 용이)

```python
# def syntax
def 함수이름(매개변수):
    return 결과

# lambda syntax
lambda 매개변수: 결과

# example: 불필요한 공백을 제외한 문자의 길이로 정렬
target = [' cat', ' tiger ', '   dog', 'snake   ']

# def
def my_key(string):
    return len(string.strip())
print(sorted(target, key=my_key))

# lambda
print(sorted(target, key=lambda x : len(x.strip())))
```



## 3. [List Comprehension](https://wikidocs.net/22805)

#### 기존 리스트를 기반으로 새로운 리스트 생성 

#### > [map과 filter](https://wikidocs.net/22803) 대체 가능



- if 지원

  ```python
  x for x in range(1, 10+1) if x % 2 == 0]
  >>> [2, 4, 6, 8, 10]
  ```

- 다중 for문 지원

  ```python
  [(x, y) for x in ['월', '화'] for y in ['수', '목', '금']]
  ```



## 4. range()

```python
# 이미 생성된 값이 담겨있음
a = [n for n in range(100)]

# 생성해야 한다는 조건만 존재
b = range(100)
```



## 5. enumerate()

#### 순서가 있는 자료형(list, set, tuple등)을 index를 포함한 enumerate 객체로 리턴 

#### > range() 대체 가능

```python
eg = ['a', 'b', 'c']

list(enumerate(eg))
>>> [(0, 'a'), (1, 'b'), (2, 'c')]

# range()
for i in range(len(eg)):
    print(i, eg[i])
    
# enumerate()
for i, v in enumerate(eg):
    print(i, v)
```



## 6. divmod()

#### 몫과 나머지 동시에 return

```python
divmod(5, 3)
>>> (1, 2)

5//3
>>> 1

5%3
>>> 2
```



## 7. print()

#### default가 ```end = '\n'```

```python
print('aa')
print('bb')
>>> aa
bb

print('aa', end=' ')
print('bb')
>>> aa bb
```



#### c.f. pprint()는 줄바꿈 처리

```python
import pprint
numbers = [[1,2,3], [4,5], [6,7,8,9]]

# print
print(numbers)
>>> [[1,2,3], [4,5], [6,7,8,9]]

# positional arguments unpacking
print(*numbers)
>>> [1,2,3], [4,5], [6,7,8,9]

# pprint
pprint.pprint(numbers)
>>> [[1,2,3],
     [4,5],
     [6,7,8,9]
    ]
```



## 8. string formatting

```python
idx = 1
fruit = "Apple"
# >>> 2: Apple로 출력하기

# %
print('%d: %s' % (idx + 1, fruit))

# str.format()
print('{0}: {1}'.format(idx + 1, fruit))

# f-string
print(f'{idx + 1}: {fruit}')
```



## 9. pass

#### pass는 Null Operation: 아무것도 하지 않는 기능

#### > 정의되지 않은 함수의 골격을 잡을 때 용이

```python
# case1()가 아무런 처리를 하지 않았기 때문에 case2()에서 에러 발생
class new(object):
	  def case1(self):
      def case2(self):
          print("example2")
            
c = new()

# pass가 에러 방지
class new(object):
      def case1(self):
          pass
      def case2(self):
          print("example2")
            
c = new()
```



## 10. locals()

```python
# 로컬 변수 출력
import pprint
pprint.pprint(locals())
```

