# 📌 오늘 배운 내용
- 레이아웃 만들 때 쓰는 JSX 문법 3개

## ✨ JSX 문법1 - className
### 📌 1. JSX에서 `class` 대신 `className`을 사용해야 하는 이유

JSX는 **HTML이 아니라 자바스크립트를 기반으로 한 문법**이기 때문에  
자바스크립트의 **예약어인 `class`** 를 그대로 사용할 수 없습니다.

그래서 HTML에서 사용하는 `class="..."`는  
JSX에서는 반드시 `className="..."`으로 작성해야 합니다.

---

### ✅ 예시 코드

```jsx
// App.js
function App() {
  return (
    <div className="App">
      <div className="black-nav">
        <h4>리액트 예제</h4>
      </div>
    </div>
  );
}
```
---
## ✨ JSX 문법 2 - 변수를 HTML에 넣을 때는 `{ 중괄호 }`

JSX에서는 HTML 코드 안에 **변수**를 넣을 때 반드시  
`{ 중괄호 }` 문법을 사용해야 합니다.

이는 **JSX가 자바스크립트 기반**이기 때문에 가능한 문법이며,  
HTML 속성 속에도 중괄호를 사용할 수 있습니다.

---

### ✅ 중괄호 사용 가능한 속성 예시

- `className={변수}`
- `id={변수}`
- `href={변수}`
- `src={변수}`  
등 대부분의 HTML 속성에 사용 가능합니다.

---

### 📌 이를 전문 용어로는?

> **"데이터 바인딩"** (Data Binding)  
: 자바스크립트의 데이터를 HTML에 연결해주는 작업

---

### 💡 예시 코드

```jsx
function App() {
  var data = 'red';

  return (
    <div className="App">
      <div className="black-nav">
        <div>개발 blog</div>
        <div className={data}>안녕하세요</div>
      </div>
    </div>
  );
}
```
---
## ✨ JSX 문법 3 - html에 style속성

`<div style="color : blue">` 이런걸 넣고 싶으면
JSX 상에서는 style={ } 안에 { } **자료형**으로 집어넣어야합니다. 

**{ 속성명 : '속성값' }** 이렇게 넣으면 됩니다. 
근데 font-size 처럼 속성명에 **대쉬기호를 쓸 수 없습니다.**

대쉬기호 대신 모든 단어를 붙여써야합니다. 붙여쓸 땐 **앞글자를 대문자로 치환**해야합니다.

---

### 💡 예시 코드

```
<div style={ {color : 'blue', fontSize : '30px'} }> 글씨 </div>
```

