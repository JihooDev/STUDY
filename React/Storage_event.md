### Storage Event

---

addEventListener 객체에 대해서 공부를 할 때 이 storage 이벤트는 중요하게 생각하지 않았다.

storage 이벤트는 이번에 React 프로젝트를 하며 엄청 큰 도움을 주어서 정리하게 되었다🙂

localstorage 의 값이 들어올 때 상태(state) 를 변경시켜야 했는데 그 상태를 변경시키는 명분이 없어서 애를 많이 먹었다😟

Storage 이벤트는

localStorage에 값이 설정될 때마다 동일한 출처에서 `storage`다른 모든 항목에 대해 이벤트가 전달 된다.

그래서 내가 쓴 코드는 이러하다.

```jsx
useEffect(()=>{
	window.addEventListener('storage',function(){
		console.log('변경!')
	})
},[])
```

`sessionStorage에게도 동일하게 적용되며 useEffect와 사용하면 가끔은 유용하게 사용할 수 있다고 생각한다.`

React가 버전을 업데이트 할 때 의존성배열에 localStorage가 변경되었을 때만 실행하게 할 수 있도록 만들어 주었으면 좋겠다…