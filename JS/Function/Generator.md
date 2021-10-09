# Generator

Generator는 함수의 실행을 중간에 멈췄따가 재개 할 수 있는 기능이다.

```javascript
function* fn() {
  console.log('1');
  yield 1;
  console.log('2');
  yield 2;
  console.log('3');
  console.log('4');
  yield 3;
  return 'finish';
}

const a = fn();
```

위와 같은 형태로 function 옆에 `*`을 붙여 제너레이터 함수를 선언하고 안에 yield라는 일종의 브레이크를 갖게 된다.

처음 실행 시에는 아무 것도 뜨지 않지만 console에 `a.next();`를 입력하게 되면 다음 브레이크(yield \*;)까지 실행하는 구조이다. 해당 예시에서는 마지막 브레이크를 지나면 `"finish"`를 반환하고 한 번 더 next를 실행하면 undefined 값을 갖게 된다.

제너레이터의 특성으로는
_iterable_

- Symbol.iterator 메서드가 있다.
- Symbol.iterator는 iterator를 반환해야 한다.

_iterator_

- next 메소드를 가진다.
- next 메소드는 value와 done 속성을 가진 객체를 반환한다.
- 작업이 끝나면 done은 true가 된다.

# Generator

Generator는 함수의 실행을 중간에 멈췄따가 재개 할 수 있는 기능이다.

```javascript
function* fn() {
  console.log('1');
  yield 1;
  console.log('2');
  yield 2;
  console.log('3');
  console.log('4');
  yield 3;
  return 'finish';
}

const a = fn();
```

위와 같은 형태로 function 옆에 `*`을 붙여 제너레이터 함수를 선언하고 안에 yield라는 일종의 브레이크를 갖게 된다.

처음 실행 시에는 아무 것도 뜨지 않지만 console에 `a.next();`를 입력하게 되면 다음 브레이크(yield \*;)까지 실행하는 구조이다. 해당 예시에서는 마지막 브레이크를 지나면 `"finish"`를 반환하고 한 번 더 next를 실행하면 undefined 값을 갖게 된다.

제너레이터의 특성으로는
_iterable_

- Symbol.iterator 메서드가 있다.
- Symbol.iterator는 iterator를 반환해야 한다.

_iterator_

- next 메소드를 가진다.
- next 메소드는 value와 done 속성을 가진 객체를 반환한다.
- 작업이 끝나면 done은 true가 된다.

============복습 및 수정 필요==========

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
> 내용 : https://juicyjerry.tistory.com/153
