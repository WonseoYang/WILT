## Array 객체 #2

### arr.sort(fn)

배열을 재정렬 한다.
값을 반환만 하는 것이 아닌 배열 자체를 변경한다.
인수로 함수를 받을 수 있다.

한 자릿수의 정수들

```javascript
const arr = [2, 5, 4, 1, 3];

arr.sort(); // [1, 2, 3, 4, 5]
```

문자열

```javascript
const arr = ['b', 'a', 'e', 'c', 'd'];

arr.sort(); // ["a", "b", "c", "d", "e"]
```

두 자릿수 이상의 정수들 - 올바르지 않은 사용법

```javascript
const arr = [27, 8, 5, 13];

arr.sort(); // [13, 27, 5, 8]
//정렬 시 숫자 또한 문자형으로 취급하기 때문에 가장 앞에 있는 숫자로만 정렬이 된 것.
```

두 자릿수 이상의 정수들 - 올바른 사용법 (오름차순)

```javascript
const arr = [27, 8, 5, 13];

arr.sort((a, b) => {
  // 함수를 인수로 받아 정렬 시 특정한 로직을 수행하도록 함.
  return a - b;
}); // [5, 8, 13, 27] - 오름차순으로 정렬된 모습
//arr.sort((a,b)=>a-b);와 동일
```

두 자릿수 이상의 정수들 - 올바른 사용법 (내림차순)

```javascript
const arr = [27, 8, 5, 13];

arr.sort((a, b) => {
  // 함수를 인수로 받아 정렬 시 특정한 로직을 수행하도록 함.
  return b - a;
}); // [27, 13, 8, 5] - 내림차순으로 정렬된 모습
arr.sort((a, b) => b - a);
```

### arr.reduce(fn)

함수를 인자로 받아 배열을 돌며 특정한 동작을 시행하여 누적하는 계산을 시행한 값을 반환한다.

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.reduce((prev, cur) => {
  // 해당 함수는 누적하는 값(prev), 배열을 도는 값(cur)으로 받아
  return prev + cur; // 특정 동작(현재는 누적하여 더하기)를 시행한 값을 반환한다.
}, 0); // 누적 값의 초기 값 (현재는 0)
```

다른 예시로 객체에서 성인 나이만 찾아서 배열 형태로 반환값을 다른 변수에 할당하는 모습)

```javascript
const arr = [
  {name: 'Mike', age: 15},
  {name: 'Julie', age: 26},
  {name: 'Sam', age: 29},
  {name: 'Jake', age: 30},
  {name: 'Harry', age: 10},
];

const result = arr.reduce((prev, cur) => {
  if (cur.age > 19) {
    // 현재 도는 위치의 .age가 19보다 크다면
    prev.push(cur.name); // 최종적으로 반환 할 배열에 삽입
  }

  return prev; // 배열을 다 돌았다면 누적된 값을 반환
}, []); // 초기 값은 빈 배열

// result의 값은 ["Julie", "Sam", "Jake"]
```

### arr.reduceRight(fn)

arr.reduce()와 같지만 배열을 도는 순서가 좌측(앞)이 아닌 우측(뒤)부터라는 차이점만 존재한다.

```javascript
const arr = ['요', '하세', '안녕'];

const result = arr.reduceRight((prev, cur) => prev + cur, []);

// "안녕하세요"
```
