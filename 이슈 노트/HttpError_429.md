### HTTP ERROR 429 (To many request)

 - 주어진 시간 동안 너무 많은 API 요청을 보냄

### 해결 방법

- 서버의 요청대로 요청을 천천히 막는다
- 해당 서버에서는 얼마를 더 기다려야하고 얼마만큼의 request가 제한 되어있다고 나와있다.
- 서버 요청이 실패하면 Modal, alert 을 띄워서 사용자에게 다시 시도할 수 있도록 유도한다.
- Postman 에서 응답결과 JSON을 복제해서 Error code 429 일때만 복제된 JSON 을 응답결과 처럼 보여준다