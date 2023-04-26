## 🔴 VIewPropType 관련 이슈

```jsx
// 에러코드
ERROR  Invariant Violation: ViewPropTypes has been removed from React Native. Migrate toViewPropTypes exported from 'deprecated-react-native-prop-types'.   
ERROR  Invariant Violation: Module AppRegistry is not a registered callable module (calling runApplication). A frequent cause of the error is that the application entry file path is incorrect.
This can also happen when the JS bundle is corrupt or there is an early initializationerrorwhen loading React Native.
ERROR  Invariant Violation: Module AppRegistry is not a registered callable module (calling runApplication). A frequent cause of the error is that the application entry file path is incorrect.
This can also happen when the JS bundle is corrupt or there is an early initializationerrorwhen loading React Native.
```

### 🤷‍♂️ 왜 발생했을까?

- ViewPropTypes는 React-native에서 제거되었지만 다른 모듈에서 ViewPropTypes을 사용해서 문제가 발생한다.


### 👨‍💻 해결한 방법

1. 먼저 ViewPropTypes 를 대체 할 수 있는 모듈을 설치해야한다.

```jsx
# with NPM
npm install deprecated-react-native-prop-types

# with YARN
yarn add deprecated-react-native-prop-types
```
[deprecated-react-native-prop-types -- npm](https://www.npmjs.com/package/deprecated-react-native-prop-types/v/2.2.0)


2. node-modules/react-native/index.js 로 이동

- 아래의 코드를 찾는다.

```jsx
// node_modules/react-native/index.js

//이전 코드
get ColorPropType(): $FlowFixMe {
  invariant(
    false,
    "ColorPropType has been removed from React Native. Migrate to " +
      "ColorPropType exported from 'deprecated-react-native-prop-types'.",
 );
},
get EdgeInsetsPropType(): $FlowFixMe {
  invariant(
    false,
    "EdgeInsetsPropType has been removed from React Native. Migrate to " +
      "EdgeInsetsPropType exported from 'deprecated-react-native-prop-types'.",
  );
},
get PointPropType(): $FlowFixMe {
  invariant(
    false,
    "PointPropType has been removed from React Native. Migrate to " +
     "PointPropType exported from 'deprecated-react-native-prop-types'.",
 );
},
get ViewPropTypes(): $FlowFixMe {
 invariant(
   false,
   "ViewPropTypes has been removed from React Native. Migrate to " +
     "ViewPropTypes exported from 'deprecated-react-native-prop-types'.",
 );
},
```

- 전체를 잘라내고 아래의 코드를 붙혀넣는다.

```jsx
// 변경할 코드
get ColorPropType(): $FlowFixMe {
  return require("deprecated-react-native-prop-types").ColorPropType
},
get EdgeInsetsPropType(): $FlowFixMe {
  return require("deprecated-react-native-prop-types").EdgeInsetsPropType
},
get PointPropType(): $FlowFixMe {
  return require("deprecated-react-native-prop-types").PointPropType
},
get ViewPropTypes(): $FlowFixMe {
  return require("deprecated-react-native-prop-types").ViewPropTypes
},
```

간략하게 설명하자면 원래는 react-native에 없는 ViewPropTypes을 방금 우리가 설치한 모듈로 대체하겠다는 코드이다.
그러면 ViewPropTypes의 모든 의존성은 우리가 설치한 deprecated-react-native-prop-types 가 가지고 있다.

만약 npm i 를 해서 package.json 의 의존성을 다시 불러올때는 우리가 수정한 node-modules/react-native/index.js가
초기화 되어있을것이다. 그것을 매번 변경해주기에는 너무 번거로운 작업이다.

이럴때는 patch-package를 사용하면 되는데 patch-package에 대한 설명은 나중에 조금 더 자세하게 다뤄보겠다.

