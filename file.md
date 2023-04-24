# 비즈메시지 파일 관리

### 친구톡 이미지 등록

* 친구톡 이미지를 등록합니다.
* **POST** /v3/kakao/image/upload
* **Content-Type:** multipart/form-data

**Request**

![](<.gitbook/assets/image (13).png>)



**Response**

|  **키**  | **타입** |          **설명**          |
| :-----: | :----: | :----------------------: |
|   code  | String |           결과 코드          |
| message | String |        실패 시 결과 메시지       |
|  image  | String | 성공 시 이미지가 등록된 카카오 서버 URL |





### 친구톡 이미지 조회

* 친구톡 이미지 목록을 조회 합니다.
* **POST** /v3/kakao/image/list
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |                                                         **설명**                                                        |
| :-------: | :----: | :----: | :-------------------------------------------------------------------------------------------------------------------: |
|   bizId   | String |    O   |                                                      BIZPPURIO ID                                                     |
|   apiKey  | String |    O   |                                                        API 발급 키                                                       |
| senderKey | String |    X   | <p>발신프로필키<br>(<strong>입력시</strong> : 해당 발신프로필키에 매핑된 이미지 조회, </p><p><strong>미입력시</strong> : 공용(해당계정)으로 매핑된 이미지 조회)</p> |
| imageType | String |    O   |                                                  이미지 타입(기본=I, 와이드=W)                                                  |

**Response**

|  **키**  |           | **타입** |                        **설명**                       |
| :-----: | :-------: | :----: | :-------------------------------------------------: |
|   code  |           | String |                        결과 코드                        |
| message |           | String |                     실패 시 결과 메시지                     |
|   data  |           |  Array |                     성공 시 이미지 목록                     |
|         |   title   | String |                        이미지 제목                       |
|         |    link   | String | <p>이미지 클릭 시 이동할 URL<br>(http:// 또는 https:// 포함)</p> |
|         |  imageUrl | String |                 이미지가 등록된 카카오 서버 URL                 |
|         | createdAt | String |                       이미지 등록일                       |
|         | imageType | String |            <p>이미지 타입<br>(기본=I, 와이드=W)</p>           |

### 친구톡 이미지 삭제

* 등록된 친구톡 이미지를 삭제합니다.
* **POST** /v3/kakao/image/delete
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**  | **타입** | **필수** |     **설명**     |
| :------: | :----: | :----: | :------------: |
|   bizId  | String |    O   |  BIZPPURIO ID  |
|  apiKey  | String |    O   |    API 발급 키    |
| imageUrl | String |    O   | 삭제할 이미지 URL 정보 |

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |



###

### 알림톡 템플릿 등록용 이미지 업로드

* 이미지 알림톡 또는 아이템리스트 알림톡 템플릿 등록 시 사용될 이미지를 업로드 합니다.&#x20;

&#x20;       제한 사이즈 - 가로 500px 이상, 가로:세로 비율 2:1&#x20;

&#x20;       파일형식 및 크기 : jpg, png / 최대 500KB

* **POST** /v3/kakao/image/alimtalk/template
* **Content-Type:** multipart/form-data

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |
|  image |  File  |    O   |  업로드할 이미지 파일 |

**Response**

|  **키**  | **타입** |          **설명**          |
| :-----: | :----: | :----------------------: |
|   code  | String |           결과 코드          |
| message | String |        실패 시 결과 메시지       |
|  image  | String | 성공 시 이미지가 등록된 카카오 서버 URL |



### 알림톡 이미지 업로드

* 이미지 알림톡 또는 아이템리스트 알림톡 발송 시 사용될 이미지를 업로드 합니다.&#x20;

&#x20;       제한 사이즈 - 가로 500px 이상, 가로:세로 비율 2:1 이상 3:4 이하&#x20;

&#x20;       파일형식 및 크기 : jpg, png / 최대 500KB

* **POST** /v3/kakao/image/alimtalk
* **Content-Type:** multipart/form-data

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |
|  image |  File  |    O   |  업로드할 이미지 파일 |



**Response**

|  **키**  | **타입** |          **설명**          |
| :-----: | :----: | :----------------------: |
|   code  | String |           결과 코드          |
| message | String |        실패 시 결과 메시지       |
|  image  | String | 성공 시 이미지가 등록된 카카오 서버 URL |





### 알림톡 하이라이트 이미지 업로드

* 아이템리스트 알림톡 발송 시 사용될 아이템 하이라이트 이미지를 업로드 합니다.&#x20;

&#x20;       제한 사이즈 - 가로 108px 이상, 가로:세로 비율이 1:1&#x20;

&#x20;       파일형식 및 크기 : jpg, png / 최대 500KB&#x20;

* **POST** /v3/kakao/image/alimtalk/itemHighlight
* **Content-Type:** multipart/form-data

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |
|  image |  File  |    O   |  업로드할 이미지 파일 |

**Response**

|  **키**  | **타입** |          **설명**          |
| :-----: | :----: | :----------------------: |
|   code  | String |           결과 코드          |
| message | String |        실패 시 결과 메시지       |
|  image  | String | 성공 시 이미지가 등록된 카카오 서버 URL |
