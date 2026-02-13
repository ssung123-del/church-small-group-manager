# Church Small Group Manager

교회 소그룹 편성/운영을 위한 단일 HTML 기반 관리 도구입니다.

## 기능
- 리더/소속원 등록, 수정, 삭제
- 주소 기반 지도/거리 추천 매칭
- 중복 검사
- CSV 업로드/내보내기
- 조직도/현황 대시보드

## 실행 방법
1. 이 저장소를 클론합니다.
2. `index.html`을 브라우저에서 엽니다.
3. 첫 화면에서 아래 값을 입력해 연결합니다.
   - Apps Script Web App URL
   - 보안 토큰(APP_TOKEN)
   - Google Maps JavaScript API 키

## Google Apps Script 설정
`index.html`의 안내에 따라 Apps Script를 배포하세요.

주의:
- `GAS_CODE` 안의 `APP_TOKEN="CHANGE_ME_WITH_A_LONG_RANDOM_TOKEN"`를 반드시 변경하세요.
- 변경 후 웹앱을 재배포하세요.

## 보안 가이드
- 실제 API 키/토큰은 코드에 하드코딩하지 마세요.
- Google Maps API 키는 다음 제한을 반드시 설정하세요.
  - HTTP referrer 제한
  - API 제한(Maps JavaScript API)
- 키/토큰이 노출되면 즉시 폐기 후 재발급하세요.

## 저장 정책
연결 화면의 체크박스로 설정 저장 방식을 선택할 수 있습니다.
- 체크 ON: 브라우저 로컬 저장소에 유지
- 체크 OFF: 세션 저장(탭 종료 시 삭제)

## 파일 구조
- `index.html`: 전체 애플리케이션(UI/로직)

## 라이선스
개인/교회 내부 사용 목적에 맞게 조정해 사용하세요.
