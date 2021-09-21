# Class

## 객체 생성

ES6에서 추가된 기능이며 생성자 함수처럼 객체를 생성하기 위한 템플릿으로써 작용한다.

우선 객체를 생성하는 기본 문법을 보겠다.

```javascript
const User = function (name, age) {
  this.name = name;
  this.age = age;
  this.showName = function () {
    console.log(this.name);
  };
};

//User.prototype.showName = function () {
//  console.log(this.name);
//}; 아래 생성자 Class처럼 프로토타입에 메소드를 저장시킬 경우

const Mike = new User('Mike', 26);
console.log(Mike);
//User { name: 'Mike', age: 26, showName: [Function (anonymous)] }
Mike.showName();
//Mike
```

이는 기존의 배웠던 방식대로 생성자 함수를 이용하여 객체를 생성한 모습이다.

이 번엔 Class를 이용하여 객체를 생성 해보겠다.

```javascript
class User2 {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  showName() {
    console.log(this.name);
  }
}

const Tom = new User2('Tom', 28);
console.log(Tom);
//User2 { name: 'Tom', age: 28 }
Tom.showName();
//Tom
```

객체 생성시에 `new`를 붙이는 것은 `생성자 함수`와 같은 방식이다.

하지만 `Class 내부`는 `생성자 함수`와 다른 모습이다.

`construct`는 객체를 만들어 주는 생성자 메소드이다.
인수를 받아 객체를 초기화 하고 데이터에 값을 할당을 하는 역할을 하고 객체 내의 `메소드 함수`는 `생성자 함수`처럼 해당 객체 내부에 메소드를 저장하는 것이 아닌 프로토타입 내부에 저장시킨다.

때문에 `Class`를 이용하여 생성된 객체를 출력시켰을 때 메소드가 보이지 않지만 실행은 가능한 이유이다.
