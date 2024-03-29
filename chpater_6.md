# ▶ CHAPTER 06 - 문자열
## 우리 할 수 있다능🫡
## 1️⃣ 문자열의 이해
### 문자열의 개념
#### 문자열 = 시퀸스 자료형
##### ● 시퀸스 자료형 : 리스트와 같이 데이터를 순차적으로 메모리에 저장하는 형식의 데이터

### 문자열과 메모리 공간
* 컴퓨터는 문자를 직접 인식 모태
* 문자를 숫자로 변환하여 인식
* 최소 단위= 1비트
* 1바이트 = 8비트
* 2의 8승의 크기 256까찌의 숫자 저장 가능

### 문자열의 인덱싱
: 글자 하나하나가 **상대적인 주소**를 가짐
```
 A  B  C  D  E      # 문자열
 0  1  2  3  4      # 상대적인 주소
-5 -4 -3 -2 -1      # 주소의 역순
```

### 문자열의 슬라이싱
문자열의 주소값을 이용해 문자열의 부분값을 추출해내는 기법
```
a = "abcde"
a[0:6]      # 0부터 5까지 
a[1:]       # 1부터 끝까지
a[::2]      # 두 글자씩 띄어서 출력
```

### 문자열의 연산
* (+) 연산 (단, "정수 + 문자"는 X)
* (*) 연산 (반복)

### 문자열 함수
| 함수명 | 기능 |
| :--- | :--- |
|len() |문자열의 **문자 개수**를 반환|
|upper()|**대문자**로 변환|
|lower()|**소문자**로 변환|
|tilte()|**각 단어의 앞글자만 대문자**로 변환|
|capitalize()|**첫 문자를 대문자**로 변환|
|count("찾을 문자열")|"찾을 문자열"이 **몇 개 들어있는지 개수** 변환|
|find("찾을 문자열")|"찾을 문자열"이 **왼쪽 끝**부터 시작하여 **몇 번쨰에 있는지** 반환|
|rfind("찾을 문자열")|"찾을 문자열"이 **오른쪽 끝**부터 시작하여 **몇 번째에 있는지** 반환|
|startswith("찾을 문자열")|"찾을 문자열"로 **시작하는지** 여부 반환|
|endswith("찾을 문자열")|"찾을 문자열"로 **끝나는지** 여부 반환|
|strip()|**좌우 공백** 삭제|
|rstrip()|**오른쪽 공백** 삭제|
|Istrip()|**왼쪽 공백** 삭제|
|split()|**문자열을** 공백이나 다른 문자로 **나누어 리스트로** 반환|
|isdigit()|**문자열이 숫자인지** 여부 반환|
|islower()|**문자열이 소문자인지** 여부 반환|
|isupper()|**문자열이 대문자인지** 여부 반환|

<br>

💡TIP(?)
* 아포스트로피(')가 문장에 들어가면 큰따옴표 사용하기
* 특수문자 기능

|특수문자|기능|특수문자|기능|
| :---: | :--- |:---: | :--- |
|\Enter|다음 줄과 연속임을 표현|\||문장자체 
|\'|'문자|\"|"문자|
|\b|백스페이스|\n|줄바꾸기|
|\t|Tab키|\e|Esc키|

## 3️⃣ 문자열 서식 지정
### 개념
특정 형식에 맞추어 결과값을 출력

《 장점 》
<br> 1. 데이터와 출력 형식을 분류할 수 있음
<br> 2. 데이터를 형식에 따라 다르게 표현할 수 있음

```python
print(1, 2, 3)
print("a" + " " + "b" + " " + "c")
print("%d %d %d" % (1, 2, 3)    # 차례대로 %에 대응
print("{} {} {}".format("a", "b", "c")))  # 차례대로 {}에 대응
```
### % 서식
#### '%자료형 %(값)'

```python
print("I eat %d apples." %3)
print("I eat %s apples." %"five")

#I eat 3 apples.
#I eat five apples.
```
* 변수 해당

|서식|설명|
| :---: | :---: |
|%s|문자열|
|%c|문자 1개|
|%d|정수|
|%f|실수|
|%o|8진수|
|%x|16진수|
|%%문자%자체||

### format()
#### "{자료형}.format(인수)"
##### %서식과의 차이점: 순서대로 변수가 할당됨
```python
age = 21; name = "Subin"
print("I'm {0} years old.".format(age))
print("My name s {0} and {1} years old.".foramt(name, age))
print("Product : {0}, Price per unit: {1:.2f}.format("Apple, 5.423))

#{1:.nf}의 의미: 실수형의 표현기법, 소수점 n번째 자리까지 출력 
```

### 패딩
여유 공간을 지정하여 글자 배열을 맞추ㅗ 소수점 자릿수를 맞춤

### %서식의 패딩
* print("%10d" % 12) -> **10자리 확보**와 **우측 정렬** 후 12 출력
* print("%-10d" % 12) -> **10자리 확보**와 **좌측 정렬** 후 12 출력
* print("%10.2f" % 5.9632) -> **10자리 확보**와 **우측 정렬**, **소수점 두 번째 자리**까지 출력

### format()함수의 패딩
* print("{0 :> 10s}.format("subin")) -> **10자리 확보**와 **우측 정렬** 후 subin 출력
* print("{0 :< 10s}.format("subin")) -> **10자리 확보**와 **좌측 정렬** 후 subin 출력
* print("{0 :> 10.5f}.format("subin", 1.023)) -> **10자리 확보**와 **우측 정렬**, **소수점 다섯 번째 자리**까지 출력

💡**네이밍(naming)**
<br> 변수명을 서식에 할당할 수 있는 기능
<br> : 특정 변수명을 사용하여 출력값을 직접 할당 가능
```python
print("Product: %(name)5s, Price per inot: %(price)5.5f." %{"name":"Apple", "price": 5.234})

print("Product: {name>:5s}, Price per inot: {price:5,5f}.".format(name = "Apple", price = 5.234))

#Product: Apple, Price: 5.23400.
```

내용 수정