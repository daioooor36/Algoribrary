```java

import java.util.Scanner;

public class source01
{
	public static void main(String[] args)
	{
		Scanner in = new Scanner(System.in);
		
		System.out.println("10진수->16진수 변환 프로그램이다");
		System.out.println("10진수를 16진수로 바꾸려면 A키를 누르고,");
		System.out.println("16진수를 10진수로 바꾸려면 B키를 누르세요.");
		
		System.out.println("A나 B를 누르세요 : ");		
		String input = in.next().toUpperCase();
		
		System.out.println("변환할 숫자를 입력하세요 : ");
		int num = in.nextInt();
		
		if(input.equals("A"))
		{
			System.out.printf("10진수 값 : %d --> 16진수 값 : %x", num, num);
		}
		else if(input.equals("B"))
		{
			System.out.printf("16진수 값 : %x --> 10진수 값 : %d", num, num);
		}
		else
		{
			System.out.println("A와 B키만 사용해야 한다.");
		}
	}
}

```