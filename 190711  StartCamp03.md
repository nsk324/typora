# 190711 | StartCamp03

## 1.html

```bash
student@DESKTOP MINGW64 ~/TIL/00_StartCamp/03_Day/01_flask (master)
$ FLASK_APP=hello.py flask run
#아니면 이렇게 하면 됨


```

> 주소창이 생깁니다. 그걸 드가면 머가 나와여 (ctrl+클릭) 후
>
>  (ctrl+C로 서버 끄기)

```bash

student@DESKTOP MINGW64 ~/TIL/00_StartCamp/03_Day/01_flask (master)
$ code ~/.bash_profile

```



```python
export FLASK_ENV=development
```



```python
from flask import Flask
import datetime

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello world!'

@app.route('/ssafy')
def ssafy():
    return '왕 크다 왕 맛있다'

@app.route('/dday')
def dday():
    today = datetime.datetime.now()
    endgame = datetime.datetime(2019, 11, 29)
    td = endgame - today
    return f'사피 1학기 종료까지 {td.days}일 남았습니다.'#일수로 나옴

@app.route('/html')
def html():
    return '<h1>This is HTML h1 tag!<h1>' #테그 열면 테그 닫아줘야함

app.route('/html_line')#/하면 클로징 의미
def html_line():
    return """
    <h1> 여러줄로 작성하자~!~!~! 우끼끼 </h1>
    <ul> #unordered
        <li>1번</li>
        <li>2번</li>
    </ul>
    """
```

return """



""" 



기능을 사용하여 여러줄을만들수있습니다.

이제 기능을 추가할 것입니다. (위의 코드에 이어서)

```python
@app.route('/greeting/<string:name>') #이름을 받아서 출력할거임.
def greeting(name):
    return f'반갑습니다. {name}님~!'  #주소/greeting/남수경 하면 드감

@app.route('/cube/<int:number>') ##세제곱을 하는걸 받을거임
def mul(number):
    return f'{number}의 세 제곱은 {number**3}입니다.'
```



### 문1) 점심 메뉴 리스트(다섯 개)에서 n명의 사람개 뽑아 출력 하기

**flask는 문자형만 뱉을 수 있습니다 그래서 무족권 str()에 감싸서 뱉어야 합니다.**

```python
import random

@app.route('/lunch/<int:person>') #이미 int로 받아옴
def lun(person):
    i = ["아몬드치킨샌드위치", "쇠고기볶음", "갈치카레구이", "빨간우동", "프라이두부샐러드"]
    j = str(random.sample(i, person))
    return f'오늘 드실 밥은 {j}입니다.'
```



### 서버가 대신 열어줄 수 있도록 해 보겠습니다~

html은 템플릿츠라는 파일에 다 넣을것입니다. flask에서 템플릿츠 한번에 드가서 뭐시기저시기

'templates' 플라스크는 기본적으로 app.py 라는 이름으로 만들어서 합니다.

탬플릿을 templates라는 파일에서 할거에요



app.py파일에서

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def hello():
    return render_template('index.html')


```

하고 템플릿츠 안에서 templates 파일 안에 index.html 만들어줌



idex.html 파일 안에서 ! + tap

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>Heading 1</h1>
</body>
</html>
```

그다음 실시

html 에서는 변수나 함수를 쓸수있나,,, 없는듯.. 



하고 템플릿츠 안에서 templates 파일 안에 greeting.html 만들어줌

greeting.html안에서

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>{{ html_name }}안녕~</h1>
</body>
</html>
```





app.py파일에서

```python
from flask import Flask, render_template

@app.route('/greeting/<string:name>')
def greeting(name):
    return render_template('greeting.html', html_name=name)
    
```

 1과 2의 가장 큰 차이점은 

1 : 엔터 누르면 <h1> 테그 안에 있던 내용이 보여졌습니다.

2: 엔터 누르면 확장되어서 내가 입력하는것까지 템플릿의 html을 통해 보여줄수있읍니다. (멍미)





### 삼승 구하기

 templates 파일 안에 cube.html 만들어줌

greeting.html안에서

```html
<body>
    <h1>{{ number }}의 세 제곱은 {{ result }} 입니다.</h1>
</body>
</html>
```



app.py파일에서

```python
from flask import Flask, render_template

@app.route('/cube/<int:number>')
def cube(number):
    result = number ** 3
    return render_template('cube.html', result=result, number=number)
```



## html 템플릿 안에서 쓰는 문법

{{ 변수 }} > 보여줄거에요

body 안 가정하는법? 

{% it 뭐시기 뭐시기 %}

{% else %}

{% endif % } 



닫아주는것까지 해야함

```html
<body>
    {% if html_name == '승연' %}
        <h2>{{ html_name }} 안녕?</h2>
    {% else %}
        <h2>{{ html_name}}님 오셨습니까ㅏ.</h2>
    {% endif %}
</body>
```



### 영화

app.py

```python
from flask import Flask, render_template

@app.route('/movie')
def movie():
    movies = ['토이스토리4', '알라딘', '스파이더맨', '비스트', '기생충']
    return render_template('movie.html', movies=movies)
