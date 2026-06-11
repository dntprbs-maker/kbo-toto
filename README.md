# ⚾ KBO 야구 분석 및 자동 배포 시스템 (kbo-toto)

구글 드라이브(Google Drive)에 업로드된 최신 KBO 야구 분석 및 경기 일정 데이터를 감시하여, 깃허브 저장소로 실시간 자동 배포하는 자동화 프로젝트입니다.

---

## 🛠️ 시스템 아키텍처 (System Architecture)

본 프로젝트는 통합 자동화 플랫폼인 **Make.com**을 기반으로 구축되었으며, 다음과 같은 흐름으로 데이터가 실시간 동기화됩니다.

1. **구글 드라이브 감시 (Watch Files)**
   - 지정된 드라이브 폴더 내 `index.html` 파일의 변경 사항을 15분 주기로 실시간 감시합니다.
2. **데이터 다운로드 (Download a File)**
   - 변경이 감지되면 최신 상태의 HTML 파일을 동적으로 다운로드합니다.
3. **깃허브 API 식별자 조회 (Get File SHA)**
   - 깃허브 파일 업데이트 규칙(API 사양)에 맞추어 기존 파일의 고유 버전 코드(`sha`)를 자동으로 조회합니다.
4. **Base64 암호화 및 파일 업데이트 (Update Content)**
   - 다운로드한 HTML 데이터를 깃허브 전송 규격인 `Base64` 형식으로 자동 인코딩한 후, 저장소의 `main` 브랜치에 안전하게 덮어씁니다.

---

## 🚀 기술 스택 (Tech Stack)

- **Automation:** Make.com (구 Integromat)
- **Data Source:** Google Drive API
- **Deployment:** GitHub REST API v3 / GitHub Pages
- **Language:** HTML5 / Markdown

---

## 📌 주요 특징 (Features)

- **100% 무인 자동화:** 사람이 매번 깃허브에 코드를 푸시할 필요 없이, 구글 드라이브 파일 수정만으로 웹사이트가 즉시 갱신됩니다.
- **안정적인 API 연동:** REST API의 `PUT` 메서드와 `sha` 동적 매핑을 통해 파일 충돌 없는 깨끗한 데이터 업데이트를 보장합니다.

---
_Generated & Managed automatically by Make.com Automation System._
