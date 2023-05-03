# 템플릿 관리

### 템플릿 신규 등록

* 템플릿을 신규 등록합니다. 사전에 발신프로필 또는 발신 프로필 그룹이 등록 되어있어야 합니다.
* **POST** /v3/kakao/template/add
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (6) (1) (1).png>)

![](<.gitbook/assets/image (4) (1).png>)

**Response**

|    키    |   타입   |                                                                  설명                                                                 |
| :-----: | :----: | :---------------------------------------------------------------------------------------------------------------------------------: |
|   code  | String |                                                                결과 코드                                                                |
| message | String |                                                             실패 시 결과 메시지                                                             |
|   data  | Object | <p>성공 시 템플릿 정보<br><strong>(*</strong><a href="template.md#undefined-3"><strong>템플릿 상세 조회 반환 값 참조</strong></a><strong>)</strong></p> |

**ex)**

템플릿 등록 : [https://kapi.ppurio.com/kakao/template/add](https://kapi.ppurio.com/kakao/template/add)

```json5
{
  "senderKey": "05aa099bcbc5220a8c0b2XXXXXXXXXXXXX",
  "senderKeyType": "S",
  "templateName": "봇키워드 버튼 템플릿",
  "templateContent": "봇키워드 테스트",
  "templateMessageType": "MI",
  "templateExtra": "부가정보입니다",
  "templateAd": "광고성메시지입니다",
  "categoryCode": "002001",
  "securityFlag": false,
  "templateEmphasizeType": "ITEM_LIST",
  "templateHeader": "헤더 값",
  "templateImageName": "템플릿 이미지 파일 명",
  "templateImageUrl": "템플릿 이미지 링크",
  "templateItem": {
    "list": [{"description": "아이템 리스트 디스크립션", "title": "타이틀"}],
    "summary": {"description": "아이템 요약정보 디스크립션", "title": "타이틀"}
  },
  "templateItemHighlight": {
    "description": "아이템 하이라이트 디스크립션",
    "imageUrl": "썸네일 이미지 주소",
    "title": "아이템 하이라이트 타이틀"
  },
  "templateTitle": "강조표기타이틀입니다.",
  "templateSubtitle": "강조표기보조문구입니다.",
  "buttons": [{"linkType": "BK", "name": "봇키워드 버튼"}],
  "quickReplies": [{"linkType": "BK", "name": "봇키워드 버튼"}],
  "bizId": "kakaoapi",
  "apiKey": "Q4jh8oXXXXXXXX"
}

```





### 템플릿 코드 유효성 검증

* 등록하려는 템플릿 코드의 유효성을 검증합니다.
* &#x20;**POST** /v3/kakao/template/codeCheck
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (15).png>)

**Response**\


|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |



### 템플릿 목록 조회

* 발신프로필에 등록된 템플릿 목록을 조회합니다.
* **POST** /v3/kakao/template/list
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (7).png>)

**Response**

![](<.gitbook/assets/image (1) (1).png>)



### 템플릿 상세 조회

* 템플릿을 조회 합니다.
* **POST** /v3/kakao/template/detail
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (5) (1).png>)



**Response**

![](<.gitbook/assets/image (11) (1).png>)



### 템플릿 수정

* 등록된 템플릿을 수정합니다. 템플릿 상태가 **대기(R)**이고 템플릿 검수상태가 **등록(REG)** 또는 **반려(REJ)**인 경우에만 수정 가능합니다.
* **POST** /v3/kakao/template/update
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (9) (1).png>)



**Response**

|  **키**  | **타입** |                           **설명**                           |
| :-----: | :----: | :--------------------------------------------------------: |
|   code  | String |                            결과 코드                           |
| message | String |                         실패 시 결과 메시지                        |
|   data  | Object | <p>성공 시 템플릿 정보<br><strong>(*템플릿 상세조회 반환 값 참조)</strong></p> |







### 템플릿 삭제

* 등록된 템플릿을 삭제합니다. 템플릿 상태가 **대기(R)**이고 템플릿 검수상태가 **등록(REG)** 또는 **반려(REJ)**인 경우에만 삭제 가능합니다.
* **POST** /v3/kakao/template/delete
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (9).png>)



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |





### 템플릿 카테고리 전체 조회

* 템플릿 등록시 사용할 카테고리 목록 전체를 조회합니다.
* **POST** /v3/kakao/template/category/all
* **Content-Type:** application/json; charset=utf-8

**Request**

|  **키**  | **타입** | **필수** |    **설명**    |
| :-----: | :----: | :----: | :----------: |
|  bizId  | String |    O   | BIZPPURIO ID |
| message | String |    O   |   API 발급 키   |



**Response**



