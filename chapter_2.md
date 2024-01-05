# ▶ CHAPTER 02 - 변수와 자료형
## 열심ㅎi ㅎrl보ㅈr구~ ㅠ^ㅠ 🥵

(1) 변수의 이해
```python
>>> professor = "Sungchul Choi"
>>> print(professor)
Sungchul Choi
>>> a = 7
>>> b = 5
>>> print(a + b)
12
>>> a = 7
>>> b = 5
>>> print('a + b')
a + b
```
&emsp;&emsp;⭐**print()** 함수 : 괄호 속 부분을 화면으로 **출력**

<hr>

&emsp; a. 변수와 값 &ensp;(위에 코드 쪼개서 분석하기?)
```python
>>> professor = "Sungchul Choi"
>>> print(professor)
Sungchul Choi
```
&emsp;&emsp; ▶ professor = "Sungchul Choi"
<br>
&emsp;&emsp;&emsp;&emsp;└ 의미 : ***professor라는 변수에 Sungchul Choi라는 값을 넣어라.**
<br>
&emsp;&emsp;&emsp;&emsp;└ 추가 설명(?) : 변수에 값을 넣는 과정 = 할당(assignment)
<br>
```python
>>> a = 7
>>> b = 5
>>> print(a + b)
12
>>> a = 7
>>> b = 5
>>> print("a + b")
a + b
```
&emsp;&emsp;⭐ print(a + b)와 print("a + b")의 차이점은 ?
<br>
&emsp;&emsp; : **" "** 의 차이 -> 문자열로 인식하기 때문에 **a + b** 그대로 출력됨
<br>

&emsp; b. 변수와 메모리
<br>
&emsp;&emsp; 프로그래밍 속 변수 = 어떠한 값을 저장하는 **장소**
<br>
&emsp;&emsp; 메모리(memory) = 변수에 값이 저장되는 **공간**
<br>
&emsp;&emsp; 메모리 주소 = 변수의 **저장 위치**
<br>
&emsp;&emsp;&emsp;&emsp; └ RAM (휘발성)
<br>
&emsp;⭐**변수에 들어가는 값은 반드시 어떠한 특정 메모리 주소를 갖게 됨**
<br>

&emsp;c.변수명 선언
* **알파벳, 숫자, 밑줄( _ )로 선언**해야함 **(단, 한글 사용X and 숫자로 시작X)**
* **변수명** 은 **의미 있는 단어**로 표기하면 좋음 (사람들 간의 의사소통을 위해서)
*  **대소문자 구분됨** (BUT 모든 변수명을 소문자로 하는 걸 추천드려용^V^)
*  **예약어**와 같은 특별한 의미가 있는 것은 **변수명으로 지정X**

<hr>

(2) 자료형과 기본 연산
<br>
&emsp; a. 메모리 공간
<br>
&emsp;&emsp; └ 변수를 메모리에 저장할 때 그 변수의 크기만큼 용량(공간)을 할당받음
<br>
&emsp;&emsp;  (컴퓨터는 이진수를 활용해 *이진수 한 자리 = 비트*)
<br>
&emsp;&emsp; (8개의 비트 = 1바이트, 1024바이트 = 1킬로바이트 ···)

<br>
&emsp; b. 기본 자료형
<br>
&emsp;&emsp; (ㄱ) 정수형 : 0, 1, 2, 3 
<br>
&emsp;&emsp; (ㄴ) 실수형 : 10.2, 9.8
<br>
&emsp;&emsp; (ㄷ) 문자형 : " " 또는 ' ' 안에 있으면 다 문자형 ㄷㄷ
<br>
&emsp;&emsp; (ㄹ) 불린형 : True 또는 False을 표현할 때
<br>
&emsp;&emsp; ♧ 동적 타이핑 : data = 8 자체로 선언 후 인터프리터가 알아서 판단

<br>
&emsp; c. 간단한 연산 

|연산자|기호|
| :---: | :---: |
|덧셈|+|
|뺄셈|-|
|곱셈|*|
|제곱|**|
|나눗셈|/|
|몫|//|
|나머지|%|
|증가 연산|+=|
|감소 연산|-=|
<hr>
(3) 자료형 변환 -> 실수형으로 정수형으로 바꿀 때 내림.
<br>
&emsp;&emsp; (ㄱ) 정수형 변환 : int()

```python
>>> a = 10.3
>>> b = int(a)
>>> print(b)
10
```
&emsp;&emsp; (ㄴ) 실수형 변환 : float()

```python
>>> a = 20
>>> b = float(a)
>>> print(b)
20.0
```
&emsp;&emsp; (ㄷ) 문자형 변환 : str()
<br>
&emsp;&emsp; ⭐**문자끼리의 합은 이어붙이기** (연산X)
<br>
&emsp;&emsp; ⭐**숫자와 문자끼리 연산 불가능**
```python
>>> a = 1
>>> b = 2
>>> i = str(a)
>>> j = str(b)
>>>print(i + j)
12
```
&emsp;&emsp; (ㄹ) 자료형 확인하기 : type()

```python
>>> a = int(10.3)
>>> type(a)
<class 'int'>
```