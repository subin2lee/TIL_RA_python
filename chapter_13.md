# ▶ CHAPTER 13 - CSV와 로그 관리
## 린가드 서울fc옴 ㅋㅋ, 그는 외 여기까지.. 나락을 갓나..🤟 기릿.

## 1️⃣ CSV
콤마(,)를 기준으로 나누어진 값
<br> 모든 자료형을 포함하는 것
<br> 엑셀 형태의 데이터 → 텍스트 형태

```python
연도, 제조사, 모델, 설명, 가격
1997, Ford, E350, "ac, abs, moon", 3000.00
1999, Chevy, "Venture ""Extended Edition""", "", 4900.00
```
* 제일 상단 - **필드, 헤더, 열 이름** (텍스트 데이가 이렵됨)
* 그 밑부터 - **한 줄의 데이터 = 하나의 객체** (필드의 실제 데이터가 있음)

## 2️⃣ CSV 파일 만들기
1. 소스파일에서 파일을 작업 폴더로 이동시키기
2. 엑셀에서 1번에서 만든 파일을 열기
3. 메뉴 바에서 [파일] - [다른 이름으로 저장]을 선택하기
4. [다른 이름으로 저장] 대화상자에서 '파일 형식'을 'CSV'로 선택 후 [저장] 버튼을 클릭하기
5. 엑셀을 종료한 후 메모장에서 파일을 열기

## 3️⃣ CSV 파일 다루기
### (1) 파일 객체
일반적인 텍스트 파일을 퍼리하듯 파일을 읽어온 후 한 줄씩 데이터를 처리함

```python
line_counter = 0            # 파일의 총 줄 수를 세는 변수
data_header = []            # 데이터의 필드값을 저장하는 리스트
customer_list = []          # customer의 개별 리스트를 저장하는 리스트

with open("customers.csv") as customer_data :
                            # customer.csv 파일을 customer_data 객체에 저장
    while 1 :
        data = customer_data.readline() # customer.csv의 데이터 변수에 한 줄씩 저장
        if not data: break              # 데이터가 없을 때 반복문 종료
        if line_counter == 0 :          # 첫 번째 데이터는 데이터의 필드
            data_header = data.split(",")   #데이터의 필드는 data_header 리스트에 저장, 데이터 저장 시 "," 분리
        else :
            customer_list.append(data.split(","))   # 일반 데이터는 customer_list 객체 저장, 데이터 저장 시 ","로 분리
        line_counter += 1

print("Header:", data_header)       # 데이터 필드값 출력
for i in range(0, 10) :             # 데이터 출력(샘플 10개만)
    print("Data", i, ":", customer_list[i])
print(len(customer_list))           # 전체 데이터 크기 출력
```
→ 직관적으로 이해할 수 있는 매우 쉬운 구조
<br> → 열 이름을 키의 값으로 한 딕셔러니형으로 처리할 수 있음
<hr>

### (2) csv 객체
기본적으로 파일 객체가 아닌 csv 객체를 이용하여 csv 파일 형태의 데이터를 다룰 수 있음

```python
import csv
f = open("./korea_floatinf_population_data.csv", "r")
reader = csv.reader(
    f,                  # 연결할 대상 파일 객페
    delimiter = ",",    # 데이터를 분리하는 기준
    quotechar = "",     # 데이터를 묶을 때 사용하는 문자
    quoting = csv.QUOTE_ALL)    # 데이터를 묶는 기준
```
* QUOTE_ALL: 모든 데이터를 자료형에 상관없이 묶음
* QUOTE_MINIMAL: 최소한의 데이터만 묶음
* QUOTE_NONNUMERIC: 숫자 데이터가 아닌 경우에만 묶음 
* QUOTE_NONE:데이터 묶는 작업하지 않음
* reader(): 데이터를 읽어올 때
* writer(): 데이터르르 쓸 때 

## 2️⃣ 로그 관리
### (1) 로깅의 개념
* 행동 정보 : 이동이나 클릭 등 프로그램을 사용할 때 이루어지는 모든 기본적인 이벤트
    * 행동 정보 저장 = 로그 정보 저장
