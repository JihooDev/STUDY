# React-native 이미지 로딩
---

### 1. 원하는 로딩 Lottie 찾기
---

[LottieFiles: Download Free lightweight animations for website & apps.](https://lottiefiles.com/)
위의 링크로 들어가면 수 많은 애니메이션을 json파일로 가져와서 이쁘게 사용할 수 있다.
주로 나는 로딩, 요청이 성공했을 때 Lottie를 주로 사용한다.
원하는 애니메이션을 찾고 json으로 저장한다.

### 2. 공통적인 컴포넌트 만들기

---

적용 전에 package.json에 아래의 코드를 추가한다.

```jsx
"lottie-react-native": "^5.1.4",
```

이후 npm install을 해서 package.json의 의존성을 설치한다.

```jsx
npm install
```

이제 컴포넌트를 만든다.
컴포넌트의 장점은 하나만 만들어놓으면 여기저기서 유용하게 사용할 수 있다.

```jsx
import AnimatedLottieView from 'lottie-react-native'
import React from 'react'
import styled from 'styled-components'

const ImageLoad = () => {
    return (
        <ImageLoadView>
            <AnimatedLottieView
                source={require('../assets/lottie/image_load.json')}
                loop
                autoPlay
            />
        </ImageLoadView>
    )
}

const ImageLoadView = styled.View`
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: 999;
    background-color: #fff;
`

export default ImageLoad
```

나는 이렇게 작성했다. 여기서 중요한점은 width와 height를 100% 로 고정시켜놓는다는 점이다.
그 이유는 언제 어디서나 가져다 쓸수있어야하는 만큼 거기에 대한 크기를 일일이 지정하기에는 너무 손이 많이 간다.

### 3. 사용하기
---

우리가 만든 ImageLoad 컴포넌트를 보였다가 이미지가 로드되면 안보여줄 상태를 만든다.
```jsx
const [imageLoad, setImageLoad] = useState(true);
```

그리고 사용하면 된다.

여기서 중요하게 생각해야 할 점은
아래의 코드를 감싸는 `<View>`태그가 필요하고 이 태그에는 style속성으로 width와 height가 지정되어있어야 한다.
또한 overflow : hidden으로 로딩 컴포넌트가 벗어나지 않게 조절해준다.
```jsx
{imageLoad ? <ImageLoad /> : null}
<Image
    source={{ uri: imageUrl }}
    style={{ width: '100%', height: '100%' }}
    resizeMode={'cover'}
    onLoadEnd={() => setImageLoad(false)}
/>
```

`<Image />` 태그의 onLoadEnd는 이미지 로드에 성공하거나 실패할 때 호출된다.
처음에는 기본값으로 imageLoad의 상태를 true로 놔두고 이미지가 로드되면 false로 바꿔서 이미지 로드 전 로딩을 구현 할 수 있다.

### 4. 주의해야할 점
---
배열에 담긴 값을 FlatList나 map을 사용해서 이미지 로드를 구현 할 시
무조건 render 되는 부분은 따로 빼놓는걸 권장한다.
이유는 상태는 하나이고 여러가지를 같이 렌더링 하다보니
예를들어 10개의 이미지 중 하나만 성공하면 다른 이미지들은 불러오기 전인데 로딩이 끝나버리고
예전과 같이 깜빡이는 현상을 발견 할 수 있다.
이미지 1 = 상태 1 로 관리해야 한다.