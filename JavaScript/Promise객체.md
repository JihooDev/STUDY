# Promise 객체

비동기 처리를 조금 더 편하게 처리 할 수 있는 ES6에서 도입된 기능이다.

**Promise 는 자바스크립트 비동기 처리에 사용**되는 객체이다.

## Promise 가 필요한 이유?

주로 서버에서 받아온 데이터를 화면에 표시할 때 사용된다.

예를 들어 요청한 데이터를 다 받아오기도 전에 화면에 출력하려면 에러가 발생하거나 빈 화면을 출력한다. 이러한 문제점을 해결하기 위한 것이 Promise 이다. 

이전에는 비동기 처리를 하기 위해 콜백함수로 처리를 해야했다.

하지만 콜백함수로 처리하게되는 코드가 많으면 콜백지옥이 발생하게 된다.

콜백 지옥이란 콜백함수안의 또 콜백함수 그리고 또 콜백함수 이렇게 계속 파고 드는 것을 말한다.

콜백 지옥(콜백헬) 은 가독성을 나쁘게 하며 실수를 유발하는 원인이 된다

콜백지옥의 간단한 예시 코드이다.

```jsx
step1(function (value1) {
    step2(function (value2) {
        step3(function (value3) {
            step4(function (value4) {
                step5(function (value5) {
                    step6(function (value6) {
                        // Do something with value6
                    });
                });
            });
        });
    });
});
```

사실 Promise를 조금 더 편하게 사용하기 위해 async 와 await 이 나왔지만

먼저 Promise를 이해하고 넘어가겠다.

## Promise 활용

### Promise 객체의 생성 방법

```jsx
const myPromise = new Promise((resolve,reject) ={
	if(3===3){
    resolve("성공!")
  } else {
    reject("실패")
  }
})
```

Promise 생성자 함수를 new 연산자와 함께 호출하면 Promise 객체를 생성한다.

Promise는 두가지의 파라미터를 전달 받는다.

resolve와 reject를 받는다.

두개의 파라미터를 이해하려면 비동기 작업이 가질수 있는 3가지의 상태를 이해 하여야 한다.

**pending : 대기상태 (이행하지도, 거부하지도 않은 초기상태)**

**fulfilled : 이행상태 (연산이 성공적으로 수행 됨)**

**rejected : 실패상태(연산이 실패 함)**

이 세가지는 비동기작업에서 기본적으로 알고 있어야하는 3가지의 상태이다.

그렇다면 resolve와 reject는 무엇일까?

pending에서 fulfilled로 넘어가면 그 결과는 성공이다.

이러한 과정을 resolve라고 부른다.

그렇다면 pending 에서 rejected로 넘어가면 당연히 결과는 실패이다.

그래서 reject 라고 부른다.

이러한 개념을 잘 이해하고 다음 단계로 넘어가니 공부가 조금은 수월했다,

아래의 코드는 숫자값을 받아 숫자이면 양수와 음수를 구분해주는 간단한 Promise 예제이다.

```jsx
function myP(num) {
  // 1. 함수를 하나 선언한다

  // 2. 함수안에서 excutor 라는 함수를 선언하고
  //    excutor 함수는 resolve와 reject를 매개변수로 넘겨받는다.
  const excutor = (resolve, reject) => {
    // 3. setTimeOut 비동기 함수를 호출하고 2초 뒤에 실행되도록 한다.
    setTimeout(() => {
      // 4. setTimeOut 함수 안에서 myP에서 넘겨받는 num 매개변수의
      //    타입을 비교하는 조건문을 만든다.
      if (typeof num === "number") {
        // 5. 연산이 성공적으로 마무리 되면 resolve함수를 실행한다.
        resolve(num >= 0 ? "양수" : "음수");
      } else {
        // 6. 연산이 실패로 돌아가면 reject 함수를 실행한다.
        reject("숫자형 타입이 아닙니다.");
      }
    }, 2000);
  };
  const asyncTest = new Promise(excutor);
  // 7. asyncTest 라는 변수에 Promise객체를 담고 Promise객체는 excutor를 참조한다.
  return asyncTest;
  // 8. asyncTest를 return 하며 nyP 함수의 값은 asyncTest를 가지고있다.
}

const result = myP(20);
// 9. result라는 변수에 myP함수를 담고 myP함수가 가지고있는 매개변수 num에 20을 전달한다
//    넘겨준 20은 숫자형타입이고 -1보다 큰 양수이기 때문에 "양수를 출력한다"

// 10. result를 then과 catch로 실행한다.
// 이행 : then()
// 거부 : catch()
result
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  })
  .finally(() => {
    console.log("연산 끝");
  });

// ** finally는 이행을 하거나 실패를 해도 무조건 실행을 한다.
```

주석이 많아져서 코드가 복잡해 보이지만 주석을 다 지우면 어떻게 돌아가는지 감이 잡힌다.
여기서 나한테는 아주 익숙한 메서드들이 등장해서 이해하기가 너무 편했다.

then 과 catch와 finally인데

then 은 작업이 성공적으로 마쳤을때 실행 할 코드를 작성하는 공간이고

catch 는 작업이 실패했을 때 실행 할 코드를 작성하는 공간이다.
error 를 확인하는 용도로 catch 메서드를 사용하며 콜백지옥의 단점인 error 처리를 완벽하게 보완해준다.

finally는 성공적으로 마치던 실패로 마치던 무조건 실행 된다.

나는 finally가 굳이 필요 할 까? 라고 생각을 했었다.

근데 필요가 없으면 존재하지 않아야 하는게 아닌가? 라고 의문심을 가지고 문서를 뒤지기 시작했다

모질라에서는 이렇게 나와있다.

[Promise.prototype.finally() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise/finally)

```jsx
finally 메서드
---------------------------------------------------------------------
finally 메서드는 결과에 관계없이 promise가 처리되면 무언가를 프로세싱 또는 정리를
수행하려는 경우에 유용합니다.
```

## 느낀 점

- async 와 await을 배우기 전 무조건 거쳐야 할 단계이고 Promise 는 왜 존재하는지 부터 이해하자.
- 공식문서를 자꾸 들여다보며 공부하자.

# 참고자료

---

[Promise.prototype.finally() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise/finally)

[Promise - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)