# Call

`call` 메소드는 모든 함수에서 사용이 가능하며
`this`를 특정 값으로 지정할 수 있다.

```javascript
const mike = {
  name: 'Mike',
};

function showThisName() {
  console.log(this.name);
}

showThisName.call(mike); // Mike

//showThisName 함수가 mike 객체의 메소드가 아니지만
//call 메소드를 사용하여 this(함수를 부르는 객체 명)를 지정함.
```

**`call`로 `this`를 지정하며 다른 인수를 넣는 모습**

```javascript
const mike = {
  name: 'Mike',
};

function updateInfo(birthYear, occupation) {
  this.birthYear = birthYear;
  this.occupation = occupation;
}

updateInfo.call(mike, 1996, 'student');
// { name: 'Mike', birthYear: 1996, occupation: 'student' }
```
