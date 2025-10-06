# Repository Guidelines

## 프로젝트 구조 및 모듈 구성
핵심 수치와 전통 슬롯 개수는 `common/defines/tmaps_defines.txt`에서 관리합니다. 사용자 인터페이스 배치는 `interface/topbar_traditions_view.gui`에 정의되어 있으니 행 오프셋과 위젯 크기를 여기서 조정하세요. 문자열은 `localisation/tmaps_l_english.yml`에 있으며 UTF-8 with BOM 포맷을 유지합니다. `descriptor.mod`는 지원 버전을 선언하므로 Stellaris 패치에 맞춰 갱신하고, `thumbnail.png`는 워크숍 미리보기로 사용하므로 교체하지 않는 한 수정하지 마세요.

## 빌드·테스트·개발 명령
별도의 자동 빌드가 없어 로컬 스크립트를 자유롭게 활용하면 됩니다. 릴리스를 준비할 때는 `zip -r dist/Eight_Traditions_Slots_Standard.zip descriptor.mod common interface localisation thumbnail.png`로 패키징합니다. 빠른 반복 작업은 리포지토리를 `~/Documents/Paradox Interactive/Stellaris/mod/Eight_Traditions_Slots_Standard`에 복사하고 런처 항목을 갱신하세요.

## 코딩 스타일 및 네이밍 규칙
`.gui` 파일은 탭 들여쓰기를, `.txt` 데이터 블록은 두 칸 들여쓰기를, 로컬라이제이션은 YAML 스타일을 지킵니다. 식별자에는 `tmaps_` 접두사를 재사용해 충돌을 방지합니다. 인라인 주석은 `#` 뒤에 짧게 설명하고 오래된 주석은 삭제합니다. 변수 블록은 기능 단위(예: 승천 특전, 전통 행)로 묶고 기존 순서를 유지해 가독성을 높입니다.

## 테스트 지침
Stellaris를 `-debug_mode`로 실행한 뒤 새 저장 파일을 불러 UI가 겹치지 않는지 확인하세요. 오류는 `~/Documents/Paradox Interactive/Stellaris/logs/error.log`에서 확인할 수 있으며, 누락된 로컬라이제이션 키나 GUI 파싱 실패를 여기서 찾습니다. 번역을 조정하면 특수문자가 올바르게 표시되는지와 `$KEY$` 플레이스홀더가 남지 않았는지 확인하세요.

## 커밋 및 PR 가이드라인
Git 기록은 짧은 명령형 메시지를 사용하므로 `전통 행 오프셋 조정`처럼 구체적으로 작성합니다. Pull Request에는 변경이 미치는 플레이/UI 영향, 수정한 파일 목록, 관련 워크숍 이슈를 요약하세요. GUI 변경 시 전후 스크린샷을 첨부하고 저장 호환성에 대한 안내가 필요하면 명시합니다.

## 배포 및 패키징 팁
릴리스 전에 `descriptor.mod`의 버전 정보가 대상 Stellaris 패치와 일치하는지 확인하세요. 생성한 zip을 첨부하고 동일한 변경 요약을 Steam 워크숍 변경 로그에 게시합니다. Overhaul 태그나 다른 GUI 모드와의 충돌 가능성을 미리 안내하여 플레이어가 로드 순서를 조정할 수 있게 하세요.
