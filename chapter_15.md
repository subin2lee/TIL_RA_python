# ▶ CHAPTER 15 - XML과 JSON
## 이제 끝이다앗...! ^^b

## 1️⃣ XML의 이해
### (1) XML의 개념 및 표현하기
확장적인 마크업 언어 - 데이터의 구조와 의미를 설명하는 태크를 사용해 어떤 데이터의 속성과 값을 표현하는 언어

```xml
<?xml version = "1.0>
<학생>
    <이름>한재일</이름>
    <학번>20105503></학번>
    <나이>26</나이>
    <학과>산업경영공학과</학과>
    <성별>남성</성별>
</학생>
```
→ 시작 태그와 종료 태그 사이에 어떤 값이 있고, 그 값은 태크의 이름으로 만들어진 속성에 대한 값이 됨
<hr>

### (2) XML 문서
딕셔너리형의 구조와 같음

## 2️⃣ XML 파싱
#### (1) BeautifulSoup 모듈 개요
* BeautifulSoup 모듈 - 파이썬 마크업 언어 스크래핑 도구
<br> (HTML처럼 정규 표현식을 활용해 파싱을 해도 문제 없음)

#### (2) 모듈 사용법
모듈 설치는 conda 사용
>conda create -n python_moc python = 3.6
<br> conda install lxml
<br> conda install -c anaconda beautifulsoup4 = 4.5.1

|목적|설명
|:---:|:---|
|객체 생성|xml문서를 분석하는 새로운 객체를 생성|
|태그 검색|필요한 태그를 검색하여 여러 개를 반환하는 함수|

```python
from bs4 import BeautifulSoup

with open("books.xml", "r", encoding = "utf8") as books_file :
    books_xml = books_file.read()

soup = BeautifulSoup(books_xml, "lxml")

for book_info in soup.find_all ("author") :
    print(book_info)
    print(book_info.get_text())
```

## 3️⃣ JSON의 이해
자바스크립트의 데이터 객체 표현 방식을 데이터 교환의 표준으로 삼은 데이터 표현 언어

<br> [XML과 비슷한 점]
* 딕셔너리형과 매우 비슷한 **키-값**으로 구성됨

<br> [XML과 다른 점]
* 간결성 (기계와 인간 모두 이해하기 쉬움)
* 데이터 용량 적고, 코드로의 전환이 쉬움