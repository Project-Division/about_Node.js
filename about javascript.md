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
undefined nero // this로 현재 객체의 name 참조 불가능
undefined hero
undefined xero
```

### 2. 화살표 함수 사용
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
zero nero // this로 현재 객체의 name 참조 가능
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
