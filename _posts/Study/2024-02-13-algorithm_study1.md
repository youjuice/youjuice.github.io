---
last_modified_at: 2024-02-13
no_link_title:    false 
no_excerpt:       false 
hide_image:       false

layout:           post
cover:            false
sidebar:          false
order:            0

caption:          
toc:              true
toc_sticky:       true

title:            [Before JUNGLE] 1주차 알고리즘 스터디
hide_title:       false
description:      백준 알고리즘_Python
hide_description: true
date:             2024-02-13 22:31:00
featured:         false
categories:       - study
tag:              - algorithm 
                  - python
---

## [Before JUNGLE] 1주차 알고리즘 스터디

### [#1316 그룹 단어 체커](https://www.acmicpc.net/problem/1316)

> **문제**

그룹 단어란 단어에 존재하는 모든 문자에 대해서, 각 문자가 연속해서 나타나는 경우만을 말한다. 
예를 들면, ccazzzzbb는 c, a, z, b가 모두 연속해서 나타나고, 
kin도 k, i, n이 연속해서 나타나기 때문에 그룹 단어이지만, 
aabbbccb는 b가 떨어져서 나타나기 때문에 그룹 단어가 아니다.

단어 N개를 입력으로 받아 그룹 단어의 개수를 출력하는 프로그램을 작성하시오.

> **입력**

첫째 줄에 단어의 개수 N이 들어온다. N은 100보다 작거나 같은 자연수이다. 
둘째 줄부터 N개의 줄에 단어가 들어온다. 단어는 알파벳 소문자로만 되어있고 중복되지 않으며, 길이는 최대 100이다.

> **출력** 

첫째 줄에 그룹 단어의 개수를 출력한다.

<br>
**체감 난이도**: ★★★ 

알고리즘을 풀어본 적도 없는데다 기억도 가물가물한 파이썬으로 풀려니 더 감이 안잡혔다. 
체감상 이번 스터디 문제 중 가장 어려웠음..

#### Code
```python
n = int(input())
checker_list = []
count = 0

# n개의 단어를 입력받아 리스트에 저장
for i in range(n):
    input_word = input()
    checker_list.append(input_word)

# Group 단어인지 판별하는 함수
def group_checker(word):
    already_group = set()
    
    for j in range(len(word)):
        if word[j] != word[j-1] and word[j] in already_group:
            return False
        already_group.add(word[j])
    
    return True

# Group 단어의 개수 체크
for k in range(n):
    if group_checker(checker_list[k]) == True:
        count += 1
        
print(count)
```

#### Solution

##### ✔ def `group_checker`

aaabbaa처럼 이미 그룹이 끝난 문자열 이후에 중복된 문자가 나올 것을 효과적으로 판별하기 위해 
중복된 원소를 허용하지 않는 `set()`을 활용했다. 

> **set**이란?
> - 파이썬에서 제공하는 내장 자료형
> - **중복된 원소**를 허용하지 않는다.
> - 원소들 간에 **순서가 없이** 저장되어 있다.
> - 변경 가능한 자료형이다. (새로운 원소를 추가, 삭제 가능)
 

`set()`을 활용해 이미 존재하는 문자들을 `already_group`에 저장한 다음,
`word[j] != word[j-1]` 이거나 `already_group`에 이미 있는 문자가 재등장한 경우
False 처리를 했다.

---

### [#1978 소수 찾기](https://www.acmicpc.net/problem/1978)

> **문제**

주어진 수 N개 중에서 소수가 몇 개인지 찾아서 출력하는 프로그램을 작성하시오.

> **입력**

첫 줄에 수의 개수 N이 주어진다. N은 100이하이다. 다음으로 N개의 수가 주어지는데 수는 1,000 이하의 자연수이다.

> **출력** 

주어진 수들 중 소수의 개수를 출력한다.

<br>
**체감 난이도**: ★

초반에 문제를 잘못 이해해서 소수인지 확인하는 알고리즘을 짜서 틀리긴 했지만 금방 풀 수 있었다..

#### Code
```python
count = int(input())
values = map(int, input().split())
prime_count = 0

# 소수인지 판별하는 함수
def is_prime(num):
    if num == 1:
        return False         
    for i in range(2, num):
        if num % i == 0:
            return False
    return True

# 소수의 개수 체크
for num in values:
    if is_prime(num):
        prime_count += 1
        
print(prime_count)
```

