# 190729 | Web&HTML>_CSS

웹 : 정보공간

http://info.cern.ch/ 최초의 웹

서비스 : 



## 1. 냐항

### 1) 서버

보통 서버 컴퓨타는 모니터 띠고 가로로 눕혀서 여러개로 표현합니다~

어떻게 요청 보내나? 브라우저로 보냅니다~~ 그중에 크롬을 씁니다~

多:一 가능

### 2) 요청의 종류

1. 줘(get) 

   :주소창에 쓰는 모든 요청의 방식

   : 돈까스집가서 스시 주세여 하는것 (내가 그동안 잘 못 보냈던 요청들)

   :나 이거 줘 (html)

   :그래 여깄어 (html)

2. 받아/ 처리해 줘  (Post)

   : 나는 이런것들을 처리 해 줬으면 좋겠어~ 

   : 요청에 부분에 대한 처리를 시행 후 다시 줌



####  웹 서비스를 개발한다는것?

**서버컴퓨터에서 요청과, 응답을 처리 할 프로그램을 개발한다.**



## 2. static webservice

- 클라이언트가 요청을 보내면 서버가 응답을 한다.
- 클라이언트가 요청보내는 프로그램 : 브라우저

#### DNS (도네임 네임 서비스)

### 1)  IP(Internet Protocol)





### 2) 도메인 (Domain)



- 

### 3)  URL (Uniform Resource Locator)



Static web 

정해진 페이지만 제공할 수 있습니다.



Dynamic Web

Flask할 때, variable routing 될 떄,,. (뭔지 모르겠음)\

접속 할 때 마다 변해야 할 필요가 있는 사이트 .ex) 실시간 댓글 반영



우리는 왜 동적 웹을 쓰는가? 

ex) https://hphk/lectures/1 만약 강의가 하나가 있으면 정적 하면 되지만, 

강의가 만 개 이상이 되버리면 하나하나 지정해줘야 하는 번거로움이 생기게 됩니다.



모든 웹 서비스에서, 서버 컴퓨터에 달라고(get)하는 법? 

-> 브라우저에서 요청 할 수 있습니다.



 these days 

URI(identifi cator, 식별자) > URL(locator, 자원이 있는 위치) 요즘은 URI를 사용합니다~ 트렌드쓰~



WEB Page

W3c : 웹 표준을 정하는 곳입니다. world wide web consortium css/ html/js 할수잇는데 우니느 js 빼고 두개 배운다.~



## html hypertext markup language

1)  **hypertext**

 :link 를 통해 text를 넘나든다 

- hpter text를 주고받는 규칙 : http (**hyper text** Transfer Protocol)

2) **Markup**

: 어떠한 역할 or 의미 를 부여하는것 like 형광팬으로 마킹 하듯이 

ex) 닌 제목 니는 본문 니는 약간 중요쓰 너는  부제목쓰

3) **HTML**

텍스트를 넘나드는 친구에게 역할을 부여하는 것

웹 페이지를 작성하기 위한 역할 표시 언어

> 프로그래밍 언어는 아닙니다~



## Cascading Style Sheet

- html 에 살을 붙여놓음



## JavaScript

- 활기를 불어넣는 느낌

  

HTML 파일 : HTML로 작성된 문서파일
 ex) 네이버 뉴스 보여줘~ 



HTML 표준

## 1. HTML 문서의 기본 구조

- head, body

head  : 브라우저에 나타나지 않음 브라우저 텝에 나타남

body : 브라우저 화면에 나타나는 정보, 실제 내용에 해당



^디버깅이 안되있기 때문에 조심히 하세욤^



메타정보란 ? 정보의 정보

## 1. 간단한 html 문서 만들어 보기

1) 환경만들기

```bash

student@DESKTOP MINGW64 ~
$ cd TIL/

student@DESKTOP MINGW64 ~/TIL (master)
$ ls
00_StartCamp/  01_Python/  entry_point/  README.md

student@DESKTOP MINGW64 ~/TIL (master)
$ mkdir 02_web

student@DESKTOP MINGW64 ~/TIL (master)
$ cd 02_web/

student@DESKTOP MINGW64 ~/TIL/02_web (master)
$ mkdir 00_html_intro

student@DESKTOP MINGW64 ~/TIL/02_web (master)
$ cd 00_html_intro/

student@DESKTOP MINGW64 ~/TIL/02_web/00_html_intro (master)
$ touch 01_intro.html
```

``<!DOCTYPE html>``

이 사용하는 문서는 html이라고 도장 찍어주는 역할

```html
<html lang="ko">

</html>
```

1. " " 써야함

2. =는 다 붙여써야합니다.

   ```html
   <!DOCTYPE html>
   <html lang="ko">
       <head>
           <meta charset="UTF-8">
           <title>Hello World!</title>
       </head>
       <body>
           <h1>안녕~ 나는 남수경이야~!</h1>
       </body>
   </html>
   ```

   결과 : ![1564370213316](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1564370213316.png)

### 1) 냐항

## 2. Tag와  DOM TREE

### 1) 주석

`` <!-- 주석내용 -->``

### 2) 요소

- 태그

- 내용

  ``<h1> 요소 </h1> ``

  <h1> 이게 태그임ㅋㅋ

    



### 3) self-closing element

``<img  src="url"/>

닫는테그 없음, 메타태그/ 인풋



### 4) 속성

- 태그에는 속성이 지정 될 수 있다.

  `` <a href='google.com'/>``

  속성명 : href 속성값 : google.com

  id, class,style은 태그와 상관없이 모두 사용 가능

  1) id : 유일 식별자 (중복불가)

  2) class : 스타일 시트에 정의된 class를 요소에 지정 (중복 가능)

  3) style: 인라인 스타일을 요소에 지정

### 5) DOM트리

```html
<body>
    <h1>웹문서</h1>
    <ul>
        <li>HTML</li>
        <li>CS</li>
    </ul>
</body>
```



- body - h1태그          부보- 자식관계
- li 태그는 형제 관계
- h1와 ul은 형제 관계
- 2 space



### 5) 시맨틱태그

- div  > 그저 공간분할

  ``<div>이것은공간</div>  공간 자체에 대한 어떤 의미도 없음

  but, 코드의 가독성을 높이고 유지보수가 쉬워진다.

  개발자가 의도한 요소의 의미를 show 

- 웹에 존재하는 웹페이지들에  'metadata'를 부여하여 기존의 데이터 집합을 '의미'와 '관련성'을 가지는 거대한 데이터의 집합으로 구축하고자 하는 발상입니다.
- 개발자 및 사용자 뿐 아니라 검색엔진(구굴)에 의미있는 정보의 그룹을 태그로 표현하여 단순히 보여주기 위한 것을 넘어서 의미를 가지는 태그들을 가지기 위한 노력
- SEO(search engine optimization) : 검색엔진 최적화
  - 웹 페이지 검색 엔진이 자료를 수집하고 순위를 매기는 방식에 맞게 웹 페이지를 구성해서 검색 결과의 상위에 노출될 수 있도록 하는 작업

| 태그    | 설명                                                         |
| ------- | ------------------------------------------------------------ |
| header  | 헤더                                                         |
| nav     | 네비게이션 ( ㅇㅓ딘가 이동하기 용이하도록)                   |
| aside   | 사이드에 위치한 공간, 메인 콘텐츠는 아니지만 그래도 사용 ex)날씨 |
| section | 신문기사 섹션과 비슷하게 느껴짐                              |
| article | 독립적으로 구분되는 영역 (포럼.신문 등 글)                   |
| footer  | 그 회사 전화번호 주소같이 제일밑에잇음                       |
|         | Tag와  DOM TREE                                              |

## w

crom e 확장프로그램 (web developer)  다운

information > view document ourline

![1564377083362](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1564377083362.png)



## 3. Markup - Tag의 종류 (어떤역할/ 어떤태그)

### 1) 텍스트 태그 



```html
<h1> contents</h1>
---
<h6> contents </h6>
```

````html
<p>contents </p>
````

글자크기 뿐 아니라 역할이 있는거입~



p 태그  안 본문을 넣는다



```
오류 메세지가 나지 않으니 만약 테그쌍이 맞는지 잘 봅니다.
```



``<b> contents </b>``

``<strong> contents  </strong>``

둘다 강하게보이지만 밑에 strong은 시멘틱 (의미가 있따)



```html
<ol> list 순서있는
<ul> list 순서 없는
```

### 3.1 레이아웃태그

```html
<div>의미없는블록</div>
<span>의미 없는 인라인</span>
```

### 3.2 링크 태그

```
<a href="google.com"/>
<!-- 이 링크를 클릭하면 구글으로 간가 -->

```



### 3.3 미디어 태그

```html
<img src="/profile.jpg"/>
```

추가 속성 

tabindex : 사용자가 탭 누를때 순서 지정

alt : 이미지가 로드되지 않을때 나오는 문구 선정

```html
<video src="video.mp4"/>
```

```html
<iframe src="htts://www.w3schools.com">
</iframe>
```

i frame을 사용할 시 문서에서 유투브를 볼 수 있음

### 3.3 미디어 태그

``` html
<ul>
    <li>순서없는</li>
    <li>항목</li>
</ul>
```



html은 문서이다. 네이버의 서버에 요청을 보내는 것이다.

파비콘 : 웹브라우저 주소차에 표시되는 아이콘



### 3. 4 레이아웃 태그

```html
의미 없는
<div>
    
    
</div>

<span>

</span>
의미 있는
<header></header>

굵은 효과주기
<b>	</b>

<strong>	</strong> <!--이게 시멘틱-->

이텔릭 효과 주기
<i>  </i>

<em>  </em> <!-- 이게 시멘틱-->
```





```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Hi, HTML!</title>
        <style>
            h1 {
                color:aqua;
            }
        </style>
    </head>
    <!--Bold-->
    <div>
        <b>This is bold.</b>
        <strong>This is strong.(semantic)</strong>
    </div>
    <!--italic-->
    <div>
        <i>This is italic</i>
        <em>This is em.(semantic)</em>
    </div>
    <!--highlighted 형광펜-->
    <h2>This is <mark>Mark</mark>.</h2>
    
    <hr>
    
    <!--del / ins -->
    <!--del: 텍스트가 삭제 되었음을 나타냄 (취소선)-->
    <h2>This is <del>del</del>.</h2>
    
    <hr>

    <!--ins: 텍스트가 새로 추가 되었음을 나타냄 (밑줄)-->
    <h2>This is <ins>ins</ins>.</h2>
    
    <hr>

    <!--p / br 개행(self closing) -->
    <p>
        This is p tag.<br>
        This is p tag.<br>
        This is p tag.<br>
        This is p tag.<br>
        This is p tag.<br>
        This is p tag.<br>
    </p>
    
    <hr>
    <!-- <p> 이새끼는 그냥 엔터가 말을 안 들음 pre -->
    
        <pre>
        from flask import Flask
        app = Flask(__name__)
        @app.route('/')
        def hello():
            return 'Hello World!'
    </pre>

    <!-- hr 이새끼는 구분선을 만들어 줍니다. -->
    <hr>
    <!-- q / blockquote -->
    <p>
        Justin said, <q>Hello world!</q>
    </p>
    <blockquote>
        Hello world!
    </blockquote>

    <!-- ol / ul / li -->
    <ol>
        <li>first</li>
        <li>second</li>
        <li>third</li>
    </ol>
    <ul>
        <li>first</li>
        <li>second</li>
        <li>third</li>
    </ul>

    <body>
        <!--Heading-->
        <h1>Hi, h1!</h1>
        <h2>Hi, h2!</h2>
        <h3>Hi, h3!</h3>
        <h4>Hi, h4!</h4>
        <h5>Hi, h5!</h5>
        <h6>Hi, h6!</h6>
    </body>
</html>
```



## 4.실습

