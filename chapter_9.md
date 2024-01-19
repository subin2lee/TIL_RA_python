# ▶ CHAPTER 09 - 파이썬 스타일 코드 II
## git이랑 언제 친해짐..? -> 평생 불가능할지도..
## 1️⃣ 람다 함수
### 람다 함수의 사용
: 함수의 이름 없이 함수처럼 사용할 수 있는 익명의 함수
<br> 일반적인 함수처럼 def, return, 이름을 지정하지 않아도 사용 가능

```python
f = lambda x, y : x + y
print(f(1, 4))

# 5
```
→ f함수와 **구조는 같고 표현 방법이 다름**

[ 다른 식으로 표현하기 ]
```python
print((lambda x : x + 1)(5))
```
⎿ x에 인수 5를 할당하여 결과가 반환됨

[ 오류발생 ]
```python
f = lambda x : x / 2
print(f(3, 5))
```
⎿ 매개변수는 x밖에 주어지지 않았지만, 인자가 2개나 있음

* 함수와 작동방식은 비슷한 것 같음 (매개변수와 반환값)
* 파이썬 3.x부터 권장은 하지 않지만 코드가 간단하고 다른 함수와 함께 사용되니 꼭 알아두면 조흠^^b

## 2️⃣ 맵리듀스
### • map(함수 이름, 리스트 데이터) 
: 연속 데이터를 저장하는 시퀀스 자료형에서 요소마다 같은 기능을 적용할 때 주로 사용함. (리스트나 튜플)
```python
>>> ex = [1, 2,3 ,4 ,5]
>>> f = lambda x : x ** 2
>>> print(list(map(f, ex)))

#[1, 4, 9, 16, 25]
```
⎿ 함수 f를 ex의 각 요소에 맵핑(mapping)하라는 의미임

#### 1. 제너레이터의 사용
파이썬 3.x에선 반드시 **list**를 사용하여 리스트로 반환해야 하는 이유가 **제너레이터** 땜시.
<br> &emsp; ✔︎ 제너레이터 : 시퀀스 자료형의 데이터를 처리할 때 *실행 시점의 값을 생성*하여 *효율적으로 메모리를 관리* 할 수 있음

[list를 사용하지 않을 때는 이처럼 코딩 작성하기]
```python
>>> ex = [1, 2, 3, 4, 5]
>>> f = lambda x : x ** 2
>>> for value in map(f, ex) :
•••     print(value)
•••

#1, 4, 9, 16, 25
```
#### 2. 리스트 컴프리헨션과의 비교
: 굳이 람다 함수나 map()를 사용하지 않고 **리스트 컴프리헨션 기법**으로 얼마든지 같은 효과를 낼 수 있음

```python
ex = [1, 2, 3, 4, 5]
print([x ** 2 for x in ex])

#[1, 4, 9, 16, 25]
```
#### 3. 한 개 이상의 시퀀스 자료형 데이터의 처리
: 여러 개의 시퀀스 자료형 데이터를 입력값으로 사용할 있다는 점
```python
ex = [1, 2, 3, 4, 5]
f = lambda x, y : x + y
print(list(map(f, ex, ex)))

#[2, 4, 6, 8, 10]
```
```python
print([x + y for x, y in zip(ex, ex)])

#[2, 4, 6, 8, 10]
```

#### 4. 필터링 기능
- 리스트 컴프리헨션과의 차이점 : else문을 반드시 작성해 해당 경우가 존재하지 않는 경우를 지정해주어야 함
```python
#map()
print(list(map(lambda x : x ** 2 if x % 2 == 0 else x, ex)))

#리스트 컴프리헨션
print([x ** 2 if x % 2 == 0 else x for x in ex])

#[1, 4, 3, 16, 5]
```
### • reduce()함수
: 리스트와 같은 시퀀스 자료형에 차례대로 함수를 적용한 다음 모든 값을 통합시켜 주는 함수
```python
from functools import reduce
print(reduce(lambda x, y : x + y, [1, 2, 3, 4, 5]))

#15
```
이 함수가 어떻게 작동하는지 직관적으로 보기
```python
x = 0            #x+y를 계속 저장해주는 변수
for y in [1, 2, 3,4 ,5] :
    x += y       #y는 리스트값을 하나식 할당받는 변수

print(x)
```
- map()함수와의 차이점 : 리스트 변수의 모든 값을 **람다함수**로 적용해야 함

## 3️⃣ 별표의 활용
### 별표의 사용
: 곱하기 기호 (연산)
<br> : **여러 개의 변수가 함수에 한 번에 들어갈 수 있도록 처리**

* 파이썬 함수 속 별표(*) : 변수 앞에 붙어 여러ㅓ 개의 변수를 한 번에 넣을 수 잇는 컨테이너 역할을 함
<br> : **언패킹**하는 기능이 있음

```python
def asterisk_test(a, args) :
    print(a, *args)
    print(type(args))
asterisk_test(1, (2, 3, 4, 5, 6))

#1, 2, 3, 4, 5, 6
#<class 'tuple'>
```
⎿ 매개변수 args에 별표가 붙지 않음
<br>
⎿ 하지만 결과값이 저렇게 나온 이유는 **args** 때문임
<br> 이는 해당 변수를 **언패킹**한다는 의미

