# Spread 문법

Spread 문법은 javaScript 에서 자주 사용하는 유용한 문법이다.

React에서 매우 유용하게 사용했던 친구 중 하나이다.
나머지 매개변수 기능을 반대로 제공해주는 친구라고 생각하면 편할 것이다.

나는 미리 사용을 해봤는데 주로 배열이나 객체를 펼칠 때 사용했다.

객체를 펼친다 라는 건 무슨 말인지 처음에는 의아했다. 

코드를 한번 보면 확실하게 이해가 갈 것이다.

```jsx
// Spread 연산자 사용
let arr2 = [1, 2, 3, 4, 5];

console.log(...arr2);

// result = 1 2 3 4 5
```

말 그대로 펼쳐준다.

Spread 문법은 이터러블 객체에만 사용할 수 있다.

또한 아주 유용한 예제가 있다.

```jsx
// Spread 1 
const cookie = { 
    base: "cookie", 
    madeIn: "korea" 
  }; 
   
  const chocoCookie = { 
    ...cookie, 
    toping: "choco" 
  }; 

  console.log(chocoCookie); 
   
// Spread 2
  const man = ["손흥민", "박지성", "이강인"]; 
  const woman = ["미연", "우기", "소연"]; 
   
  const allPeople = [...man, ...woman]; 
  console.log(allPeople);
```

### Spread1 (필요한 부분만 활용해서 객체를 간단하게 복사)

1. cookie 라는 곳에 중복될거같은 key와 value를 적어준다.
2. chocoCookie 도 base와 madeIn을 적어줘야하지만 중복되기 때문에 cookie를 펼쳐주며 코드의 가독성을 높혀준다.

### Spread2 (배열을 복사해서 하나의 배열에 모으기)

1. 남자와 여자를 따로 구분 해놓는다.
2. 모든 사람의 list가 필요하면 allPeople이라는 배열을 만들어서 넣어준다.