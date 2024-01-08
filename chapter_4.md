# ▶ CHAPTER 03 - 화면 입출력과 리스트
## 행복㉭Ł 하루ገト 되길 ~ ♧
(1) 조건문
- 코드를 짤 때, 고려할 점 !!
1. 어떤 기준으로 결정해야 하는가 ? -> **조건**의 설정
&emsp; 2. 언제까지 해야 하는가 ? -> **반복**의 설정
<br>
<br>
&emsp; a. 조건문의 개념
<br>
&emsp;&emsp; : **조건을 나타내는 기준** and **실행해야 할 명령**
<br>
&emsp;&emsp; ⭐ 반드시 **True** / **False**
<br>
<br>
&emsp; b. if - else문
```python
if <조건> :        #조건문이 무조건 콜롬(:) 붙이기
    <수행 명령 1>  #4칸 들여쓰기 (Tab사용)
    <수행 명령 2>
else :             #조건이 불일치할 경우 (생략해도 상관X)
    <수행 명령 a>
    <수행 명령 b>
```

<br>
&emsp; c. 조건의 판단

- 비교연산자

|비교연산자|비교상태|
| :---: | :--- |
|a < b|~보다 작다|
|a <= b|작거나 같다|
|a > b|~보다 크다|
|a >= b|크거나 같다|
|a == b|값이 같음|
|a is b|메모리 주소가 같음|
|a != b|값이 다름|
|a is not b 연산|메모리 주소가 다름|

- True와 False 치환
<br>
&emsp; └ **True = 1, False = 0**

- 논리 연산자

|논리연산자|설명|
| :---: | :--- |
|and|두 값이 **모두 참**일 경우 True, 아니면 False|
|or|두 값 중 **하나만 참**일 경우 True, 두 값 **모두 거짓**일 경우 False|
|not|**값을 역으로 반환**|

- if-elif-ekse문
<br>
&emsp; : 이를 사용하는 이유는 조건문에 만족함에도 불구하고 계속 돌아가서. 이를 막기 위헤
<hr>
(3) 반복문 (⭐핵심적으로 사용)
<br>
&emsp; a. for 

```python
for looper in [1, 2, 3, 4, 5]
    print("hello")
```
&emsp; └ 리스트의 값을 하나씩 가져와 looper라는 변수에 할당
> for qustn in range(**시작 번호 , 마지막 번호, 증가값**)

&emsp;💡알아두면 좋ㅇ느 거 !!
<br>
&emsp; 1️⃣ 반목문의 변수는 i, j, k로 지정
<br>
&emsp; 2️⃣ 대부분 0부터 반복
<br>
&emsp; 3️⃣ 잘못 작성시 무한 루프 발생 ..
<br>
<br>
&emsp; b. while문
<br>
&emsp;&emsp; : 어떤 조건이 만족하는 동안 수행, 거짓이면 더이상 수행X
<br>
<br>
&emsp;&emsp; <for문과 while문의 차이점>
|문법|반복횟수|
| :--- | :--- |
|for문|! 확실 !|
|while문|! 불확실 !|

<br>
&emsp; c. 반목문의 제어

- break문 : 반복을 종료하는 방법
- continue문 : 특정 조건은 뛰어넘고 다음 반복문을 수행하는 방법
- else문 : 어떤 조건이 완전히 끝났을 때 한번 더 실행하는 역할 (확인용, 굳이 사용X)
<br>
&emsp; 💡되도록 **제어 구문을 안 쓰기**
<hr>
(4) 코드의 오류를 처리하는 방법
<br>
&emsp; -> 디버그(debug) : 오류를 수정하는 과정
<br>
&emsp; -> 디버깅(debugging) : 잘못된 것을 찾아내고 고치는 것
<br>
<br>
&emsp; < 문법적 오류 >
<br>
&emsp; 1️⃣ 들여쓰기 오류 : IndentationError 
<br>
&emsp; 2️⃣ 오탈자로 인한 오류 : ValueError
<br>
&emsp; 3️⃣ 논리적 오류 : 코드는 제대로 작성했지만 원하는 결과 출력X
<br>
&emsp; -> 이를 해결하긴 위해선 ?!
<br>
&emsp;&emsp; ⅰ) 셸에서 실행하는 방법
<br>
&emsp;&emsp; ⅱ ) If __name__ == '__main__' &emsp;=>&emsp; 함수 안에 들어있지 않는 코드들을 작동되지 않게 하기 위해서 (권장X)
<br>
&emsp;&emsp; ⭐스스로 해결하기 (구글링이 체고다 ! gOod ~) 
