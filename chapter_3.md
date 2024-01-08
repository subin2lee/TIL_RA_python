# ▶ CHAPTER 03 - 화면 입출력과 리스트
## ㄴ.. レト락도 락ㅇi다..☆

(1) 파이썬 프로그래밍 환경
<br> 
&emsp; a. 사용자 인터페이스
<br>
- GUI(Graphical User Interface) - 아이콘을 하나 클릭하면 그에 대한 명령이 실행됨
<br>
- CLI(Command Line Interface) - 키보드만으로 명령을 입력하는 환경
<br>
&emsp; └ 윈도, 맥, 리눅스 등 모든 운영체제에서 기본적으로 지원함.
<hr>
(2) 화면 입출력
<br>
&emsp; a. 표준 입력 함수 : **input()함수**
<br>
&emsp;&emsp; └ 콘솔 창에서 입력을 받기 위해서 사용됨
<br>
&emsp;&emsp; └ 실행 될 때, 사용자가 입력할 수 있도록 대기 상태됨

```python
print('Enter your name: ')
somebody = input()
print('Hi', somebody, 'How are you today?)
```
&emsp; └ 입력 받은 값은 somebody 변수에 저장됨
<br>
&emsp; ⭐input()에 값을 입력 받으면, 그 값의 자료형은 **문자형**
<br>
<br>
&emsp; b. 표준 출력 함수 : **print()함수**

```python
>>> print('Hello World!', 'Hello Again!!!!')
Hello World! Hello Again!!!!
```
&emsp; └ 콤마(,) : +기호처럼 연결시켜줌 (**변수의 자료형 상관없이**)
<br>
&emsp; 🤔 **+기호**와의 차이점 : +기호는 문자형만 연결시켜줌
<hr>
(3) 리스트의 이해
<br>
&emsp; a. 리스트의 개념
<br>
&emsp;&emsp; └ 하나의 변수에 여러 값을 저장하는 변수형 =  **시퀀스자료형**
<br>
&emsp;&emsp; 💡시퀀스 자료형 = 여러 자료를 순서대로 넣음 (다양한 자료형 포함 가능)

```python
colors = ['red', 'blue', 'green']
```
&emsp; b. 인덱싱과 슬라이싱
<br>
<br>
&emsp;&emsp; 》 ( b - 1 ) **인덱싱(indexing)** : 리스트에 저장되어 있는 값에 접근하기 위해 이 값의 상대적인 주소를 사용하는 것.

```python
colors = ['red', 'blue', 'green']
           0️⃣     1️⃣      2️⃣
print(colors[0])
print(colors[2])
print(len(colors))
```
&emsp;&emsp; - 인덱싱은 0번째부터 ···
<br>
&emsp;&emsp; - len() : 리스트의 길이 = 리슽 안에 있는 값의 개수를 반환함
<br>
<br>
&emsp;&emsp; 》 ( b - 2 ) **슬라이싱(slicing)** : 리스트의 인덱스 기능을 사용하여 전체 리스트에서 일부를 잘라내어 사용하는 것
> 변수명[**시작 인덱스 : 마지막 인덱스**] 

&emsp; ⚠️ 마지막 인덱스의 의미(?) = **"마지막 인덱스 - 1"**

```python
>>> cities = ['서울', '부산', '인천', '대구', '대전', '광주', '울산', '수원']
>>> cities[0:5]
['서울', '부산', '인천', '대구', '대전']
>>> cities[5:]         #변수명[시작인덱스 : ] => 시작부터 끝까지
['광주', '울산', '수원']
```
<br>
&emsp;&emsp; 》 ( b - 3 ) **리버스 인덱스(reverse index)** : -1 부터 할당해 역순으로 올라가는 방식

