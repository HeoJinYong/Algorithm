# 알고리즘문제풀이(파이썬)

## 백준

1. [백준단계별로풀기](https://www.acmicpc.net/step/1)

```python
a ,b = map(int,input().split())
+ : 더하기
- : 빼기
* : 곱하기
/ : 나누기
// : 몫
% : 나머지
  \를 출력하기 위해서는 \\를 사용
```

210209





## 파이썬알고리즘(자료)

- 섹션2

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/1. k번째 약수/in1.txt", 'rt')

n , k = map(int,f.read().split())
cnt = 0
for i in range(1,n+1):
  if n%i == 0:
    cnt+=1
  if cnt == k:
    print(i)
    sys.exit()

print(-1)
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/2. K번째 수/in1.txt", 'rt')
z = f.read().split("\n")
n = int(z[0])

for i in range(1,n+1):
  n,s,e,k = map(int,z[2*i-1].split(" "))
  a = list(map(int,z[2*i].split(" ")))
  a = a[s-1:e]
  a.sort()
  print("#%d %d" %(i, a[k-1]))
  print(a)
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/3. k번째 큰 수/in1.txt", 'rt')
z = f.read().split("\n")
n,k = map(int,z[0].split(' '))
dff = list(map(int,z[1].split(" ")))
tem = set()

result = list(combinations(dff, 3))
for i in range(len(result)):
  tem.add(sum(result[i]))

res = list(tem)
res.sort(reverse=True)
print(res[k-1])
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/4. 대표값/in1.txt", 'rt')
z = f.read().split("\n")
n = int(z[0])
dff = list(map(int,z[1].split(" ")))
total = sum(dff)

ave = total / n
ave = ave + 0.5
ave = int(ave)
min = 9999999999999
for idx, x in enumerate(dff):
    tmp=x-ave
    if tmp<min:
        min=tmp
        score=x
        res=idx+1  #순서는 +1해줘야한다.
    elif tmp==min:  #1.여러 개일 경우 먼저 점수가 높은 학생의 번호
        if x>score:
            score=x
            res=idx+1
print(ave, res)
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/5. 정다면체/in1.txt", 'rt')
z = f.read()
n, m = map(int,z.split(" "))
k = []
for i in range(1,n+1):
  for j in range(1,m+1):
    k.append(i+j)

z = [0]*(max(k)+1) #1 부터 max까지 횟수를 구하기 위한 기준

for i in k:
  for j in range(1,max(k)+1):
    if i == j:
      z[j] += 1

for a ,b in enumerate(z):
  print(a,b)
  if b == max(z):
    print(a)
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/6. 자릿수의 합/in1.txt", 'rt')
z = f.read().split("\n")
n = int(z[0])
m = list(map(str,z[1].split(" ")))
z = [0]*n

def digit_sum(n,m):
  for i in range(n): #갯수 반복
    for j in range(len(m[i])): #자릿수에 대한 합 z에 넣어주기
      z[i] += int(m[i][j])

digit_sum(n,m)

for i in range(len(z)):
  if z[i] == max(z):
    print(m[i])
    break
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/7. 소수(에라토스테네스 체)/in3.txt", 'rt')
n = int(f.read())

ch = [1] * (n+1) # N까지 모든 자리에 대한 1을 대입
cnt = 0
for i in range(2,n+1):
  if ch[i]==1:
    for j in range(2*i,n+1,i):   #배수가 되는것 다 1을 추가시켜준다
      ch[j] += 1

print(ch)
for i in range(len(ch)):
  if ch[i] == 1:
    cnt += 1 #1인 것을 구하며 카운트 해준다.

print(cnt-2) #0과1은 제외시켜줘야 하므로 2개를 빼준다.
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/8. 뒤집은 소수/in2.txt", 'rt')
z = f.read().split("\n")
n = int(z[0])
m = list(map(str,z[1].split(" ")))
tem = []

def reverse(x):
  x = x[::-1]
  return x

def isPrime(x):
  ch = [1] * (100001) # N까지 모든 자리에 대한 1을 대입
  for i in range(2,100001):
    if ch[i]==1:
      for j in range(2*i,100001,i):   #배수가 되는것 다 1을 추가시켜준다
        ch[j] += 1
  if ch[x] == 1 and x != 1:
    return True


for i in m:
  tem.append(int(reverse(i)))

for j in tem:
  if isPrime(j) == True:
    print(j)
```

```python
f = open("/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/9. 주사위 게임/in1.txt", 'rt')
z = f.read().split("\n")

n = int(z[0])
m = [] #각 주사위에 합을 구한 것 대입시키기 위해 리스트

for i in range(1,n+1): #각 줄 별 합 구해서 리스트에 대입하기
  res = 0
  df = list(map(int,z[i].split(" "))) #3개 숫자를 리스트 형식으로 받음
  df.sort()
  a,b,c = df
  if a == b and b == c:
    res = 10000+a*1000
    m.append(res)
  elif a==b or a==c:
    res = 1000+a*100
    m.append(res)
  elif b==c:
    res = 1000+b*100
    m.append(res)
  else:
    res = c*100
    m.append(res)

print(m)
print(max(m))
```

```python
f = open("/gdrive/MyDrive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 2/10. 점수 계산/in3.txt", 'rt')
z = f.read().split("\n")
n = int(z[0])
df = list(map(int,z[1].split(" ")))

res = [0] * n
if df[0]==1:
  res[0] = 1

for i in range(1,len(df)):
  if df[i] == 1:
    res[i] = res[i-1]+1

print(sum(res))
```



- 섹션3

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/1. 회문 문자열 검사/in1.txt","rt")
f = data.read().split("\n")
n = f.pop(0)

m = []
k = []

for i in f:
  m.append(i.lower())

for i in range(len(m)):
  k.append(m[i][::-1])
  if m[i] == k[i]:
    print("#"+str(i+1)+" Yes")
  else:
    print("#"+str(i+1)+" No")
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/2. 숫자만 추출/in1.txt","rt")
f = data.read()
res = ""
for i in range(len(f)):
  if f[i].isdigit() == True:
    res += f[i]

res = int(res)
cnt = 0
for i in range(1,res+1):
  if res%i == 0:
    cnt+=1
    
print(res)
print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/4. 두 리스트 합치기/in1.txt","rt")
f = data.read().split("\n")
k = []
for i in range(len(f)):
  if i%2 == 1:
    x = list(map(int,f[i].split(" ")))
    k += x
k.sort()
print(k)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/5. 수들의 합/in2.txt","rt")
f = data.read().split("\n")
n,m = map(int,f[0].split(" "))
a = list(map(int,f[1].split(" ")))
# print(n,m)
# print(a)
cnt = 0
for i in range(n):
  res = a[i]
  for j in range(i+1,n):
    res += a[j]
    if res == m:
      cnt += 1
print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/6. 격자판 최대합/in1.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
k = []
max = 0
for i in range(n):  #각 행별로의 합을 구한 후 max값 지정
  n_i = list(map(int,f[i].split(" ")))
  k.append(n_i)
  if sum(n_i) > max:
    max = sum(n_i)

for i in range(n):  #열 별로의 합 구한 후 max 지정
  res = 0
  for j in range(n):
    res += k[j][i]
    if max < res:
      max = res
for i in range(n):  #우 하단 대각선 구한 후 max 지정
  res = 0
  res += k[i][i]
  if max < res:
    max = res
for i in range(n): #우 상단 대각선 구한 후 max 지정
  res = 0
  res += k[-i][-i]
  if max < res:
    max = res

max
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/7. 사과나무/in1.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
k = n//2
z = []
res = 0

for i in range(n):                #[2,1,0,1,2]를 통해 앞뒤에 지우는 것을 반복하는 것을 통해 구함
  if k-i > 0:
    z.append(k-i)
  else:
    z.append(-k+i)

for i in range(n):
  df = list(map(int,f[i].split(" ")))
  for j in range(z[i]):
    df.pop(0)
    df.pop(-1)
  res += sum(df)

print(res)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/9. 봉우리/in3.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
k = []
z = [0] * (n+2)
k.append(z)
for i in range(n):
  n_i = list(map(int,f[i].split(" ")))
  k.append([0]+n_i+[0])
k.append(z)

cnt = 0
for i in range(1,n+1):
  for j in range(1,n+1):
    tem = k[i][j]
    if tem > k[i-1][j] and tem > k[i+1][j] and tem > k[i][j-1] and tem > k[i][j+1]:
      cnt += 1

print(cnt)
```

```python
import sys

data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 3/10. 스도쿠 검사/in1.txt","rt")
f = data.read().split("\n")
k = []

for i in range(9):
  n_i = list(map(int,f[i].split(" ")))
  k.append(n_i)

for i in range(9): #행과 열에 합이 45인지에 대한 여부 확인
  tem = 0
  tem = sum(k[i])
  if tem != 45:
    print("No")
  else:
    tem_ = 0
    for j in range(9):
      tem_ += k[j][i]
    if tem_ != 45:
      print("No")

z_1 = []
z_2 = []
z_3 = []
z_4 = []
z_5 = []
z_6 = []
z_7 = []
z_8 = []
z_9 = []

for i in range(3): #각 3 X 3 에서의 만족을 하는지에 대한 여부 확인
  for j in range(3):                                 # 0 1 2 
    z_1.append(k[i][j])                             # 3 4 5
    z_2.append(k[i][j+3])                           # 6 7 8
    z_3.append(k[i][j+6])
    z_4.append(k[i+3][j])
    z_5.append(k[i+3][j+3])
    z_6.append(k[i+3][j+6])
    z_7.append(k[i+6][j])
    z_8.append(k[i+6][j+3])
    z_9.append(k[i+6][j+6])

for i in range(1):
  if sum(z_1) != 45:
    print("NO")
    break
  if sum(z_2) != 45:
    print("NO")
    break
  if sum(z_3) != 45:
    print("NO")
    break
  if sum(z_4) != 45:
    print("NO")
    break
  if sum(z_5) != 45:
    print("NO")
    break
  if sum(z_6) != 45:
    print("NO")
    break
  if sum(z_7) != 45:
    print("NO")
    break
  if sum(z_8) != 45:
    print("NO")
    break
  if sum(z_9) != 45:
    print("NO") 
    break
```

- 섹션4 [그리디_탐욕알고리즘(정렬을 통한 미리 제거) , 이분탐색(MID사용)]

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/1. 이분검색/in1.txt","rt")
f = data.read().split("\n")
n,m = map(int,f.pop(0).split(" "))
x = list(map(int,f[0].split((" "))))
x.sort()

lt=0
rt=n-1

while lt <= rt:
  mid = (lt+rt)//2
  if x[mid] == m:
    print(mid+1)
    break
  elif x[mid] > m:
    rt = mid - 1
  else: 
    lt = mid + 1
```

```python
######어렵다######
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/4. 마구간 정하기/in2.txt","rt")
f = data.read().split("\n")
n,c = map(int,f.pop(0).split(" "))
x = list(map(int,f))
x.sort()
print(n,c)
print(x)

def Count(len):
    cnt=1
    ep=x[0]
    for i in range(1, n):
        if x[i]-ep>=len:
            cnt+=1
            ep=x[i]
    return cnt

lt=0
rt=x[n-1]
while lt<=rt:
    mid=(lt+rt)//2
    print(mid,Count(mid),lt,rt)
    if Count(mid) < c:
        rt=mid-1
    else:
        res=mid
        lt=mid+1

print(res)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/5. 회의실 배정/in1.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
meeting=[]
for i in range(n):
    a, b=map(int, f[i].split(" "))
    meeting.append((a, b))
meeting.sort(key=lambda x : (x[1], x[0]))  #meeting을 끝나는시간 -> 시작하는시간 순으로 정렬해주기 [이게 핵심]
print(meeting)
et=0
cnt=0
for x, y in meeting:
    if x>=et:
        et=y
        cnt+=1
        print(et)
print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/6. 씨름선수/in2.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
person=[]
for i in range(n):
    a, b=map(int, f[i].split(" "))
    person.append((a, b))
person.sort(reverse=True)  #키는 큰거부터 작은순으로 나열했기에 키는 제외 몸무게만 크면 된다!
print(person)
largest=0
cnt=0
for x, y in person:
    if y>largest:
        largest=y
        cnt+=1
        print(largest)
print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/7. 창고 정리/in2.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
m = int(f.pop(1))
x = list(map(int,f[0].split(" ")))
print(x)
for a in range(m): #m번 실행하는데 가장 큰 곳을 찾아서 -1 가장 작은 곳 찾아서 +1
  max = 0
  min = 99999999999
  for i in range(n):
    if x[i] > max:
      max = x[i]
    if x[i] < min:
      min = x[i]
  x[x.index(max)] = max -1
  x[x.index(min)] = min +1
  
print(x)
x.sort()
print(x[-1]-x[0])
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/8. 침몰하는 타이타닉/in3.txt","rt")
f = data.read().split("\n")
n, m = map(int,f.pop(0).split(" "))
x = list(map(int,f[0].split(" ")))
x.sort(reverse=True)
y = []
while x:
  tem = x[-1] + x[0]  #2명이하로만 탈 수 있다는 조건 때문에 [가장 큰 + 가장 작은]
  if len(x) == 1:
    y.append(x[0])
    break
  if tem <= m :
    y.append([x.pop(0),x.pop(-1)])
  else:
    y.append([x.pop(0)])

print(y)
print(len(y))
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/9. 증가수열 만들기/in3.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f[0].split(" ")))
y = []
res = ""
if x[0]<=x[-1]:  #처음시작을 어디서 뽑을지에 대한 판단 기준
  y.append(x.pop(0))
  res += "L"
