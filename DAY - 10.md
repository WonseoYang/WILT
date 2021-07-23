브라우저의 자바스크립트 엔진 자체에 내장된 객체를 말한다.
별도의 패키지 설치가 필요 없이 사용이 가능하다.

종류는 무수히 많으며
오늘은 그 중에 일부분 내장객체와 그 안에 메소드들을 배워보려 한다.

## Object 객체

### Object.assign()

`Object 객체`의 `assign 메소드`는 객체를 복제할 때 사용된다.

먼저 복제의 잘못된 예를 먼저 보겠다.

```javascript
const user1 = {
  name: 'Mike',
  age: 26,
};

const user2 = user1;
```

일반적으로 변수를 할당하는 형태로 복제를 하려고 하였지만
위의 잘못된 예시는 복제가 아닌 `user1`이 참조하는 객체의 주소 값을 **같이 사용**하는 것이다.

아래가 객체 복사의 올바른 예이다.

```javascript
const user1 = {
  name: 'Mike',
  age: 26,
};

const user2 = Object.assign({}, user1);
//user2에 객체를 {}로 초기화하고 user1이 참조하고 있는 객체 값을 덮어 씌운다.
```

### Object.keys()

`Object 객체`의 `keys 메소드`는 객체의 키(프로퍼티명)를 반환할 때 사용된다.

```javascript
const user = {
  name: 'Mike',
  age: 26,
};

console.log(Object.keys(user)); //["name", "age"]
//배열 형태로 키가 반환 된다.
```

### Object.values()

`Object 객체`의 `values 메소드`는 `keys 메소드`와 비슷하다.
객체의 키 값을 반환할 때 사용된다.

```javascript
const user = {
  name: 'Mike',
  age: 26,
};

console.log(Object.values(user)); //["Mike", 26]
//배열 형태로 키 값들이 반환 된다.
```

### Object.entries()

`Object 객체`의 `entries 메소드`는 `values 메소드`와 `keys 메소드`를 합친 것과 같다.
객체의 키와 키 값을 같이 반환할 때 사용된다.

```javascript
const user = {
  name: 'Mike',
  age: 26,
};

console.log(Object.entries(user));
//["name", "Mike"],
//["age", 26]
//2차원 배열 형태로 키와 키 값들이 반환 된다.
```

### Object.fromEntries()

`Object 객체`의 `fromEntries 메소드`는 `entries`의 반대로 키와 키 값 배열들을 객체 형태로 변환하여 반환하는 메소드이다.

```javascript
const user = [
  ['name', 'Mike'],
  ['age', 26],
];

Object.fromEntries(user);

console.log(user);
//{
//name : "Mike",
//age : 26,
//}
```