#### Solution
`is_prime` 함수를 만들어서 소수인지 판별하여 True, False값을 반환하도록 하였다.
또한 함수 내에 1은 따로 **False**값을 지정하였다.

##### ✔`map(int, input().split())`
백준 알고리즘 풀이를 하면서 가장 유용하게 쓴 함수이다.

- `input()`: 사용자로부터 입력 받음
- `input().split()`: 사용자의 입력을 공백을 기준으로 나눠 리스트로 변환
- `map(int, input().split())`: 리스트의 각 요소를 정수로 변환

✘ `int()` 함수는 문자열을 정수로 변환할 수 있지만, 리스트 전체에는 적용되지 않는다. 
즉, `int(input().split())`는 작동하지 않는 함수이다.

---

### [#2798 소수 찾기](https://www.acmicpc.net/problem/2798)

> **문제**

(중략)

김정인 버전의 블랙잭에서 각 카드에는 양의 정수가 쓰여 있다. 
그 다음, 딜러는 N장의 카드를 모두 숫자가 보이도록 바닥에 놓는다. 
그런 후에 딜러는 숫자 M을 크게 외친다.

이제 플레이어는 제한된 시간 안에 N장의 카드 중에서 3장의 카드를 골라야 한다. 
블랙잭 변형 게임이기 때문에, 플레이어가 고른 카드의 합은 M을 넘지 않으면서 M과 최대한 가깝게 만들어야 한다.

N장의 카드에 써져 있는 숫자가 주어졌을 때, M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 구해 출력하시오.

> **입력**

첫째 줄에 카드의 개수 N(3 ≤ N ≤ 100)과 M(10 ≤ M ≤ 300,000)이 주어진다. 둘째 줄에는 카드에 쓰여 있는 수가 주어지며, 이 값은 100,000을 넘지 않는 양의 정수이다.

합이 M을 넘지 않는 카드 3장을 찾을 수 있는 경우만 입력으로 주어진다.

> **출력** 

첫째 줄에 M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 출력한다.

<br>
**체감 난이도**: ★★

일단 문제가 굉장히 길다.. 그리고 생각보다 까다로웠던 것 같다.

#### Code
```python
n, m = map(int, input().split())

card_list = list(map(int, input().split()))
card_list.sort()            # 순서대로 정렬

min_diff = float('inf')     # 무한대로 초기화
result = 0

# m값과 가장 차이가 적은 경우 찾기
for a in range (n):
    for b in range (a + 1, n):
        for c in range (b + 1, n):
            sum = card_list[a] + card_list[b] + card_list[c]
            diff = m - sum
            if 0 <= diff < min_diff:
                min_diff = diff
                result = m - min_diff

print(result)
```

#### Solution
`card_list`를 오름차순으로 정렬한 다음, 3장을 더할 수 있는 모든 경우의 수를 더하여 M값에 가장 가까운 값을 찾는다.
또한, M값을 넘으면 안된다는 룰이 있으므로 `0 <= diff` 조건을 추가해준다.

✘ 최솟값을 구할 것이기 때문에 `min_diff`의 값을 0이 아닌 **무한**으로 초기화 할 것!!

---

### [#7568 덩치](https://www.acmicpc.net/problem/7568)

> **문제**

우리는 사람의 덩치를 키와 몸무게, 이 두 개의 값으로 표현하여 그 등수를 매겨보려고 한다. 
어떤 사람의 몸무게가 x kg이고 키가 y cm라면 이 사람의 덩치는 (x, y)로 표시된다. 
두 사람 A 와 B의 덩치가 각각 (x, y), (p, q)라고 할 때 x > p 그리고 y > q 이라면 우리는 A의 덩치가 B의 덩치보다 "더 크다"고 말한다.

(중략)

여러분은 학생 N명의 몸무게와 키가 담긴 입력을 읽어서 각 사람의 덩치 등수를 계산하여 출력해야 한다.

> **입력**

첫 줄에는 전체 사람의 수 N이 주어진다. 그리고 이어지는 N개의 줄에는 각 사람의 몸무게와 키를 나타내는 양의 정수 x와 y가 하나의 공백을 두고 각각 나타난다.

> **출력** 

여러분은 입력에 나열된 사람의 덩치 등수를 구해서 그 순서대로 첫 줄에 출력해야 한다. 단, 각 덩치 등수는 공백문자로 분리되어야 한다.

<br>
**체감 난이도**: ★★

