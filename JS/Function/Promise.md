# Promise

```javascript
const pr = new Promise((resolve, reject) => {
  //resolve = 성공했을 때의 실행하는 함수
  //reject = 실패했을 때의 실행하는 함수
  //code . . .
});
```

위의 어떤 일이 완료(성공 or 실패) 됐을 때의 실행되는 함수를 `callback 함수`라고 한다.

`Promise 함수`는 `state`와 `result`라는 프로퍼티를 기본으로 갖는다.
이는 처음에 함수가 생성될 때는 각각 state는 pending 즉 대기하는 값을 가지고 있고 result는 정의되지 않은 undefined 값을 가지고 있는다.

성공 즉 resolve가 호출되면 이 프로미스 함수의 state는 fulfilled 이행됐다는 값으로 바뀌고 result는 value 값을 가진다.

반대로 실패 즉 reject가 호출되면 프로미스 함수의 state는 rejected 거부됐다는 값으로 바뀌고 result는 error 값을 가진다.

아래와 같은 예시로

```javascript
const pr = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('OK');
  }, 3000);
});

pr.then(
  function (result) {
    console.log(result + '!, 가지러 가자');
  },
  function (err) {
    console.log('다시 주문 해주세요.');
  },
);
```

3초 뒤에 성공 호출하는 프로미스 함수를 적용하면 3초 뒤에 `OK!, 가지러 가자!`라는 문구가 출력된다.

여기서 then의 역할은 성공 실패 차례대로 첫번째는 성공 시에 실행되는 함수가 입력되는 곳이고 두번째는 실패 시에 실행되는 함수를 입력 해주면 된다.

then 대신에 사용될 수 있는 것으로는 catch와 finally가 있는데 위 예시의 then을 같은 형식으로 하여 먼저 catch는

```javascript
pr.then(function (result) {
  //성공 시에
  console.log(result + '!, 가지러 가자');
}).catch(function (err) {
  //실패 시에
  console.log('다시 주문 해주세요.');
});
```

로 표현하여 명확하게 구분하여 가독성이 좋고 에러를 잡기에도 용이하여 사용이 권장된다.
여기에 finally까지 사용하면

```javascript
pr.then(function (result) {
  //성공 시에
  console.log(result + '!, 가지러 가자');
})
  .catch(function (err) {
    //실패 시에
    console.log('다시 주문 해주세요.');
  })
  .finally(function () {
    //항시 실행
    console.log('=== 주문 끝 ===');
  });
```

형태가 되는데 finally의 역할은 성공이든 실패든 이행 시에 꼭 실행되어야 하는 함수를 실행 시키는 역할이다.

해당 프로미스 함수 관련해서는 아직 나에게는 복잡한 개념이라 복습을 하며 어떠한 곳에 어떻게 적용 시킬지 고민을 많이 해봐야 하는 사항인 것 같다.
</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
