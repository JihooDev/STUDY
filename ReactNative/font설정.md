### -android

---

- 프로젝트 디렉토리에서 android/app/src/main/assets/fonts 폴더를 생성한 후 다운로드 받은 폰트 파일을 추가한다

* 사용방법

```jsx
// styled-component

const MainText = styled.Text`
  font-family: "NotoSansKR-Bold";
`;
```

### -ios

---

1. 프로젝트 디렉토리에서 ios 폴더에 Fonts 폴더를 생성하고 해당 폴더에 사용할 폰트 파일을 넣어준다 (otf,ttf)
2. ios/project_name.xcodeproj이나 ios/project_name.xcworkspace을 실행하여 xcode를 실행
   <img src="https://velog.velcdn.com/images%2Ftjdgus0528%2Fpost%2F76eb4a48-4ccd-4540-a549-0118bdc75299%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-05%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.14.25.png">
3. 자신의 프로젝트에서 우클릭하여 Add Files to ‘프로젝트이름’ 클릭
4. ios/Fonts 폴더를 선택 -> Create folder references를 선택 -> Add to target: 자신의 프로젝트 -> Add를 눌러 폴더를 추가
   <img src="https://velog.velcdn.com/images%2Ftjdgus0528%2Fpost%2F9459304a-34a7-4b1a-a769-06c299eb105f%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-05%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.19.55.png">
5. 중간 TARGETS 부분에서 자시의 프로젝트 클릭 -> 오른쪽 초록색 부분에서 오른쪽 클릭 -> 노란색 부분 생긴 -> ADD ROW 누르기
   <img src="https://velog.velcdn.com/images%2Ftjdgus0528%2Fpost%2Fc3732498-dbee-4870-8415-cda2c6857cc1%2F%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%202022.%201.%205.%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.22.jpg">
6. Key 부분을 Fonts provided by application로 설정한다
7. item 추가하여 해당 폰트를 직접 1개씩 추가한다

- 사용방법

```jsx
// styled-component

const MainText = styled.Text`
  font-family: "NotoSansKR-Bold";
`;
```
