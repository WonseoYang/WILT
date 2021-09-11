# setTimeout

**`SetTimeout`은 일정 시간이 지난 후 함수를 실행하는 것이다.**

```javascript
function fn(){
    console.log("타임 아웃");
}

setTimeout(fn, 3000);	// 3초 뒤 fn() 함수 실행

----------------------------------

setTimeout(function(){
  console.log(3);
}, 3000);	//위와 동일하게 작동(함수를 안에 작성)

-----------------------------------

function showName(name){
  console.log(name);
}

setTimeout(showName, 3000, "Mike");
// 실행 할 함수의 인수가 필요하다면 setTimeout의 인수의 맨 뒤에 넣어주면 된다.

```

인수로 동작할 함수와 실행 후 동작까지의 시간을 받는다.

같이 사용하는 함수로는 `ClearTimeout(tId);`이 있다.

```javascript
const myTimeout = setTimeout((fn) => console.log(`Time ${fn} !!`), 3000, 'Out');
clearTimeout(myTimeout);
```

이 처럼 setTimeout은 값을 반환하는데 해당 값을 할당하여 해당 setTimeout의 이름처럼 사용할 수 있다.

값을 할당받은 변수를 clearTimeout에 인수로 넣어주면 해당 setTimeout의 실행을 막는다.
</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
