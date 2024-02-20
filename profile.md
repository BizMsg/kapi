# 발신프로필 관리

&#x20;인증토큰 요청

* 발신프로필 등록을 위한 카카오톡 채널 인증 토큰을 요청합니다.
* **POST** /v3/kakao/profile/token
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="171.94744121715078" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="251" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">phoneNumber</td><td align="center">String</td><td align="center">O</td><td align="center">토큰을 수신할 휴대폰번호<br>(Yellow ID의 핸드폰번호와 일치)</td></tr><tr><td align="center">yellowId</td><td align="center">String</td><td align="center">O</td><td align="center">카카오톡 채널(@ID)</td></tr></tbody></table>

**Request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="165.33333333333331" align="center"></th><th width="339" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr></tbody></table>

### 발신프로필 카테고리 전체 조회

* 발신프로필 등록시 사용할 카테고리 목록 전체를 조회합니다.
* **POST** /v3/kakao/profile/category/all
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th width="153.00141043723553" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="209" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="150" align="center"></th><th width="150" align="center"></th><th width="203" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">총 개수</td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Array</td><td align="center">성공 시 템플릿 목록</td></tr><tr><td align="center"></td><td align="center">code</td><td align="center">String</td><td align="center">카테고리 코드</td></tr><tr><td align="center"></td><td align="center">name</td><td align="center">String</td><td align="center">카테고리 이름</td></tr></tbody></table>

### 발신프로필 카테고리 조회

* 카테고리 코드에 해당하는 특정 카테고리를 조회합니다.
* **POST** /v3/kakao/profile/category
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="241" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">categoryCode</td><td align="center">String</td><td align="center">O</td><td align="center">카테고리 코드</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="150" align="center"></th><th width="150" align="center"></th><th width="203" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지 </td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Object</td><td align="center">성공 시 카테고리 정보 </td></tr><tr><td align="center"></td><td align="center">code</td><td align="center">String</td><td align="center">카테고리 코드</td></tr><tr><td align="center"></td><td align="center">name</td><td align="center">String</td><td align="center">카테고리 이름</td></tr></tbody></table>

### 발신프로필 등록

* 발신프로필을 신규 등록합니다.
* **POST** /v3/kakao/profile/create
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="248" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">token</td><td align="center">String</td><td align="center">O</td><td align="center">수신받은 인증토큰</td></tr><tr><td align="center">phoneNumber</td><td align="center">String</td><td align="center">O</td><td align="center">토큰을 수신할 휴대폰번호<br>(Yellow ID의 핸드폰번호와 일치)</td></tr><tr><td align="center">yellowId</td><td align="center">String</td><td align="center">O</td><td align="center">카카오톡 채널(@ID)</td></tr><tr><td align="center">categoryCode</td><td align="center">String</td><td align="center">O</td><td align="center">카테고리 코드</td></tr></tbody></table>

**Response**

<table data-header-hidden data-full-width="false"><thead><tr><th align="center">Text</th><th align="center"></th><th align="center"></th><th align="center"></th><th data-hidden align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td><td align="center"></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td><td align="center"></td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지</td><td align="center"></td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Object</td><td align="center">성공 시 발신프로필 정보</td><td align="center"></td></tr><tr><td align="center"></td><td align="center">senderKey</td><td align="center">String</td><td align="center">발신프로필 키</td><td align="center">senderKey</td></tr></tbody></table>

### 발신프로필 조회

