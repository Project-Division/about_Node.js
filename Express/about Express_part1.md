***
# Express 프레임워크

### Node.js에서 사용할 수 있는 웹 서버 프레임워크
### 미들웨어 사용, 확장성 면에서 우수

>설치
```
npm i express
```

<br><br>
***
# nodemon 모듈
### 서버 코드를 수정할 시 자동으로 서버를 재시작해주는 모듈

> 설치
```
npm i -D nodemon
```
> package.json 설정
```json
{
  "name": "express_test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "nodemon app" <<
  },
  "author": "",
  "license": "ISC"
}
```

<br><br>
***

# express로 웹서버 구동
> 코드
```javascript
const express = require('express');

const app = express();
app.set("port", 3000); // 서버 포트 설정

app.get("/", (req, res) => {
    res.send("Hello, World!");
});

app.listen(app.get("port"), () => {
    console.log(`${app.get("port")} 번 포트에서 대기중.`);
});
```

> 웹서버 구동 명령
```
npm start
```
![사진](https://media.discordapp.net/attachments/976023220769677342/1197366561317593188/image.png?ex=65bb0182&is=65a88c82&hm=5d5a59f803885ede639636ecc79759af01eb46aa1cc90b283611ef39c6833fd8&=&format=webp&quality=lossless&width=896&height=650)

> 구동된 웹

![사진](https://media.discordapp.net/attachments/976023220769677342/1197367433451798629/image.png?ex=65bb0252&is=65a88d52&hm=ac878428bd7b1eec5e4780b7b7ba1a37c5b7384a27c05709411d566af0c9b464&=&format=webp&quality=lossless&width=862&height=441)


<br><br>
***

# 미들웨어

### 요청과 응답의 중간에 위치하여 요청과 응답을 조작하여 기능을 추가하는 방법

> 미들웨어 실행 범위

|코드|작동범위|
|---|---|
|app.use(미들웨어 함수)|모든 요청|
|app.use('/abc', 미들웨어 함수)|abc로 시작되는 요청|
|app.use((err, req, res, next) => {})|오류 발생 시 실행|
|app.post('/abc', 미들웨어 함수)|abc로 시작되는 POST 요청|


<br>

> 모든 요청 미들웨어

```javascript
const app = express();
app.set("port", 3000);

app.use((req, res, next) => {
    console.log("요청이 실행될 때 마다 실행됨");
    next(); // 다른 등록된 미들웨어를 호출하기 위해 사용
});

...

```

![사진](https://media.discordapp.net/attachments/976023220769677342/1197368131711152261/image.png?ex=65bb02f8&is=65a88df8&hm=ce689142ffc2893037c042244fe778ca32816658a22a9338eeac56dad9d696ad&=&format=webp&quality=lossless&width=1120&height=316)


<br>

> POST 요청 미들웨어

```javascript
app.post("/test", (req, res, next) => {
    console.log("POST 요청에서 실행됨");
});
```

![사진](https://media.discordapp.net/attachments/976023220769677342/1197371131867439154/image.png?ex=65bb05c3&is=65a890c3&hm=eebece98ec1bb3324b3a1605aa8ee51741c590371ee4ab9c33547edfdf06f12f&=&format=webp&quality=lossless&width=1089&height=279)

![사진](https://media.discordapp.net/attachments/976023220769677342/1197371437569278042/image.png?ex=65bb060c&is=65a8910c&hm=a046a3e724b19031042227df0fd9c21b3221fa3efc64e26a3b0c3cecde2bce36&=&format=webp&quality=lossless&width=628&height=214)

> 오류 발생 시 미들웨어

```javascript
app.use((req, res, next) => {
    const err = new Error(`${req.method} ${req.url} 라우터가 없습니다.`);
    err.status = 404;
    next(error);
});

app.use((err, req, res, next) => {
    console.error(err);
    res.status(500).send(err.message);
});
```

### 지정되지 않은 라우터로 요청 발생할 시 404오류 발생

![사진](https://media.discordapp.net/attachments/1197382009174097990/1197402197256851476/image.png?ex=65bb22b2&is=65a8adb2&hm=1b2ac1f64c3482584667e9af50cb8e17c6fbe538c125eb7d639e84defc063ac3&=&format=webp&quality=lossless&width=771&height=459)

![사진](https://media.discordapp.net/attachments/1197382009174097990/1197382036877484063/image.png?ex=65bb0feb&is=65a89aeb&hm=3d896136a3d0aa740b5c515de69495a762a529cd312b1ea6740c730bac00153b&=&format=webp&quality=lossless&width=1335&height=402)

<br><br>
***

# static
### 정적인 파일들을 제공하는 라우터

> public 라우터를 프로젝트의 public 폴더의 파일에 접근하도록 설정

```javascript
app.use("/public", express.static(path.join(__dirname, "public")));
```

![사진](https://media.discordapp.net/attachments/1197382009174097990/1197402633774829618/image.png?ex=65bb231a&is=65a8ae1a&hm=1ee3daf27a0e29263f00ee1a2d2a920c21ab2f3f3eacfe45211216ce51efc696&=&format=webp&quality=lossless&width=1335&height=523)

![사진](https://media.discordapp.net/attachments/1197382009174097990/1197402779040370688/image.png?ex=65bb233d&is=65a8ae3d&hm=f28eeeafb195131d1fd17adfeb5548b6a1be461434a78c8efae38ebbea1e22fe&=&format=webp&quality=lossless&width=640&height=640)

<br><br>
***