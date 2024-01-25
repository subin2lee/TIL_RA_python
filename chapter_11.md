# ▶ CHAPTER 11 - 모듈과 패키지
## 저는 이 시대에 체고으l.. ㅇ.아..으른임니다ㅏ..
## 1️⃣ 모듈과 패키지의 이해
### 모듈의 개념
: 작은 프로그램 조각
<br> ⌙ 하나하나 연결해 어떤 목적을 가진 프로그램을 만들기 위한 작은 프로그램

*  모듈마다 역할이 있어서 **서로 다른 모듈과 인터페이스만 연결** 되면 사용가능함
    * 인터페이스 : 모듈 간의 연결을 위한 약속
<br> (모듈화된 프로그램을 사용하면 쉽게 사용, 제공됨)

* **import** : 모듈을 사용할 수 있도록 호출하는 명령어
<br> &emsp;&emsp; ⌙ 사용 : 해당 모듈을 메모리에 올리라는 의미
------

### 패키지의 개념
: 모듈의 묶음

* **from** : 모듈을 호출하기 위해 패키지부터 호출하는 명령어

## 2️⃣ 모듈 만들기
### 모듈 만들기 실습
```python
#fah_converter.py(.py파일 자체가 모듈)
def covert_c_to_f(celcius_value) :
    return celcius_value * 9.0 / 5 + 32
```
```python
#module_ex.py
import fah_converter

print("Enter a celsius value:")
celsius = float(input())
fahrenheit = fah_converter.covert_c_to_f(celsius)
print("That's", fahrenheit, "degrees Fahrenheit.")
```
⌙ 클라이언트 코드 
<br> ⌙ **import** 파일 내 함수를 불러옴
<br> ⌙ 함수를 부르기 : **모듈명.함수명(클래스/병수명)**

------
### 네임스페이스
: 모듈 호출의 범위를 지정하는 것

<br> ✖︎ 호출되는 모듈의 이름 = 클라이언트 이름
<br> &emsp; ⎿ 익숙하지 않을 때 발생하는 실수와 기존 클래스를 상속받아 사용하다가 발생 가능
<br> &emsp; 이를 해결하고자 **호출된 모듈의 사용 범위를 명확히 지정!**

#### (1) 알리아스(alias) : 모듈 안으로 코드를 호출하는 방법 (일종의 별칭으로 모듈의 이름을 바꿔 부를 때 사용함) - 🍥 가장 선호하는 방식임 ^^b
* 다른 코드와 이름이 헷갈릴 때 사용하는 키워드 - **as** (모듈의 이름을 간단하게 바꿀 수 있음)
```python
import fah_cinverter as fah
print(fah.covert_x_to_f(41.6))
```
> [질문: 이 말이 이해가 않 되요.(맞춤법 압니다..)]
> * 현재 사용하는 클라이언트 프로그램에 같은 이름의 코드가 있더라도 모듈 내에서만 한정하여 호출해야 한다.

#### (2) from : 모듈에서 특정 함수 또는 클래스만 호출하는 방법
```python
from fah_converter import covert_c_to_f
print(covert_c_to_f(41.6))
```
⎿ 별도의 모듈명을 써 주지 않아도 단독으로 사용 가능함

* from 모듈명 import 모듈 안에 있는 함수명 - 해당 모듈 안에 있는 함수를 가져다 사용가능함
    * 주의해야 할 점 - from은 꼭 모듈을 호출하기 위한 키워드가 아님 (패키지를 호출하거나 해당 패키지 안에 있는 모듈을 호출할 때도 사용함)

#### 별표(*) : 해당 모듈 안에 있는 모든 함수, 클래스, 변수를 가져옴 (모든 것이라는 의미도 가짐)
```python
from ha_converter import *
print(covert_c_to_f(41.6))
```
⎿ 해당 모듈 안에 있는 모든 사용 가능한 리소스를 호출

---
### 내장 모듈의 사용
: 별다른 조치 없이 import문 한 줄로 사용 가능함

#### (1) random 모듈
* random.randint(0, 100) - 0부터 100까자 사이의 정수 난수를 생성
* random.randint() - 일반적인 난수 생성

#### (2) time 모듈
* time.localtime() - 현재 시간 출력

#### (3) urllib 모듈
* 특징 : 특정url의 정보를 불러올 수 있음
* urllib.request.urlopen() - 광호 안에 특정 웹 주소를 입력하면 해당 주소의 HTML 정보를 가져옴
* response.read() - 응답받은 것으로부터 데이터를 읽는 메서드

> 파이썬 모듈 검색은 [구글링 체고ㅇㅇ 반박시 교수님과 토론하셈]

## 3️⃣ 패키지 만들기
### 패키지의 구성
* 패키지 : 여러 개의 .py 파일이 하나의 디렉터리에 들어가 있는 것
* 라이브러리(library) : 다른 사람이 만든 프로그램이 불러와 사용하는 것
<br> **[주의할 점]**
<br> 파일명 자체가 **예약어**를 반드시 지켜야만 실행되는 경우가 많음
----

### 패키지 만들기 실습
#### (1) 디렉터리 구성하기
```
mkdir roboadvisor
cd roboadvisor
mkdir crawling
mkdir database
mkdir analysis
```

