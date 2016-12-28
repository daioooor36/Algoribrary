## 최대공약수 구하기


### 1. 실행 결과
```
약수를 구할 두 정숫값을 입력하세요
입력 1 : 280
입력 2 : 30
280과 30의 최대공약수는 10이다
```

### 2. 프로그램 작성 시 알아야 할 기능

#### 2.1 임의의 숫자의 약수를 구하는 방법

```java
import java.util.Scanner;

public class source01
{
	public static void main(String[] args)
	{    
    Scanner in = new Scanner(System.in);

		System.out.println("약수를 구할 정숫값을 입력하세요");
		System.out.print("입력 : ");
		int num = in.nextInt();

		for(int i=1 ; i<=num ; i++)
		{
			if(num % i == 0)
			{
				System.out.print(i + " ");
			}
		}
	}
}
```


#### 2.2 임의의 두 숫자에 공통으로 해당하는 약수를 구하는 방법

```java
import java.util.Scanner;

public class source02
{
	public static void main(String[] args)
	{		
		Scanner in = new Scanner(System.in);

		System.out.println("공약수를 구할 두 정숫값을 입력하세요");
		System.out.print("입력1 : ");
		int num_1 = in.nextInt();
		System.out.print("입력2 : ");
		int num_2 = in.nextInt();

		int max_num = (num_1 > num_2) ? num_1 : num_2;

		for(int i=1 ; i<=max_num ; i++)
		{
			if( num_1%i==0 && num_2%i==0 )
			{
				System.out.print(i + " ");
			}
		}
	}
}
```


<hr/>

### [Solution]
#### 2.3 임의의 두 숫자에 공통으로 해당하는 약수 중 최댓값을 선택하는 방법

```java
import java.util.Scanner;

public class source01
{
	public static void main(String[] args)
	{		
		Scanner in = new Scanner(System.in);

		System.out.println("공약수를 구할 두 정숫값을 입력하세요");
		System.out.print("입력1 : ");
		int num_1 = in.nextInt();
		System.out.print("입력2 : ");
		int num_2 = in.nextInt();

		int max_num = (num_1 > num_2) ? num_1 : num_2;

		for(int i=max_num ; i>=1 ; i--)
		{
			if( num_1%i==0 && num_2%i==0 )
			{
				System.out.println(num_1 + "과 " + num_2 + "의 최대공약수는 " + i + "이다");
				break;
			}
		}
	}
}
```
