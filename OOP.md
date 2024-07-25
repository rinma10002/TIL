# 객체 지향 프로그래밍
# 객체

### 클래스 Class
- 파이썬에서 타입을 표현하는 방법

### 객체 Object
- 클래스에서 정의한 것을 토대로 메모리에 할당된 것, **속성(변수)** 과 **행동(메서드)** 으로 구성된 모든 것

### 인스턴스 Instance
- 클래스의 속성과 행동을 기반으로 생성된 개별 객체
- Ex) 아이유는 객체다 (O), 아이유는 인스턴스다(X), 아이유는 가수의 인스턴스다(O)


# 클래스 Class

## 클래스 정의

`class ClassName`

1. `class` : 클래스 키워드
2. `ClassName` : 클래스 이름은 파스칼 케이스 방식으로 작성

## 클래스 구성요소

```python
# 클래스 정의
class Person:
    blood_color = 'red'

    def __init__(self, name) :
        self.name = name
    
    def singing(self) :
        return f'{self.name}이 노래합니다.'

# 인스턴스 생성
singer1 = Person('iu')

# (인스턴스) 메서드 호출
print(singer1.singing()) # iu이 노래합니다.

# 속성(변수) 접근
print(singer1.blood_color) # red

# 인스턴스 속성(변수)
print(singer1.name) # iu
```

### 생성자 메서드 
- `def __init__(self, name) :`
- 객체를 생성할 때 자동으로 호출되는 특별한 메서드 (Magic method)
- 인스턴스를 생성하고, 필요한 초기값을 설정

### 인스턴스 변수 
- `self.name = name`
- 인스턴스(객체)마다 별도로 유지되는 변수
- 인스턴스마다 독립적인 값을 가지며, 인스턴스가 생성될 때마다 초기화됨
- 특징: self가 붙어 있으면 인스턴스 변수다!

### 클래스 변수 

- 클래스 내부에 선언된 변수(위에선 `blood_color = 'red'`이 부분)
- 클래스로 생성된 모든 인스턴스들이 공유하는 변수

### 인스턴스 메서드
- `def singing(self) :`
- 각각의 인스턴스가 호출할 수 있는 메서드
- 인스턴스 변수에 접근하고 수정하는 등의 작업을 수행

# 메서드(총 세가지)

## 1.인스턴스 메서드

### 인스턴스 메서드 구조
- 인스턴스의 상태를 조작하거나 동작을 수행
- 반드시 첫 번째 매개변수로 인스턴스 자신 **(self)** 을 전달받음
    
    `def instance_method(self, arg1, …)` 

## 2.클래스 메서드
클래스가 호출하는 메서드 

### 클래스 메서드 구조

```python
@classmethod
def class_method(cls, args, …) :
	pass
```

- `@classmethod` : 데코레이터를 사용하여 정의
- `cls` : 호출 시, 첫번째 인자로 해당 메서드를 호출하는 클래스가 전달됨, 전달될 때 사용하는 매개변수 이름 = `cls` (생성자 메서드에서 self를 받는것과 비슷하다고 보면 됨)

## 3.스태틱 메서드
- 클래스 메서드도 아니고 인스턴스 메서드도 아닌 상관없이 독립적으로 동작하는 메서드
- `@staticmethod` 가 맨처음에 붙음
### 스테틱 메서드 구조

```python
Class MyClass :
	 @staticmethod
	 def static_method(arg1, ...) :
		 pass
```

## 인스턴스와 클래스 간의 이름 공간

- 독립적인 이름공간을 가진다 
- LEGB 기억해보자!


## 매직 메서드

- 인스턴스 메서드
- 특정 상황에 자동으로 호출되는 메서드
- Double underscore(__)가 있는 메서드는 특수한 동작을 위해 만들어진 메서드
- 기억 해야할것:  
    1. `__str__(self)`
    2. `__init__(self)`

## 데코레이터

다른 함수의 코드를 유지한 채로 수정하거나 확장하기 위해 사용되는 함수, 원래 함수의 중간에 끼어드는 구문은 불가!
```python
# 데코레이터 정의

def my_decorator(func) :
	def wrapper() :
	# 함수 실행 전에 수행할 작업
	print('함수 실행 전')
	# 원본 함수 호출
	result = func()
	# 함수 실행 후에 수행할 작업
	print('함수 실행 후')
	return result
return wrapper
```

