# 💡오늘의 학습내용
- React-bootstrap 사용법 

---

## 🔧React-Bootstrap 라이브러리를 설치해서 이용하기

리액트에 맞게 변형한 React-Bootstrap을 설치합시다.

react bootstrap이라고 구글 검색하면 맨 처음에 나오는 사이트로 들어갑시다. 

📜 설치1.에디터에서 터미널켜고 

```npm install react-bootstrap bootstrap```

📜 설치 2. 어떤 스타일은 Bootstrap CSS 파일을 요구하는 경우가 있습니다.

그래서 그냥 그 사이트에 있는 CSS 파일을 index.html 파일의 <head> 태그 안에 복붙해주시면 됩니다. 

![image](https://github.com/user-attachments/assets/f5f46a89-e100-4292-aeb7-5ac37992d8e5)

사이트 내에 이걸 찾아 복붙하시면 됩니다. 아까랑 같은 페이지의 CSS라는 항목에 있을듯

길어서 싫으면 App.js 에 import 'bootstrap/dist/css/bootstrap.min.css 

---

## 🔧React-Bootstrap 사용법

```
import {Button} from 'react-bootstrap'

function App(){
  return (
    <div>
      <Button variant="primary">Primary</Button>
    </div>
  )
}
```

근데 다만 복사붙여넣기할 때 대문자로 시작하는 컴포넌트이름은 상단에 저렇게 import 해와야합니다. 

 
