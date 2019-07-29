# **190709** (화) | 냐항

## 1. 기본

1. 컴퓨터 조작하기

   -웹브라우저 조작하기

   ```python
   import webbrowser
   
   webbrowser.open_new()
   #그냥 열기
   webbrowser.open_new_()
   #주소를 새탭에서 열기
   
   ```

   

``ls`` 파일 내용 보기

 ``mkdir til``  til이라는 새 폴더 만들기

 ``mkdir 03_day 04_day 05_day`` 이렇게 띄어쓰길 하면 한번에 여러개 만들수도 있음

``cd til/`` til 파일에 들어가기

![](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562632219660.png)

내가 어디에 있는지

![pwd를 사용하면 어디에있는지 정확하게 알 수 있다](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562632249862.png)

pwd를 사용하면 어디에있는지 정확하게 알 수 있다



**control + ← 하면 단어 단위로 지워 줌**

**control + L 하면 제대로 볼 수 있게 해줌**

**control + ` 하면 터미널 바로 눌러짐**

**터미널 죽여라 하면 휴지통 눌어야 죽음 kill...**

**항상 수정 후 저장한 후 실행하기**

``touch 이름``  폴더 아닌 파일 만들기



``code .`` **(코드 띠어야함)**  사용하면 현제 위치에서 다시 한 번 에디터를 열어줌 (or open file 을 이용해서 마우스로 이동할수도잇음)



### 1) webbrowser 외부함수

``` python
import webbrowser

webbrowser.open('https://google.com')
#구글 열어줘
webbrowser.open_new('https://google.com')
#새 창에서 열어줘
webbrowser.open_new_tab('https://google.com')
#새 탭에서 열어줘
```

> 터미널 창

```python
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/01_Day
$ python 00_auto_browser.py
# 00 뭐시기 파일 실행시켜
```





### 2) List 활용해서 아이돌 검색결과 새 탭 나오게 하기

``https://search.naver.com/search.naver?query=검색해보기`` 하면 지절로 검색됨

```   python
import webbrowser

idols=["드림케쳐", "우주소녀", "AB6", "워너원"]

for idol in idols:
    print(idol)
    webbrowser.open_new_tab('https://search.naver.com/search.naver?query='+idol)
    print(type(i))
    ##string과 string을 붙여야하기 때문에 + 넣는다 1. : 잊지말기 2. 텝 잊지말기 3.타입함수 사용
```



![결과](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562634981920.png)





## 2. 크롤링

### 1) requests 외부함수(존나머ㅁ) 사용

```python
import requests

requests.get('주소')
#주소에 요청보내서 정보 받아줘라

requests.get('주소').text
#주소에 요청 보내서 정보 받아서 글만 뽑아줘

requests.get('주소').status_code
#주소에 요청 보내서 정보 받아서 상태만 뽑아줘
```

200이 이상적인거 404가 ㅈ같은거...

부르기

> > ``pip install requests --user `` 해서 다운받기
>
> > ``pip list`` 하면 여태까지 다운받은 목록 잇음



### 2) bs4 패키지(개멈) 사용(모듈개념)

내가 받아온 문서를 예쁘게 만들어줘

```python
from bs4 import BeautifulSoup
text = bs4.BeautifulSoup(변수, 'html.parser')
#유의미한 정보 가져오기
```

> ``pip install bs4 --user``  해서 다운받기



> id는 거의 고유하다

### 3) .select(selecter) > 리스트

``text.select('선택자')`` 

문서안 특정 내용들을 뽑아줘(select) 리스트로 뽑아죠

### 4) .select_one(selector) > string

``text.select_one('선택자')``

문서 안 특정내용을 string으로 뽑아죠



> **선택자 가져오는법** (ctrl + shift + c)
>
> 우클릭 > 검사>  Select an element 뭐시기 클릭 후 가져오고싶은 정보 클릭 > 정보가 담겨잇는 라인 블록화 > 우클 후 slect 복사



### 5) 정보 스크랩(크롤링)해보기 

```python
import requests
response = requests.get('주소').text
#원하는 정보가잇는 주소로 요청보내 응답 저장
print(response)
#정보 출력하여 확인
```



```python

#정보 조작하기 편하게 바꾸고

#바꾼 정보 중 원하는 것만뽑아서

#출력한다.
```



**control + enter 하면 중간에 바로 내려감**



### 6) enumerate()

enumerate 안 리스트 넣으면 리스트 번호와 값 2가지를 뱉는다 (tuple 형태)

숫자, 내용





### 1) 네이버 금융 KOSPI 지수 가져오기

```python
import requests
from bs4 import BeautifulSoup
#requests 와 bs4 불러오기
url = 'https://finance.naver.com/sise/'
#url 변수화
html = requests.get(url).text
#text로 요청한 후 변수화
soup = BeautifulSoup(html, 'html.parser')
#뷰티풀습사용해서 받은 자료 정리하여 변수화
kospi = soup.select_one('#KOSPI_now').text
#원하는 자료의 선택자 선택하여 select함수 사용 이때 string으로 ''해 줘야함
```



### 2) 네이버 환율 지수 가져오기

```python
import requests
from bs4 import BeautifulSoup
#requests 와 bs4 불러오기

url = 'https://finance.naver.com/marketindex/'
#url 저장

html = requests.get(url).text
#자료 불러오기
soup = BeautifulSoup(html,'html.parser')
#예쁘게 만들기

exchange = soup.select_one('#exchangeList > li.on > a.head.usd > div > span.value')
#이것만 골라와 주세염

print(f'현재의 원/달러 환율은 {exchange.text}입니다.')
#아까와 달리 exchange 정의할때 . text 여기서 해줌ㅋ
```



### 3) 네이버 실시간 검색어 가져오기



```python
import requests
from bs4 import BeautifulSoup

url ='https://www.naver.com/'
html = requests.get(url).text
soup = BeautifulSoup(html,'html.parser')
#url 서버에 요청 보내서 텍스트로 가져와서 예쁘게(파써) 만들기

names = soup.select('#PM_ID_ct > div.header > div.section_navbar > div.area_hotkeyword.PM_CL_realtimeKeyword_base > div.ah_roll.PM_CL_realtimeKeyword_rolling_base > div > ul > li .ah_k')
#print(type(names))

for idx, name in enumerate(names):
    print(f'{idx+1}위: {name.text}')
#idx가 0부터 시작되기 떄문에 1 더해주고 name은 text로 뽑아줌 
```

>  list 선택자 만드는법
>
> 
>
> ![1562639639702](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562639639702.png) ctrl + shif +c 해서 하위거 선택 한 다음 위에 올라가서 이름 잇는거 밑에거 선택![1562639601292](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562639601292.png)

> ul > li .ah_k









|                            API                            |               Crawling                |           package            |
| :-------------------------------------------------------: | :-----------------------------------: | :--------------------------: |
|             프로그래밍 하라고 준 데이터 쓰기              | 사람 보라고 준 데이터를 억지로 긁은거 | 제발 쓰라고 주는 코드 덩어리 |
| 친절 ( 무료는 아니지만 해킹할수잇다면 언제든지 사용 가능) |                                       |                              |

세상엔 수 많은 데이터들이 있고 우리는 그걸 사용할수잇다 ~ 와우 



## 3.GIT

- 분산버전관리 시스템

  코드의 history관리, 개발과정 역사 보기가능 =/=github (클라우드 서비스)

- 차이 / 수정이유 log 가능, 과거모습 복원가능

- 수정한 내용만 담기때문에 파일의 크기가 즁말 작다

  | **add**    | **커밋할 목록에 추가**                                       |
  | ---------- | ------------------------------------------------------------ |
  | **commit** | 커밋(create a snapshot) 만들기                               |
  | **push**   | 현재까지의 역사(commits)가 기록되잇는곳에 새로 생성한 커밋들 반영하기 |

  

  

  ## github에 올리는 공식

- $git add helloworld.py

- $git commit -m"" 

- > 수정명

- $git config --global user.name "John"  



ctrl + t 탭 추가

ctrl + w 닫기

ctrl +l 

앞으로 깃이 관리할거야

`` cd ..`` 파일 올라가기

``pwd`` 현재 나는 어디 위치에 잇는지

### 초기세팅

![1562649384617](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562649384617.png)

앞으로 til 폴더를 git이 관리할거야

git add . 내 폴더의 모든걸 담을거야

![1562649511512](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562649511512.png)git init 이걸 할거야

git status > 내가 잘 담았는지 확인 할 수 있는 명령어

![1562649804132](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562649804132.png)

https://github.com/nsk324/TIL.git

![1562650050955](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562650050955.png)

![1562649994729](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562649994729.png)

![1562650007830](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562650007830.png)



![1562650650583](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562650650583.png)



![1562650704259](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562650704259.png)commit 말

![1562650723422](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562650723422.png)

올려주세용~





## 끝말잇기 게임

![1562653125101](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562653125101.png)

```python

student@DESKTOP MINGW64 ~/endgame (master)
$ git add .

student@DESKTOP MINGW64 ~/endgame (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   README.md


student@DESKTOP MINGW64 ~/endgame (master)
$ git commit -m "1 turn"
[master (root-commit) b392588] 1 turn
 1 file changed, 2 insertions(+)
 create mode 100644 README.md

student@DESKTOP MINGW64 ~/endgame (master)
$ git remote add origin https://github.com/nsk324/endgame.git

student@DESKTOP MINGW64 ~/endgame (master)
$ git push origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 244 bytes | 244.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/nsk324/endgame.git
 * [new branch]      master -> master

student@DESKTOP MINGW64 ~/endgame (master)
$ cd endgame
bash: cd: endgame: No such file or directory

student@DESKTOP MINGW64 ~/endgame (master)
$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/nsk324/endgame
 * branch            master     -> FETCH_HEAD
   b392588..c6997f9  master     -> origin/master
Updating b392588..c6997f9
Fast-forward
 README.md | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)

