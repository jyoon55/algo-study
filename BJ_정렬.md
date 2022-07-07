### 수 정렬하기

문제 N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.

입력 첫째 줄에 수의 개수 N(1 ≤ N ≤ 1,000)이 주어진다. 둘째 줄부터 N개의 줄에는 수 주어진다. 이 수는 절댓값이 1,000보다 작거나 같은 정수이다. 수는 중복되지 않는다.

출력 첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.

```python
x = int(input())
num_list = []
for i in range(x):
    num_list.append(int(input()))
num_list1 = sorted(num_list)
for i in range(len(num_list)):
    print(num_list1[i])
```

###  수 정렬하기2

1과 같은 문제이지만 시간을 단축하기 위한 문제

다만 주피터노트북에서 stdin이 계속 오류가 남

```python
import sys
n = int(sys.stdin.readline())
nums = []
for _ in range(n):
    nums.append(sys.stdin.readline())
for i in sorted(nums):
    sys.stdout.write(str(i)+'\n')
```

### 수 정렬하기3

똑같은 문제이고 메모리 문제를 해결하기 위함

```python
import sys

n = int(sys.stdin.readline())
num_list = [0] * 10001

for _ in range(n):
    num_list[int(sys.stdin.readline())] += 1

for i in range(10001):
    if num_list[i] != 0:
        for j in range(num_list[i]):
            print(i)
```

### 통계학

입력

 첫째 줄에 수의 개수 N(1 ≤ N ≤ 500,000)이 주어진다. 단, N은 홀수이다. 그 다음 N개의 줄에는 정수들이 주어진다. 입력되는 정수의 절댓값은 4,000을 넘지 않는다.

출력 

첫째 줄에는 산술평균을 출력한다. 소수점 이하 첫째 자리에서 반올림한 값을 출력한다.

둘째 줄에는 중앙값을 출력한다.

셋째 줄에는 최빈값을 출력한다. 여러 개 있을 때에는 최빈값 중 두 번째로 작은 값을 출력한다.

넷째 줄에는 범위를 출력한다.

```python
import sys
from collections import Counter
n = int(sys.stdin.readline())
li = []
for _ in range(n):
    li.append(int(sys.stdin.readline()))

print(round(sum(li)/n))
 

li.sort()
print(li[n//2])
 
# 최빈값 
# counter로 하면 시간초과 
cnt_li = Counter(li).most_common()
if len(cnt_li) > 1 and cnt_li[0][1]==cnt_li[1][1]: #최빈값 2개 이상
    print(cnt_li[1][0])
else:
    print(cnt_li[0][0])

print(max(li)-min(li))

```

### 소트인사이드 

문제 배열을 정렬하는 것은 쉽다. 수가 주어지면, 그 수의 각 자리수를 내림차순으로 정렬해보자.

입력 첫째 줄에 정렬하려고 하는 수 N이 주어진다. N은 1,000,000,000보다 작거나 같은 자연수이다.

출력 첫째 줄에 자리수를 내림차순으로 정렬한 수를 출력한다.

```python
n = int(input())
 
li = []
for i in str(n):
    li.append(int(i))
    
li.sort(reverse=True) # 내림차순
 
for i in li:
    print(i,end='')
```

### 좌표정렬하기

문제 2차원 평면 위의 점 N개가 주어진다. 좌표를 x좌표가 증가하는 순으로, x좌표가 같으면 y좌표가 증가하는 순서로 정렬한 다음 출력하는 프로그램을 작성하시오.

