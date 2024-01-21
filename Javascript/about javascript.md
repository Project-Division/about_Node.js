***
# 1. 변수 선언

### 1. const
- 블록 스코프
- 상수이므로 **한번 값을 대입하면 변경할 수 없음**
```javascript
if (true) {
    const x = 3;
}
console.log(x); // 오류 발생(x가 정의되지 않음)
```

### 2. let
- 블록 스코프
```javascript
if (true) {
    let x = 3;
}
console.log(x); // 오류 발생(x가 정의되지 않음)
```

### 3. var
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

> ## 장점
 ### 1. 기존 함수 사용
 #### this로 현재 객체의 name 참조 불가능
```javascript
var obj = {
    name: 'zero',
    friends: ['nero', 'hero', 'xero'],

    print_names: function() {
        this.friends.forEach(function(friend) {
           console.log(this.name, friend);
        });
    },
}

obj.print_names();
```

```markdown
undefined nero
undefined hero
undefined xero
```

### 2. 화살표 함수 사용
#### this로 현재 객체의 name 참조 가능
```javascript
var obj = {
    name: 'zero',
    friends: ['nero', 'hero', 'xero'],

    print_names: function() {
        this.friends.forEach((friend) => {
           console.log(this.name, friend);
        });
    }
}

obj.print_names();
```

```markdown
zero nero
zero hero
zero xero
```

<br><br>
***

# 5. 비구조화 할당
### 1. 인덱스로 접근
```javascript
var array = ['nodejs', {}, 10, true];

node = array[0];
obj = array[1];
bool = array[3];

console.log(`node = ${node}, obj = ${obj}, bool = ${bool}`);
```

```
node = nodejs, obj = [object Object], bool = true
```

### 2. 비구조화 할당 사용
```javascript
var array = ['nodejs', {}, 10, true];

const [node, obj, val, bool] = array;

console.log(`node = ${node}, obj = ${obj}, bool = ${bool}`);
```

```
node = nodejs, obj = [object Object], bool = true
```

<br><br>
***

# 6. 프로미스
### 콜백 함수 대신 사용

### 1. 
```javascript
const condition = true;

const p = new Promise((resolve, reject) => {
    if (condition)
        resolve("성공");
    else
        reject("실패");
});

p.then((message) => {
    console.log(message);
})
.catch((error) => {
    console.error(error);
})
```

```
성공
```

### 2. 여러 개를 한번에 실행 (Promise.all)

```javascript
const condition = true;

const p1 = new Promise((resolve, reject) => {
    if (condition)
        resolve("성공1");
    else
        reject("실패1");
});

const p2 = new Promise((resolve, reject) => {
    if (condition)
        resolve("성공2");
    else
        reject("실패2");
});

Promise.all([p1, p2]).then((message) => {
    console.log(message);
})
.catch((error) => {
    console.error(error);
})
```

```
[ '성공1', '성공2' ]
```

<br><br>
***

# 7. async / await

### async 키워드로 비동기로 처리할 함수 정의, setTimeout으로 스레드 생성
### async 함수 내에서 다른 async 함수를 호출할 때 함수 이름 앞에 await 사용

```javascript
const f = async () => {
  var t = Date.now();
  while (t + 2000 > Date.now())
    continue;
  return "2초 경과";
};

async function _main() {
    console.log("start");

    var msg = await f();
    console.log(msg);

    console.log("end");
}

setTimeout(_main, 0);
```

```
start
2초 경과
end
```

<br><br>
***
# 8. foreach, for ... in

> foreach
### array 객체에만 사용 가능

```javascript
var arr = ["apple", "banana", "apple"];
arr.forEach((name) => { console.log(name); });
```

```
apple
banana
apple
```

<br>

> for ... in

### 객체의 key 값에 접근

```javascript
var obj = {'key1': 'value1', 'key2': 'value2'};
for (var key in obj) {
    console.log(key, obj[key]);
}
```

```
key1 value1
key2 value2
```