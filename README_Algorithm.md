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





- 섹션6
- 섹션7
- 섹션8

