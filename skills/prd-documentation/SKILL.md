---
name: prd-documentation
description: Assists in creating and reviewing Product Requirements Documents (PRDs). Provides both DOCUMENTATION (writing PRDs with structured templates) and REVIEW (validating PRDs against 6 criteria with scoring). Use when writing PRDs, creating product specs, documenting requirements, defining success metrics, reviewing PRD quality, or requesting feedback on product specifications.
---

# PRD 작성 및 검토

## 작동 모드

- **DOCUMENTATION 모드**: 새 PRD 작성 또는 기존 초안 확장
- **REVIEW 모드**: PRD 품질 검증 및 점수 평가

---

## DOCUMENTATION 모드: PRD 작성

### PRD 구조 (11개 섹션)

1. **Executive Summary** — 제품명, 문제, 타겟, 솔루션, 핵심 지표
2. **문제 정의 및 컨텍스트** — 문제 설명, 근거 데이터, 타겟 사용자, 현재 대안
3. **목표 및 성공 지표** — 비즈니스/사용자 목표, SMART 목표, KPI 표
4. **유저스토리 및 유스케이스** — 주요 플로우, 엣지 케이스
5. **기능 요구사항** — 기능별 설명, 우선순위(Must/Should/Nice), 의존성
6. **비기능 요구사항** — 성능, 보안, 접근성, 신뢰성
7. **범위 및 제약사항** — In Scope, Out of Scope, 제약 조건
8. **디자인 및 기술 고려사항** — UI/UX 가이드라인, 아키텍처 개요
9. **런치 및 롤아웃 계획** — 출시 일정, 단계별 롤아웃, 성공 기준
10. **위험 요소 및 완화 방안** — 위험 목록(영향/확률), 미해결 질문
11. **부록** — 용어집, 참고 문서, 리서치 결과물

> 각 섹션의 상세 작성 가이드와 템플릿은 [references/prd-structure.md](references/prd-structure.md)를 참조한다.

### PRD 작성 원칙

- **What을 정의, How는 팀에게 위임** — 구현 방법을 지시하지 않는다
- **데이터 기반** — 주장을 근거로 뒷받침한다
- **우선순위 명시** — 모든 것이 Must-have가 될 수 없다
- **성공 기준 명확화** — 무엇을 달성했을 때 완료인지 정의한다

---

## REVIEW 모드: PRD 검토

### 검토 프로세스

1. Google Drive에서 PRD Review Guide 로드:
   - **ID**: `1abFQ6IDCEyB1GP0WTSkwKQHeB_iQL5wlZkSEnxdvhYU`
   - `mcp__google-drive__getGoogleDocContent` 사용

2. 6가지 기준으로 평가 (각 0-100점):

| # | 평가 영역 | 핵심 질문 |
|---|-----------|----------|
| I | 전반적인 명확성 및 목적 | 모든 이해관계자가 이해할 수 있는가? |
| II | 문제 정의 및 근거 | 문제가 명확하고 증거로 뒷받침되는가? |
| III | 목표 및 Impact 크기 | SMART 목표이며 충분한 임팩트인가? |
| IV | 솔루션 및 우선순위 | 요구사항이 완전하고 우선순위가 명확한가? |
| V | 성공 지표 및 측정 계획 | 명확한 지표와 측정 방법이 있는가? |
| VI | 한계점과 잠재 위험 | 위험이 식별되고 완화 방안이 있는가? |

**점수 기준:** 90-100 우수 / 70-89 양호 / 50-69 개선필요 / 50미만 재작성

3. 검토 결과 출력 — 상세 포맷은 [references/review-format.md](references/review-format.md) 참조

### 최종 권고사항

- ✅ **승인 (Approved)** — 개발 진행 가능 (평균 80점 이상)
- ⚠️ **부분 승인 (Approved with Revisions)** — 소규모 수정 후 진행 (60-79점)
- ❌ **반려 (Revision Required)** — 대폭 수정 필요 (60점 미만)

---

## 연계 워크플로우

- **이전 단계**: `idea-generation` 스킬에서 검증된 아이디어 수신
- **다음 단계**: 승인된 PRD를 `userstory-documentation` 스킬로 전달
- **문서 저장**: `google-docs-writer` 스킬로 Google Docs 내보내기
