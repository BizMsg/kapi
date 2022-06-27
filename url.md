# 플러그인 콜백 URL

* 플러그인을 버튼이 포함된 메시지를 발송했을 때, 결과를 전달받을 콜백 URL을 관리합니다.
* 플러그인 당 1개의 콜백 URL을 가질 수 있고, 카카오톡 채널 기준으로 저장됩니다.
* 동일한 카카오톡 채널로 생성된 플러그인 콜백 URL은 공유 됩니다.

### 플러그인 콜백 URL 조회

* 발신프로필 키로 해당 카카오톡 채널에 등록된 플러그인 콜백 URL을 조회합니다.
* **POST** /v3/kakao/plugin/callbackUrl/list
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
| senderKey | String |    O   |    발신프로필     |

**Response**

|  **키**  |                |  **타입** |                                **설명**                                |
| :-----: | :------------: | :-----: | :------------------------------------------------------------------: |
|   code  |                |  String |                                 결과 코드                                |
| message |                |  String |                              실패 시 결과 메시지                             |
|   data  |                |  Array  |                          성공 시 플러그인 콜백 URL 목록                         |
|         |    pluginId    |  String |                               플러그인 아이디                               |
|         |   pluginType   |  String | <p>플러그인 타입 <br>(SECURE_IMAGE: 보안이미지전송, ONE_TIME_PROFILE: 개인정보이용)</p> |
|         | pluginTypeName |  String |                              플러그인 타입 이름                              |
|         |   callbackUrl  |  String |                             Callback Url                             |
|         |   modifiable   | Boolean |             <p>수정 가능 여부<br>(다른 허브파트너에서 등록한 경우 수정 불가)</p>             |
|         |    deletable   | Boolean |             <p>삭제 가능 여부<br>(다른 허브파트너에서 등록한 경우 삭제 불가)</p>             |



### 플러그인 콜백 URL 등록

* 발신프로필 키로 해당 카카오톡 채널에 플러그인 콜백 URL을 등록합니다.
* **POST** /v3/kakao/plugin/callbackUrl/create
* **Content-Type:** application/json; charset=utf-8

**Request**

|    **키**    | **타입** | **필수** |                       **설명**                       |
| :---------: | :----: | :----: | :------------------------------------------------: |
|    bizId    | String |    O   |                    BIZPPURIO ID                    |
|    apiKey   | String |    O   |                      API 발급 키                      |
|  senderKey  | String |    O   |                       발신프로필                        |
|  pluginType | String |    O   | <p>플러그인 타입<br>(SECURE_IMAGE, ONE_TIME_PROFILE)</p> |
|   pluginId  | String |    O   |                      플러그인 아이디                      |
| callbackUrl | String |    O   |                       콜백 URL                       |

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |



### **플러그인 콜백 URL 수정**

* 발신프로필 키로 해당 카카오톡 채널에 등록된 플러그인 콜백 URL을 수정합니다.
* **POST** /v3/kakao/plugin/callbackUrl/update
* **Content-Type:** application/json; charset=utf-8

**Request**

|    **키**    | **타입** | **필수** |    **설명**    |
| :---------: | :----: | :----: | :----------: |
|    bizId    | String |    O   | BIZPPURIO ID |
|    apiKey   | String |    O   |   API 발급 키   |
|  senderKey  | String |    O   |    발신프로필     |
|   pluginId  | String |    O   |   플러그인 아이디   |
| callbackUrl | String |    O   |    콜백 URL    |

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |



### 플러그인 콜백 URL 삭제

* 발신프로필 키로 해당 카카오톡 채널에 등록된 플러그인 콜백 URL을 삭제합니다.
* **POST** /v3/kakao/plugin/callbackUrl/delete
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
| senderKey | String |    O   |    발신프로필 키   |
|  pluginId | String |    O   |   플러그인 아이디   |

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |
