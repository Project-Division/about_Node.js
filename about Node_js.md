# 1. 모듈로 만들기

## ```checkEven.js```
```javascript
function isEven(val) {
    if (val % 2 == 0)
        return true;
    return false;
}

module.exports = {
    isEven
};
```

## ```test.js```
```javascript
const { isEven } = require("./checkEven")

if (isEven(5))
    console.log("짝수 입니다.");
else
    console.log("홀수 입니다.");
```

```
홀수 입니다.
```