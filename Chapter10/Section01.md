```java

import java.util.Scanner;

public class source01
{
	public static void main(String[] args)
	{
		Scanner in = new Scanner(System.in);
		
		System.out.println("10����->16���� ��ȯ ���α׷��̴�");
		System.out.println("10������ 16������ �ٲٷ��� AŰ�� ������,");
		System.out.println("16������ 10������ �ٲٷ��� BŰ�� ��������.");
		
		System.out.println("A�� B�� �������� : ");		
		String input = in.next().toUpperCase();
		
		System.out.println("��ȯ�� ���ڸ� �Է��ϼ��� : ");
		int num = in.nextInt();
		
		if(input.equals("A"))
		{
			System.out.printf("10���� �� : %d --> 16���� �� : %x", num, num);
		}
		else if(input.equals("B"))
		{
			System.out.printf("16���� �� : %x --> 10���� �� : %d", num, num);
		}
		else
		{
			System.out.println("A�� BŰ�� ����ؾ� �Ѵ�.");
		}
	}
}

```