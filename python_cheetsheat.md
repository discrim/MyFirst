# Python Cheetsheat
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
```
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
```
a.add():  6
a.mul():  8
a.sub():  2
a.div():  2.0
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
```
a.add():  6
a.mul():  8
a.sub():  2
a.div():  2.0
a.pow():  16
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
```
a.div():  0
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
```
Family.lastname:  Kim
a.lastname:  Kim
b.lastname:  Kim
Execute Family.lastname = 'Park'
a.lastname:  Park
b.lastname:  Park
id(Family.lastname):  59794464
id(a.lastname):  59794464
id(b.lastname):  59794464
```