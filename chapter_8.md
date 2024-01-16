# ▶ CHAPTER 08 - 파이썬 스타일 코드 I
## git push가 않 되...... 이게 왜..?
## 1️⃣ 파이썬 스타일 코드의 이해
### ☛ 파이썬 스타일 코드의 개념
: 파이썬 스타일의 코드 작성 기법

### ☛ 파이썬 스타일 코드를 사용하는 이유 
: 코드상으로 사람이 해야하는 일을 최대한 줄이면서 같은 결과를 얻을 수 있는 문법 체계가 만들어짐
>인간의 시간이 컴퓨터의 시간보다 더 중요하다

< 파이썬 스타일 코드를 배워야하는 이유>
* 다른 사람이 작성한 코드를 쉽게 이해할 수 있음
* 효율적임 (빠르게 코드를 작성할 수 있음)
* **코드가 간결해지고 시간을 줄일 수 있음**

### ☛ 문자열의 분리 및 결합
#### 문자열의 분리 : split()
: 특정 값을 기준으로 문자열을 분리하여 리스트 형태로 반환
<br> : 텍스트를 리스트 형태로 간단히 나누어 분리할 수 있음

#### 문자열의 결합: join()
: 문자열로 구성된 리스트를 하쳐 하나의 문자열로 만듦

### ☛ 리스트 컴프리 헨션
: 기존 리스트형을 사용하여 간단하게 새로운 리스트를 만드는 기법
<br> ***한 줄로 코드를 작성할 수 있음**

* 일반적인 반복문과 리스트
```python
>>> result = []
>>> for i in range(10) :
•••     result.append(i)
•••
>>> result
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

* 리스트 컴프리헨션
```python
>>> result = [ i for i in range(10)]
>>> result
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### 시용법
1. 필터링
```python
>>> result = [ i for i in range(10) if i % 2 == 0]
>>> result
[0, 2, ,4 ,6 ,8]
```
→ 조건문을 넣어줌

2. 중첩 반복문
```python
>>> word_1 = "Hello"
>>> word_2 = "World"
>>> result = [i = j for i in word_1 for j in word_2]
>>> result
['HW', 'Ho', 'Hr', 'Hl', 'Hd', 'eW', 'eo', 'er', 'el', 'ed', 'lW', 'lo', 'lr', 'll', 'ld', 'lW', 'lo', 'lr', 'll', 'ld', 'oW', 'oo', 'or', 'ol', 'od']
```

3. 이차원 리스트
: **대괄호**가 중효함
```python
>>> case_1 = ['a', 'b', 'c']
>>> case_2 = ['d', 'e', 'f']
>>> result =[[i + j for i in case_1] for j in case_2]
>>> result
[['ad', 'bd', 'cd'], ['ae', 'be', 'ce'], ['af', 'bf', 'cf']]
```

#### 성능
: 리스트 컴프리헨션은 내부적으로 잘 구성된 메모리 사용 방식으로 기존 반복문보다 시간 면에서 효율적인 연산이 가능

### ☛ 다양한 방식의 리스트값 출력
#### enumerate()
: 리스트의 값을 추출할 때 인덱스를 붙여 함꼐 출력하는 방법
<br> 딕셔너리형으로 인덱스(key), 단어(value) -> 쌍으로 묶어 출력
```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']) :
...     print(i, v)
... 
0 tic
1 tac
2 toe
```

#### zip()
: 1개 이상의 리스트값이 같은 인덱스에 있을 때 병렬로 묶는 함수
```python
>>> alist = ['a1', 'a2', 'a3']
>>> blist = ['b1', 'b2', 'b3']
>>> for a, b in zip(alist, blist) :
...     print(a, b)
... 
a1 b1
a2 b2
a3 b3
```

<enumerate()와 zip() 같이 사용하는 방법>

```python
>>> alist = ['a1', 'a2', 'a3']
>>> blist = ['b1', 'b2', 'b3']
>>> for i, (a, b) in enumerate(zip(alist, blist)) :
...     print(i, a, b)
... 
0 a1 b1
1 a2 b2
2 a3 b3
```