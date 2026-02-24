---
name: pm-knowledge-base
description: Provides access to Product Management frameworks, methodologies, and best practices. Includes RICE prioritization, Kano model, OKR framework, user persona templates, North Star metrics, and PM workflows. Use when asking about PM methodologies, frameworks, prioritization techniques, goal-setting, user research, or product strategy guidance.
---

# PM 지식 베이스

PM 프레임워크, 방법론, 베스트 프랙티스를 즉시 참조할 수 있는 지식 베이스다.

---

## 프레임워크 선택 가이드

| 상황 | 추천 프레임워크 |
|------|----------------|
| 기능/아이디어 우선순위화 | RICE, Kano, Value vs. Effort |
| 팀/조직 목표 설정 | OKRs, North Star Metric |
| 사용자 이해 | User Personas, JTBD |
| 제품 시장 적합성 검증 | Product-Market Fit |
| 로드맵 계획 | Kano + RICE 결합 |

---

## 지식 영역

### 1. 우선순위화 프레임워크
- **RICE** — [references/rice.md](references/rice.md): Reach×Impact×Confidence/Effort 공식, 계산 예시, 활용 시점
- **Kano** — [references/kano.md](references/kano.md): 기본/성과/감동 니즈 분류, 고객 조사 방법
- **MoSCoW**: Must / Should / Could / Won't 분류 (빠른 범위 결정)
- **Value vs. Effort**: 2×2 매트릭스 (단순 의사결정)

### 2. 목표 설정 프레임워크
- **OKRs** — [references/okr.md](references/okr.md): Objective + Key Results, 작성 가이드, 예시
- **North Star** — [references/north-star.md](references/north-star.md): 핵심 가치 지표 정의, 선택 방법
- **SMART 목표**: Specific / Measurable / Achievable / Relevant / Time-bound

### 3. 사용자 리서치 방법
- **User Personas** — [references/personas.md](references/personas.md): 페르소나 템플릿, 생성 5단계
- **JTBD** — [references/jtbd.md](references/jtbd.md): Job Statement 형식, Functional/Emotional/Social Jobs
- **사용자 여정 지도**: 단계별 불편 지점 시각화
- **공감 지도**: 사용자의 생각/감정/행동/발언 매핑

### 4. 제품 전략
- **Product-Market Fit** — [references/pmf.md](references/pmf.md): PMF 징후, 측정 방법 (Sean Ellis Test, NPS)
- **경쟁사 분석**: 강점/약점 분석 및 차별화 기회 발굴
- **Go-to-Market**: 타겟, 메시지, 채널, 출시 전략

### 5. 개발 워크플로우
- **Agile/Scrum**: 스프린트 계획, 백로그 관리, 레트로스펙티브
- **스토리 매핑**: 사용자 여정 기반 백로그 시각화
- **로드맵 커뮤니케이션**: 테마 기반 로드맵, 신뢰도 수준 표시

---

## 주요 지표 사전

| 지표 | 계산식 | 용도 |
|------|--------|------|
| DAU/MAU | 일간 / 월간 활성 사용자 | 참여도 |
| CAC | 총 마케팅비 / 신규 고객 | 획득 효율성 |
| LTV | ARPU × 평균 고객 생애 | 고객 가치 |
| LTV:CAC | 고객 가치 / 획득 비용 | 비즈니스 건전성 (3:1 이상) |
| NPS | 추천자% - 비추천자% | 제품 만족도 |
| Churn Rate | 이탈 사용자 / 시작 사용자 × 100% | 유지율 |
| MRR | 월 구독 수익 | SaaS 건전성 |

---

## PM 워크플로우 요약

**PRD 작성:** 문제 발굴 → 목표 정의 → 솔루션 탐색 → PRD 작성 → 검토/승인 → 유저스토리 분해

**스프린트 계획:** 백로그 정제 → 스프린트 목표 → 스토리 선택 → 용량 확인 → 의존성 파악

**기능 출시:** 사전 준비(GTM, CS 교육) → 배포 → 지표 모니터링 → 피드백 수집 → 반복 개선

---

## 흔한 PM 시나리오

**이해관계자 요청 충돌:** 목표 정렬 → RICE로 우선순위화 → 용량 배분 (기능 60% / 기술 부채 20% / 버그 20%) → 투명한 트레이드오프 소통

**CEO 기능 요청:** 컨텍스트 이해 → 광범위한 니즈인지 확인 → RICE로 임팩트 평가 → 로드맵 비교 후 반영 여부 결정 → 근거 공유

**기능 채택률 저조:** 발견 가능성 문제? UX 마찰? 가치 부재? → 분석 → 온보딩 개선, UI 단순화, 인앱 안내 실험
