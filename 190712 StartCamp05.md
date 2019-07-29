# 190712 | StartCamp05

깃헙 사이트에 올리면 안되는 파일이 있습니다. 그런건

.git ignore 안에 하고 뭐시기넣으면 git이 관리 못하게 (add 못함)됩니다. 

개인정보를 보호할수있습니다.



토큰을 따로 관리할수있는.. 그런걸..할 수 있읍니다..

>![img](https://lh3.googleusercontent.com/RJ4jnr30NkOL3zFByvWdY0JNWH_q7F4Up2I0RsRxV0m-N25MHB0IlwWg5GzCy3w-XiCK6yy_UA=w640-h400-e365)
>
>모멘텀이라는 extensio인데 즁말 좋다.. 하루에 한번씩 바뀐다.. 여행가고싶어진다.(안가고싶을듯..)

오늘 할 파일은 

이제 배포를 해야되기때문에 따로 파일을 만들어서 올릴 것입니다~



Git bash 킵시다. > users student에 위치한것입니다. > 

1) mkdir telegram_bot

2) telegram_bot안에서 code . > VSC open됨 

3) ctrl+` 로 터미널 열기

4)app.py  파일 만듭니다.

## 1. app.py에서 할 일

### 1)app.py 파일만들기

> https://flask.palletsprojects.com/en/1.0.x/공식문서에서 공식을 확인하십쇼.
>
> python document 쳐서 파이썬 공식 찾아보세요..

```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
```

이것이 공식입니다.

### 2)telegram 가입 및 다운

웹브라우저 다운합니다. 엡에서 가입 후 컴터 가입합니다.

### 3)Bot을 만들때,  BotFather에게 물어보세요 이름 만들기

1.  처음 만들때 : /newbot
2.  이름 만드세요 : 뭐시기뭐시기
3. 무족권 "이름_token"하여 하세요  : 뭐시기_ _token

### 4)순서

1.  **봇 토큰 (토큰은 중요하기때문에 메모장에 적으세요**![1562893407552](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562893407552.png)

   

2. **botfather가 말한거 중 링크를 타고 들어가서 authorizing 보세요 making requests 보세요**

   ![1562893479931](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562893479931.png)

   위의 형태로 request합니다.

    /bot + 우리의 토큰 + / 메소트네임(다양)

   get 방식 post 방식을 둘다지원한다.

   대소문자 필수로 지키세요.

   

   ### getMe

   

   

   > get 요청이란? 주소창에  치는게 거의 다 get입니다. 
   >
   > 그러므로 주소창에 넣어도 됩니다.

   ![1562893909198](C:\Users\student\Documents\1562893909198.png)

   3. chat id를 찾아야 합니다.숫자로 구성이 되있습니다. 뭘까요? 이건 메서드를 사용할수있어요

   available methods 에 드가서 봇새영

   ![1562894179810](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894179810.png)

   parameter가 optional 하니까 다 굳이 안넣어도 됩니다.

   ### getUpdates

   ![1562894344260](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894344260.png)

   

   왜 result가 없냐? 아직 대화를 안해봐서입니다.

   ![1562894432279](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894432279.png)

   하면

   ![1562894444646](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894444646.png)

   이렇게 나옵니다. 대박이죠...

   ![1562894500485](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894500485.png)

   이것이 저희  chat id 입니다.

   ### sendMessage

   이전과 같이 해봤읍니다.

   ![1562894754725](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894754725.png)

   어머 에러가 났어요~!

   

   ![1562894777182](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894777182.png)

   require이 필수이기때문에 넣어주야합니다.

   

   **How?**

   항상 물음표로 시작할게요 그리고 &로 나열할수있씁니다~

   /sendMessage?chat_id=715152799&text=이현우 바보

   ![1562894980085](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562894980085.png)

   

## 2.파이썬 코드로 텔레그램 메시지 보내기

### 1)다시 파일 만드세요 

$ touch send_message.py



### 2) 요청합니다.

1. import
2. requests.get("주소") 였는데 , 우리가 보낼거는 토큰, 메소드, 파라미터들을 변수화 해서 넣어볼겁니다.



```python
#파이썬 코드로 텔레그램 메시지 보내기
import requests

api_url = 'https://api.telegram.org'
token = '882942571:AAEw3b3z6jUge7M9jOtcyTdLA3Haf6BT1AI'
chat_id = '715152799'
text = '이현우 바보'

send_message = requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')

print(send_message.text)

