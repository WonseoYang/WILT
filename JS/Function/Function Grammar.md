# 함수

프로그래밍을 하다보면 일정 동작을 요구하는 코드를 필요하는 곳이 많이 보일 때가 있다.
특정 값을 받아 특정한 동작 후에 특정한 결과(값)를 도출해내는 경우 말이다.
예를 들면 로그인, 회원가입 등등과 같은 것 들이 대표적인 예이다.

이러한 상황들에서 쓰이는 것이 함수이다.
함수는 프로그램을 구성하는 주요 `구성 요소(building block)`이다.
함수를 이용하면 같은 동작을 계속 작성할 필요 없이 함수를 작성하고 호출하여 동작 할 수 있다.

### 함수 선언

`함수 선언(function declaration)`을 이용하여 함수를 선언한다.

형식은 아래와 같다.

```javascript
function name(parameters){	//name에 해당 함수의 이름이, parameters에는 인자로 받는 변수를 포함한다.
...함수 본문...//해당 함수에서 동작 할 내용을 입력한다.
}
```

간단한 예시로는

```javascript
function showMessage() {
  alert('안녕하세요!');
}

showMessage();
showMessage();
```

이러한 모습의 예시가 있는데 해당 예시에서는 showMessage()함수에 '안녕하세요' 알림 창을 띄우는 동작이 담겨있다.
아래에는 해당 함수를 두 번 호출 하였기에 '안녕하세요' 알림 창이 두 번 뜨는 결과를 볼 수 있다.

### 지역 변수

함수 내에서 선언한 변수인 `지역 변수(local variable)`는 함수 안에서만 접근할 수 있다.

```javascript
function showMessage() {
  let message = '안녕하세요!'; // 지역 변수

  alert(message);
}

showMessage(); // 안녕하세요!

alert(message); // ReferenceError: message is not defined
//(message는 함수 내 지역 변수이기 때문에 에러가 발생합니다.)
```

### 외부 변수

함수 내부에서 함수 외부의 변수인 `외부 변수(outer variable)`에 접근할 수 있다.

```javascript
let userName = 'John';

function showMessage() {
  let message = 'Hello, ' + userName; // 지역변수(Hello, ) + 외부변수(John)
  alert(message);
}

showMessage(); // Hello, John 출력
```

함수에선 외부 변수에 접근하여 불러오는 것뿐만이 아닌 수정도 가능하다.

```javascript
let userName = 'John';

function showMessage() {
  userName = 'Bob'; // (1) 외부 변수를 수정함

  let message = 'Hello, ' + userName;
  alert(message);
}

alert(userName); // 함수 호출 전이므로 John 이 출력 됨

showMessage();

alert(userName); // 함수에 의해 Bob 으로 값이 바뀌고 출력 됨
```

### 전역 변수

```javascript
let userName = 'John';

function showMessage() {
  let userName = 'Bob'; // 같은 이름을 가진 지역 변수를 선언합니다.

  let message = 'Hello, ' + userName; // Bob
  alert(message);
}

// 함수는 내부 변수인 userName만 사용합니다,
showMessage(); //때문에 Hello, Bob 이 출력됩니다.

alert(userName); // 함수는 외부 변수에 접근하지 않습니다. 따라서 값이 변경되지 않고, John이 출력됩니다.
```

외부 변수는 지역 변수가 없는 경우에만 사용할 수 있다.

함수 내부에 외부 변수와 동일한 이름을 가진 변수가 선언되었다면, 내부 변수는 외부 변수를 가린다. 위 예시에서 함수 내부에 외부 변수와 동일한 이름을 가진 지역 변수 userName가 선언되어 있다. 외부 변수는 내부 변수에 가려져 값이 수정되지 않았다.

또한 위 예시의 userName처럼, 함수 외부에 선언된 변수는 **_`전역 변수(global variable)`_** 라고 부른다.
전역 변수는 같은 이름을 가진 지역 변수에 의해 가려지지만 않는다면 모든 함수에서 접근할 수 있다.

변수는 연관되는 함수 내에 선언하고, 전역 변수는 되도록 사용하지 않는 것이 좋다. 비교적 근래에 작성된 코드들은 대부분 전역변수를 사용하지 않거나 최소한으로만 사용한다.
다만 프로젝트 전반에서 사용되는 데이터는 전역 변수에 저장하는 것이 유용한 경우도 있으니 이 점을 기억하자.

### 매개변수

매개변수(parameter)를 이용하면 임의의 데이터를 함수 안에 전달할 수 있다.

