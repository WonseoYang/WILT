# bind

`bind`는 함수의 this 값을 하나의 객체로만 영구히 고정시켜 놓는 메소드이다.

```javascript
const mike = {
  name: 'Mike',
};

function updateInfo(birthYear, occupation) {
  this.birthYear = birthYear;
  this.occupation = occupation;
}

updateInfo.call(mike, 1996, 'Student');
console.log(mike); // { name: 'Mike', birthYear: 1996, occupation: 'Student' }

const boundMike = updateInfo.bind(mike);
boundMike(2002, 'FEDev');
console.log(mike); // { name: 'Mike', birthYear: 2002, occupation: 'FEDev' }
```

해당 모습처럼 `bind`를 이용하여 특정 함수에 고정할 `this` 값을 넣어 반환된 값을 변수 형태에 할당하여 사용할 때에는 함수 형태로 매개변수만 받아서 사용할 수 있다.