else:
  y.append(x.pop(-1))
  res += "R"


while x: #뽑은 기준에 따라 선택
  tem = y[-1]
  if x[0]>tem and x[-1]>tem:  #둘다 기준보다 클 경우 둘다를 비교
    if x[0]<=x[-1]:
      y.append(x.pop(0))
      res += "L"
    else:
      y.append(x.pop(-1))
      res += "R"
  if x[0]>tem and x[-1]<=tem:
    y.append(x.pop(0))
    res += "L"
  if x[0]<=tem and x[-1]>tem:
    y.append(x.pop(-1))
    res += "R"
  if x[0]<=tem and x[-1]<=tem: #마지막으로 둘다 작게 되면 종료
    break

print(len(y))
print(res)
```

```python
##생각필요 각자리 별로 1부터 시작하기 때문에 1에 대한 것 적용하고 
##2에 대한 것 적용 하지만 1에 대해 적용한 것이 2에 어떤 식으로 영
##향을 줄지 생각
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 4/10. 역수열/in1.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f[0].split(" ")))
print(x)
z = [0]*n

for i in range(n):
  for j in range(n):
    if x[i]==0 and z[j]==0:
      z[j] = i+1
      break
    elif z[j] == 0 and x[i] != 0:
      x[i] -= 1

print(z)
```

- 섹션5[스택,큐,해쉬,힙] 매우중요 🌟 🌟 🌟 🌟 🌟 🌟 🌟 🌟

```python
from collections import deque as dq 
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/1. 가장 큰 수/in1.txt","rt")
n,m = map(int,data.read().split(" "))
x = list(map(int,str(n)))
y = []
for i in x: #가장 앞에 자리 수에 기준으로 선택한 후 그것에 따라 뒤에 값과 비교하여 횟수도 줄여주고
  while y and m>0 and y[-1]<i:  # 과정 반복 [크기는 앞자리 수가 클수록 더욱 커진다는 것을 명심]
    y.pop()
    m -=1
  y.append(i) #Y에 추가한 후 y를 결과 값으로 도출

