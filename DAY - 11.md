## Number 객체

### toFixed()

소수점을 끊는 메소드이다.

```javascript
let num = 5.1537987897897123123;

num.toFixed(2); //5.15 - 2째 자리까지 끊는 모습.
```

### parseInt()

읽을 수 있는 부분까지를 정수형으로 변환하는 메소드

```javascript
let num = '50px';

parseInt(num); // 50
```

### parseFloat()

읽을 수 있는 부분까지를 실수형으로 변환하는 메소드

```javascript
let num = '26.125%';

parseFloat(num); // 26.125
```

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

# 추가 메모 사항

## 계산된 프로퍼티

이름 그대로 이미 계산이 완료된 프로퍼티(속성 명, 키 값)이다.
간단한 예를 통해서도 이해가 될만큼 개념은 쉽다.

다만 아직 나에겐 실사용에서 어떻게 유용하게 사용할 것인지는 고민해야봐야 할 개념이다.

```javascript
let n = 'name';

const user = {
  [n]: 'Mike', // name : "Mike",
  ['a' + 'ge']: 26, // age : 26,
  [4 + 1]: 5, // 5 : 5,
};
```

주석과 같이 동작하는 형태이다.

## Symbol

`Symbol`은 `객체 속성(object property)`을 만들 수 있는 `원시 데이터 형식(primitive data type)`이다.

`Symbol 형식`으로 할당을 하면 `독립적인 값`이 되기때문에, 같은 값으로 정의해도 같은 값이 아니다.

`Symbol 형식`의 값끼리도 예외는 아니다.

```javascript
const a = 5;
const b = Symbol(5);
const c = Symbol(5);

console.log(a); // 5
console.log(b); // 5
console.log(c); // 5

a == b; // false
a === b; // false

b == c; // false
b === c; // false
```

`Symbol 형식`으로 객체의 키를 선언하면 `for in`문과 위의 `Object 객체`의 메소드로 키를 확인하여도 확인되지 않는 특이점이 있다.

### Symbol.for()

위의 일반 `Symbol`과 다르게 `Symbol.for()` 형태로 선언하게 되면 같은 값끼리는 키를 공유하여 같은 값으로 인식한다.

```javascript
const a = 5;
const b = Symbol.for(5);
const c = Symbol.for(5);

console.log(a); // 5
console.log(b); // 5
console.log(c); // 5

a == b; // false
a === b; // false

b == c; // true
b === c; // true
```

## 번외 메소드

해당 메소드는 아직 배우지 않은 `prototype`이라는 메소드이다.

### includes()

문자열 또는 배열에서 포함되어있는 지를 확인하여 `true`, `false' 값을 반환하는 메소드이다.

```javascript
const a = '안녕하세요';
const b = [1, 2, 3, 4, 5];

a.includes('녕'); // true
a.includes('양'); // false
b.includes(5); // true
b.includes(26); // false
```
