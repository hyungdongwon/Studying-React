# 💡오늘의 학습내용 
- 전환 애니메이션 주는 법 (transition)

---

## 📋애니메이션을 만드는 step

1. 애니메이션 동작 전 스타일을 담을 className 만들기 

2. 애니메이션 동작 후 스타일을 담을 className 만들기 

3. transition 속성도 추가

4. 원할 때 2번 탈부착

### 1. 애니메이션 동작 전 2. 애니메이션 동작 후 className 만들기 

```
.start {
  opacity : 0
}
.end {
  opacity : 1;
}
```

### 3. transition 추가

```
.start {
  opacity : 0
}
.end {
  opacity : 1;
  transition : opacity 0.5s;
}
```
transition은 "해당 속성이 변할 때 서서히 변경해주세요~" 라는 뜻입니다. 

그럼 이제 원하는 <div> 요소에 start 넣어두고 end 를 탈부착할 때 마다 fade in이 됩니다. 

### 4. 원할 때 end 부착

```
function TabContent({탭}){

  let [fade, setFade] = useState('')

  useEffect(()=>{
    setFade('end')
  }, [탭])

  return (
    <div className={'start ' + fade}>
      { [<div>내용0</div>, <div>내용1</div>, <div>내용2</div>][탭] }
    </div>
  )
}
```

탭이라는게 변할 때 end를 저기 부착하고 싶으면 동적인 UI 만드는 법 떠올리면 됩니다. 

- fade라는 state 하나 만들고 

- state에 따라서 className이 어떻게 보일지 작성하고

- 원할 때 fade를 변경했습니다.

### ⚠️이렇게하면 애니메이션 동작이 되지않음. 왤까?⚠️

end라는 클래스명을 부착하는게 맞긴 맞는데 

실은 떼었다가 붙여야 애니메이션이 보입니다. end를 떼었다가 붙여보셈 

```
function TabContent({탭}){

  let [fade, setFade] = useState('')

  useEffect(()=>{
    setTImeout(()=>{ setFade('end') }, 100)
  return ()=>{
    setFade('')
  }
  }, [탭])

  return (
    <div className={'start ' + fade}>
      { [<div>내용0</div>, <div>내용1</div>, <div>내용2</div>][탭] }
    </div>
  )
}
```

### ❓ setTimeout를 쓰는이유

리액트 18버전 이상부터는 automatic batch 라는 기능이 생겼습니다.

state 변경함수들이 연달아서 여러개 처리되어야한다면 

state 변경함수를 다 처리하고 마지막에 한 번만 재렌더링됩니다. 

그래서 'end' 로 변경하는거랑 ' ' 이걸로 변경하는거랑 약간 시간차를 뒀습니다.

찾아보면 setTimeout 말고 flushSync() 이런거 써도 될 것 같기도 합니다. automatic batching을 막아줍니다.

 

---

