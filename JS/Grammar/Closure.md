# 클로저 (Closure)

클로저는 함수와 함수가 선언된 어휘적 환경의 조합이다. 클로저를 이해하려면 자바스크립트가 어떻게 변수의 유효범위를 지정하는지(Lexical scoping / 렉시컬 환경)를 먼저 이해해야 한다.

```javascript
//스크립트 시작 준비 단계 (1)
let one; // (2)
one = 1; // (3)
function addOne(num) {
  console.log(one + num);
}

addOne(5); // (4)
```

해당 스크립트를 실행하였을 Lexical 환경의 변화는 아래와 같다.

(1) `one : 초기화X [현재 사용불가]`
`addOne:function` **이 Lexical 환경에 올라간다.**

(2) **본격적으로 위에서부터 아래로 읽어내림**
`one : undefined [사용 가능]`
`addOne : function`

(3) `one : 1`
`addOne : function`

(4) **함수를 실행하며 새로운 Lexical 환경 생성**

**내부 Lexical 환경 (함수를 실행하여 생성된 Lexical 환경)**
함수가 넘겨받은 매개변수와 지역변수들이 저장 되어 있음.
`num :5`
**전역 Lexical 환경 (기존에 존재하던 Lexical 함수)**
전역 스코프의 변수와 함수가 저장되어 있음.
`one : 1`
`addOne : function`

**내부 Lexical 환경은 전역 Lexical 환경을 참조하고 있음.**

**_다만, 내부 Lexical 환경이 참조하는 바로 위 상위 값은 늘 전역 Lexical 환경은 아니고 상위 함수의 Lexical 환경을 참조할 수 있음._**
`예를 들면, addOne()함수 실행 시에 해당 함수 표현식대로 동작을 할 때에 num은 내부 Lexical 환경에 존재하여 바로 찾을 수 있지만 one은 내부 Lexical 환경에 존재하지 않아 참조하는 외부의 전역 Lexical 환경에서 변수를 가져옴`

마무리로 예를 들며 어휘적 환경을 마무리 하도록 하겠다.

```javascript
function makeAdder(x) {
  return function (y) {
    return x + y;
  };
}

const add3 = makeAdder(3);
console.log(add3(2));
```

순차 설명)

1. 전역 Lexical 환경에서 makeAdder()와 add3 상수를 선언 함.
2. const add3에 할당되는 makeAdder(3) 실행
3. 해당 함수는 add3에 makeAdder에서 return 되는 함수를 할당 하며 makeAdder Lexical 환경을 생성하며 안에는 x : 3의 값을 가지고 있음.

```javascript
const add3 = function (y) {
  return 3 + y;
};
```

해당 함수가 add3에 할당되는 구조. 4. console.log()안에서 add3(2)가 실행 되며 add3의 Lexical 환경이 생성되며 y : 2의 값을 가지고 있음.

x + y의 계산을 할 때에 x는 add3의 Lexical 환경에 존재하지 않기에 상위에 참조하는 makeAdder의 Lexical 환경에서 x의 값을에 접근하고 y의 값은 해당 add3의 Lexical 환경에서 참조하여 `3 + 2(y인자)`를 반환하여 콘솔 창에 5가 출력 됨.

**_이 함수는 생성될 당시의 외부 변수(전역 변수, 상위 함수의 Lexical 환경이 가지는 변수)를 기억하여 이후에도 계속 접근이 가능 한 이러한 함수와 Lexical 환경의 조합을 `Closure` 라고 한다._**
