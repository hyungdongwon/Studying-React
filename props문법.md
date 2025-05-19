# 💡 오늘 학습 내용 
- 부모의 state 가져다쓰고 싶을 때는 props

## ❓props문법을 쓰는 이유

자바스크립트에선 다른 함수에 있는 변수를 마음대로 가져다쓸 수 없습니다. 

![image](https://github.com/user-attachments/assets/3df12e1b-88a7-4222-be72-0b4c3e5d3ad2)

근데 컴포넌트 2개가 부모/자식 관계인 경우엔 가능합니다. 

(다른 컴포넌트 안에 있는 컴포넌트를 자식컴포넌트라고 부릅니다)


![image](https://github.com/user-attachments/assets/9d901148-c3c8-45f5-948d-76512cdf7cf3)

부모 컴포넌트의 state를 자식 컴포넌트로 전송해줄 수 있습니다. 그럼 자식도 사용가능

전송시엔 props라는 문법을 사용합니다. 

---

## 🔧props로 부모 -> 자식 state 전송하는 법 

2개의 step을 따라주시면 됩니다.

1. 자식컴포넌트 사용하는 곳에 가서 <자식컴포넌트 작명={state이름} /> 

2. 자식컴포넌트 만드는 function으로 가서 props라는 파라미터 등록 후 props.작명 사용

하지만 이론만 설명하면 이해가 되지 않으니 예시를 보아야합니다.

---

```
function App (){
  let [글제목, 글제목변경] = useState(['남자코트 추천', '강남 우동맛집', '파이썬독학']);
  return (
    <div>
      <Modal 글제목={글제목}></Modal>
    </div>
  )
}

function Modal(props){
  return (
    <div className="modal">
      <h4>{ props.글제목[0] }</h4>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  )
}
```

1. 자식컴포넌트 사용하는 곳에 가서 <자식컴포넌트 작명={state이름} /> 

2. 자식컴포넌트 만드는 곳에 가서 props라는 파라미터 등록 후 props.작명 사용하면 됩니다.

### 🔖참고사항 

props는 <Modal 이런거={이런거}  저런거={저런거}> 이렇게 10개 100개 1000개 무한히 전송이 가능합니다.

꼭 state만 전송할 수 있는건 아닙니다. 

<Modal 글제목={변수명}> 일반 변수, 함수 전송도 가능하고 

<Modal 글제목="강남우동맛집"> 일반 문자전송은 중괄호 없이 이렇게 해도 됩니다.

![image](https://github.com/user-attachments/assets/9e213c6b-f4a7-4a52-bedd-ff37422174a9)

▲ 자식 → 부모 패륜방향 전송은 불가능합니다.

![image](https://github.com/user-attachments/assets/ad9f2f6d-0509-472c-8158-e29d825036bc)

▲ 옆집 컴포넌트로의 불륜전송도 불가능합니다. 


---



