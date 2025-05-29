# 💡오늘의 학습내용
- styled-components 라이브러리 사용법

---

## ❓styled-components 를 왜사용할까?

컴포넌트가 많은 경우 스타일링을 하다보면 불편함이 생기는데

1. class 만들어놓은걸 까먹고 중복해서 또 만들거나

2. 갑자기 다른 이상한 컴포넌트에 원하지않는 스타일이 적용되거나

3. CSS 파일이 너무 길어져서 수정이 어렵거나

이런 경우가 있다.

그래서 스타일을 바로 입혀서 컴포넌트를 만들어버릴 수도 있는데

styled-components 라는 인기 라이브러리를 설치하여 이용하면 된다.

### ⭐CSS 파일도 오염방지 가능⭐

App.css 파일을 만들어서 App.js에서 import해서 쓴다고 해도 

거기 적은 클래스명들은 Detail.js까지 사용가능. (오염됨)

프로젝트 사이즈가 작을 땐 편리하겠지만 사이즈가 커지면 관리하기 힘듬. 
 
그럴 땐 styled-components 써도 되지만 그냥 CSS파일에서도 다른 JS 파일에 간섭하지 않는 **'모듈화'** 기능을 제공하는데

**컴포넌트명.module.css**

이렇게 CSS 파일을 작명하면 됩니다.

그리고 **컴포넌트명.js 파일에서 import 해서 쓰면 그 스타일들은 컴포넌트명.js 파일에만 적용.**

---

## 🔧셋팅방법

```
npm install styled-components
```

```
import styled from 'styled-components'
```

사용하고 싶은 컴포넌트 맨위에 이런걸 import 해와야합니다.

---

## 🔧styled-components 기본적인 사용법 

```
import styled from 'styled-components';

let Box = styled.div`
  padding : 20px;
  color : grey
`;
let YellowBtn = styled.button`
  background : yellow;
  color : black;
  padding : 10px;
`;

function Detail(){
  return (
    <div>
      <Box>
        <YellowBtn>버튼임</YellowBtn>
      </Box>
    </div>
  )
}
```

1. <div>를 하나 만들고 싶으면 저렇게 styled.div 라는걸 사용하면 된다.

```<p>``` 만들려면 styled.p 이런 식임 

2. 오른쪽에 `` backtick 기호를 이용해서 CSS 스타일을 넣을 수 있다. 

3. 그럼 그 자리에 컴포넌트를 남겨주는데 변수에 저장해서 쓰면 된다.

---

##⭐ 추가 문법 : props로 재활용가능

```
import styled from 'styled-components';

let YellowBtn = styled.button`
  background : ${ props => props.bg };
  color : black;
  padding : 10px;
`;

function Detail(){
  return (
    <div>
        <YellowBtn bg="orange">오렌지색 버튼임</YellowBtn>
        <YellowBtn bg="blue">파란색 버튼임</YellowBtn>
    </div>
  )
}
```
${ props => props.bg } 이게 styled-components 에서의 props 뚫는 문법.

bg부분에 자유롭게 작명하면되고

컴포넌트 쓸 때 bg라는 props를 입력가능.

---

## 👍장단점👎

👍장점1. CSS 파일 오픈할 필요없이 JS 파일에서 바로 스타일넣을 수 있음.

👍장점2. 여기 적은 스타일이 다른 JS 파일로 오염되지 않습니다. 원래 그냥 CSS파일은 오염됨.

👍장점3. 페이지 로딩시간 단축됩니다. 왜냐면 저기 적은 스타일은 html 페이지의 <style>태그에 넣어줘서 그럼. 

---

👎단점1. JS 파일이 매우 복잡해집니다.

그리고 이 컴포넌트가 styled 인지 아니면 일반 컴포넌트인지 구분도 어렵다.


 
👎단점2. JS 파일 간 중복 디자인이 많이 필요하면?

다른 파일에서 스타일 넣은 것들 import 해와서 쓰면 됩니다.

근데 그럼 CSS파일 쓰는거랑 차이가 없을 수도?


 
👎단점3. CSS 담당하는 디자이너가 있다면 협업시 불편할텐데 

그 사람이 styled-components 문법을 모른다면 

그 사람이 CSS로 짠걸 styled-components 문법으로 다시 바꾸거나 그런 작업이 필요.
 

