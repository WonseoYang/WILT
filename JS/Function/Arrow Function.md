# 화살표 함수 기본

함수 선언문 그리고 함수 표현식보다 더 간결한 문법으로 함수를 생성하는 방법이 있는데 바로 그것이 화살표 함수이다.

`화살표 함수(arrow function)` 이름은 문법의 생김새에서 비롯됐다.

```javascript
let func = (arg1, arg2, ...argN) => expression;
```

이러한 형태로 arg1부터 argN까지의 인자를 받아 expression에 기술된 동작을 수행하여 반환하는 func이라는 함수이다.

화살표 함수는 표현식에서 더 축약된 형태인데 위 화살표 함수를 표현식으로 바꾸게 된다면

```javascript
let func = function (arg1, arg2, ...argN) {
  return expression;
};
```

이러하다 간단한 예로는

```javascript
let double = (n) => n * 2;
//let double = function(n) { return n*2}와 거의 동일하다.

alert(douvle(3)); //6이 출력된다.
```

인수가 없다면 괄호를 비우면 된다.

```javascript
let sayHi = () => alert('안녕하세요');

sayHi(); //'안녕하세요' 출력
```

함수 표현식에서 썼던 것처럼 값처럼 사용할 수 있다.

```javascript
let age = prompt('나이를 알려주세요', 18);

let welcome = age < 18 ? () => alert('안녕') : () => alert('안녕하세요');
```

처음에는 가독성이 떨어져 보일 수 있지만 익숙해지면 간결한 함수들을 표현하는 데에 있어서 용이할 것 같다.

### 본문이 여러 줄인 화살표 함수

이처럼 위에서 했던 화살표 함수는 `=>`를 기준으로 좌측에 있는 인수를 이용하여 우측에 있는 표현식을 평가하는 함수다.

하지만 평가해야 할 표현식이나 구문이 여러 개인 함수일 수도 있다. 이 경우에도 역시 화살표 함수를 사용해 함수를 만들 수 있지만 중괄호 안에 평가해야 할 코드를 작성해야 한다. 그리고 `return`을 이용해 명시적으로 결과 값을 반환 해주어야 한다.

```javascript
let sum = (a, b) => {
  let result = a + b;
  return result;
};

alert(sum(1, 2)); //3
```

</br></br></br>

> ### 출처
>
> 내용 : https://ko.javascript.info/intro
