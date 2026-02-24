---
name: google-docs-writer
description: Exports PM artifacts (PRDs, user stories, idea assessments) to Google Docs with professional formatting and team collaboration features. Handles document creation, formatting, sharing, and organization in Google Drive. Use when exporting documents, sharing with team, creating Google Docs, formatting PM deliverables, or organizing Drive folders.
---

# Google Docs 내보내기 및 문서 관리

## 목적

다른 스킬(idea-generation, prd-documentation, userstory-documentation)에서 생성된 PM 산출물을 전문적으로 포맷팅된 Google Docs로 내보내 팀 협업 및 이해관계자 검토를 지원한다.

**모든 내보낸 문서는 한글로 작성하며 프로젝트 폴더 구조를 따른다.**

---

## 핵심 워크플로우

```
PM 산출물 수신 (PRD / 유저스토리 / 아이디어)
    ↓
1. 콘텐츠 준비 — 구조 파싱, 포맷 규칙 매핑
    ↓
2. 문서 생성/업데이트 — createGoogleDoc 또는 updateGoogleDoc
    ↓
3. 포맷팅 적용 — 제목 계층, 텍스트 스타일, 단락 간격
    ↓
4. 폴더 정리 — 적절한 폴더로 이동, 필요 시 폴더 생성
    ↓
5. 공유 링크 반환
```

---

## 문서 유형별 구조

### PRD 문서
- 제목 페이지 (문서명, 작성자, 날짜, 버전, 상태)
- 목차 (자동 생성)
- 11개 섹션 (H2 헤딩)
- 목표/요구사항/위험 표 (포맷팅 적용)

### 유저스토리 문서
- 제목 페이지 (기능명, Epic, 스프린트, 작성자)
- 스토리 요약 (스토리 수, 우선순위 분류)
- 각 스토리 (H3 제목, 이탤릭체 스토리 구문, AC 목록)

### 아이디어 검증 문서
- 제목 페이지 (아이디어명, 검증 상태, 결정)
- 아이디어 개요 (One-liner, 문제, 타겟)
- 검증 프레임워크 (JTBD, 경쟁사, 가치 제안, DVF, RICE, 10문항)
- 권고사항 (Go/No-Go 강조 표시)

> 각 문서 타입별 상세 포맷 규칙은 [references/templates.md](references/templates.md) 참조

---

## 폴더 구조

```
📁 Projects/
├── 📁 {프로젝트명}/
│   ├── 아이디어 검증.gdoc
│   ├── PRD.gdoc
│   ├── 유저스토리.gdoc
│   └── 프로젝트 로그.gdoc
```

기존 문서 업데이트 시:
1. `mcp__google-drive__search`로 문서 검색
2. `mcp__google-drive__getGoogleDocContent`로 현재 내용 확인
3. `mcp__google-drive__updateGoogleDoc`으로 콘텐츠 교체

---

## 포맷팅 기준 (요약)

| 요소 | 스타일 |
|------|--------|
| 문서 제목 (H1) | 24pt, Bold |
| 섹션 (H2) | 18pt, Bold |
| 서브섹션 (H3) | 14pt, Bold |
| 본문 | 11pt, Regular |
| 표 헤더 | Bold, 연회색 배경 |

> 상세 포맷팅 가이드 (색상, 간격, 테이블 스타일)는 [references/formatting.md](references/formatting.md) 참조

---

## 오류 처리

| 오류 | 처리 방법 |
|------|----------|
| 문서 없음 | 제목으로 검색 후 사용자 확인, 없으면 새로 생성 |
| 포맷팅 실패 | 오류 건너뛰고 plain text로 진행, 사용자에게 알림 |
| 폴더 생성 실패 | 기존 폴더 사용 또는 루트에 저장 |
| 권한 없음 | 권한 문제 설명 후 접근 요청 안내 |
