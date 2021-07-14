# 논리 연산자

자바스크립트엔 세 종류의 논리 연산자 ||(OR), &&(AND), !(NOT)이 있다.

연산자에 '논리’라는 수식어가 붙긴 하지만 논리 연산자는 피연산자로 불린형뿐만 아니라 모든 타입의 값을 받을 수 있다. 연산 결과 역시 모든 타입이 될 수 있다.

### || (OR)

‘OR’ 연산자는 두 개의 수직선 기호로 만들 수 있습.

```javascript
result = a || b;
```

내가 배웠던 자바에서와 동일하게 보통 조건문인 if 조건문에 여러 조건들을 걸어 논리 연산을 진행 하는 방식에서 많이 사용된다.
헌데 OR 연산자에서는 그 조건들 중에 하나라도 true값을 가진다면 조건문을 true로 통과한다.

조건문 안에서의 or 연산자는 좌측부터 우측 순으로 탐색을 하여 true(1)나 false(0) 값을 도출한다.

아래의 예와같이 말이다.

```javascript
alert(true || true); // true
alert(false || true); // true
alert(true || false); // true
alert(false || false); // false
```

```javascript
alert(1 || 0); // 1 (1은 truthy임)

alert(null || 1); // 1 (1은 truthy임)
alert(null || 0 || 1); // 1 (1은 truthy임)

alert(undefined || null || 0); // 0 (모두 falsy이므로, 마지막 값을 반환함)
```

이와 같이 false와 0 말고도 undefined, null도 앞에서 했던 boolean에서 배웠던 것처럼 false와 같은 값으로 처리가 된다.
때문에 마지막 구문에서는 세 개의 조건이 전부 false 처리되어 최종적으로 0(false) 값을 받는다.

또한 alert 문안에 OR 연산자에 변수나 값을 둔다면 탐색을 하다가 참 값에서 멈추며 그 참 값을 출력한다.

```javascript
alert(alert(1) || 2 || alert(3));
//alert(1)에서 1을 출력하고 해당 alert 메소드는 값을 반환하지 않는 메소드이기에 //undefined 값을 반환하는 alert(1) 다음에 있는 피연산자를 평가한다.
//2에서는 참 값을 받기 때문에 2를 출력하고 해당 alert 문은 끝난다.
```

### && (AND)

두 개의 앰퍼샌드를 연달아 쓰면 AND 연산자 &&를 만들 수 있다.

```javscript
result = a && b;
```

전에 나왔던 OR 연산자는 하나라도 참이면 참(true)을 뱉고 참이 하나라도 없다면 거짓(false)을 뱉는 형식이지만
AND 연산자는 모든 피연산자가 참일 때 참(true) 반환합니다. 그 외의 경우는 false를 반환한다.

OR 연산자와 똑같이 좌측에서 우측으로 참 또는 거짓 값을 확인한다.

아래의 예와같이 말이다.

```javascript
alert(true && true); // true
alert(false && true); // false
alert(true && false); // false
alert(false && false); // false
```

아래는 if 조건문 안에 대입을 한 예이다.

```javascript
let hour = 12;
let minute = 30;

if (hour == 12 && minute == 30) {
  alert('현재 시각은 12시 30분입니다.');
}
```

반환 문에서 좌측부터 우측까지의 순서를 확인해볼 수 있는 예로는

```javascript
alert(1 && 2 && 3); // 마지막 값, 3
```

이 처럼 좌측부터 우측 순으로 탐색을 하기에 앞의 참 값(1,2)를 거치고 결국엔 3값을 출력하는 것을 볼 수 있다.

또한 alert 문안에 AND 연산자에 변수나 값을 둔다면 탐색을 하다가 거짓 값에서 멈추며 그 참 값을 출력한다.

```javascript
alert(1 && null && 2);
//1에서 true값을 받고 넘어가고 null에서 false 값을 받아
//전부 참 값을 받지 못하여 null이 출력된다.
```

### ! (NOT)

논리 연산자 NOT은 느낌표 !를 써서 만들 수 있다.

NOT 연산자의 문법은 매우 간단하다.

```javascript
result = !value;
```

NOT 연산자는 인수를 하나만 받고, 다음 순서대로 연산을 수행한다.

피연산자를 불린형(true / false)으로 변환한다.
1에서 변환된 값의 역을 반환한다.

```javascript
alert(!true); // false
alert(!0); // true
```

또한 NOT을 두 개 연달아 사용(!!)하면 값을 불린형과 같이 사용할 수 있다.

```javascript
alert(!!'non-empty string'); // true
alert(!!null); // false
```

# null 병합 연산자 '??'

null 병합 연산자(nullish coalescing operator) ??를 사용하면 짧은 문법으로 여러 피연산자 중 그 값이 ‘확정되어있는’ 변수를 찾을 수 있다.

a ?? b의 평가 결과는 다음과 같다.

a가 null도 아니고 undefined도 아니면 a
그 외의 경우는 b
null 병합 연산자 ??없이 x = a ?? b와 동일한 동작을 하는 코드를 작성하면 다음과 같은데

```javascript
x = a !== null && a !== undefined ? a : b;
```

이러면 코드가 지저분해 보이고 길어진다 이를 해결하기 위해 null 병합 연산자를 아래와 같은 방식으로 사용한다.

```javascript
let firstName = null;
let lastName = null;
let nickName = 'Supercoder';

// null이나 undefined가 아닌 첫 번째 피연산자
alert(firstName ?? lastName ?? nickName ?? 'Anonymous'); // Supercoder
```

이는 사용자의 모든 이름(이름, 성씨, 별명)의 변수에 값이 들어있지 않거나 정의되지 않았을 경우에는 익명의 사용자(Annonymous)로 출력하는 구문이다.

### '??'와 '||'의 차이

앞선 OR 연산자와 매우 흡사해 보이지만 매우 중요한 차이점이 하나 존재한다

OR 연산자는 앞선 파트에서 다뤘듯이 좌측부터 우측으로 탐색하며 첫 번째로 만나는 true 값을 반환하는데
null 병합 연산지인 ?? 연산자는 null이나 undefined와 같은 정의 되지 않은 값을 만났을 때의 값을 반환한다.

이 둘은 null, undefined, 0 을 구분지어야 할 때 이 차이점이 사용된다.
그 예는 아래와 같다.

```javascript
let height = 0;

alert(height || 100); // 100 [ 0||100 == false||100 ]
alert(height ?? 100); // 0   [ 0??100 == false??100 ]
```

</br></br></br>

> ### 출처
>
> 내용 : https://ko.javascript.info/intro
> 썸네일 제작 : https://www.canva.com/
