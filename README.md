# Church Small Group Manager (Firebase)

교회 소그룹 편성/운영을 위한 단일 HTML 기반 도구입니다.
현재 백엔드는 **Firebase Firestore**를 사용합니다.

## 주요 기능
- 리더/소속원 등록, 수정, 삭제
- 주소 기반 지도/거리 추천 배정
- 중복 검사
- CSV 대량 업로드/내보내기
- 조직도/현황 대시보드

## 빠른 시작
1. Firebase 프로젝트 생성
2. Firestore Database 활성화
3. Firebase 콘솔의 Web 앱 `Firebase config` JSON 준비
4. Google Maps JavaScript API 키 준비
5. `index.html` 열기 후 연결 화면에서 아래 입력
   - Firebase config JSON
   - Google Maps JavaScript API 키

## 대량 입력 전략 (속도 최적화)
CSV 업로드 시 아래를 권장합니다.
- 가능한 경우 `lat`,`lng` 컬럼을 함께 넣기
  - 좌표가 있으면 지오코딩 호출을 생략해서 매우 빨라집니다.
- 리더/소속원 저장은 Firestore `batch commit`으로 처리됩니다.
- 소속원 대량 입력 후 리더별 인원 수(`current_members`)를 일괄 재계산합니다.

## CSV 권장 컬럼
### 리더
- `name`(필수)
- `address` 또는 `lat`,`lng`(둘 중 하나 필수)
- `role`,`gender`,`birthdate`,`contact`,`max_capacity`

### 소속원
- `name`(필수)
- `address` 또는 `lat`,`lng`(둘 중 하나 필수)
- `role`,`gender`,`birthdate`,`contact`,`status`,`leader_name`

## Firestore 컬렉션
- `leaders`
- `members`

문서 공통 필드
- `id`(숫자)

## 보안 체크리스트
- API 키/토큰을 코드에 하드코딩하지 않기
- Google Maps API 키 제한 필수
  - HTTP referrer 제한
  - API 제한: Maps JavaScript API
- Firestore Rules를 운영 정책에 맞게 제한

## 설정 저장 정책
연결 화면의 체크박스로 설정 저장 방식 선택
- ON: `localStorage` 유지
- OFF: `sessionStorage` 유지(탭 종료 시 삭제)

## 파일 구조
- `index.html`: 전체 애플리케이션(UI + Firebase 데이터 로직)

## 라이선스
개인/교회 내부 사용 목적에 맞게 조정해 사용하세요.
