***
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

<br><br>
***
# 2. console 객체

### - console.log(내용)
   - 콘솔에 로그 표시

### - console.dir(객체, 옵션)
   - 객체를 콘솔에 표시
```javascript
const obj = {
    name: 'outside',
    inside: {
        name: 'inside'
    }
};

console.dir(obj);
```
```
{ name: 'outside', inside: { name: 'inside' } }
```

<br><br>
***

# 3. 타이머

### - setTimeout(콜백함수, 밀리초)
   - 주어진 밀리초 이후에 콜백함수 실행
```javascript
const f = () => {
    console.log("2초 경과");
}

console.log("setTimeout 호출 전");
setTimeout(f, 2000);
console.log("호출 후");
```

```
setTimeout 호출 전
호출 후
2초 경과
```

### - clearTimeout(id)
   - setTimeout 취소

### - setInterval(콜백 함수, 밀리초)
   - 주어진 밀리초마다 콜백 함수를 반복 실행
```javascript
var count = 0;
var iv;

const f = () => {
    if (++count > 4)
        clearInterval(iv);
    console.log("1초마다 5번 실행됩니다.");
}

iv = setInterval(f, 1000);
```

```
1초마다 5번 실행됩니다.
1초마다 5번 실행됩니다.
1초마다 5번 실행됩니다.
1초마다 5번 실행됩니다.
1초마다 5번 실행됩니다.
```

### - clearInterval(id)
   - setInterval 취소

<br><br>
***

# 4. process 객체

## - process.env 객체

>시스템의 환경변수

```javascript
console.dir(process.env);
```

```
{
  USERDOMAIN_ROAMINGPROFILE: 'KKS_LAPTOP',
  PROCESSOR_LEVEL: '6',
  SESSIONNAME: 'Console',
  ALLUSERSPROFILE: 'C:\\ProgramData',
  PROCESSOR_ARCHITECTURE: 'AMD64',
  PSModulePath: 'C:\\Program Files\\WindowsPowerShell\\Modules;C:\\WINDOWS\\system32\\WindowsPowerShell\\v1.0\\Modules',
  SystemDrive: 'C:',
  USERNAME: 'kks00',
  'ProgramFiles(x86)': 'C:\\Program Files (x86)',
  FPS_BROWSER_USER_PROFILE_STRING: 'Default',
...
```

<br>

> dotenv 패키지

### .env 파일을 읽어 process.env 객체에 넣음

- .env
```
SECRET_KEY=test_key
```

- env.js
```javascript
require("dotenv").config();
console.dir(process.env);
```

```
{
  SECRET_KEY: 'test_key',
  ...
}
```

<br>

## - process.exit(코드)
   - 실행중인 노드 프로세스 종료

<br><br>
***

# 5. 예외 처리

```javascript
setInterval(() => {
    try {
        throw new Error("오류");
    } catch (err) {
        console.error(err);
    }
}, 1000);
```

```
Error: 오류
    at Timeout._onTimeout (C:\Users\kks00\Desktop\untitled\tests\error.js:3:15)
    at listOnTimeout (node:internal/timers:564:17)
    at process.processTimers (node:internal/timers:507:7)
...
```