res=''.join(map(str, y))
print(res)
```

```python
####어려움####
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/2. 쇠막대기/in1.txt","rt")
f = data.read()
x = []
cnt = 0
for i in range(len(f)):
  if f[i] == '(':
    x.append(f[i])
  else:
    x.pop()
    if f[i-1] == '(':
      cnt += len(x)  #중복으로 포함되는 것을 생각
    else:
      cnt += 1 #오로지 한가지가 두개로 나뉘는 것
      
print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/3. 후위표기식 만들기/in4.txt","rt")
f = list(map(str,data.read()))
res = ""
tem = []
f = ['3','*','2','*','5','*','7','*','10']
for x in f:
  if x.isdigit() == True:
    res += x
  else:
    if x == '(':
      tem.append(x)
    if x == ')':
      while tem and tem[-1]!= '(':
        res+=tem.pop()
      tem.pop()  #"("를 빼주는 과정                       #사칙연산 우선순위 생각 곱/나누기는 먼저나오는 것 먼저
    if x == "+" or x=="-":                                # + , -도 마찬가지로 먼저나오는 것 먼저
      while tem and tem[-1]!= '(':                        # 3 + 2 - 10 = 3 2 + 10 - 으로 나온다
        res+=tem.pop()
      tem.append(x)
    if x == "*" or x =="/":
      while tem and (tem[-1] == '/' or tem[-1] == '*'):   # 3 * 2 / 10 = 3 2 * 10 / 으로 나온다
        res+=tem.pop()
      tem.append(x)
