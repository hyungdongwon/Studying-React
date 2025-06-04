# 💡오늘의 학습내용 
- Redux Toolkit 설치

---

## ❓Redux 쓰는 이유

**Redux는 props 없이 state를 공유할 수 있게 도와주는 라이브러리입니다.** 

<img width="364" alt="캡처" src="https://github.com/user-attachments/assets/a05ddea7-b1ff-4397-a550-dd1f0004b498" />

이거 설치하면 **js 파일 하나에 state들을 보관할 수 있는데**

그걸 모든 컴포넌트가 직접 꺼내쓸 수 있습니다. 

그래서 사이트가 커지면 쓸 수 밖에 없어서 

개발자 구인시에도 redux같은 라이브러리 숙련도를 대부분 요구합니다. 

---

## 🔧Redux 설치방법. 

```
npm install @reduxjs/toolkit@1.8.1 react-redux 
```

redux toolkit이라는 라이브러리를 설치할 건데 redux의 개선버전이라고 보면 됩니다. 문법이 좀 더 쉬워짐 

---

## 🔧Redux 셋팅

```
import { configureStore } from '@reduxjs/toolkit'

export default configureStore({
  reducer: { }
}) 

```

1. 아무데나 store.js 파일을 만들어서 위 코드를 복붙해줍니다. 

아까 말했던 state들을 보관하는 파일입니다. 

```
import { Provider } from "react-redux";
import store from './store.js'

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <Provider store={store}>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </Provider>
  </React.StrictMode>
); 
```
2. index.js 또는 main.jsx 파일가서 Provider 라는 컴포넌트와 아까 작성한 파일을 import 해옵니다. 

그리고 밑에 ```<Provider store={import해온거}>``` 이걸로 ```<App/>``` 을 감싸면 됩니다. 

그럼 이제 ```<App>``` 과 그 모든 자식컴포넌트들은 store.js에 있던 state를 맘대로 꺼내쓸 수 있습니다.