student@DESKTOP MINGW64 ~/endgame (master)
$ git add .

student@DESKTOP MINGW64 ~/endgame (master)
$ git commit -m "3 turn"
[master b54bc31] 3 turn
 1 file changed, 2 insertions(+), 1 deletion(-)

student@DESKTOP MINGW64 ~/endgame (master)
$ git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 287 bytes | 287.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/nsk324/endgame.git
   c6997f9..b54bc31  master -> master

student@DESKTOP MINGW64 ~/endgame (master)
$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/nsk324/endgame
 * branch            master     -> FETCH_HEAD
   b54bc31..fae64d0  master     -> origin/master
Updating b54bc31..fae64d0
Fast-forward
 README.md | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)

student@DESKTOP MINGW64 ~/endgame (master)
$ git add .

student@DESKTOP MINGW64 ~/endgame (master)
$ git add .

student@DESKTOP MINGW64 ~/endgame (master)
$ git commit -m "5 turn"
[master ae7cfcf] 5 turn
 1 file changed, 2 insertions(+), 1 deletion(-)

student@DESKTOP MINGW64 ~/endgame (master)
$ git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 268 bytes | 268.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/nsk324/endgame.git
   fae64d0..ae7cfcf  master -> master

student@DESKTOP MINGW64 ~/endgame (master)
$
```

incoming current 충돌~



## Format f string

```python
#1. pyformat

name = '홍길동'
english_name = 'hong'

print('안녕하세요, {}입니다. My name is {}'.format(name, english_name))
#안녕하세요, 홍길동입니다. My name is hong

print('안녕하세요, {1}입니다. My name is {0}'.format(name, english_name))
#안녕하세요, hong입니다. My name is 홍길동

print('안녕하세요, {1}입니다. My name is {1}'.format(name, english_name))
#안녕하세요, hong입니다. My name is hong


```

ctrl+/ 시에는 주석처리 됩니다.

```python
#2. f-strings

name = '홍길동'
print(f'안녕하세요, {name}입니다.')
print('안녕하세요',name,'입니다.')
#안녕하세요, 홍길동입니다.

import random
menu = ['김밥천국', '스타벅스', '부대찌개']
lunch = random.choice(menu)
print('오늘의 점심은 {}입니다.'.format(lunch))
print(f'오늘의 점심은 {lunch}입니다.')
#오늘의 점심은 부대찌개입니다.

import random
numbers = list(range(1,46))
lotto = random.sample(numbers,6)
print(f"오늘의 행운 번호는 {sorted(lotto)}입니다.")
#오늘의 행운 번호는 [3, 6, 13, 17, 34, 43]입니다.(오름차순)



```



## 파일명 바꾸기

파일 명이 5050개 정도로 엄청 많을 때

os.chdir(r'폴더주소')

작업하는 위치 변경

```python
# Create dummy files
import os
import random

family = ['김','이','박','최','황','오','강','한','제갈','하','정','송','현','손','조']
given = ['길동','준','민준','소미','수진','지은','동해','민태','준호','세정','지훈','성우','성원']

for i in range(500):
    cmd = f"touch ./dummy/{i+1}_{random.choice(family)}{random.choice(given)}.txt"
    print(cmd)
    os.system(cmd)
    #500명의 사람들 만들기

to
```



```python
import os
#os 파일 불러오기

os.chdir(r'C:\Users\student\TIL\00_StartCamp\02_Day\dummy')
#r은 raw라는 뜻인데 ''안의 \를 그대로 봐다란말 dummy들이 있는 파일 넣어라...

for filename in os.listdir('.'):
    os.rename(filename, f'SAMSUNG_{filename}')
#현재 디렉토리에 있는 모든 파일들을 가지고 올 것입니다..
#앞의 리턴값이 리스트기때문에 가능한것

```



```python
import os
#os 파일 불러오기

os.chdir(r'C:\Users\student\TIL\00_StartCamp\02_Day\dummy')
#r은 raw라는 뜻인데 ''안의 \를 그대로 봐다란말 dummy들이 있는 파일 넣어라...

for filename in os.listdir('.'):
    os.rename(filename, filename.replace('SAMSUNG_','SSAFY_'))
```



## textfile 읽고 쓰는것

```python
#1. 파일 쓰기(옛날 방식)

f = open('ssafy.txt','w') ## w가 쓰겟다는 말임
for i in range(10):
    f.write(f'This is line {i}.\n')
    #\n하면 엔터친거처럼 개행됨.. r 붙여주면 그대로드간대..
f.close() #반드시 해줘야함.... 열엇으면...닫기...
```





udacity > 강의 질 좋음

edx > 강의 질 좋음

https://www.youtube.com/user/cs50tv

코딩도장 > 정리잘되잇음.. 강의보단 내용이 좋음

점프 투 파이선

python documentation >tutorial



```python
#2. 파일쓰기(최신방식)
with open('with_ssafy.txt','w') as f: 
    for i in range(10):
        f.write(f'This is line {i}.\n')
```

