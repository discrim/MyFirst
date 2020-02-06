# IQ Sampler Code Reading
Memo everything that I searched while reading  IQ Sampler Code.
## Misc
### `ifndef, define, endif`
- Source: [전처리문의 종류(#include, #define, #ifdef, … )](http://sarghis.com/blog/802/)
- 한 헤더를 두 번 이상 #include 하면 syntax error. 이를 막기 위한 방법이다. 의도하지 않더라도 코디 짜다 실수로 그렇게 할 때가 있다.
- 사용될 헤더에 적어준다.
Ex. my_header.h 에 이 보호장치를 하려면  
```C
#ifndef _MY_HEADER_
#define _MY_HEADER_
// 코드 본문
#endif _MY_HEADER_
```
- 언더바를 앞뒤로 몇 개나 붙일지는 상사의 convention을 따르자.
### `\r`
- Source: [[C/C++] C언어 이스케이프 문자(Escape Character, 이스케이프 시퀀스)](https://arer.tistory.com/95)
- 캐리지 리턴: 커서를 현재 줄의 처음으로 옮김.
## `bg.h`
### `typedef enum { ... } ConnState`
- 연결상태를 7가지로 구분한다.
- `scanning`
- `opening`
- `discoverService`
- `discoverCharacteristics`
- `enableNotifications`
- `enableCTE`
- `running`
## `bg.c`
## `common.h`
### `_WIN32_WINNT, WINVER`
- Source: [Update WINVER and _WIN32_WINNT](https://docs.microsoft.com/en-us/cpp/porting/modifying-winver-and-win32-winnt?view=vs-2019), [버전 매크로](http://www.jiniya.net/wp/archives/2215)
- 이 프로그램이 어떤 버전의 Windows에서부터 사용될 수 있는지 알려준다.
- 새로 나온 프로그램은 예전 운영체제에서 못 쓰는 경우가 있기 때문에, 그 제한사항을 개발자가 수동으로 메모해두는 것이다. 컴파일러는 이 매크로와 자기가 돌아가고 있는 운영체제를 비교하고, 만약 버전이 맞지 않으면 컴파일하지 않는다.
- Ex. 어떤 프로그램은 Windows XP에서는 못 쓰지만, Windows Vista부터는 사용할 수 있다.
- 이곳의  _WIN32_WINNT 값은 0X0600 이고, 이는  Windows Vista이다.
### `locatorMeasurement_t`
- `typedef struct LocatorMeasurement`
- `azimuth`: x축에서 y축으로 반시계로 도는 각
- `elevation`: 바닥에서 z축으로 일어서는 각
- `distance`: 반지름
## `main.c`
### `fgets`
- Source: [70.4 파일에서 문자열 읽기](https://dojang.io/mod/page/view.php?id=610)
### `fscanf`
- Source: [70.2 서식을 지정하여 파일에서 문자열 읽기](https://dojang.io/mod/page/view.php?id=608)
### Thread 쓰레드
- `CreateThread`
