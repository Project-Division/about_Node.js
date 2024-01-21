***
# res 객체

> 메서드

* res.send(버퍼, 문자열, html, json)

* res.sendFile(파일 경로)

* res.json(JSON 데이터)

* res.redirect(주소)

* res.render('템플릿 파일 경로', { 변수 })


<br><br>
***

# EJS 템플릿 엔진

### HTML 문법을 그대로 사용하고 추가로 자바스크립트 문법을 사용할 수 있음

<br>

> ejs 설치

```
npm i ejs
```

> view engine 설정

```javascript
...

app.set('views', path.join(__dirname, 'views'))
app.set('view engine', 'ejs')

...
```

<br><br>

> index.js

```javascript
...

app.get("/login/:id", (req, res, next) => {
    let user_id = req.params.id;
    let query = req.query;

    res.render('login', {
        user_id, query
    });
});

...
```

> views/login.ejs

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h1>user_id = <%= user_id %></h1>

    <% for (var key in query) { %>
        <h3>key = <%= key %>, value = <%= query[key] %></h3>
    <% } %>
</body>
</html>
```

![사진](https://media.discordapp.net/attachments/1196215613144703076/1198453670833045545/image.png?ex=65bef5f5&is=65ac80f5&hm=b0c08450c1309662f619c9af79c706cd586612d930bcc07a6ec131ec46f9f5bf&=&format=webp&quality=lossless&width=1266&height=653)