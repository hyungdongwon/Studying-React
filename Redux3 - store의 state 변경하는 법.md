# 💡오늘의 학습내용 
- store의 state 변경하는 법

---

## ❓Redux 사용이유

![image](https://github.com/user-attachments/assets/d03c8354-5bb4-4534-aae5-782c82a606d7)

컴포넌트 100개에서 직접 'kim' 이라는 state 변경하다가

갑자기 'kim'이 123이 되어버리는 버그가 발생하면

범인 찾으려고 컴포넌트 100개를 다 뒤져야합니다.

![image](https://github.com/user-attachments/assets/ad97b0ba-bae0-4d9a-8c0b-44abcbf2427a)

근데 state 수정함수를 store.js에 미리 만들어두고

컴포넌트는 그거 실행해달라고 부탁만 하는 식으로 코드를 짜놓으면

'kim'이 123이 되어버리는 버그가 발생했을 때 범인찾기가 수월합니다.

---


## 🔧store의 state 변경하는 법 

Redux의 state를 변경하고 싶으면 변경하는 법이 따로 있습니다. 

1. store.js에 state변경해주는 함수부터 만들고

2. export 해두고

3. 필요할 때 import 해서 쓰면 되는데 dispatch() 로 감싸서 써야합니다.

state 수정해주는 함수부터 store.js에 만들어두고

그걸 컴포넌트에서 원할 때 실행하는 식으로 코드를 짭니다. 

```
let user = createSlice({
  name : 'user',
  initialState : 'kim',
  reducers : {
    changeName(state){
      return 'john ' + state
    }
  }
}) 
```
### 📋1. store.js 안에 state 수정해주는 함수부터 만듭니다.
 
slice 안에 reducers : { } 열고 거기 안에 함수 만들면 됩니다.

- 함수 작명 맘대로 합니다.

- 파라미터 하나 작명하면 그건 기존 state가 됩니다.

- return 우측에 새로운 state 입력하면 그걸로 기존 state를 갈아치워줍니다.

### 📋2. 다른 곳에서 쓰기좋게 export 해둡니다.

```
export let { changeName } = user.actions 
```

이런 코드 store.js 밑에 추가하면 됩니다.

slice이름.actions 라고 적으면 state 변경함수가 전부 그 자리에 출력됩니다.

그걸 변수에 저장했다가 export 하라는 뜻일 뿐임 

### 📋3. 원할 때 import 해서 사용합니다. 근데 dispatch() 로 감싸서 써야함 

```
(Cart.js)

import { useDispatch, useSelector } from "react-redux"
import { changeName } from "./../store.js"

(생략) 

<button onClick={()=>{
  dispatch(changeName())
}}>버튼임</button> 
```

- store.js에서 원하는 state변경함수 가져오면 되고 

- useDispatch 라는 것도 라이브러리에서 가져옵니다.

- 그리고 dispatch( state변경함수() ) 이렇게 감싸서 실행하면 state 진짜로 변경됩니다.

- dispatch로 꼭 감싸야 실행됩니다.

 
