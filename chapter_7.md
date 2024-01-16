# ▶ CHAPTER 07 - 자료구조
## 이걸 레알레알마드리드 난제다;;
## 1️⃣ 자료구조의 이해
### ☛ 자료구조의 개념
#### 자료구조(data structure) - 데이터의 특징을 반영하여 저장하는 방식
* 특징이 있는 정보를 메모리에 효율적으로 저장/반환하는 방법으로 데이터를 관리하는 방식
* 대용량이면, 메모리에 빨리 저장하고 검색함 (효율적으로 사용해야 실행 시간↓)

### ☛ 파이썬에서의 자료구조

|자료구조명|특징|
|:---:|:---|
|스택(stack)|나중에 들어온 값이 먼저 나감|
|큐(queue)|먼저 들어온 값이 먼저 나감|
|튜플(tuple)|리스트와 같지만 데이터의 변경 허용X|
|세트(set)|데이터 중복X, 수학의 집합 연산을 지원|
|딕셔너리(dictionary)|key와 value의 형태로 데이터 저장 (key값은 다른 데이터와 중복 허용X)|
|collections 묘듈|여러 자료구조를 효율적으로 사용할 수 있도록 지원하는 파이썬 내장모듈|

## 2️⃣스택과 큐
### ☛ 스택
#### 마지막에 들어간 데이터가 가장 먼저 나오는 형태 (Last In First Out)

☆ .append() -> push(데이터 저장), .pop() -> pop(데이터 추출) 