이것도 문제가 상당히 길다.. ~~거의 비문학 지문급.~~ 이 문제를 풀 때 출력값을 리스트로 출력했더니 틀린 답이라고 나왔다. 출력 부분도 잘 읽어봐야 할 듯..

#### Code
```python
n =int(input())

body_list = []
volume_count_list = []

# 입력값 리스트에 저장
for i in range(n):
    w, h = map(int, input().split())
    body_list.append((w, h))

# 덩치 순위를 매기는 함수
def volume(num):
    volume_count = 0
    for j in range(n):
        if body_list[num][0] < body_list[j][0] and body_list[num][1] < body_list[j][1]:
            volume_count += 1
    return volume_count + 1

# 사람들의 순위를 리스트에 저장
for k in range(n):
    result = volume(k)
    volume_count_list.append(result)
    
print(*volume_count_list)       # 언패킹(unpacking)
```

#### Solution

이 문제에서는 각 사람의 키와 몸무게 정보를 튜플로 묶어서 리스트에 넣는 방식으로 입력값을 저장했다.

> ##### ✔ 튜플과 리스트 (Tuple & List)
> - 데이터 쌍을 표현하는 방식에는 튜플과 리스트가 있는데 이 둘은 **불변성**에 따라 나뉜다.
> - **튜플**은 **불변**하므로 한 번 생성된 후에는 변경할 수 없다.
  ex. `[(1, 'apple'), (2, 'banana'), (3, 'orange')]`
> - **리스트**는 **가변**하므로 데이터를 변경하거나 추가할 수 있다.
  ex. `[[1, 'apple'], [2, 'banana'], [3, 'orange']]`
 
만약 자신보다 덩치가 큰 사람의 데이터가 있다면 `volume_count`를 1씩 더해 본인의 등수를 반환하도록 `volume`함수를 만들었다.
그리고 순위를 리스트에 저장한 다음 **언패킹(unpacking)** 한 데이터를 출력하도록 하였다.

> ✔ **언패킹 (unpacking)** 이란?
> 리스트, 튜플, 세트 등과 같은 **iterable 객체**에서 사용 할 수 있으며, * 연산자를 사용함.

---

### [#10870 피보나치 수 5](https://www.acmicpc.net/problem/10870)

> **문제**

피보나치 수는 0과 1로 시작한다. 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1이다. 그 다음 2번째 부터는 바로 앞 두 피보나치 수의 합이 된다.

이를 식으로 써보면 Fn = Fn-1 + Fn-2 (n ≥ 2)가 된다.

n=17일때 까지 피보나치 수를 써보면 다음과 같다.

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597

n이 주어졌을 때, n번째 피보나치 수를 구하는 프로그램을 작성하시오.

> **입력**

첫째 줄에 n이 주어진다. n은 20보다 작거나 같은 자연수 또는 0이다.

> **출력** 

첫째 줄에 n번째 피보나치 수를 출력한다.

<br>
**체감 난이도**: ★

이 문제는 소수 문제 정도의 난이도였다. 굉장히 쉽게 풀렸던 문제.. 

#### Code
```python
num = int(input())
f_list = [0, 1]     # 0번째, 1번째 피보나치 수는 미리 넣어둠

for i in range(2, num+1):
    new = f_list[i-1] + f_list[i-2]     # 피보나치 공식
    f_list.append(new)

print(f_list[num])      # n번째 피보나치 수 출력
```

#### Solution
n을 입력받아 피보나치 공식을 활용해 n번째 피보나치 수열의 값을 구하면 된다.
(0번째 피보나치 수와 1번째 피보나치 수는 미리 리스트에 넣어두었다.)

---

1주차 스터디 문제 풀이 끝!!!
파이썬으로 게임은 만들어봤지만 알고리즘 문제는 처음 풀어봐서 꽤 어려웠다...
그치만 푸는 과정이 생각보다 재밌다ㅎㅎ 어려운 문제 좀 구경해봤는데, 하나도 모르겠더라..

그리고 1학년 때 배운 뒤로 잘 안써서 그런가 확실히 많이 까먹은 것 같다. 기본적인 것들을 꽤 검색했다.
파이썬 문법도 한번 훑고 가야겠다. 열심히 공부해서 정글에서 잘 적응해야지..^^

이제 CS50 강의 열심히 듣자!! 그럼 20000

<br>
> 혹시 더 좋은 알고리즘 풀이가 있다면 언제든 댓글로 알려주세요 :)
