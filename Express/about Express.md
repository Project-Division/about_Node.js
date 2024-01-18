***
# Express 프레임워크

- Node.js에서 사용할 수 있는 웹 서버 프레임워크
- 미들웨어 사용, 확장성 면에서 우수

>설치
```
npm i express
```

<br><br>
***
# nodemon 모듈
- 서버 코드를 수정할 시 자동으로 서버를 재시작해주는 모듈
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

> 구동된 웹서버

![사진](https://media.discordapp.net/attachments/976023220769677342/1197365506068459551/image.png?ex=65bb0086&is=65a88b86&hm=4b93e405718576938d9acb07c56e8001e0c65975d488b0736b44f155f61d2375&=&format=webp&quality=lossless&width=1102&height=650)