![stack](https://velog.velcdn.com/images/youngsik823/post/980bfb26-3a8d-4593-9343-3e3cf860d9a4/image.png)

```python
>>> a = [1, 2, 3, 4 ,5]
>>> a.append(10)     #데이터 저장
>>> a
[1, 2, 3, 4 ,5, 10]
>>> a.pop()          #데이터 추출
10
```

```python
word = input("Input a word: ")
world_list = list(word)
print(world_list)

result= []
for _ in irange(len(world_list)) : #_기호가 있으면 해당 반복문에서 생성되는 값은 코드에서 사용하지 않음
    result.append(world_list.pop()) #world_list를 추출하면서 result라는 빈 리스트에 추가하기 !

print(result)
print(word[::-1])

#Input a word : PYTHON
#['P', 'Y', 'T', 'H', 'O', 'N']
#['N', 'O', 'H', 'T', 'Y', 'P']
#NOHTYP
```

### ☛ 큐
#### 먼저 들어간 데이터가 먼저 나옴 (Fist in First Out)

![queue](https://s3.stackabuse.com/media/articles/guide-to-queues-in-python-1.png)

```python
>>> a = [1, 2, 3, 4, 5]
>>> a.append(10)   # a = [1, 2, 3, 4, 5, 10]
>>> a.pop(0)       #맨 처음(인데스 0번째)값을 가져온다
1
>>> a.pop(0)
2
```

## 3️⃣ 튜플과 세트
### ☛ 튜플
#### 여러 자료를 순서대로 넣음 - 리스트 개념 & 값을 변경하는 것이 불가능함
##### 시퀀스 자료형 : 여러 데이터를 하나의 변수에 저장하는 기법

```python
>>> t = (1, 2, 3)
>>> print(t + t , t * 2)
(1, 2, 3, 1, 2 ,3)(1, 2, 3, 1, 2, 3)
>>> len(t)
3
```

➢ 튜플을 선언 할 때 -> **()** 이용
<br➢ 연산, 인덱싱, 슬랑이싱 모두 동일

<br>

⭐️ **튜플의 값은 마음대로 변결할 수 없다 !!**
```python
>>> t= [1]
#오류발생, 오류발생 🚨 -> 튜플 오브젝트에는 새로운 아이템 할당 허용X
```
⭐️ **콤마(,)를 붙여 t가 튜플임을 선언해야 함**
<br>

⌜튜플 사용해야하는 경우⌟
<br> : 주민번호와 같은 사용하는 사람이 마음대로 데이터를 바꾸지 말아야 할 때

### ☛ 세트
#### 값을 순서 없이 저장하지만 중복 허용X
```python
>>> s = set([1, 2, 3, 1, 2, 3])
>>> s
{1, 2, 3}
>>> s.add(1)    
s
{1, 2, 3}      # add를 사용하였지만 중복을 허용하지 않기에 추가되지 않음
>>> s.remove(1)
>>> s
{2, 3}
>>> s.update([1, 4, 5, 6, 7])
>>> s
{1, 2, 3, 4, 5, 6, 7}
>>> s.discard(3)
>>> s
{1, 2, 4, 5, 6, 7}
>>> s.clrat()
>>> s
set()
```
→ 원소 하나 추가 add(), 원소 하나 제거 remove() or discard(), 새로운 리스트 추가 update(), 모든 변수를 지움 clear()
<br> ⭐️ **값은 모두 순서 없이 저장되는 동시에 중복을 제거하고 저장됨**

#### • 집합 연산

|연산|함수|기호|의미|
|:--:|:--:|:---:|:---|
|합집합|union|\||두 집합의 중복값을 제거하고 합치는 연산|
|교집합|intersection|&|두 집합 양쪽에 모두 포함된 값만 추출하는 연산|
|차집합|difference|-|s1의 원소 중 s2에 포함된 원소를 제거하는 연산|

## 4️⃣ 딕셔너리
#### 데이터의 유일한 구분자 - key, 실제 데이터 - value
#### (색인 - 데이터를 찾기 쉽도록 구분해 놓은 유일한 정보, 단어를 검색하는 방식)

### ☛ 파이썬에서의 딕셔러니
> 딕셔너리 변수 ={키1:값1, 키2:값2, 키3:값3, •••}

⭐️ **다양한 자료형이 들어갈 수 잇음 !!**
<br> ⎿ 리스트처럼 한 번에 여러 데이터를 입력 or 튜플/세트와 같은 데이터 사용 가능

```python
#선언 방법
>>> student_info = {20230101: "Subin", 20231098: "the8", 202320021: "Seungyeon"}    

#해당변수의 특정 값 호출 -> [] 대괄호 안에 키 넣기
>>> student_info[20230101]    
"Subin"

#재할당과 데이터 추가 (리스트와 같음)
>>> student_info[20230101] = "shibam"
>>> student_info[20234876] = "Kangin"
>>> student_info
{20230101: "shibam", 20231098: "the8", 20230021: "Seungyeon", 20234876: "Kangin"}
```
특정 값 호출 시 **변수의 자료형을 모르고 호출하면** 리스트로 오해할 수 있음

### ☛ 딕셔너리 함수
```python
>>> country_code = {}
>>> country_code = {"America": 1, "Korea": 82, "China": 86, "Japan": 81}
>>> country_code
{"America": 1, "Korea": 82, "China": 86, "Japan": 81}
```
1. key(키)만 출력할 때 -> keys()함수
![Alt text](image.png)

2. value(값)만 출력할 때 -> values()함수
![Alt text](image-1.png)

3. 키-값 쌍을 모두 보여줄 때 -> items()함수
![Alt text](image-2.png)

<for문과 if문과 함께 쓰일 떄>
* for문 
![Alt text](image-3.png)

* if문 - 해당 변수 안에 특정 키나 값이 있는지 확인할 때
![Alt text](image-4.png)

## 5️⃣ collections 모듈 <br>(작성자의 이해력 문제로.. 난관에 봉착했다는 사실)
#### 기존에 배웠던 자료구조보다 효율적이고 편리함

### ☛ deque 모듈
: 스택과 큐를 모두 지원하는 묘듈
```python
>>> from collections import deque
>>>
>>> deque_list =  deque()
>>> for i in range(5) :
•••     deque_list.append(i)
•••
>>> print(deque_list)
deque([0,1 ,2 ,3 4])
```
* 스택처럼 표현하는 방법
```python
>>> deque_list.pop()
4
>>> deque_list.pop()
3
>>> deque_list.pop()
2
>>> deque_list
deque([0, 1])
```
* 큐처럼 표현하는 방법 - pop(0)은 실행X
<br> **appendleft()함수 사용**

```python
>>> from collections import deque
>>> 
>>> deque_list = deque()
>>> for i in rangge(5) :
•••     deque_list.appendleft(i)
•••
>>> print(deque_list)
deque([4, 3, 2, 1, 0])
```

* 장점(이믕데이짜식아)
<br> 연결 리스트(linked list)의 특성을 지원한다.
<br> &emsp;&emsp; ⎿ 연결 리스트가 뭉디 ?
<br> &emsp;&emsp;&emsp; : 데이터 저장 시 요소의 값을 한 쪽으로 연결한 후, 요소 다음 값의 주소값을 저장하는 기법
<br> &emsp;&emsp; ⎿ 원형으로 데이터를 저장할 수 있음
* **rotate()** - 기존 deque에 저장된 요소들 값의 인덱스를 바꾸는 기법
<br> ⎿ 각 요소의 인덱스 번호를 하나씩 옮긴다면 실제로 요소를 옮기지 않더라도 인덱스 번호를 바꿀 수 있음

```python
>>> from collections import deque
>>>
>>> deque_list = deque()
>>> for i in range(5) :
•••     deque_list.append(i)
•••
>>> print(deque_list)
deque([0, 1, 2, 3, 4])
>>> deque_list.rotate(2)
deque([3, 4, 0, 1, 2])
>>> deque_list.rotate(2)
>>> print(deque_list)
deque([1, 2, 3, 4, 0])
```

* **reversed()함수** - 반대로 데이터 저장
```python
>>> print(deque(reversed(deque_list)))
deque([0, 4, 3, 2, 1])
```

* **extend()** or **extendleft()**
```python
>>> deque_list.extend([5, 6, 7])
>>> print(deque_list)
deque([1, 2, 3, 4, 0, 5, 6, 7])
>>> deque_list.extendleft([5, 6, 7])
>>> print(deque_list)
deque([7, 6, 5, 1, 2, 3, 4, 0, 5, 6, 7])
```

* 메모리의 효쥴적 사용과 빠른 속도라서 유용함 - 데이터를 효율적으로 저장하고 삭제 가능

### ☛ OrderedDict 모듈
: 순서를 가진 딕셔너리 객체

```python
from collections import OrderedDict

d = OrderedDict()
d['x'] = 100
d['y'] = 200
d['z'] = 300
d['l'] = 500

# x 100
# y 200
# z 300
# l 500
```
* x, y, z, l의 순서대로 키-값 쌍이 출력됨
* 딕셔너리로 데이터 처리 시 키나 값을 데이터를 정렬할 때 많이 사용됨

### ☛ defaultdict 모듈
: 딕셔너리의 변수를 생성할 때 키에 기본값을 지정하는 방식
```python
from collections import defaultdict

d = defaultdict(lamda: 0)  #defaultdict 모듈을 선언하면서 동시에 초깃값을 0으로 설정
                           #lamda는 return 0이라고 생각하면 돼
print(d["first"])

# 0
```
```python
from collections import defaultdict

s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4), ('red', 1)]
d = defaultdicit(list)

for k, v in s:
    d[k].append(v)

print(d.items())
[('blue', [2, 4]), ('red', [1]), ('yellow', [1, 3])]

#dict_items([('yellow', [1, 3]), ('blue', [2, 4]), ('red', [1])])
```
* d를 defaultdict 타입으로 선언하면서 초깃값을 리스트로 선언
* 중요한 것 : 변수 d는 deafultdict 타입이면서 list가 초깃값으로 선언되었기 때문에 새로운 키 값이 없더라도 별도로 오류 발생X

### ☛ Counter 모듈
: 시퀀스 자료형의 데이터 값의 개수를 딕셔너리 형태로 반환하는 방법
(리스트나 문자열과 같은 시퀸스 자료형에 저장된 요소 중에서 같은 값이 몇 개 있는지 그 개수를 반환 -> .count() 상위버전...?)
```python
>>> from collections import Counter
>>> 
>>> text = list('gallahad')
>>> text
['g', 'a', 'l', 'l', 'a', 'h', 'a', 'd']
>>> c = Counter(text)
>>> c
Counter({'a': 3, 'l': 2, 'g': 1, 'h': 1, 'd': 1})
>>> c["a"]
3
```
* 딕셔너리 형태나 키워드 형태의 매개변수를 사용하여 Counter를 생성할 수 있음

< Counter 객체를 생성하는 방법 >
* element()함수를 사용히여 각 요소의 개수만큼 리스트형의 결과를 출력하였음
```python
>>> from collections import Counter
>>>
>>> c = Counter({'red': 4, 'blue': 2})
>>> print(list(c.elements()))
['red', 'red', 'red', 'red', 'blue', 'blue']
```

* 매개변수를 사용하여 Counter를 생성하는 방법 (key, value)
```python
>>> from collections import Counter
>>>
>>> c = Counter(cats = s, dogs = 8)
>>> print(c)
Counter({'dogs': 8, 'cats': 4})
>>> print(list(c.elements()))
['cats', 'cats', 'cats', 'cats', 'dogs', 'dogs', 'dogs', 'dogs', 'dogs','dogs', 'dogs', 'dogs']
```

* 사칙연산 지원
<br> ⎿ **.subtract()** -> 차를 구하는 함수
<br> ⎿ **+** -> 두 Counter 객체에 있는 각 요소를 더한 것
<br> ⎿ **&** -> 두 객체에 같은 값이 있을 때(교집합인 경우)
<br> ⎿ **|** -> 두 Counter 객체에서 하나가 포함되어 있다면, 그리고 좀 더 큰 값이 있다면 그 값으로 합집합을 적용
```python
>> from collections import Counter
>>>
>>> c = Counter(a = 4, b = 2, c = 0, d = -2)
>>> d = Counter(a = 1, b = 2, c = 3, d = 4)
c.subtract(d)         # c - d
>>> c
Counter({'a': 3, 'b': 0, 'c': -3, 'd': -6})
```

### ☛ Counter 모듈
: 튜플의 형태로 데이터 구조체를 저장하는 방법
<br> : 내가 만든 리스트를 다른 사람도 쉽게 사용할 수 있도록 해주는 자료구조

[좌표 평면에서의 점의 위치 찾는 코드]
```python
>>> from collections import namedtuple
>>>
>>> Point = namedtuple('Point', ['x', 'y']) #객체이름 - Point, 저장요소 - x, y  
>>> p = Point(11, y = 22)
>>> p
Point(x=11, y=22)
>>p.x, p.y
(11, 22)
>>> print(p[0] + p[1])
33
```
**☆p 변수에 저장된 값을 호출하는 방법**
<br> 첫째 - 요소의 이름을 그대로 사용하는 방법
<br> 둘째 - 인덱스를 사용하는 방법 (들어간 순서대로 값이 저장됨)
<br> ⎿ 덧셈 연산이나 언패킹 연산 모두 가능