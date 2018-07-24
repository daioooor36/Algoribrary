## 탐욕 알고리즘
스마트 폰 내에 여유메모리 공간에서 앱 각각의 실행 시간이 최소가 되는 알고리즘을 구현한다.

<pre>
    앱 이름       차지하는 메모리크기   실행시간(ms)
  전화번호부             50 K              20
벨소리 다운로드          10 K              30
     게임               25 K              15
    카메라              15 K              40
</pre>

### 프로그램 조건
<pre>
* 입력
  - 입력 파일의 이름은 input.txt 이다.
  - 입력 데이터는 T개의 테스트 케이스로 이루어져 있으며 파일 첫 번째 행에 주어진다.
  - 각 테스트의 첫 번째 행에는 두 정수 E, F(1 ≤ E ≤ F ≤ 10000)가 주어진다. 이때 E는 운영체제가 기본적으로 차지하는 메모리의 크기고, F는 제공된 전체 메모리의 크기이다.
  - 각 테스트의 두번 째 행에는 스마트폰에 포팅될 앱의 개수를 나타내는 정수 N이 주어진다.
  - N행 각각에는 P(1 ≤ P ≤ 50000)와  W(1 ≤ W ≤ 10000)가 주어진다. P는 이 앱을 실행하는 데 소요되는 시간이고, W는 프로그램이 차지하는 메모리 크기다.

* 출력
  - 출력 파일의 이름은 output.txt 이다.
  - 각 테스트에 주어진 메모리 크기를 갖는 애들이 실행될 때 소요되는 최소 시간을 출력한다.
  - 사용하는 앱의 메모리 크기가 정확히 맞지 않으면 -1을 대신 출력한다.
</pre>

### 실행 결과
<pre>
입력
----------------
3
10 110
2
1 1
30 50
10 110
2
1 1
50 30
1 6
2
10 3
20 4
</pre>

<pre>
출력
---------------
스마트폰의 최소 실행 시간 : 60
스마트폰의 최소 실행 시간 : 100
-1
</pre>


<hr/>
### Source Code [Java]

```Java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.StringTokenizer;

public class source01
{
	static int T;
	static int E, F;
	static int MAX_N;
	static int[] P;
	static int[] W;

	static int MAX_MEMORY = 10000;
	static int MAX_TIME   = 50000;
	static int MAX_VALUE  = MAX_MEMORY * MAX_TIME;
	static int[] S = new int [MAX_MEMORY + 1];

	static BufferedWriter bw;

	public static void main(String[] args) throws IOException
	{
		// File Input
		String desc = fileRead("input.txt");

		// File Output setting
		fileWrite("output.txt");

		// 솔루션 모듈
		solvingModule(desc);
	}

	// File Input
	private static String fileRead(String url) throws IOException
	{
		BufferedReader br = new BufferedReader(new FileReader(url));

		String text = "";
		String buffer = "";

		while((buffer = br.readLine()) != null)
		{
			text += buffer + " ";
		}		

		br.close();

		return text;
	}

	// File output setting
	private static void fileWrite(String url) throws IOException
	{
		bw = new BufferedWriter(new FileWriter(url));		
	}

	// 솔루션 모듈
	private static void solvingModule(String text) throws IOException
	{
		// BufferedReader 객체를 통해 한 줄의 문자열을 읽어와 공백(" ")을 기준으로 문자들을 쪼갬
		StringTokenizer st = new StringTokenizer(text);

		// token들은 모두 String이기 때문에, Integer.parseInt() 메소드를 이용해서 int형으로 변환
		// T개의 테스트 횟수
		T = Integer.parseInt(st.nextToken().trim());	// T

		// token들이 더 이상 존재하지 않을 때까지 반복문 수행
		// while(st.hasMoreTokens())
		for(int cnt=0; cnt<T; cnt++)
		{			
			// OS메모리(E)와 전체메모리(F)
			E = Integer.parseInt(st.nextToken().trim());		// E
			F = Integer.parseInt(st.nextToken().trim());		// F

			// N개의 앱
			MAX_N = Integer.parseInt(st.nextToken().trim());	// N

			// 앱 개수에 대한 배열할당
			P = new int[MAX_N];
			W = new int[MAX_N];

			// P시간, W메모리
			for(int i=0; i<MAX_N; i++)
			{
				P[i] = Integer.parseInt(st.nextToken().trim());	// P
				W[i] = Integer.parseInt(st.nextToken().trim());	// W
			}

			// 계산 테이블 초기화
			init_S();

			// 테스트케이스 해결메소드
			solveTestCase();
		}

		// File close
		bw.close();
	}

	// 배열 초기화
	private static void init_S()
	{
		S[0] = 0;

		for(int i=1; i<S.length; i++)
		{
			S[i] = MAX_VALUE;
		}
	}

	// 테스트케이스 해결메소드
	private static void solveTestCase() throws IOException
	{		
		for(int app_cnt = 0; app_cnt < MAX_N; app_cnt++)
		{
			for(int i = 0; i < F - E; i++)
			{
				// if(기존수행 시간 + 추가앱 시간 > 동일메모리의 수행시간)
				if( S[i] + P[app_cnt] < S[i+W[app_cnt]])
				{
					S[i+W[app_cnt]] = S[i] + P[app_cnt];
				}
			}
		}

		// 결과 검증
		// 마지막 공간이 여전히 초기값(MAX_VALUE)이라면 이 수치에 접근하지 못했다는 것(=실패).
		String result = "";

		if(S[F - E] == MAX_VALUE)
			result = "-1\n";
		else
			result = "스마트폰의 최소 실행 시간 : " + S[F - E] + "\n";		

		bw.write(result);
		System.out.print(result);

		// for(int j: input) System.out.print(j + " ");
	}
}
```

<br>
