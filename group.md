# 그룹 관리



{% hint style="info" %}
\[카카오비즈메시지센터]에서 **발신프로필 그룹**을 먼저 생성해야 합니다
{% endhint %}



&#x20;발신프로필 여러 개를 그룹으로 관리 가능합니다.

* 동일 그룹에 속한 발신프로필은 그룹으로 등록된 템플릿을 공유하여 사용 할 수 있습니다.



### 그룹 조회

* 발신프로필 그룹 목록을 조회합니다.
* **POST** /v3/kakao/group
* **Content-Type:** application/json; charset=utf-8

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |

**Response**

|  **키**  |           | **타입** |    **설명**   |
| :-----: | :-------: | :----: | :---------: |
|   code  |           | String |    결과 코드    |
| message |           | String | 실패 시 결과 메시지 |
|   data  |           |  Array |  성공 시 그룹 목록 |
|         |  groupKey | String |    그룹 Key   |
|         |    name   | String |    그룹 이름    |
|         | createdAt | String |     생성 일    |

**ex)**

그룹 조회 : [https://kapi.ppurio.com/kakao/group](https://kapi.ppurio.com/kakao/group)

```json5
{
  "code": "200",
  "message": "",
  "data": [
    {
      "groupKey": "e08e332a91d7a2571c3ba3XXXXXXXXXXXXX",
      "name": "그룹테스트12",
      "createdAt": ""
    }
  ]
}
```



### 그룹 전체 조회

* 발신프로필 그룹 전체 목록을 조회합니다.
* **POST** /v3/kakao/group/all
* **Content-Type:** application/json; charset=utf-8

**Request**

|  **키** | **타입** | **필수** |    **설명**    |
| :----: | :----: | :----: | :----------: |
|  bizId | String |    O   | BIZPPURIO ID |
| apiKey | String |    O   |   API 발급 키   |

**Response**

|  **키**  |           | **타입** |    **설명**   |
| :-----: | :-------: | :----: | :---------: |
|   code  |           | String |    결과 코드    |
| message |           | String | 실패 시 결과 메시지 |
|   data  |           |  Array |  성공 시 그룹 목록 |
|         |  groupKey | String |    그룹 Key   |
|         |    name   | String |    그룹 이름    |
|         | createdAt | String |    생성 일자    |

### 그룹 내 발신프로필 추가

* 발신프로필 그룹에 발신 프로필을 추가합니다.
* **POST** /v3/kakao/group/profile/add
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
|  groupKey | String |    O   |  발신프로필 그룹 키  |
| senderKey | String |    O   |    발신프로필     |

**Response**

|  **키**  |           | **타입** |    **설명**   |
| :-----: | :-------: | :----: | :---------: |
|   code  |           | String |    결과 코드    |
| message |           | String | 실패 시 결과 메시지 |
|   data  |           |  Array |  성공 시 그룹 목록 |
|         |  groupKey | String |    그룹 Key   |
|         |    name   | String |    그룹 이름    |
|         | createdAt | String |    생성 일자    |

### 그룹에 발신프로필 삭제

* 발신프로필 그룹에 발신 프로필을 삭제합니다.
* **POST** /v3/kakao/group/profile/delete
* **Content-Type:** application/json; charset=utf-8

**Request**

|   **키**   | **타입** | **필수** |    **설명**    |
| :-------: | :----: | :----: | :----------: |
|   bizId   | String |    O   | BIZPPURIO ID |
|   apiKey  | String |    O   |   API 발급 키   |
|  groupKey | String |    O   |  발신프로필 그룹 키  |
| senderKey | String |    O   |    발신프로필     |

**Request**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |

**ex)**

그룹에 발신프로필 삭제 : [https://kapi.ppurio.com/kakao/group/profile/delete](https://kapi.ppurio.com/kakao/group/profile/delete)

```json
{
  "bizId": "kakaoapi",
  "apiKey": "Q4jh8oXXXXXXXX",
  "senderKey": "05aa099bcbc5220a8c0b2XXXXXXXXXXXXX",
  "groupKey": "e08e332a91d7a2571c3ba317bXXXXXXXXXXXX"
}
```
