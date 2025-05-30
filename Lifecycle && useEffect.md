# 💡오늘의 학습내용 
- Lifecycle
- useEffect

## 📖컴포넌트의 인생 

컴포넌트는 Lifecycle이라는 개념이 있습니다.

컴포넌트도 인생이 있다

![image](https://github.com/user-attachments/assets/5cef9601-f427-4590-8ec3-ad33a4cee577)

컴포넌트는

1. 생성이 될 수도 있고 (전문용어로 mount)

2. 재렌더링이 될 수도 있고 (전문용어로 update)

3. 삭제가 될 수도 있습니다. (전문용어로 unmount)

 컴포넌트의 인생을 배우는 이유는 **컴포넌트 인생 중간중간에 간섭할 수 있기 때문**

![image](https://github.com/user-attachments/assets/850fbf0f-32a7-4d73-ba3e-731849c3731a)

갈고리를 달아서 코드를 넣어주면 됩니다.

그럼 진짜 페이지 장착시, 업데이트시, 제거시 코드실행가능 

갈고리는 영어로 hook이라고 합니다. 

그래서 저걸 Lifecycle hook 이라고 부릅니다. 

---

## 🔧React에서 Lifecycle hook 쓰는 법

```
import {useState, useEffect} from 'react';

function Detail(){

  useEffect(()=>{
    //여기적은 코드는 컴포넌트 로드 & 업데이트 마다 실행됨
    console.log('안녕')
  });
  
  return (생략)
}
```

상단에서 useEffect import해오고 

콜백함수 추가해서 안에 코드 적으면 이제 그 코드는 컴포넌트가 mount & update시 실행됩니다.

그래서 이게 Lifecycle hook 입니다. 

---


## ❓useEffect의 사용목적❓

⚠️ **useEffect 안에 적은 코드는 html 렌더링 이후에 동작합니다.** ⚠️

코드의 실행 시점을 조절할 수 있기 때문에

조금이라도 html 렌더링이 빠른 사이트를 원하면 오래걸리는 것들은 useEffect 안에 넣어보길 바랍니다. 

이 함수를 useEffect라고 작명한 이유도 알 수 있는데 

함수안에 이것저것 코드짤 때 

함수의 핵심기능 외에 쓸데없는 기능들을 프로그래밍 용어로 side effect라고 부릅니다.

그래서 useEffect도 거기서 따온건데

컴포넌트의 핵심 기능은 html 렌더링이라 

그거 외의 쓸데없는 기능들은 useEffect 안에 적으라는 소리입니다. 

오래걸리는 반복연산, 서버에서 데이터가져오는 작업, 타이머다는거 

이런건 useEffect 안에 많이 적습니다.

---

## 🔧useEffect에 넣을 수 있는 실행조건 

```
useEffect(()=>{ 실행할코드 }, [count])

```


useEffect()의 둘째 파라미터로 [ ] 를 넣을 수 있는데

거기에 변수나 state같은 것들을 넣을 수 있습니다.

그렇게 하면 [ ]에 있는 변수나 state 가 변할 때만 useEffect 안의 코드를 실행해줍니다.

**(참고) [ ] 안에 state 여러개 넣을 수 있음**

---

```
useEffect(()=>{ 실행할코드 }, [])
```


아무것도 안넣으면 컴포넌트 mount시 (로드시) 1회 실행하고 영영 실행해주지 않습니다.

---

## 🔧clean up function

useEffect 동작하기 전에 특정코드를 실행하고 싶으면

return ()=>{} 안에 넣을 수 있습니다. 

```
useEffect(()=>{ 
  그 다음 실행됨 
  return ()=>{
    여기있는게 먼저실행됨
  }
}, [count])

```

### 📜 사용EX)

예를 들면 숙제로 했던 setTimeout 타이머인데

setTimeout() 쓸 때마다 브라우저 안에 타이머가 하나 생깁니다.

근데 useEffect 안에 썼기 때문에 컴포넌트가 mount 될 때 마다 실행됩니다. 

그럼 잘못 코드를 짜면 타이머가 100개 1000개 생길 수도 있겠군요.

나중에 그런 버그를 방지하고 싶으면useEffect에서 타이머 만들기 전에 기존 타이머를 싹 제거하라고 코드를 짜면 되는데

그런거 짤 때 return ()=>{} 안에 짜면 됩니다. 







