# 전개 구문

`전개구문 (Spread Syntax)`이란 나머지 매개변수처럼 `...변수명`의 형태로 생겼으나 생김새는 많이 다르다.

아래의 예로 간단히 살펴보겠다.

**전개구문을 이용하여 한 객체의 모든 내용을 다른 객체 안에 집어넣기**

```javascript
const user1 = {name: 'Mike'};
const user2 = {...user1, age: 30}; // user1 객체의 내용을 user2 객체 내 앞 부분에 삽입
user2.name = 'Sam';

console.log(user1); // { name: 'Mike' }
console.log(user2); // { name: 'Sam', age: 30 }
```

**배열 내에 순서를 건드리지 않고 배열 끼리의 순서를 바꿔 집어넣기**

```javascript
let arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

arr1 = [...arr2, ...arr1]; // arr1 배열 안에 전개 구문을 이용하여 arr2 배열을 넣고 그 뒤에 arr1을 넣음

console.log(arr1); // [ 4, 5, 6, 1, 2, 3 ]
```

**객체와 배열 형태들을 한 객체 안에 저장할 때**

```javascript
let user = {name: 'Mike'};
let info = {age: 30};
let fe = ['JS', 'React'];
let lang = ['Korean', 'English'];

user = {
  user, // user 객체 내용을 넣고
  info, // info 객체 내용을 넣고
  skills: [...fe, ...lang], // skills 프로퍼티의 배열 값 안에는 fe와 lang의 모든 정보를 전개구문을 통하여 집어넣음
};

console.log(user);
//	{
//		user: { name: 'Mike' },
//		info: { age: 30 },
//		skills: [ 'JS', 'React', 'Korean', 'English' ]
//	}
```
