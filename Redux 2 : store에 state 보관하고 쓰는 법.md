# 💡오늘의 학습내용 
- Redux store에 state 보관하는 법

## 🔧Redux store에 state 보관하는 법

step 1. createSlice( ) 로 state 만들고

step 2. configureStore( ) 안에 등록하면 됩니다.

```
import { configureStore, createSlice } from '@reduxjs/toolkit'

let user = createSlice({
  name : 'user',
  initialState : 'kim'
})

export default configureStore({
  reducer: {
    user : user.reducer
  }
}) 
```

1. createSlice( ) 상단에서 import 해온 다음에 

**{ name : 'state이름', initialState : 'state값' } 이거 넣으면 state 하나 생성가능합니다.**

(createSlice( ) 는 useState( ) 와 용도가 비슷하다고 보면 됩니다)

 

2. state 등록은 configureStore( ) 안에 하면 됩니다.

**{ 작명 : createSlice만든거.reducer } 이러면 등록 끝입니다.**

여기 등록한 state는 모든 컴포넌트가 자유롭게 사용가능합니다. 

---


## 🔧Redux store에 있던 state 가져다쓰는 법

```
import { useSelector } from "react-redux"

function Cart(){
  let a = useSelector((state) => { return state } )
  console.log(a)

  return (생략)
}
```

아무 컴포넌트에서 useSelector((state) => { return state } ) 쓰면 store에 있던 모든 state가 그 자리에 남습니다. 



