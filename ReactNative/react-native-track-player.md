# React-Native Track Player
---
<aside>
💡 react-native track player는 react-native 모바일 응용 프로그램에서 오디오 파일을 재생할 수 있는 javaScript 라이브러리이다. 오디오파일 재생을 쉽게 구현하고 진행률을 파악할 수 있으며 다양한 이벤트를 처리하는 인터페이스를 제공한다

</aside>

## 설치
---
```bash
npm install react-native-track-player
```

or

```bash
yarn add react-native-track-player
```

IOS = cd ios && pod install

## 사용법

---

```jsx
import TrackPlayer from 'react-native-track-player';

// ...

TrackPlayer.setupPlayer().then(() => {
  // TrackPlayer를 사용할 준비가 됨
});

TrackPlayer.add({
  id: 'trackId', // 재생할 오디오의 아이디 (임의 값)
  url: require('path/to/track.mp3'), // 재생할 오디오의 파일
  title: 'Track Title', // 재생할 오디오의 타이틀 (제목)
  artist: 'Track Artist', // 아티스트 이름
  artwork: require('path/to/artwork.png') // 해당 앨범의 이미지
});

```

### setupPlayer()로 준비가 완료되었을 때

```jsx
TrackPlayer.play(); // 오디오를 재생함
TrackPlayer.pause(); // 중지함
TrackPlayer.skipToNext(); // 다음 트랙으로 넘어감
TrackPlayer.skipToPrevious(); // 이전 트랙으로 감

```

### 이벤트리스너 제공

```jsx
// service.js

module.exports = async function () {
    try {
        TrackPlayer.addEventListener('remote-play', () => {
            TrackPlayer.play()
        })

        TrackPlayer.addEventListener('remote-pause', () => {
            TrackPlayer.pause()
        });

        TrackPlayer.addEventListener('remote-next', () => {
            TrackPlayer.skipToNext()
        });

        TrackPlayer.addEventListener('remote-previous', () => {
            TrackPlayer.skipToPrevious()
        });

        TrackPlayer.addEventListener('remote-stop', () => {
            TrackPlayer.destroy()
        });
    } catch (error) {
        console.error(error, 'eventListener ERROR')
    }
}
```

## State (재생에 관련 된 현재의 상태를 가져옴)

---

```jsx
const state = await TrackPlayer.getState();
console.log(state); // 상태 값
```

| 이름 | 설명 |
| --- | --- |
| None | 현재 로드된 미디어가 없음을 나타내는 상태 |
| Ready | 플레이어가 플레이를 시작할 준비가 되었음을 나타내는 상태 |
| Playing | 플레이어가 현재 재생 중임을 나타내는 상태 |
| Paused | 플레이어가 현재 일시 중지되었음을 나타내는 상태 |
| Stopped | 플레이어가 현재 정지되었음을 나타내는 상태 |
| Buffering | 플레이어가 현재 버퍼링 중임을 나타내는 상태("재생" 상태) |
| Connecting | 플레이어가 현재 버퍼링 중임을 나타내는 상태("일시중지" 상태) |