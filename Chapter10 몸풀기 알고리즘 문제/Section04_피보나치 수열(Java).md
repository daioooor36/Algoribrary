## 피보나치 수열 구하기

### 1. 문제개요
아기 토끼를 키우기 시작했다고 가정하자. 한 쌍의 토끼는 생후 1개월 후에 짝짓기를 하며, 짝짓기한 지 1개월 후에 다시 한 쌍의 토끼를 낳는다. 태어난 토끼가 죽지 않고 계속 살아 있다면 1년 동안 토끼는 몇 쌍이 될까?

  * 1 개월 후에는 여전히 1쌍
  * 2 개월 후에는 1쌍의 토끼가 새로 태어나기 때문에 2쌍
  * 3 개월 후에는 첫 번쨰 암토끼가 다시 1쌍의 토끼를 낳으므로 3쌍
  * 4 개월 후에는 2마리의 암토끼가 각각 1쌍의 토끼를 낳으므로 5쌍

*** 피보나치 형태 {1, 2, 3, 5, 8, 13, 21, ...}**
![firstEqn](https://latex.codecogs.com/gif.latex?f_%7Bn%7D%20%3D%20f_%7Bn-1%7D%20&plus;%20f_%7Bn-2%7D)

### 2. 실행 결과
<pre>
피보나치 수열을 구해보자
   1     2     3      5     8      13     21      34      55      89     144     233
 377   610   987   1597   2584   4181   6765   10946   17711   28657   46368   75025
</pre>

<hr/>
### Source Code [Java]
```java
public class source01
{
	public static void main(String[] args)
	{
		int first = 0;
		int second = 1;
		int result;

		System.out.println("피보나치 수열을 구해보자");
		System.out.print(first + "\t" + second + "\t");

		// 20번 째 수까지만 출력
		for(int i = 0 ; i<20 ; i++)
		{
			if(i == 10)
				System.out.println();

			result = first + second;
			first = second;
			second = result;
			System.out.print(result + "\t");
		}
	}
}
```
