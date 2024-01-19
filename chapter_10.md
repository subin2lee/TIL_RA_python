# ▶ CHAPTER 10 - 객체 지향 프로그래밍
## ㄹㅇ 이해력의 문제로..😭
## 1️⃣ 객체 지향 프로그램밍의 이해
### 객체 지향 프로그래밍을 배우는 이유
* 남이 작성한 코드를 재사용하고 싶을 때 사용하는 대표적인 방법
    * 어떤 기능을 수행하는 하나의 단일 프로그램 객체라고 하는 코드로 만들어 다른 프로그래머가 재사용할 수 있도록 함

### 객체와 클래스
* 객체(object) : 실생활에 존재하는 실제적인 물건 또는 개념
    * 속성(attribute) - 변수(variable)
    * 행동(action) - 함수(function)

* 클래스(class) : 객체가 가져야 할 기본 정보를 담은 코드 (객체들을 위한 설계도)

* 인스턴스(instance) : 실제로 생성되는 객체

→ 속성을 할당한 객체를 만든 후, 정보를 클래스에 담고 실제 생성되는 객체에 변수 할당

## 2️⃣ 파이썬의 객체 지향 프로그래밍
### 클래스 구현하기
* 클래스 선언하기 위한 기본 코드 템플릿
> class SoccerPlayer (object)
>> class : 클래스 예약어
<br>SoceerPlayer : 클래스 이름 (첫 글자와 중간 글자는 대문자)
<br>object : 상속받는 객체명

    * 상속의 의미 : 기존에 만즌 클래스의 특징을 그대로 이어받아 사용하는 것

* 작명 기법

|작명 기법|설명|예시|
|:---:|:---|:---|
|snake_case|띄어쓰기 부분에"_"를 추가하여 변수의 이름 지정|함수, 변수명|
|CamelCase|띄어쓰기 부분에 대문자를 사용하여 변수의 이름 지정|클래스명|

1. 속성의 선언 : **__init__()** 라는 예약 함수 사용
```python
class SoccerPlayer(object) :
    def __init__(self, name, position, back_number) :
        self.name = name
        self.position = position
        self.back_number = back_number
```
* **__init()함수** : 클래스에서 사용할 변수를 정의하는 함수
    * self - 클래스에서 생성된 인스턴스에 접근하는 예약어 (생성된 인스턴스를 지정하는 변수)
    * __init__() 내에서만 새로운 속성을 생성해야 함

2. 함수의 선언 : 함수 자체가 다양한 동작을 정의할 수 있음
```python
class SoccerPlayer(object) :
    def change_back_number(self, new_number) :
        print("선수의 등번호를 변경한다 : From %d to %d" %(self.back_number, new_number))
        self.back_number = new_number
```
* **self를 매개변수에 반드시 넣어야 함**
    * 이것이 있어야 실제로 인스턴스가 사용할 수 있는 함수로 선언됨

3. _의 쓰임 : 개수에 따라 여러 가지로 나눌 수 있음
* for _ in range(10)에서의 쓰임 : 변수명 대신 사용
* __(2개)의 쓰임 : 특수한 예약 함수나 변수 의미
******
### 인스턴스 사용하기
: 클래스에서 실제적인 데이터가 입력되어 사용할 수 있는 형태의 객체
<br> : 다양한 정볼르 사용하기 위해 할당한 상태로 사용해야 함

* 호출 방법
> Kangin = SoccerPlayer ("Kangin", "MF", 18) :
>> Kangin - 객체명
<br> SoccerPlayer - 클래스 이름
<br> "Kangin", "MF", 18 - __init__함수 인터페이스 초깃값

