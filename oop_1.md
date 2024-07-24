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