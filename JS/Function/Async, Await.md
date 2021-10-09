# async / await

await은 async 함수 안에서만 동작하는 키워드이다.

만약, 함수 바깥에서 사용하면 SyntaxError가 발생한다.

Promise 함수를 기다리기 위해 await문은 Promise가 fulfill 되거나 reject 될 때까지 async함수의 실행을 일시 정지하고, Promise가 fulfill 되면 async함수를 일시 정지한 부분부터 실행합니다. 이때 await문의 반환 값은 Promise에서 fulfill 된 값이 됩니다. 만약, reject가 되면, await 문은 reject 된 값을 throw 한다.

```javascript
function resolveAfter2Seconds(x) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(x);
    }, 2000);
  });
}

async function f1() {
  var x = await resolveAfter2Seconds(10);
  console.log(x); // 10
}

f1();
```

위의 예시의 f1 함수 안에 변수 x가 await이 사용되었다.

해당 함수가 실행되면서 변수 x가 있는 줄에서 실행이 잠시 중단되었다가 Promise가 이행(resolved) 될 때까지 기다렸다가 실행이 된다. 이때 변수 x에 값이 할당되게 되어 2초 뒤에 콘솔에 10이 찍히게 된다.

즉 await의 기능은 프라미스가 처리되길 기다리는 동안엔 엔진이 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을 할 수 있기 때문에 CPU 리소스가 낭비되지 않는다.

await는 promise.then보다 좀 더 세련되게 프라미스의 result 값을 얻을 수 있도록 해주는 문법이다. promise.then보다 가독성 좋고 쓰기도 쉽다.
</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
