# 💡오늘의 학습내용 
- 리액트에서 자주쓰는 if문 작성패턴 5개

---

## 🔧 1. 컴포넌트 안에서 쓰는 if/else

```
function Component() {
  if ( true ) {
    return <p>참이면 보여줄 HTML</p>;
  } else {
    return null;
  }
} 
```

return () 안의 JSX 내에서는 사용 불가능합니다.

<div> if (어쩌구) {저쩌구} </div> 이게 안된다는 소리입니다.

그래서 보통 return + JSX 전체를 퉤 뱉는 if문을 작성해서 사용합니다. 

---

## 🔧2. JSX안에서 쓰는 삼항연산자 

```
function Component() {
  return (
    <div>
      {
        1 === 1
        ? <p>참이면 보여줄 HTML</p>
        : null
      }
    </div>
  )
} 
```

삼항연산자는 그냥 if와는 다르게 JSX 안에서도 실행가능하며 조건을 간단히 주고 싶을 때 사용합니다.

```
function Component() {
  return (
    <div>
      {
        1 === 1
        ? <p>참이면 보여줄 HTML</p>
        : ( 2 === 2 
            ? <p>안녕</p> 
            : <p>반갑</p> 
          )
      }
    </div>
  )
} 
```

삼항연산자는 중첩 사용도 됩니다. 

---

## 🔧3. && 연산자로 if 역할 대신하기

```
function Component() {
  return (
    <div>
      { 1 === 1 && <p>참이면 보여줄 HTML</p> }
    </div>
  )
}
```

html 조건부로 보여줄 때 이런 경우가 많습니다.

"만약에 이 변수가 참이면 <p></p>를 이 자리에 뱉고 참이 아니면 null 뱉고"

UI만들 때 이런거 매우 자주 씁니다. 

이걸 조금 더 쉽게 축약할 수 있습니다. && 연산자를 쓰면 됩니다.

---

## 🔧4. switch / case 조건문

```
function Component2(){
  var user = 'seller';
  switch (user){
    case 'seller' :
      return <h4>판매자 로그인</h4>
    case 'customer' :
      return <h4>구매자 로그인</h4>
    default : 
      return <h4>그냥 로그인</h4>
  }
}
```

1. switch (검사할변수){} 이거부터 작성하고

2. 그 안에 case 검사할변수가이거랑일치하냐 : 를 넣어줍니다.

3. 그래서 이게 일치하면 case : 밑에 있는 코드를 실행해줍니다.

4. default : 는 그냥 맨 마지막에 쓰는 else문과 동일합니다.

 
장점은 if문 연달아쓸 때 코드가 약간 줄어들 수 있는데

조건식란에서 변수하나만 검사할 수 있다는게 단점입니다. 

---

## 🔧5. object/array 자료형 응용 

```
function Component() {
  var 현재상태 = 'info';
  return (
    <div>
      {
        { 
           info : <p>상품정보</p>,
           shipping : <p>배송관련</p>,
           refund : <p>환불약관</p>
        }[현재상태]
      }

    </div>
  )
} 
```

그럼 이제 현재상태라는 변수의 값에 따라서 원하는 HTML을 보여줄 수 있습니다.

만약에 var 현재상태가 'info'면 info 항목에 저장된 <p>태그가 보여질 것이고

만약에 var 현재상태가 'refund'면 refund 항목에 저장된 <p>태그가 보여지겠죠? 
