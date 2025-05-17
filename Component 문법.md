## 💡오늘의 학습내용 
- Component 문법
---


### 🔖Component 란?
리액트는 긴 HTML을 한 단어로 깔끔하게 치환해서 넣을 수 있는 문법을 제공합니다.

축약한 HTML 덩어리를 **Component** 라고 부릅니다. 

이걸 이용하면 함수 만들듯, 변수 만들듯 HTML을 깔끔하게 한 단어로 치환해서 원하는 곳에 꽂아넣을 수 있습니다.

---

### 🔧복잡한 html을 한 단어로 치환할 수 있는 Component 문법 예시 
```
function App (){
  return (
    <div>
      (생략)
      <Modal></Modal>
    </div>
  )
}

function Modal(){
  return (
    <div className="modal">
      <h4>제목</h4>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}
```
1. function을 이용해서 함수를 하나 만들어주고 작명합니다. 

2. 그 함수 안에 return () 안에 축약을 원하는 HTML을 담으면 됩니다.

3. 그럼 원하는 곳에서 <함수명></함수명> 사용하면 아까 축약한 HTML이 등장합니다.

---

## ⚠️Component 만들 때 주의점    

- component 작명할 땐 영어대문자로 보통 작명합니다.

- return () 안엔 html 태그들이 평행하게 여러개 들어갈 수 없습니다.

- component 안에 component 를 만들진 않습니다. 

- <컴포넌트></컴포넌트> 이렇게 써도 되고 <컴포넌트/> 이렇게 써도 됩니다.

---
   
## ❓어떤 HTML들을 Component 만드는게 좋을까

- 사이트에 반복해서 출현하는 HTML 덩어리들은 Component로 만들면 좋습니다.

- 내용이 매우 자주 변경될 것 같은 HTML 부분을 잘라서 Component로 만들면 좋습니다.

- 다른 페이지를 만들고 싶다면 그 페이지의 HTML 내용을 하나의 Component로 만드는게 좋습니다.

- 또는 다른 팀원과 협업할 때 웹페이지를 Component 단위로 나눠서 작업을 분배하기도 합니다.

---

## 👎Component의 단점

- HTML 깔끔하게 쓰려고 Component를 수백개 만들면 그것 만으로도 관리가 어렵다.

- function 안에 있는 변수를 다른 function에서 맘대로 쓸 수 가 없다. props라는 문법을 이용해 state를 <Modal>까지 전해줘야 비로소 사용가능.

---

## 📖 오늘의 정리 

온갖 잡다한걸 Component로 쪼개지 말고 꼭 필요한 곳만 Component로 쪼개자