* 발신프로필 정보를 조회합니다.
* **POST** /v3/kakao/profile
* **Content-Type:** application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="232" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">String</td><td align="center">O</td><td align="center">등록된 발신프로필의 키</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="165.47893790611795" align="center"></th><th width="150" align="center"></th><th width="203" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td align="center">String</td><td align="center">실패 시 결과 메시지 </td></tr><tr><td align="center">data</td><td align="center"></td><td align="center">Object</td><td align="center">성공 시 카테고리 정보</td></tr><tr><td align="center"></td><td align="center">senderKey</td><td align="center">String</td><td align="center">조회된 발신프로필 키</td></tr><tr><td align="center"></td><td align="center">uuid</td><td align="center">String</td><td align="center">카카오톡 채널</td></tr><tr><td align="center"></td><td align="center">name</td><td align="center">String</td><td align="center">카카오톡 채널 발신프로필 명</td></tr><tr><td align="center"></td><td align="center">status</td><td align="center">String</td><td align="center">발신프로필 상태</td></tr><tr><td align="center"></td><td align="center">block</td><td align="center">Boolean</td><td align="center">발신프로필 차단 여부</td></tr><tr><td align="center"></td><td align="center">dormant</td><td align="center">Boolean</td><td align="center">발신프로필 휴면 여부</td></tr><tr><td align="center"></td><td align="center">profileStatus</td><td align="center">String</td><td align="center">카카오톡 채널 상태 <br>(A: activated, C: deactivated, B: block, E: deleting, D: deleted)</td></tr><tr><td align="center"></td><td align="center">createdAt</td><td align="center">String</td><td align="center">발신프로필 등록일</td></tr><tr><td align="center"></td><td align="center">modifiedAt</td><td align="center">String</td><td align="center">최종 수정일</td></tr><tr><td align="center"></td><td align="center">categoryCode</td><td align="center">String</td><td align="center">발신프로필 카테고리코드</td></tr><tr><td align="center"></td><td align="center">alimtalk</td><td align="center">Boolean</td><td align="center">알림톡 사용 여부</td></tr><tr><td align="center"></td><td align="center">bizchat</td><td align="center">Boolean</td><td align="center">상담톡 사용 여부</td></tr><tr><td align="center"></td><td align="center">brandtalk</td><td align="center">Boolean</td><td align="center">브랜드톡 사용 여부</td></tr><tr><td align="center"></td><td align="center">committalCompanyName</td><td align="center">String</td><td align="center">위탁사 이름 (상담톡 관련)</td></tr><tr><td align="center"></td><td align="center">chennelKey</td><td align="center">String</td><td align="center">메시지 전송 결과 수신 채널키</td></tr><tr><td align="center"></td><td align="center">businessprofile</td><td align="center">Boolean</td><td align="center">카카오톡 채널 비즈니스 인증 여부</td></tr><tr><td align="center"></td><td align="center">businessType</td><td align="center">String</td><td align="center">카카오톡 채널 비즈니스 인증 타입</td></tr></tbody></table>





### 발신프로필 리스트 전체조회

• 발신프로필 목록을 조회합니다.

• POST /v3/kakao/profile/use

• Content-Type: application/json; charset=utf-8

