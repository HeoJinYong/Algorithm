# 알고리즘문제풀이(파이썬)

* ## 백준

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





* ## 파이썬알고리즘(자료)

1. 섹션2

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

   

   ### - 섹션

