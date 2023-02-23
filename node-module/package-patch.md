## 🔥 node-module patch

---

<aside>
💡 node-module을 직접적으로 수정할 시 로컬에서는 괜찮지만 yarn을 업데이트 하면 수정한 파일은 모두 날라가고만다. 그리고 다른 팀원이 내 프로젝트를 clone이나 pull을 받으면 npm install 그리고 yarn을 해줘야하는데 내가 수정한 사항들은 다른 팀원에게 반영되지 않는다. 즉 컨트롤 + s를 누르지않고 파일을 닫는 행위와 같은것이다. 여러 오픈소스를 내가 직접 개조하고 변경하고 싶을때가 있을것이다. 그럴때는 node-module안의 코드를 수정하고 patch 를 사용하여 module을 관리하자

</aside>

## 💥 사용방법

---

### 1. Install

```jsx
npm i patch-package
yarn add -D patch-package postinstall-postinstall
```

### 2. package-json에 script 추가

```jsx
// package.json

"scripts": {
	"postinstall": "patch-package" 
}
```

### 3. 모듈 수정 후

```bash
yarn patch-package [package-name]
```

 수정한 node_module 안 패키지를 patch-package를 이용하여 패키지화 시킨다.

### 4. git 명령어로 공유

```bash
git add patches/[...patch]
git commit -m [commit message goes here]
```