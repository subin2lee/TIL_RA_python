# ▶ CHAPTER 12 - 예외 처리와 파일다루기
## 나 3주차인데.. 아직까지 맥북 모름, git 모름, python 모름
## 1️⃣ 예외 처리
### 예외의 개념과 사례
* 예외 : 프로그램을 개발하면서 예상하지 못한 상황이 발생하는 것
* 사례 : MS오피스 자동저장, 영어 입력을 한글 입력으로 등등..
----
### 예측 가능한 예외와 예측 불가능한 예외
* 예측 가능한 예외 : 발생 여부를 개발자가 사전에 인지할 수 있는 예외 - 대책 마련 가능

* 예측 불가능한 예외 
    * 발생 - 인터프리터가 자동으로 이것이 예외라고 사용자에게 알려줌
    <br> 프로그램이 종료되므로 적절한 조치를 해야 함 -> **예외 처리 구문**
----
### 예외 처리 구문
**[예외 처리가 중요한 이유]**
<br> : 프로그램도 일종의 제품이기 때문에 완성도를 높이는 중요한 개념임

#### (1) try-except문
```python
try : 
    예외 발생 가능한 코드
except 예외 타입 :
    예외 발생 시 실행되는 코드
```

```python 
for i in range(10) :
    try :
        print(10 / i)
    except ZeroDivisionError :
        print("Not divided by 0")
```
#### (2) try-except-else문
* 장점 : 에러가 발생하지 않을 경우의 수행문을 정의해 놓으면 에러가 발생하지 않는 경우에도 일어날 일을 사용자가 정확히 예측할 수 있음
    * 그런데 굳이 사용하지 않는 코드임 ㅎㅎ
```python
try : 
    예외 발생 가능한 코드
except 예외 타입 :
    예외 발생 시 실행되는 코드
else :
    예외가 발생하지 않을 때 실행되는 코드
```

```python
for i in range(10) :
    try :
        result = 10/i
    except ZeroDivisionError :
        print("Not divided by 0")
    else :
        print(10/i)
```
#### (3) try-except-finally문
* finally문 - 예외 발생 여부와 상관없이 반드시 실행되는 코드
```python
try : 
    예외 발생 가능한 코드
except 예외 타입 :
    예외 발생 시 실행되는 코드
finally :
    예외 발생 여부와 상관없이 실행되는 코드
```
```python
try :
    for i in range(1, 10) :
        result = 10//i
        print(result)
except ZeroDivisionError :
    print("Not divided by 0")
finally :
    print("종료되었숨다.")
```

#### (4) raise문
* 예외를 발생시키는 코드

> raise 예외 타입(예외 정보)

```python
while True :
    value = input("변횐할 정수값을 입력해 주세요: ")
    for digit in value :
        if digit not in "0123456789" :
            raise ValueError ("숫자값을 입력하지 않았습니다.")
    print("정수값으로 변환된 숫자-", int(value))
```
⌙ 에러 종류 : ValueError로 사용자가 입력을 잘못했을 대 입력이 잘못된 것을 알려주면서 종료 ^^b

#### (5) assert문
* 미리 알아야 할 예외 정보가 조건을 만족하지 않을 경우 예외를 발생
* 장점: 잘못된 입력 여부를 사전에 확인하여 나중에 필요없는 연산을 막아주어 다른 사람이 만든 코드를 사용하는데 좋은 가이드가 됨
> assert 예외 조건
```python
def get_binary_number(decimal_number) :
    assert isinstance(decimal_number, int)
    return bin(decimal_number)
print(get_binary_number(10))
print(get_binary_number(("10")))
```
⌙ isinstance() : 입력된 값이 다음에 나오는 클래스의 인스턴스인지를 확인하는 함수 (이게 무슨 소리인지 모르겟숨다..)
----
### 🍥 예외의 종류
|예외|내용|
|:---:|:---|
|IndexError|리스트의 인덱스 범위를 넘어갈 때|
|NameError|존재하지 않는 변수를 호출할 때|
|ZeroDivisionError|0으로 숫자를 나눌 때|
|ValueError|변환할 수 없는 문자나 숫자를 변화할 때|
|FileNotFoundError|존재하지 않는 파일을 호출할 때|

### 🍥 예외에 대한 에러 메세지
* 내장 예외와 함께 사용하기 좋음
```python 
for i in range(10) :
    try :
        print(10 / i)
    except ZeroDivisionError as e :
        print(e)
        print("Not divided by 0")

#division by zero
```
⌙ division by zero라는 에러 메세지로 특정한 에러를 빠르게 이해할 수 있음

## 2️⃣ 파일 다루기
### 파일의 개념
: 컴퓨터를 실행할 때 가장 기본이 되는 단위
<br> [프로그램을 실행하는 것 = 파일을 실행하는 것]

<br> 우리가 컴퓨터에 보이는 아이콘도 다 ~ 파일로 연결되어있다 이말이여 ~, 고냥 편하게 사용하고 싶어갖고 그렇게 만든거여 ~ 알긋냐잉 ~ ? (넹엄마.)

#### 파일과 디렉터리의 차이 
* 디렉터리 : 파일을 담는 또 하나의 파일로, 여러 파일을 포함할 수 있다.
<br> 직접 프로그램을 실행하지 않지만, 다른 파일들을 구분하고 논리적인 단위로 파일을 묶을 수 잇다.
----

### 파일의 종류
|바이너리 파일|텍스트 파일|
|:---|:---|
|컴퓨터만 이해할 수 있는 형태인 이진법 형식으로 저장|사람도 이해할 수 있는 문자열 혀식으로 저장|
|메모장X|메모장O|
|엑셀or워드|HTML, python 코드|

