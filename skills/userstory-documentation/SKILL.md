---
name: userstory-documentation
description: Assists in creating and reviewing User Stories with Acceptance Criteria. Provides both DOCUMENTATION (writing user stories following INVEST principles and 3C's framework) and REVIEW (validating stories against comprehensive checklist). Use when writing user stories, creating acceptance criteria, breaking down features, refining backlog items, reviewing story quality, or requesting feedback on user stories.
---

# 유저스토리 작성 및 검증

## 작동 모드

- **DOCUMENTATION 모드**: PRD 요구사항을 유저스토리로 분해 및 작성
- **REVIEW 모드**: 기존 유저스토리 품질 검증 및 Pass/Fail 판정

---

## DOCUMENTATION 모드: 유저스토리 작성

### 표준 템플릿

```
제목: [동사] [객체]

As a [구체적 사용자 페르소나]
I want to [구체적 액션/기능]
So that [구체적 혜택/결과]

컨텍스트:
[배경 정보, 비즈니스 근거]

수락 기준:
Given [전제 조건]
When [액션/이벤트]
Then [기대 결과]

메모:
- [디자인 참조, 기술 고려사항]
- [의존성, 가정]
```

### 기능을 유저스토리로 분해하는 4단계

**1단계 — 사용자 페르소나 파악**
- 이 기능을 사용할 사람은 누구인가?
- 역할/권한의 차이가 있는가?
- 각자의 목표는 무엇인가?

**2단계 — 사용자 플로우 매핑**
- 기능을 통한 주요 경로
- 대안 플로우
- 오류 상태

**3단계 — 스토리 계층 구조 생성**
```
Epic: [고수준 기능]
├── Story 1: [독립적 사용자 가치]
├── Story 2: [독립적 사용자 가치]
└── Story 3: [독립적 사용자 가치]
```

**4단계 — 수직 슬라이싱 (Vertical Slicing)**
- 각 스토리가 엔드투엔드 가치 전달
- 수평 슬라이싱(프론트엔드/백엔드/DB) 지양
- 반복 가능한 납품 가능

> 수락 기준(AC) 포맷 옵션 및 예시는 [references/story-format.md](references/story-format.md) 참조

---

## REVIEW 모드: 유저스토리 검증

### 검증 프로세스

1. Google Drive에서 User Story Review Checklist 로드:
   - **ID**: `1xZvwxbvgpDmLC9r0Ni58DNh0hAvDhwAi9hzVxvAG7cs`
   - `mcp__google-drive__getGoogleDocContent` 사용

2. 3단계 검증 프레임워크 적용:

**Part 1: 3 C's (기본 요소)**
| 항목 | 평가 기준 | Pass 조건 |
|------|-----------|----------|
| Card | 표준 형식 준수, 제목 명확성, 설명 간결성 | 3가지 모두 충족 |
| Conversation | 팀 논의 증거, 논의 내용 문서화 | 협업 증거 있음 |
| Confirmation | AC가 명확·측정 가능·테스트 가능, 엣지 케이스 포함 | QA가 테스트 작성 가능 |

**Part 2: INVEST 원칙**
| 원칙 | 핵심 질문 | Pass 조건 |
|------|-----------|----------|
| Independent | 독립적으로 개발·테스트·배포 가능한가? | 다른 스토리 의존성 최소화 |
| Negotiable | 결과(What)에 집중하고 구현(How)은 열려 있는가? | 팀이 방법 논의 가능 |
| Valuable | 사용자/비즈니스에 명확한 가치가 있는가? | "So that" 절에 혜택 명시 |
| Estimable | 팀이 작업량을 추정할 수 있는가? | 주요 미지수 없음 |
| Small | 1 스프린트 내 완료 가능한가? | 1-2주 내 완료 가능 |
| Testable | 완료를 객관적으로 검증 가능한가? | 명확한 성공/실패 기준 |

**Part 3: 추가 점검**
- [ ] 사용자 페르소나 구체적 (일반적 "user" 사용 금지)
- [ ] UI/UX 디자인 첨부 또는 참조
- [ ] 비기능 요구사항 (성능, 보안 등) 명시
- [ ] 팀의 Definition of Ready 충족

> 상세 검증 기준 및 예시는 [references/review-framework.md](references/review-framework.md) 참조

### 검증 결과 출력

```
# 유저스토리 검증 결과

## 스토리: [스토리 제목]

### Part 1: 3 C's
- Card: ✅/❌ — [피드백]
- Conversation: ✅/❌ — [피드백]
- Confirmation: ✅/❌ — [피드백]

### Part 2: INVEST
- I: ✅/❌  N: ✅/❌  V: ✅/❌
- E: ✅/❌  S: ✅/❌  T: ✅/❌
[각 항목 피드백]

### Part 3: 추가 점검
[체크리스트 결과]

## 최종 판정
- [ ] ✅ PASS — 개발 준비 완료
- [ ] ⚠️ PASS (소규모 수정) — 스프린트 진입 전 수정
- [ ] ❌ FAIL — 대폭 수정 필요

## 우선 수정 항목
1. [구체적 액션 1]
2. [구체적 액션 2]
```

---

## 연계 워크플로우

- **이전 단계**: `prd-documentation` 스킬에서 기능 요구사항 수신
- **다음 단계**: 승인된 스토리를 `google-docs-writer` 스킬로 내보내기
