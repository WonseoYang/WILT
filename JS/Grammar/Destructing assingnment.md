# 구조 분해 할당

객체와 배열은 자바스크립트에서 가장 많이 쓰이는 자료 구조 중 하나이다.

개발을 하다 보면 객체나 배열의 일부가 필요하거나 복사해서 새로운 객체나 배열이 필요한 경우가 생기는 그때 유용하게 사용할 수 있는 문법이 구조 분해 할당(Destructuring assignment)이다.

우선 말 그대로 구조를 분해하여 그 값을 할당하는 것으로
객체, 배열 등을 분해하여 값을 다른 변수에 각각 할당한다.

구조 분해 할당 구문은 객체나 배열의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 ES2015에 새로 추가된 자바스크립트 표현식

```javascript
const before = ['첫번째 값', '두번째 값', '세번째 값'];

const [after1, after2, after3] = before;
//const after1 = before[0];
//const after2 = before[1];
//const after3 = before[2]; 와 같은 로직

console.log(after1); // "첫번째 값"
console.log(after2); // "두번째 값"
console.log(after3); // "세번째 값"
```

### str.split()을 응용한 구조 분해 할당

```javascript
const before = '첫번째 값-두번째 값-세번째 값';

const [after1, after2, after3] = before.split('-');
// before 문자열을 "-"을 기준으로 분해하여 after1,2,3에 구조 분해 할당

console.log(after1); // "첫번째 값"
console.log(after2); // "두번째 값"
console.log(after3); // "세번째 값"
```

### 할당하는 갯수가 맞지 않을 때

위치가 맞물리지 않는 값은 `undefined` 값을 받는다.

```javascript
const [a, b, c] = [1, 2];

console.log(a); // 1
console.log(b); // 2
console.log(c); // undefined
```

이러한 문제는 기본 값(초기 값)을 설정 해주면 해결이 가능하다.

```javascript
const [a, b, c = 0] = [1, 2];

console.log(a); // 1
console.log(b); // 2
console.log(c); // 0
```

### 필요하지 않은 값을 무시

할당받는 변수 명을 비워두면 해결이 가능하다.

```javascript
const [a, , c] = [1, 2, 3];

console.log(a); // 1
console.log(c); // 3
```

### 값 서로 바꾸기

보통 두 변수 간의 값을 바꿀 때는 한 값을 잃어버리기 때문에 중간에 임시 변수를 하나 만들어 교환해야 했지만 구조 분해에서는 간단히 값 변경이 가능하다.

```javascript
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1
```

### 객체 구조 분해 할당

다른 점은 할당 받을 변수를 객체 처럼 `{` `}`로 감싸주면 된다.

```javascript
const user = {
  name: 'Mike',
  age: 26,
};

const {name, age} = user;

console.log(name);
console.log(age);
```

분해하여 할당받는 변수 명은 객체의 프로퍼티 값에 보통 맞춰야 하지만
할당받는 변수 명을 바꿀 때는 해당 문법과 같이 바꾸면 다른 변수 명에 프로퍼티의 값을 할당받을 수 있다.

```javascript
const user = {
  name: 'Mike',
  age: 26,
};

let {name: userName, age: userAge} = user;
//name 프로퍼티의 값을 userName 변수에 할당
//age 프로퍼티의 값을 userAge 변수에 할당

console.log(userName); // "Mike"
console.log(userAge); // 26
```

### 객체 구조 분해 할당 - 기본 값 주기

객체 또한 배열 처럼 구조 분해 할당 시에 기본 값(초기 값)을 정해줄 수 있다.

```javascript
const user = {
  name: 'Mike',
  age: 26,
};

const {name, age, gender = 'male'} = user; // user 객체에 gender 위치의 세번쨰 프로퍼티 값은 존재하지 않지만 기본값("male")을 주어 분해하여 할당 되지 않아도 값을 존재한다.

console.log(name); // "Mike"
console.log(age); // 26
console.log(gender); // "male"
```

**_구조 분해 할당 시에 기본 값은 말 그대로 기본 값이기에 객체나 배열에 해당 위치에 맞는 값이 존재한다면 그 값으로 덮어 씌워진다._**
