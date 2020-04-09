# C Cheatsheet
1. [Measure Time](#measure-time)
1. [Inline Function](#inline-function)
1. [Signal, Interrupt](#signal-interrupt)
### Measure Time
```c
#include <stdio.h>	// printf()
#include <time.h>		// clock_t, clock()

int main(void)
{
	clock_t clk1, clk2;	// Data type that stores clock counts
	int sum = 0;
	
	clk1 = clock();	// Record current clock count (the moment before beginning the task)
	for (int ii = 0; ii < 100000000; ii++)
	{
		sum += ii;	// Do a repetitive task to spend enough time
	}
	clk2 = clock();	// Record current clock count (the moment after finishing the task)
	
	printf("clk1: %5d\nclk2: %5d\nElapsed Time: %2.3f\n",
		(int)clk1, (int)clk2, (float)(clk2 - clk1) / CLOCKS_PER_SEC);
	
	return 0;
}
```
### Inline Function
Source: [양주종의 코딩스쿨](https://blog.naver.com/ahalinux/220822513868)
* If a function is declared as `inline', the compiler inserts the whole lines of the function definition into the called location instead of calling the function.
* The code become (obviously) longer.
* The code become faster because there is no overhead time for function call.
### Signal, Interrupt
Source: [C언어_시스템프로그래밍 : 시그널](http://blog.naver.com/bitnang/70172674474)
```c
#include <signal.h>

int main(void)
{
	raise(SIGINT)	// Same as keyboard interrupt 'Ctrl + C'
	return 0;
}
```
