# 플러그인 콜백 URL

* 플러그인을 버튼이 포함된 메시지를 발송했을 때, 결과를 전달받을 콜백 URL을 관리합니다.
* 플러그인 당 1개의 콜백 URL을 가질 수 있고, 카카오톡 채널 기준으로 저장됩니다.
* 동일한 카카오톡 채널로 생성된 플러그인 콜백 URL은 공유 됩니다.

### 플러그인 콜백 URL 조회

* 발신프로필 키로 해당 카카오톡 채널에 등록된 플러그인 콜백 URL을 조회합니다.
* **POST** /v3/kakao/plugin/callbackUrl/list
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 </td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="164.21293800539084" align="center"></th><th width="150" align="center"></th><th width="292" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Array</td><td align="center">성공 시 플러그인 콜백 URL 목록</td></tr><tr><td align="center"></td><td align="center">pluginId</td><td align="center">String</td><td align="center">플러그인 아이디</td></tr><tr><td align="center"></td><td align="center">pluginType</td><td align="center">String</td><td align="center">플러그인 타입 <br>(SECURE_IMAGE: 보안이미지전송, ONE_TIME_PROFILE: 개인정보이용)</td></tr><tr><td align="center"></td><td align="center">pluginTypeName</td><td align="center">String</td><td align="center">플러그인 타입 이름</td></tr><tr><td align="center"></td><td align="center">callbackUrl</td><td align="center">String</td><td align="center">Callback Url</td></tr><tr><td align="center"></td><td align="center">modifiable</td><td align="center">Boolean</td><td align="center">수정 가능 여부<br>(다른 허브파트너에서 등록한 경우 수정 불가)</td></tr><tr><td align="center"></td><td align="center">deletable</td><td align="center">Boolean</td><td align="center">삭제 가능 여부<br>(다른 허브파트너에서 등록한 경우 삭제 불가)</td></tr></tbody></table>



### 플러그인 콜백 URL 등록

* 발신프로필 키로 해당 카카오톡 채널에 플러그인 콜백 URL을 등록합니다.
* **POST** /v3/kakao/plugin/callbackUrl/create
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 </td></tr><tr><td align="center">pluginType</td><td align="center">String</td><td align="center">O</td><td align="center">플러그인 타입<br>(SECURE_IMAGE, ONE_TIME_PROFILE)</td></tr><tr><td align="center">pluginId</td><td align="center">String</td><td align="center">O</td><td align="center">플러그인 아이디</td></tr><tr><td align="center">callbackUrl</td><td align="center">String</td><td align="center">O</td><td align="center">콜백 URL</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="165.33333333333331" align="center"></th><th width="339" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr></tbody></table>



### **플러그인 콜백 URL 수정**

* 발신프로필 키로 해당 카카오톡 채널에 등록된 플러그인 콜백 URL을 수정합니다.
* **POST** /v3/kakao/plugin/callbackUrl/update
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 </td></tr><tr><td align="center">pluginId</td><td align="center">String</td><td align="center">O</td><td align="center">플러그인 아이디</td></tr><tr><td align="center">callbackUrl</td><td align="center">String</td><td align="center">O</td><td align="center">콜백 URL</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="165.33333333333331" align="center"></th><th width="339" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr></tbody></table>



### 플러그인 콜백 URL 삭제

* 발신프로필 키로 해당 카카오톡 채널에 등록된 플러그인 콜백 URL을 삭제합니다.
* **POST** /v3/kakao/plugin/callbackUrl/delete
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="285" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">발신프로필 키</td></tr><tr><td align="center">pluginId</td><td align="center">String</td><td align="center">O</td><td align="center">플러그인 아이디</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="165.33333333333331" align="center"></th><th width="339" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr></tbody></table>
