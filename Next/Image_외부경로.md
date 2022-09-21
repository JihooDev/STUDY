## 에러 발생 🤢

---

Next 의 Image 는 웹의 최적화의 엄청난 도움을 준다.

내 작업폴더에 있는 이미지를 업로드 할때는 경로만 쉽게 넣어주면 정상적으로 작동했지만

JSON 의 이미지 경로들은 모두 https:// 로 시작하는 경로였다. 

그래서 경로를 불러오면 hostname을 찾을수 없다는 결과가 나왔고 일단은 html의 기본 태그인 img 태그로 사용을 해왔다.

하지만 다른 텍스트는 불러오고 이미지는 2초 3초 뒤에 나오니 ui 부분에서 굉장히 불편했다.

<img width="100%" alt="스크린샷 2022-09-21 오전 9 10 04" src="https://user-images.githubusercontent.com/105398995/191387475-abd98bff-b8d0-4150-8b3f-8457a1a005b2.png">


## 해결 😃

---

정답은 next.config에 있었다.

Next 는 웹팩을 기본 번들러로 사용한다.

Next 를 조금 더 커스텀하게 사용하기 위해 next.config.js 에서 기본 설정을 할 수 있다.

next 서버 빌드 단계에서 사용되며 브라우저 빌드에는 포함되지 않는다.

본론으로 넘어가서 images 라는 객체 안해서 domain을 설정 해주어야 한다.

예를 들어서 이미지 경로가

```jsx
[https://images.chosun.com/resizer/sD2V9t5EOBvs-FOtUUDOJekXUx4=/616x0/smart/cloudfront-ap-northeast-1.images.arcpublishing.com/chosun/U4IIQNIIYFLA3JC7EYMNJMOCIA.JPG](https://images.chosun.com/resizer/sD2V9t5EOBvs-FOtUUDOJekXUx4=/616x0/smart/cloudfront-ap-northeast-1.images.arcpublishing.com/chosun/U4IIQNIIYFLA3JC7EYMNJMOCIA.JPG)
```

https:// 로 시작한다면 https:// {{next.config에 추가할 내용 }} /resizer

domains 배열에 [images.chosun.com](https://images.chosun.com/resizer/sD2V9t5EOBvs-FOtUUDOJekXUx4=/616x0/smart/cloudfront-ap-northeast-1.images.arcpublishing.com/chosun/U4IIQNIIYFLA3JC7EYMNJMOCIA.JPG) 이 부분을 추가 하면 된다.

<img width="100%" alt="스크린샷 2022-09-21 오전 9 08 16" src="https://user-images.githubusercontent.com/105398995/191387435-72f4a11f-27d0-4170-b36f-1123f037372c.png">

