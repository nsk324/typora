# 190710 startcamp03

## 1. 파일 읽기 

두 가지 방법이 있다.



### 파일을 읽기 신 / 구

 신 : with as 사용 > close 안해도 됨

구 : close 잊으면 큰일남





#### 1. read() 이용하여 파일 읽기

```python
#1-1. 파일 읽기(옛날 방식) - read ()
f = open('ssafy.txt', 'r') #읽다. 
all_text = f.read()  #읽겠다 파일을 문자 열로 return
print(all_text)
f.close() # 꼭 닫아주기


#1-2. 파일 읽기 (최신 방식)
with open('with_ssafy.txt','r') as f:
    all_text = f.read()
    print(all_text)
    
```



#### 2.readlines() 이용하여 파일 읽기

```python
#2-1. 파일 읽기 (옛날 방식) - readlines()
#라인을 모두 다 읽어서 리스트 만든 후 출력
f = open('ssafy.txt', 'r')
lines = f.readlines()

for line in lines:
    print(lines)
    print(line)

f.close()


#2-2. 파일 읽기(최신 방식) -readlines()
with open('with_ssafy.txt', 'r') as f:
    lines = f.readlines() #list형식으로 out
    for line in lines:
        print(line.strip())
```

readlines()는 리스트로 값을 out

**.strip() > 양쪽 공백을 지우겟다**





## 2. 리스트 형식 파일을 거꾸로 출력 후 파일 저장하기

>   writelines_ssafy
>
> 0
>
> 1
>
> 2
>
> 3
>
> 4
>
> 5 
>
> 된걸 거꾸로 새 파일 만들어보기



```python
# 파일에 잇는걸 다 가져온다 (list)/ 꺼굴로 돌린다 / 다시 파일 만든다

#1. 각각의 라인을 리스트의 요소로 불러오기
with open('writelines_ssafy.txt', 'r') as f:
    lines = f.readlines()

#2. 뒤집기
lines.reverse() #원본 뒤집기

#3. line 을 작성하기 ( 뒤집 은걸 하나씩 꺼내서 써주면 된다)

with open('reverse_ssafy.txt', 'w') as f:
    for line in lines:
        f.write(line)
```



####  reversed 매소드 사용하여 뒤집기 ( )

1) reverse(메서드) / reversed (함수) 

원본을 바꾸냐 리턴을 하냐의 차이





2)sort(메서드) / sorted (함수)



## 2. csv(comma seperated value) 확장자를 가진거 바꿔보기

csv는 엑셀로 열린다.

> **다양한 확장 툴 사용**

엑셀 뷰어 다운 네모 눌러서,,,



```python
lunch = {
    '양자강': '054',
    '김밥카페': '051',
    '순남시래기': '053'
}
#딕셔너리

#1. 방법 1
#.items() 튜플 형태로 나옴 ('양자강, '054') (0,1)
# 한글 깨짐을 막기 위해 인코딩 인자 넣어주기
with open('lunch.csv', 'w', encoding='utf-8') as f:
    for item in lunch.items():       
        f.write(f'{item[0]},{item[1]}\n')
```

``encoding='ufg-8``' 가져왔을때 깨지지 말라고 

. split(' 기준점 ')

리스트의 나열

csv를

```py
#1. split 
with open('lunch.csv','r',encoding='utf-8') as f:
    lines = f.readlines() # 리스트 타입
    for line in lines:
        print(line.strip()) # 개행되는부분들이 사라지도록
        print(line.strip().split(','))#, 를 기준으로 list 형식으로 반환
        print(type(line.strip().split(',')))


```



결과

```bash
<결과>
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/02_Day (master)
$ python 07_csv_read.py
양자강,054
['양자강', '054']
<class 'list'>
김밥카페,051
['김밥카페', '051']
<class 'list'>
순남시래기,053
['순남시래기', '053']
<class 'list'>
```



#### scv reader

```python
#2. scv reader

import csv ## csv조작할때 쓰는거

with open('lunch.csv', 'r', encoding='utf-8') as f:
    lines = csv.reader(f)

    for line in lines:
        print(line) #line 이라는 list 형태의 자료형이다.
```



결과

```python
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/02_Day (master)
$ python 07_csv_read.py
['양자강', '054']
['김밥카페', '051']
['순남시래기', '053']
```

