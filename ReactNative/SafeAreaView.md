### SafeAreaView

---

SafeAreaView는 ReactNative는 핵심 구성 요소이다.
이 컴포넌트의 목적은 안전 영역 경계 내에서 콘텐츠를 렌더링하는 것이다.
현재 IOS 버전 11 이상이 설치된 IOS 기기에서만 작동한다.

<img width="100%" src="https://s3-us-west-2.amazonaws.com/secure.notion-static.com/445feb08-364f-4277-9f99-89f97f1ea94f/Untitled.png">

왼쪽의 기기와 오른쪽 기기는 SafeAreaView를 사용할 때와 사용하지 않았을 때의 차이는 확연히 차이가 난다.
그냥 View 를 사용해서 구축을 한다면 안드로이드와 IOS 모두 영역을 직접 손 봐야하는 까다로운 작업이 생긴다.
SafeAreaView를 사용해서 개발을 한다면 까다로운 작업을 줄일 수 있다.