# 💡 오늘의 학습내용 
- navigate() 함수
- nested routes

---

## ❓ React 프로젝트 폴더구조는?

리액트는 그냥 html 이쁘게 만들어주는 쪼그만한 **라이브러리일** 뿐입니다. 

그래서 여러분이 만들 파일들은 95% 확률로 .js 파일이기 때문에 

비슷한 .js 파일끼리 한 폴더에 묶어놓으면 그냥 그게 좋은 폴더구조입니다. 

컴포넌트 역할하는 js 파일은 components 폴더에 묶고

페이지 역할하는 js 파일은 routes 아니면 pages 폴더에 묶고

자주 쓰는 함수가 들어있는 js 파일은 utils 폴더에 묶고

알아서 필요할 때마다 폴더 만들어쓰십시오 

```
import { Routes, Route, Link, useNavigate, Outlet } from 'react-router-dom'
```

---

## 🔧 페이지 이동기능을 만들고 싶으면 useNavigate().

```
function App(){
  let navigate = useNavigate()
  
  return (
    (생략)
    <button onClick={()=>{ navigate('/detail') }}>이동버튼</button>
  )
}
```

useNavigate() 쓰면 그 자리에 유용한 함수가 남습니다.

페이지 이동시켜주는 함수입니다.

그럼 이제 navigate('/detail') 이런 코드가 실행되면 /detail 페이지로 이동가능합니다.

navigate(2) 숫자넣으면 앞으로가기, 뒤로가기 기능개발도 가능합니다.

-1 넣으면 뒤로 1번 가기

2 넣으면 앞으로 2번 가기 기능입니다. 

## ⚠️404페이지는? 

```
<Route path="*" element={ <div>없는페이지임</div> } />
```

```<Route path="*">``` 하나 맨 밑에 만들어두면 됩니다.

* 경로는 모든 경로를 뜻해서

위에 만들어둔 /detail 이런게 아닌 이상한 페이지 접속시 * 경로로 안내해줍니다. 

---

## 🔧 서브경로 만들 수 있는 nested routes

/about/member로 접속하면 회사멤버 소개하는 페이지

/about/location으로 접속하면 회사위치 소개하는 페이지

```
<Route path="/about/member" element={ <div>멤버들</div> } />
<Route path="/about/location" element={ <div>회사위치</div> } />
```

이렇게 만들어도 되겠지만

```
<Route path="/about" element={ <About/> } >  
  <Route path="member" element={ <div>멤버들</div> } />
  <Route path="location" element={ <div>회사위치</div> } />
</Route>
```

Route>안에 <Route>를 넣을 수 있는데 이걸 Nested routes 라고 부릅니다.

저렇게 쓰면

/about/member로 접속시 ```<About> &<div>멤버들</div>``` 을 보여줍니다.

/about/location으로 접속시 ```<About> & <div>회사위치</div>``` 을 보여줍니다.

진짜 보이는지 <About>컴포넌트 하나 만들어서 확인해봅시다. 

### ⚠️(참고)

실은 위처럼 코드짜면 

/about/member로 접속시 ```<About>안에 <div>멤버들</div>``` 을 보여줍니다.

그래서 <About> 컴포넌트 안에 <div>를 어디다 보여줄지 표기해야 잘보여줍니다. 

```
<Route path="/about" element={ <About/> } >  
  <Route path="member" element={ <div>멤버들</div> } />
  <Route path="location" element={ <div>회사위치</div> } />
</Route>
```

```
function About(){
  return (
    <div>
      <h4>about페이지임</h4>
      <Outlet></Outlet>
    </div>
  )
}
```

위에서 import해온 <Outlet>은 nested routes안의 element들을 어디에 보여줄지 표기하는 곳입니다. 

그래서 이렇게 해두면 

/about/member로 접속시 <Outlet>자리에 아까의 ```<div>``` 박스들이 잘 보입니다. 

그래서 유사한 서브페이지들이 많이 필요하다면 이렇게 만들어도 됩니다.

방금 만든거 보면 페이지 url을 바꿀 때 마다 각각 다른 UI를 보여주는데

이것도 동적인 UI 만드는 방법 중 하나입니다.

그래서 라우터써도 동적인 UI 만들 수 있습니다.

라우터쓰면 뒤로가기 버튼을 이용가능하다는 장점이 있을듯요 