#이렇게 변수화 하는 이유는 여러군대에서 변수를 사용할 수 있기 때문입니다.
```



### 3) 보안강화하는법,  

터미널에

 pip install python-decouple --user

touch .env 함으로서 .env파일 만들어서 여기에 중요정보를 보관할것입니다.

github 안 .env하면 못드감



.env파일(ㅁ든것들에 스페이스 잇으면안됨)

```python
TELEGRAM_BOT_TOKEN='882942571:AAEw3b3z6jUge7M9jOtcyTdLA3Haf6BT1AI'
CHAT_ID='715152799'
```

하고 저장합니다.

그리고 send message.py 파일에서 위의 정보를 지워줍니다.



## 3. .gitignore 파일만들기

.env 파일 깃이 관리 못하게하려면 .gitignore 파일에 .env 하면된다.

깃허브에서 깃이그노어에서 제공하는거 잇긴하다. 찾는법 python .gitignore 쳐서 다 복사해갖고 ignore파일에 붙여넣귀해보면됩니다.

그리고 우리가 env파일에 있는걸 불러와야 합니다. 

아까전에 decouple(떨여뜨려놓다) 다운받았었는데요 필요할때는 불러올수잇읍니다.

```python
#파이썬 코드로 텔레그램 메시지 보내기
from decouple import config 
import requests

api_url = 'https://api.telegram.org'
token = config('TELEGRAM_BOT_TOKREN')
chat_id = congif('CHAT_ID')
text = '이현우 바보'

send_message = requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')

print(send_message.text)

#이렇게 변수화 하는 이유는 여러군대에서 변수를 사용할 수 있기 때문입니다.
```

app.py입니다.



## FLASK에서 해보기

### 1)mkdir templates(html 보관하는상자)

```python
from flask import Flask, render_template, request
from decouple import config 
import requests

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

@app.route('/write')
def write():
    return render_template('write.html')

@app.route('/send')
def send():
    api_url = 'https://api.telegram.org'
    token = config('TELEGRAM_BOT_TOKEN')
    chat_id = config('CHAT_ID')
    text = request.args.get('message')
    requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')
    
    return render_template('send.html')
```

app.py 파일 입니다.



### 2) 템플릿츠 안에 write.html만들기

```html
<h1>Telegram
    <form action="/send">
        <input type="text" name="message">
        <input type="submit" value="메시지 전송">
    </form>
</h1>

>>> send라는 곳으로 보낼것입니다.~
```

메시지라는 박스를 열어서 뭔지 확인해야 하기 때문에 app.py에서 받을때 열어봐야합니다 request.args.get

### 3) send.html 만들기

```html
<h1>메시지가 성공적으로 전송되었습돠</h1>
```





## 웹푹?

새탭 열어서 NGROK 검색 >  GET STARTED FOR FREE (로그인 하면 24시간가능)>ngrok실행x>파일 복사>c>사용자>student에 복사

명령프롬포트>engrok.exe http 5000 (터널이 생긴것입니다.) > 우리는 https 사용할것임

![1562902118847](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562902118847.png)

https://5036f~~~.io까지 복사하세요 > 끄지말고 메모장가서 적어

![1562908590586](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562908590586.png)



### 1. setWebhook 등록

https://api.telegram.org/bot882942571:AAEw3b3z6jUge7M9jOtcyTdLA3Haf6BT1AI/setWebhook?url=주소/bottoken

![1562908842615](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562908842615.png)

왜 토큰을 붙였나요? /{token} >아무나 이 주소로 접근하지 못하게 해 줍니다.(app.py)

> 웹훅설정ㅎ바니다.(telegram -> flask)

### 에코 버전

```python
from flask import Flask, render_template, request
from decouple import config 
import requests

app = Flask(__name__)

api_url = 'https://api.telegram.org'
token = config('TELEGRAM_BOT_TOKEN')
chat_id = config('CHAT_ID')

@app.route('/')
def hello_world():
    return 'Hello, World!'

@app.route('/write')
def write():
    return render_template('write.html')

@app.route('/send')
def send():
    text = request.args.get('message')
    requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')
    
    return render_template('send.html')

@app.route(f'/{token}', methods=['POST']) #아무나 들어오지못하도록 token 그리고 플라스크가 post 요청을 보냅니다.
def telegram():
    #1. 구조 print 해보기 & 변수 저장
    #print(request.get_json())
    #print(type(request.get_json()))
    from_telegram = request.get_json()
    print(from_telegram)

    #2. 메시지를 그대로 돌려 보내기
    if from_telegram.get('message') is not None :
        chat_id = from_telegram.get('message').get('from').get('id')
        # print(chat_id)
        text = from_telegram.get('message').get('text')
        res = requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')
        print(res)
    return '', 200 



```



```python
from flask import Flask, render_template, request
from decouple import config 
import requests

app = Flask(__name__)

api_url = 'https://api.telegram.org'
token = config('TELEGRAM_BOT_TOKEN')
chat_id = config('CHAT_ID')

naver_client_id = config('NAVER_CLIENT_ID')
naver_client_secret = config('NAVER_CLIENT_SECRET')

@app.route('/')
def hello_world():
    return 'Hello, World!'

@app.route('/write')
def write():
    return render_template('write.html')

@app.route('/send')
def send():
    text = request.args.get('message')
    requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')
    
    return render_template('send.html')

@app.route(f'/{token}', methods=['POST']) #아무나 들어오지못하도록 token 그리고 플라스크가 post 요청을 보냅니다.
def telegram():
    #1. 구조 print 해보기 & 변수 저장
    #print(request.get_json())
    #print(type(request.get_json()))
    from_telegram = request.get_json()
    print(from_telegram)

    #2. 메시지를 그대로 돌려 보내기
    if from_telegram.get('message') is not None :
        chat_id = from_telegram.get('message').get('from').get('id')
        # print(chat_id)
        text = from_telegram.get('message').get('text')
      
        
        #3. keyword(번역)
        if text[0:4] == '/번역 ':
            headers = {'X-Naver-Client-ID': naver_client_id, 'X-Naver-Client-Secret': naver_client_secret} # 네이버가 요구한 방식
            data = {'source': 'ko', 'target': 'en', 'text': text[4:]}
            
    
            papago_res =requests.post('https://openapi.naver.com/v1/papago/n2mt', headers=headers, data=data) #post 요청방식을 사용
            print(papago_res)
            text = papago_res.json().get('message').get("result").get("translatedText")
            print(text)
        res = requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')
    return '', 200 



```



### 배포

pythonanywhere 사이트 드가기



web add a new web app > flask > python 3.7>next 

코드이식

상단의 Files> directories > mysite/flask_app.py클릭

```python
from flask import Flask, render_template, request
from decouple import config 
import requests

app = Flask(__name__)

api_url = 'https://api.telegram.org'
token = config('TELEGRAM_BOT_TOKEN')
chat_id = config('CHAT_ID')

naver_client_id = config('NAVER_CLIENT_ID')
naver_client_secret = config('NAVER_CLIENT_SECRET')

@app.route('/')
def hello_world():
    return 'Hello, World!'

@app.route(f'/{token}', methods=['POST']) #아무나 들어오지못하도록 token 그리고 플라스크가 post 요청을 보냅니다.
def telegram():
    #1. 구조 print 해보기 & 변수 저장
    from_telegram = request.get_json()

    #2. 메시지를 그대로 돌려 보내기
    if from_telegram.get('message') is not None :
        chat_id = from_telegram.get('message').get('from').get('id')
        # print(chat_id)
        text = from_telegram.get('message').get('text')
      
        
        #3. keyword(번역)
        if text[0:4] == '/번역 ':
            headers = {'X-Naver-Client-ID': naver_client_id, 'X-Naver-Client-Secret': naver_client_secret} # 네이버가 요구한 방식
            data = {'source': 'ko', 'target': 'en', 'text': text[4:]}
            
    
            papago_res =requests.post('https://openapi.naver.com/v1/papago/n2mt', headers=headers, data=data) #post 요청방식을 사용
            print(papago_res)
            text = papago_res.json().get('message').get("result").get("translatedText")
            print(text)
        res = requests.get(f'{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={text}')
    return '', 200 

```

유명한것들 bs4 flask등은 이미 설치되잇지만 decouple 은 설치안되서 설치해줘야함

 save>consols> bash > pip3 install python-decouple --user

.env에 환경변수로 지정한것도  지정해줘야함

Files>Files>.env검색 > .env파일내용을 복붙함.

웹북설정 바까죠야함 왜? 새 주소로 접속할수잇게되는데 엥그록(우리로컬)로 싸주게 됩니다.

Web> reload 후 복사해서 ngrok과바꿔주기

![1562920231213](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1562920231213.png)

reload