## String 객체

### length

문자열의 길이를 반환한다.

```javascript
const text = '안녕하세요';

text.length; // 5
```

### desc

특정 위치에 접근한다.

```javascript
const text = '안녕하세요';

text[2]; // 녕
```

### toUpperCase() / toLowerCase()

영문 문자열을 전부 대문자 / 소문자로 변환시킨다.

```javascript
const text = 'Hello, Everyone';

text.toUpperCase(); //"HELLO, EVERYONE"
text.toLowerCase(); //"hello, everyone"
```

### str.indexOf(text)

문자열에서 `text`의 위치를 찾는다.

```javascript
const desc = '안녕하세요';

desc.indexOf('녕'); // 2
```

찾는 문자열이 포함되어 있지 않다면 `-1`을 반환한다.

### str.slice(n, m)

str에서 n 위치부터 m 위치의 전까지를 잘라서 반환한다.

다만 m위치가 존재하지 않으면 끝까지 잘라서 반환하며
m이 음수로 주어지면 끝에서부터 세는 것으로 한다.

**_주의할 점은 문자열의 위치는 0부터 시작한다._**

ex) -3이면 끝에서 3번째의 문자열의 전까지

```javascript
const desc = '안녕하세요';

desc.slice(2, 4); // "하세"
//2번째인 '하'부터 4번째인 '요'의 전인 '세'까지 잘라낸다.
```

### str.subString(n, m)

`slice 메소드`와 마찬가지로 문자열을 잘라낸다.
다른 점은 n과 m을 바꿔도 동작한다는 차이다.

```javascript
const desc = '안녕하세요';

desc.slice(4, 2); // "하세"
//2번째인 '하'부터 4번째인 '요'의 전인 '세'까지 잘라낸다.
```

### str.substr(n, m)

마찬가지로 문자열을 잘라낸다.
다른 점은 `n`부터 시작하여 `m`개의 문자열을 잘라서 반환한다는 것이다..

```javascript
const desc = '안녕하세요';

desc.slice(2, 2); // "하세"
//2번째인 '하'부터 시작하여 2개인 '세'까지 잘라낸다.
```

### str.trim()

문자열의 시작과 끝에만 있는 공백을 제거 한다.

```javascript
const desc = '   안녕 하십니까              ';

desc.trim(); // "안녕 하십니까"
```

### str.repeat(n)

문자열을 `n`번 반복한다.

```javascript
const desc = 'Hi! ';

desc.repeat(4); // "Hi! Hi! Hi! Hi! "
```

### str.prototype.replaceAll

문자열 a를 b로 치환한다.

다만 문자열 자체를 변경하는 것이 아닌 변경된 값을 반환한다.

```javascript
const text = "I Love BackEnd, I'm BackEnd Developer";

console.log(text.replaceAll('BackEnd', 'FrontEnd'));
// I Love FrontEnd, I'm FrontEnd Developer
```

### str.includes()

문자열에서 포함되어있는 지를 확인하여 `true`, `false' 값을 반환하는 메소드이다.

```javascript
const a = '안녕하세요';

a.includes('녕'); // true
a.includes('양'); // false
```

</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
