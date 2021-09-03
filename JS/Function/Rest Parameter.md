# 나머지 매개변수

특정 갯수의 인자(매개변수)를 필요로 하는 함수에 함수 실행문에서의 인수를 인자 갯수보다 적게 보내면 함수는 undefined를 반환하지만 인자보다 인수가 더 많아서 인수가 남는 경우에 남는 변수를 `나머지 매개변수(Rest parameters)`라고 한다.

여러 번 사용되는 함수인데 인수의 개수가 특정 지어지지 않았을 때 사용되며 나머지 매개변수는 인자를 배열 형태로 받는 형식이다

(나머지 매개변수는 배열의 메소드 사용이 가능하다.(length(), reduce(), 등등...)

**ex) 인수로 보내는 모든 수를 더하는 함수.**

```javascript
function addAll(...nums) {
  let result = 0;
  nums.forEach((num) => (result += num));
  return result;
}

console.log(addAll(1, 2, 3)); // 6
console.log(addAll(4, 5, 6)); // 15
```

**ex) 생성자 함수 프로퍼티에 값이 하나가 아닐 때.**

```javascript
function User(name, age, ...skills) {
  this.name = name;
  this.age = age;
  this.skills = skills;
}

let user1 = new User('Mike', 30, 'HTML', 'CSS');
let user2 = new User('Wonseo', 26, 'JS', 'React');
let user3 = new User('Sam', 20, 'Java');

console.log(user1); // User { name: 'Mike', age: 30, skills: [ 'HTML', 'CSS' ] }
console.log(user2); // User { name: 'Wonseo', age: 26, skills: [ 'JS', 'React' ] }
console.log(user3); // User { name: 'Sam', age: 20, skills: [ 'Java' ] }
```

**_나머지 매개변수는 인자에서 항상 마지막에 위치하여야 한다.
(오류 초래) Rest parameter must be last formal parameter]_**

</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
