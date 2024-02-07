# 구간 합

Created date: 2024년 2월 7일

<br>

<aside>
💡 구간 합은 여러 코딩 테스트 문제에서 자주 사용되는 핵심 개념<br>
— 합 배열을 이용해 시간 복잡도를 더 줄이기 위해 사용하는 특수한 목적의 알고리즘

</aside>

<br>

# 01 합 배열

> **합 배열 S 정의** <br>
S[i] = A[0] + A[1] + A[2] + ... + A[i-1] + A[i]
> 
- 기존의 배열을 전처리한 배열
- 합 배열을 미리 구해 놓으면 기존 배열의 일정 범위의 합을 구하는 시간 복잡도가 $O(n)$에서 $O(1)$로 감소

> **합 배열 S를 만드는 공식** <br>
S[i] = S[i-1] + A[i] <br>
(단, S[0] = A[0])
> 

<br>

# 02 구간 합

> **구간 합을 구하는 공식** <br>
i에서 j까지의 구간 합을 구하는 공식은 <br>
S[j] - S[i-1]
> 

![Untitled](image/prefix_sum1.png)

- 합 배열만 미리 구해 두면 구간 합은 한 번의 계산으로 구할 수 있음

<br>

# 실전 문제 - 구간 합 구하기 4

## 문제

![Untitled](image/prefix_sum2.png)

![Untitled](image/prefix_sum3.png)

[https://www.acmicpc.net/problem/11659](https://www.acmicpc.net/problem/11659)

## 풀이

### 첫번째 시도: 맞았습니다!!

```java
import java.io.*;
import java.util.StringTokenizer;

public class Ex11659_240207 {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    int N, M;
    int[] A;
    int[] S;

    void run() throws IOException {
        // input
        StringTokenizer st1 = new StringTokenizer(br.readLine(), " ");
        N = Integer.parseInt(st1.nextToken());
        M = Integer.parseInt(st1.nextToken());
        A = new int[N];
        S = new int[N];
        StringTokenizer st2 = new StringTokenizer(br.readLine(), " ");
        for (int n = 0; n < N; n++) {
            A[n] = Integer.parseInt(st2.nextToken());
            if (n == 0) S[n] = A[n];
            else S[n] = S[n - 1] + A[n];
        }

        // process
        int i, j, result;
        for (int m = 0; m < M; m++) {
            StringTokenizer st3 = new StringTokenizer(br.readLine(), " ");
            i = Integer.parseInt(st3.nextToken()) - 1;
            j = Integer.parseInt(st3.nextToken()) - 1;
            if (i == 0) {
                result = S[j];
            } else {
                result = S[j] - S[i - 1];
            }
            bw.write(result + "\n");
        }

        bw.flush();
        br.close();
        bw.close();
    }

    public static void main(String[] args) throws IOException {
        Ex11659_240207 my = new Ex11659_240207();
        my.run();
    }
}
```

![Untitled](image/prefix_sum4.png)

## 후기

- 입력 받는 수는 1,000보다 작거나 같은 수이지만 입력받는 개수는 100,000까지도 가능하므로 합 배열 S는 long형으로 만들었다면 더 좋았을듯