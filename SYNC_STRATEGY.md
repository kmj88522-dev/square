# Square Sync Strategy

이 문서는 장기 동기화 방향 메모다. 현재 v0.1/v0.2 작업에서 Google 로그인, Google Drive 연동, 서버 동기화는 구현하지 않는다.

## 핵심 원칙

- 사용자가 쓰는 데이터 원본은 하나여야 한다.
- Book, Page, Square의 content, value, style, actions는 공통 데이터다.
- x, y, width, height, visible은 desktop, tablet, mobile 레이아웃으로 분리한다.
- PC, 태블릿, 모바일은 같은 데이터를 보되, 화면 배치만 다르게 편집할 수 있어야 한다.

## 현재 단계

- 저장 위치: localStorage
- 백업 방식: JSON 내보내기/불러오기
- 기기별 레이아웃: `layoutsByDevice.desktop/tablet/mobile`
- 후방호환: 기존 `x`, `y`, `width`, `height`, `visible` 필드는 유지

## Google 로그인/Drive 후보 설계

장기적으로는 다음 방식이 가장 단순하다.

1. Google OAuth 로그인
2. Google Drive `appDataFolder` 또는 사용자가 고른 Drive 폴더에 Square JSON 저장
3. 각 Book 또는 전체 workspace를 하나의 JSON 파일로 동기화
4. 수정 시 `updatedAt`과 revision 정보를 비교
5. 충돌이 있으면 자동 병합보다 사용자 선택을 우선

## 피해야 할 것

- v0.1에서 Google Drive 연동을 성급히 구현하지 않는다.
- 로그인 없이는 다른 기기 자동 동기화를 약속하지 않는다.
- 기기별 레이아웃 때문에 content/style/actions가 복제되지 않게 한다.
- B001 같은 기존 code 체계를 S001로 즉시 바꾸지 않는다.

## 다음 구현 후보

- 설정 화면에 저장 위치 표시
- JSON 백업 파일 구조 안정화
- Google Drive 연동 전용 데이터 어댑터 설계
- 충돌 감지용 `workspaceUpdatedAt`, `deviceUpdatedAt` 추가
