---
description: api 응답코드에 대한 상세내용입니다.
---

# 코드 정의



<table><thead><tr><th width="112.5" align="center">code</th><th align="center">설명</th></tr></thead><tbody><tr><td align="center">200</td><td align="center">요청 성공</td></tr><tr><td align="center">101</td><td align="center">사용자 없음</td></tr><tr><td align="center">102</td><td align="center">유효하지 않은 API key</td></tr><tr><td align="center">103</td><td align="center">중지된 사용자</td></tr><tr><td align="center">403</td><td align="center">권한 없음</td></tr><tr><td align="center">405</td><td align="center">파라미터 오류</td></tr><tr><td align="center">504</td><td align="center">템플릿 코드 중복</td></tr><tr><td align="center">505</td><td align="center">템플릿 이름 중복</td></tr><tr><td align="center">506</td><td align="center">템플릿 내용이 1000자 초과</td></tr><tr><td align="center">507</td><td align="center">유효하지 않은 발신프로필</td></tr><tr><td align="center">508</td><td align="center">요청한 데이터가 없음, 삭제 상태의 데이터 요청 시 응답</td></tr><tr><td align="center">509</td><td align="center">요청을 처리할 수 있는 상태가 아님 (ex, 템릿 검수 요청이 가능한 상태가 아님)</td></tr><tr><td align="center">510</td><td align="center">템플릿의 버튼/바로연결 형식이 유효하지 않음</td></tr><tr><td align="center">511</td><td align="center">대표링크/버튼/바로연결의 링크가 유효하지 않음</td></tr><tr><td align="center">512</td><td align="center">발신프로필 추가 및 그룹 내 발신프로필 추가가 제한된 상태</td></tr><tr><td align="center">513</td><td align="center">메시지 결과 수신 채널이 올바르지 않음</td></tr><tr><td align="center">514</td><td align="center">비즈니스 인증이 필요한 카카오톡 채널</td></tr><tr><td align="center">525</td><td align="center">템플릿의 카테고리가 유효하지 않음</td></tr><tr><td align="center">530</td><td align="center">유효하지 않은 플러그인</td></tr><tr><td align="center">600</td><td align="center">이미지 업로드 실패</td></tr><tr><td align="center">610</td><td align="center">파일 업로드 실패</td></tr><tr><td align="center">611</td><td align="center">첨부파일의 크기가 50MB를 초과</td></tr><tr><td align="center">612</td><td align="center">첨부파일 형식이 유효하지 않음</td></tr><tr><td align="center">613</td><td align="center">첨부파일의 개수가 10개를 초과</td></tr><tr><td align="center">614</td><td align="center">첨부파일이 존재하지 않음</td></tr><tr><td align="center">801~805</td><td align="center">발신프로필 등록이 차단된 상태</td></tr></tbody></table>



<table><thead><tr><th width="113">code</th><th width="320.66666666666663">message</th><th>설명</th></tr></thead><tbody><tr><td>0000</td><td>-</td><td>요청 성공</td></tr><tr><td></td><td>MissingRequiredParameterException</td><td>필수 파라미터가 없음</td></tr><tr><td></td><td>InvalidImageLengthException</td><td>이미지 용량 초과</td></tr><tr><td></td><td>InvalidImageShapeException</td><td>발송할  없는 이미 사이즈</td></tr><tr><td></td><td>InvalidImageFormatException</td><td>지원하지 않는 이미지 형식</td></tr><tr><td></td><td>FailedToUploadImageException</td><td>내부 시스템 오류로 업로드 실패</td></tr><tr><td></td><td>result.failure[].error.message 참고</td><td>일부 이미지 업로드 실패</td></tr><tr><td></td><td>Request Entity Too Large</td><td>이미지 용량 초과</td></tr></tbody></table>



