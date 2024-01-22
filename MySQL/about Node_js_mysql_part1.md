***
# 1. 테이블 생성

> test_node_js 데이터베이스를 생성하고, users 테이블 생성

![사진](https://media.discordapp.net/attachments/1197382009174097990/1198807796112699513/image.png?ex=65c03fc3&is=65adcac3&hm=dc62922a95a17580c382483bd120481732d6cb4ee6f096b29df9ee61717963af&=&format=webp&quality=lossless&width=1094&height=654)

> 테스트를 위해 임의로 유저 3명 추가

![사진](https://media.discordapp.net/attachments/1197382009174097990/1198807940761665596/image.png?ex=65c03fe5&is=65adcae5&hm=57e64895988057e05b418ba90d182b12a5daf3375669896e56a08d6e11ed3e7e&=&format=webp&quality=lossless&width=1023&height=396)

<br><br>
***

# 2. 데이터베이스와 연동

> 오류 해결을 위한 작업

[Client does not support authentication protocol requested by server.](https://velog.io/@zedy_dev/MySQL-%EC%97%90%EB%9F%AC-%ED%95%B4%EA%B2%B0-Client-does-not-support-authentication-protocol-requested-by-server.-plugin-type-was-sha256password)

<br>

> mysql 라이브러리 설치

```
npm i mysql
```

<br>

> DB와 연결

>> .env
```
SQL_SERVER_HOST=localhost
SQL_SERVER_USER=root
SQL_SERVER_PASSWORD= **masked**
SQL_SERVER_DATABASE=test_node_js
```

>> 
```javascript
require("dotenv").config();

const mysql = require('mysql');

const connection = mysql.createConnection({
    host: process.env.SQL_SERVER_HOST,
    user: process.env.SQL_SERVER_USER,
    password: process.env.SQL_SERVER_PASSWORD,
    database: process.env.SQL_SERVER_DATABASE
});

connection.connect();

connection.end();
```

***
<br><br>

# 3. 연동된 데이터베이스에서 데이터 가져오기

```javascript
...
connection.query(`SELECT * FROM users`, (error, rows, fields) => {
    if (error) throw error;
    console.dir(rows);
});
...
```

<br>

![사진](https://media.discordapp.net/attachments/1197382009174097990/1198814126873513984/image.png?ex=65c045a8&is=65add0a8&hm=ff3f4c5c2face14d02f5c421c3617325bd6d1984ed103a0e3b9423ed07e99ae6&=&format=webp&quality=lossless&width=851&height=257)