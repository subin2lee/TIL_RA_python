# ▶ CHAPTER 05 - 함수
## 용용 죽겟지0ω0。。。💀
### [쉬어가는 TIME]
여러 명이 프로그램을 함께 개발할 때, 코드를 어떻게 해야하묘 ?
<br>
▶ **가장 잘하는 사람이 혼자 작성하기**
<br>
<br>
**_하지만_** 우리가 **_필요한 부분을 나우어 작성하고 합치는 것_** 이 일반적이고... many many 사용해용 ~
<hr> 

## 1️⃣ 함수 기초
### **함수(function)** : 코드 덩어리 or 코드의 묶음
&emsp; ☞ 장점
<br>
&emsp;&emsp; 1. **필요할 떄마다 호출 가능** - 같은 작업을 여러 번 반복X
<br>
&emsp;&emsp; 2. **논리적인 단위로 분할** 가능
<br>
&emsp;&emsp; 3. **코드의 캡슐화** - 인터페이스 잘 정의하기
<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; └ 입력값과 출력값을 명확히 한다는 것 !
<br>
<br>

&emsp; **《선언하는 방법》**
```python
def 함수 이름 (매개변수) : 
    명령문 1
    명령문 2
    return <반환값>
```
* **def**로 시작 and **콜론(:)** 꼭 찍어주기
* 함수 이름은 **소문자**와 **'_'** 사용하기 -> **짧고 명료하게 !!**
* 매개변수 : 함수에 입력값으로 사용하는 변수 (1개 이상)
* 명령문 : 무조건 **들여쓰기** 
* return : 값을 반환
<hr>

### 함수의 실행 순서
```python
def calculate_retangular_area(x, y) : # 3
    return x * y   # 4

rectangle_x = 10
rectangle_y = 20
print("사각형 x의 길이:", rectangel_x) # 1
print("사각형 y의 길이:", rectangel_y) # 2

print("사각형의 넓이:", calculate_retangular_area(rectangle_x, rectangle_y))    # 5
```
- 수학에서의 함수와 비슷해yo !

### 함수의 형태
▶ 매개변수 X, 반환값 X : 함수 내부 명령문만 수행
```python
def a_rectangle_area() :
    print(5 * 7)

a_rectangle_area()
# 35

#함수 자체의 반환값은 없기에 none 값을 가짐
```

▶ 매개변수 O, 반환값 X : 매개변수를 사용하여 명령문만 수행
```python
def b_rectangle_area(x, y) :
    print(x * y)

b_rectangle_area(5, 7)  # -> 이거 자체가 치환된 것은 아님
# 35

#함수 자체의 반환값은 없기에 none 값을 가짐
```

▶ 매개변수 X, 반환값 O : 매개변수 없이 명령문을 수행한 후 결과값 반환
```python
def c_rectangle_area() :
    return(5 * 7)

print(c_rectangle_area())
# 35
```

▶ 매개변수 O, 반환값 O : 매개변수를 사용하여 명령문을 수행한 후 결과값 반환
```python
def d_rectangle_area(x, y) :
    return(x * y)

print(d_rectangle_area(5, 7))
# 35
```

## 2️⃣ 함수 심화
### 호출방식 -> ㄹㅇ 이해가 않 되..
* 값에 의한 호출 (call by value)
<br>
: 함수에 인수를 넘길 때 **값**만 넘김
<br>
: 함수 내부의 인수값 변경 시 **호출된 변수에 영향을 주지 않음**

* 참조 호출 (call by reference)
<br>
: 함수에 인술르 넘길 때 **메모리 주소**를 넘김
<br>
: 함수 내부의 인수값 변경 시 **호출된 변수값도 변경됨**

* 객체 호출 (call by object reference)
<br>
: 객체의 주소가 함수로 넘어감
```python
def spam(eggs) :    #eggs을 수학의 x라고 생각하기   
    eggs.append(1)
    eggs = [2, 3]   #여기 eggs와 매개변수의 eggs가 다름

ham = [0]           
spam(ham)           #ham은 egss(수학의 x)에 대립해주었다고 생각하면 될 듯(?)
print(ham)

# [0, 1]
```
#### 변수의 사용 범위
* **지역 변수** : 함수 내부에서만 사용 (함수 안에 있는 변수)
* **전역 변수** : 프로그램 전체에서 사용 (함수 밖에 있는 변수)

&emsp;&emsp; 💀 변수의 이름만 같지, 다른 **메모리 주소**를 가지고 있음

