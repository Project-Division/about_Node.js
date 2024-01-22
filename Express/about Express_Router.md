***
# 라우터별로 분리하여 소스 작성하기

> index.js

```javascript
...
const login_router = require("./routes/login");
app.use("/login", login_router);
...
```

> ./routes/login.js

```javascript
const express  = require("express");

const router = express.Router();

router.get("/:id", (req, res, next) => {
    let user_id = req.params.id;
    let query = req.query;

    res.render('login', {
        user_id, query
    });
});

module.exports = router;
```

<br>

![사진](https://media.discordapp.net/attachments/1197382009174097990/1198826000876851300/image.png?ex=65c050b7&is=65addbb7&hm=a58c72e2ae8fb2dbbcc709887ddb7e65fbefcb2bd888c1e722f6d0056ac3c014&=&format=webp&quality=lossless&width=1094&height=654)

