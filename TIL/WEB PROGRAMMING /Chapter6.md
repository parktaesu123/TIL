## 스타일 형식

```
선택자 { 속성1: 속성값1; 속성2; 속성값2; }

p {
	text-align: center;
	color: blue;
	}
```

## <스타일 시트>

### 브라우저 기본 스타일

### 사용자 스타일

→인라인 스타일

- 적용할 대상에 직접 표시한다.

```html
 <p style="color: brown;">holy</p>
```

→내부 스타일 시트

- <head> 태그 안에서 정의한다.
- 해당 선택자 범위에 속하는 것들에 스타일을 입힌다.

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        #container {
            width: 600px;
            margin: 20px auto;
        }
        h1 {
            display: inline-block;
            background-color: #0404aa;
            color: #fff;
        }
        .accent {
            font-weight: bold;
            color: red;
        }
    </style>
</head>
```

### →외부 스타일 시트

- 웹 문서에서 사용할 스타일을 별도 파일로 저장해 놓고 필요할 때 가져다 쓴다.
- link태그를 사용한다.
    
    ```html
    <link rel="stylesheet" href="css/firstcss.css">
    ```
    

---

### 전체 선택자

- 모든 요소에 적용합니다.

```html
 * {
            text-align: center;
            margin: 0;
            font-style: italic;
        }
```

### 타입 선택자

- 특정 태그를 사용한 모든 요소에 스타일을 적용합니다.

```html
p {
            color: blue;     
            margin: 0;
        }
```

### 클래스 선택자

- 특정 부분만 선택해서 스타일을 적용합니다.
- 클래스 이름앞에 **.** (마침표)를 붙여야 합니다.

```html
.accent {
            border: 1px solid #000;
            padding: 5px;
        }
        .bg {
            background-color: #ddd;
        }
        
 <h1 class="accent bg">레드향</h1>
    <p class="asdf">집가고 싶다</p>
    <p>이이이이이이</p>
    <p style="color: brown;">holy</p>
```

### id선택자

- 클래스 선택자와 비슷하지만 문서에서 한 번만 적용할 수 있다는 점이 다르다
- id이름앞에 #을 붙인다.

```html
#container {
            width: 500px; 너비 
            margin: 10px auto; 중앙배치
            padding: 10px; 테두리와 내용사이 여백
            border: 1px solid #000; 테두리 굵기와 색깔
        }
 
 <div id="container">
        <h1>레드향</h1>
        <p>시험얼마 안남았다 젠장</p>
    </div>
```

### 그룹 선택자

- 쉼표로 구분해서 여러 선택자를 나열한 후 스타일 규칙을 정의 한다.

```html
h1, p {
	text-align: center; //중앙 정렬
	}
```
---

## 캐스캐이딩

- CSS에서는 웹 요소에 둘 이상의 스타일을 적용할 때 우선순위에 따라 적용할 스타일을 결정한다.
- 캐스케이딩은 스타일끼리 충돌하지 않도록 막아 주는 중요한 개념이다.
- 스타일이 충돌하지 않게 하는 2가지 방법
    
    ```
    - **스타일 우선순위**: 스타일 규칙의 중요도와 적용 범위에 따라 우선순위가 결정되고,
    그 우선순위에 따라 위에서 아래로 스타일을 적용한다.
    - **스타일 상속**: 태그의 포함 관계에 따라 부모 요소의 스타일을 자식 요소로, 
    위에서 아래로 전달한다.
    ```
    

### 스타일 우선순위

- 다음 3가지 개념에 따라 지정된다.
    - 얼마나 중요한가?
        1. **사용자 스타일**
        2. **제작자 스타일**
        3. **브라우저 기본 스타일**
    - 적용 범위는 어디까지인가?
        1. **!important**: 어떤 스타일보다 우선 작용하는 스타일이다.
        2. **인라인 스타일**: 태그 안에 style속성을 사용해 해당 태그만 스타일을 적용한다.
        3. **id 스타일**: 지정한 부분에만 적용되는 스타일이지만 한 문서에 한 번만 적용할 수 있다.
        4. **클래스 스타일**: 지정한 부분에만 적용되는 스타일로 한 문서에 여러 번 적용할 수 있다.
        5. **타입 스타일**: 특정 태그에 스타일을 똑같이 적용한다.
    - 소스 코드의 작성 순서는 어떠한가?
        - 스타일 시트에서 중요도와 적용 범위가 같다면 스타일을 정의한 소스순서로 우선순위가 정해진다.
        - 나중에 작성한 스타일이 먼저 작성한 스타일을 덮어쓴다.
        
        ```html
        p {
                    color: black;
                }
                h1 {
                    color: brown !important;
                }
                p {
                    color: blue;
                }
         
         <h1 style="color: green;">레드향</h1>
            <p style="color: red;">껍질에 붉은 빛이 돌아 레드향이라 불린다.</p>
            <p>레드향은 한라봉과 귤을 교배한 것으로</p>
            <p>일반 귤보다 2~3배 크고, 과육이 붉고 통통하다.</p>
        ```
        

### 스타일 상속

- 여러 태그는 서로 **포함 관계**가 있다. 이때 포함하는 태그를 부모 요소, 포함된 태그를 자식요소라고 한다.
- 스타일시트에서는 자식 요소에서 별도로 스타일을 지정하지 않으면 부모 요소의 스타일 속성들이 자식 요소로 전달된다. → **스타일 상속**