아래 예시에서는 함수`showMessage()`는 매개변수로 `from`과 `text`를 가진다.

```javascript
function showMessage(from, text) {
  // 매개변수 from, text를 가진다.
  alert(from + ': ' + text); //from, text를 받아 해당 형식으로 알림 창을 띄운다.
}

showMessage('Ann', 'Hello!'); // Ann: Hello! (*)
showMessage('Ann', "What's up?"); // Ann: What's up? (**)
```

좀 더 심화된 예시 ⇩

```javascript
function showMessage(from, text) {
  //showMessage() 함수에서 매개변수로 from, text를 가진다.

  from = '*' + from + '*'; // 매개변수로 받은 from에 문자로 살을 더 붙인다.

  alert(from + ': ' + text); //살을 더 붙인 from과 text를 정해진 형식대로 알림 창으로 출력.
}

let from = 'Ann'; //from 변수에 "Ann" 저장

showMessage(from, 'Hello'); // *Ann*: Hello

alert(from); // 외부변수이기에 변경되지 않은 from 값인  "Ann"을 출력한다.
```

### 기본값

매개변수에 값을 전달하지 않으면 그 값은 `undefined`가 된다.

예시를 통해 알아보자. 위에서 정의한 `showMessage(from, text)`는 매개변수가 2개지만 아래와 같이 인수를 하나만 넣어서 호출할 수도 있다.

```javascript
showMessage('Ann');
```

이렇게 코드를 작성하여도 오류가 발생하지는 않는다. 두 번째 매개변수에 값을 전달하지 않았기에 `text`엔 `undefined`가 할당될 뿐이다. 따라서 실행되지 않은 에러 대신에 `"Ann: undefined"`가 출력된다.

매개변수에 값이 전달되지 않아도 그 값이 `undefined`가 되지 않도록 하려면 `기본값(default value)`을 설정해주면 된다. 매개변수 오른쪽에 `=`을 붙이고 `undefined` 대신 설정하고 하는 기본값을 써주면 된다.

```javascript
function showMessage(from, text = 'no text given') {
  alert(from + ': ' + text);
}

showMessage('Ann'); //Ann: no text given
```

이렇게 하면 text값을 받지 못해도 `undefined` 대신에 기본값인 "no text given"이 할당됩니다.
또한 아래와 같이 기본 값으로 함수를 불러올 수도 있다.

```javascript
function showMessage(from, text = anotherFunction()) {
  // anotherFunction()은 text값이 없을 때만 호출됨
  // anotherFunction()의 반환 값이 text의 값이 됨
}
```

자바스크립트에선 함수를 호출할 때마다 매개변수 기본값을 평가한다. 물론 해당하는 매개변수가 없을 때만 기본값을 평가하는 것이다.

위 예시에선 `showMessage()`를 호출할 때 매개변수 `text`에 값이 없는 경우 `anotherFunction()`이 호출됩니다.

##### 매개변수 기본값을 설정할 수 있는 또 다른 방법

가끔은 함수 선언부에서 매개변수 기본값을 설정하는 것 대신 함수가 실행되는 도중에 기본값을 설정하는 게 논리에 맞는 경우가 생기기도 한다.

이런 경우엔 일단 매개변수를 undefined와 비교하여 함수 호출 시 매개변수가 생략되었는지를 확인한다.

```javascript
function showMessage(text) {
  if (text === undefined) {
    text = '빈 문자열';
  }

  alert(text);
}

showMessage(); // 빈 문자열
```

이렇게 `if`문을 쓰는 것 대신 논리 연산자 `||`를 사용할 수도 있다.

```javascript
// 매개변수가 생략되었거나 빈 문자열("")이 넘어오면 변수에 '빈 문자열'이 할당됩니다.
function showMessage(text) {
  text = text || '빈 문자열';
  ...
}
```

이 외에도 모던 자바스크립트 엔진이 지원하는 `null 병합 연산자(nullish coalescing operator) ??`를 사용하면 `0`처럼 `falsy`로 평가되는 값들을 일반 값처럼 처리할 수 있어서 좋다.

```javascript
// 매개변수 'count'가 넘어오지 않으면 'unknown'을 출력해주는 함수
function showCount(count) {
  alert(count ?? 'unknown');
}

showCount(0); // 0 - 카운트가 넘어왔지만 0으로 넘어왔을 때
showCount(null); // unknown - 카운트가 null로 넘어왔을 때
showCount(); // unknown - 카운트가 아무 값도 넘어오지 않았을 때
```

### 반환값

