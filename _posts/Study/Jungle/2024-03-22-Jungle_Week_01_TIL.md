---
no_link_title:    false
no_excerpt:       false
hide_image:       true

layout:           post
cover:            false
sidebar:          false
order:            0      
toc:              true

image:
  path:           /assets/img/banner/jungle_banner.png

title:            크래프톤 정글 1주차 개발일지
hide_title:       false
description:      KRAFTON JUNGLE Week 01
hide_description: false
date:             2024-03-21 22:00:00
featured:         false
categories:       [study]
tag:              [jungle]
---

## JUNGLE TIL-240322 (W01)

* toc
{:toc}

### 1. BOJ Issue
#### [9020. 골드바흐의 추측](https://www.acmicpc.net/problem/9020)
아이디어만 떠오르면 쉽게 풀리는데.. 아이디어를 생각하기가 어렵다
{:.note}

```python
def is_prime(num):                    # 소수인지 확인하는 함수
    if num == 1:
        return False
    for k in range(2, num):
        if num % k == 0:
            return False
    return True

def gold(a, b):
    if is_prime(a) and is_prime(b):   # 만약 수의 쌍이 둘다 소수이면,
        print(a, b)                   # 출력
    else:
        a -= 1                        
        b += 1
        gold(a, b)                    # 아니라면 a는 1씩 감소, b는 1씩 증가시키며 체크

T = int(input())

for i in range(T):
    n = int(input())
    gold(n//2, n//2)                  # 중간부터 시작해야 차이가 가장 적은 쌍부터 출력
```
> - 처음 시도한 코드는 `n`까지의 모든 소수를 리스트에 넣은 다음, `n`에서 리스트에 있는 소수들을 뺀 값을 `is_prime`으로 체크하는 방식이었다.
> - 그러나 반복문을 꽤 많이 돌기에 역시나 시간 초과가 났다. (물론 이 알고리즘애서도 풀 수 있는 방법이 있다.)
> - 어차피 입력받을 수가 짝수여서 홀수의 합으로 이루어지기에 가능한 쌍을 먼저 추출해 각각 소수인지 체크하는 방식이 훨씬 빠르다. 

#### [1914. 하노이 탑](https://www.acmicpc.net/problem/1914)
개인적으로 가장 흥미로웠던 문제!!
{:.note}

```python
def hanoi(n, start, end):
    if n > 1:
        hanoi(n-1, start, 6-start-end)    # 과정 1

    print(f'{start} {end}')               # 과정 2

    if n > 1:
        hanoi(n-1, 6-start-end, end)      # 과정 3

N = int(input())

print(2**N - 1)                           # 하노이 이동 횟수

if N <= 20:
    hanoi(N, 1, 3) 
```
> **하노이의 과정** (재귀적으로 반복)
> 1. 가장 큰 원판을 제외한 나머지 원판들을 중간 기둥으로 옮긴다.
> 2. 가장 큰 원판을 목표 기둥으로 옮긴다.
> 3. 중간 기둥에 있는 나머지 원판들을 목표 기둥으로 옮긴다. 

#### [9663. N-Queen](https://www.acmicpc.net/problem/9663)
가장 어렵고 오래걸렸던 문제..
{:.note}

- 처음에 2차원 배열로 코드를 짰다가 시간 초과로 인해 **1차원 배열**로 변경했다.
- 어차피 한 열에 하나의 퀸만 들어갈 수 있으므로 모든 좌표를 나타낼 필요가 없다.

<br>

**✔ 방법 1** <br>
[연구소 문제](https://youjuice.github.io/Posts/Baekjoon_14502/)를 풀어봤다면 아이디어는 금방 떠오른다. 문제는 구현이 어렵다. 
```python
def visit(a):   # 방문처리
    for i in range(a):
        if chess[i] == chess[a]:                      # 행, 열 체크
            return False
        if abs(a - i) == abs(chess[a] - chess[i]):    # 대각선 체크
            return False
    return True
```
> 방문을 체크하는 함수 (**안전한지 확인**하는 함수)
> - 이미 같은 열에 퀸이 존재한다면 -> False
> - 대각선에 퀸이 존재한다면 -> False

```python
def queens(x):
    global count
    if x == n:                # 모든 퀸이 배치되었다면,
        count += 1            # count
        return
    for i in range(n):        
        chess[x] = i          # 퀸 배치
        if visit(x) is True:  # 배치 가능하다면?
            queens(x + 1)     # 다음 행 퀸 배치
```
> - 여기서 **백트래킹** 방법이 적용된다.
> - 우선 퀸을 배치하고 배치가 가능하다면, 다음 행에 퀸을 배치한다.

```python
n = int(input())
count = 0
chess = [0] * n

queens(0)
print(count)
```
> 입력받고 결과값 출력

<br>

**✔ 방법 2**<br>
그러나 위의 방법은 pypy3로는 가능하지만 python으로 제출했을 때 시간초과가 난다. 그래서 생각해본 최적화 방법,,
```python
N = int(input())
visited = [0] * N
up_cross = [0] * (2*N-1)       # / 대각선 2N-1개
down_cross = [0] * (2*N-1)     # \ 대각선 2N-1개
count = 0


def queens(i):
    global count
    if i == N:
        count += 1
        return
    for j in range(N):
        if visited[j] == 1:     # 방문 여부 체크
            continue

        a = i + j               # up_cross 라벨링
        b = i - j               # down_cross 라벨링

        if up_cross[a] == 1 or down_cross[b] == 1:      # 대각선 체크
            continue

        visited[j] = up_cross[a] = down_cross[b] = 1    # 방문 체크
        queens(i + 1)
        visited[j] = up_cross[a] = down_cross[b] = 0    # 백트래킹!!

queens(0)
print(count)
```
> - 위 방식과 기본적인 원리는 같다. (재귀, 백트래킹)
> - 하지만 `visit` 함수를 통해 따로 체크하는 방식이 아닌 대각선 체크 리스트를 활용하는 것이다.
> - `up_cross`와 `down_cross` 리스트를 만든 다음, 각각의 대각선에 **라벨링**을 하는 방식이다.
> - 이를 활용해 대각선을 체크하고 행,열 방문을 체크해 퀸을 배치한다. 

### 2. Keywords
#### 재귀 (Recursion)
- 함수가 자기 자신을 호출하는 것
- 주어진 문제를 더 작은 부분으로 분할하여 해결하는데 사용
- But, 재귀 호출이 너무 깊어지면 스택 오버플로우와 같은 문제가 발생할 수 있음

##### 💡 Example
✔ **반복문**을 사용한 팩토리얼 계산:
```python
def factorial_iterative(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

# 사용 예시
print(factorial_iterative(5))
```

✔ **재귀**를 사용한 팩토리얼 계산:
```python
def factorial_recursive(n):
    if n == 0:
        return 1
    else:
        return n * factorial_recursive(n - 1)

# 사용 예시
print(factorial_recursive(5))
```
