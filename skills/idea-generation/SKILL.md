---
name: idea-generation
description: Facilitates product idea brainstorming and validation using JTBD framework, competitive analysis, and value proposition development. Provides both GENERATION (creating new ideas) and VALIDATION (reviewing existing ideas with 10-question assessment). Use when generating product ideas, validating concepts, analyzing market opportunities, identifying user needs, exploring product innovation opportunities, or reviewing idea proposals.
---

# 제품 아이디어 발굴 및 검증

## 작동 모드

요청 내용에 따라 두 가지 모드 중 하나를 실행한다:

- **GENERATION 모드**: 아이디어 발굴 및 체계적 탐색
- **VALIDATION 모드**: 기존 아이디어 검증 및 Go/No-Go 결정

---

## GENERATION 모드: 아이디어 발굴

### 1단계 — 컨텍스트 파악

다음 정보를 수집한다:
- **대상 사용자/시장**: 누구를 위해 만드는가?
- **문제 영역**: 어떤 불편함 또는 기회를 탐색하는가?
- **사업 목표**: 전략적 방향은?
- **제약 조건**: 예산, 일정, 기술, 규제

### 2단계 — JTBD 분석

**Job Statement 형식:**
```
When [상황], I want to [동기], so I can [기대 결과]
```

탐색 질문:
- 사용자가 완수하려는 Job은 무엇인가?
- Functional / Emotional / Social 차원은?
- 현재 대안 또는 우회책은?
- 성공했을 때의 모습은?

### 3단계 — 경쟁사 분석

| 경쟁사 | 강점 | 약점 | 우리의 기회 |
|--------|------|------|------------|
| [이름] | ... | ... | ... |

화이트 스페이스 기회 목록 도출.

### 4단계 — 가치 제안 개발

```
For [타겟 고객]
Who [니즈 또는 기회]
Our [제품/서비스명]
Is a [카테고리]
That [핵심 혜택]
Unlike [주요 경쟁 대안]
We [차별화 요소]
```

### 5단계 — DVF 검증

| 차원 | 평가 | 점수 (1-5) |
|------|------|-----------|
| Desirability | 실제 문제를 해결하는가? | |
| Viability | 비즈니스 모델이 있는가? | |
| Feasibility | 기술적으로 구현 가능한가? | |

### 6단계 — RICE 우선순위화

**공식:** `(Reach × Impact × Confidence) / Effort`

- **Reach**: 분기당 영향받는 사용자 수
- **Impact**: 0.25(최소) / 0.5(낮음) / 1(보통) / 2(높음) / 3(매우 높음)
- **Confidence**: 50%(낮음) / 80%(보통) / 100%(높음)
- **Effort**: 인원-개월

---

## VALIDATION 모드: 아이디어 검증

### 검증 프로세스

1. Google Drive에서 Product Idea Assessment Guide 로드:
   - **ID**: `11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU`
   - `mcp__google-drive__getGoogleDocContent` 사용

2. 10가지 핵심 질문으로 기회 평가:
   1. 가치 제안: 어떤 문제를 정확히 해결하는가?
   2. 타겟 시장: 누구의 문제를 해결하는가?
   3. 시장 규모: 기회의 크기는?
   4. 경쟁 환경: 어떤 대안이 존재하는가?
   5. 차별화 요소: 우리가 최적인 이유는?
   6. 시장 타이밍: 왜 지금인가?
   7. GTM 전략: 어떻게 시장에 진입하는가?
   8. 수익/지표: 어떻게 성공을 측정하고 수익을 창출하는가?
   9. 핵심 성공 요인: 필수 조건은?
   10. 최종 권고: Go 또는 No-Go?

### 검증 출력 형식

```
## 아이디어 검증 결과

### 10가지 질문 평가
[각 질문별 답변과 평가]

### DVF 점수
- Desirability: [X/5] — [근거]
- Viability: [X/5] — [근거]
- Feasibility: [X/5] — [근거]

### RICE 점수
- Reach: [수치]
- Impact: [점수]
- Confidence: [%]
- Effort: [인원-개월]
- **RICE Score: [계산값]**

### 종합 평가
[2-3문장 요약]

### 권고사항
- [ ] ✅ **GO** — PRD 단계로 진행
- [ ] ❌ **NO-GO** — 재검토 또는 폐기
- [ ] 🔄 **PIVOT** — 방향 수정 후 재검증

### 다음 단계
[구체적 액션 아이템]
```

---

## 다음 워크플로우

- **아이디어 검증 완료 → PRD 작성**: `prd-documentation` 스킬 활용
- **문서 저장 필요**: `google-docs-writer` 스킬로 Google Docs 내보내기
- **프레임워크 설명 필요**: `pm-knowledge-base` 스킬 참조