`함수`를 호출하였을 때 호출한 그 곳에 특정 값을 반환하게 할 수 있다.
이때 이 특정 값을 `반환 값(return value)`라고 한다.

```javascript
function sum(a, b) {
  //sum 함수는 a, b를 매개변수로 받아서
  return a + b; //더한 값을 반환한다.
}
let result = sum(1, 2); //변수 result는 sum함수로 인해 1과 2가 더해진 값인
alert(result); // 3 이 출력된다.
```

지시자 `return`은 함수 내 어디서든 사용이 가능하다. 실행 흐름이 지시자 `return`을 만나면 함수 실행은 즉시 중단되고 함수를 호출한 곳에 값을 반환하는 구조이다. 위에 있는 예시에서는 반환 값을 `result`에 할당하였다.

아래 예시는 함수 하나에 여러 개의 `return`을 적용한 모습이다.

```javascript
function checkAge(age) {
  if (age >= 18) {
    return true;
  } else {
    return confirm('보호자의 동의를 받으셨나요?');
  }
}

let age = prompt('나이를 알려주세요', 18);

if (checkAge(age)) {
  //checkAge()함수에서 18세 이상이거나 18세 이상이 아니더라도
  //confirm창에서 확인을 누른다면 true 값을 받아 접속 허용 창을 띄운다.
  alert('접속 허용');
} else {
  //18세 이상이 아니지만 confirm 창에서 아니오를 누른다면 false값을 받아 접속 차단 창을 띄운다.
  alert('접속 차단');
}
```

아래 예시와 같이 지시자 `return`만 명시하는 것도 가능하다. 이런 경우는 함수를 즉시 종료하는 경우이다.

```javascript
function showMovie(age) {
  if (!checkAge(age)) {
    //false를 반환하면 아래 알림 창을 띄우지 않고 함수를 종료한다.
    return;
  }

  alert('영화 상영'); // (*)
  // ...
}
```

---

**_ - 아래는 함수에서 `return` 사용시 주의해야할 점이다. - _**

##### return 문이 없거나 return 지시자만 있는 함수는 undefined를 반환한다.

`return`문이 없는 함수도 무언가를 반환한다. `undefined`를 반환한다.

```javascript
function doNothing() {
  /* empty */
}

alert(doNothing() === undefined); // true
```

`return` 지시자만 있는 경우도 `undefined`를 반환한다. `return`은 `return undefined`와 동일하게 동작한다.

```javascript
function doNothing() {
  return;
}

alert(doNothing() === undefined); // true
```

##### return 값 사이에 절대 줄을 삽입하지 않는다.

반환하려는 값이 긴 표현식인 경우, 아래와 같이 지시자 `return`과 반환하려는 값 사이에 새 줄을 넣어 코드를 작성하고 싶을 수도 있다.

```javascript
return;
some + long + expression + or + whatever * f(a) + f(b);
```

자바스크립트는 `return`문 끝에 세미콜론을 자동으로 넣기 때문에 이렇게 `return`문을 작성하면 안된다. 위 코드는 아래 코드처럼 동작한다.

```javascript
return;
some + long + expression + or + whatever * f(a) + f(b);
```

따라서 반환하고자 했던 표현식을 반환하지 못하고 아무것도 반환하지 않는 것처럼 되어버린다.

표현식을 여러 줄에 걸쳐 작성하고 싶다면 표현식이 `return` 지시자가 있는 줄에서 시작하도록 작성해야 한다. 또는 아래와 같이 여는 괄호를 `return` 지시자와 같은 줄에 써줘도 괜찮다.

```javascript
return some + long + expression + or + whatever * f(a) + f(b);
```

이렇게 하면 의도한 대로 표현식을 반환할 수 있다.

---

### 함수 이름짓기

함수는 어떤 동작을 수행하기 위한 코드를 모아놓은 것이다. 따라서 함수의 이름은 대개 동사인데 함수 이름은 가능한 한 간결하고 명확해야 한다. 함수가 어떤 동작을 하는지 설명할 수 있어야 하고 코드를 읽는 사람은 함수 이름만 보고도 함수가 어떤 기능을 하는지 힌트를 얻을 수 있어야 한다.

함수가 어떤 동작을 하는지 축약해서 설명해주는 동사를 접두어로 붙여 함수 이름을 만드는 게 관습이라고 한다. 다만 팀프로젝트 시에는 팀 내에서 그 뜻이 반드시 합의된 접두어만 사용해야 힌다.

"show"로 시작하는 함수는 대개 무언가를 보여주는 함수이다.
그 외에는 아래와 같은 접두어를 사용하는게 일반적이다.