while tem:
  res+=tem.pop()

res
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/4. 후위식 연산/in5.txt","rt")
f = list(map(str,data.read()))
tem = []

for x in f:
  if x.isdigit() == True:
    tem.append(int(x))
  else:
    if x =="+":
      tem_ = tem.pop(-2) + tem.pop(-1)
      tem.append(tem_)
    if x =="*":
      tem_ = tem.pop(-2) * tem.pop(-1)
      tem.append(tem_)
    if x =="/":
      tem_ = tem.pop(-2) / tem.pop(-1)
      tem.append(tem_)
    if x =="-":
      tem_ = tem.pop(-2) - tem.pop(-1)
      tem.append(tem_)

res =''.join(map(str,tem))
print(res)
```

```python
from collections import deque as dq 
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/5. 공주구하기/in5.txt","rt")
n,m = list(map(int,data.read().split(" ")))
dq = dq()
for i in range(1,n+1):
  dq.append(i)
while dq:
  if len(dq)==1:
    print(dq.popleft())
    break
  else:
    for j in range(1,m+1):  
      if j == m:  #m을 외친 사람을 지워준다.
        dq.popleft()
      else: #m이 아닌 사람을 뒤로 꼬리물기 식 (순환)
        dq.append(dq.popleft()) 
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/6. 응급실/in5.txt","rt")
f = data.read().split("\n")
n,m = map(int,f.pop(0).split(" "))
x = list(map(int,f.pop(0).split(" ")))
y = [0]*n
y[m] = 1 #M번째환자에 대한 기준을 정해주기 위해서 적용
cnt = 0

while x:
  k = max(x)
  if x[0] == k:
    x.pop(0) #위험도가 높았던 것은 위험도 차례에서 제거
    tem = y.pop(0) # 순서에서도 제거
    cnt += 1
    if tem == 1: #근데 순서에서 제거 시켜줬던 것이 M이라는 위에서 정해준 기준이랑 같다면 끝내기
      print(cnt)
      break
  else:
    x.append(x.pop(0)) #위험도에 대한 순환
    y.append(y.pop(0)) #순번을 정했던 거에 대한 순환
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/7. 교육과정 설계/in5.txt","rt")
f = data.read().split("\n")
m = f.pop(0)
n = int(f.pop(0)) 
x = []
for i in range(n):
  x.append(f.pop(0))
