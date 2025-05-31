# 💡오늘의 학습내용 
- AJAX

## ❓서버란?

유저가 데이터달라고 요청을 하면 데이터를 보내주는 간단한 프로그램일 뿐입니다.

![image](https://github.com/user-attachments/assets/7d37a3ce-4eef-4a4a-b4ab-ad03008e36ed)

유저가 그냥 데이터달라고 떼쓰면 서버가 보내주진 않습니다.

서버에 데이터를 요청할 때는 정확한 규격에 맞춰서 요청해야하는데 

1. 어떤 데이터인지 (URL 형식으로)

2. 어떤 방법으로 요청할지 (GET or POST)

잘 기재해야 데이터를 보내줍니다. 

데이터를 가져올 때는 보통 **GET** 고르면 되고 

데이터를 서버로 보낼 때는 **POST** 고르면 됩니다. 

그리고 어떤 데이터를 보고싶은지 URL만 잘 기재하면 됩니다.

---

## 🔧GET/POST 요청하는 법

GET요청을 날리고 싶으면 가장 쉬운 방법은 브라우저 주소창입니다.

거기에 URL 아무거나 적으면 그 곳으로 GET요청을 날려줍니다.


POST요청을 날리고 싶으면

```<form action="요청할url" method="post">``` 태그 이용하면 됩니다.

그럼 폼이 전송되었을 때 POST요청을 날려줍니다. 

근데 GET, POST 요청을 저렇게 날리면 단점이 뭐냐면 브라우저가 새로고침됩니다.

---

## ❓ AJAX란? 

서버에 GET, POST 요청을 할 때 **새로고침 없이** 데이터를 주고받을 수 있게 도와주는

간단한 브라우저 기능을 AJAX라고 합니다. 

그거 쓰면 새로고침 없이도 쇼핑몰 상품을 더 가져올 수도 있고

새로고침 없이도 댓글을 서버로 전송할 수도 있고 

그런 기능을 만들 수 있는 것임 

AJAX로 GET/POST요청하려면 방법 3개 중 택1 하면 됩니다.

- 1. XMLHttpRequest라는 옛날 문법 쓰기

- 2. fetch() 라는 최신 문법 쓰기

- 3. axios 같은 외부 라이브러리 쓰기 

- 3번이 가장 편하니 3번을 써봅시다.

```
npm install axios 
```

---

## 🔧AJAX 사용법 

```
import axios from 'axios'

function App(){
  return (
    <button onClick={()=>{
      axios.get('https://codingapple1.github.io/shop/data2.json').then((결과)=>{
        console.log(결과.data)
      })
      .catch(()=>{
        console.log('실패함')
      })
    }}>버튼</button>
  )
}
```

- 1. axios를 쓰려면 상단에서 import해오고

- 2. axios.get(URL) 이러면 그 URL로 GET요청이 됩니다.

- 3. 데이터 가져온 결과는 결과.data 안에 들어있습니다. 그래서 위의 버튼 누르면 서버에서 가져온 데이터가 콘솔창에 출력됩니다. 

- 4. 인터넷이 안되거나 URL이 이상하면 실패하는데 실패했을 때 실행할 코드는 .catch() 안에 적으면 됩니다.

---

## 🔧AJAX로 서버 요청법

### POST요청 하는 법

```
axios.post('URL', {name : 'kim'})
```

이거 실행하면 서버로 { name : 'kim' } 자료가 전송됩니다. 

완료시 특정 코드를 실행하고 싶으면 이것도 역시 .then() 뒤에 붙이면 됩니다.

### 동시에 AJAX 요청 여러개 날리려면

```
Promise.all( [axios.get('URL1'), axios.get('URL2')] )
```

이러면 URL1, URL2로 GET요청을 동시에 해줍니다.

둘 다 완료시 특정 코드를 실행하고 싶으면 .then() 뒤에 붙이면 됩니다.

---

## ❓JSON 이란?

원래 서버와 문자자료만 주고받을 수 있음 object/array 이런거 못주고받습니다.

근데 방금만해도 array 자료 받아온 것 같은데 그건 어떻게 한거냐면 

object/array 자료에 따옴표를 쳐놓으면 됩니다.

 
```"{"name" : "kim"}"```

이걸 JSON 이라고 합니다.

JSON은 문자 취급을 받기 때문에 서버와 자유롭게 주고받을 수 있습니다.

 

그래서 실제로 결과.data 출력해보면 따옴표쳐진 JSON이 나와야하는데

axios 라이브러리는 JSON -> object/array **변환작업을 자동**으로 해줘서 출력해보면 object/array가 나옵니다. 

---

## ⚠️ajax로 가져온 데이터를 html에 꽂을 때 에러나는경우들. 

1. ajax요청으로 데이터를 가져와서 

2. state에 저장하라고 코드를 짜놨고

3. state를 html에 넣어서 보여달라고 <div> {state.어쩌구} </div> 이렇게 코드 짰습니다.

잘 될 것 같은데 이 상황에서 state가 텅 비어있다고 에러가 나는 경우가 많습니다.

이유는 ajax 요청보다 html 렌더링이 더 빨라서 그럴 수 있습니다. 

state안에 뭐가 들어있으면 보여달라고 if문 같은걸 추가하거나 그러면 됩니다. 