```



movie.html을 템플릿 파일에 만들어바바

```html
<body>
    <h1>영화목록</h1>
    {% for movie in movies %}
        <li>{{ movie }}</li>
    {% endfor %}
</body>
```



어제는 python파일에서 그냥 아주 간편하게 문장을 보여줬다.(정적)

오늘은 variable routing을 사용하여 특정갑을 받아 그 값을 포함해서 결과를 도출한다. (동적)\

그대신  동등한 계급의 ""templates"" 안의 html 파일과 연동되어 결과를 도출하게 됩니다.

 (py 파일에서는  주소를 만듬, 대충 변수를 선정, 그리고 html에서 계산하고?▲print함)



### 핑퐁 

ping.html form+ tap

```html
<form action="">
    <input type="text"> #입력받음
    <input type="submit"> #버튼생김
</form>
```



app.py

```python
from flask import Flask, render_template

@app.route('/ping')
def ping():
    return render_template('ping.html')
```

![결과화면](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562815242809.png)

app.py

```python
from flask import Flask, render_template, request

@app.route('/pong')
def pong():
    age = request.args.get('age')
    return render_template('pong.html', age=age)
```



pong.html

```html
<h1>{{ age }}</h1>
```



함수정의

함수 실행되면 html이 열린다

머가 드가면 입력 창이 뿌려진다

pong이라는 html이 열리는데 내가 입=""력햇던게 뿌려진다.



>  **웹 서비스는 request 와 response 다.**



## 2. 

### 네이버 드가기

```python
from flask import Flask, render_template

@app.route('/naver')
def naver():
    return render_template('naver.html')
```



```html
<h1>네이버 검색</h1>
<form action="http://search.naver.com/search.naver">
    <input type="text" name="query">
    <input type="submit" value="네이버 검색"> 
</form>
```



### 구글 드가기

```python
@app.route('/google')
def google():
    return render_template('google.html')
```

```html
<h1>Google 검색</h1>
<form action="https://www.google.com/search">
    <input type="text" name="q">
    <input type="submit" value="구글검색" >
</form>
```



### 새롱ㄴ

1. mkdir 00_flask
2. touch app.py
3. mkdir templates

![1562822554186](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562822554186.png)

**플라스크 시작시, 꼭 필요한것**

```python
from flask import Flask, render_template, request

app =Flask(__name __)

@app.route('/catch')
def catch():
    retun render_template('catch.html') # catch.html을 열거야
    
```









```html
from flask import Flask, render_template, request
import requests
import random

app = Flask(__name__)

@app.route('/catch')
def catch():
    return render_template('catch.html')

@app.route('/result')
def result():
    #1. form 태그로 날린 데이터를 받는다.
    word = request.args.get('word')

#2. ARTII api로 요청을 보내 받은 응답 결과를 text로 fonts(변수)에 저장
    fonts = requests.get('http://artii.herokuapp.com/fonts_list').text

#3. fonts(str)를 fonts(list)로 바꾼다.
    fonts = fonts.split('\n')

#4. fonts(list)안에 들어있는 요소 중 하나를 선택해 font에 담는다.
    font = random.choice(fonts)

#5. 위에서 우리가 만든 word와 font를 가지고 다시 요청을 보낸다.
#요청 결과(응답)를 result에 저장한다.
    result = requests.get(f'http://artii.herokuapp.com/make?text={word}&font={font}').text

#최종적으로 result에 담긴 문자열을 result.html에서 보여준다.
    return render_template("result.html", result=result)
    
```

action : submit을 햇을대  /result 라는곳으로 갈거야

word 박스에 담아서 보낼거야.

result.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <pre>{{ result }}</pre>
</body>
</html>
```



catch.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>ASCII ART에 오신 것을 환영 합니다. ^__* </h1>
    <form action="/result">
        영단어를 입력하세요 : <input type="text" name="word">
        <input type="submit">

    </form>
</body>
</html>
```

![1562826108885](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562826108885.png)



## Dictionary 

딕셔너리에서 키는 mutable한 것들 못드감 ex) 딕셔너리, 리스트



#### 1 . Dictionary 만들기

```python
lunch = {
    '중국집':'02'
}
```



#### 2. 딕셔너리 내용 추가하기

```python
lunch = dict(중국집='02')

lunch['분식집'] = '031'
```

-함수로 dictionary 만드는 방법   처음 중국집에 ''붙이면안됩니다.

#### 3. 딕셔너리 값 가져오기

```python
idol = {
    'bts': {
        '지민':24,
        'RM':25
    }
}

print(idol['bts']['RM'])

print(idol.get('bts').get('RM'))
```



#### 4. 딕셔너리 반복문 활용하기

#### 4-1 . 기본 활용

```python
for key in lunch:
    print(key)
    print(lunch[key])
```



<메소드 활용>

#### 4-2 .items() - key, value 모두 가져오기

```python
for key, value in lunch.items():
    print(key, value)
```



#### 4-3 .values() - value만 가져오기

```python
for value in lunch.values():
     print(value)
