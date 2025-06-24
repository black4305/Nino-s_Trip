# CLAUDE.md

이 파일은 Claude Code (claude.ai/code)가 이 저장소에서 작업할 때 참고하는 가이드입니다.

## 프로젝트 개요

**Nino's Trip**은 Flask로 구축된 한국 여행 가이드 웹 애플리케이션으로, 여러 카테고리에 걸쳐 가족 친화적인 장소 추천을 제공합니다. 이 애플리케이션은 "NeStory"라는 PWA(Progressive Web App)로 서비스됩니다.

## 기술 스택

- **백엔드**: Flask (Python 웹 프레임워크)
- **데이터베이스**: 다양한 콘텐츠 카테고리별 SQLite 데이터베이스
- **프론트엔드**: 바닐라 JavaScript와 HTML/CSS (빌드 프로세스 없음)
- **배포**: Vercel 배포 구성

## 개발 명령어

### 로컬 개발
```bash
python app.py
```
Flask 개발 서버를 localhost:5000에서 실행

### 배포
Vercel 배포를 위한 프로젝트 구성:
- `vercel.json` - Vercel 구성 파일
- `requirements.txt` - Flask 종속성만 포함하도록 최적화

## 데이터베이스 구조

애플리케이션은 `/data` 디렉토리에 여러 SQLite 데이터베이스를 사용:
- `event.db` - 월별 이벤트 및 활동
- `nino-trip.db` - 가족 여행 추천
- `forest.db` - 숲/자연 장소
- `cafe.db` - 카페 추천
- `kids_restaurant.db` - 아이 친화적인 레스토랑
- `culture_center.db` - 문화센터 및 활동
- `activity.db` - 다양한 활동
- `db.sqlite3` - 사용자 문의 메인 데이터베이스

## 애플리케이션 구조

### 주요 파일
- `app.py` - 라우트 핸들러와 데이터베이스 함수가 있는 Flask 애플리케이션
- `templates/index.html` - 탭 네비게이션이 있는 메인 애플리케이션 인터페이스
- `templates/admin.html` - 관리자 인터페이스 (비밀번호: 0819)
- `static/script.js` - 탭 전환용 클라이언트 사이드 JavaScript
- `static/style.css` - 다크 테마 반응형 스타일링

### 주요 기능
- 탭 인터페이스를 통한 다중 카테고리 여행 가이드
- 사용자 문의 관리를 위한 관리자 패널
- 문의 관리를 위한 REST API 엔드포인트
- 오프라인 지원이 포함된 PWA 기능
- Google Analytics 통합

### API 엔드포인트
- `POST /api/inquiries` - 새 문의 제출
- `GET /api/inquiries` - 모든 문의 조회
- `PATCH /api/inquiries/<id>` - 문의 응답 업데이트
- `DELETE /api/inquiries/<id>` - 문의 삭제
- `GET/POST /admin` - 관리자 인증 및 인터페이스

## 데이터 처리

데이터베이스 함수는 렌더링 전 콘텐츠 포맷팅(대시로 구분된 항목을 줄바꿈으로 변환)을 포함합니다. 각 카테고리는 디스플레이에 적합하게 콘텐츠를 포맷팅하는 자체 데이터 검색 함수를 가지고 있습니다.