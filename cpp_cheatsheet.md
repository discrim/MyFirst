# C++ Cheatsheet
1. [Dynamic Allocation 동적 할당, 동적 어레이](#dynamic-allocation-동적-할당-동적-어레이)
	1. [Single Variable](#single-variable)
	1. [Array](#array)
1. [Null Pointer](#null-pointer)
1. [Random Number 난수 생성](#random-number-난수-생성)
1. [Command Line Arguments Parsing](#command-line-arguments-parsing)
	1. [Type Casting from String (Character Array) to Integer](#type-casting-from-string-character-array-to-integer)
1. [`make` and makefile](#make-and-makefile)
1. [Vector](#vector)
	1. [Vector Basics](#vector-basics)
	1. [Member Functions](#member-functions)
	1. [Vector Iteration](#vector-iteration)
1. [Namespace](#namespace)
	1. [Namespace Basis](#namespace-basics)
	1. [Simplified Access](#simplified-access)
1. [Format String (Can Behave as Format Specifier of C)](#format-string-can-behave-as-format-specifier-of-c))
### Dynamic Allocation 동적 할당, 동적 어레이
Source: [cplusplus.com](http://www.cplusplus.com/doc/tutorial/dynamic/)
#### Single Variable
```cpp
// pointer = new type;
int foo;
foo = new int;
```
#### Array
```cpp
// pointer = new type [num_of_element];
int* foo;
foo = new int [5];
```
### Null Pointer
Source: [cppreference.com](https://en.cppreference.com/w/cpp/language/nullptr), [소년코딩](https://boycoding.tistory.com/200)  

키워드. 포인터가 아무 것도 가리키지 않게 하려면 `nullptr`를 assign 해주자.
```cpp
int* ptr = nullptr;
```
### Random Number 난수 생성
Source: [여기](https://arer.tistory.com/10)
```cpp
#include <iostream>
#include <cstdlib> // srand(), rand()
#include <ctime> // time() for seed value

int main(void)
{
  srand((unsigned int)time(NULL));
  cout << rand() << endl;
  return 0;
}
```
### Command Line Arguments Parsing
Source: [cprogramming.com](https://www.cprogramming.com/tutorial/lesson14.html), [cplusplus.com](http://www.cplusplus.com/articles/DEN36Up4/)
```cpp
int main(int argc, char* argv[])
{
  // CODE
  return 0;
}
```
#### Type Casting from String (Character Array) to Integer
```cpp
// Assume ./a.exe 3
int main(int argc, char* argv[])
{
  std::cout << stoi(argv[1]) << endl; // 3
  return 0;
}
```
### `make` and makefile
- Source: [make와 Makefile](https://bowbowbow.tistory.com/12)
### Vector
#### Vector Basics
* Array-based
* STL -> Uses `template` -> Can store any type of data
* Need `#include <vector>`
* `namespace` is `std`
```cpp
std::vector<int> v1;			// Empty vector.
std::vector<int> v2(3);			// {0, 0, 0}
std::vector<int> v3(4, 2);		// {2, 2, 2, 2}
std::vector<int> v4 = {1, 2, 3};	// {1, 2, 3}
std::vector<int> v5(v3);		// Copy v3 to make v4.
```
#### Member Functions
```cpp
std::vector<int> vv = {1, 2};
vv.assign(5, 2);		// Clear vv and fill it with five 2's.
vv.at(idx);			// Refer to idx'th element of vv. Slower than vv[idx]
				// but range check is included so it is safer.
vv.front();			// Refer to the first element.
vv.back();			// Refer to the last element.
vv.clear();			// Erase all the element but still occupies memory.
vv.size();			// Number of elements in the vector.
vv.capacity();			// Numbef of elements that the vector can store
				// without allocating more memory.
vv.push_back(val);		// Append val at the end. If need more memory, double the capacity.
vv.pop_back();			// Delete the last element but does not free its memory.
vv.swap(another_vector);	// Swap everything of vv and another_vector (elements, capacity, etc.)
vv.insert(5, 8);		// At index 5, insert 8 while pushing orinal values.
vv.insert(2, 3, 4);		// At index 2, insert three 4's while pushing original values.
vv.empty();			// true if the vector has no elements, i.e. true if vv.size() == 0.
```
#### Vector Iteration
Source: [여기](https://hyeonstorage.tistory.com/318)
```cpp
// Update here
v.erase(iter);
v.
```
### Namespace
Ref: [TCPSchool](http://www.tcpschool.com/cpp/cpp_scope_namespace)  
#### Namespace Basics
- Can be defined at global location or inside of another namespace, but not in a block.
- Has external link; namespace defined in a header file can be used in separate source file.
- Use `::`, `scope resolution operator` to access a namespace.
```c++
// myns.h
#include <string>

namespace yonsei {
	void display();
	int year = 1885;
	std::string color;
}

namespace michigan {
	void display();
	int year;
	std::string city = "Ann Arbor";
}
```
```c++
// myns_test1.cpp
#include <iostream>
#include "myns.h"

int main(void) {
	std::cout << yonsei::year << "\n";
	yonsei::color = "Royal Blue"; // Declared but undefined in header
	std::cout << yonsei::color << "\n";
	
	michigan::year = 1817; // Declared but undefined in header
	std::cout << michigan::year << "\n";
	std::cout << michigan::color << "\n";
}
```
```
1885
Royal Blue
1817
Ann Arbor
```
#### Simplified Access
To access a namespace by typing `myspace::` everytime is tedious. There are two solusions.
- `using` directive: `using namespace myspace` enables to access all the contents in `myspace` without typing `myspace::` in front of its members.
- `using` declaration: `using myspace::yournumber` enables to access `yournumber` in `myspace` without typing `myspace::` in fron of `yournumber`, but not the other members.
```cpp
// myns_test2.cpp
#include <iostream>
#include "myns.h" // Same header as above.

using namespace yonsei;
// using michigan::year;
	// Invokes error "reference to 'year' is ambiguous"
	// because both yonsei and michigan have 'year' in them.
using michigan::city;

int main(void) {
	std::cout << year << "\n";
	yonsei::color = "Royal Blue"; // Declared but undefined in header
	std::cout << color << "\n";
	
	michigan::year = 1817; // Declared but undefined in header
	std::cout << michigan::year << "\n";
	std::cout << city << "\n";
}

```
```
1885
Royal Blue
1817
Ann Arbor
```
### Format String (Can Behave as Format Specifier of C)
Ref: [cppreference.com](https://en.cppreference.com/w/cpp/utility/format/format)  
Use `std::format()` in `<format>` header if `C++20` or later.
```c++
#include <iostream>
#include <format>

int main() {
	std::cout << std::format("Hello {}!\n", "world"); // Prints "Hello world!"
	std::cout << std::format("{} {}!", "Hello", "world", "something"); // Prints "Hello world!"
}
```
