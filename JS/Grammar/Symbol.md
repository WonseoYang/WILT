## Symbol

`Symbol`은 `객체 속성(Object Property)`을 만들 수 있는 `원시 데이터 형식(Primitive Data Type)`이다.

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

</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
