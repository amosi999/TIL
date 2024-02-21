# 슬라이딩 윈도우

Created date: 2024년 2월 18일
Last edited date: 2024년 2월 21일

<br>

# 01 슬라이딩 윈도우

- 2개의 포인터로 범위를 지정한 다음 범위(window)를 유지한 채로 이동(sliding)하며 문제를 해결
- 투 포인터 알고리즘과 매우 비슷하고 원리도 간단하므로 문제를 풀며 이해

<br>

# 실전 문제 - DNA 비밀번호 (12891)

## 문제

![Untitled](image/slidng_window_image1.png)
![Untitled](image/slidng_window_image2.png)

[https://www.acmicpc.net/problem/12891](https://www.acmicpc.net/problem/12891)

## 풀이

범위를 유지하며 이동해 문제를 해결하는데, 이동할때마다 매번 조건에 맞는지 계산하는 게 아니라 이전 범위와 겹치는 부분은 그대로 사용하고 달라진 부분만 빼고 더하며 조건에 맞는지 검사