- "get…" – 값을 반환함
- "calc…" – 무언가를 계산함
- "create…" – 무언가를 생성함
- "check…" – 무언가를 확인하고 불린값을 반환함
- 등등...

##### 함수는 동작 하나만 담당해야 한다.

함수는 함수 이름에 언급되어있는 동작을 정확히 수행해야 한다.
그 이외의 동작은 수행해선 안 된다.

독립적인 두 개의 동작은 독립된 함수 두 개에서 나눠서 수행할 수 있게 해야 한다. 한 장소에서 두 동작을 동시에 필요로 하는 경우라도 말이다.
(이 경우는 제3의 함수를 만들어 그곳에서 두 함수를 호출합니다).

개발자들이 빈번히 하는 실수로는

- `getAge()` 함수는 나이를 얻어오는 동작만 수행해야 합니다. `alert` 창에 나이를 출력해주는 동작은 이 함수에 들어가지 않는 것이 좋습니다.
- `createForm()` 함수는 form을 만들고 이를 반환하는 동작만 해야 합니다. `form`을 문서에 추가하는 동작이 해당 함수에 들어가 있으면 좋지 않습니다.
- `checkPermission()` 함수는 승인 여부를 확인하고 그 결과를 반환하는 동작만 해야 합니다. 승인 여부를 보여주는 메시지를 띄우는 동작이 들어가 있으면 좋지 않습니다.

위 예시들은 접두어의 의미가 합의되었다고 가정하고 만들어진 예시이다. 본인이나 본인이 속한 팀에서 접두어의 의미를 재합의하여 함수를 만들 수도 있긴 하지만, 아마도 위 예시에서 사용한 접두어 의미와 크게 차이가 나진 않을 것이다. 어찌 되었든 접두어를 사용하여 함수 이름을 지을 땐, 해당 접두어에 어떤 의미가 있는지 잘 이해하고 있어야 한다. 해당 접두어가 붙은 함수가 어떤 동작을 하는지, 어떤 동작은 하지 못하는지 알고 있어야 한다. 접두어를 붙여 만든 모두 함수는 팀에서 만든 규칙을 반드시 따라야 한다. 팀원들은 이 규칙을 충분히 이해하고 있어야 하며 팀원들 사이에 이 규칙이 잘 공유되어야 한다.

### 함수 == 주석

함수는 간결하고 한 가지 기능만 수행할 수 있게 만들어야 한다. 함수가 길어지면 함수를 잘게 쪼갤 때가 되었다는 신호로 받아들이셔야 합니다. 함수를 쪼개는 건 쉬운 작업은 아니다. 하지만 함수를 분리해 작성하면 많은 장점이 있기 때문에 함수가 길어질 경우엔 함수를 분리해 작성할 것을 권유합니다.

이것이 내가 나중에 코딩테스트를 준비하며 해야할 함수형 프로그래밍인 것 같다.

함수를 간결하게 만들면 테스트와 디버깅이 쉬워진다. 그리고 함수 그 자체로 주석의 역할까지 한다.

같은 동작을 하는 함수, `showPrimes(n)`를 두 개 만들어 비교해 봅시다. `showPrimes(n)`은 n까지의 소수(prime numbers)를 출력해줍니다.

첫 번째 `showPrimes(n)`에선 레이블을 사용해 반복문이 작성된 코드를 보자.

```javascript
function showPrimes(n) {
  nextPrime: for (let i = 2; i < n; i++) {
    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }

    alert(i); // 소수
  }
}
```

두 번째 `showPrimes(n)`는 소수인지 아닌지 여부를 검증하는 코드를 따로 분리해 isPrime(n)이라는 함수에 넣어서 작성된 코드를 보자.

```javascript
function showPrimes(n) {
  for (let i = 2; i < n; i++) {
    if (!isPrime(i)) continue;

    alert(i); // a prime
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if (n % i == 0) return false;
  }
  return true;
}
```

두 번째 showPrimes(n)가 더 이해하기 쉬운 것을 볼 수 있다. isPrime 함수 이름을 보고 해당 함수가 소수 여부를 검증하는 동작을 한다는 걸 쉽게 알 수 있다. 이렇게 이름만 보고도 어떤 동작을 하는지 알 수 있는 코드를 자기 설명적(self-describing) 코드라고 부른다.

위와 같이 함수는 중복을 없애려는 용도 외에도 사용할 수 있다. 이렇게 함수를 활용하면 코드가 정돈되고 가독성이 높아진다.

</br></br></br>

> ### 출처
>
> 내용 : https://ko.javascript.info/intro