**Request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="202" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th width="147" align="center"></th><th width="150" align="center"></th><th width="180"></th><th width="122"></th><th width="104" align="center"></th><th width="289" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td></td><td></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td></td><td></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td></td><td></td><td align="center">String</td><td align="center">실패 시 결과 메시지 </td></tr><tr><td align="center">data</td><td align="center"></td><td></td><td></td><td align="center">Object</td><td align="center">성공 시 데이터</td></tr><tr><td align="center"></td><td align="center">success</td><td></td><td></td><td align="center">Array</td><td align="center">성공케이스에 대한 리스트</td></tr><tr><td align="center"></td><td align="center"></td><td>senderKey</td><td></td><td align="center">String</td><td align="center">발신프로필 키</td></tr><tr><td align="center"></td><td align="center"></td><td>uuid</td><td></td><td align="center">String</td><td align="center">발신프로필 상태</td></tr><tr><td align="center"></td><td align="center"></td><td>name</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 프로필 명</td></tr><tr><td align="center"></td><td align="center"></td><td>status</td><td></td><td align="center">String</td><td align="center">상태 (A: 정상)</td></tr><tr><td align="center"></td><td align="center"></td><td>block</td><td></td><td align="center">String</td><td align="center">발신 프로필 차단 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>dormant</td><td></td><td align="center">String</td><td align="center">발신 프로필 휴면 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>profileStatus</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 상태 (A: activated, C: deactivated, B: block, E: deleting, D: deleted)</td></tr><tr><td align="center"></td><td align="center"></td><td>createdAt</td><td></td><td align="center">String</td><td align="center">등록일</td></tr><tr><td align="center"></td><td align="center"></td><td>modifiedAt</td><td></td><td align="center">String</td><td align="center">최종 수정일</td></tr><tr><td align="center"></td><td align="center"></td><td>categoryCode</td><td></td><td align="center">String</td><td align="center">카테고리 코드</td></tr><tr><td align="center"></td><td align="center"></td><td>alimtalk</td><td></td><td align="center">String</td><td align="center">알림톡 사용 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>bizchat</td><td></td><td align="center">String</td><td align="center">상담톡 사용 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>brandtalk</td><td></td><td align="center">String</td><td align="center">브랜드톡 사용 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>commitalCompanyName</td><td></td><td align="center">String</td><td align="center">위탁사 이름 (상담톡 관련)</td></tr><tr><td align="center"></td><td align="center"></td><td>channelKey</td><td></td><td align="center">String</td><td align="center">메시지 전송 결과 수신 채널키</td></tr><tr><td align="center"></td><td align="center"></td><td>businessProfile</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 비즈니스 인증 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>businessType</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 비즈니스 인증 타입</td></tr><tr><td align="center"></td><td align="center"></td><td>groups</td><td></td><td align="center">Array</td><td align="center">발신 프로필 그룹 정보</td></tr><tr><td align="center"></td><td align="center"></td><td></td><td>groupKey</td><td align="center">String</td><td align="center">발신 프로필 그룹 키</td></tr><tr><td align="center"></td><td align="center"></td><td></td><td>name</td><td align="center">Array</td><td align="center">이름</td></tr><tr><td align="center"></td><td align="center"></td><td></td><td>createdAt</td><td align="center">String</td><td align="center">등록일</td></tr><tr><td align="center"></td><td align="center">fail</td><td></td><td></td><td align="center">Array</td><td align="center">실패케이스에 대한 리스트</td></tr><tr><td align="center"></td><td align="center"></td><td>senderKey</td><td></td><td align="center">String</td><td align="center">발신 프로필 키</td></tr><tr><td align="center"></td><td align="center"></td><td>code</td><td></td><td align="center">String</td><td align="center">실패 결과 코드</td></tr><tr><td align="center"></td><td align="center"></td><td>message</td><td></td><td align="center">String</td><td align="center">실패 메시지</td></tr></tbody></table>







### 발신프로필 리스트 조회&#x20;

• 발신프로필 목록을 조회합니다.

• POST /v3/kakao/profile/multi

• Content-Type: application/json; charset=utf-8

**request**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="196" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">Array</td><td align="center">O</td><td align="center">발신 프로필 목록 </td></tr></tbody></table>



**response**

