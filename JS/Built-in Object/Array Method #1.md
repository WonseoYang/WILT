## Array 객체 #1

### arr.slice(n, m)

배열의 `n` 위치 인덱스부터 `m` 위치 인덱스까지만 남기고 전부 삭제한다.

```javascript
let str = [0, 1, 2, 3, 4, 5, 6];

console.log(str.slice(2, 4)); // [2, 3]
//2번째 인덱스부터 4번째 인덱스까지만 잘라서 반환
```

**_반환 O / 변경 X_**

### arr.splice(n, m)

배열의 `n` 위치의 인덱스부터 `m`개 값을 인덱스까지 삭제한다.
또한 해당 결과를 반환하기도 하여 다른 값에 할당 또한 할 수도 있다.

```javascript
let str = [0, 1, 2, 3, 4, 5, 6];
str.splice(2, 2); // 2번째 인덱스부터 2개의 값을 삭제
console.log(str); // [0,1,4,5,6]
```

**_반환 O / 변경 O_**

#### arr.splice(n, m, x) - 지운 후에 추가까지 하는 법

배열의 `n` 위치의 인덱스부터 `m`번만큼 뒤의 값을 인덱스까지 삭제하고 삭제된 자리에 x값을 추가한다.

```javascript
let str = [0, 1, 2, 3, 4, 5, 6];
str.splice(2, 2, '삭제된 자리'); // 2번째 인덱스부터 2개의 값을 삭제하고 삭제된 자리에 "삭제된 자리" 추가
console.log(str); //[0, 1, "삭제된 자리", 4, 5, 6]
```

### arr.concat(arr2, arr3, ...)

배열을 합쳐서 새 배열을 반환.

```javascript
let arr = [0, 1, 2, 3];
let arr2 = [4, 5, 6];

console.log(arr.concat(arr2)); // [0, 1, 2, 3, 4, 5, 6]
// arr 배열에 arr2를 붙여서 반환.
```

### arr.forEach(fn)

`forEach메소드`는 함수를 인자로 받고 함수의 매개변수로 해당 배열의 값과 인덱스를 받아서 사용된다.

간단한 예시로는

```javascript
let arr = ['0번째 자리', '1번째 자리', '2번째 자리', '3번째 자리', '4번째 자리', '5번째 자리'];

arr.forEach((value, index) => {
  console.log(index + '의 값은 ' + value); // 배열을 돌며 차례대로 맞는 값과 인덱스 번호를 출력.
});
```

### arr.indexOf()

배열 내에서 특정 값의 인덱스 번호를 알아낼 때 사용한다.

```javascript
let arr = [1, 2, 3, 4, 5];
//3을 찾는다.
console.log(arr.indexOf(3)); // 2
```

찾으려는 값이 중복된 경우 찾을 때에는

```javascript
let arr = [1, 2, 3, 4, 5, 3, 4, 5];
//3을 4번째 인덱스부터 찾는다.
console.log(arr.indexOf(3, 4)); // 5
// 4번째 인덱스부터 찾기에 2번째 인덱스에 있는 3이 잡히지 않은 모습
```

### arr.lastIndexOf()

배열 내에서 특정 값의 인덱스 번호를 알아낼 때 사용한다.
**_다만 `arr.indexOf()`와 다른 점이라면 `arr.lastIndexOf()`는 뒤에서부터 탐색한다._**

```javascript
let arr = [1, 2, 3, 4, 5, 3, 4, 5];

console.log(arr.lastIndexOf(3)); // 5
```

### arr.includes(x)

`String 객체`의 `str.includes()` 같은 동작.
해당 배열 내에 특정 값(x)이 포함되어 있는지 확인하여 `true` / `false` 값을 반환 함.

```javascript
let arr = [1, 2, 3, 4, 5];

arr.includes(3); // true
arr.includes(10); // false
```

### arr.find(fn)

`arr.includes()`와 비슷하지만 함수를 인자로 받아 보다 더 세밀한 값을 찾아낼 수 있음.
ex) 짝수 찾기, 소수 찾기, 특정 범위 내의 값 찾기 등등...
**_단, 첫번째 `true값`을 반환하고 끝이며 값을 찾지 못하면 `undefined`를 반환_**

```javascript
let arr = [1, 2, 3, 4, 5, 3, 4, 5];

console.log(
  arr.find((value) => {
    return value % 2 == 0;
  }),
);

//2
//첫번째 인덱스부터 반복하여 값을 2로 나누어 나머지가 없는 값을 반환
```

### arr.findIndex(fn)

`arr.find()`와 비슷하지만 반환하는 것이 값이 아닌 인덱스.
**_단, 첫번째 `true`값을 반환하고 끝이며 값을 찾지 못하면 `-1`을 반환_**

