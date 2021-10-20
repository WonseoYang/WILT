# **속성 선택자**

- 단순 속성

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
