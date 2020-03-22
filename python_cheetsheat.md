# Python Cheetsheat
### Line Continuation
Source: [Stackoverflow](https://stackoverflow.com/questions/53162/how-can-i-do-a-line-break-line-continuation-in-python)  
Enclose with parantheses or add backslash.
```python
a = ((i1 < 20) and
     (i2 < 30) and
     (i3 < 40))
b = (i1 < 20) and \
    (i2 < 30) and \
    (i3 < 40)
```
### Class
Source: [점프 투 파이썬](https://wikidocs.net/28)
#### Basics
```python
class FourCal:
    def setdata(self, in1, in2):
        self.opnd1 = in1                # Used self. Therefore, instance's opnd1 = in1
        self.opnd2 = in2                # Used self. Therefore, instance's opnd2 = in2
    def add(self):
        return self.opnd1 + self.opnd2
    def mul(self):
        return self.opnd1 * self.opnd2
    def sub(self):
        return self.opnd1 - self.opnd2
    def div(self):
        return self.opnd1 / self.opnd2

a = FourCal()
a.setdata(4, 2)

b = FourCal()
b.setdata(3, 7)

print("a.opnd1: ", a.opnd1)
print("b.opnd1: ", b.opnd1)

print("id(a.opnd1): ", id(a.opnd1))
print("id(b.opnd1): ", id(b.opnd1))

print("a.add(): ", a.add())
print("a.mul(): ", a.mul())
print("a.sub(): ", a.sub())
print("a.div(): ", a.div())

print("b.add(): ", b.add())
print("b.mul(): ", b.mul())
print("b.sub(): ", b.sub())
print("b.div(): ", b.div())
```
```python
a.opnd1:  4
b.opnd1:  3
id(a.opnd1):  1632303072
id(b.opnd1):  1632303056
a.add():  6
a.mul():  8
a.sub():  2
a.div():  2.0
b.add():  10
b.mul():  21
b.sub():  -4
b.div():  0.42857142857142855
>>>
```
- `self`: Instance
#### Constructor
```python
class FourCal:
    def __init__(self, in1, in2):
        self.opnd1 = in1
        self.opnd2 = in2
    def setdata(self, in1, in2):
        self.opnd1 = in1
        self.opnd2 = in2
    def add(self):
        return self.opnd1 + self.opnd2
    def mul(self):
        return self.opnd1 * self.opnd2
    def sub(self):
        return self.opnd1 - self.opnd2
    def div(self):
        return self.opnd1 / self.opnd2

a = FourCal(4, 2)

print("a.opnd1: ", a.opnd1)
print("a.opnd2: ", a.opnd2)

print("a.add(): ", a.add())
print("a.div(): ", a.div())
```
```python
a.add():  6
a.mul():  8
a.sub():  2
a.div():  2.0
>>>
```
#### Inheritance
```python
class FourCal:
    def __init__(self, in1, in2):
        self.opnd1 = in1
        self.opnd2 = in2
    def setdata(self, in1, in2):
        self.opnd1 = in1
        self.opnd2 = in2
    def add(self):
        return self.opnd1 + self.opnd2
    def mul(self):
        return self.opnd1 * self.opnd2
    def sub(self):
        return self.opnd1 - self.opnd2
    def div(self):
        return self.opnd1 / self.opnd2

class MoreFourCal(FourCal):
    def pow(self):
        return self.opnd1 ** self.opnd2

a = MoreFourCal(4, 2)

print("a.add(): ", a.add())
print("a.mul(): ", a.mul())
print("a.sub(): ", a.sub())
print("a.div(): ", a.div())
print("a.pow(): ", a.pow())
```
```python
a.add():  6
a.mul():  8
a.sub():  2
a.div():  2.0
a.pow():  16
>>>
```
#### Method Overriding
```python
class FourCal:
    def __init__(self, in1, in2):
        self.opnd1 = in1
        self.opnd2 = in2
    def setdata(self, in1, in2):
        self.opnd1 = in1
        self.opnd2 = in2
    def add(self):
        return self.opnd1 + self.opnd2
    def mul(self):
        return self.opnd1 * self.opnd2
    def sub(self):
        return self.opnd1 - self.opnd2
    def div(self):
        return self.opnd1 / self.opnd2

class SafeFourCal(FourCal):
    def div(self):
        if self.opnd2 == 0:
            return 0
        else:
            return self.opnd1 / self.opnd2

a = SafeFourCal(4, 0)

print("a.div(): ", a.div())
```
```python
a.div():  0
>>>
```
#### Class variable
```python
class Family:
    lastname = "Kim"    # Class variable

print("Family.lastname: ", Family.lastname)

a = Family()
b = Family()

print("a.lastname: ", a.lastname)
print("b.lastname: ", b.lastname)

print("Execute Family.lastname = 'Park'")
Family.lastname = 'Park'

print("a.lastname: ", a.lastname)
print("b.lastname: ", b.lastname)

print("id(Family.lastname): ", id(Family.lastname))
print("id(a.lastname): ", id(a.lastname))
print("id(b.lastname): ", id(b.lastname))
```
```python
Family.lastname:  Kim
a.lastname:  Kim
b.lastname:  Kim
Execute Family.lastname = 'Park'
a.lastname:  Park
b.lastname:  Park
id(Family.lastname):  59794464
id(a.lastname):  59794464
id(b.lastname):  59794464
>>>
```
#### `super()`
Source: [Tistory](https://rednooby.tistory.com/56), [#ashcode](https://hashcode.co.kr/questions/6419/python3-super%EC%99%80-supera-self%EC%9D%98-%EC%B0%A8%EC%9D%B4%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94)  
자식 클래스가 부모 클래스의 메소드를 사용하려면 How to let a child class use its parent's method
1. 부모 클래스의 함수를 재정의하지 않는다. Don't redefine the parent's method.
```python
class father():
    def handsome():
        print("Handsome!")

class brother():
    # Don't redefine handsome()

bro = brother()
bro.handsome()
```
```
Handsome!
>>>
```
2. 부모 클래스의 함수를 재정의하고 `super()`를 사용한다. Redefine the parent's method and use `super()`.
```python
class father():
    def handsome():
        print("Handsome!")

class brother():
    def handsome():
        super().handsome()  # Equivalent: super(father, self).handsome()
        # You can edit this brother version of handsome() if you add codes.

bro = brother()
bro.handsome()
```
```
Handsome!
>>>
```
### String Formatting (C언어의 format specifiers)
Source: [learnpython.org](https://www.learnpython.org/en/String_Formatting), [Python Official](https://docs.python.org/3/library/string.html#format-examples)
2가지 방법이 있다.
- The old %-formatting
- `str.format()`
```python
print("String: %s, Integer: %d, Floating Point Number: %4.3f" % ('Hello', 13, 5.39))
print("String: {0}, Integer: {1}, Floating Point Number: {2}".format('Hello', 13, 5.39))
print("String: {}, Integer: {}, Floating Point Number: {}".format('Hello', 13, 5.39))
print("String: {2}, Integer: {0}, Floating Point Number: {1}".format(13, 5.39, 'Hello'))
```
```python
String: Hello, Integer: 13, Floating Point Number: 5.390
String: Hello, Integer: 13, Floating Point Number: 5.39
String: Hello, Integer: 13, Floating Point Number: 5.39
String: Hello, Integer: 13, Floating Point Number: 5.39
>>>
```
