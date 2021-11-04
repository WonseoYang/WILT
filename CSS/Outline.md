# 개요

## CSS 정의와 목적

CSS는 Cascading Style Sheet의 약자이다. CSS는 문서의 콘텐츠와 레이아웃, 글꼴 및 시각적 요소들로 표현되는 문서의 외관(디자인)을 분리하기 위한 목적으로 만들어졌다.

## CSS 속성

여러 속성 값은 반드시 공백으로 구분되어야 한다.
축약 표현 속성은 여러 속성 값을 하나의 간소화된 선언으로 적용할 수 있다.
속성이 명시되지 않으면 해당 속성의 기본 값이 적용된다

## CSS의 기본 구조

```css
h1 {
  color: yellow;
  font-size: 2em;
}
```

- 선택자(selector) - "h1"
- 속성(property) - "color"
- 값(value) - "yellow"
- 선언(declaration) - "color: yellow", "font-size: 2em"
- 선언부(declaration block) - "{ color: yellow; font-size:2em; }"
- 규칙(rule set) - "h1 { color: yellow; font-size:2em; }"</br></br>
- 선택자는 보통 스타일링하고 싶은 HTML 요소나 부여한 ID 혹은 class가 위치한다.
- 선언부에 여러개의 속성과 속성값이 있을때는 ;(세미콜론)으로 구분한다.
- 각각의 선언은 속성과 속성값을 :(콜론)으로 구분한다.

> ### 출처
>
> 내용 : https://webdir.tistory.com/338
