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

## 상속

`extends`를 이용하여 다른 `객체 생성 Class`를 상속할 수 있다.

```javascript
class Car {
  construct(color) {
    this.color = color;
    this.wheels = 4;
  }
  drive() {
    console.log('drive..');
  }

  stop() {
    console.log('STOP !!');
  }
}

class Bmw extends Car {
  park() {
    console.log('PARK ~');
  }
  stop() {
    console.log('멈춥니다.');
  }
}

const z4 = new Bmw('black');

z4.drive(); //drive..
z4.stop(); //멈춥니다.
//stop은 Bmw Class에서 자식 Class인 Car의 stop(); 메소드를 덮어 씌웠기 때문에 'STOP !!'이 아닌 '멈춥니다.'가 출력된다.
z4.park(); //PARK ~
```

## 오버라이딩

### 메소드 오버라이딩

```javascript
class Car {
  construct(color) {
    this.color = color;
    this.wheels = 4;
  }
  drive() {
    console.log('drive..');
  }

  park() {
    console.log('PARK ~');
  }
}

class Bmw extends Car {
  stop() {
    console.log('멈춥니다.');
  }
  park() {
    super.park();
    console.log('띠리리리 띠리리리리');
  }
}

const z4 = new Bmw('black');

z4.drive(); //drive..
z4.stop(); //멈춥니다.
z4.park(); //PARK ~
//띠리리리 띠리리리리
//park는 super.park();를 이용하여 자식 클래스인 Car Class의 park(); 메소드를 사용하고 그 다음 console.log로 워딩을 출력한다.
```

### 생성자 오버라이딩

`부모 Class`에서 생성된 값을 가져오려면 `부모 생성자`를 호출해야 한다.

잘못된 예를 먼저 보겠다.

```javascript
class Car {
  constructor(color) {
    this.color = color;
    this.wheels = 4;
  }
  drive() {
    console.log('drive..');
  }

  stop() {
    console.log('STOP !!');
  }
  park() {
    console.log('PARK ~');
  }
}

class Bmw extends Car {
  constructor() {
    this.navigation = 1;
  }
}

const z4 = new Bmw('black');

console.log(z4);
//Error
```

이렇게 정상적으로 자식 `Class`에서 생성된 값을 못 가져오는 모습을 볼 수 있다.

이유는 `extends`를 이용하여 만든 `Class`는 자식 객체가 있다는 이유로 `빈 객체`를 생성하고 초기화 하는 단계를 건너뛰기 때문과 `부모Class`에서 `자식Class`로 인자가 전달되지 않기 때문이다.
아래와 같이 해결하도록 하자.

```javascript
class Car {
  constructor(color) {
    this.color = color;
    this.wheels = 4;
  }
  drive() {
    console.log('drive..');
  }

  stop() {
    console.log('STOP !!');
  }
  park() {
    console.log('PARK ~');
  }
}

class Bmw extends Car {
  constructor(color) {
    //인자를 받아서
    super(color); // 자식 Class에 인자를 전달하여 정상적으로 자식 Class에서 값을 생성할 수 있도록 함.
    this.navigation = 1;
  }
}

const z4 = new Bmw('black');

console.log(z4);
//Bmw { color: 'black', wheels: 4, navigation: 1 }
```

정상적으로 자식 Class에서 생성된 값을 가져올 수 있다.
