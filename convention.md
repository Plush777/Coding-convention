# 마크업 개발 컨벤션

## Table of contents
<br>

- [HTML](#1-html)

    - [기본 스타일](#1-1-기본-스타일)
    - [HTML 문서 형식을 명확하게 지정](#1-2-html-문서-형식을-명확하게-지정)
    - [Boolean 속성](#1-3-boolean-속성)
    - [불필요한 태그 작성](#1-4-불필요한-태그-작성)
    - [목적에 맞는 HTML 태그 사용](#1-5-목적에-맞는-html-태그-사용)
    - [엔티티 참조](#1-6-엔티티-참조)
    - [파일 불러오기](#1-7-파일-불러오기)
    - [주석](#1-8-주석)

<br>

- [CSS](#2-css)

    - [기본 스타일](#2-1-기본-스타일)
    - [스타일 지정 시 클래스를 사용](#2-2-스타일-지정-시-클래스를-사용)
    - [자바스크립트 공통 클래스](#2-3-자바스크립트-공통-클래스)
    - [불필요한 단위 작성](#2-4-불필요한-단위-작성)
    - [색상 표현](#2-5-색상-표현)
    - [클래스 선택자 사용](#2-6-클래스-선택자-사용)
    - [축약형 사용](#2-7축약형-사용)

<br>

- [Sass (Scss)](#3-sass-scss)

    - [.scss 문법을 사용](#scss-문법을-사용)
    - [변수명](#변수명)
    - [선택자 중첩](#선택자-중첩)

<br>

- [Naming](#4-naming)
    
    - [요소 네이밍](#4-1-요소-네이밍)
    - [이미지 네이밍](#4-2-이미지-네이밍)

<br>

- [웹 접근성 (Web accessibility)](#웹-접근성-web-accessibility)

    - 건너뛰기 링크
    - 본문 시작
    - 대체 텍스트
    - 드롭다운 메뉴
    - 테이블
    - 입력 폼 (input , checkbox , radio)
    - 새 창 및 팝업 창
    - 제목
    - 초점

<br><br>

## 1. html

HTML 코드 작성 규칙입니다.

<br>

### 1-1. 기본 스타일
<br>

들여쓰기는 일정한 간격만큼 띄어씁니다.

```html
<table>
    <thead>
        <tr>
            <th scope="col">Name</th>
            <th scope="col">Age</th>
        <tr>
    </thead>
</table>
```

<br>

속성값에는 반드시 큰따옴표("") 를 사용합니다.
```html
<a href="/">Link</a>
```

<br>

태그명,속성명,속성값 등에는 모두 소문자만 사용합니다.
```html
<a href="/" target="_blank">새 창</a>
```

[⬆️ top](#table-of-contents)

<br><br>

### 1-2. HTML 문서 형식을 명확하게 지정
<br>
브라우저의 일관된 렌더링을 위해 상단에 HTML5 DOCTYPE을 명시합니다.

```html
<!DOCTYPE html>
<html>
    <head>

    </head>
    <body>

    </body>
</html>
```

<br>

최상위 `<html>` 태그에는 lang 속성을 주어 문서의 기본 언어를 지정합니다.

```html
<html lang="ko">

</html>
```

<br>

메타태그 `charset` 을 사용하여 문자 인코딩 방식을 지정합니다.

```html
<html lang="ko">
    <meta charset="UTF-8">
</html>
```

[⬆️ top](#table-of-contents)

<br><br>

### 1-3. Boolean 속성

`selected` , `disabled` , `checked` 등의 Boolean 속성은 값을 따로 명시하지 않습니다.

Bad

```html
<input type="checkbox" checked="true">
<input type="text" disabled="true">
<select>
    <option selected="true">
</select>
```

Good

```html
<input type="checkbox" checked>
<input type="text" disabled>
<select>
    <option selected>
</select>
```

[⬆️ top](#table-of-contents)

<br><br>

### 1-4. 불필요한 태그 작성

가능하다면 불필요한 태그 작성은 피해야합니다.

Bad

```html
<span>
    <img src="">
</span>
```

Good

```html
<img src="">
```

[⬆️ top](#table-of-contents)

<br><br>

### 1-5. 목적에 맞는 HTML 태그 사용

목적에 맞는 HTML 태그를 사용하고, HTML5에서 추가 된 시멘틱 태그를 적극 활용합니다.

```html
<h1>Title</h1>

<header>
    ...
</header>
    ...
<section>
    ...
</section>

<footer>
    ...
</footer>
```

[⬆️ top](#table-of-contents)

<br><br>

### 1-6. 엔티티 참조

HTML에서 의미가 있는 `<` 나 `&` 등을 제외한 문자는 엔티티 참조를 사용하지 않습니다.

Bad 
```html
<ul>
    <li>&middot;menu</li>
</ul>
```

Good
```html
<ul>
    <li>· menu</li>
</ul>
```

[⬆️ top](#table-of-contents)

<br><br>

### 1-7. 파일 불러오기

CSS/자바스크립트 파일을 불러오는 경우 `type` 을 명시하지 않습니다. HTML5에서는 `type` 속성의 기본값이 각각 `text/css` , `text/javascript` 로 지정되어 있습니다.

<br>

CSS는 상단에서 불러오고, JS는 `<head>` 또는 `<body>` 의 마지막에서 불러옵니다.

[⬆️ top](#table-of-contents)

<br><br>

### 1-8. 주석
HTML 코드의 주석은 다음 코드처럼 코드 그룹을 구분하거나, 참고사항을 기술할 때 사용합니다.

```html
<!-- container -->
<main class="container">
    <!-- contents -->
    <div id="contents">
        <!-- lnb -->
        <div id="lnb">

        </div>
        <!-- //lnb -->
    </div>
    <!-- //contents -->
</main>
<!-- //container -->
```

[⬆️ top](#table-of-contents)

<br><br>

## 2. CSS

CSS 코드 작성 규칙입니다.

<br>

### 2-1. 기본 스타일
들여쓰기는 공백 2문자를 사용하며, 가독성을 위해 여는 중괄호 앞에는 공백 1문자를 넣고, 닫는 중괄호는 새로운 행에 배치합니다.

Bad
```css
.firstClass{

}

#firstId{}
```

Good

```css
.firstClass {

}

#firstId {}
```

<br>

프로퍼티 선언 시 `:` 이후 공백 1문자를 추가합니다.

Bad
```css
.first{
    width:100px;
    height : 100px;
}
```

Good
```css
.first{
    width: 100px;
    height: 100px;
}
```

<br>

단일 스타일은 한 줄에 표시하고, 다중 스타일은 한 줄에 프로퍼티를
하나씩 표시합니다. scss에서는 한 줄에 하나씩 작성합니다.

Bad
```css
.first{
    width: 100px;
}
.first{width: 100px; height: 100px;}
```

Good
```css
.first{width: 100px;}
.first{
    width: 100px; 
    height: 100px;
}
```
<br>

다중 선택 시 한 줄에 선택자를 하나씩 표시합니다.

Bad
```css
.first,.second,.third{

}
```

Good
```css
.first,
.second,
.third{
    
}
```

<br>

모든 스타일 선언 뒤에는 세미콜론을 붙입니다. (마지막 선언포함)

Bad
```css
.first{
    width: 100px;
    height: 100px;
    background-color: #fff
}
```

Good
```css
.first{
    width: 100px;
    height: 100px;
    background-color: #fff;
}
```

[⬆️ top](#table-of-contents)

<br><br>

### 2-2. 스타일 지정 시 클래스를 사용

마크업 개발 시 아이디는 독립적인 요소 (header,footer,aside 등) 에만 사용하며 개발자와의 혼선을 피하기위해 주로 클래스를 사용합니다. 

[⬆️ top](#table-of-contents)

<br><br>

### 2-3. 자바스크립트 공통 클래스

자바스크립트를 사용해 DOM 조작을 할 때, 스타일 지저을 위해 사용된 클래스나 공통 클래스를 사용하지 않습니다. CSS 스타일 지정 클래스와 자바스크립트 동작 제어 클래스는 서로 다른 책임을 갖기 때문에, 각각을 분리해서 관리하는 것이 유지보수 측면에서 유리합니다. 이 경우, 자바스크립트 클래스를 따로 주거나 `js-` 접두어를 붙여서 사용합니다.

```html
<div class="flex js-container">

</div>
```

[⬆️ top](#table-of-contents)

<br><br>

### 2-4. 불필요한 단위 작성

숫자 0 값 이후에는 불필요한 단위를 작성하지 않습니다.

Bad
```css
margin: 1px 0px 2px 0px;
height: 0px;
```

Good
```css
margin: 1px 0 2px 0;
height: 0;

flex: 0px; /*flex-basis 속성의 경우는 단위가 필요합니다.*/
```

<br>

border가 없을경우 `none` 대신 `0` 을 사용합니다.

Bad
```css
.bd0{border: none;}
```

Good
```css
.bd0{border: 0;}
```

[⬆️ top](#table-of-contents)

<br><br>

### 2-5. 색상 표현
16진법으로 색상을 표현할 경우 가능하면 3글자로 표현합니다.

Bad
```css
color: #000000;
```

Good
```css
color: #000;
```

[⬆️ top](#table-of-contents)

<br><br>

### 2-6. 클래스 선택자 사용
렌더링 성능을 위해 가능한 태그 선택자보다 클래스 선택자를 사용합니다.

Bad
```css
.name span{}
```

<br>

태그 선택자와 함께 속성 선택자(`[class=^=""]`)를 사용할 수 있지만 성능 이슈가 발생하므로 피해야합니다. `type` 선택자를 사용할 경우 큰 따옴표를 사용합니다.(`input[type="text"]`)

Bad
```css
.name span[class^="desc"]{}
```

Good
```css
.name .desc{}
```

<br>

선택자 길이를 짧게 유지하고 최대 3개 이상 넘지않게 제한합니다.

Bad
```css
#header .inner .headerContents .headerMenu li{}
```

Good
```css
.headerMenu li{}
```

[⬆️ top](#table-of-contents)

<br><br>

### 2-7.축약형 사용

`padding`,`margin`,`font`,`backgound`,`border`,`border-radius` 등 축양형 사용이 가능한 프로퍼티는 축약형을 사용합니다.

Bad
```css
font-family: 'Noto Sans';
font-size: 100%;
line-height: 1.6;
padding-top: 0;
padding-right: 10%;
padding-bottom: 0;
padding-left: 10%;
```

Good

```css
font: 100%/1.6 'Noto Sans';
padding: 0 10%;
```

[⬆️ top](#table-of-contents)

<br><br>

## 3. Sass (Scss)

Sass (Scss) 코드 작성 규칙입니다.

<br>

### .scss 문법을 사용

CSS에서 사용하는 모든 문법과 기능이 완전히 호환되도록 만든 `.scss` 문법을 사용합니다.

.sass
```sass
div
    width: 100px; height: 100px;
    p
    color: #000; background-color: #fff;
```

.scss
```scss
div{
    width: 100px; height: 100px;
    p{
        color: #000; background-color: #fff;
    }
}
```

[⬆️ top](#table-of-contents)

<br><br>

### 변수명

변수명은 dash (`-`) 를 사용하는 케밥 케이스(kebab-case) 를 사용합니다. 해당 파일에서마 쓰이는 경우 변수에 underscore (`_`) 를 추가해서 사용할 수 있습니다.

Bad
```scss
$mainBg: #000;
$main_bg: #000;
```

Good
```scss
$main-bg: #000;
```

[⬆️ top](#table-of-contents)

<br><br>

### 선택자 중첩

선택자 중첩은 최대 3단계까지만 사용합니다. 3단계를 넘으면 CSS 컴파일 시 보기에도 안좋고, 재사용할 수 없는 CSS를 작성하고 있을 가능성이 큽니다.

```scss
.wrap{
    .container{
        .content{
            ...
        }
    }
}
```

[⬆️ top](#table-of-contents)

<br><br>

## 4. Naming

네이밍 규칙입니다.

<br>

### 4-1. 요소 네이밍

<br>

타이틀 격인 요소는 tit 접두사를 사용합니다.

```html
<h3 class="titMyname">타이틀</h3>
<div class="titMyname">타이틀</div>
<strong class="titMyname">타이틀</strong>
```

<br>

버튼은 타입을 명시하고 btn 접두사를 사용합니다.
```html
<div class="btnArea">
	<button type="button" class="btnMyname">버튼</button>
</div>
```

[⬆️ top](#table-of-contents)

<br><br>

### 4-2. 이미지 네이밍

이미지 네이밍은 이미지의 사용 용도에 따라 접두사를 달리하여 사용합니다. 아이콘 및 로고는 svg로 저장하고 복잡한 패턴이 들어가있는 배경 이미지는 png,jpg로 저장합니다.

이미지 네이밍 형식은 다음과 같습니다.

> 접두사 + 고유이름 + 번호 + 호버 혹은 활성화 여부

<br>
이름이 두 단어 이상으로 이루어질경우 케밥 케이스로 표현합니다.<br>
ex) bg-black01.png<br>
ex) btn-close-hover.svg

<br>

이미지 종류별 접두사<br>
- 이미지 스프라이트 기법: ir-
- 사진 혹은 일러스트 형식 이미지: img-
- 타이틀 성격의 이미지: tit-
- 텍스트 형식의 이미지: txt-
- 버튼 형식의 이미지: btn-
- 아이콘 형식의 이미지: ico-
- 불렛 형식의 이미지: bullet-
- 더미이미지: dummy-
- 배경 형식의 이미지: bg-

[⬆️ top](#table-of-contents)

<br><br>

## 웹 접근성 (Web accessibility)