입력 첫째 줄에 점의 개수 N (1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N개의 줄에는 i번점의 위치 xi와 yi가 주어진다. (-100,000 ≤ xi, yi ≤ 100,000) 좌표는 항상 정수이고, 위치가 같은 두 점은 없다.

출력 첫째 줄부터 N개의 줄에 점을 정렬한 결과를 출력한다.

```python
N=int(input())

arr=[]
for i in range(N):
    a,b = map(int,input().split())
    arr.append((a,b))

arr.sort()

for i in range(N):
    print(arr[i][0],arr[i][1])
	
```

### 좌표 정렬하기2

1과 똑같은데 y좌표 기준으로 진행

```python
N=int(input())

arr=[]
for i in range(N):
    a,b = map(int,input().split())
    arr.append([b,a])

arr.sort()

for i in range(N):
    print(arr[i][1],arr[i][0])

```

### 단어정렬

문제
알파벳 소문자로 이루어진 N개의 단어가 들어오면 아래와 같은 조건에 따라 정렬하는 프로그램을 작성하시오.

길이가 짧은 것부터
길이가 같으면 사전 순으로

입력
첫째 줄에 단어의 개수 N이 주어진다. (1 ≤ N ≤ 20,000) 둘째 줄부터 N개의 줄에 걸쳐 알파벳 소문자로 이루어진 단어가 한 줄에 하나씩 주어진다. 주어지는 문자열의 길이는 50을 넘지 않는다.

출력
조건에 따라 정렬하여 단어들을 출력한다. 단, 같은 단어가 여러 번 입력된 경우에는 한 번씩만 출력한다.

```python
n=int(input())
arr = []

for i in range(n):
    arr.append(input())
    
set_arr = set(arr)    # 중복값을 제거하는 법을 몰랐음
arr=list(set_arr)     # set으로 중복값을 제거해준 이후에 다시 리스트로 지정해줘야함
arr.sort()            # sort는 문자열도 정렬해준다 알파벳순
arr.sort(key = len)   # 길이대로 다시 정렬

for w in arr:
    print(w)

```

### 나이순 정렬

문제
온라인 저지에 가입한 사람들의 나이와 이름이 가입한 순서대로 주어진다. 이때, 회원들을 나이가 증가하는 순으로, 나이가 같으면 먼저 가입한 사람이 앞에 오는 순서로 정렬하는 프로그램을 작성하시오.

입력
첫째 줄에 온라인 저지 회원의 수 N이 주어진다. (1 ≤ N ≤ 100,000)
둘째 줄부터 N개의 줄에는 각 회원의 나이와 이름이 공백으로 구분되어 주어진다. 나이는 1보다 크거나 같으며, 200보다 작거나 같은 정수이고, 이름은 알파벳 대소문자로 이루어져 있고, 길이가 100보다 작거나 같은 문자열이다. 입력은 가입한 순서로 주어진다.

출력
첫째 줄부터 총 N개의 줄에 걸쳐 온라인 저지 회원을 나이 순, 나이가 같으면 가입한 순으로 한 줄에 한 명씩 나이와 이름을 공백으로 구분해 출력한다

```python
# 숫자와 문자를 어떻게 분리해서 넣을 것인가가 관건
# 파이썬의 stable 정렬과 unstable 정렬을 알면 좋음

n = int(input())
arr = []

for i in range(n):
    age, name = map(str,input().split())
    arr.append([int(age),name])
    
arr.sort(key = lambda x : x[0])  # 그냥 정렬을 하면 나이 이후에 알파벳 순으로 정렬됨

for m in arr:
    print(m[0],m[1])

```

### 좌표압축

문제
수직선 위에 N개의 좌표 X1, X2, ..., XN이 있다. 이 좌표에 좌표 압축을 적용하려고 한다.

Xi를 좌표 압축한 결과 X'i의 값은 Xi > Xj를 만족하는 서로 다른 좌표의 개수와 같아야 한다.

X1, X2, ..., XN에 좌표 압축을 적용한 결과 X'1, X'2, ..., X'N를 출력해보자.

입력
첫째 줄에 N이 주어진다.

둘째 줄에는 공백 한 칸으로 구분된 X1, X2, ..., XN이 주어진다.

출력
첫째 줄에 X'1, X'2, ..., X'N을 공백 한 칸으로 구분해서 출력한다.

```python
n = int(input())
arr = list(map(int,input().split()))

arr2 = sorted(list(set(arr))) # 중복값을 제거 하면서 순서대로 세우는 좌표압축
dic = {arr2[i]:i for i in range(len(arr2))} #딕셔너리를 이용하여 arr2와 arr을 이용할 수 있도록 함

for a in arr:
    print(dic[a], end = ' ') # 띄어쓰기 안해줘서 틀렸음

```