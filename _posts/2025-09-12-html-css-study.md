---
title: "[goorm] HTML/CSS 기본 구조 복습"
date: 2025-09-12 23:32:00 +0900
excerpt: "HTML, CSS 기본 구조와 Flex/Grid 레이아웃 학습 기록"
categories: [notes]
tags: [HTML, CSS, Flexbox, Grid]
author_profile: true
#toc: true
---

> ✔️ **To do**
> - 배웠던 내용 다시 리마인드 하며 실습하기  
> - 몰랐던 내용은 꼭 기록 후 TIL 남기기
{: .notice--info}

### 1️⃣ HTML
##### ▫️ 개념
  - 웹을 이루는 가장 기초적인 구성 요소
  - 웹 페이지를 만들기 위한 표준 마크업 언어  

    > **마크업 언어**  
    > 태그를 이용해 문서의 구조와 의미를 표시하는 언어  
    {: .notice}

##### ▫️ 기본 구조

  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>문서 제목</title>
    </head>
    <body>
      문서 내용
    </body>
  </html>
  ```

##### ▫️ 구성 요소
  - 태그 (Tag)
      - 웹 문서를 구성하는 명령어
      - 시작 태그 `< >`와 종료 태그`< />`로 구성
      - 일부 태그는 종료 태그 없음 :  `<br>`, `<hr>`
  - 요소 (Elemant)
      - 시작 태그 + 내용 + 종료 태그
      - 빈 요소, *Empty Element*   `ex) <br>, <hr>`
      - 블록, *Block Element*          `ex) <div>, <p>`
      - 인라인, *Inline Element*      `ex) <span>, <a>`
  - 속성 (Attribute)
      - 태그를 보조하는 명령어
      - 태그 안쪽에 위치하여, 추가 정보를 제공

##### ▫️ 시맨틱 요소
  - 브라우저와 개발자에게 의미를 명확하게 설명하는 요소
  - 문서의 구조와 역할을 직관적으로 표현

    ```html
    <header>   <!-- 머리글 -->
    <nav>      <!-- 내비게이션 -->
    <section>  <!-- 구획 -->
    <article>  <!-- 독립적인 콘텐츠 -->
    <aside>    <!-- 보조 정보 -->
    <footer>   <!-- 바닥글 -->
    ```

### 2️⃣ CSS (Cascading Style Sheets)
##### ▫️ 개념
  - 문서를 사용자에게 어떻게 표시할지 지정하는 언어
  - 웹 페이지의 레이아웃과 시각적 표현 담당

##### ▫️ 기본 구조
 `선택자(selector) { 속성(property): 값(value); }`
    
    - 선택자 : 적용할 HTML 요소 지정
    - 속성 : 무엇을 바꿀지 지정
    - 값 : 어떻게 바꿀지 지정

##### ▫️ 사용 방식
  - 인라인 스타일
        
    ```html
    <p style="color:red">
    ```
        
  - 내부 스타일 시트
    
    ```html
    <style>
      p { color: red; }
    </style>
    ```
        
  - 외부 스타일 시트
    
    ```html
    <link rel="stylesheet" href="style.css">
    ```

      > **스타일 적용의 우선순위**  
      > 1. 인라인스타일
      > 2. 내부 스타일 시트
      > 3. 외부 스타일 시트
      > 4. 브라우저 기본 스타일
      {: .notice}

##### ▫️ 가상 클래스 (Pseudo-class)
  - 별도의 클래스를 없이 특정 상태 요소를 선택
    
    ```css
    :hover {}
    :active {}
    :focus {}
    :first-of-type {}
    :last-of-type {}
    :first-child {}
    :last-child {}
    ```

##### ▫️ 가상 요소 (Pseudo-element)
  - 요소의 특정 부분을 선택해 스타일 적용
    
    ```css
    ::before {}
    ::after {}
    ::selection {}
    ::marker {}
    ::first-letter {}
    ::first-line {}
    ```

##### ▫️ FlexBox
  - 1차원 배치
  - Main Axis / Cross Axis 기준 정렬
  - 컨테이너 내의 아이템들을 동적으로 정렬하기 위해 사용
  - 반응형 레이아웃에 유용
  - Container 속성
      
      ```css
      .container {
        display: flex;               /* 또는 inline-flex */
        flex-direction: row;         /* 주축 방향 (row, column, row-reverse, column-reverse) */
        flex-wrap: nowrap;           /* 줄바꿈 여부 (nowrap, wrap, wrap-reverse) */
        flex-flow: row nowrap;       /* flex-direction + flex-wrap 단축 속성 */
        justify-content: flex-start; /* 주축 정렬 */
        align-items: stretch;        /* 교차축 한 줄 정렬 */
        align-content: stretch;      /* 교차축 여러 줄 정렬 */
      }
      ```
      
  - Item 속성
      
      ```css
      .item {
        order: 0;           /* 아이템 순서 */
        flex-grow: 0;       /* 남는 공간 차지 비율 */
        flex-shrink: 1;     /* 공간 부족 시 줄어드는 비율 */
        flex-basis: auto;   /* 기본 크기 */
        flex: 0 1 auto;     /* grow, shrink, basis 단축 속성 */
        align-self: auto;   /* 개별 아이템 교차축 정렬 */
      }
      ```

##### ▫️ CSS Grid
  - 2차원 배치
  - 행(Row)와 열(Column) 단위로 컨테이너를 나누어 배치
  - 복잡한 레이아웃 구현과 반응형 디자인에 유용
  - Container 속성
      
      ```css
      .container {
        display: grid;                        /* 또는 inline-grid */
      
        grid-template-columns: 1fr 1fr 1fr;   /* 열 정의 
                                                  - px, %, auto, fr 사용 가능
                                                  - fr: 남은 공간 비율 배분
                                                  - repeat(3, 1fr): 반복 정의 */
        grid-template-rows: auto 200px auto;  /* 행 정의
                                                  - px, %, auto, fr 모두 가능 
                                                  - auto: 콘텐츠 크기에 맞춤 
                                                  - minmax(min, max) 지정 가능 */
      
        gap: 10px;                            /* 행과 열 간격 (row + column) */
        row-gap: 10px;                        /* 행 간격 전용 */
        column-gap: 20px;                     /* 열 간격 전용 */
      }
      ```
      
  - Item 속성
      
      ```css
      .item {
        grid-column-start: 1;   /* 시작 열 (숫자 인덱스, 이름 지정 가능) */
        grid-column-end: 3;     /* 끝 열 (숫자, span 2 → 2칸 차지) */
        grid-row-start: 1;      /* 시작 행 */
        grid-row-end: 2;        /* 끝 행 */
      
        grid-column: 1 / 3;     /* 열 시작/끝 단축 속성 (start / end) */
        grid-row: 1 / 2;        /* 행 시작/끝 단축 속성 */
      
        /* 개별 아이템 정렬 옵션 */
        justify-self: start;    /* 수평 정렬: start | end | center | stretch */
        align-self: center;     /* 수직 정렬: start | end | center | stretch */
      }
      ```


> ** 📘 Today I Learned :**
> - HTML, CSS 기본 구조 복습
>   - `margin`, `padding` 상하좌우 한번에 지정하는 방식 리마인드 ✔️
> - FleeBox 1차원 레이아웃 학습 및 실습
> - CSS Grid 2차원 레이아웃 학습 및 실습 <br>
>    👉 추후 개인 미션에서 반응형 레이아웃 설계에 활용할 것❗
{: .notice--info}