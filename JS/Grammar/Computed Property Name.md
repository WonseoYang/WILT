## 계산된 프로퍼티 명 (Computed Property Name)

이름 그대로 이미 계산이 완료된 프로퍼티(속성 명, 키 값)이다.
간단한 예를 통해서도 이해가 될만큼 개념은 쉽다.

다만 아직 나에겐 실사용에서 어떻게 유용하게 사용할 것인지는 고민해야봐야 할 개념이다.

```javascript
let n = 'name';

const user = {
  [n]: 'Mike', // name : "Mike",
  ['a' + 'ge']: 26, // age : 26,
  [4 + 1]: 5, // 5 : 5,
};
```

주석과 같이 동작하는 형태이다.

</br></br></br>

> ### 출처
>
> 내용 : https://www.youtube.com/watch?v=4_WLS9Lj6n4