```javascript
let arr = [1, 2, 3, 4, 5, 3, 4, 5];

console.log(
  arr.findIndex((value) => {
    return value % 2 == 0;
  }),
);

//1
//첫번째 인덱스부터 반복하여 값을 2로 나누어 나머지가 없는 값의 인덱스를 반환
```

조금 더 예를 들어보면 유저들의 이름과 나이가 저장된 객체를 배열 형태로 하여 성인이 아닌 사람을 찾을 때

```javascript
let userList = [
  {name: 'Mike', age: 25},
  {name: 'Julie', age: 28},
  {name: 'Sam', age: 15},
  {name: 'Jack', age: 26},
];

console.log(
  userList.findIndex((user) => {
    return user.age < 20;
  }),
);

// 2
// userList를 돌며 각 객체의 age가 20 미만인 것이 걸리면 해당 객체의 인덱스를 반환.
```

### arr.filter(fn)

`arr.find()`와 `arr.findIndex()`는 첫번째 `true`값을 반환하고 끝이지만
`arr.filter`는 모든 `true` 값들로 새로운 배열을 만들어 반환한다.

```javascript
let arr = [1, 2, 3, 4, 5, 6, 7, 8];

console.log(
  arr.filter((num) => {
    return num % 2 == 0;
  }),
);

// [2, 4, 6, 8]
```

### arr.reverse()

배열의 모든 값들을 역순으로 재정렬한다.

```javascript
let arr = [1, 3, 5, 2, 4, 6];

console.log(arr.reverse());

// [6, 4, 2, 5, 3, 1]
```

### arr.map(fn)

인자를 함수로 받아 배열을 돌며 함수 내에 특정 동작을 실행하고 새로운 배열을 반환한다.

간단한 예시로 이름과 나이만 있는 배열을 받아 인덱스 번호보다 1이 큰 아이디를 각각 부여하고 성인인이 아닌지의 여부를 객체 내에 추가하는 것을 예로 들겠다.

```javascript
let userList = [
  {name: 'Mike', age: 25},
  {name: 'Julie', age: 28},
  {name: 'Sam', age: 15},
  {name: 'Jack', age: 26},
];

let fixedUserList = userList.map((user, index) => {
  return Object.assign({id: index + 1}, user, {
    //(1)
    isAdult: user.age >= 20, //(2)
  });
});

console.log(fixedUserList);
// {id: 1, name: "Mike", age: 25, isAdult: true}
// {id: 2, name: "Julie", age: 28, isAdult: true}
// {id: 3, name: "Sam", age: 15, isAdult: false}
// {id: 4, name: "Jack", age: 26, isAdult: true}
```

**-설명-**
(1) : userList 배열을 돌며 함수 내에 적힌 특정 동작을 실행하여 반환하는 값을 fixedUserList에 할당한다.

(2)반환할 값은 `id`라는 프로퍼티에 인덱스 번호에서 1을 더한 값을 할당하여 초기화 하고 `userList`를 도는 값인 `user(객체)`를 받아 덮어 씌우며 `isAdult`라는 프로퍼티에 나이가 20이 넘어가면 `true`값을 아니면 `false`값을 반환하여 부여하는 프로퍼티와 값을 추가한다.

### Array.isArray()

배열은 자바스크립트 내장객체에 해당하기 때문에 일반 객체를 `typeof`로 찍어내면 둘 다 `객체(object)`로 반환한다.

때문에 `isArray()` 메소드로 구분을 지어서 확인할 수 있도록 한다.

```javascript
let user = {
  name: 'Mike',
  age: 26,
};

let userList = ['Mike', 'Julie', 'Sam'];

console.log(typeof user); // object
console.log(typeof userList); // object

console.log(Array.isArray(user)); // false
console.log(Array.isArray(userList)); // true
```

### arr.join()

배열 안의 값 들을 문자형으로 합친다.

```javascript
let arr = ['안녕', '하세', '요'];

console.log(arr.join());
// 안녕,하세,요
console.log(arr.join(''));
// 안녕하세요
console.log(arr.join('/'));
// 안녕/하세/요
```

### .split(x)

arr.join()과 반대로 문자형을 특정 값(x)을 기준으로 나누어 배열에 저장하여 반환한다.

```javascript
let arr = '1525354';

console.log(arr.split(5));
//["1", "2", "3", "4"]
```

### arr.includes()

배열에 포함되어있는 지를 확인하여 `true`, `false' 값을 반환하는 메소드이다.

```javascript
const b = [1, 2, 3, 4, 5, '안녕'];

b.includes(5); // true
b.includes(26); // false
b.includes('안녕'); // true
b.includes('하세요'); // false
```
