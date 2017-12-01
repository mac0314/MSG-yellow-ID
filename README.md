# Plusfriend-Tutorial

---------------------------------
## 카카오톡 플러스친구 튜토리얼


### 개요
Node.js [Express 프레임워크](http://expressjs.com/ko/)를 활용한 플러스친구 API 서버

#### 플러스 친구 API 관련 코드 부분
/routes/plusfriend/index.js

#### 카카오톡 플러스 친구 API v.2.0
[링크](https://github.com/plusfriend/auto_reply) 내용 참고

#### API specification

#### 1. Home Keyboard API

##### Specification
- **Method** : GET
- **URL** : http://{{localhost:3000}}/api/plusfriend/keyboard
- **Content-Type** : application/json; charset=utf-8

- **Response**

| 필드명 | 타입 | 필수여부 | 설명 |
| ---- | ---- | -------- | ----------- |
| keyboard | [Keyboard](https://github.com/plusfriend/auto_reply#6-object) | Required | 키보드 영역에 표현될 버튼에 대한 정보. 생략시 ```text``` 타입이 선택된다.|


#### 2. 메시지 수신 및 자동응답 API

##### Specification
- **Method** : POST
- **URL** : http://{{localhost:3000}}/api/plusfriend/message
- **Content-Type** : application/json; charset=utf-8
- **Parameters**

| 필드명 | 타입 | 필수여부 | 설명 |
| ---- | ---- | -------- | ----------- |
| user\_key | String | Required | 메시지를 발송한 유저 식별 키 |
| type | String | Required | text, photo |
| content | String | Required | 자동응답 명령어의 메시지 텍스트 혹은 미디어 파일 uri |

- **Response**

| 필드명 | 타입 | 필수여부 | 설명 |
| ---- | ---- | -------- | ----------- |
| message | [Message](https://github.com/plusfriend/auto_reply/blob/master/README.md#62-message) | Required | 자동응답 명령어에 대한 응답 메시지의 내용. 6.2에서 상세 기술 |
| keyboard | [Keyboard](https://github.com/plusfriend/auto_reply#6-object) | Optional | 키보드 영역에 표현될 명령어 버튼에 대한 정보. 생략시 text 타입(주관식 답변 키보드)이 선택된다. 6.1에서 상세 기술|


#### 3. 친구 추가/차단 알림 API

##### Specification
- **Method** : POST / DELETE
- **URL** : http://{{localhost:3000}}/api/plusfriend/friend
- **Content-Type** : application/json; charset=utf-8
- **Parameters**

| 필드명 | 타입 | 필수여부 | 설명 |
| ---- | ---- | -------- | ----------- |
| user\_key | String | Required | 유저 식별키 |
- **Response**

| http status code | code | message | comment |
| ---------------- | ---- | ------- | ------- |
| 200 | 0 | SUCCESS | 정상 응답 |

#### 4. 채팅방 나가기

##### Specification
- **Method** : DELETE
- **URL** : http://{{localhost:3000}}/api/plusfriend/chat\_room/:user\_key
- **Content-Type** : application/json; charset=utf-8
- **Response**

| http status code | code | message | comment |
| ---------------- | ---- | ------- | ------- |
| 200 | 0 | SUCCESS | 정상 응답 |