```python
# 데코레이터 사용
@my_decorator
def my_function() :
	print('원본 함수 실행')

my_function()
'''
함수 실행 전
원본 함수 실행
함수 실행 후
'''
```
## 상속
### 개요
#### 상속 `Inheritance`
- 기존 클래스의 속성과 메서드를 물려받아 새로운 하위 클래스를 생성하는 것

#### 상속이 필요한 이유
1. 코드 재사용
    - 상속을 통해 기존 클래스의 속성과 메서드를 재사용할 수 있음
    - 새로운 클래스를 작성할 때 기존 클래스의 기능을 그대로 활용할 수 있으며, 중복된 코드를 줄일 수 있음
2. 계층 구조
    - 상속을 통해 클래스들 간의 계층 구조를 형성할 수 있음
    - 부모 클래스와 자식 클래스 간의 관계를 표현하고, 더 구체적인 클래스를 만들 수 있음
3. 유지 보수의 용이성
    - 상속을 통해 기존 클래스의 수정이 필요한 경우, 해당 클래스만 수정하면 되므로 유지 보수가 용이해짐 
    - 코드의 일관성을 유지하고, 수정이 필요한 범위를 최소화할 수 있음

### 클래스 상속
```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):  # 메서드 재사용
        print(f'반갑습니다. {self.name}입니다.')


class Professor(Person):
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department


class Student(Person):
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa


p1 = Professor('박교수', 49, '컴퓨터공학과')
s1 = Student('김학생', 20, 3.5)

# 부모 Person 클래스의 talk 메서드를 활용
p1.talk() # 반갑습니다. 박교수입니다.

# 부모 Person 클래스의 talk 메서드를 활용
s1.talk() # 반갑습니다. 김학생입니다.
```

### 다중 상속
#### 다중 상속 정의
- 둘 이상의 상위 클래스로부터 여러 행동이나 특징을 상속받을 수 있는 것
- 상속받은 모든 클래스의 요소를 활용 가능함
- 중복된 속성이나 메서드가 있는 경우 <span style='color:crimson;'>상속 순서에 의해 결정</span>됨

#### 다중 상속 예시
```py
class Person:
    def __init__(self, name):
        self.name = name

    def greeting(self):
        return f'안녕, {self.name}'


class Mom(Person):
    gene = 'XX'

    def swim(self):
        return '엄마가 수영'


class Dad(Person):
    gene = 'XY'

    def walk(self):
        return '아빠가 걷기'


class FirstChild(Dad, Mom):
    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 응애'


baby1 = FirstChild('아가')
print(baby1.cry()) # 첫째가 응애
print(baby1.swim()) # 첫째가 수영
print(baby1.walk()) # 아빠가 걷기
print(baby1.gene) # XY
```

#### MRO (Method Resolution Order)
- 메서드 결정 순서
#### `super()`
- 부모 클래스 객체를 반환하는 내장 함수
- 다중 상속 시 MRO를 기반으로 현재 클래스가 상속하는 모든 부모 클래스 중 다음에 호출될 메서드를 결정하여 자동으로 호출

#### `mro()` 사용 예시

  ```python
  class A:
      def __init__(self):
          print('A Constructor')

  class B(A):
      def __init__(self):
          super().__init__()
          print('B Constructor')

  class C(A):
      def __init__(self):
          super().__init__()
          print('C Constructor')
          
  class D(B, C):
      def __init__(self):
          super().__init__()
          print('D Constructor')

  print(D.mro())
  ```

  ##### super의 2 가지 사용 사례
1. 단일 상속 구조
    - 명시적으로 이름을 지정하지 않고 부모 클래스를 참조할 수 있으므로, 코드를 더 유지 관리하기 쉽게 만들 수 있음
    - 클래스 이름이 변경되거나 부모 클래스가 교체되어도 super()를 사용하면 코드 수정이 더 적게 필요
2. 다중 상속 구조
    - MRO를 따른 메서드 호출
    - 복잡한 다중 상속 구조에서 발생할 수 있는 문제를 방지