* 로깅 : 프로그램이 실행되는 동안 일어나는 정보를 기록으로 남기는 일

<br> **Q. 로그는 어떻게 기록??**
<br> A. 파일을 생성하여 로그 정보를 남기는 것 (가장 일반적)
<br> 처음 프로그램을 실행할 때 로그 파일 하나를 생성하고, 그 후에 발생하는 이벤트를 로그 파일에 저장하는 방식
<hr>

### (2) 기본 로그 관리 모듈: logging
파이썬에선느 **logging**이라는 이름의 모듈을 사용함

```python
import logging

logging.debug("틀렷짜나!")
logging.info("화긴해!")
logging.warning("쪼심하래해짜나!")
logging.error("ㄷㄷ에러남;;")
logging.critical("즁댓네..")
```
→ 로깅 레벨을 지정할 수 있음. 

<br> **로깅 레벨(logging level)**
1. 1단계 - **debug** : 개발 시점에 프로그램이 문제없이 실행되는지 확인하기 위해 출력하는 결과
2. 2단계 - **info** : 기본적으로 사용자에게 실행 결과를 알려주는 로그 정보
3. 3단계 - **warnnig** : 문제가 될 수 있는 상황을 기록하는 것
4. 4/5단계 - **error, critical** : 말 그대로 에러가 발생하거나 프로그램이 더이상 수행하기 어려울 때 발생하는 에러
<br> *적절하게 잘 사용하기*

<br> ‣ 파이썬에서 로깅을 사용하기 위해서는 **Logger** 객체를 활용해야 함
<br> (logging 모듈이 Logger를 사용하고 있기 때문에 객체를 따로 만들지 않음)

```python
import logging

logger = logging.getLogger("main")      # Logger 선언
stream_hander = logging.StreamHandler()            # Logger의 출력 방법 선언
logger.addHandler(stream_hander)    # Logger의 출력 등록
```
→ StreamHandler : 출력 공간 지정

## 3️⃣ 설정 저장
### (1) 설정 저장이 필요한 이유
1. 사용자가 프로그램을 실행할 대 로깅 레벨을 지정하기 위해 코드를 수정해야 함
2. 설정값이 너무 많아질 수 있음
<hr>

### (2) 파이썬에서의 설정 저장
* configparser : 설정 자체를 저장하는 것 (실행 시점에 설정이 저장된 파일을 읽어와 적용하는 기능)
* argparse : 실행 시점에 설정 변수를 직접 지정함
<hr>

### (3) configparser 모듈
프로그램의 실행 설정값을 어떤 특정 파일에 저장하여 사용하는 방식
* 콜론(:)를 이용하여 키와 값으로 나누어져 있음
* 섹션(section) : 각 값의 상단에는 값의 그룹을 나타냄 
<br>  ⌙ 대괄호를 이용해 표시하고 하위 변수의 묶음을 표현할 때 사용

💡 **간단한 파일을 만들어 설정 정보를 저장하고, 이를 불러와 사용할 수 있음.**
<br> 👍 **설저 정보가 많고 사용자가 실행 중 자주 바꾸는 설정이 있을 때** 이 모듈을 사용하는 것이 좋음
<hr>

### (4) argparse 모듈
프로그램을 콘솔창에 실행할 때 설정하는 방식
##### 거의 모든 콘솔 프로그램은 실행 시점에서 설정할 수 있는 기능을 제공함

```python
import argparse 

parser = argparse.ArgumentParser(description = "sum two integers.")

parser.add_argument("-a", "--a_valuse", dest="a", help="A integers", type = int)

parser.add_argument("-b", "--b_valuse", dest="b", help="B integers", type = int)

args = parser.parse_args()

print(args)
print(args.a)
print(args.b)
print(args.a + args.b)
```
<br> 인수를 추가할 때 짧은 이름(-), 긴 이름/인수 표시 이름/도움말/자료형 등 (--)