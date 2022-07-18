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

- [웹 접근성 (Web accessibility)](#5-웹-접근성-web-accessibility)

    - [건너뛰기 링크](#5-1-건너뛰기-링크)
    - [블라인드 텍스트](#5-2-블라인드-텍스트)
    - [본문 시작 텍스트](#5-3-본문-시작-텍스트)
    - [대체 텍스트](#5-4-대체-텍스트)
    - [요소](#5-5-요소)
    - [새 창](#5-6-새-창-알림)
    - [초점](#5-7-초점-이동)
    - 명도대비

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

## 5. 웹 접근성 (Web accessibility)

웹 접근성 코드 작성 규칙입니다.

기준 : 한국형 웹 콘텐츠 접근성 지침 2.1 http://www.websoul.co.kr/accessibility/WA_guide21.asp

<br>

### 5-1. 건너뛰기 링크

많은 양의 컨텐츠들을 가지고 있는 홈페이지에서 원하는 영역을 도달하려면 `Tab` 키를 수도 없이 눌러야 하는데, 이 처럼 불필요한 액션을 없애기 위해 건너뛰기 링크 (Skip navigation) 이란 것을 제공해야 합니다.

![image](https://user-images.githubusercontent.com/87457620/179388102-a097ca65-d86b-4641-84f0-0a14de820458.png)

![image](https://user-images.githubusercontent.com/87457620/179388135-12161bcd-1479-47a8-b1c8-0d4db2561dad.png)

<br>

건너뛰기 링크의 위치는 `<body>` 바로 밑에 배치하는 것이 적절합니다.
```html
<body>
    <div class="accNav">
        <a href="#gnb">주요메뉴 바로가기</a>
        <a href="#content">본문 바로가기</a>
        <a href="#footer">푸터 바로가기</a>
    </div>
</body>
```

<br>

css는 다음과 같이 `Tab` 키를 눌렀을 때 활성화가 되도록 코딩합니다. (방식은 작성자마다 다를 수 있습니다.)
```css
.accNav{
    position: absolute; 
    top: 0; 
    left: 0; 
    z-index: 999999999; 
    width: 100%; 
    height: 0;
}

.accNav a{
    display: block; 
    position: absolute; 
    left: 0; 
    top: 0; 
    overflow: hidden; 
    width: 1px; 
    height: 1px; 
    margin-left: -1px; 
    margin-bottom: -1px; 
    text-align: center; 
    color: #fff;
    white-space: nowrap; 
    font-size: 0.75em;
}

.accNav a:focus,
.accNav a:hover,
.accNav a:active{
    width: 100%;
    height: auto; 
    padding: 5px 0; 
    font-weight: 700;
    color: #4A2713; 
    background: #ffc000; 
    z-index: 1000; 
}
```

[⬆️ top](#table-of-contents)

<br><br>

### 5-2. 블라인드 텍스트

숨겨야 하는 콘텐츠이지만, 스크린 리더기에는 읽혀야 하는 경우 사용됩니다. `display: none` 혹은 `visibility: hidden` 속성은 스크린 리더기에서 읽히지 않기 때문에 사용하지 않습니다.

```css
.hidden{
    display: block;
    margin: 0;
    padding: 0;
    width: 0;
    height: 0;
    overflow: hidden;
    font-size: 0;
    line-height: 0;
}
```

<br>

✅ example
```html
<!-- table caption 숨김 -->
<div class="table">
    <table>
        <caption class="hidden">테이블</caption>
        <thead>
            ...
        </thead>
        <tbody> 
            ...
        </tbody>
    </table>
</div>

<!-- 텍스트가 없는 콘텐츠 설명 -->
<button type="button" class="btnTop">
    <span class="hidden">위로 올라가기</span>
</button>
```

[⬆️ top](#table-of-contents)

<br><br>

### 5-3. 본문 시작 텍스트

페이지의 콘텐츠가 시작되는 부분에 본문 시작 텍스트를 표시해야 합니다.

```html
<div id="wrap">
    <header id="header">
        ...
    </header>
    <div class="container">
        <div id="content">
            <h2 class="hidden">본문 시작</h2>
            ...
        </div>
    </div>
    <footer id="footer">
        ...
    </footer>
</div>
```

[⬆️ top](#table-of-contents)

<br><br>

### 5-4. 대체 텍스트

눈으로 화면을 볼 수 없는 경우 이미지에 대한 설명을 대체 텍스트로 입력하여 스크린 리더기를 통해 인식할 수 있게 합니다.

![image](https://user-images.githubusercontent.com/87457620/179390122-16ecfb8e-a7d0-4786-807c-b4668c434bf8.png)

<p style="font-size: 12px;">이미지 출처: NAVER</p>

```html
<img src="logo.png" alt="제74주년 제헌절">
```

<br>

다음과 같은 이미지처럼 장식 목적의 이미지는 대체 텍스트를 빈 값으로 넣어서 스크린 리더기에 읽히지 않게 해야합니다.

![image](https://user-images.githubusercontent.com/87457620/179390270-18ed2c93-e215-4a18-ae36-afdf7ca9c450.png)

```html
<img src="dummy-coding.png" alt="">
```

[⬆️ top](#table-of-contents)

<br><br>

### 5-5. 요소

<br>

#### A. 테이블

테이블 태그 안에는 반드시 `<caption>` 태그로 테이블에 대한 제목을 작성해야 합니다.

```html
<div class="table">
    <table>
        <caption>테이블 제목</caption>
    </table>
</div>
```

<br>

스크린 리더기를 사용하는 사용자가 오직 귀로만 테이블의 정보를 얻어야 할경우, `scope` 속성을 사용하여 테이블의 데이터를 인식하고 읽는 순서를 정해주어야 합니다.

![image](https://user-images.githubusercontent.com/87457620/179393466-12b40d35-8e92-403a-a0fe-fa2f931b21cf.png)

<br>

위 이미지처럼 th의 방향이 열로 되어있을경우, `col` 로 정의합니다.

```html
<table>
    <caption> 테이블 제목</caption>
    <thead>
        <tr>
            <th scope="col">제목</th>
            <th scope="col">제목</th>
            <th scope="col">제목</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
    </tbody>
</table>
```

<br><br>

![image](https://user-images.githubusercontent.com/87457620/179393641-d0d81d98-1168-43e7-a47f-8423583acfdb.png)

반대로 th의 방향이 행으로 되어있을경우, `row` 로 정의합니다.

```html
<table>
    <caption> 테이블 제목</caption>
    <colgroup>
        <col style="width: 300px;">
        <col style="width: 700px;">
    </colgroup>
    <tbody>
        <tr>
            <th scope="row">제목</th>
            <td>내용</td>
        </tr>
        <tr>
            <th scope="row">제목</th>
            <td>내용</td>
        </tr>
        <tr>
            <th scope="row">제목</th>
            <td>내용</td>
        </tr>
    </tbody>
</table>
```

<br><br>

![image](https://user-images.githubusercontent.com/87457620/179397281-7857af8f-4928-4cc1-bcae-98d47e371cfe.png)

행 방향으로 병합 되어있을경우, `colgroup` 으로 정의합니다.

```html
<table>
    <caption> 테이블 제목</caption>
    <colgroup>
        <col style="width: 200px;">
        <col style="width: 150px;">
        <col style="width: 150px;">
        <col style="width: 150px;">
    </colgroup>
    <thead>
        <tr>
            <th rowspan="2" scope="col">제목</th>
            <th colspan="3" scope="colgroup">제목</th>
        </tr>
        <tr>
            <th scope="col">제목</th>
            <th scope="col">제목</th>
            <th scope="col">제목</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">제목</th>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <th scope="row">제목</th>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
    </tbody>
</table>
```

<br><br>

![image](https://user-images.githubusercontent.com/87457620/179397606-24323d2f-1025-4c41-bfd2-b2599b905e17.png)

열 방향으로 병합이 되어있을경우, `rowgroup` 으로 정의합니다.

```html
<table>
    <caption>테이블 제목</caption>
    <colgroup>
        <col style="width: 200px;">
        <col style="width: 200px;">
        <col style="width: 120px;">
        <col style="width: 120px;">
        <col style="width: 120px;">
    </colgroup>
    <thead>
        <tr>
            <th scope="col">제목</th>
            <th scope="col">제목</th>
            <th colspan="3" scope="colgroup">제목</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th rowspan="3" scope="rowgroup">제목</th>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <th rowspan="2" scope="rowgroup">제목</th>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
        <tr>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
            <td>내용</td>
        </tr>
    </tbody>
</table>
```

[⬆️ top](#table-of-contents)

<br><br>

#### B. 입력 폼 (input , checkbox , radio)

<br>

입력 폼에는 `<label>` 을 반드시 제공해야 합니다. 
```html
<label for="input01">
<input type="text" id="input01"/>
```

<br>

`<input>` 만 있는 경우 `title` 속성을 꼭 명시해야 합니다.
```html
<input type="text" id="user_name" title="아이디"/>
```

<br>

읽기 전용 편집 창인경우 `title` 속성을 꼭 명시해야 합니다.
```html
<input type="text" readonly value="21" title="나이"/>
```

<br>

`placeholder` 는 보조 수단으로 레이블 대체가 불가능하기 때문에 `title` 속성을 꼭 명시해야 합니다.
```html
<input type="text" placeholder="아이디 입력" title="아이디 입력"/>
```

<br>

다수의 입력 서식이 존재하는 경우 `title` 속성으로 입력 내용을 상세히 명시합니다.

```html
<input type="text" placeholder="년(4자)" title="태어난 년도 4자리" />
<input type="text" placeholder="월" title="태어난 월" />
<input type="text" placeholder="일" title="태어난 일" />
```

<br>

체크박스 , 라디오 버튼 등을 커스터마이징 하기위해 기본 스타일을 숨김처리 할 때 `display: none` , `visibility: hidden` 속성은 사용하지 않습니다. (작성 방식은 작성자마다 다를 수 있습니다.)

✅ example
```css
input[type="checkbox"],input[type="radio"]{
    -webkit-appearance: none;
    position: absolute;
    vertical-align: middle;
    visibility: visible;
    left: 0;
}
```

<br>

체크박스를 체크했을 때와 안했을 때, 라디오 버튼을 눌렀을 때 `aria-checked` 속성을 제공하여 선택됨과 선택안됨을 구분합니다.

✅ example
```html
<!-- checkbox -->
<div class="checkbox">
    <input type="checkbox" id="chk01" aria-checked="false"/>
    <label for="chk01">label</label>
    <input type="checkbox" id="chk02" aria-checked="true"/>
    <label for="chk02">label</label>
</div>
<!-- //checkbox -->

<!-- radio -->
<div class="radio">
    <input type="radio" id="rd01" name="rd" aria-checked="false">
    <label for="rd01">label</label>
    <input type="radio" id="rd02" name="rd" aria-checked="true">
    <label for="rd02">label</label>
</div>
<!-- //radio -->
```
[⬆️ top](#table-of-contents)

<br><br>

### 5-6. 새 창 알림

사전에 새 창 열림 정보를 인지할 수 있도록 새 창 알림을 제공해야 합니다.

```html
<div class="linkArea">
    <a href="https://www.naver.com/" target="_blank" title="새 창 열림">이동</a>
</div>
```
[⬆️ top](#table-of-contents)

<br><br>

### 5-7. 초점 이동

PC 웹은 키보드만으로도 사용할 수 있어야 합니다.

<br>

#### A. 링크 , 버튼 , 입력 폼

`<a>` , `<button>` , `<input>` , `<select>` 등은 `Tab` 했을 때 초점이 올바르게 이동해야하며, 시각적으로 표시 되어야 합니다. `outline: 0` 속성 사용 시 초점이 올바르게 표시되지 않으니 사용하지 않아야합니다.

<br>

#### B. 스크롤 요소

키보드 접근만으로도 스크롤 기능을 사용할 수 있어야 합니다. 스크롤 기능이 사용 된 요소에 `tabindex="0"` 또는 기능이 있는 내부 링크를 제공하는 방법 등을 이용하여
키보드로도 스크롤 기능을 운용할 수 있어야 합니다.

<br>

#### C. 레이어 팝업

레이어 팝업 활성화 시에는 레이어 영역으로 바로 접근되어 최 상단 내용부터 순차적으로 인식 및
이용 가능해야 하며 레이어 팝업 닫기 기능 실행 시에는 레이어 팝업을 실행했던 링크로 초점이
다시 회귀되어야 합니다.

[⬆️ top](#table-of-contents)