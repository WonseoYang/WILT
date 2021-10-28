# 속성 선택자

### <u>단순 속성</u>

CSS

```css
p[class] {
  color: silver;
}
p[class][id] {
  text-decoration: underline;
}
```

HTML

```html
<p class="foo">Hello</p>
<p class="bar">CSS</p>
<p class="baz" id="title">HTML</p>
```

### <u>부분 속성</u>

CSS

```css
p[class~='color'] {
  font-style: italic;
} /* 1, 2번째 요소 */
p[class^='color'] {
  font-style: italic;
} /* 1, 3번째 요소 */
p[class$='color'] {
  font-style: italic;
} /* 2번째 요소 */
p[class*='color'] {
  font-style: italic;
} /* 1, 2, 3번째 요소 */
```

HTML

```html
<p class="color hot">red</p>
<p class="cool color">blue</p>
<p class="colorful nature">rainbow</p>
```

- [class~="bar"] : class 속성의 값이 공백으로 구분한 " color " 단어가 포함되는 요소 선택
- [class^="bar"] : class 속성의 값이 "color"로 시작하는 요소 선택
- [class$="bar"] : class 속성의 값이 "color"로 끝나는 요소 선택
- [class*="bar"] : class 속성의 값이 "color" 문자가 포함되는 요소 선택
  부분 속성값으로 선택은 속성 이름과 속성값 사이에 사용되는 기호에 따라 동작이 조금 다릅니다.