```python
def f() :
    s = "I love London!" # 지역 변수
    print(s)             # 지역 변수 s가 출력됨

s = "I love Paris!"      # 전역 변수
f()
print(s)                 # 전역 변수 s가 출력됨
```

💡 같은 메모리 주솔르 갖고 있는 변수로 사용하기 위해선 **global** 키워드를 사용함.
```python
def f() :
    global s
    s = "I love London!"   # global을 사용함으로써 지역 변수 s가 전역 변수로 선언됨
    print(s)             

s = "I love Paris!"      
f()
print(s)                 
```
### 재귀함수
: 자기 자신을 다시 호출하는 함수
<br> [기본구조] 
<br> 종료조건, 단계별 반환

## 3️⃣ 함수의 인수
### ⓐ 키워드 인수
: 함수에 입력되는 매개변수의 변수명을 사용하여 함수의 인수를 지정하는 방법
```python
def print_something(my_name, your_name) :
    print("Hello {0}, My name is {1}".format(your_name, my_name))

print_something("Sungchul", "TEAMLAB")     # 순서대로 입력

# 변수명만 정확히 기재되면 순서 상관없이 원하는 변수에 인수를 넣을 수 있음
print_something(your_name = "TEAMLAB", my_name = "Sungchul") 
```
### ⓑ 디폴트 인수
: 매개변수에 **기본값** 설정
<br> 
(아무런 값도 인수로 넘어가지 않을 때 지정된 기본값을 사용하는 방식)

```python
def print_something_2(my_name, your_name = "Shibam") :  # your_name에 Shibam이라는 기본값 지정
    print("Hello {0}, My name is {1}".format(your_name, my_name))

print_something_2("Subin", "Shibam")

# 이걸 출력해도 기본값이 지정되어 있어서 위에 행과 똑같은 결과값이 나옴
print_something_2("Subin") 
```

### ⓒ 가변 인수
: 함수의 매개변수 개수를 지정하지 않았을 때 ( __*__ 를 사용함)
```python
def asterisk_test(a, b, *args) : # *args에 나머지 숫자들이 들어가있음
    return a + b + sum(args)

print(asterisk_test(1, 2, 3, 4, 5))
```
#### 결과값은 괄호에 묶여 출력 (튜플형)
```python
def asterisk_test_2 (*args) :
    x, y, *z = args  # *z는 나머지 값들을 리스트로 받음
    return x, y, z

print(asterisk_test_2(3, 4, 5))

# (3, 4, [5])
```
### ⓓ 키워드 가변 인수
: 가변 인수의 단점인 변수의 이름을 저장할 수 없는 걸 보완해줌 (__**__ 사용함)
<br> ☞ 입력값은 **딕셔너리 자료형** 으로 사용할 수 잇음

###### 딕셔너리 자료형 : 변수와 값을 쌍으로 저장하는 방식
```python
def kwargs_test(**kwargs) :
    print(kwargs)
    print("First valu is {first}".format(**kwargs))   # 개별 변수명을 따로 불러서 사용 가능혀 ~
    print("Second value is {second}".format(**kwargs))
    print("Third value is {third}".format(**kwargs))

kwargs_test(first = 3, second = 4, third = 5)

#딕셔너리 자료형 변수에 **를 사용해서 개별 변수로 풀리면서 함수에 들어감
```

## 4️⃣ 좋은 코드를 작성하는 방법
### 좋은 코드의 의미
다른 사람들이 내가 작성한 코드를 쉽게 이해할 수 있는 거 !

### 코딩 규칙
ⅰ) 들여쓰기 4스페이스 (tab사용)
<br>ⅱ) 한 줄에 최대 79자까지
<br> ⅲ) 불필요한 공백 없애기
<br> ⅳ) = 연산자는 1칸 이상 띄우지 않기
<br> ⅴ) 주석은 항상 갱신하고 불필요한 주석 삭제하기
<br> ⅵ) 소문자l , 대문자O, 대문자I 구분하기 어려우니 사용금지
<br> ⅶ) 함수명은 소문자로 구성, 필요하면 밑줄로
<br> 등등😐

### 함수 개발 가이드라인
* 함수이름 : 함수의 역할과 의도가 명확하게 드러나면서 **짧게**
* 함수역할 : 한 가지 역할을 **명확하게**
* 함수를 만들어야 하는 경우 : 공통으로 사용되는 코드이고, 복잡한 로직이 사용돼 식별 가능하는게 해야 할 때
