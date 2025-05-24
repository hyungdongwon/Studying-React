#💡오늘의 학습내용 
- React 에서 image파일 넣는법
---

## 🔧html 안에서 src 폴더의 이미지를 넣고 싶으면 
```
import bg from './bg.png'

function App(){
  return (
    <div>
      <div className="main-bg" style={{ backgroundImage : 'url(' + bg + ')' }}></div>
    </div>
  )
}
```

html 안에서 이미지를 집어넣고 싶으면 

이미지를 import 해오고 사용해야합니다. 

1. import 작명 from './이미지경로' 한 다음에

2. 이미지경로가 필요한 곳에서 작명한걸 사용하면 됩니다. 

```<img>``` 태그 쓰고싶으면 ```<img src={bg}/>``` 이렇게 써도 보입니다. 

귀찮으면 css파일을 활용.

## 💫public 폴더의 용도 

여러가지 소스코드는 src 폴더에 보관하면 되는데 

이미지같은 static 파일의 경우 public 폴더에 보관해도 됩니다.

리액트로 개발을 끝내면 build 작업이라는걸 하는데 

지금까지 짰던 코드를 한 파일로 압축해주는 작업입니다. 

src 폴더에 있던 코드와 파일은 다 압축이 되는데 public 폴더에 있는 것들은 그대로 보존해줍니다. 

그래서 형태를 보존하고 싶은 파일은 public 폴더에 넣으면 되는데 js 파일은 그럴 일은 거의 없고 

이미지, txt, json 등 수정이 필요없는 static 파일들의 경우엔 public 폴더에 보관해도 상관없습니다.

---

## 🔧public 폴더에 있는 이미지 사용할 땐

```
<img src="/logo192.png" /> 
```

그냥 /이미지경로 사용하면 됩니다. 

그래서 페이지에 이미지 100장을 넣어야하는 경우 

public 폴더에 밀어넣으면 import 100번 안해도 되니 편리합니다. 

css 파일에서도 /이미지경로 사용하면 됩니다.

### 🔖권장되는 방식

```
<img src={process.env.PUBLIC_URL + '/logo192.png'} /> 
```

리액트로 만든 html 페이지를 배포할 때

codingapple.com 경로에 배포하면 아무런 문제가 없지만

codingapple.com/어쩌구/ 경로에 배포하면

/logo192.png 이렇게 쓰면 파일을 찾을 수 없다고 나올 수도 있습니다. 

그래서 /어쩌구/ 를 뜻하는 process.env.PUBLIC_URL 이것도 더해주면 된다고 하는군요. 

---



 
