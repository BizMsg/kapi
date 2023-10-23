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

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="150" align="center"></th><th width="150" align="center"></th><th width="203" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Array</td><td align="center">성공 시 그룹 목록</td></tr><tr><td align="center"></td><td align="center">groupKey</td><td align="center">String</td><td align="center">그룹 Key</td></tr><tr><td align="center"></td><td align="center">name</td><td align="center">String</td><td align="center">그룹 이름</td></tr><tr><td align="center"></td><td align="center">createdAt</td><td align="center">String</td><td align="center">생성 일</td></tr></tbody></table>

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

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="150" align="center"></th><th width="150" align="center"></th><th width="203" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Array</td><td align="center">성공 시 그룹 목록</td></tr><tr><td align="center"></td><td align="center">groupKey</td><td align="center">String</td><td align="center">그룹 Key</td></tr><tr><td align="center"></td><td align="center">name</td><td align="center">String</td><td align="center">그룹 이름</td></tr><tr><td align="center"></td><td align="center">createdAt</td><td align="center">String</td><td align="center">생성 일자</td></tr></tbody></table>

### 그룹 내 발신프로필 추가

* 발신프로필 그룹에 발신 프로필을 추가합니다.
* **POST** /v3/kakao/group/profile/add
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">groupKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 그룹 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 </td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="150" align="center"></th><th width="150" align="center"></th><th width="203" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Array</td><td align="center">성공 시 그룹 목록</td></tr><tr><td align="center"></td><td align="center">groupKey</td><td align="center">String</td><td align="center">그룹 Key</td></tr><tr><td align="center"></td><td align="center">name</td><td align="center">String</td><td align="center">그룹 이름</td></tr><tr><td align="center"></td><td align="center">createdAt</td><td align="center">String</td><td align="center">생성 일자</td></tr></tbody></table>

### 그룹에 발신프로필 삭제

* 발신프로필 그룹에 발신 프로필을 삭제합니다.
* **POST** /v3/kakao/group/profile/delete
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">groupKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 그룹 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 </td></tr></tbody></table>

**Request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="165.33333333333331" align="center"></th><th width="339" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr></tbody></table>

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
