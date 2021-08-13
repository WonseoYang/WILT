# 추가 메모 사항

## 번외 메소드

해당 메소드는 아직 배우지 않은 `prototype`이라는 메소드이다.

### includes()

문자열 또는 배열에서 포함되어있는 지를 확인하여 `true`, `false' 값을 반환하는 메소드이다.

```javascript
const a = '안녕하세요';
const b = [1, 2, 3, 4, 5];

a.includes('녕'); // true
a.includes('양'); // false
b.includes(5); // true
b.includes(26); // false
```