```python
#전체 SoccerPlayer 코드
class SoccePlayer(object) :
    def __init__(self, name, position, back_number) :
        self.name = name
        self.position = position
        self.back_number = back_number
    def change_back_number(self, new_number) :
        print("선수의 등번호를 변경한다: From %d to %d" % (self.back_number, new_number))
        self.back_number = new_number
    def __str__(self) :
        return "Hello, My name is %s. I play in %s in center" % (self.name, self.position)
    
#SoccerPlayer를 사용하는 instance 코드
Kangin = SoccePlayer("Kangin", "MF", 18)

print("현재 선수의 등번호는:", Kangin.back_number)
Kangin.change_back_number(19)
print("현재 선수의 등번호는:", Kangin.back_number)
print(Kangin)

#현재 선수의 등번호는: 18
#선수의 등번호를 변경한다: From 18 to 19
#현재 선수의 등번호는: 19
#Hello, My name is Kangin. I play in MF in center
```
*********
### 클래스를 사용하는 이유
* **자신의코드를 다른 사람이 손쉽게 사용할 수 있도록 설계하기 위해서**
* **데이터를 변환하거나 데이터베이스에 저장하는 등의 역할이 필요할 때가 있음**
* 코드를 손쉽게 선언할 수 있음 -> 이차원 리스트보다 명확하게 저장된 데이터를 확인할 수 있음
* 다른 사람들이 결과를 사용할 때 이 데이터가 무엇을 위한 데이터인지 알 수 있음
```python
#데이터
names = ["Messi", "Ramos", "Ronaldo", "Park", "Buffon"]
positions = ["MF", "DF", "CF", "WF", "GK"]
numbers = [10, 4, 7, 13, 1]

#이차원 리스트
players = [[name, position, number] for name, position, number in zip(names, positions, numbers)]
print(players) 
print(players[0])

#전체 SoccerPlayer 코드
class SoccePlayer(object) :
    def __init__(self, name, position, back_number) :
        self.name = name
        self.position = position
        self.back_number = back_number
    def change_back_number(self, new_number) :
        print("선수의 등번호를 변경한다: From %d to %d" % (self.back_number, new_number))
        self.back_number = new_number
    def __str__(self) :
        return "Hello, My name is %s. I play in %s in center." % (self.name, self.position)
    
#클래스 인스터스
player_objects = [SoccePlayer(name, position, number) for name, position, number in zip(names, positions, numbers)]
print(player_objects[0])

#[['Messi', 'MF', 10], ['Ramos', 'DF', 4], ['Ronaldo', 'CF', 7], ['Park', 'WF', 13], ['Buffon', 'GK', 1]]
#['Messi', 'MF', 10]
#Hello, My name is Messi. I play in MF in center.
```

[주의해야 할 점 - **객체 지향 프로그래밍 만능주의**]
* 이 개념을 사용해 코드를 만들고 싶은 욕심 수직상승(?)
* 하지만 파이썬은 코드를 쉽게 코딩하고 싶은 고민에 나온 언어이므로, 필요한 방법을 적재적소에 적용시켜 쉽게 문제 해결하는 것이 좋음 ^_^

## 3️⃣ 객체 지향 프로그래밍의 특징
**실생활을 모델링함**

1. 상속 : 부모클래스에 정의된 속성과 메서드를 자식 클래스가 물려받아 사용한다는 것
* 파이썬의 모든 객체는 object 객체를 상속함
```python
class Person(object) :
    pass
```
* Person 클래스가 가진 생성자를 그대로 사용하여 인스턴스를 만듦
```python
class Person(object) :
    def __init__(self, name, age) :
        self.name = name
        self.age = age

class Korean(Person) :
    pass

first_korean = Korean("Sungchul", 35)
print(first_korean.name)

#Sungchul
```
* 부모 클래스보다 **자식 클래스가 더 구체화**됨 -> 부모 클래스의 메서드를 재정의한다

* 자식 클래스에 __init__() 함수를 생성할 때, **super().__init__(매개변수)**라고 입력
    * super() : 부모 클래스를 가리킴
    * 부모 클래스의 __init__()를 그대로 사용한다는 뜻
    
* 함수 재정의 : 오버라이딩
    * 오버라이딩 : 상속 시 함수 이름과 필요한 매개변수는 그대로 유지하면서 함수의 수행 코드를 변경하는 것
