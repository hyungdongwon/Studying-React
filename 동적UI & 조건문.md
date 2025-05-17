## 💡오늘 학습한 내용
- 리액트에서 동적인 UI만드는법

---
## ❓ 동적UI란

유저가 조작시 형태가 바뀌는

모달창 탭 서브메뉴 툴팁 경고문 등 그런 UI들을 의미합니다. 

---

## 📋리액트에서 동적인 UI 만드는 step

### 🔧 1. html css로 미리 UI 디자인을 다 해놓고

---

### 🔧 2. UI의 현재 상태를 state로 저장

``` let [modal, setModal] = useState(false); ``` 

영어로 작명시 state변경함수는 set을 앞에 붙이는게 관습입니다. 

state에 무슨 자료를 넣어야되냐면 정말 맘대로 하면 됩니다.

그냥 현재 모달창의 상태만 표현할 수 있으면 됩니다.

모달창은 열림/닫힘 이 두개 상태밖에 없기 때문에 그거 2종류만 표현할 수 있는 자료형이면 됩니다. 

---

### 🔧 3. state에 따라서 UI가 어떻게 보일지 조건문 등으로 작성

```
EX)코드

function App (){

  let [modal, setModal] = useState(false);
  return (
    <div className="app">
      (생략)
      {
        modal == true ? <Modal></Modal> : null
      }
    </div>
  )
}
```

---

## 📜 JSX문법 - 조건문 사용

조건문은 if / else 문법을 쓰면 되는데 

JSX 안에서는 if else 문법을 바로 사용할 수 없습니다.

하지만 if 문법 대신 삼항연산자라는건 JSX 중괄호 안에서 사용가능합니다.


```
조건식 ? 조건식 참일 때 실행할 코드 : 조건식 거짓일 때 실행할 코드

3 > 1 ? console.log('맞음') : console.log('아님') 
```

예를 들어 이렇게 쓰면 3 > 1 이게 참이기 때문에 '맞음'이 출력됩니다. 

