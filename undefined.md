# 템플릿 관리

### 템플릿 신규 등록

* 템플릿을 신규 등록합니다. 사전에 발신프로필 또는 발신 프로필 그룹이 등록 되어있어야 합니다.
* **POST** /v3/kakao/template/add
* **Content-Type:** application/json; charset=utf-8

**Request**

|         **키**         |    **-**    |    **-**    |  **타입** | **필수** |                                                                                                                                                                           **설명**                                                                                                                                                                           |
| :-------------------: | :---------: | :---------: | :-----: | :----: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|         bizId         |             |             |  String |    O   |                                                                                                                                                                        BIZPPURIO ID                                                                                                                                                                        |
|         apiKey        |             |             |  String |    O   |                                                                                                                                                                          API 발급 키                                                                                                                                                                          |
|       senderKey       |             |             |  String |    O   |                                                                                                                                                           발신 프로필 키(senderKeyType이 G인 경우 프로필 그룹키)                                                                                                                                                           |
|     senderKeyType     |             |             |  String |    X   |                                                                                                                                                              발신 프로필 키 타입 (S:일반(default), G:그룹)                                                                                                                                                             |
|      templateCode     |             |             |  String |    X   |                                                                                                                                               템플릿 코드 (영문, 숫자, 언더바(\_), 하이픈(-)만 입력 가능, 최대 30자, 빈 값일 경우 자동 생성)                                                                                                                                               |
|      templateName     |             |             |  String |    O   |                                                                                                                                                                           템플릿 이름                                                                                                                                                                           |
|  templateMessageType  |             |             |  String |    O   |                                                                    <p>템플릿 메시지 유형</p><p><strong>(</strong>BA:기본형, EX:부가정보형, AD:광고추가형, MI:복합형)</p><p>- EX : templateExtra 필드 필수</p><p>- AD : templateAd 필드 필수, 그룹 템플릿 사용 불가</p><p>- MI : templateExtra, templateAd 필드 필수, 그룹 템플릿 사용 불가</p>                                                                   |
| templateEmphasizeType |             |             |  String |    O   | <p>템플릿 강조 유형</p><p>(NONE: 선택안함, TEXT: 강조표기형, IMAGE: 이미지형, ITEM_LIST: 아이템리스트형)</p><p>- TEXT : templateTitle, templateSubtitle 필수</p><p>- ITEM_LIST: templateItem.list 필드 필수,</p><p>templateImage(Name,Url), templateHeader, templateItemHighlight 필드 중 1개 이상 필수, templateItem.summary 필드 사용 가능</p><p>- IMAGE: templateImageName, templateImageUrl 필드 필수</p> |
|    templateContent    |             |             |  String |    O   |                                                                                                                                                                           템플릿 내용                                                                                                                                                                           |
|     templateExtra     |             |             |  String |    X   |                                                                                                                                                 <p>부가정보</p><p>- templateMessageType "EX", "MI" 선택 시 필수</p>                                                                                                                                                 |
|       templateAd      |             |             |  String |    X   |                                                                                                                                                <p>광고성메시지</p><p>- templateMessageType "AD", "MI" 선택 시 필수</p>                                                                                                                                                |
|   templateImageName   |             |             |  String |    X   |                                                                                                                                              <p>템플릿 이미지 파일명</p><p>- templateEmphasizeType "IMAGE" 선택 시 필수</p>                                                                                                                                              |
|    templateImageUrl   |             |             |  String |    X   |                                                                                                                                               <p>템플릿 이미지 링크</p><p>- templateEmphasizeType "IMAGE" 선택 시 필수</p>                                                                                                                                              |
|     templateTitle     |             |             |  String |    X   |                                                                                                                                          <p>템플릿 내용 중 강조 표기할 핵심 정보</p><p>- templateEmphasizeType "TEX"” 선택 시 필수</p>                                                                                                                                         |
|    templateSubtitle   |             |             |  String |    X   |                                                                                                                                               <p>강조 표기 보조 문구</p><p>- templateEmphasizeType "TEXT" 선택 시 필수</p>                                                                                                                                              |
|     templateHeader    |             |             |  String |    X   |                                                                                                                                                                     헤더 (최대 16자까지 입력 가능)                                                                                                                                                                    |
| templateItemHighlight |             |             |  Object |    X   |                                                                                                                                                                          아이템 하이라이트                                                                                                                                                                         |
|                       |    title    |             |  String |    O   |                                                                                                                                                        타이틀 (최대 30자까지 입력 가능, 썸네일 이미지가 있을 경우 21자까지 입력)                                                                                                                                                       |
|                       | description |             |  String |    O   |                                                                                                                                                       상세 설명 (최대 19자까지 입력 가능, 썸네일 이미지가 있을 경우 13자까지 입력)                                                                                                                                                      |
|                       |   imageUrl  |             |  String |    X   |                                                                                                                                                                썸네일 이미지 주소 (최대 500자까지 입력 가능)                                                                                                                                                                |
|      templateItem     |             |             |  Object |    X   |                                                                                                                                                                           아이템 정보                                                                                                                                                                           |
|                       |     list    |             |  Array  |    O   |                                                                                                                                       <p>아이템 리스트 (최소 2개, 최대 10개)</p><p>- templateEmphasizeType "TEM_LIST" 선택 시 필수</p>                                                                                                                                      |
|                       |             |    title    |  String |    O   |                                                                                                                                                                     타이틀 (최대 6자까지 입력 가능                                                                                                                                                                     |
|                       |             | description |  String |    O   |                                                                                                                                                                   디스크립션 (최대 23자까지 입력 가능)                                                                                                                                                                   |
|                       |   summary   |             |  Object |    X   |                                                                                                                                                                          아이템 요약 정보                                                                                                                                                                         |
|                       |             |    title    |  String |    O   |                                                                                                                                                                     타이틀 (최대 6자까지 입력 가능)                                                                                                                                                                    |
|                       |             | description |  String |    O   |                                                                                                                                                   디스크립션 (변수 및 화폐 단위, 숫자, 쉼표, 마침표만 사용 가능, 최대 14자까지 입력 가능)                                                                                                                                                   |
|      categoryCode     |             |             |  String |    O   |                                                                                                                                                                         템플릿 카테고리 코드                                                                                                                                                                        |
|      securityFlag     |             |             | Boolean |    X   |                                                                                                                                보안 템플릿 여부, OTP등 보안 메시지 일 경우 설정 발신 당시의 메인 디바이스를 제외한 모든 디바이스에 메시지 텍스트 미 노출 (true:설정, false:미설정)                                                                                                                               |
|        buttons        |             |             |  Array  |    X   |                                                                                                                                                        버튼 정보 (최대 5개 등록 가능, 바로 연결과 함께 사용 시 최대 2개로 제한)                                                                                                                                                       |
|                       |     name    |             |  String |    O   |                                                                                                                                                   <p>버튼명</p><p>- linkType "AC" 선택 시 버튼명은 "채널추가" 로 고정</p>                                                                                                                                                   |
|                       |   linkType  |             |  String |    O   |                                                                                                     <p>버튼 링크타입 <br>(DS:배송조회, WL:웹링크, AL:앱링크, BK:봇키워, MD: 메시지전달, AC: 채널추가, BC: 상담톡전환, BT: 봇전환, P1: 이미지 보안전송 플러그인, P2 : 개인정보이용 플러그인, P3: 원클릭 결제 플러그인)</p>                                                                                                    |
|                       |   linkAnd   |             |  String |    X   |                                                                                                                                       <p>Android 앱 링크 주소 (AL 사용시 필수)</p><p>- linkIos, linkAnd, linkMo 중 2가지 필수 입력</p>                                                                                                                                      |
|                       |   linklos   |             |  String |    X   |                                                                                                                                                                   IOS 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                  |
|                       |    linkMo   |             |  String |    X   |                                                                                                                                                                   모바일 웹 링크 주소 (WL 사용시 필수)                                                                                                                                                                  |
|                       |    linkPc   |             |  String |    X   |                                                                                                                                                                   모바일 웹 링크 주소 (WL 사용시 필수)                                                                                                                                                                  |
|                       |   pluginId  |             |  String |    X   |                                                                                                                                                                 플러그인 ID (P1, P2, P3 사용시 필수)                                                                                                                                                                |
|      quickReplies     |             |             |  Array  |    X   |                                                                                                                                             <p>바로연결 정보 (최대 10개 등록 가능)</p><p>- 상담톡 이용 채널에 한해 바로연결 기능 사용이 가능</p>                                                                                                                                             |
|                       |     name    |             |  String |    O   |                                                                                                                                                                            바로연결명                                                                                                                                                                           |
|                       |   linkType  |             |  String |    O   |                                                                                                                              <p>바로연결 링크타입</p><p><strong>(</strong>WL:웹링크, AL:앱링크, BK:봇키워드, MD: 메시지전달, BC : 상담톡전환, BT: 봇전환)</p>                                                                                                                             |
|                       |   linkAnd   |             |  String |    X   |                                                                                                                                                                 Android 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                |
|                       |   linklos   |             |  String |    X   |                                                                                                                                                                   IOS 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                  |
|                       |    linkMo   |             |  String |    X   |                                                                                                                                                                   모바일 웹 링크 주소 (WL 사용시 필수)                                                                                                                                                                  |
|                       |    linkPc   |             |  String |    X   |                                                                                                                                                                   PC 웹 링크 주소 (WL 사용시 선택)                                                                                                                                                                   |

**Response**

|    키    |   타입   |                                                                  설명                                                                  |
| :-----: | :----: | :----------------------------------------------------------------------------------------------------------------------------------: |
|   code  | String |                                                                 결과 코드                                                                |
| message | String |                                                              실패 시 결과 메시지                                                             |
|   data  | Object | <p>성공 시 템플릿 정보<br><strong>(*</strong><a href="undefined.md#undefined-3"><strong>템플릿 상세 조회 반환 값 참조</strong></a><strong>)</strong></p> |

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

|     **키**     | **타입** | **필수** |                          **설명**                          |
| :-----------: | :----: | :----: | :------------------------------------------------------: |
|     bizId     | String |    O   |                       BIZPPURIO ID                       |
|     apiKey    | String |    O   |                         API 발급 키                         |
|   senderKey   | String |    O   |     <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p>    |
| senderKeyType | String |    X   |        <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>       |
|  templateCode | String |    O   | <p>템플릿 코드<br>(영문, 숫자, 언더바(_), 하이픈(-)만 입력 가능, 최대 30자)</p> |

**Response**\


|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |

~~~~

### 템플릿 목록 조회

* 발신프로필에 등록된 템플릿 목록을 조회합니다.
* **POST** /v3/kakao/template/list
* **Content-Type:** application/json; charset=utf-8

**Request**

|       **키**      | **타입** | **필수** |                                               **설명**                                               |
| :--------------: | :----: | :----: | :------------------------------------------------------------------------------------------------: |
|       bizId      | String |    O   |                                            BIZPPURIO ID                                            |
|      apiKey      | String |    O   |                                              API 발급 키                                              |
|     senderKey    | String |    O   |                          <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p>                         |
|   senderKeyType  | String |    X   |                             <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>                            |
|  templateStatus  | String |    X   | <p>템플릿 상태<br>(REG: 등록, REQ: 검수요청, REJ: 반려,</p><p>STP: 차단, RDY: 발송전, ACT: 정상, DMT: 휴면, BLK: 차단)</p> |
|       page       | String |    X   |                                         요청 페이지 (default: 1)                                        |
|       count      | String |    X   |                                     페이지 별 템플릿 개수 (default: 30)                                     |
|      keyword     | String |    X   |                                     검색 키워드 (글자 수 2자 \~ 50자 제한)                                     |
|     startDate    | String |    X   |                                    생성일자 기준 시작일자 (yyyyMMddHHmmss)                                   |
|      endDate     | String |    X   |                                    생성일자 기준 종료일자 (yyyyMMddHHmmss)                                   |
| categoryCodeList |  Array |    X   |                                        검색 대상의 템플릿 카테고리 코드 목록                                       |
|                  | String |    O   |                                               카테고리 코드                                              |

**Response**

|    **키**    |               |  **타입** |                                               **설명**                                               |
| :---------: | :-----------: | :-----: | :------------------------------------------------------------------------------------------------: |
|     code    |               |  String |                                                결과 코드                                               |
|   message   |               |  String |                                                총 개수                                                |
|  totalCount |               | Integer |                                               총 페이지 수                                              |
| currentPage |               | Integer |                                               현재 페이지                                               |
|     data    |               |  Array  |                                             성공 시 템플릿 목록                                            |
|             |   senderKey   |  String |                                              발신 프로필 키                                              |
|             | senderKeyType |  String |                                             발신 프로필 키 타입                                            |
|             |  templateCode |  String |                                               템플릿 코드                                               |
|             |  templateName |  String |                                               템플릿 이름                                               |
|             |  categoryCode |  String |                                             템플릿 카테고리 코드                                            |
|             |   createdAt   |  String |                                                 등록일                                                |
|             |   modifiedAt  |  String |                                                 수정일                                                |
|             | serviceStatus |  String | <p>템플릿 상태<br>(REG: 등록, REQ: 검수요청, REJ: 반려,</p><p>STP: 차단, RDY: 발송전, ACT: 정상, DMT: 휴면, BLK: 차단)</p> |





### 템플릿 상세 조회

* 템플릿을 조회 합니다.
* **POST** /v3/kakao/template/detail
* **Content-Type:** application/json; charset=utf-8

**Request**

****

|     **키**     | **타입** | **필수** |                          **설명**                          |
| :-----------: | :----: | :----: | :------------------------------------------------------: |
|     bizId     | String |    O   |                       BIZPPURIO ID                       |
|     apiKey    | String |    O   |                         API 발급 키                         |
|   senderKey   | String |    O   |     <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p>    |
| senderKeyType | String |    X   |        <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>       |
|  templateCode | String |    O   | <p>템플릿 코드<br>(영문, 숫자, 언더바(_), 하이픈(-)만 입력 가능, 최대 30자)</p> |

**Response**

|         |                       |             |                  |         |                                                                                                                                                    |
| :-----: | :-------------------: | :---------: | :--------------: | :-----: | :------------------------------------------------------------------------------------------------------------------------------------------------: |
|   code  |                       |             |                  |  String |                                                                        결과 코드                                                                       |
| message |                       |             |                  |  String |                                                                     실패 시 결과 메시지                                                                    |
|   data  |                       |             |                  |  Object |                                                                     성공 시 템플릿 정보                                                                    |
|         |      templateCode     |             |                  |  String |                                                                       템플릿 코드                                                                       |
|         |      templateName     |             |                  |  String |                                                                       템플릿 이름                                                                       |
|         |  templateMessageType  |             |                  |  String |                               <p>템플릿 메시지 유형</p><p><strong>(</strong>BA:기본형(default), EX:부가정보형, AD:광고추가형, MI:복합형)</p>                               |
|         | templateEmphasizeType |             |                  |  String |                                  <p>템플릿 강조 유형</p><p>(NONE: 선택안함, TEXT: 강조표기형, IMAGE: 이미지형, ITEM_LIST: 아이템리스트형)</p>                                 |
|         |    templateContent    |             |                  |  String |                                                                       템플릿 내용                                                                       |
|         |     templateExtra     |             |                  |  String |                                                                        부가정보                                                                        |
|         |       templateAd      |             |                  |  String |                                                                       광고성 메시지                                                                      |
|         |   templateImageName   |             |                  |  String |                                                                     템플릿 이미지 파일명                                                                    |
|         |    templateImageUrl   |             |                  |  String |                                                                     템플릿 이미지 링크                                                                     |
|         |     templateTitle     |             |                  |  String |                                                                템플릿 내용 중 강조 표기할 핵심 정보                                                               |
|         |    templateSubtitle   |             |                  |  String |                                                                     강조 표기 보조 문구                                                                    |
|         |     templateHeader    |             |                  |  String |                                                                         헤더                                                                         |
|         | templateItemHighlight |             |                  |  Object |                                                                      아이템 하이라이트                                                                     |
|         |                       |    title    |                  |  String |                                                                         타이틀                                                                        |
|         |                       | description |                  |  String |                                                                        상세 설명                                                                       |
|         |                       |   imageUrl  |                  |  String |                                                                     썸네일 이미지 주소                                                                     |
|         |      templateItem     |             |                  |  Object |                                                                       아이템 정보                                                                       |
|         |                       |     list    |                  |  Array  |                                                                       아이템 리스트                                                                      |
|         |                       |             |       title      |  String |                                                                         타이틀                                                                        |
|         |                       |             |    description   |  String |                                                                        디스크립션                                                                       |
|         |                       |   summary   |                  |  Object |                                                                      아이템 요약 정보                                                                     |
|         |                       |             |       title      |  String |                                                                         타이틀                                                                        |
|         |                       |             |    description   |  String |                                                                        디스크립션                                                                       |
|         |      categoryCode     |             |                  |  String |                                                                     템플릿 카테고리 코드                                                                    |
|         |      securityFlag     |             |                  | Boolean |                                                     <p>보안 템플릿 여부</p><p>(true:설정, false:미설정)</p>                                                    |
|         |    inspectionStatus   |             |                  |  String |                                             <p>검수 상태</p><p>(REG: 등록, REQ: 검수요청, REJ: 반려, APR : 승인)</p>                                             |
|         |       createdAt       |             |                  |  String |                                                                         생성일                                                                        |
|         |       modifiedAt      |             |                  |  String |                                                                         수정일                                                                        |
|         |         status        |             |                  |  String |                                                     <p>템플릿 상태</p><p>(S:중지, A:정상, R:대기(발송전))</p>                                                    |
|         |         block         |             |                  | Boolean |                                                            템플릿 차단 여부 (true:차단, false: 해제                                                           |
|         |        dormant        |             |                  | Boolean |                                                           템플릿 휴면 여부 (true:휴면, false: 해제)                                                           |
|         |        buttons        |             |                  |  Array  |                                                                        버튼 정보                                                                       |
|         |                       |     name    |                  |  String |                                                                         버튼명                                                                        |
|         |                       |   linkType  |                  |  String | <p>버튼 링크타입<br>(DS:배송조회, WL:웹링크, AL:앱링크, BK:봇키워, MD: 메시지전달, AC: 채널추가, BC: 상담톡전환, BT: 봇전환, P1: 이미지 보안전송 플러그인, P2 : 개인정보이용 플러그인, P3: 원클릭 결제 플러그인)</p> |
|         |                       |   linkAnd   |                  |  String |                                                                   Android 앱 링크 주소                                                                  |
|         |                       |   linklos   |                  |  String |                                                                     IOS 앱 링크 주소                                                                    |
|         |                       |    linkMo   |                  |  String |                                                                     모바일 웹 링크 주소                                                                    |
|         |                       |    linkPc   |                  |  String |                                                                     PC 웹 링크 주소                                                                     |
|         |                       |   pluginId  |                  |  String |                                                                       플러그인 ID                                                                      |
|         |      quickReplies     |             |                  |  Array  |                                                                       바로연결 정보                                                                      |
|         |                       |     name    |                  |  String |                                                                       바로연결 명                                                                       |
|         |                       |   linktype  |                  |  String |                          <p>바로연결 링크타입</p><p><strong>(</strong>WL:웹링크, AL:앱링크, BK:봇키워드, MD: 메시지전달, BC : 상담톡전환, BT: 봇전환)</p>                         |
|         |                       |   linkAnd   |                  |  String |                                                                       바로연결 정보                                                                      |
|         |                       |   linklos   |                  |  String |                                                                     IOS 앱 링크 주소                                                                    |
|         |                       |    linkMo   |                  |  String |                                                                     모바일 웹 링크 주소                                                                    |
|         |                       |    linkPc   |                  |  String |                                                                     PC 웹 링크 주소                                                                     |
|         |        comments       |             |                  |  Array  |                                                                        댓글 목록                                                                       |
|         |                       |   content   |                  |  String |                                                                        댓글 본문                                                                       |
|         |                       |  createdAt  |                  |  String |                                                                       댓글 생성일                                                                       |
|         |                       |    status   |                  |  String |                                             <p>댓글 상태</p><p>(REQ:등록, INQ:문의, APR:승인, REJ:반려, REP:답변)</p>                                            |
|         |                       |   userName  |                  |  String |                                                                       댓글 작성자                                                                       |
|         |                       |  attachment |                  |  Array  |                                                                        첨부파일                                                                        |
|         |                       |             | originalFileName |  String |                                                                     업로드한 파일 이름                                                                     |
|         |                       |             |     filePath     |  String |                                                                     파일 다운로드 경로                                                                     |





### 템플릿 수정

* 등록된 템플릿을 수정합니다. 템플릿 상태가 **대기(R)**이고 템플릿 검수상태가 **등록(REG)** 또는 **반려(REJ)**인 경우에만 수정 가능합니다.
* **POST** /v3/kakao/template/update
* **Content-Type:** application/json; charset=utf-8

**Request**

|         **키**         |    **-**    |    **-**    |  **타입** | **필수** |                                                                                                                                                                           **설명**                                                                                                                                                                           |
| :-------------------: | :---------: | :---------: | :-----: | :----: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|         bizId         |             |             |  String |    O   |                                                                                                                                                                        BIZPPURIO ID                                                                                                                                                                        |
|         apiKey        |             |             |  String |    O   |                                                                                                                                                                          API 발급 키                                                                                                                                                                          |
|       senderKey       |             |             |  String |    O   |                                                                                                                                                           발신 프로필 키(senderKeyType이 G인 경우 프로필 그룹키)                                                                                                                                                           |
|     senderKeyType     |             |             |  String |    X   |                                                                                                                                                              발신 프로필 키 타입 (S:일반(default), G:그룹)                                                                                                                                                             |
|      templateCode     |             |             |  String |    O   |                                                                                                                                                                          기존 템플릿 코드                                                                                                                                                                         |
|    newTemplateCode    |             |             |  String |    X   |                                                                                                                                                    수정하려는 템플릿 코드 (영문, 숫자, 언더바(\_), 하이픈(-)만 입력 가능, 최대 30자)                                                                                                                                                   |
|      templateName     |             |             |  String |    O   |                                                                                                                                                                           템플릿 이름                                                                                                                                                                           |
|  templateMessageType  |             |             |  String |    O   |                                                                    <p>템플릿 메시지 유형</p><p><strong>(</strong>BA:기본형, EX:부가정보형, AD:광고추가형, MI:복합형)</p><p>- EX : templateExtra 필드 필수</p><p>- AD : templateAd 필드 필수, 그룹 템플릿 사용 불가</p><p>- MI : templateExtra, templateAd 필드 필수, 그룹 템플릿 사용 불가</p>                                                                   |
| templateEmphasizeType |             |             |  String |    O   | <p>템플릿 강조 유형</p><p>(NONE: 선택안함, TEXT: 강조표기형, IMAGE: 이미지형, ITEM_LIST: 아이템리스트형)</p><p>- TEXT : templateTitle, templateSubtitle 필수</p><p>- ITEM_LIST: templateItem.list 필드 필수,</p><p>templateImage(Name,Url), templateHeader, templateItemHighlight 필드 중 1개 이상 필수, templateItem.summary 필드 사용 가능</p><p>- IMAGE: templateImageName, templateImageUrl 필드 필수</p> |
|    templateContent    |             |             |  String |    O   |                                                                                                                                                                           템플릿 내용                                                                                                                                                                           |
|     templateExtra     |             |             |  String |    X   |                                                                                                                                                 <p>부가정보</p><p>- templateMessageType "EX", "MI" 선택 시 필수</p>                                                                                                                                                 |
|       templateAd      |             |             |  String |    X   |                                                                                                                                                <p>광고성메시지</p><p>- templateMessageType "AD", "MI" 선택 시 필수</p>                                                                                                                                                |
|   templateImageName   |             |             |  String |    X   |                                                                                                                                              <p>템플릿 이미지 파일명</p><p>- templateEmphasizeType "IMAGE" 선택 시 필수</p>                                                                                                                                              |
|    templateImageUrl   |             |             |  String |    X   |                                                                                                                                               <p>템플릿 이미지 링크</p><p>- templateEmphasizeType "IMAGE" 선택 시 필수</p>                                                                                                                                              |
|     templateTitle     |             |             |  String |    X   |                                                                                                                                          <p>템플릿 내용 중 강조 표기할 핵심 정보</p><p>- templateEmphasizeType "TEXT" 선택 시 필수</p>                                                                                                                                         |
|    templateSubtitle   |             |             |  String |    X   |                                                                                                                                               <p>강조 표기 보조 문구</p><p>- templateEmphasizeType "TEXT" 선택 시 필수</p>                                                                                                                                              |
|     templateHeader    |             |             |  String |    X   |                                                                                                                                                                     헤더 (최대 16자까지 입력 가능)                                                                                                                                                                    |
| templateItemHighlight |             |             |  Object |    X   |                                                                                                                                                                          아이템 하이라이트                                                                                                                                                                         |
|                       |    title    |             |  String |    O   |                                                                                                                                                        타이틀 (최대 30자까지 입력 가능, 썸네일 이미지가 있을 경우 21자까지 입력)                                                                                                                                                       |
|                       | description |             |  String |    O   |                                                                                                                                                       상세 설명 (최대 19자까지 입력 가능, 썸네일 이미지가 있을 경우 13자까지 입력)                                                                                                                                                      |
|                       |   imageUrl  |             |  String |    X   |                                                                                                                                                                썸네일 이미지 주소 (최대 500자까지 입력 가능)                                                                                                                                                                |
|      templateItem     |             |             |  Object |    X   |                                                                                                                                                                           아이템 정보                                                                                                                                                                           |
|                       |     list    |             |  Array  |    O   |                                                                                                                             <p>아이템 리스트 (최소 2개, 최대 10개)</p><p>- templateEmphasizeType "ITEM_LIST" 선택 시 필수타이틀 (최대 6자까지 입력 가능)</p>                                                                                                                            |
|                       |             |    title    |  String |    O   |                                                                                                                                                                     타이틀 (최대 6자까지 입력 가능)                                                                                                                                                                    |
|                       |             | description |  String |    O   |                                                                                                                                                                   디스크립션 (최대 23자까지 입력 가능)                                                                                                                                                                   |
|                       |   summary   |             |  Object |    X   |                                                                                                                                                                          아이템 요약 정보                                                                                                                                                                         |
|                       |             |    title    |  String |    O   |                                                                                                                                                                     타이틀 (최대 6자까지 입력 가능)                                                                                                                                                                    |
|                       |             | description |  String |    O   |                                                                                                                                                   디스크립션 (변수 및 화폐 단위, 숫자, 쉼표, 마침표만 사용 가능, 최대 14자까지 입력 가능)                                                                                                                                                   |
|      categoryCode     |             |             |  String |    O   |                                                                                                                                                                         템플릿 카테고리 코드                                                                                                                                                                        |
|      securityFlag     |             |             | Boolean |    X   |                                                                                                                                보안 템플릿 여부, OTP등 보안 메시지 일 경우 설정 발신 당시의 메인 디바이스를 제외한 모든 디바이스에 메시지 텍스트 미 노출 (true:설정, false:미설정)                                                                                                                               |
|        buttons        |             |             |  Array  |    X   |                                                                                                                                                        버튼 정보 (최대 5개 등록 가능, 바로 연결과 함께 사용 시 최대 2개로 제한)                                                                                                                                                       |
|                       |     name    |             |  String |    O   |                                                                                                                                                   <p>버튼명</p><p>- linkType "AC" 선택 시 버튼명은 "채널추가" 로 고정</p>                                                                                                                                                   |
|                       |   linkType  |             |  String |    O   |                                                                                                          버튼 링크타입 (DS:배송조회, WL:웹링크, AL:앱링크, BK:봇키워, MD: 메시지전달, AC: 채널추가, BC: 상담톡전환, BT: 봇전환, P1: 이미지 보안전송 플러그인, P2 : 개인정보이용 플러그인, P3: 원클릭 결제 플러그인)                                                                                                          |
|                       |   linkAnd   |             |  String |    X   |                                                                                                                                                                 Android 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                |
|                       |   linklos   |             |  String |    X   |                                                                                                                                                                   IOS 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                  |
|                       |    linkMo   |             |  String |    X   |                                                                                                                                                                   모바일 웹 링크 주소 (WL 사용시 필수)                                                                                                                                                                  |
|                       |    linkPc   |             |  String |    X   |                                                                                                                                                                   PC 웹 링크 주소 (WL 사용시 선택)                                                                                                                                                                   |
|                       |   pluginId  |             |  String |    X   |                                                                                                                                                                 플러그인 ID (P1, P2, P3 사용시 필수)                                                                                                                                                                |
|      quickReplies     |             |             |  Array  |    X   |                                                                                                                                             <p>바로연결 정보 (최대 10개 등록 가능)</p><p>- 상담톡 이용 채널에 한해 바로연결 기능 사용이 가능</p>                                                                                                                                             |
|                       |     name    |             |  String |    O   |                                                                                                                                                                            바로연결명                                                                                                                                                                           |
|                       |   linkType  |             |  String |    O   |                                                                                                                              <p>바로연결 링크타입</p><p><strong>(</strong>WL:웹링크, AL:앱링크, BK:봇키워드, MD: 메시지전달, BC : 상담톡전환, BT: 봇전환)</p>                                                                                                                             |
|                       |   linkAnd   |             |  String |    X   |                                                                                                                                                                 Android 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                |
|                       |   linklos   |             |  String |    X   |                                                                                                                                                                   IOS 앱 링크 주소 (AL 사용시 필수)                                                                                                                                                                  |
|                       |    linkMo   |             |  String |    X   |                                                                                                                                                                   모바일 웹 링크 주소 (WL 사용시 필수)                                                                                                                                                                  |
|                       |    linkPc   |             |  String |    X   |                                                                                                                                                                   PC 웹 링크 주소 (WL 사용시 선택)                                                                                                                                                                   |



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

|     **키**     | **타입** | **필수** |                          **설명**                          |
| :-----------: | :----: | :----: | :------------------------------------------------------: |
|     bizId     | String |    O   |                       BIZPPURIO ID                       |
|     apiKey    | String |    O   |                         API 발급 키                         |
|   senderKey   | String |    O   |     <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p>    |
| senderKeyType | String |    X   |        <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>       |
|  templateCode | String |    O   | <p>템플릿 코드<br>(영문, 숫자, 언더바(_), 하이픈(-)만 입력 가능, 최대 30자)</p> |



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

|     **키**     | **타입** | **필수** |                               **설명**                               |
| :-----------: | :----: | :----: | :----------------------------------------------------------------: |
|     bizId     | String |    O   |                            BIZPPURIO ID                            |
|     apiKey    | String |    O   |                              API 발급 키                              |
|   senderKey   | String |    O   | <p>발신 프로필 키<br><strong></strong>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |             <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>            |
|  templateCode | String |    O   |                               템플릿 코드                               |
|    comment    | String |    X   |                    의견 또는 문의사항 (최대 500자까지 입력 가능)                    |

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

**Request**

|     **키**     | **타입** | **필수** |                       **설명**                      |
| :-----------: | :----: | :----: | :-----------------------------------------------: |
|     bizId     | String |    O   |                    BIZPPURIO ID                   |
|     apiKey    | String |    O   |                      API 발급 키                     |
|   senderKey   | String |    O   | <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |    <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>    |
|  templateCode | String |    O   |                       템플릿 코드                      |
|    comment    | String |    O   |       <p>의견 또는 문의사항<br>(최대 500자까지 입력 가능)</p>      |
|   attachment  |  File  |    X   |           업로드할 파일의 절대 경로, 다수의 파일 업로드 가능           |



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

|     **키**     | **타입** | **필수** |                       **설명**                      |
| :-----------: | :----: | :----: | :-----------------------------------------------: |
|     bizId     | String |    O   |                    BIZPPURIO ID                   |
|     apiKey    | String |    O   |                      API 발급 키                     |
|   senderKey   | String |    O   | <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |    <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>    |
|  templateCode | String |    O   |                       템플릿 코드                      |

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

|     **키**     | **타입** | **필수** |                       **설명**                      |
| :-----------: | :----: | :----: | :-----------------------------------------------: |
|     bizId     | String |    O   |                    BIZPPURIO ID                   |
|     apiKey    | String |    O   |                      API 발급 키                     |
|   senderKey   | String |    O   | <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |    <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>    |
|  templateCode | String |    O   |                       템플릿 코드                      |



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

|     **키**     | **타입** | **필수** |                       **설명**                      |
| :-----------: | :----: | :----: | :-----------------------------------------------: |
|     bizId     | String |    O   |                    BIZPPURIO ID                   |
|     apiKey    | String |    O   |                      API 발급 키                     |
|   senderKey   | String |    O   | <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |    <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>    |
|  templateCode | String |    O   |                       템플릿 코드                      |



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

|     **키**     | **타입** | **필수** |                       **설명**                      |
| :-----------: | :----: | :----: | :-----------------------------------------------: |
|     bizId     | String |    O   |                    BIZPPURIO ID                   |
|     apiKey    | String |    O   |                      API 발급 키                     |
|   senderKey   | String |    O   | <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |    <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>    |
|  templateCode | String |    O   |                       템플릿 코드                      |



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

|     **키**     | **타입** | **필수** |                       **설명**                      |
| :-----------: | :----: | :----: | :-----------------------------------------------: |
|     bizId     | String |    O   |                    BIZPPURIO ID                   |
|     apiKey    | String |    O   |                      API 발급 키                     |
|   senderKey   | String |    O   | <p>발신 프로필 키<br>(senderKeyType이 G인 경우 프로필 그룹키)</p> |
| senderKeyType | String |    X   |    <p>발신 프로필 키 타입<br>(S:일반(default), G:그룹)</p>    |
|  templateCode | String |    O   |                       템플릿 코드                      |



**Response**

|  **키**  | **타입** |    **설명**   |
| :-----: | :----: | :---------: |
|   code  | String |    결과 코드    |
| message | String | 실패 시 결과 메시지 |