⭐️ 텍스트 파일도 **컴퓨터가 처리하기 위해 바이너리 형태로 저장된 파일**이라는 사실 !!

* 변경 기준 : 아스키코드(ASCII) or 유니코드(Unicode) - 인코딩

---

### 파일 읽기
* **open()** 함수 사용.
> f = open("파일명", "파일 열기 모드")
<br> f.close()

[ 파일 열기 모드 ]
|종류|설명|
|:---:|:---|
|r|읽기 모드 : 파일을 읽기만 할 때|
|w|쓰기 모드 : 파일에 내용을 쓸 때|
|a|추가 모드 : 파일의 마지막에 새로운 내용을 추가 할 때|

#### (1) 파일 읽기
```python
f = open("dream.txt", "r") #읽기모드 , 파일객체
contents = f.read() #contents변수에 문자열로 저장
print(contents) 
f.close   # 파일종료
```

⭐️ 이미 수정하고 있는 파일을 다른 프로그램에서 동시에 호출하면 에러가 발생함
<br> ⌙ **하나의 파이썬 프로그램이 하나의 파일을 사용할 때 사용을 완료하면 반드시 해당 파일을 종료해야 함**

#### (2) with문과 함께 사용하기
* 들여쓰기 동안 open()함수 유지, 끝나면 open()함수도 종료
```python
with open("dream.txt","r") as my_file :
    contents = my_file.rea()
    print(type(contents), contents
```

#### (3) 한 줄씩 읽어 리스트형으로 반환하기
* readlines()함수를 사용해 한 줄씩 내용을 읽어와 문자열 형태로 저장할 수 있음
* \n으로 나뉘어짐 
```python
with open("dream.txt","r") as my_file :
    content_list = my_file.readlines()
    print(type(content_list))
    print(content_list)
```
#### (4) 실행할 때마다 한 줄씩 읽어 오기
* 파일의 내용을 찾다가 중간에 멈춰야 할 필요가 있는 대용량 데이터는 아래와 같은 코드를 많이 사용함
```python
with open("dream.txt", "r") as my_file :
    i = 0
    while 1 :   #항상 수행
        line = my_file.readline()
        if not line :  #내용이 없으면 종료
            break
        print(str(i)+"==="+ line.replace("\n",""))
        i = i + 1
```
#### (5) 파일에 저장된 글자의 통계 정보 출력하기
* split()함수와 len()함수를 함께 사용함
```python
with open("dream.txt", "r") as my_file :
    contents = my_file.read()
    word_list = contents.split(" ")
    line_list = contents.split("\n")

print("총 글자의 수:", len(contents))
print("총 단어의 수:", len(word_list))
print("총 줄의 수:", len(line_list))
```
-----
### 파일 쓰기
* 인코딩 : 텍스트 파일을 저장하기 위해선 저장할 때 사용하는 표준을 지정해야 함.
<br> utf8을 일반적으로 많이 사용함.
<br> **운영체제나 파일의 사용 환경에 따라 다르게 설정해야 함**

```python
f = open("count_log.txt", "w", encoding = "utf8")
for i in range(1, 11) :
    data = "%번째 줄이다.\n"%i
    f.write(data)
f.close()
```

#### (1) 파일 열기 모드 a로 새로운 글 추가하기
* w(쓰기 모드) - 새로운 파일 생성
<br> w로 파일을 부르면 **기존 파일이 삭제되고 새로운 파일이 생겨 새로운 내용만 기록됨**

* 상황에 따라 계속 추가해주어야 할 때 **"a"(추가 모드)** 를 사용해주면 됨.

#### (2) 디렉터리 만들기
* **os모듈** 사용하기
    * **log** - 디렉터리 생성 코드
    * **os.path.isdir** - 기존 디렉터리의 존재 여부 확인
    <br> 없으면 "FileExistsError" 발생함

####  (3) 로그 파일 만들기
* 로그 파일 : 프로그램이 동작하는 동안 여러 가지 중간 기록을 저장하는 역할을 하는 파일
<br> (예시 - 외부 접속자의 접속 기록이나 접속 시간 등을 저장하는 파일)

```python
import os

if not os.path.isdir("log") :
    os.mkdir("log")

if not os.path.exists("log/count_log.txt") :
    f = open("log/count_log.txt", "w", encoding = "utf8")
    f.write("기록이 시작된다.\n")
    f.close()

with open("log/count_log.txt", "a", encoding = "utf8") as f :
    import random, datetime
    for i in range(1, 11) :
        stamp = str(datatime.datetime.now())
        value = random.random() * 1000000
        log_line = stamp + "\t" + str(value) + "값이 생성되었다." +"\n"
        f.write(log_line)
```
----
### pickle 모듈
* 영속화 : 필요한 객체를 파일로 저장시켜 다시 사용할 수 있도록 하는 것 
    * **pickle()** : 리스트에 들어간 데이터나 클래스의 오브젝트 등을 파일로 저장시켜 나중에 다시 사용할 수 있도록 해줌

**[pickle모듈을 사용하기 위해서]**
1.  객체를 저장할 수 있는 파일을 열고 저장하고자 하는 객체를 넘기면 됨
    * **wb** : 바이너리 파일로 저장됨
    * **dump(저장할 객체, 저장될 파일 객체)**

2. 저장된 pickle 파일을 불러오는 프로세스도 저장 프로세스와 같음
    * **rb** : 바이너리 형태로 읽음
    *  **load(해당 변수)** - 불러오기

3. 사용자가 직접 생성한 클래스도 저장함
