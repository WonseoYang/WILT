# apply

`apply`는 함수 배개변수를 처리하는 방법을 제외하면 `call`과 안전히 같다.

`call`은 일반적인 함수와 마찬가지로 매개변수를 직접 받지만, `apply`는 매개변수를 배열로 받는다.

즉, 함수 실행 시에 `this`를 지정하는 것은 `call`과 같지만 뒤에 붙는 매개변수들을 배열로만 묶어주면 `call`과 똑같이 동작한다.

```javascript
const arr = [1996, 'student'];

function updateInfo(birthYear, occupation) {
  this.birthYear = birthYear;
  this.occupation = occupation;
}

updateInfo.apply(mike, [1996, 'student']);
// updateInfo.apply(mike, arr); =<이와 같이 작성하여도 똑같은 결과가 나온다.
console.log(mike);
// { name: 'Mike', birthYear: 1996, occupation: 'student' }
```