while x:
  a = x.pop(0)
  res = []
  for b in m:
    if b in a:
      res.append(a.index(b))
    else:
      continue
  tem1 = res.copy()  #얻어진 인덱스값
  res.sort()         #정렬을 해준 인덱스값
  if res == tem1:    #두개를 비교해주는 것으로 필수과목 순서가 맞는지 확인가능
    if len(res) != len(m): #주어진 필수과목은 다 이수해야하기 때문에 그것에 맞는 갯수가 일치해야함
      print("NO")
    else:
      print("Yes")
  else:
    print("No")
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/8. 단어찾기/in5.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
k = list(map(str,f))
x = set(k[:n]) #기준이 되는 단어 [n개]
y = set(k[n:]) #쓰여진 단어 [n-1개]
result = x-y #쓰여지지 않은 단어 출력
print(result)
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/9. 아나그램(구글)/in5.txt","rt")
f = data.read().split("\n")
x1 = list(map(str,f.pop(0)))
x2 = list(map(str,f.pop(0)))
x1.sort() #그냥 정렬시킨다음에 같으면 YES 아니면 NO
x2.sort()
if x1 == x2:
  print("Yes")
else:
  print("No")
```

```python
#딕셔너리를 이용한 방법 (시간복잡도 가장 우수)
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/9. 아나그램(구글)/in5.txt","rt")
f = data.read().split("\n")
x1 = list(map(str,f.pop(0)))
x2 = list(map(str,f.pop(0)))
sH=dict()
for x in x1:
    sH[x]=sH.get(x, 0)+1
for x in x2:
    sH[x]=sH.get(x, 0)-1

for x in a:
    if(sH.get(x)>0):
        print("NO")
        break;
else:
    print("YES")
```

```python
import heapq as hq

data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/10. 최소힙/in1.txt","rt")
x = list(map(int,data.read().split("\n")))
heap =[]

for a in x:
  if a == -1:
    break
  if a == 0:
    print(hq.heappop(heap)) #최소힙에서 최솟값을 꺼내는 명령어
  else:
    hq.heappush(heap, a) #최소힙에 a를 입력하는 명령어
```

```python
import heapq as hq

data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 5/11. 최대힙/in1.txt","rt")
x = list(map(int,data.read().split("\n")))
heap =[]

for a in x:
  if a == -1:
    break
  if a == 0:
    print(hq.heappop(heap)[1]) #(-a,a)로 입력했기 때문에 a를 출력하기 위해 인덱스 [1]을 넣어준다.
  else:
    hq.heappush(heap,(-a,a)) #-a를 통해 더 작으면 작을수록 -를 생각해서 대입
```



- 섹션6 [기초적인 DFS]

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/1. 재귀함수란(이진수출력)/in4.txt","rt")
n = int(data.read())
res = []
def change(n):
  if n == 1:
    return res.append(1)
  res.append(n%2)
  change(n//2)

change(n)
res.reverse()

print(res)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/3. 부분집합 구하기/in2.txt","rt")
n = int(data.read())
ch = [0] *(n+1)

def DFS(v):
  if v == n+1:  #깊이가 가장 마지막에 오면 그것에 대한 마무리 지어주기
    for i in range(1,n+1): #ch안에 사용된 것을 추출하기 위한 for 문
      if ch[i] == 1:
        print(i, end="")
    print()
  else:                
    ch[v] = 1
    DFS(v+1)
    ch[v] = 0
    DFS(v+1)
    
#v는 사용 -> v+1 사용 .... -> n사용 -> 출력
#                             n미사용 -> 출력
#                       n-1 미사용 -> n 사용 -> 출력
# ..............

DFS(1)
```

```python
import sys
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/4. 합이 같은 부분집합/in5.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f.pop(0).split(" ")))
y = [0]*n

def DFS(v):
  if v == n:  
    res = []
    for i in range(n):
      if y[i] == 1:
        res.append(x[i])
    if sum(res) == sum(x)/2: #마지막까지 오면 사용한 것에 대한 리스트 = 전체의 절반 비교
      print("YES")
      sys.exit()
  else:
    y[v] = 1
    DFS(v+1)
    y[v] = 0
    DFS(v+1)

DFS(0)
print("No")

--------------------------------

##위랑 같은 문제

import sys
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/4. 합이 같은 부분집합/in1.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f.pop(0).split(" ")))
total = sum(x)

def DFS(L,sum):
  if sum > total/2:  #전체의 절반보다 크면 그냥 끝내버리기
    return     
  if L == n:  #마지막 까지 왔을 때 값에 비교
    if sum == (total-sum):
      print("Yes")
      sys.exit()
  else:
    DFS(L+1,sum+x[L]) #사용하고 다음꺼 비교 -> 결국 다음꺼도 사용하고 안하고
    DFS(L+1,sum)   #사용안하고 다음꺼 비교 -> 결국 다음꺼도 사용하고 안하고
DFS(0,0)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/5. 바둑이 승차/in5.txt","rt")
f = data.read().split("\n")
n, m = map(int,f.pop(0).split(" "))
x = list(map(int,f))
tem = 0

def DFS(L,sum):
  global tem
  if sum > n:
    return
  if L == m:
    if tem < sum <= n: #사용 된거의 합이 가방의 무게보다는 작거나 같고 tem보다는 큰!
      tem = sum
  else:
    DFS(L+1,sum+x[L])
    DFS(L+1,sum)
DFS(0,0)
print(tem)
```

