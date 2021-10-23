# 선택자의 조합

```css
p.bar {
  ...;
}
```

요소와 클래스를 조합한 경우입니다.
이 경우에는 p 태그이면서 class 속성에 bar가 있어야 적용됩니다.

```css
.foo.bar {
  ...;
}
```

다중 클래스의 경우입니다.
이 경우에는 class 속성에 foo와 bar가 모두 있어야 적용됩니다.

```css
#foo.bar {
  ...;
}
```

id와 class를 조합한 경우입니다.
이 경우에는 id가 foo이며 class가 bar인 요소에 적용됩니다.
