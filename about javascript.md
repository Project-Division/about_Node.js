***
# 1. 변수 선언

>## 1. const
- 블록 스코프
- 상수이므로 **한번 값을 대입하면 변경할 수 없음**
```javascript
if (true) {
    const x = 3;
}
console.log(x); // 오류 발생(x가 정의되지 않음)
```

>## 2. let
- 블록 스코프
```javascript
if (true) {
    let x = 3;
}
console.log(x); // 오류 발생(x가 정의되지 않음)
```

>## 3. var
- 함수 스코프

```javascript
if (true) {
    var x = 3;
}
console.log(x); // 에러 없이 잘 실행됨
```

<br><br>
***


# 2. 템플릿 문자열
```javascript
const num1 = 1;
const num2 = 2;
console.log(`num1 = ${num1}, num2 = ${num2}`);
```

```
num1 = 1, num2 = 2
```

<br><br>
***

# 3. 객체 리터럴
```javascript
var sayNode = function() {
    console.log("Node");
};

var obj = {
    sayJS() {
      console.log("JS");
    },
    sayNode,
    es6: 'fantastic'
};

obj.sayJS();
obj.sayNode();
console.log(obj.es6);
```

```
JS
Node
fantastic
```

<br><br>
***
# 4. 화살표 함수
```javascript
add1 = function(x, y) {
  return x + y;
};

const add2 = (x, y) => { return x + y };

console.log(add1(3, 2));
console.log(add2(3, 2));
```

```
5
5
```