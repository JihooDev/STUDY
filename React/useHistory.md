# useHistory

useHistory는 react-router-dom 안에 있는 객체이다. react-router-dom@5 버전까지 가능하며 react-router-dom@6 버전부터는 useNavigate 객체로 변경되었다.

## 사용법

```jsx
const history = useHistory();
```

변수에 useHistory를 추가해서 사용할 수 있다.

### 1. push

```jsx
<button onClick={()=> history.push('/about')}>어바웃으로</button>
```

push는 페이지를 이동 할 수 있다.
go 라는 것도 똑같이 페이지를 이동하지만 두개의 차이점은 push는 prop을 전달 할 수 있다.
또한 히스토리 스택에 새 항목을 푸시한다.

### 2. go

```jsx
<button onClick={()=> history.go('/about')}>어바웃으로</button>
```

go 는 push와  비슷하게 사용된다.
히스토리 스택의 포인터를 n 항목 별로 이동한다.
페이지를 이동할 때 굉장히 많이 사용된다.

### 3. goBack

```jsx
<button onClick={()=> history.goBack(-1)}>뒤로가기</button>
```

뒤로가기 기능이라고 생각하면 될거 같다.
웹 브라우저 마다 뒤로가기 기능은 항상 존재하지만 대 부분 왼쪽 위편에 존재한다.
사용자가 예를 들어 웹 쇼핑을 하고 디테일 페이지에 들어왔을 때 눈에 잘 보이고 마우스 이동이 적은 위치에 이 버튼을 배치하면 ux 부분에서도 큰 도움이 될거 같다.

### 4. replace

```jsx
<button onClick={()=> history.replace('/payment')}>결제하기</button>
```

replace 함수는 히스토리 스택에 현재 항목을 추가하는게 아닌 대체를 한다.
프로젝트를 할 때 한번 사용해 봤는데 굉장히 유용하게 사용할 때가 많았다.
스택을 대체해야 하는 순간은 프로젝트를 하다보면 한번씩은 생긴다.
예를 들어 한번만 신청할 수 있는 이벤트 페이지에서 사용자가 양식을 입력하고 제출 버튼을 눌렀을 때 뒤로가기를 눌렀을 때 다시는 그 페이지에 들어올 수 없어야 한다.
현재는 react-router-dom@6 버전을 많이 사용함으로 요즘은 useNavigate를 주로 사용한다.
5버전과 6버전의 차이점은 나중에 정리해보겠다.