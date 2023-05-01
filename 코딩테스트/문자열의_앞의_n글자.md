## 1. 문제설명

---

문자열 my_string과 정수 n이 매개변수로 주어질 때, my_string의 앞의 n글자로 이루어진 문자열을 return 하는 solution 함수를 작성해 주세요.

### 제한 조건

- my_string은 숫자와 알파벳으로 이루어져 있습니다.
- 1 ≤ my_string의 길이 ≤ 1,000
- 1 ≤ n ≤ my_string의 길이

### 입출력 예

|my_string|n|result|
|------|---|---|
|"ProgrammerS123"|11|"ProgrammerS"|
|"He110W0r1d"|5|"He110"|


## 2.해결

---

```jsx
function solution(my_string, n) {
  return my_string.slice(0, n);
}
```

매우 간단한 문제이다.
문제와 같은 상황이라면 기본적으로 지원하는 slice메서드를 사용해도 되고 substring을 사용해도 된다.
slice와 substring 의 차이점은 음수가 입력된 상황에서 발생한다.
substring은 음수는 무조건 0으로 인식한다.
slice는 음수를 입력한 경우 가장 뒤 글자부터 계산을 하여 출력한다.

```jsx
  const testText = "뉴진스의하입보이요";

  // substring
  console.log(testText.substring(-3, 5));
  // output : '뉴진스의하'

  console.log(testText.slice(-3, 5));
  // output : ""
```