<table data-header-hidden><thead><tr><th width="147" align="center"></th><th width="150" align="center"></th><th width="180"></th><th width="122"></th><th width="104" align="center"></th><th width="289" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"></td><td></td><td></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center"></td><td></td><td></td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center"></td><td></td><td></td><td align="center">String</td><td align="center">실패 시 결과 메시지 </td></tr><tr><td align="center">data</td><td align="center"></td><td></td><td></td><td align="center">Object</td><td align="center">성공 시 데이터</td></tr><tr><td align="center"></td><td align="center">success</td><td></td><td></td><td align="center">Array</td><td align="center">성공케이스에 대한 리스트</td></tr><tr><td align="center"></td><td align="center"></td><td>senderKey</td><td></td><td align="center">String</td><td align="center">발신프로필 키</td></tr><tr><td align="center"></td><td align="center"></td><td>uuid</td><td></td><td align="center">String</td><td align="center">발신프로필 상태</td></tr><tr><td align="center"></td><td align="center"></td><td>name</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 프로필 명</td></tr><tr><td align="center"></td><td align="center"></td><td>status</td><td></td><td align="center">String</td><td align="center">상태 (A: 정상)</td></tr><tr><td align="center"></td><td align="center"></td><td>block</td><td></td><td align="center">String</td><td align="center">발신 프로필 차단 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>dormant</td><td></td><td align="center">String</td><td align="center">발신 프로필 휴면 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>profileStatus</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 상태 (A: activated, C: deactivated, B: block, E: deleting, D: deleted)</td></tr><tr><td align="center"></td><td align="center"></td><td>createdAt</td><td></td><td align="center">String</td><td align="center">등록일</td></tr><tr><td align="center"></td><td align="center"></td><td>modifiedAt</td><td></td><td align="center">String</td><td align="center">최종 수정일</td></tr><tr><td align="center"></td><td align="center"></td><td>categoryCode</td><td></td><td align="center">String</td><td align="center">카테고리 코드</td></tr><tr><td align="center"></td><td align="center"></td><td>alimtalk</td><td></td><td align="center">String</td><td align="center">알림톡 사용 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>bizchat</td><td></td><td align="center">String</td><td align="center">상담톡 사용 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>brandtalk</td><td></td><td align="center">String</td><td align="center">브랜드톡 사용 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>commitalCompanyName</td><td></td><td align="center">String</td><td align="center">위탁사 이름 (상담톡 관련)</td></tr><tr><td align="center"></td><td align="center"></td><td>channelKey</td><td></td><td align="center">String</td><td align="center">메시지 전송 결과 수신 채널키</td></tr><tr><td align="center"></td><td align="center"></td><td>businessProfile</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 비즈니스 인증 여부</td></tr><tr><td align="center"></td><td align="center"></td><td>businessType</td><td></td><td align="center">String</td><td align="center">카카오톡 채널 비즈니스 인증 타입</td></tr><tr><td align="center"></td><td align="center"></td><td>groups</td><td></td><td align="center">Array</td><td align="center">발신 프로필 그룹 정보</td></tr><tr><td align="center"></td><td align="center"></td><td></td><td>groupKey</td><td align="center">String</td><td align="center">발신 프로필 그룹 키</td></tr><tr><td align="center"></td><td align="center"></td><td></td><td>name</td><td align="center">Array</td><td align="center">이름</td></tr><tr><td align="center"></td><td align="center"></td><td></td><td>createdAt</td><td align="center">String</td><td align="center">등록일</td></tr><tr><td align="center"></td><td align="center">fail</td><td></td><td></td><td align="center">Array</td><td align="center">실패케이스에 대한 리스트</td></tr><tr><td align="center"></td><td align="center"></td><td>senderKey</td><td></td><td align="center">String</td><td align="center">발신 프로필 키</td></tr><tr><td align="center"></td><td align="center"></td><td>code</td><td></td><td align="center">String</td><td align="center">실패 결과 코드</td></tr><tr><td align="center"></td><td align="center"></td><td>message</td><td></td><td align="center">String</td><td align="center">실패 메시지</td></tr></tbody></table>



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

<table data-header-hidden><thead><tr><th width="150" align="center">Text</th><th width="150" align="center"></th><th width="150" align="center">필수</th><th width="215" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>필수</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">bizId</td><td align="center">String</td><td align="center">O</td><td align="center">BIZPPURIO ID</td></tr><tr><td align="center">apiKey</td><td align="center">String</td><td align="center">O</td><td align="center">API 발급 키</td></tr><tr><td align="center">senderKey</td><td align="center">Array</td><td align="center">O</td><td align="center">등록된 발신프로필의 키</td></tr></tbody></table>

**Response**

<table data-header-hidden><thead><tr><th align="center">Text</th><th width="165.33333333333331" align="center"></th><th width="339" align="center"></th></tr></thead><tbody><tr><td align="center"><strong>키</strong></td><td align="center"><strong>타입</strong></td><td align="center"><strong>설명</strong></td></tr><tr><td align="center">code</td><td align="center">String</td><td align="center">결과 코드</td></tr><tr><td align="center">message</td><td align="center">String</td><td align="center">실패 시 결과 메시지</td></tr></tbody></table>
