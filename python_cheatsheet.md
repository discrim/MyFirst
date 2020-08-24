# Python Cheatsheet
1. [Pure Python](#pure-python)
	1. [Line Continuation](#line-continuation)
	1. [Class](#class)
	     1. [Basics](#basics)
	     1. [Constructor](#constructor)
	     1. [Inheritance](#inheritance)
	     1. [Method Overriding](#method-overriding)
	     1. [Class Variable](#class-variable)
	     1. [`super()`](#super)
	1. [String Formatting (C언어의 format specifiers)](#string-formatting-c언어의-format-specifiers)
	1. [Count in List with Conditions](#count-in-list-with-conditions)
	1. [File I/O](#file-io)
		1. [List Files in a Directory](#list-files-in-a-directory)
		1. [Extract a Filename or Last Folder from Path](#extract-a-filename-or-last-folder-from-path)
	1. [Import files from a higher directory](#import-files-from-a-higher-directory)
1. [Virtual Environment in Windows Using CMD: `venv`](#virtual-environment-in-windows-using-cmd-venv)
1. [`pip`](#pip)
	1. [Show / Export Installed Package List: `freeze`](#show--export-installed-package-list-freeze)
	1. [Install Packages From a List in TXT File](#install-packages-from-a-list-in-txt-file)
	1. [Downgrade Package](#downgrade-package)
1. [`numpy`](#numpy)
	1. [Array Basics](#array-basics)
	1. [Random Number](#random-number)
1. [`imageio`](#imageio)
	1. [Make GIF Out of Multiple Still Images](#make-gif-out-of-multiple-still-images)
1. [`PyYAML`](#pyyaml)
	1. [What is `YAML`? - Crash Course](#what-is-yaml---crash-course)
	1. [How to use `YAML` file in Python? - Basics](#how-to-use-yaml-file-in-python---basics)
1. [Anaconda](#anaconda)
	1. [How to run Anaconda Python in Notepad++](#how-to-run-anaconda-python-in-notepad)
## Pure Python
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
어떤 자식 클래스에서 `mymethod()`를 재정의했다고 가정하자.  
(즉 부모 클래스에 `mymethod()`가 있고, 자식 클래스에도 `mymethod()`가 있는데 부모것과 동작이 다르다)  
이 때, 자식 클래스 안에서 부모 클래스의 `mymethod()`를 사용하려면 `super().mymethod()`를 사용하고, 자식 클래스의 `mymethod()`를 사용하려면 `self.mymethod()`를 사용한다.  
Example:
```python
class Parent():    
    def sing_once( self ):
        print("LOUD VOICE !")

class Child( Parent ):
    def sing_once( self ):
        print("quite voice ~")
    
    def sing_twice( self ):
        # Want to call both Parent's sing_once and Child's sing_once
        self.sing_once()
        super().sing_once()
        
if __name__ == "__main__":
    p1 = Parent()
    c1 = Child()
    
    print("p1.sing_once(): ")
    p1.sing_once()
    
    print("\nc1.sing_once(): ")
    c1.sing_once()
    
    print("\nc1.sing_twice(): ")
    c1.sing_twice()
```
```
p1.sing_once(): 
LOUD VOICE !

c1.sing_once(): 
quite voice ~

c1.sing_twice(): 
quite voice ~
LOUD VOICE !
>>>
```
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
### Count in List with Conditions
Source: [GeeksforGeeks](https://www.geeksforgeeks.org/python-count-of-elements-matching-particular-condition/)  
`count = sumn(1 for elem in mylist if elem > 5)`
### File I/O
#### List Files in a Directory
```python
from os import listdir
mypath = "D:/Desktop/test folder"

# Returns a list of filenames.
allfiles = listdir(mypath)
print(allfiles)

# Returns elements of allfiles that ends with ".txt".
txtfiles = [ff for ff in allfiles if ff.endswith(".txt")]
print(txtfiles)
```
```
['text.txt', 'image.png', 'executable.exe']
['text.txt']
```
#### Extract a Filename or Last Folder from Path
```python
from os.path import basename
print(basename('D:/folder/file.exe'))
print(basename('D:/folder/another_folder'))
```
```
'file.exe'
'another_folder'
```
### Import files from a higher directory
You must add the higher directory explicitly to the path:
```python
import sys
sys.path.append(os.path.dirname(os.path.abspath(os.path.dirname(__file__))))
```
Now Python also perceives the higher directory as a current directory `.`, you can use:
```python
from . import something_from_the_higher_directory
```
Similarly, you can add any directory to the path:
```python
import sys
sys.path.append("C:/mydirectory/")

from . import something_in_mydirectory
```
## Virtual Environment in Windows Using CMD: `venv`
Ref: [코딩도장](https://dojang.io/mod/page/view.php?id=2470)  
Assume we are saving a virtual environment in `C:\venvs` such as `C:\venvs\myenv1`.
```
C:\venvs>python -m venv myenv1
C:\venvs>cd myenv1
C:\venvs\myenv1>Scripts\activate.bat	# Activate (enter) the virtual environment.
(myenv1) C:\venvs\myenv1>		# You are now in the virtual environment.
(myenv1) C:\venvs\myenv1>Scripts\deactivate.bat	# Deactivate (exit) the virtual environment.
C:\venvs\myenv1>			# Back to the root environment.
```
If you install a package via `pip` when you are in a virtual environment, it is only installed in the virtual environment, i.e. in `C:\venvs\myenv1\Lib\site-packages`, not in the root environment.
```
(myenv1) C:\venvs\myenv1>pip install mypackage
```
[Export Installed Package List](#export-installed-package-list) and [Install Packages From a List in TXT File](#install-packages-from-a-list-in-txt-file) can be useful when setting an environment for a certain program.
## `pip`
### Show / Export Installed Package List: `freeze`
```
C:>pip freeze	# Display the installed packege list in CMD
C:>pip freeze > mylist.txt	# Save the list in list.txt
```
### Install Packages From a List in TXT File
```
C:>pip install -r mylist.txt
```
### Downgrade Package
1. Uninstall the higher version.
2. Install while specifying a desired version.
e.g.
```
pip3 uninstall numpy <- Uninstall numpy 1.18.2
pip3 install numpy==1.16.1
```
Solution to my incident on 2020-04-09 while doing EECS 504 final project (Ref: [StackOverflow](https://stackoverflow.com/questions/55890813/how-to-fix-object-arrays-cannot-be-loaded-when-allow-pickle-false-for-imdb-loa))
## `numpy`
Assume `import numpy as np`.
[https://numpy.org/doc/stable/genindex.html](https://numpy.org/doc/stable/genindex.html)
### Array Basics
* Make an array: `x = np.array([[1, 2], [3, 4]])`
* [numpy.append](https://numpy.org/doc/stable/reference/generated/numpy.append.html#numpy.append): `z = np.append(x, y, axis=0)`
* [numpy.transpose](https://numpy.org/doc/stable/reference/generated/numpy.transpose.html#numpy.transpose): `y = x.T`. For complicated transpose (3D axis swap, axis change), see the reference.
* [numpy.delete](https://numpy.org/doc/stable/reference/generated/numpy.delete.html#numpy.delete): `y = np.delete(x, obj=2, axis=1)` to delete x's 2nd index of 1st axis (which is 3rd column).
### Random Number
Source: [numpy](https://numpy.org/doc/stable/reference/random/legacy.html#simple-random-data)  
Make an array of 2-row, 3-col ...
* numbers between `\[0, 1)` from uniform distributtion: `x = np.random.rand(2, 3)`
* numbers from standard normal distribution: `x = np.random.randn(2, 3)`
* integers with some parameters: `x = np.random.randint(low=4, high=17, size=(2, 3))`
(`[low, high)`. `high`, `size` are optional
## `imageio`
### Make GIF Out of Multiple Still Images
Ref: [Basic](https://stackoverflow.com/questions/753190/programmatically-generate-video-or-animated-gif-in-python), [Change Playback Speed](https://stackoverflow.com/questions/38433425/custom-frame-duration-for-animated-gif-in-python-imageio)  
Basic
```python
import imageio
images = []
for filename in filenames:
    images.append(imageio.imread(filename))
imageio.mimsave('/path/to/movie.gif', images)
```
Application with file I/O and slower playback speed (1 fps)
```python
from os import listdir
from os.path import basename
from imageio import imread, mimsave

def main(dir):
    images = []
    allfiles = listdir(dir)
    pngfiles = [ff for ff in allfiles if ff.endswith('.png')]	# Bring all PNG files
    for filename in pngfiles:
        images.append(imread(dir + '/' + filename))
    kwargs = {"duration":1}					# Time to maintain a single image in seconds
    mimsave(dir + '/movie.gif', images, **kwargs)

if __name__ == "__main__":
    mypath = r'D:\still_image_storage'
    main(mypath)
```
## `PyYAML`
### What is `YAML`? - Crash Course
A type of file that stores data in a certain structure.  
E.g. Assume you open notepad and write the following:
```yaml
firstname: John
lastname: Doe
age: 33
education:
  - highschool:
    - name: ABC High
      GPA: 3.45
    college:
    - name: DEF University
      GPA: 3.78
```
and save it as `JohnD.yaml` (not `JohnD.txt`). Then you just stored the data in `YAML` type.
### How to use `YAML` file in Python? - Basics
1. Install `PyYAML`
```
pip install pyyaml
```
2. See the example below.
```python
# yaml_test.py
import yaml
file = open('JohnD.yaml')
dict_from_yaml = yaml.safe_load(file)	# Extract and convert data from YAML file into dictionary type
print(dict_from_yaml)
```
Put `JohnD.yaml` (of the previous section) in the folder where `yaml_test.py` exists.  
Run `yaml_test.py`. The output is as follows:
```
{'firstname': 'John', 'lastname': 'Doe', 'age': 33, 'education':
[{'highschool': [{'name': 'ABC High', 'GPA': 3.45}],
'college': [{'name': 'DEF University', 'GPA': 3.78}]}]}
```
## Anaconda
### How to run Anaconda Python in Notepad++
Source: [Here](https://samyzaf.com/braude/PYTHON/notepad.txt)
