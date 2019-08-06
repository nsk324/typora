# 190731 | Web&HTML_CSS03

## font 바꾸기

> 07_font.html
>
> [https://fonts.google.com](https://fonts.google.com/)
>
> 

1. font size

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <meta http-equiv="X-UA-Compatible" content="ie=edge">
       <link rel="stylesheet" href="07_font.css">
       <link href="https://fonts.googleapis.com/css?family=Lacquer|Noto+Serif+KR&display=swap" rel="stylesheet">
       <title>Document</title>
   </head>
   <body>
       <h1>My font</h1>
       <p id="font1">
           산은 산이고 물은 물이로다....
           활기찬 하루 보내세요!
           (하지만 피곤함)
       </p>
       <p id="font2">
           mountain is mountain. water is water.
           Fighting!
           (However, I'm tired)
       </p>
   </body>
   </html>
   ```

   ![](C:\Users\student\Desktop\typora\image\0731-1.PNG)

```css
#font1 {
    font-size: 30px;
    font-family: 'Noto Serif KR', serif;
    font-weight: 500;
    letter-spacing: 5px;
    text-align: center;
}

#font2{
    font-size: 40px;
    font-family: 'Lacquer', sans-serif;
    font-weight: 500;
    letter-spacing: 5px;
    text-align: center;
}
```

![](C:\Users\student\Desktop\typora\image\0731-2.PNG)



## position

### 기본 위치

100px 100px

### 상대 위치

기본위치를 기준으로 얼만큼 떨어져 있는가? top, bottom, left,right를 사용하여 위치 이동\

### 절대위치

부모 또는 가장 가까이 있는 조상요소를 기준(기본 위치 말고)으로 좌표만큼 이동함

### 고정위치

부모 요소와 상관 없이 좌표를 사용하여 위치를 이동한다. 스크롤 이동해도 화면에서 사라지지않고 계속 ㅇ동한다.

```css
.fixed{
	position: fixed;
	bottom: 0;
	right : 0;
}
```

re

> 08_position.html 08_position.css

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="08_position.css">
    <title>Document</title>
</head>
<body>
    기본위치(static)
    <div>
        static
    </div>
    상대위치:static(기본위치)일 때를 기준으로 삼음
    <div class="relative">
        relative
    </div>
    절대위치(absolute)
    <div class="parent">
        부모 - relative
        <div class="absolute-child">
        자식 - absolute
        </div>
    </div>
    
    고정위치
    <div class="fixed">
        fixed
    </div>
</body>
</html>
```

```css
div {
    height: 100px;
    width: 100px;
    background-color: purple;
    line-height: 100px;
    text-align: center;
}

.relative {
    position: relative;
    top: 100px;
    left: 100px;
    background-color: purple;
    line-height: 100px;
    text-align: center;
}

.parent{
    position: relative;
}

.absolute-child {
    position:absolute;
    top: 50px;
    left: 50px;
}

.fixed {
    position:fixed;
    bottom:0;
    right:0;
}
```

