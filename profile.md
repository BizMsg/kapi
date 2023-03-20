# 발신프로필 관리

&#x20;인증토큰 요청

* 발신프로필 등록을 위한 카카오톡 채널 인증 토큰을 요청합니다.
* **POST** /v3/kakao/profile/token
* **Content-Type:** application/json; charset=utf-8

**Request**

|    **키**    | **타입** | **필수** |                     **설명**                     |
| :---------: | :----: | :----: | :--------------------------------------------: |
|    bizId    | String |    O   |                  BIZPPURIO ID                  |
|    apiKey   | String |    O   |                    API 발급 키                    |
| phoneNumber | String |    O   | <p>토큰을 수신할 휴대폰번호<br>(Yellow ID의 핸드폰번호와 일치)</p> |
|   yellowId  | String |    O   |                  카카오톡 채널(@ID)                  |

**Request**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |

### 발신프로필 카테고리 전체 조회

* 발신프로필 등록시 사용할 카테고리 목록 전체를 조회합니다.
* **POST** /v3/kakao/profile/category/all
* **Content-Type:** application/json; charset=utf-8

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |

**Response**

|  **키**  |      | **타입** |    **설명**   |
| :-----: | :--: | :----: | :---------: |
|   code  |      | String |    결과 코드    |
| message |      | String |     총 개수    |
|   data  |      |  Array | 성공 시 템플릿 목록 |
|         | code | String |   카테고리 코드   |
|         | name | String |   카테고리 이름   |

### 발신프로필 카테고리 조회

* 카테고리 코드에 해당하는 특정 카테고리를 조회합니다.
* **POST** /v3/kakao/profile/category
* **Content-Type:** application/json; charset=utf-8

**Request**

|     **키**    | **타입** | **필수** |    **설명**    |
| :----------: | :----: | :----: | :----------: |
|     bizId    | String |    O   | BIZPPURIO ID |
|    apiKey    | String |    O   |   API 발급 키   |
| categoryCode | String |    O   |    카테고리 코드   |

**Response**

|  **키**  |      | **타입** |     **설명**    |
| :-----: | :--: | :----: | :-----------: |
|   code  |      | String |     결과 코드     |
| message |      | String |  실패 시 결과 메시지  |
|   data  |      | Object | 성공 시 카테고리 정보  |
|         | code | String |    카테고리 코드    |
|         | name | String |    카테고리 이름    |

### 발신프로필 등록

* 발신프로필을 신규 등록합니다.
* **POST** /v3/kakao/profile/create
* **Content-Type:** application/json; charset=utf-8

**Request**

|     **키**    | **타입** | **필수** |                              **설명**                             |
| :----------: | :----: | :----: | :-------------------------------------------------------------: |
|     bizId    | String |    O   |                           BIZPPURIO ID                          |
|    apiKey    | String |    O   |                             API 발급 키                            |
|     token    | String |    O   |                            수신받은 인증토큰                            |
|  phoneNumber | String |    O   | <p>토큰을 수신할 휴대폰번호<br><strong></strong>(Yellow ID의 핸드폰번호와 일치)</p> |
|   yellowId   | String |    O   |                           카카오톡 채널(@ID)                          |
| categoryCode | String |    O   |                             카테고리 코드                             |

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |

### 발신프로필 조회

* 발신프로필 정보를 조회합니다.
* **POST** /v3/kakao/profile
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
| senderKey | String |    O   | 등록된 발신프로필의 키 |

**Response**