```python
#############################################
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/7. 동전교환/in5.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f.pop(0).split(" ")))
print(x)
print(n)
x.reverse() # 일부러 큰 것부터 비교해주기 위해서 (빠른 처리)
m = int(f.pop(0))
print(m)
res = 99999  #가장 최소의 갯수를 구하기 위한 기준

def DFS(L,sum):
  global res
  if L >= res:  #최소 갯수 보다 크면 중단
    return
  if sum > m:   #기준에 되는 값보다 크면 중단
    return
  if sum == m:  #기준에 맞는 값이면 그것에 사용된 갯수를 비교하여 재설정
    if L < res:
      res = L
  else:
    for i in range(n): #일단 제일 큰 값부터 비교해주는 것이기 때문에
      DFS(L+1,sum+x[i]) #비교금액에 넘어가는 경우에는 재귀함수 기준 넘어감
      
DFS(0,0)
print(res)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/8. 순열 구하기/in1.txt","rt")
n, m = map(int,data.read().split(" "))
x = [i for i in range(1,n+1)]
cnt = 0
y = [0]*m #m개에 대한 리스트 넣어주기
ch = [0]*(n+1)
cnt = 0
def DFS(v):
  global cnt
  if v == m:
    for i in range(m):
      print(y[i], end = " ")
    cnt += 1
    print()
  else:
    for i in range(1,n+1):
      if ch[i] == 0: #기준이 되었던 값이 사용되지 않았으면              
        ch[i] = 1  #그것을 사용한다고 표시하고                          1. ch[1] = 1  4. ch[2] = 1    8. ch[3] = 1            13.ch[2] = 1 ...->
        y[v] = i  #그것을 결과 리스트에 넣어주고                        2. y[0] = 1   5. y[1] = 2     9. y[1] = 3
        DFS(v+1) #그다음 것을 비교한다.                                 3. DFS(1)     6. DFS(2) 종료  10. DFS(2) 종료
        ch[i] = 0 #그리고는 사용하지 않았다고 표기                                    7. ch[2] = 0    11. ch[3] = 0
DFS(0)                                                                  12. ch[1] = 0
print(cnt)
```

```python
###############################################################3
import sys
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/9. 수열 추측하기/in3.txt","rt")
n, m = map(int,data.read().split(" "))
x = [i for i in range(1,n+1)]
cnt = 0
y = [0]*(n+1)
ch = [0]*(n)
a = [1] * (n)
for i in range(1,n):               #각 위치별로 사용되는 횟수 정해주기
  a[i]= int(a[i-1]*((n-i)/i))

def DFS(L,sum):
  if sum == m and L == n:
    for i in range(n):
      print(ch[i], end=' ')
    sys.exit()
  else:
    for i in range(1,n+1):
      if y[i] == 0:
        y[i] = 1
        ch[L] = i
        DFS(L+1,sum+(ch[L]*a[L])) #각 순서별로 위에서 정해준 a리스트에서의 만큼 사용
        y[i] = 0
        
DFS(0,0)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/10. 조합 구하기/in1.txt","rt")
n, m = map(int,data.read().split(" "))
n=4
m=2
x = [i for i in range(1,n+1)]
cnt = 0
res = [0]*(n)
def DFS(v,s):
  global cnt
  if v == m:
    for i in range(m):
      print(res[i], end=" ")
    cnt +=1
    print()
  else:
    for i in range(s,n+1):  #                                
      res[v] = i           # 1. res[0] = 1   3.res[1] = 2    5.res[1] = 3
      DFS(v+1,i+1)         # 2. DFS(1,2)     4.DFS(2,3)종료  6.DFS(2,3)종료
                           # 7. res[0] = 2  ...>
DFS(0,1)
print(cnt)


-------------------------------

#위에 문제 조합으로 풀기
from itertools import combinations

data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/10. 조합 구하기/in1.txt","rt")
n, m = map(int,data.read().split(" "))

x = [i for i in range(1,n+1)]
k = list(combinations(x,m))

for i in range(len(k)):
  print(k[i])
print(len(k))
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/11. 수들의 조합/in1.txt","rt")
f = data.read().split("\n")
n, m = map(int,f.pop(0).split(" "))
x = list(map(int,f.pop(0).split(" ")))
k = int(f.pop(0))
cnt = 0
def DFS(L,s,sum):
  global cnt
  if L==m:   #마지막 까지 왔을 때 그것의 합이 6의 배수인지 확인하고 갯수 추가
    if sum%k == 0:
      cnt+=1
  else:
    for i in range(s,n):   #레벨 높이기 , 사용된 것에 대한 기준으로 s, 합구하기
      DFS(L+1,i+1,sum+x[i])  

DFS(0,0,0)
print(cnt)
```

