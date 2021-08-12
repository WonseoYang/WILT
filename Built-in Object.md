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