|  **키**  |                      |  **타입** |                                                  **설명**                                                  |
| :-----: | :------------------: | :-----: | :------------------------------------------------------------------------------------------------------: |
|   code  |                      |  String |                                                   결과 코드                                                  |
| message |                      |  String |                                               실패 시 결과 메시지                                                |
|   data  |                      |  Object |                                               성공 시 카테고리 정보                                               |
|         |       senderKey      |  String |                                                조회된 발신프로필 키                                               |
|         |         uuid         |  String |                                                  카카오톡 채널                                                 |
|         |         name         |  String |                                              카카오톡 채널 발신프로필 명                                             |
|         |        status        |  String |                                                 발신프로필 상태                                                 |
|         |         block        | Boolean |                                                발신프로필 차단 여부                                               |
|         |        dormant       | Boolean |                                                발신프로필 휴면 여부                                               |
|         |     profileStatus    |  String | <p>카카오톡 채널 상태 <br><strong></strong>(A: activated, C: deactivated, B: block, E: deleting, D: deleted)</p> |
|         |       createdAt      |  String |                                                 발신프로필 등록일                                                |
|         |      modifiedAt      |  String |                                                  최종 수정일                                                  |
|         |     categoryCode     |  String |                                               발신프로필 카테고리코드                                               |
|         |       alimtalk       | Boolean |                                                 알림톡 사용 여부                                                |
|         |        bizchat       | Boolean |                                                 상담톡 사용 여부                                                |
|         |       brandtalk      | Boolean |                                                브랜드톡 사용 여부                                                |
|         | committalCompanyName |  String |                                              위탁사 이름 (상담톡 관련)                                             |
|         |      chennelKey      |  String |                                             메시지 전송 결과 수신 채널키                                             |
|         |    businessprofile   | Boolean |                                            카카오톡 채널 비즈니스 인증 여부                                            |
|         |     businessType     |  String |                                            카카오톡 채널 비즈니스 인증 타입                                            |

### 발신프로필 리스트 전체조회

* 발신프로필 전체 목록을 조회합니다.
* **POST** /v3/kakao/profile/all
* **Content-Type:** application/json; charset=utf-8

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |

**Response**

|  **키**  |            |           | **타입** | **설명**        |
| :-----: | :--------: | :-------: | :----: | ------------- |
|   code  |            |           | String | 결과 코드         |
| message |            |           | String | 실패 시 결과 메시지   |
|   data  |            |           | Object | 성공 시 발신프로필 목록 |
|         |  senderKey |           | String | 조회된 발신프로필 키   |
|         | yellowName |           | String | 발신프로필 명       |
|         | yellowStat |           | String | 발신프로필 상태      |
|         |    rdate   |           | String | 발신프로필 생성일자    |
|         |   groups   |           |  Array | 성공 시 그룹데이터    |
|         |            |  groupKey | String | 그룹 키          |
|         |            |    name   | String | 그룹 이름         |
|         |            | createdAt | String | 생성 일자         |



### 발신프로필 리스트 조회

* 발신프로필 목록을 조회합니다.
* **POST** /v3/kakao/profile/list
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
| senderKey |  Array |    O   |  발신 프로필 목록   |

**Response**

|  **키**  |            |           | **타입** |     **설명**    |
| :-----: | :--------: | :-------: | :----: | :-----------: |
|   code  |            |           | String |     결과 코드     |
| message |            |           | String |  실패 시 결과 메시지  |
|   data  |            |           | Object | 성공 시 발신프로필 목록 |
|         |  senderKey |           | String | 조회된 발신프로필 key |
|         | yellowName |           | String |    발신프로필 명    |
|         | yellowStat |           | String |    발신프로필 상태   |
|         |    rdate   |           | String |   발신프로필 생성일자  |
|         |   groups   |           |  Array |   성공 시 그룹데이터  |
|         |            |  groupKey | String |     그룹 key    |
|         |            |    name   | String |      그룹이름     |
|         |            | createdAt | String |      생성일자     |

**ex)**

```json5
{
  "bizId": "kakaoapi",
  "apiKey": "Q4jh8oXXXXXXXX",
  "senderKey": ["05aa099bcbc5220a8c0b2XXXXXXXXXXXXX", "03423ege2545c0b2XXXXXXXXXXXXX"]
}
```

### 미사용 프로필 휴면 해제

* 장기 미사용으로 인해 휴면 상태인 발신 프로필을 **차단 해제**합니다.
* **POST** /v3/kakao/profile/recover
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
| senderKey |  Array |    O   | 등록된 발신프로필의 키 |

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |
