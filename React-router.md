# 💡오늘의 학습내용 
- router셋팅이랑 기본 라우팅

---

## ❓router의 사용이유

일반 html css js 사이트는 그냥 html 파일 여러개 만들면 그게 하나의 페이지인데 

근데 리액트는 html 파일을 하나만 사용합니다.

그래서 리액트에선 누가 다른 페이지 요청하면 그냥 내부에 있는 ```<div>```를 갈아치워서 보여주면 됩니다. 

근데 직접 코드짜면 귀찮으니 react-router-dom 이라는 외부 라이브러리 설치해서 구현하는게 일반적.

---

## 📜 router 설치법

터미널 열어서  ```npm install react-router-dom@6``` 입력해서 설치합니다.

```
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
      <BrowserRouter>
        <App />
      </BrowserRouter>
  </React.StrictMode>
); 
```

셋팅은 index.js (또는 main.jsx) 파일로 가서 

 ▲ import 해오고

<BrowserRouter> 이걸로 <App/> 이걸 감싸면 끝.

---

## 🔧router로 페이지 나누는 법 

```
(App.js)

import { Routes, Route, Link } from 'react-router-dom'

function App(){
  return (
    (생략)
    <Routes>
      <Route path="/detail" element={ <div>상세페이지임</div> } />
      <Route path="/about" element={ <div>어바웃페이지임</div> } />
    </Routes>
  )
}
```

1. 우선 상단에서 여러가지 컴포넌트를 import 해오고 

2. <Routes> 만들고 그 안에 <Route>를 작성합니다.

3. <Route path="/url경로" element={ <보여줄html> } /> 이렇게 작성하면 됩니다. 

그래서 방금 페이지 2개 만든 것임 

---

## 🔧페이지 이동 버튼은

유저들은 주소창에 url 입력해서 들어가지 않고 링크타고 들어갑니다. 

링크를 만들고 싶으면 react-router-dom에서 Link 컴포넌트 import 해오고 

원하는 곳에서 <Link> 쓰면 됩니다. 

```
<Link to="/">홈</Link>
<Link to="/detail">상세페이지</Link>
```




