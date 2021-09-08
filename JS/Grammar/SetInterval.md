# setInterval

**`setInterval`은 일정 시간 간격으로 함수를 반복하는 것이다.**

```javascript
const myInterval = setInterval((fn) => console.log(`Time ${fn} !!`), 3000, 'Interval');
clearInterval(myInterval);
```

`setTimeInterval`은 위처럼 `setTimeout`과 문법은 같다.

해당 함수들의 간단한 예로는

```javascript
let num = 0;
function showTime() {
  console.log(`안녕하세요, 현재 접속하신지 ${num++}초 됐습니다.`);

  if (num > 5) {
    clearInterval(tId);
  }
}

const tId = setInterval(showTime, 1000);
//안녕하세요, 현재 접속하신지 0초 됐습니다.
//안녕하세요, 현재 접속하신지 1초 됐습니다.
//안녕하세요, 현재 접속하신지 2초 됐습니다.
//안녕하세요, 현재 접속하신지 3초 됐습니다.
//안녕하세요, 현재 접속하신지 4초 됐습니다.
//안녕하세요, 현재 접속하신지 5초 됐습니다.
//		[num이 5가 넘었으므로 종료된다.]
```
