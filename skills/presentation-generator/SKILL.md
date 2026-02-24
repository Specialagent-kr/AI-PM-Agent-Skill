---
name: presentation-generator
description: Creates professional presentation slides for PM deliverables (idea validations, PRD reviews, roadmaps) using Google Slides. Generates persuasive, well-designed presentations with clear structure, visual hierarchy, and professional styling. Use when creating presentations, pitch decks, stakeholder reviews, or executive summaries.
---

# 프레젠테이션 생성

## 목적

아이디어 검증, PRD 검토, 로드맵 등 PM 산출물을 이해관계자 커뮤니케이션용 Google Slides 발표자료로 변환한다.

**모든 발표자료는 한글로 작성하며 프로젝트 폴더에 저장한다.**

---

## 핵심 워크플로우

```
PM 산출물 수신 (아이디어 / PRD / 로드맵)
    ↓
1. 콘텐츠 파싱 — 핵심 데이터 포인트 추출
    ↓
2. 슬라이드 구성 — 발표 유형별 슬라이드 구조 선택
    ↓
3. Google Slides 생성 — createGoogleSlides 호출
    ↓
4. 스타일 적용 — 색상, 타이포그래피, 레이아웃
    ↓
5. 폴더 이동 — /Projects/{프로젝트명}/에 저장
    ↓
6. 공유 링크 반환
```

---

## 발표자료 유형별 구조

### 아이디어 검증 (20슬라이드)

```
[1] 타이틀       [2] 목차
[3] 요약         [4] 프로젝트 목표
[5] 문제 정의    [6] 제안 솔루션
[7] 타겟 시장    [8] 경쟁사 분석
[9] 섹션 구분    [10] 문제-솔루션 적합성
[11] 시장/실현가능성  [12] 비즈니스 케이스
[13] RICE 점수   [14] DVF 평가
[15] 검증 요약   [16] 주요 리스크
[17] 섹션 구분   [18] 즉시 실행 계획
[19] 단기 로드맵 [20] 결론/의사결정 요청
```

### PRD 검토 (18슬라이드)

```
[1] 타이틀  [2] 목차  [3] 문제 정의  [4] 사용자 리서치
[5] 솔루션 개요  [6] 유저스토리  [7] 기능 요구사항
[8] 비기능 요구사항  [9] 성공 지표  [10] 디자인 목업
[11] 기술 아키텍처  [12] 구현 단계  [13] 리소스 요구사항
[14] 리스크/완화  [15] GTM 계획  [16] 타임라인
[17] 예산/ROI  [18] 승인 요청
```

### 로드맵 (15슬라이드)

```
[1] 타이틀  [2] 목차  [3] 비전/전략
[4-7] 분기별 우선순위 (Q1-Q4)
[8-9] 기능 심층 분석
[10] 리소스 배분  [11] 의존성  [12] 리스크
[13] 성공 지표  [14] 다음 단계  [15] Q&A
```

> 각 슬라이드 상세 구조는 [references/slide-templates.md](references/slide-templates.md) 참조

---

## 디자인 기준 (요약)

| 요소 | 기준 |
|------|------|
| 타이틀 폰트 | 32-44pt, Bold |
| 본문 폰트 | 18-20pt, Regular |
| 슬라이드당 글머리 | 최대 5-6개 |
| 여백 | 사방 72pt |
| 메인 색상 | 딥 블루 (#1a237e) |
| 배경 | 흰색 (#ffffff) |

> 색상, 레이아웃, 텍스트 상세 규칙은 [references/design-guide.md](references/design-guide.md) 참조

---

## 폴더 구조

```
📁 Projects/
├── 📁 {프로젝트명}/
│   └── 발표자료.gslides
```

기존 발표자료 업데이트 시:
1. `mcp__google-drive__search`로 파일 검색
2. `mcp__google-drive__getGoogleSlidesContent`로 현재 내용 확인
3. `mcp__google-drive__updateGoogleSlides`로 슬라이드 교체

---

## 오류 처리

| 오류 | 처리 방법 |
|------|----------|
| 슬라이드 없음 | 제목으로 검색 후 새로 생성 |
| 스타일 적용 실패 | plain 텍스트로 진행, 사용자에게 알림 |
| 폴더 생성 실패 | 루트에 저장 |
