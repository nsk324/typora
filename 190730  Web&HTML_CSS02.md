# 190730 | Web&HTML>_CSS-2

> 04.markup.html 파일

## list 기호 스타일 바꾸기

```html
<ol>
            <li style="list-style: upper-alpha">int</li>
            <li style="list-style-type: lower-greek">float</li>
            <li style="list-style-type: upper-latin">complex</li>
            <li><del>complex</del></li>
        </ol>
```

첫번째 ol의 형식이 대문자, 그리스분자, 라틴어로 바뀌었다.

아래와같이 ul의 형식을 동그라미 -> 사각형으로 바꿔 보았다.

```html
        <h3>기초</h3>
        <ul>
            <li style="list-style-type: square">HTML</li>
            <li style="list-style-type: square">CSS</li>
        </ul>     
```

![](C:\Users\student\Desktop\typora\image\0730-1.PNG)



python documentation

MDN web docs



## 링크 걸기

```html
<h1>프로그래밍 교육</h1>
        <hr>
        <a href="https://docs.python.org/3/"><h2>파이썬</h2></a>
        <h3>Number type</h3>
```

href : 하이퍼 레퍼런스

**내 탭이 없어지고 열리게 되어 불편하다**

```html
<a href="https://docs.python.org/3/" target="_blank"><h2>파이썬</h2></a>
<a href="https://developer.mozilla.org/ko/" target="_blank"><h2>웹</h2></a>
```

**새 탭에서 열리게 됩니다.**

<테그 안에 글을 넣는 실수를 자주 하게 됩니다.>



## 같은 폴더 내에 있는 index.html파일로 이동하게 해 보자

1. 같은 파일내에 index.html 만들기
2. a 테그 안에 글을 넣어주게 되면 그 글에 하이퍼링크가 걸리게 돕니다.
3. a 테그 안에 파일 명을 "" 안에 넣어주면 됩니다.

```html
<h1>참고링크</h1>
<h2>파이썬</h2>
<a href="https://docs.python.org/3/">하하핳하하핳핳</a>
<h2>웹</h2>
<a href="https://developer.mozilla.org/ko/">넘 어려워..</a>
```

```html
<a href="index.html">[참고 사이트]</a>
```



## 제목을 미디어로 바꿔보자(이미지, 아이테그, 동영상)

1. img + tap 사용

   ``<img src="" alt="">`` (스크린 리더가 alt를 읽어본다.)

2. images 파일 만들기

3. 손가락이 보이긴 한데 어디론가 안감

   ``<a href="#"> </a>``

4. 픽셀 크기 지정하기 (img 안에서 width height)

```html
<a href="#" target="_blank"><img src="images/파이썬.png" alt="python logo" width="50px" height="50px"> </a>

<a href="https://developer.mozilla.org/ko/" target="_blank"><img src="images/웹.jpg" alt="web"> </a> 
```



## 영상을 넣어보자

1. 유투브
2. 소스코드 복사 (우클릭)
3. iframe이라는 테그로 들어감

```html
<iframe width="1252" height="704" src="https://www.youtube.com/embed/MYSk2r9YqeU?list=RDMYSk2r9YqeU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```







> 05_lunch.html 파일

## 점심을 나타내는 표를 넣어보자

1. table 텝
2. tr 텝 : 가로줄 만드는 역할
3. th 텝 : 테이블 헤드
4. td 텝 : 셀 만드는 역할
   - 행 두 개를 합치려면? ``<td rowspan="2">짬뽕</td>``
   - 열 두 개를 합치려면 ? ``<td colspan="2">초밥</td>``

```html
<table>
    <tr>
        <th></th>
        <th>월</th>
        <th>화</th>
        <th>수</th>
    </tr>

    <tr>
        <td>A코스</td>
        <td rowspan="2">짬뽕</td>
        <td colspan="2">초밥</td>
    </tr>
    
    <tr>
        <td>B코스</td>
        <td>김치찌개</td>
        <td>삼계탕</td>
    </tr>
</table>
```

![](C:\Users\student\Desktop\typora\image\0730-2.PNG)



## 시간 나타내는 표를 넣어보자



```html
<table border="1px solid black">
    <tr>
        <th></th>
        <th>월</th>
        <th>화</th>
        <th>수</th>
    </tr>

    <tr>
        <td>A코스</td>
        <td rowspan="2">짬뽕</td>
        <td colspan="2">초밥</td>
    </tr>
    
    <tr>
        <td>B코스</td>
        <td>김치찌개</td>
        <td>삼계탕</td>
    </tr>
</table>
```

![](C:\Users\student\Desktop\typora\image\0730-3.PNG)



5. 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>MUSIC TIMETABLE</title>
    <style>
        td{
            border : 1px solid darkgray
        }
    </style>
</head>
<body>
    <h1>2019년 타임테이블</h1>
    <table>
        <tr>
            <th>TIME</th>
            <th>INDOOR</th>
            <th colspan="2">OUTDOOR</th>
        </tr>

        <tr>
            <td></td>
            <td>소극장</td>
            <td>잔디마당</td>
            <td>대공연장</td>
        </tr>

        <tr>
            <td>10:00</td>
            <td rowspan="2">안녕하신가영</td>
            <td></td>
            <td>10cm</td>
        </tr>

        <tr>
            <td>13:00</td>
            <td rowspan="2">선우정아</td>
            <td rowspan="2">참깨와 솜사탕</td>
        </tr>

        <tr>
            <td>15:00</td>
            <td></td>
        </tr>

        <tr>
            <td>17:00</td>
            <td>크러쉬</td>
            <td></td>
            <td>폴킴</td>
        </tr>

    </table>
</body>
</html>
```

![](C:\Users\student\Desktop\typora\image\0730-4.PNG)



## form 

form 텝 하기

```html
<form action="">
    
</form>
```

input과 form은 같이 다닙니다.

```html
<form action="">
    TEXT: <input type="text">
    Number: <input type="text">
    PASSWORD: <input type="text">
    Email: <input type="text">
    DATE: <input type="text">
</form>
```

![1564450138527](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1564450138527.png)

in line level element (옆으로 쭉 붙는 형태)

아래로 내리고싶어요~ 개행  ``<br>``사용 (close 필요 x)

```html
<form action="">
    TEXT: <input type="text"><br>
    Number: <input type="text"><br>
    PASSWORD: <input type="text"><br>
    Email: <input type="text"><br>
    DATE: <input type="text">
</form>
```

![](C:\Users\student\Desktop\typora\image\0730-6.PNG)

input  안 placeholer = "" 미리 적혀있는것~

```html
<form action="">
    TEXT: <input type="text" placeholder="내용을 입력 해 주세요"><br>
    Number: <input type="text"><br>
    PASSWORD: <input type="text"><br>
    Email: <input type="text"><br>
    DATE: <input type="text">
</form>
```

![](C:\Users\student\Desktop\typora\image\0730-7.PNG)

```html
<form action="">
    <input type="radio" name = "language">HTML<br>
    <input type="radio" name = "language">CSS<br>
    <input type="radio" name = "language"disabled>JS
</form>
```

![1564450594587](C:\Users\student\Desktop\typora\image\0730-8.PNG)





## option (drop down list)

```html
<form action="">
    <select name="country">
        <option value="한국">한국</option>
        <option value="중국">중국</option>
        <option value="일본">일본</option>
    </select>
</form>
```





## 체크박스

```html
<form action="">

    한국: <input type="checkbox">
    일본: <input type="checkbox"><br>
    <input type="submit" value="제출하세요">
</form>
```

<fome> open에 있는 action에서 submit 한 정보를 보내줍니다.



![](C:\Users\student\Desktop\typora\image\0730-9.PNG)





## 서브웨이 주문서 만들기



```html
<h1>FORM</h1>
<P>주문서를 작성하여 주십시오</P>

<form action="">
    <!-- input에 대한 label-->
    <label for="">이름:</label>
    <input type="text" placeholder="이름을 입력하여 주세요">
    <label for="text">날짜:</label>
    <input type="date" id="date-1">
    
    <!--radio 타입-->
    <h2>1. 샌드위치 선택</h2>
    <input type="radio" name="sandwich" value="1">에그 마요<br>
    <input type="radio" name="sandwich" value="2">이탈리안 비엠티<br>
    <input type="radio" name="sandwich" value="3">터키 베이컨 에그마요
    <hr>
    <!-- 눌렀을때 값이 넘어가도록 value 값 지정-->



    <!--콤보박스-->
    <h2>2. 사이즈 선택</h2>
    <input type="number" min="15" max="30" step="15">
    <hr>
    <!-- 현재 이 상태에서는 정보가 넘어가진 않음ㅎ-->

    <!--select dropdown list 키, value 형태로 넘어가게 됩니다.-->
    <h2>3. 빵</h2>
    <select value="bread">
        <option value="1">허니오트</option>
        <option value="2">플랫브레드</option>
        <option value="3">하티 이탈리안</option>
    </select>
    <hr>

    <!--check box-->
    <h2>4. 야채소스</h2>
    <input type="checkbox" name="source" value="1"> 토마토<br>
    <input type="checkbox" name="source" value="2"> 오이<br>
    <input type="checkbox" name="source" value="3"> 할라피뇨<br>
    <input type="checkbox" name="source" value="4"> 핫 칠리<br>
    <input type="checkbox" name="source" value="5"> 바베큐<br>

    <input type="submit" value="제출">
</form>
```



# css

```css
셀렉터{선언; 선언;}

셀렉터{프로퍼티:값; 프로퍼티:값;}

h1{color:blue; font-sixe:15px;}
```

기본사용법

1. 주석

   ```css
    /*주석은 이렇게 적혀요*/
   ```



## css 활용하기

1. Inline(인라인)

   -html 요소의 style에 css 넣기 

   

2. Embedding(내부참조)

   -HTML 내부에 css를 포함 시키기

   

3. link file (외부참조)

   -외부에 있는 css파일을 로드하기



> 01_css intro

```html
<!--inline-->
<h1 style="color:blue;font-size:100px">This is my site!</h1>
```



> 02_embedding(내부참조)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        h1 {
            color:blue;
            font-size: 100px
        }
    </style>
</head>
<body>
    <!--inline-->
    <!-- <h1 style="color:blue;font-size:100px">This is my site!</h1> -->
    <!--embedding-->
    <h1>This is my site!</h1>
</body>
</html>
```



> 3. link file(외부참조)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="01_css_intro.css">
    <title>Document</title>

</head>
<body>

    <h1>This is my site!</h1>
</body>
</html>
```



css.intro.css 파일에 아래와같이한다

```css
h1{
    color:red;
    font-size: 150px
}
```

![1564462624150](C:\Users\student\Desktop\typora\image\0730-10.PNG)



## 실습

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="02_css_prac.css">
    <title>Document</title>
</head>
<body>
    <h1>This is my site</h1>
    <h2>I love my site</h2>
</body>
</html>
```



### css파일

```css
h1{
    color:black;
    background-color: red;
    font-size: 150px;
}

h2{
    color:bisque;
    background-color: red;
    font-size: 70px;
}
```

![](C:\Users\student\Desktop\typora\image\0730-11.PNG)



###  단순선택자 태그 선택자

```css

```



### 클래스 선택자

```css
.clss{color:blue;}
(클래스명){ㅇㅇ :ㅇㅇㅇ ;}
```

###  아이디 선택자

```css
#id{color:blue;}
```



### 후손 / 자식 셀렉터

태그는 중첩 될 수 있다. 따라서 ol 태그 밑 li 태그 등이 올 수 있다.

이 때, 자식 셀렉터(공백)을 사용하게 되면?  해당되는 모든 자손을 선택한다.

ex) ol -li - ul- li 에서 ol 밑에있는 li만 하고싶을때

후손 셀렉터(>) :해당 태그 내에 있는 직계자식 요소만 선택



1. meta 테그 밑 link태그를 활용해 불러올 css 파일 입력

```html

```



```css

```

## em

배수단위 (상대단위) 100% = 1em



### rem

: 최상위 요소(html)의 사이즈를 기준으로 삼는다. r은 root를 의미

html 크기 없으면 브라우저를 기준으로 한다 16pixel 0.5rem은 8pixel



### viewport

디바이스마다 다른 크기 화면을 가지고있기에 상대단위인 viewport를 기준으로 ㅁ나든 단위

v2



### 색상 표현 단위

HEX #ff0000 (빨강) #00ff00 ##0000ff

RGB rgb(255, 0, 0) 투명도도 설정 할 수 있음 마지막 인자로 넣으면... 

RGBA





## 실습

04_css_unit.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="04_css_unit.css">
    <title>Document</title>
</head>
<body>
    <h1>This is sue's cafe.</h1>
    <hr>
    <div>
        <h2>Sue's main menu</h2>
        <ul>
            <li>pasta</li>
            <li>salad</li>
        </ul>
    </div>
    <div>
        <h2>Sue's dessert</h2>
        <ul>
            <li>Carror Cake</li>
            <li>Cup Cake</li>
        </ul>
    </div>
</body>
</html>
```



04_css_unit.css

```css
h1 {
    color: blue;
    font-size: 50%; /*브라우저의 기본 default 사이즈를 기준으로~*/
}

div{
    color:red;
    font-size: 50%;
}

ul{
    color: rgb(48,199,66);
    font-size: 2rem;
}

div > h2 {
    color: skyblue;
    font-size: 5em;
}

/* em 은 상속의 영향을 받기 때문에 div는 8pixel인데 거기에서 8em이니 40pixel이 되겠디*/

```



![](C:\Users\student\Desktop\typora\image\0730-12.PNG)



## Box model

- **content** : 실제 내용 위치

- **Padding** : 테두리 내부여백 요소에 적용된 배경의 컬러, 이미지는 패딩까지 적용

- **Border**: 테두리 영역

- **Margin**: 테두리 바깥 여백, 배경화면 지정 불가



### 1. margin

```html
margin{
magin-top:10px;   /* 실컨텐츠는 내려감*/
marin-right:20px; /*'' 오른쪽으로*/
margin-left:30px
margin-bottom:40px
}
```



### 2. padding

```html
.margin-padding{
margin:10px /*  아래 위 오 왼 10px만큼 공백 줌*/
padding:30px 
}
```



### 3. border

```html
.border{
border-width:2px;
border-style:dashed'
border-color:black;
}
```

### 4. shorthand

```html
위 아래 위위 아래 위 아래 위위 아래 위 아래 위위 아래
```

```htnk
.border{
border:2px, dashed, black;
}
```



### 실습

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="05_box_model.css">
    <title>My Box Model</title>
</head>
<body>
    <div class="margin">
        margin
    </div>
    <hr>
    <div class="margin-padding">
        margin-padding
    </div>
    <hr>

    <div class="border">
        border
    </div>
    <hr>
    <div class="margin-1">
        margin-1
    </div>
    <div class="margin-2">
        margin-2
    </div>
    <div class="margin-3">
        margin-3
    </div>
    <div class="margin-4">
        margin-4
    </div>
    <hr>
    
    <div class="border-short">
        border-short
    </div>
    <hr>

</body>
</html>
```





css 파일

```css
.margin {
    margin-top: 10px;
    margin-bottom: 20px;
    margin-right: 30px;
    margin-left: 40px;
}

.margin-padding{
    margin:10px;
    padding:13px;

}

.border{
    border-width: 2px;
    border-style: dotted;
    border-color: red;
}

.margin-1{
    margin:10px;
}

.margin-2{
    margin: 10px 20px
}

.margin-3{
    margin: 10px 20px 30px
}

.margin-4{
    margin: 10px 20px 30px 40px
}

.border-short{
    border: 3px dashed teal
}
```





## block

항상 새로운 라인에서 시작

화면 크기에서 전체 가로폭을 차지 width 100%

너비가 정해지면 나머지가 마진으로 놔두게됨



```html
margin-right auto; <!--왼쪽정렬-->
margin-left auto; <!--오른쪽정렬-->


margin-right auto; 
margin-left auto;<!--가운데정렬-->
```



## inline

새로운 라인에서 시작하지 않음

문장에 들어갈 수 있음

content의 너비만큼 가로폭 차지

width height margin-top/bottom 프로퍼티 지정 할 수 없음

상 하 여백은 line-height로 지정

예) span, a, strong, img, br, input, select, textarea, buttom



## inline-block

block과 inline레벨 요소 특징 모두 갖음

inline처럼 한 줄에 표시 되면서 blcok에서 width, height, margin(top bottom) 가능

> inline-block으로 태어나는 애는 없고 지정되는것입니다.

## None

해당 요소를 화면에 표시하지 않는다(공간(영역)조차 사라진다)



## hidden

공간은 남아 있다 하지만 그 콘텐츠만 안보이는 것 분





## 실습

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="06_box_model_2.css">
    <title>Document</title>
</head>
<body>
    <!--display-->
    <!--1. block level element-->
    <h1>
        이것은 block 요소, 기본적으로 너비의 100% 차지
    </h1>

    <div>
        너비가 정해지면 나머지를 마진으로~~!
    </div>

    <div id="div-1">
        block의 오른쪽 마진을 오토로 주면 왼쪽으로 붙어요 (왼쪽정렬)
    </div>

    <div id="div-2">
        block의 왼쪽 마진을 오토로 주면 오른쪽으로 붙어요 (오른쪽정렬)
    </div>

    <div id="div-3">
        block의 왼쪽/오른쪽 마진을 auto로 주면 가운데 정렬~
    </div>

    <div id="div-4">
        중앙정열은 그냥 margin auto로 하면 돼요
    </div>

</body>
</html>
```





```css
div {
    width: 100px;
    height: 100px;
}

#div-1 {
    margin-left:auto;
}

#div-2 {
    margin-right:auto;
}

#div-3 {
    margin-left:auto;
    margin-right:auto;
}

#div-4 {
    margin:auto;
}

```

![](C:\Users\student\Desktop\typora\image\0730-14.PNG)





## 실습

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="06_box_model_2.css">
    <title>Document</title>
</head>
<body>
    <!--display-->
    <!--1. block level element-->
    <h1>
        이것은 block 요소, 기본적으로 너비의 100% 차지
    </h1>

    <div>
        너비가 정해지면 나머지를 마진으로~~!
    </div>

    <div id="div-1">
        block의 오른쪽 마진을 오토로 주면 왼쪽으로 붙어요 (왼쪽정렬)
    </div>

    <div id="div-2">
        block의 왼쪽 마진을 오토로 주면 오른쪽으로 붙어요 (오른쪽정렬)
    </div>

    <div id="div-3">
        block의 왼쪽/오른쪽 마진을 auto로 주면 가운데 정렬~
    </div>

    <div id="div-4">
        중앙정열은 그냥 margin auto로 하면 돼요
    </div>
    <hr>

    <!--2. inline level element-->
    <span>인라인 요소</span>
    <input type="text" placeholder="텍스트를 입력하세요">
    <input type="date">

    <!--3. inline-block element-->
    <p>
        p태그는 원래 block level 요소지요?
    </p>
    <hr>
    <p>
        이제는 inline-block 요소가 되어 붙을 거에요
    </p>
    <hr>
    <!--None-->
    <div id="div-5">
        이건 display none 속성입니다. 요소가 보이지도 않고 영역도 차지하지 않아요.
    </div>

    <!-- visibility-->
    <!-- 1. visible 기본값
    2. hidden -->

    <hr>
    <div id="div-6">
        이건 해당 요소를 안보이게 하지요,
        display none과 다른건 기둥뒤에공간이 있어요
    </div>


</body>
</html>
```



```css
div {
    width: 100px;
    height: 100px;
}

#div-1 {
    margin-left:auto;
}

#div-2 {
    margin-right:auto;
}

#div-3 {
    margin-left:auto;
    margin-right:auto;
}

#div-4 {
    margin:auto;
}

/* p {
    display: inline-block;
} */

#div-5 {
    display : none
}

#div-6 {
    visibility : hidden
}

body {
    background-image: url("images/탕수육.jfif") 
    bac
}
```