#### (2) 디렉터리별로 필요한 모듈 만들기
하나의 패키지 - 중첩된 구조로 만들 수 있으므로 패키지 안에 또 하나의 ㅍ키지가 들어갈 수 있음
* 각각의 디렉털를 하나의 패키지로 선언하기 위해선 예약된 파일을 만들어야 함 - **__init__.py**
    * **__init__.py** : 각 디렉터리가 패키지임을 나타내는 예약 파일
        * 이 친구를 추가하면 패키지의 기본 구조가 만들어짐
    <br> 💀 패키지의 구조 설계 - 하위 패키지별로 해야 하는 일, 하위 패키지 에 소속된 모듈들이 해야 할 일 -> 따로 정의

```python
#series.py(analysis 디렉터리)
def series_test() :
    print("series")
```
```python
#statics.py(analusis 디렉터리)
def statics_test() :
    print("statics")
```
```python
>>> from roboadvisor.analysis import series
>>> series.series_test
series
```
⎿ 코드 실행 시**pycache**라는 디렉터리 생성 - 파이썬의 언어적 특성으로 생기는 결과
* __pycache__ : 실행 시점에서 해당 모듈을 수정해도 결과가 반영되지 않음. (완전히 종료한 후 수정해야 해당 모듈의 결과가 반영)

* ⭐️ 인터프리터 언어이지만 내부적으로 컴파일 과정도 거치고, 효율적으로 사용하기 위한 여러 가지 과정을 거침

#### (3) 디렉터리 별로 __init__.py 구성하기
: 해당 디렉터리가 파이선의 패키지라고 선언하는 초기화 스트립트 (거의 모든 라이브러리에 있음)
<br> : 패키지 개발자 or 설치 시 확인해야 할 내용 등의 **메타데이터**라고 할 수 있음

```python
#__init__.py (roboadvisor 디렉터리)
import analysis
import crawling
import database

__all__ = ['analysis', 'crawling', 'database']
```
⎿ 각각의 패키지를 __init__.py 안에 __all__과 import문을 사용해 선언

```python
#__init__.py(analysis 디렉터리)
from . import series
from . import statics

__all__ = ["series", "statics"]
```
⎿ 각 패키지에 포함된 모듈명을 모두 작성해야 함 -> 패키지로 표시하기 위해 꼭 해야 하는 작업, 패키지별로 모두 처리

* 🍥TIP - import문 앞에 "from . "을 붙이는 이유는 현재 디렉터리인 analysis의 패키지를 호출하기 위함 (안 하면 상위 디렉터리에서 오류 발생)

#### (4) __main__.py 파일 만들기
: 패키지 자체를 실행하기 위해서

<br> [구성] - form과 import문으로 호출 후 **[if __name__ == '__main__']**

```python
#__main__.py
from analysis.series import series_test
from crawling.parser import parser_test

if __name__ == '__main__' :
    series_test()
    parser_test()
```

#### (5) 실행하기(패키지 이름만 호출)
: 해당 패키지의 최상위 디렉터리에서 **'python 패키지명'** 을 입력
```
python rovoadvisor
```
-----

### 패키지 네임스페이스
: 패키지 내에서 모듈을 서로 호출하라 때 사용하는 패키지

|이름|기능||
|:---:|:---|---|
|절대 참조|모듈의 경로를 모두 호출하는 것|
|상대 참조|호출하는 디렉터리 기준으로 호출하는 것|
⭐️ **절대 참조 사용하는 걸 추천** - 모든 패키지의 경로를 정확히 기록하는 것이 더 이해하기 쉬움

```python
#절대 참조
__all__ = ["analysis", "crawling", "database"]

from roboadvisor import analysis
from roboadvisor import crawling
from roboadvisor import database
```
```python
#상대 참조
from . series import series_test
from .. crawling.parser import parser_test
```
⎿ 점 1게(.) - 현재 디렉터리, 점 2개(..) - 부모 디렉터리

## 4️⃣ 가상환경 사용하기
### 가상환경의 개념
: 패키지를 설치할 때 서로 다른 프로젝트가 영향을 주지 않도록 독립적인 프로젝트 수행 환경
<br> (데이터를 다루는 프로젝트, 웹을 다루는 프로젝트 등등 다룰 때)

* 가상환경 도구

|가상환경 도구|특징|
|:---:|:---|
|virtualenv + pip| 가장 대표적인 가상환경 관리도구 |
| |레퍼런스와 패키지가 가장 많음|
|conda|상용 가상환경 도구인 miniconda의 기본 가상환경|
| |설치가 쉬워 윈도에서 유용함|

---
### 가상환경 설정하기
conda 사용함

#### (1) 가상환경 만들기
> conda create -n my_project python=3.4
>> conda create - 가상환경 새로 만들기
<br> -n my_prpject - 가상환경 이름
<br> Python = 3, 4 - 파이썬 버전

⌙ 화면에 "Proceed([y]/n)?' 나오면 y 입력해서 설치 ㄱㄱ

#### (2) 가상환경 실행하기
> activate my_project
>> 'my_project라는 가상환경을 활성화하라'의 의미

> where python
>> 파이썬의 위치가 어디인지 출력해줌

> deactivate
>> 가상환경 종료

#### (3) 가상환경 패키지 설치하기
> conda install matplotlib

#### (4) 가상환경 패키지 실습하기
```python
>>> import matplotlib.pyplot as plt
>>> plt.plot([1, 2, 3, 4])
[<matplotlib.lines.Line2D object at 0x00어쩌고저쩌고>]
>>> plt.ylabel('some numbers')
Text(0, 0.5, 'some nummbers')
>>> plt.show()  # 그래프가 화면에 !!
```

💡 jupyter 패키지
> conda install jupyter
>> 패키지 설치

> jupyter notebook
>> jupyter 환경에서 코딩 가능 ㅇㅇ! (ctrl + enter하면 누른 결과를 볼 수 있음)