## Next.js 의 디렉토리 구조

---

### -NextJS 자동설정

---

```jsx
npx create-next-app@latest
# or
yarn create next-app
```

### 1. Pages

---

Next.js 에서는 route 설정을 따로 하지 않고 .js, .jsx, .ts, .tsx 로 파일을 생성하면 파일 이름을 기반으로 route가 설정된다. 예를들어 pages/shop.js 를 생성하면 /shop으로 쉽게 접근이 가능하다.
header 같은경우는 페이지가 아니라 component라는 폴더를 하나 만들어서 그 곳에서 관리한다. 그 이유는 pages 내에 들어가는 파일은 다른 페이지에서 재 사용은 가능하지만 사용하는 용도가 다르다고 생각한다.
재사용이 가능한 컴포넌트들은 component라는 폴더를 하나 만들어서 관리하자

### 2. public

---

정적 파일은 Next.js의 public 폴더에서 관리한다.
예를 들어 이미지, 폰트 파일 리소스, robots.txt, favicon 등을 관리한다.
또한 기본 URL 또는 웹사이트 도메인 이름으로 엑세스 하려는 모든 파일을 관리하는 폴더이다.

### 3. styles

---

Global styles 폴더이다. 컴포넌트의 개별 css는 각 컴포넌트 폴더에 module로 관리한다.

### 4. api

---

Next.js로 API 를 구축하기 위해 사용한다.
