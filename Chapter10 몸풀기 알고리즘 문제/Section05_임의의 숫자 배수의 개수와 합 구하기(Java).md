## 임의의 숫자 배수의 개수와 합 구하기

### 1. 문제개요
사용자가 입력한 숫자의 1~1,000 사이의 배수의 개수와 그 배수들의 총 합을 구하는 문제이다.

### 2. 실행 결과
<pre>
1~1000 사이에서 선택한 수의 배수가 몇 개고, 배수의 합은 얼마인가?
1부터 1000 사이의 수 중에서 하나를 입력하세요 ==> 4
1부터 1000 사이 4의 배수의 개수 : 250, 배수의 합 : 125500
</pre>

<hr/>
### Source Code [Java]
```java
import java.util.Scanner;

public class source01
{
	public static void main(String[] args)
	{
		Scanner in = new Scanner(System.in);

		System.out.println("1~1000 사이에서 선택한 수의 배수가 몇 개고, 배수의 합은 얼마인가?");
		System.out.print("1부터 1000 사이의 수 중에서 하나를 입력하세요 ==> ");

		int num = in.nextInt();
		int sum = 0;
		int cnt = 0;

		for(int i = 1; i <= 1000; i++)
		{
			if(i % num == 0)
			{
				cnt ++;
				sum += i;
			}
		}

		System.out.printf("1부터 1000 사이 4의 배수의 개수 : %d, 배수의 합 : %d", cnt, sum);		
	}
}
```