```python
class Person(object) :
    def __init__(self, name, age, gender) :
        self.name = name
        self.age = age
        self.gender = gender
    def about_me(self) :
        print("저의 이름은", self.name , "이고요, 제 나이는", str(self.age), "살입니다.")
```
```python
#부모 클래스 Person으로부터 상속
class Employee(Person) :
    def __initt__(self, name, age, gender, salary, hire_date) :
        super().__init__(name, age, gender)
        self.salary = salary
        self.hire_date = hire_date

    def do_work(self) :
        print("열심히 일을 한다.")

    def about_me(self) :
        super().about_me()
        print(" wp rmqdusms", self.salary, "ㄴ원이고, 제 입사일은", self.hire_date, "입니다.")
```
*********
2. 다형성 : 같은 이름의 메서드가 다른 기능을 하는 것
* 크롤러(crawler) : 인터넷에서 데이터를 모으는 프로그램

* 이름은 같지만 다른 내용으로 구현함 (로직 차이)
```python
n_crawler = NaverCrawler()
d_crawler = DaumCrawler()
cralwers = [n_crawler, d_crawler]
news = []
for cralwer in cralwers :
    news.append(cralwer.do_crawling())
```

* talk : 두 동물 클래싀 역할이 다른 것을 확인 가능
    * NotLmplementedError : 자식 클래스에만 해당 함수를 사용 가능

```python
class Animal:   
    def __init__(self, name) :
        self.anme = name
    def talk(self) :
        raise NotImplementedError("Subclass must implement abstract method")
    
class Cat(Animal) :
    def talk(self) :
        return 'Meow!'
    
class Dog(Animal) :
    def talk(self) :
        return "Woof! Woof!"
    
animals = [Cat("Missy"), Cat("Mr.Mistoffelees", Dog("Lassie"))]
for animal in animals :
    print(animal.name = " : " = animal.talk())
```
<hr>
3. 가시성 : 객체의 정보를 볼 수 잇는 레벨을 조절하여 객체의 정보 접근을 숨기는 것

* 캡술화(encapsulation) : 내부 내용을 세부적으로 알 필요 없고 **사용방법만 명확히 알면** 사용가능
    * 사용해야 하는 이유: 클래스 간 간섭 및 정보 공유를 최소화하여 개별 클래스가 단독으로도 잘 동작할 수 있도록 해야함
* 정보 은닉(information hiding) : 외부에서 코드 내불르 볼 수 없게 하기 위해 내부의 정볼르 숨김

* 캡술화와 정보 은닉의 비슷한 점 : 코드 내부 구현을 잘 해서 외부에서 쉽게 사용하게 하고, 코드의 세부적인 내용을 모르게 하는 것

```python
class Product(object) :
    pass

class Inventory(object) :
    def __init__(self) :
        self.__items = []

    #@property
    # def items(self) :
    #     return self.__items

    def add_new_item(self, product) :
        if type(product) == Product :
            self.__items.append(product)
            print("new item added")

        else :
            raise ValueError("Invalid Item")
        
    def get_number_of_items(self) :
        return len(self,__items)
    
my_inventory = Inventory()
my_inventory.add_new_item(Product())
my_inventory.add_new_item(Product())


my_inventory.__items

#new item added
#new item added
#Traceback (most recent call last):
#  File "/Users/isubin/workspace/practice/visi.py", line 24, in <module>
#    my_inventory.__items
#AttributeError: 'Inventory' object has no attribute '__items'
```
* 오류 발생 이유 : _가 특수 역할을 하는 예약 문자로 클래스에서 변수에 두 개가 붙어있어 사용될 클래스 내부에서만 접근할 수 있고 외부에는 호출하여 사용하지 못해서

→ 클래스 내부용으로만 변수를 사ㅏ용하고 싶다면 "__변수명" 형태로 변수 선언

* 외부에서 사용하기 위해서 : **데코레이터(decorator) - @property** 사용하기 
```python
class Inventory(object) :
    def __init__(self) :
        self.__items = []

    @property
    def items(self) :
        return self.__items
```
→ __items 변수의 원래 이름이 아닌 items로 호출
<br> ⎿ @property를 붙인 함수 이름으로 **실제 __items를 사용할 수 있는 것** (private 변수 -> public 변수)