```



#### 4-4 .keys() - key만 가져오기

```python
for key in lunch.keys():
    print(key)
```



### 문제

#### 문1) 평균을 구하시오

```python
score = {
    '수학':80,
    '국어':90,
    '음악':100
}


total_score = 0
for subject_score in score.values():
    total_score += subject_score

average_score = total_score / len(score)
print(average_score)
```

len(list) list의 갯수



#### 문2) 반 평균을 구하시오

```python
scores = {
    'a': {
        '수학':80,
        '국어':90,
        '음악':100
    },

    'b': {
        '수학':80,
        '국어':90,
        '음악':100
    }
}

total_score = 0
length = 0

for person_score in scores.values():
    for subject_score in person_score.values():
        total_score += subject_score
        length += 1

average_score = total_score/length
print(average_score)
```

현재, scores는 키가 'a','b'입니다. 

'a', 'b' 각각의 키가 과목이고, 점수가 value입니다.

그렇기때문에 for 문을 사용해서 scores를 해체하고 a b를 해체하여 더해줍니다.



for 문을 한번 돌 때 마다 1을 더해줍니다 > 총 평균



### 문3)  다음은 도시별 최근 일 온도입니다.

```py

city = {
    '서울': [-6, -10, 5],
    '대전': [-3, -5, 2],
    '광주': [0, -2, 10],
    '부산': [2, -2, 9]
}
```



#### 3-1 도시별 최근 일의 온도 평균?

```py
for name, temp in city.items():
    average_temp = sum(temp)/len(temp)
    print(f'{name} : {average_temp}')
```

> .items() 



#### 3-2. 도시 중 최근 3일 중에 가장 추웠던, 가장 더웠던 곳은?

> 다음에..

#### 3-3. 서울은 영상 2도였던 적이 있나요? -> ex. 네 있어요 or 없어요!

```python
if 2 in city['서울']:
    print("네 있어요")
else:
    print("없어요")
```



## 3. lotto API

플라스크

먼저, 같은 위치에 app.py와 templates (파일) 만들어준다.

flask에서 Flask, render_template, request 가져오고

그냥 requests 가져옴



lotto_check.html

```html

<body>
    <h1>로똥또로로똥또롱또로로로ㅗ로</h1>
    <form action="/lotto_result">
        로또회차: <input type="number" name="num">
        로또번호: <input type="text" name="numbers">
        <input type="submit" value="내 집 마련">
    </form>
</body>

```

각 정보의 박스 명이 num, numbers,내집마련

![1562832250363](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562832250363.png)



진짜 보기 힘듬.. 애 이름은 제이슨... 

설정 > 확장 프로그램 > 햄버거 >  크롭 jsonviewer 다운 하면 엄청 예쁘게나옴

![1562832449347](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562832449347.png)

![1562832570594](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562832570594.png)

와우~



lotto_result.html

```htm
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <p>당첨번호:{{ winner }}</p>
    <p>내 번호 :{{ numbers }}</p>
    <p>결과는~~!~~@~!~!~!:{{ result }}</p>
</body>
</html>
```



```python
from flask import Flask, render_template, request
from bs4 import BeautifulSoup
import requests
#각 위치마다 가져올수있는 함수가 다름

app = Flask(__name__)

@app.route('/lotto_check')
def lotto_check():
    return render_template('lotto_check.html')   
#그저 html만(첫화면) 보여줌

@app.route('/lotto_result')
def lotto_result():
    num = request.args.get('num') #폼으로 날린 데이터를 받을때
    res = requests.get(f'https://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo={num}') #받은 번호를 넣어야 하기 때문에 f스트링을 사용하여 동적으로 바꿔줍니다.
    lotto = res.json() #json 자료형식이 lotto에 담김. dictionary임)

    #1. 번호 6개 가져오기
    winner = []
    for i in range(1, 7):
        winner.append(lotto[f'drwtNo{i}']) #위너에 append(추가합니다.) lotto라는 딕셔너리에서 가져옵니다.

    #2. 내 번호 리스트 만들기
    numbers = []
    for num in request.args.get('numbers').split(): #list로 만들어 줍니다.
        numbers.append(int(num))

    if len(numbers) == 6:
        #번호 교집합 개수 찾기
        matched = 0
        for num in numbers:
            if num in winner:
                matched += 1
        
        if matched == 6:
            result = '1등입니다!!!(퇴사)'
        elif matched == 5:
            if lotto['bnusNo'] in numbers:
                result = '2등입니다!!!(탈조선)'
            else:
                result = '3등입니다!!!(소고기)'
        elif matched == 4:
            result = '4등입니다!!!(택시)'
        elif matched == 3:
            result = '5등입니다!!!(복권)'
        else:
            result = '꽝입니다!!!(돈날림)'

    else:
        result = '번호의 수가 6개가 아닙니다.'
    return render_template('lotto_result.html', winner=winner, numbers=numbers, result=result)
```



### 네이버 ![1562916766910](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562916766910.png)

![](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562917620437.png)