```python
>>> def asterisk_test(a, *args) :
        print(a, args)
        print(type(args))

>>> asterisk_test(1, *(2, 3, 4, 5, 6))

#1 (2, 3, 4, 5, 6)
#<class 'tuple'>
```
→ 함수 안의 별표나 함수 밖의 별표 모두 컨테이너값의 패킹과 언패킹을 다룬다는 측면에서 기본적으로 같은 목적으로 사용됨

* 튜플형을 언패킹할 때는 별표 하나만(*) 사용함
```python
a, b, c = ([1, 2], [3, 4], [5, 6])
print(a, b, c)
#[1, 2] [3, 4] [5, 6]

data = ([1, 2], [3, 4], [5, 6])
print(*data)
#[1, 2] [3, 4] [5, 6]
```

```python
for data in zip(*[[[1,2], [3, 4], [5, 6]]]) :
    print(data)
    print(type(data))

#(1, 3, 5)
#<class 'tuple'>
#(2, 4, 6)
#<class 'tuple'>
```

* 딕셔너리형을 언패킹할 때는 별표 두 개만(**) 사용함
```python
def asterisk_test(a, b, c, d) :
    print(a, b, c, d)

data = {"b": 1, "c" : 2, "d" : 3}
asterisk_test(10, **data)

#10 1 2 3
```
## 4️⃣ 선형대수학
### 백터와 행렬의 개념
1. 벡터(vector) : 크기와 방향을 모두 가진 것
<br> ⎿ in python) 3개 이상의 정보를 활용할 때..?

### 파이썬 스타일 코드로 표현한 벡터
* 기본적으로 리스트의 형태로 표현 (튜플, 딕셔너리로 표현 가능)
* 벡터의 연산 : 각 인덱스값이 같은 위치에 있는 값끼리 연산
```python
#좋은 코드가 아님 (간결X)
u = [2, 2]
v = [2, 3]
z = [3, 5]

result = []
for i in range(len(u)) :
    result.append(u[i]+ v[i]+ z[i])

print(result)
```
```python
u = [2, 2]
v = [2, 3]
z = [3, 5]

result = [sum(t) for t in zip(u, v, z)]
print(result)
```
* 별표를 사용한 함수화 : 4개 이상의 변수를 사용할 때
```python
def vector_addition(*args) :
    return [sum(t) for t in zip(*args)]

u = [2, 2]
v = [2, 3]
z = [3, 5]
print(vector_addition(u, v, z))
```
⎿ 위에 파이썬 코드 중 **[sum(t) for t in zip(u, v, z)]** 같은 효과를 낼 수 있음

* 스칼라 - 벡터 연산 : 분배 법칙 적용
```python
u = [1, 2, 3]
v = [4, 4, 4]
alpha = 2

result = [alpha * sum(t) for t in zip(u, v)]
print(result)
```
*******

2. 행렬(matirx)  : 1개 이상의 벡터 모임 (이차원 리스트)
<br> - m개의 행과 n개의 열
<br> - 행렬 a의 i행, j열의 값을 **a의 ij번째 값**이라고 함

![matrix](https://tcpschool.com/lectures/img_codingmath_25.png)

### 파이썬 스타일 코드로 표현한 행렬
: 기본적으로 리스트로 표현함 (튜플, 딕셔너리로 표현 가능)

* 행렬의 연산 : 가장 쉬운 표현 방법은 **별표(*)와 zip()**   
```python
matrix_a = [[3, 6], [4, 5]]
matrix_b = [[5, 8], [6, 7]]
result = [[sum(row) for row in zip(*t)] for t in zip(matrix_a, matrix_b)]
print(result)

#[[8, 14], [10, 12]]
```
* 행렬의 동치 : 2개의 행렬이 서로 같은지를 나타내는 표현 (A = B)
<br> &emsp; ✔︎ all() : 안에 있는 모든 값이 참일 경우에만 True -> and
<br> &emsp; ✔︎ any() : 하나라도 참이 있으면 True, 모두가 거짓일 때만 False -> or

```python
print(any([False, False, False]))
print(any([False, True, False]))
print(all([False, True, True]))
print(all([True, True, True]))
```

✖︎ 이 코드의 설명을 보아도 이해가 되지 않아요 !
```python
matrix_a = [[1, 1], [1, 1]]
matrix_b = [[1, 1], [1, 1]]
print(all([row[0] == value for t in zip(matrix_a, matrix_b) for row in zip(*t) for value in row]))
```

* 전치행렬 : 행과 열을 바꾸어 만든 행렬
<br> ⎿ 구현방법 : 별표(*)와 zip() 이용

```python
matrix_a = [[1, 2, 3,], [4, 5, 6]]
result = [[element for element in t] for t in zip(*matrix_a)]
print(result)
```

* 행렬의 곱셈 : 앞 행렬의 행과 뒤 행렬의 열을 선형 결합 (두 행렬의 크기가 같아야함)
<br> ⎿ 구현방법 : 전치행렬의 코드 기법 사용 (한 행렬 - 열의 값, 다른 행렬 - 행의 값 추출 후 곱하기)

```python
matrix_a = [[1, 1, 2], [2, 1, 1]]
matrix_b = [[1, 1], [2, 1], [1, 3]]
result = [[sum(a * b for a, b in zip(row_a, column_b)) for column_b in zip(*matrix_b)] for row_a in matrix_a]
print(result)
```