## 소수 구하기
1~1,000 사이의 숫자 중에서 1과 그 자신 이외의 정수로 나누어지지 않는 소수를 구하는 문제이다.

### 1. 문제개요
<pre>
1부터 1000 사이의 수 중에서 소수를 구하는 프로그램
1   2   3   5   7   11  13  17
19  23  29  31  37  41  43  47
53  59  61  67  71  73  79  83...
</pre>

### 2. 구현해야 할 기능
\- 소수를 구하는 기능
<br>
\- 한 행에 값을 8개씩 맞춰 출력하는 기능

<hr/>

### Source Code [Java]
```java
public class source01
{
	public static void main(String[] args)
	{
		int i, j, cnt = 0;

		System.out.println("1부터 1000 사이의 수 중에서 소수를 구하는 프로그램");

		for(i = 1; i <= 1000; i++)
		{
			for(j = 2; j <= i; j++)
			{
				if(i % j == 0)
					break;
			}

			if(i == 1 || i == j)
			{
				System.out.print(i + "\t");
				// 10개 출력 시 줄바꿈
				if(++cnt % 10 == 0)
					System.out.println();
			}
		}

		System.out.printf("\n1부터 1000 사이의 소수는 %d개이다.", cnt);
	}
}
```
