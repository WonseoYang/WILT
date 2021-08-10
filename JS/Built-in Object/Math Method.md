## Math 객체

Math는 Number 자료형만 지원하며 BigInt와는 사용할 수 없다.

### Math.ceil()

`Math 객체`의 올림 메소드이다.

```javascript
let num1 = 5.1;
let num2 = 5.7;

Math.ceil(num1); //6;
Math.ceil(num2); //6;
```

### Math.floor()

`Math 객체`의 내림 메소드이다.

```javascript
let num1 = 5.1;
let num2 = 5.7;

Math.floor(num1); //5;
Math.floor(num2); //5;
```

### Math.round()

`Math 객체`의 반올림 메소드이다.

```javascript
let num1 = 5.1;
let num2 = 5.7;

Math.round(num1); //5;
Math.round(num2); //6;
```

### Math.random()

`Math 객체`에서 `0 ~ 1` 사이 무작위의 실수를 생성하는 메소드이다.

```javascript
Math.random(); // 0.7053534276282645
Math.random(); // 0.2551242745528477
```

### Math.max() / Math.min()

`Math 객체`의 최대 값과 최소 값을 찾아내는 메소드이다.

```javascript
Math.max(1, 2, 3, 4, 5, 6, 7); // 7
Math.min(1, 2, 3, 4, 5, 6, 7); // 1
```

### Math.abs()

`Math 객체`의 절대값으로 변환하는 메소드이다.

```javascript
Math.abs(-5); // 5
```

### Math.pow(n, m)

Math 객체의 매개변수로 받는 `n`의 `m`제곱을 반환하는 메소드이다.

```javascript
Math.pow(2, 10); // 1024
// 2의 10제곱인 1024를 반환
```

### Math.pow()

`Math 객체`의 제곱 값을 반환하는 메소드이다.

```javascript
Math.sqrt(5); // 25
```

</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