ctrl-p : 파일 찾기

ctrl ` 위아래 왓다갓다

### 크롤링

```python
import requests
from bs4 import BeautifulSoup

html = requests.get('https://www.naver.com').text
soup = BeautifulSoup(html, 'html.parser')
tags = soup.select('#PM_ID_ct > div.header > div.section_navbar > div.area_hotkeyword.PM_CL_realtimeKeyword_base > div.ah_roll.PM_CL_realtimeKeyword_rolling_base > div > ul > li .ah_k')

for tag in tags:
    print (tag.text)
```


결과

```python
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/02_Day (master)
$ python 08_naver_rank.py
강지환
안다르 워터레깅스
현대건설
이랜드몰 반값데이
류현진 올스타전
김혜수
임은경
배지현
돌벽지
부산 지하철 파업
조선생존기
패션플러스
메이썸
진화
두올산업
화사
진관사
금나나
보스웰리아
카라스코
```



날짜 넣고싶다면

```python
import requests
from bs4 import BeautifulSoup
from datetime import datetime

html = requests.get('https://www.naver.com').text
soup = BeautifulSoup(html, 'html.parser')
tags = soup.select('#PM_ID_ct > div.header > div.section_navbar > div.area_hotkeyword.PM_CL_realtimeKeyword_base > div.ah_roll.PM_CL_realtimeKeyword_rolling_base > div > ul > li .ah_k')

for tag in tags:
    print (tag.text)

now = datetime.now()
with open('naver.txt', 'w', encoding='utf-8') as f:
    f.write(f'{now} 기준 네이버 실시간 검색어\n')
    for idx, tag in enumerate(tags):
        f.write(f'{index+1}위: {tag.text}\n')

```



결과

```txt
2019-07-10 11:30:38.149356 기준 네이버 실시간 검색어
1위: 강지환
2위: 안다르 워터레깅스
3위: 패션플러스
4위: 현대건설
5위: 이랜드몰 반값데이
6위: 임은경
7위: 김혜수
8위: 류현진 올스타전
9위: 배지현
10위: 돌벽지
11위: 부산 지하철 파업
12위: 메이썸
13위: 진관사
14위: 조선생존기
15위: 진화
16위: 화사
17위: 두올산업
18위: 카라스코
19위: 타짜3
20위: 트러블 패치

```



### 멜론 랭크

``.status_code`` 

:응답상태를 알아보기위해 > 에러 명이 나옵니다..  4번대 에러가 나오면 우리가(client) 잘못한 것입니다.



`header=뭐시기` 하면 헤더값을 줌

```python
import requests
from bs4 import BeautifulSoup

#딕셔너리에 멜론 페이지 > 검사 > 네트워크 > ctrl+r > name Headers > requests > 요청하는 사람이 헤더 정보를 넘겨줘야하는거>useragent 다 긁기



headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36'
}
response = requests.get("https://www.melon.com/chart/index.htm", headers=headers)
response.encoding = 'utf-8'
res = response.text





soup = BeautifulSoup(res, 'html.parser')
songs = soup.select('.lst50') #.는 클래스란 뜻, select는 list로 반환
for song in songs:
    rank = song.select_one('#lst50 > td:nth-child(2) > div > span.rank').text
    name = song.select_one('#lst50 > td:nth-child(6) > div > div > div.ellipsis.rank01 > span > a').text
    artist = song.select_one('#lst50 > td:nth-child(6) > div > div > div.ellipsis.rank02 > a').text
    print(f'{rank}위 : {name} / {artist}')
```



### csv 파일로 옮겨보자

```python
import requests
from bs4 import BeautifulSoup


headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36'
}
response = requests.get("https://www.melon.com/chart/index.htm", headers=headers)
response.encoding = 'utf-8'
res = response.text
soup = BeautifulSoup(res, 'html.parser')
songs = soup.select('.lst50') #.는 클래스란 뜻, select는 list로 반환


그
with open('melon.csv','w', encoding='utf-8') as f:
    for song in songs:
        rank = song.select_one('#lst50 > td:nth-child(2) > div > span.rank').text
        name = song.select_one('#lst50 > td:nth-child(6) > div > div > div.ellipsis.rank01 > span > a').text
        artist = song.select_one('#lst50 > td:nth-child(6) > div > div > div.ellipsis.rank02 > a').text
      
    f.write(f'{rank}위 : {name} / {artist}\n')
