# 상속, prototype

```javascript
const bmw = {
  color: 'red',
  wheels: 4,
  navigation: 1,
  drive() {
    console.log('drive...');
  },
};

const benz = {
  color: 'black',
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};
```

이렇게 차를 객체형태로 정리를 하였을 때 현재는 2개의 객체가 동일한 바퀴 속성 값 4, drive라는 메소드를 가지고 있다.

이를 프로토타입을 통해 공통된 값을 객체로 따로 생성하여 상속시킬 수 있다.

```javascript
const car = {
  //공통된 값을 담은 객체
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};

const bmw = {
  color: 'red',
  navigation: 1,
};

const benz = {
  color: 'black',
};
bmw.__proto__ = car; // 프로토타입으로 상속을 한다.
benz.__proto__ = car; // 프로토타입으로 상속을 한다.

// 상속 받아도 객체 내부 값에 추가,변경,삭제는 없다.
console.log(bmw); // { color: 'red', navigation: 1 }
console.log(benz); // { color: 'black' }

//다만 사용 시에 값을 끌어와 사용이 가능하다.
console.log(bmw.wheels); // 4
benz.drive(); // drive...
```

또한, 상속 받았더라도 다시 상속을 줄 수도 있으며 그 내부의 프로토 값까지 같이 상속된다.

```javascript
const car = {
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};

const bmw = {
  color: 'red',
  navigation: 1,
};

const kickBoard = {
  color: 'black',
};

bmw.__proto__ = car; //bmw가 car를 상속받고
kickBoard.__proto__ = bmw; //kickBoard가 car를 상속받은 bmw를 상속 받는다.

console.log(kickBoard); //{ color: 'black' }

kickBoard.drive(); // drive...
```

kickBoard가 상속받은 bmw의 color 속성의 "red"가 아닌 "black"으로 나온 이유는 속성을 사용 시에 현 객체의 속성을 먼저 확인하고 없을 시에 prototype을 확인하기 때문에 상속을 더 나중에 받을수록 혹은 본인이 그 값을 가지고 있는 것이 더 우선순위를 갖게 된다.

또한 객체 자체의 값만을 찍으면 보이지 않지만 for in문을 사용하여 속성을 찍어내면 상속받은 객체들의 속성들도 가지고 있다.

```javascript
const car = {
  //공통된 값을 담은 객체
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};

const bmw = {
  color: 'red',
  navigation: 1,
};

const kickBoard = {
  color: 'black',
};

bmw.__proto__ = car; //bmw가 car를 상속받고
kickBoard.__proto__ = bmw; //kickBoard가 car를 상속받은 bmw를 상속 받는다.

for (key in kickBoard) {
  console.log(key);
}
//color
//navigation
//wheels
//drive

//현 객체 자체의 값과 상속받은 값을 구분 지을 시에는 hasOwnProperty 메소드를 이용하면 된다.
for (key in kickBoard) {
  if (kickBoard.hasOwnProperty(key)) {
    console.log('O ' + key);
  } else {
    console.log('X ' + key);
  }
}
// O color
// X navigation
// X wheels
// X drive
```

하지만 Object 메소드를 이용한 결과들은 상속받은 값을 사용할 수 없다.

```javascript
const car = {
  //공통된 값을 담은 객체
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};

const bmw = {
  color: 'red',
  navigation: 1,
};

const kickBoard = {
  color: 'black',
};

bmw.__proto__ = car;
kickBoard.__proto__ = bmw;

console.log(Object.keys(kickBoard)); // [ 'color' ]
console.log(Object.values(kickBoard)); // [ 'black' ]
```

생성자 함수를 이용하여 각자의 속성에 값을 부여받고 프로토타입으로 기본 값 혹은 공통된 값을 부여하여 찍어내는 모습도 보겠다.

우선 굉장히 비효율적인 모습부터 보겠다.

```javascript
const car = {
  //공통된 값을 담은 객체
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};

const Bmw = function (color) {
  this.color = color;
};

const x5 = new Bmw('Red');
const z4 = new Bmw('Blue');

x5.__proto__ = car;
z4.__proto__ = car;

//프로토타입으로 상속받은 값
console.log(x5.wheels); //4
console.log(z4.wheels); //4
//생성자 함수로 객체 생성 시에 부여받은 속성과 값
console.log(x5.color); //Red
console.log(z4.color); //Blue
```

간편하려고 쓰는 생성자 함수로 객체를 생성한 후에 일일히 프로토타입 속성에 값을 넣어주는 것은 굉장히 비효율적이다.

이러한 문제를 해결하기 위해 생성자 함수에 프로토타입 속성 값을 미리 상속시켜주는 것이다.

```javascript
const Bmw = function (color) {
  this.color = color;
};

Bmw.prototype.wheels = 4;
Bmw.prototype.drive = function () {
  console.log('drive...');
};

const x5 = new Bmw('Red');
const z4 = new Bmw('Blue');

//프로토타입으로 상속받은 값
console.log(x5.wheels); //4
console.log(z4.wheels); //4
//생성자 함수로 객체 생성 시에 부여받은 속성과 값
console.log(x5.color); //Red
console.log(z4.color); //Blue
```

생성자 함수로 만드는 객체에 프로토타입 타입 값을 생성자 함수로 넣어놓는 방법이다.

해당 생성자 함수, 선언, 상속 등의 이유로 객체 내에 속성과 값들은 생성된 위치를 찾기 힘들다.

이를 구분하기 위해 instanceof나 constructor를 사용하여 어느 객체, 생성자 함수에서 생성된 것인지 확인할 수 있다.

```javascript
const Bmw = function (color) {
  this.color = color;
};

Bmw.prototype.wheels = 4;
Bmw.prototype.drive = function () {
  console.log('drive...');
};

const x5 = new Bmw('Red');
const z4 = new Bmw('Blue');

console.log(z4); //Bmw { color: 'Blue' }
console.log(z4 instanceof Bmw); //true
console.log(z4.constructor); //[Function: Bmw]
console.log(x5.constructor); //[Function: Bmw]
```

또한 생성자 함수에 프로토타입 속성과 값을 정해주는 구문을 객체 생성 구문처럼 줄일 수 있다.

```javascript
const Bmw = function (color) {
  this.color = color;
};

Bmw.prototype = {
  //Bmw 생성자 함수에 프로토타입 속성과 값을 지정하는 모습
  contructor: Bmw,
  wheels: 4,
  drive() {
    console.log('drive...');
  },
};

const x5 = new Bmw('Red');
const z4 = new Bmw('Blue');
```

다만 원래는 저렇게 작성하면 해당 생성자 함수로 생성된 객체는 constructor를 가지지 못한다.

때문에 Bmw의 프로토타입 값을 지정하는 곳에 constructor까지 같이 지정하는 것이 생성자 함수를 통해 프로토타입 값을 가지며 constructor까지 갖는 객체를 생성하는 구문을 가독성 좋게 작성한 것이다.

한 줄씩 프로토타입 속성과 값을 넣어주는 것이 나쁜 방법은 아니다.

### closure를 이용한 생성자 함수

```javascript
const Bmw = function (color) {
  const c = color;
  this.getColor = function () {
    console.log(c);
  };
};

const x5 = new Bmw('red');
x5.getColor(); //red
x5.color = 'Black'; // 값 변경
console.log(x5.color); //Black
x5.getColor(); //red
```

생성된 객체는 값이 자유롭게 변경되고 삭제되고 추가될 수 있지만 초기의 값을 기억하는 함수를 지정해두면 해당 함수 내의 값은 변경될 수 없다.