```python
>>> cities = ['서울', '부산', '인천', '대구', '대전', '광주', '울산', '수원']
               -8      -7      -6      -5      -4      -3     -2      -1
>>> cities[-8:]
['서울', '부산', '인천', '대구', '대전', '광주', '울산', '수원']
```
<br>
&emsp;&emsp; 》 ( b - 4 ) **인덱스 범위를 넘어가는 슬라이싱(slicing with over index)**
<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; - 변수명[:] = 모든 변수의 값들이 반환됨
<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; - 범위가 넘어가도 최대 범위로 지정함
<br>
<br>
&emsp;&emsp; 》 ( b - 5 ) **증가값(step)** 

>변수명[시작 인덱스:마지막 인덱스:**증가값**]

&emsp;&emsp; - 변수명[::증가값] -> 증가값 단위로 
&emsp;&emsp; - 변수명[::리버스] -> 역으로 슬라이싱
<hr>
(4) 리스트의 연산

- 덧셈 연산 : 두 변수를 합쳐져 각각의 리스트가 하나의 리스트로 !
```python
>>> color1 = ['red', 'blue', 'yellow']
>>> color2 = ['orange', 'black', 'white']
>>> print(color1 + color2)
['red', 'blue', 'yellow', 'orange', 'black', 'white']
```
- 곱셈 연산 : 리스트에 n을 곱했을 때 해당 리스트를 n배만큼 늘려줌
```python
>>> color1 * 2
['red', 'blue', 'yellow', 'red', 'blue', 'yellow']
```
- in 연산 : 포함 여부를 확인하는 연산
```python
>>> 'blue' in color2
False
```
- 리스트 추가 및 삭제

|함수|기능|
| :---: | :--- |
|append()|새로운 값을 기존 리스트의 맨 끝에 추가|
|extend()|새로운 리스트를 기존 리스트에 추가 (덧셈연산)|
|insert(i, 값)|기존 리스트의 i번째 인덱스에 새로운 값을 추가, i번째 인덱스를 기준으로 뒤쪽의 인덱스는 하나씩 밀림|
|remove()|리스트 내의 특정 값을 삭제|
|del|특정 인덱스값 삭제|

- 패킹 : 한 변수에 여러 개의 데이터를 할당
- 언패킹 : 패킹 되어 있을 때, 그것을 각각의 변수로 반환
```python
>>> t = [1, 2, 3,]  #패킹
>>> a, b, c = t     #언패킹
>>> print(t, a, b, c)
[1, 2, 3]1 2 3
```
- ⭐이차원 리스트 : 여러 개의 리스트를 하나의 변수에 할당
```python
>>>print(midterm_score[0][2])
                       행 열
```
<hr>
(5) 리스트의 메모리 관리 방식
🥵 파이썬은 리스트를 저장할 때 갑 자체가 아닌 값이 위치한  [메모리주소]를 저장함.
<br>
&emsp; a. 리스트의 개념
<br>
&emsp; ☞ == 은 값*을 비교하는 연산
<br>
&emsp; ☞ is 은 메모리주소를 비교하는 연산
<br>
&emsp;&emsp;&emsp; -> 5 ~ 256까지는 특정 메모리 주소에 저장
<br>
<br>

&emsp; b. 메모리 저장 구조로 인한 리스트의 특징
<br>
&emsp; └ ⭐ **하나의 리스트에 다양한 자료형 포함 가능**
<br>
&emsp; └ ⭐⭐**리스트의 저장 방식**⭐⭐
```python
>>> a = [5, 4, 3, 2, 1]
>>> b = [1, 2, 3, 4, 5]
>>> b = a
>>> print(b)
[5, 4, 3, 2, 1]
```
```python
>>> a.sort()
>>> print(b)
[1, 2, 3, 4, 5]
```
&emsp; **Q. a만 정렬하였는데 b도 정렬된 이유는 ?**
<br>
&emsp; **A. b = a를 입력한 순간 b에 a의 메모리 주소가 저장되어서**
<br>
<br>
&emsp; 『어떤 리스트값을 하나의 변수에 **할당하는 순간** 두 변수는 **같은 메모리 주소를 할당**받음』
