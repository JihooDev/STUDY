# async & await

ES8 에서는 제너레이터보다 간단하고 가독성 좋게 비동기 처리를 동기처럼 동작하도록 구현할 수 있는 async 와 await이 도입 되었다.

Promise 의 후속 처리 메서드 없이 마치 동기 처럼 Promise가 처리 결과를 반홚하도록 구현 할 수 있다.

## async 함수

function 앞에 async를 적어주면 함수는 Promise 객체를 생성했을 때 처럼 Promise 를 반환한다.

Promise 가 아닌 값을 반환 하더라도 이행 상태의 Promise로 감싸주면 그 값을 감싸서 이행 된 Promise로 반환한다.

```jsx
async function f() {
  return 1;
}

f().then(alert); // 1
```

Promise를 반환 받아도 가능하지만 결과는 똑같다.

결론으로 async 가 앞에 붙은 함수는 반드시 Promise를 반환하고 Promise가 아닌 값 들은 내부적으로 Promise로 감싸서 반환 해준다.

명시적으로 Promise를 반환하지 않더라고 async 함수는 암묵적으로 반환값을 resolve 하는 Promise를 반환한다.

## await 키워드

await 키워드는 반드시 async 함수 내부에서 사용해야 한다.

비동기 처리가 수행된 상태(settled) 가 될 때 까지 대기하다가 완료되면 resolve한 처리결과를 반환한다. 

Promise가 settled 상태가 되면 reesolve한 처리 결과가 res 변수에 할당된다.

이 처럼 await 키워드는 다음 실행을 일시 중지시켰다가 상태에 따라서 다시 재개된다.

```jsx
async function foo() {
  let asyncTest = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("완료");
    }, 2000);
  });

  let result = await asyncTest; //

  console.log(result);
}

foo();

// 결과 : 완료
```

위의 코드처럼 result 라는 변수는 Promise 처리가 끝날 때 까지 대기하고 있다가 asyncTest 함수를 가진다. 

테스트를 해보려고 await을 지워보고 실행 시키니 pending(대기상태) 를 출력한다.

아직 비동기처리가 시작되기 전 이여서 값을 가지고 있지 않다.

### ** 주의 **

- async 함수가 아닌 일반 함수에서 await을 사용하면 *Syntax error* 가 출력된다

## 정리

function 앞에 async 키워드를 정의하면 두가지의 효과가 있다.

- 언제나 Promise를 반환하는 함수가 됨
- await을 사용할 수 있음

Promise 앞에 await을 붙히면 자바스크립트는 끝날 때 까지 대기한다.

- 처리가 완료되면 Promise의 result를 반환한다.

# 참고자료

---

[](https://ko.javascript.info/async-await)