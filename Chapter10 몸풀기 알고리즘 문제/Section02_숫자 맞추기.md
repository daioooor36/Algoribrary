## Up-Down 숫자 맞추기 게임

### 1. 프로그램 작성 시 알아야 할 기능
>#### 1.1 프로그램에서 난수를 생성하는 방법
>>* 난수 생성 방법 [C]
```c
srand(time(NULL));
int num = rand() % 10;  // 난수범위: 0~9
```

>#### 1.2 사용자가 정확한 답을 맞추기 까지 루프실행되도록 하는 방법



### 2. Section02 실행 결과
```
0부터 9까지의 숫자를 입력하세요
[1번째 도전] : 5
5보다 작습니다
[2번째 도전] : 1
1보다 큽니다
[3번째 도전] : 3
우와! 정확하다. 3번째 만에 맞췄군요
```
<hr/>
### Source code [C]
```c
#include <stdio.h>
#include <time.h>
#include <stdlib.h>

void main()
{
	int num;		// 난수 값
	int cnt = 0;	// 수행 횟수
	int input;		// 입력 값

	srand((unsigned)time(NULL));
	num = rand()%10;

	printf("0부터 9까지의 숫자를 입력하세요\n");
	while(1)
	{
		printf("[%d번째 도전] : ", ++cnt);
		scanf_s("%d", &input);

		if(input > num)
		{
			printf("%d보다 작습니다\n", input);
		}
		else if(input < num)
		{
			printf("%d보다 큽니다\n", input);			
		}
		else
		{
			printf("우와! 정확하다. %d번째 만에 맞췄군요\n", cnt);
			break;
		}
	}
}
```