```python
#################################################################
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 6/15. 경로탐색/in1.txt","rt")
f = data.read().split("\n")
n, m = map(int,f.pop(0).split(" "))

cnt = 0
ch = [0]*(n+1)
tem = [[0]*(n+1) for _ in range(n+1)]

ch[1] = 1
for i in range(m):
  a, b=map(int, f.pop(0).split(" "))
  tem[a][b]=1

path = []
path.append(1)                                         #ch[1] = 1 , append(1)  1을 사용한 것으로 지정해준다.

def DFS(v):
  global cnt, path
  if v==n:
    cnt+=1
    print(1)
    # for x in path:
      # print(x, end=' ')
    # print()
  else:
    for i in range(1, n+1):
      if tem[v][i]==1 and ch[i]==0:                      #1.tem[1][1] == 1 & ch[1]==0 옳지 않다 -> tem[1][2] == 1 & ch[2] == 0?   5.tem[2][3] & ch[3] == 0
        ch[i]=1                                          #2. ch[2] = 1                                                            6.ch[3] = 1
        path.append(i)                                   #3. path.append(2)                                                       7. append(3)
        print(i,ch,path)                         
        DFS(i)                                           #4. DFS(2)                                                               8. DFS(3)
        path.pop()
        ch[i]=0

print(tem)
DFS(1)
# print(cnt)
```



- 섹션7 [DFS , BFS]

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/1. 최대점수 구하기/in2.txt","rt")
f = data.read().split("\n")
n,m = map(int,f.pop(0).split(" "))
pv = []
pt = []
for i in range(n):
  a, b=map(int,f[i].split(" "))
  pv.append(a)
  pt.append(b)

res = -99999999999
def DFS(L,sum,time):
  global res
  if time > m: #시간이 기준보다 크면 리텅
    return
  if L == n : #최대 깊이 까지 왔을 때 합을 비교
    if sum > res:
      res = sum
  else:
    DFS(L+1,sum+pv[L],time+pt[L])  #사용하기 때문에 시간하고 점수를 더해줌
    DFS(L+1,sum,time)             #사용하지 않기 때문에 시간하고 점수를 더해주지 않음
DFS(0,0,0)
print(res)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/2. 휴가/in3.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
pv =[]
pt =[]
for i in range(n):
  a, b=map(int,f[i].split(" "))
  pv.append(a)
  pt.append(b)

res = -99999999999
def DFS(L,sum):
  global res
  if L > n:
    return
  if L == n :
    if sum > res:
      res = sum
  else:
    DFS(L+pv[L],sum+pt[L]) #사용하게 되면 일자를 그만큼 뒤로 미뤄줘야하고 합계는 더해준다.
    DFS(L+1,sum)           #사용하지 않으면 일자는 하루만 미루고 합계는 더해주지 않는다.

DFS(0,0)
print(res)
```

```python
#######################################
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/3. 양팔저울/in4.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f.pop(0).split(" ")))
s = sum(x)
res = set()
def DFS(L,sum):
  global res
  if L == n:
    if 0<sum<=s:  #0~전체합 사이에 존재하면 집합에 넣어준다. 나중에 비교하기 위해서
      res.add(sum)
  else:
    DFS(L+1,sum+x[L]) #무게의 기준을 더해주냐
    DFS(L+1,sum-x[L]) #무게의 기준을 빼주냐
    DFS(L+1,sum)      #아예 사용하지 않느냐
DFS(0,0)
print(s-len(res))
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/4. 동전바꿔주기/in2.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
m = int(f.pop(0))
pv = []
pt = []
for i in range(m):
  a, b=map(int,f[i].split(" "))
  pv.append(a)
  pt.append(b)
cnt = 0

print(pv,pt)

def DFS(L,sum):
  global cnt
  if sum > n:
    return
  if L == m:
    if sum == n:
      cnt+=1
  else:
    for i in range(pt[L]+1): #동전의 갯수에 대한 기준    
      DFS(L+1,sum+(pv[L]*i)) #그 금액 만큼 더해주는 것   1.DFS(1,pv[0]*(0~pt[0]))

DFS(0,0)
print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/5. 동전분배하기/in1.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = list(map(int,f))
money = [0]*3
res = 99999999999

def DFS(L):
  global res, tem
  if L == n:
    k = max(money) - min(money)
    if k < res:                         #k가 가장 작은 값이 되면 그것을 res에 대입
      tem = set()
      for i in money:                  #모든 사람의 값이 달라야하기 때문에 집합으로 갯수 비교
        tem.add(i)
      if len(tem) == 3:
        res = k
        print(tem)
  else:
    for i in range(3):
      money[i] += x[L]                     #1.money[0] += x[0]        3.money[0] += x[1]
      DFS(L+1)                             #2. DFS(1)
      money[i] -= x[L]

DFS(0)
print(res)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/7. 송아지 찾기/in4.txt","rt")
n,m = map(int,data.read().split(" "))
res = 9999999999
cnt = 0

print(n,m)

if m > n:
  while m-n >= 5:
    cnt+=1
    n += 5
if m-n == 4:
  n=m
  cnt = cnt + 2
else:
  cnt = cnt + abs(m-n)

print(cnt)
```

```python
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/8. 사과나무/in3.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
x = []
for i in range(n):
  x.append(list(map(int,f[i].split(" "))))

