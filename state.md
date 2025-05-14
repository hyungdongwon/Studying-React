# 📌 오늘 배운 내용 - React state

## 🧠 state란?

React에서는 일반 변수보다 **state**를 사용해서 데이터를 저장하고 관리하는 것이 일반적입니다.  
state는 컴포넌트의 **데이터 상태를 저장하고**, 이 값이 바뀌면 자동으로 화면이 다시 렌더링됩니다.

---

## ✅ state 만드는 법

```
import { useState } from 'react';
import './App.css';

function App() {
  let [a, b] = useState('남자 코트 추천');
  let posts = '강남 우동 맛집';

  return (
    <div className="App">
      <div className="black-nav">
        <div>개발 blog</div>
      </div>
      <div className="list">
        <h4>글제목</h4>
        <p>2월 17일 발행</p>
        <hr/>
      </div>
    </div>
  );
}
```
---
```let [a, b] = useState('남자 코트 추천');```
- a 자리는 state 이름 (원하는 이름으로 자유롭게 지을 수 있음)
- b 자리는 state를 변경할 때 사용하는 함수
  
즉, 위 코드는 "남자 코트 추천"이라는 값을 state에 저장하고
나중에 a를 사용해서 꺼내 쓸 수 있게 만든 것!

## 변수 말고 state에 데이터 저장해서 쓰는 이유
자료 잠깐 보관하는게 끝인데 
그럼 변수 만들어 쓰면 되는거지 왜 굳이 state 만들어쓸까?
state는 변동사항이 생기면 state쓰는 html도 자동으로 재렌더링해줍니다



