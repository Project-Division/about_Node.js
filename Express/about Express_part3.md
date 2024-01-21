***
# Express 유용한 미들웨어

## 1. body-parser

#### 요청의 본문을 해석해주는 미들웨어

|메소드|본문 데이터 타입|
|---|---|
|bodyParser.json()|JSON|
|bodyParser.raw()|버퍼|
|bodyParser.text()|텍스트|

<br>

```javascript
const bodyParser = require('body-parser');

...
app.use(bodyParser.text()); // 본문 데이터 타입에 맞게 설정
app.use(bodyParser.urlencoded({
    extended: false
}));
...

app.post("/test", (req, res, next) => {
    console.log("/test POST 요청이 발생할 시 실행됨.");

    const req_data = req.body;

    for (var key in req_data) {
        console.log(key, req_data[key]);
    }

    res.send("OK");
});
```

![사진](https://media.discordapp.net/attachments/1196215613144703076/1198481282062094406/image.png?ex=65bf0fac&is=65ac9aac&hm=7f575e6705ce71e5248e9c215f142a0154d020ac0484fce6e047c88d11544565&=&format=webp&quality=lossless&width=1332&height=653)

![사진](https://media.discordapp.net/attachments/1196215613144703076/1198478268131725512/image.png?ex=65bf0cdd&is=65ac97dd&hm=ddc2fead8134186343ace1c07b072929eec50f825dc1b357d0a22a19741a141c&=&format=webp&quality=lossless&width=574&height=129)

<br><br>
***

## 2. cookie-parser

#### 요청에 동봉된 쿠키를 해석해주는 미들웨어

```javascript
const cookieParser = require("cookie-parser");

...
app.use(cookieParser());
...

app.post("/cookies_test", (req, res, next) => {
    console.log("/cookies_test POST 요청이 발생할 시 실행됨.");

    console.dir(req.cookies);

    res.send("OK");
});
```

![사진](https://media.discordapp.net/attachments/1196215613144703076/1198481462723358780/image.png?ex=65bf0fd7&is=65ac9ad7&hm=84b1b12b174778d75af5e03b32eaeffc7620764965d01f38a734424e92f7cc08&=&format=webp&quality=lossless&width=1299&height=653)

![사진](https://media.discordapp.net/attachments/1196215613144703076/1198481650351353896/image.png?ex=65bf1004&is=65ac9b04&hm=34d0adb2b255b9e97c004028ae15ef9642110a6e00e8ad2053e64af439383214&=&format=webp&quality=lossless&width=720&height=122)

<br><br>
***

## 3. express-session

#### 세션 관리용 미들웨어
#### 생성된 req.session 객체에 값을 대입하거나 삭제하여 이용

<br>

> 설치
```
npm i express-session
```

<br>

```javascript
var session = require('express-session');

app.use(session({
    resave: false, // 요청 왔을 때 세션에 변경사항 없어도 다시 저장
    saveUninitialized: true, // 저장할 내역 없어도 저장
    secret: process.env.COOKIE_SECRET_KEY,
    cookie: {
        httpOnly: true, // 클라이언트에서 쿠키 확인 불가능
        secure: false // https 사용 시 true
    }
}));

...
app.use((req, res, next) => {
    console.log("요청이 실행될 때 마다 실행됨");

    console.log(`현재 세션 id = ${req.sessionID}`);
    console.dir(req.session);

    next();
});
...
```

```
현재 세션 id = zZ5uf2Re2I8dXCcEB6x8M82YqcUF4cjs
Session {
  cookie: {
    path: '/',
    _expires: null,
    originalMaxAge: null,
    httpOnly: true,
    secure: false
  }
}
```