# C++ Cheatsheet
1. [Dynamic Allocation 동적 할당, 동적 어레이](#dynamic-allocation-동적-할당-동적-어레이)
	1. [Single Variable](#single-variable)
	1. [Array](#array)
1. [Null Pointer](#null-pointer)
1. [Random Number 난수 생성](#random-number-난수-생성)
1. [Command Line Arguments Parsing](#command-line-arguments-parsing)
	1. [Type Casting from String (Character Array) to Integer](#type-casting-from-string-character-array-to-integer)
1. [`make` and makefile](#make-and-makefile)
1. [Vector Iteration](#vector-iteration)
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
### Vector Iteration
Source: [여기](https://hyeonstorage.tistory.com/318)
