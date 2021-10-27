# 상속 선택자

- ### 조상 자손 선택자</br>
  아래의 태그는 ul 밑에 있는 모든 태그를 선택합니다.
  ```css
  ul li {
    color: red;
  }
  ```
- ### 부모 자손 선택자</br>
  아래 선택자는 #lecture 바로 밑에 있는 li만을 선택합니다.

```css
#lecture > li {
  border: 1px solid red;
}
```

- ### 동시 선택자 (형제 관계 선택자)</br>
  아래 코드는 ul과 ol을 동시에 선택합니다.

```css
ul,
ol {
  background-color: powderblue;
}
```