```

왜 헤더 정보 보내야해? 브라우저대신 요청을 보내야 하는데 그것이 헤더다





```bash
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/02_Day (master)
$ cd 03_Day/
bash: cd: 03_Day/: No such file or directory

student@DESKTOP MINGW64 ~/TIL/00_StartCamp/02_Day (master)
$ cd ..

student@DESKTOP MINGW64 ~/TIL/00_StartCamp (master)
$ ls
01_Day  02_Day  03_Day  04_Day  05_Day

student@DESKTOP MINGW64 ~/TIL/00_StartCamp (master)
$ cd 03_Day/

student@DESKTOP MINGW64 ~/TIL/00_StartCamp/03_Day (master)
$
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/03_Day (master)
$ code .
#열기
```

움직이기



## 문1) 문자열을 입력받아 문자열의 첫 글자와 마지막 글자를 출력하는 프로그램을 만드시오

```python

str = input('문자를 입력하세요 : ')

print(f'첫 글자는 {str[0]}')

print(f'마지막 글자는{str[-1]}.')
```



## 문2) 자연수 n이 주어질 때, 1부터 n까지 한 줄에 하나씩 출력하는 프로그램을 만드세요.

```
n = int(input('자연수를 넣어 주세요 :'))

for i in range(n):
    print(i+1)
```



## 문3) 숫자를 입력 받아 짝수/홀수를 구분하는 코드를 작성하세요

```python
number = int(input("숫자를 입력 하세요 : "))

if number % 2 == 0:
    print("짝수입니다.")
else:
    print("홀수입니다.")
```

숫자로 입력 받으려면 int(input())

```python
number = int(input("숫자를 입력 하세요 : "))

if number % 2 :
    print("홀수.")
else:
    print("짝수.")
```

false = 0

true =1

## 문)4. 표준 입력으로 국어, 영어, 수학, 과학 점수가 입력 됩니다.

국어는 90점 이상, 영어는 80점 초과, 수학은 85점 초과, 과학은 80점 이상일 때 합격 이라고 정했습니다.

(한 과목이라도 조건에 만족하지 않으면 불합격)

다음 코드를 완성하여 합격이면 True ,불합격이면 False가 출력되도록 작성하세요.

```python
국어 = int(input('국어:'))
영어 = int(input('영어:'))
수학 = int(input('수학:'))
과학 = int(input('과학:'))

if 국어>=90 and 영어>80 and 수학 > 85 and 과학 >=80 :
    print(true)
else:
    print(False)
```



### 문)5. 표준 입력으로 물품 가격 여러 개가 문자열 한 줄로 입력되고, 각 가격은 ;(세미콜론)으로 구분되어 있습니다. 

입력된 가격을 높은 가격순으로 한줄에 하나씩 출력하는 프로그램을 만드세요.

입력예시: 30000;2000;400000

출력예시 :

40000

30000

2000

```python
prices = input("물품 가격을 입력 하세요 :")



makes = prices.split(';') #; 기준 > list 형식

boxs = []#빈 리스트



for make in makes:

​    boxs.append(int(make)) 

boxs.sort(reverse=True)



for box in boxs:

​    print(box)
```



## HTML과 css



#### HTML(hypertext markup language)

링크로 넘나든다. 중요한걸 마킹해서 표시하겟다.



#### CSS(cascading style sheets)

: html을 꾸며주는 



뼈대 : 헤드테그  +바디테그

1. ! 탭 >자동으로 골격 나옴

2. title 사이에 적어보자

3. <body> 테그 안 <h1> +  tap 눌러보자

4. <p> 테그를 사용해보자

5. <ol> 을 사용해보자

< 난중에할거임>



## 파이썬 기반 flask  사용해보자

터미널에

```bash
pip install flask --user
```

in

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello world!'
```

 실행하는법

```bash
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/03_Day/01_flask (master)
$ FLASK_APP=hello.py flask run
```

path에 추가하라고 한다.

The script flask.exe is installed in 'C:\Users\student\AppData\Roaming\Python\Python37\Scripts' which is not on PATH.



우리가 어디론가 요청을 보내면, 응답을 주는데 우리가 server가 될 수 있음ㅋ