|  **키**  |           | **타입** |       **설명**      |
| :-----: | :-------: | :----: | :---------------: |
|   code  |           | String |       결과 코드       |
| message |           | String |    실패 시 결과 메시지    |
|   data  |           |  Array |    성공 시 카테고리 목록   |
|         |    code   | String |      카테고리 코드      |
|         |    name   | String |      카테고리 이름      |
|         | groupName | String |     카테고리 그룹 이름    |
|         | Inclusion | String | 카테고리 적용 대상 템플릿 설명 |
|         | exclusion | String | 카테고리 제외 대상 템플릿 설명 |



### 템플릿 카테고리 조회

* 카테고리 코드에 해당하는 특정 템플릿 카테고리를 조회합니다.
* **POST** /v3/kakao/template/category
* **Content-Type:** application/json; charset=utf-8

**Request**

|     **키**    | **타입** | **필수** |    **설명**    |
| :----------: | :----: | :----: | :----------: |
|     bizId    | String |    O   | BIZPPURIO ID |
|    apiKey    | String |    O   |   API 발급 키   |
| categoryCode | String |    O   |    카테고리 코드   |

**Response**

|  **키**  |           | **타입** |       **설명**      |
| :-----: | :-------: | :----: | :---------------: |
|   code  |           | String |       결과 코드       |
| message |           | String |    실패 시 결과 메시지    |
|   data  |           |  Array |   성공 시 카테고리 정보    |
|         |    code   | String |      카테고리 코드      |
|         |    name   | String |      카테고리 이름      |
|         | groupName | String |     카테고리 그룹 이름    |
|         | Inclusion | String | 카테고리 적용 대상 템플릿 설명 |
|         | exclusion | String | 카테고리 제외 대상 템플릿 설명 |

**ex)**&#x20;

&#x20;템플릿 카테고리 조회 : [https://kapi.ppurio.com/kakao/template/category](https://kapi.ppurio.com/kakao/template/category)

```json5

{
  "code": "200",
  "message": "",
  "date": {
    "code": "001001",
    "name": "예시 카테고리",
    "groupName": "예시 카테고리 그룹",
    "inclusion": "이런 템플릿을 이 카테고리에 적용하세요",
    "exclusion": "이런 템플릿은 이 카테고리에 적용하지 마세요"
  }
}
```





### 템플릿 검수 요청

* 등록된 템플릿을 검수 요청합니다. 템플릿 상태가 **대기(R)**이고 템플릿 검수상태가 **등록(REG)**인 경우에만 요청 가능합니다.
* **POST** /v3/kakao/template/request
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (10).png>)

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |





### 템플릿 검수 요청 (파일 첨부)

* 등록된 템플릿을 검수 요청합니다. 템플릿 상태가 **대기(R)**이고 템플릿 검수상태가 **등록(REG)**인 경우에만 요청 가능합니다. \
  파일과 함께 문의 또는 의견을 남길수 있습니다. 파일 형식은 **png**, **jpg**, **jpge**, **gif**, **pdf**, **hwp**, **doc**, **docx**만 가능하며 개당 **50MB**까지 첨부할 수 있습니다.
* **POST** /v3/kakao/template/request\_with\_file
* **Content-Type:** multipart/form-data

**Request**\


![](<.gitbook/assets/image (12).png>)



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |



### 템플릿 검수 요청 취소

* 검수 요청 상태의 템플릿을 취소 요청합니다. 템플릿 상태가 **대기(R)**이고 템플릿 검수상태가 **검수 요청(REQ)**인 경우에만 요청 가능합니다.
* **POST** /v3/kakao/template/cancel\_request
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (4).png>)

**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |





### 템플릿 사용 중지

* 등록된 템플릿을 중지 상태로 변경합니다. 템플릿 상태가 **대기(R)** 또는 **정상(A)** 이고 템플릿 검수상태가 **승인(APR)**인 경우에만 요청 가능합니다.
* **POST** /v3/kakao/template/stop
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (3).png>)



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |





### 템플릿 사용 중지 해제

* 등록된 템플릿을 정상 상태로 되돌립니다. 템플릿 상태가 **중지(S)** 이고 템플릿 검수상태가 **승인(APR)**인 경우에만 요청 가능합니다.
* **POST** /v3/kakao/template/reuse
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (6) (1).png>)



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |





### 템플릿 승인 취소

* 승인된 템플릿이 **대기(R)** 상태 일 때 승인 취소할 수 있습니다. 승인 취소시 **등록(REG)** 상태로 변경되며 재 검수 요청 가능합니다.
* **POST** /v3/kakao/template/cancel\_approval
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (2) (2).png>)



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |





### 템플릿 휴면 해제

* 장기간 미사용으로 휴면된 템플릿을 해제합니다. 해제 후 **30일**간 사용하지 않는 경우 **재 휴면 처리** 됩니다.
* **POST** /v3/kakao/template/release
* **Content-Type:** application/json; charset=utf-8

**Request**

![](<.gitbook/assets/image (5).png>)



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |

