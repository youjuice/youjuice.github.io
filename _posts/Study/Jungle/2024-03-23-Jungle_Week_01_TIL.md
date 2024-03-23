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
date:             2024-03-23 12:00:00
featured:         false
categories:       [study]
tag:              [jungle]
---

## JUNGLE - 240323 (W01)

* toc
{:toc}

### 1. BOJ Issue
#### [2751. 수 정렬하기 2](https://www.acmicpc.net/problem/2751)
`sys.stdin.readline()`으로도 풀리긴 하는데 다른 정렬 방법을 사용해서 풀어보라고 만든 문제인 듯하여 병합 정렬을 사용해서 풀어보았다. 
근데 문제는 병합 정렬 방식은 pypy3로만 가능하다. (python은 시간초과 나옴..)
{:.note}

<br>

**✔ 방법 1 - `sys.stdin.readline()`**
```python
import sys

N = int(sys.stdin.readline())
n_list = [int(sys.stdin.readline()) for i in range(1, N+1)]

result = sorted(n_list)

for num in result:
    print(num)
```
> - 이렇게 풀면 python으로 시간 초과 없이 풀린다.
> - 하지만, 정렬 공부를 위해 **병합 정렬**을 활용해 풀어보았다.

<br>

**✔ 방법 2 - 병합 정렬**
```python
def divide(ex_list):
    if len(ex_list) == 1:           # 재귀 탈출 조건
        return ex_list

    mid = len(ex_list) // 2         # 중간값
    left = divide(ex_list[:mid])    # 왼쪽
    right = divide(ex_list[mid:])   # 오른쪽

    return merge(left, right)
```
> - 리스트를 반으로 나누어 두 개의 부분 리스트로 **분할**
> - 두 부분 리스트를 **병합**하여 하나의 정렬된 리스트로 합침
> - 재귀 호출의 탈출 조건은 **리스트의 길이**가 **1**이 될 때

```python
def merge(left, right):
    merge_list = []
    right_num, left_num = 0, 0 

    while len(left) > left_num and len(right) > right_num:
        if left[left_num] <= right[right_num]:
            merge_list.append(left[left_num])
            left_num += 1
        else:
            merge_list.append(right[right_num])
            right_num += 1

    merge_list.extend(left[left_num:])
    merge_list.extend(right[right_num:])

    return merge_list
```
> - 두 개의 부분 리스트를 하나의 정렬된 리스트로 합치는 함수
> - 두 부분 리스트의 요소를 비교하여 더 작은 값을 새로운 리스트에 추가

[분할 정복](#분할-정복-divide-and-conquer) 기법을 사용하여 구현
{:.note}

### 2. Keywords
#### 정렬 (Sort)
##### 선택 정렬 (Selection Sort)
```python
# 선택 정렬 (Best: O(n^2) Worst: O(n^2))
def SelectionSort(arr):
    for i in range(len(arr)):
        min_index = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]
    return arr
```
- 배열에서 **최솟값**을 찾아 첫번째 원소와 교환
- 그 다음 두번째로 작은 원소를 찾아 두번째 원소와 교환
- 위의 과정을 반복하여 전체 배열 정렬

##### 삽입 정렬 (Insertion Sort)
```python
# 삽입 정렬 (Best: O(n) Worst: O(n^2))
def InsertionSort(arr):
    for i in range(1, len(arr)):
        tmp = i
        while tmp > 0 and arr[tmp-1] > arr[tmp]:
            arr[tmp], arr[tmp-1] = arr[tmp-1], arr[tmp]
            tmp = tmp-1
    return arr
```
- 배열을 정렬된 부분과 정렬되지 않은 부분으로 나눔
- 정렬되지 않은 부분에서 원소를 선택하여 정렬된 부분의 **적절한 위치에 삽입**
- 위의 과정을 반복하여 전체 배열 정렬

##### 버블 정렬 (Bubble Sort)
```python
# 버븥 정렬 (Best: O(n^2) Worst: O(n^2))
def BubbleSort(arr):
    for i in range(len(arr)):
        for j in range(len(arr)-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr
```
- **인접한 두 원소**를 비교하며 순서가 잘못된 경우 위치를 **교환**
- 위 과정을 배열의 끝까지 반복하며 가장 큰 원소가 마지막으로 이동

##### 병합 정렬 (Merge Sort)
```python
# 병합 정렬 (Best: O(nlogn) Worst: O(nlogn)
def MergeSort(arr):
    if len(arr) < 2:
        return arr

    mid = len(arr)//2

    left = MergeSort(arr[:mid])
    right = MergeSort(arr[mid:])

    merged_array = []
    a, b = 0, 0

    while a < len(left) and b < len(right):
        if left[a] < right[b]:
            merged_array.append(left[a])
            a += 1
        else:
            merged_array.append(right[b])
            b += 1

    merged_array += left[a:]
    merged_array += right[b:]

    return merged_array
```
- 배열을 반으로 나누어 각각을 **재귀적**으로 정렬
- **정렬된 하위 배열을 병합**하여 하나의 정렬된 배열을 만듬
- 위의 과정을 반복하여 전체 배열 정렬

##### 퀵 정렬 (Quick Sort)
```python
# 퀵 정렬 (Best: O(nlogn) Worst: O(n^2))
def QuickSort(arr):
if len(arr) < 2:
return arr

    pivot = arr[len(arr)//2]
    smaller, equal, larger = [], [], []

    for num in arr:
        if num < pivot:
            smaller.append(num)
        elif num > pivot:
            larger.append(num)
        else:
            equal.append(num)

    return QuickSort(smaller) + QuickSort(equal) + QuickSort(larger)
```
- `pivot`을 기준으로 **배열을 분할**하고, `pivot`을 기준으로 작은 원소는 왼쪽으로, 큰 원소는 오른쪽으로 이동
- 이러한 과정을 **재귀적으로 반복**하여 각 부분 배열을 정렬
- 분할 및 정렬이 불가능할 때까지 이를 반복

#### 탐색 (Search)
##### 완전 탐색 (Linear Search)
```python
# 완전 탐색 1 - for문 활용
def LinearSearch(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

# 완전 탐색 2 - 재귀 활용
def LinearSearch_2(arr, target, i=0):
    if i == len(arr):
        return -1
    elif arr[i] == target:
        return i
    else:
        return LinearSearch_2(arr, target, i+1)
```
- **모든** 가능한 **경우의 수**를 직접적으로 탐색하여 해결책을 찾는 방법
- **재귀**를 활용하여 구현 가능

##### 이진 탐색 (Binary Search)
```python
# 이진 탐색
def BinarySearch(arr, target):
    start, end = 0, len(arr) - 1

    while start <= end:
        mid = (start + end) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            start = mid + 1
        else:
            end = mid - 1
    return -1
```
- 탐색 범위를 **반으로 나누어** 탐색하는 효율적인 알고리즘
- 단, 탐색 대상이 **정렬**되어 있어야 함

#### 분할 정복 (Divide and Conquer)
1. **분할 (Divide)** : 문제를 더 이상 분할할 수 없을 때까지 동일한 유형의 여러 하위 문제로 나눈다.
2. **정복 (Conquer)** : 가장 작은 단위의 하위 문제를 해결하여 정복한다.
3. **조합 (Combine)** : 하위 문제에 대한 결과를 원래 문제에 대한 결과로 조합한다.

```
function F(x):
  if F(x)가 간단 then:
    return F(x)를 계산한 값
  else:
    x 를 x1, x2로 분할
    F(x1)과 F(x2)를 호출
    return F(x1), F(x2)로 F(x)를 구한 값
```
**✔ 장점** 
> - 문제를 나눔으로써 어려운 문제를 해결할 수 있으며 효율적인 알고리즘 구상 가능
> - 문제를 나누어 해결한다는 특징상 병렬적으로 문제를 해결하는 데 큰 강점

**✔ 단점**
> - 함수를 재귀적으로 호출한다는 점에서 함수 호출로 인한 오버헤드 발생
> - 스택에 다양한 데이터를 보관하고 있어야 하므로 스택 오버플로우 발생 