res = []
y = [0]*n
y[0] = n//2
y[-1] = n//2
for i in range(1,n//2):  #각 행마다 빼줘야하는 갯수 정리
  y[i] = y[i-1] - 1
  y[-i-1] = y[-i] - 1

for i in range(n):
  a = x[i]
  for j in range(y[i]):
    a.pop(0)
    a.pop(-1)
  res += a

print(sum(res))
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/9. 미로의 최단거리 통로/in2.txt","rt")
f = data.read().split("\n")
board = []
for i in range(7):
  board.append(list(map(int,f[i].split(" "))))
board[0][0] = 1   #출발점에 대한 정의
dis = [[0] * 7 for i in range(7)]
dx = [1,-1,0,0]   
dy = [0,0,1,-1]
q = dq() #가장 최근에 대한 좌표 입력해주기 위해서
q.append((0,0))

while q:
  tem = q.popleft()
  for i in range(4): # x+1, x-1, y+1, y-1
    x = tem[0] + dx[i]  #tem[0] = x , tem[1] = y
    y = tem[1] + dy[i]
    if 0<=x<=6 and 0<=y<=6 and board[x][y]==0:
      board[x][y]=1
      dis[x][y]=dis[tem[0]][tem[1]]+1
      q.append((x, y))
if dis[6][6] == 0:
  print(-1)
else:
  print(dis[6][6])
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/10. 미로탐색/in2.txt","rt")
f = data.read().split("\n")
board = []
for i in range(7):
  board.append(list(map(int,f[i].split(" "))))
board[0][0]=1
dx = [1,-1,0,0]
dy = [0,0,1,-1]
cnt = 0

def DFS(x,y):
  global cnt
  if x == 6 and y == 6:
    cnt +=1
  else:
    for i in range(4):
      xx = x + dx[i]
      yy = y + dy[i]
      if 0 <=xx<=6 and 0 <=yy<=6 and board[xx][yy]==0:
        board[xx][yy] = 1
        DFS(xx,yy)
        board[xx][yy] = 0

DFS(0,0)
print(cnt)
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/11. 등산경로/in5.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
board = []
for i in range(n):
  board.append(list(map(int,f[i].split(" "))))
dx = [1,-1,0,0]
dy = [0,0,1,-1]
cnt = 0
def DFS(x,y):
  global cnt
  if x > n or y > n:
    return
  if x == n-1 and y == n-1:
    cnt +=1
  else:
    for i in range(4):
      xx = x + dx[i]
      yy = y + dy[i]
      if 0 <=xx<=n-1 and 0 <=yy<=n-1 and board[x][y] < board[xx][yy]:
        DFS(xx,yy)

DFS(0,0)
print(cnt)
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/12. 단지번호붙이기/in3.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
board = []
for i in range(n):
  board.append(list(map(int,f[i])))

print(board)

dx = [1,-1,0,0]
dy = [0,0,1,-1]

def DFS(x,y):
  global cnt
  cnt+=1
  board[x][y]=0
  for i in range(4):
    xx=x+dx[i]
    yy=y+dy[i]
    if 0<=xx<n and 0<=yy<n and board[xx][yy]==1:
      DFS(xx, yy)

res = []
for a in range(n):
  for b in range(n):
    if board[a][b] == 1:
      cnt = 0
      DFS(a,b)
      res.append(cnt)
      
res.sort()
print(len(res))
print(res)
```

```python
from collections import deque as dq
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/13. 섬나라 아일랜드/in3.txt","rt")
f = data.read().split("\n")
n = int(f.pop(0))
board = []
for i in range(n):
  board.append(list(map(int,f[i].split(" "))))

dx = [1,-1,0,0,1,1,-1,-1] #대각선까지 포함해줘야하기 때문에
dy = [0,0,1,-1,1,-1,1,-1]

def DFS(x,y):
  global cnt
  cnt+=1
  board[x][y]=0
  for i in range(8):
    xx=x+dx[i]
    yy=y+dy[i]
    if 0<=xx<n and 0<=yy<n and board[xx][yy]==1:
      DFS(xx, yy)

res = []
for a in range(n):
  for b in range(n):
    if board[a][b] == 1:
      cnt = 0
      DFS(a,b)
      res.append(cnt)
      
res.sort()
print(len(res))
```

```python
from collections import deque
data = open("/content/gdrive/My Drive/알고리즘스터디/파이썬알고리즘_문제풀이/섹션 7/16. 사다리타기/in2.txt","rt")
f = data.read().split("\n")
board = []
for i in range(10):
  board.append(list(map(int,f[i].split(" "))))
dis = [[0]*10 for i in range(10)]

print(dis)

def DFS(x,y):
  dis[x][y] = 1  #경로해줘야한다. 했던 곳을 또 반복해서 갈 수 도 있기 때문에.
  if x == 0:
    print(y)
  else:
    if y-1>=0 and board[x][y-1]==1 and dis[x][y-1]==0:  #왼쪽으로 이동
      DFS(x, y-1)
    elif y+1<10 and board[x][y+1]==1 and dis[x][y+1]==0: #오른쪽으로 이동
      DFS(x, y+1)
    else:
      DFS(x-1, y)                                       #그냥 위로 이동

for i in range(10):
  if board[9][i] == 2:
    DFS(9,i)
```



- 섹션8

