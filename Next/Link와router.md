# Link 태그와 router의 차이점

Next.js 를 사용하며 다른 분들의 코드를 보면 router.push 로 경로이동을 하는 코드도 보고 Link 태그로 경로 이동을하는 코드를 보며 뭔가 다른점이 있을것이라고 생각하며 구글에 검색했다.

## 1. Route

```jsx
<button onClick={()=> router.push('/about')}>어바웃으로 이동</button>
```

router.push를 사용하려면 일단 useRouter 객체를 import 해주어야 한다.
router를 사용하면 동적라우팅이 가능해진다.
즉 자기가 알아서 페이지를 할당해주며 보여주는 것이다.
router.push 는 javascript의 window객체 안에있는
window.location과 비슷하게 동작 함으로
a 태그를 생성하지 않기에 SEO에 불리하다.
대부분 onClick 이벤트 핸들러와 같이 사용 된다.

## 2. Link

```jsx
<Link href={'/about'}>
	어바웃으로 이동
</Link>
```

Link 태그는 react 의 router-dom 객체에서도 사용을 해본 적이 있어서 사용함에 있어서 어색하지 않았다.
<Link>태그의 동작원리는 <a> 태그를 생성하기 때문에 웹사이트가 크롤링 되어서 SEO에 유리하다.
또한 페이지를 다시 로드하지 않기에 SPA 동작처럼 보이게 만든다.