***
# Node.js 파일 시스템 접근

## fs모듈
   - 파일 시스템에 접근할 수 있게 해주는 모듈

<br>

## 1. 파일 읽기
### files/readme.txt
```
저를 읽어주세요.
```
### readFile.js
```javascript
const fs = require("fs");

fs.readFile("./files/readme.txt", (err, data) => {
    if (err)
        throw err;
    console.log(data);
    console.log(data.toString());
});
```

```
<Buffer ec a0 80 eb a5 bc 20 ec 9d bd ec 96 b4 ec a3 bc ec 84 b8 ec 9a 94 2e>
저를 읽어주세요.
```

<br>

## 2. 파일 쓰기

### writeFile.js
```javascript
const fs = require("fs")

fs.writeFile("./files/written.txt", "테스트", (err) => {
    if (err)
        throw err;
    console.log("쓰기 완료.");
});
```

### ./files/written.txt
```
테스트
```

<br>

## 3. 비동기 메서드

### 동기 메서드
   - 파일 읽기가 완료되면 콜백 함수가 실행됨.
   - 요청만 해두고 다음 코드를 실행함.

### 비동기 메서드
   - 파일 읽기가 완료되면 다음 코드가 실행됨

### 1. let data = fs.readFileSync(파일경로)
   - 읽은 데이터를 data 변수에 저장
   - 콜백 함수를 인자로 받지 않음

<br>

## 4. 기타 메서드들

### 1. fs.access(경로, 옵션, 콜백)
   - 폴더나 파일에 접근할 수 있는지 확인

***

> ### 디렉토리

### 1. fs.readdir(경로, 콜백)
### 2. fs.mkdir(경로, 콜백)
### 3. fs.rmdir(경로, 콜백)

***

> ### 파일

### 1. fs.unlink(경로, 콜백)
### 2. fs.rename(경로, 콜백)