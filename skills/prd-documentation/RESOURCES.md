# PRD Documentation Skill - Google Drive Resources

## Overview

This document maps the Google Drive resources used by the `prd-documentation` skill for both documentation and review purposes.

---

## Resource List

### 1. PRD Review Guide

**Document Information:**
- **Name:** PRD Review Guide (PRD 검토 가이드라인 및 템플릿)
- **Google Drive ID:** `1abFQ6IDCEyB1GP0WTSkwKQHeB_iQL5wlZkSEnxdvhYU`
- **Type:** Validation Framework
- **Format:** Google Docs
- **Access Method:** `mcp__google-drive__getGoogleDocContent`

**Usage in Skill:**
- **Mode:** Review Mode
- **When:** User requests PRD review or validation
- **How:** Load document to reference 6 evaluation criteria and scoring guidelines

**Content Summary:**
```
Title: PRD 검토 가이드라인 및 템플릿

Key Sections:
1. 목적 (Purpose)
   - Structured PRD review approach
   - Ensuring comprehensiveness and clarity

2. 검토 체크리스트 (Review Checklist)
   I. 전반적인 명확성 및 목적
   II. 문제 정의 및 근거
   III. 목표 및 Impact 크기
   IV. 솔루션 및 우선순위
   V. 성공 지표 및 측정 계획
   VI. 한계점과 잠재 위험

3. 피드백 제공 포맷 (Feedback Format)
   - Score (100점 만점)
   - 검토 결과 요약 (잘한 점, 보완할 점)
   - 구체적인 개선 사항 (Actionable Feedback)

4. 종합 코멘트 및 인사 (Summary & Closing)

Length: ~2,170 characters
```

**Integration Example:**
```python
# When review mode is triggered
def review_prd(prd_content):
    # Load review guide from Google Drive
    guide_content = mcp.google_drive.getGoogleDocContent(
        documentId="1abFQ6IDCEyB1GP0WTSkwKQHeB_iQL5wlZkSEnxdvhYU"
    )

    # Extract 6 criteria and scoring guidelines
    criteria = extract_review_criteria(guide_content)

    # Evaluate PRD against each criterion
    evaluation = evaluate_prd(prd_content, criteria)

    # Generate feedback using guide format
    feedback = generate_feedback(evaluation, guide_content)

    return feedback
```

---

### 2. PRD Template

**Document Information:**
- **Name:** PRD Template
- **Google Drive ID:** `16YxSymNoB5M5YKkPLzB_sQorl7wIuTzH4VqKQU-99UI`
- **Type:** Documentation Template
- **Format:** Google Docs
- **Access Method:** `mcp__google-drive__getGoogleDocContent`

**Usage in Skill:**
- **Mode:** Documentation Mode
- **When:** User requests PRD creation or needs template reference
- **How:** Load document to show standard structure and examples

**Content Summary:**
```
Title: PRD Template

Key Sections:
1. Template structure overview
2. Section-by-section guidelines
3. Best practices for each section
4. Example content
5. Common patterns and formats

Length: ~[to be measured]
```

**Integration Example:**
```python
# When documentation mode is triggered
def create_prd(requirements):
    # Load PRD template from Google Drive (optional)
    template_content = mcp.google_drive.getGoogleDocContent(
        documentId="16YxSymNoB5M5YKkPLzB_sQorl7wIuTzH4VqKQU-99UI"
    )

    # Use template structure as guide
    prd_structure = extract_template_structure(template_content)

    # Generate PRD following template
    prd = generate_prd(requirements, prd_structure)

    return prd
```

---

## Evaluation Framework

### 6 Review Criteria (from Google Drive Resource)

#### I. 전반적인 명확성 및 목적 (Overall Clarity & Purpose)

**Evaluation Points:**
- Is the PRD understandable to all stakeholders?
- Is the language clear and unambiguous?
- Is the "Why" (purpose) clearly explained?
- Is the core problem/opportunity stated?

**Scoring Guidance:**
- 90-100: Crystal clear, all stakeholders can understand
- 70-89: Mostly clear, minor clarifications needed
- 50-69: Some ambiguity, requires significant clarification
- <50: Unclear, needs major revision

---

#### II. 문제 정의 및 근거 (Problem Definition & Rationale)

**Evaluation Points:**
- Is the user/business problem well-defined, specific, compelling?
- What evidence supports the problem?
  - User research
  - Data analysis
  - Market trends
  - Customer feedback
- Are target user segments clearly identified?
- Are pain points addressed?

**Scoring Guidance:**
- 90-100: Well-defined problem with strong evidence
- 70-89: Clear problem, adequate evidence
- 50-69: Vague problem or weak evidence
- <50: Problem unclear, no evidence

---

#### III. 목표 및 Impact 크기 (Goals & Impact)

**Evaluation Points:**
- Do goals follow SMART principles?
  - Specific
  - Measurable
  - Achievable
  - Relevant
  - Time-bound
- What is the expected impact on metrics?
- Is the impact large enough to justify effort?

**Scoring Guidance:**
- 90-100: SMART goals with significant impact
- 70-89: Goals mostly SMART, impact quantified
- 50-69: Goals lack SMART elements or unclear impact
- <50: No clear goals

---

#### IV. 솔루션 및 우선순위 (Solution & Prioritization)

**Evaluation Points:**
- Are user stories written from user perspective?
- Do they cover primary and edge cases?
- Are functional requirements clear and detailed enough?
- Are non-functional requirements addressed?
- Is scope clearly defined (in/out)?
- Are requirements prioritized with rationale?

**Scoring Guidance:**
- 90-100: Comprehensive requirements, clear priorities
- 70-89: Good coverage, minor gaps
- 50-69: Incomplete or unclear priorities
- <50: Major gaps

---

#### V. 성공 지표 및 측정 계획 (Success Metrics & Measurement)

**Evaluation Points:**
- What specific metrics measure success?
- How will they be tracked?
- Are analytics/logging requirements defined?
- Is there a baseline or benchmark?

**Scoring Guidance:**
- 90-100: Clear metrics with measurement plan
- 70-89: Metrics defined, some details
- 50-69: Vague metrics or no plan
- <50: No clear metrics

---

#### VI. 한계점과 잠재 위험 (Limitations & Risks)

**Evaluation Points:**
- Are known unknowns listed?
- Are owners assigned to open questions?
- Have risks been identified?
- Are mitigation strategies considered?

**Scoring Guidance:**
- 90-100: Risks identified with mitigation
- 70-89: Risks identified, some mitigation
- 50-69: Incomplete risk assessment
- <50: No risk identification

---

## Feedback Format (from Google Drive Resource)

### 1. 검토 결과 (Review Results)

For each of the 6 criteria:

**Format:**
```
### [Criterion Name]

**Score:** [X/100]

**검토 결과 요약:**
- 잘한 점: [Strengths]
- 보완할 점: [Areas for improvement]

**구체적인 개선 사항 (Actionable Feedback):**
- [Specific action 1]: [Why it matters]
- [Specific action 2]: [Why it matters]
```

---

### 2. 종합 코멘트 (Overall Summary)

**Format:**
```
## 종합 코멘트

**전체 평가:**
[2-3 paragraphs synthesizing the review]

**주요 액션 아이템:**
1. [Action item 1]
2. [Action item 2]
3. [Action item 3]
```

---

### 3. 인사 (Closing)

**Format:**
```
감사 인사를 하고 보완된 피드백 제출을 요청합니다.

Thank you for the opportunity to review this PRD.
Please address the feedback above and resubmit for
a follow-up review if needed.
```

---

## Feedback Tone & Style (from Google Drive Resource)

### Guidelines

**구체적으로 (Be Specific):**
- Reference specific sections or points in PRD
- Quote exact text when possible

**건설적으로 (Be Constructive):**
- Focus on content and ideas, not personal criticism
- Frame as suggestions or questions

**추론 설명 (Explain Reasoning):**
- Briefly explain why suggesting something
- Provide context or perspective

**피드백 우선순위화 (Prioritize Feedback):**
- Highlight most important points
- Distinguish must-fix from nice-to-have

**액션아이템 제시 (Provide Action Items):**
- Suggest alternatives or solutions
- Make feedback actionable

**질문과 요구사항 구분 (Distinguish Questions from Requirements):**
- Clarify what needs clarification vs. must change

---

## Usage Guidelines

### When to Reference Google Drive Resources

**PRD Review Guide:**
- User says "review this PRD"
- User asks "validate PRD quality"
- User requests "PRD feedback"
- User provides PRD for evaluation

**PRD Template:**
- User says "create a PRD"
- User asks "what should a PRD include"
- User needs "PRD structure guidance"
- User is starting new PRD

### Review Process

1. Load PRD Review Guide from Google Drive
2. Extract 6 criteria and scoring guidelines
3. Evaluate PRD against each criterion
4. Score each (0-100)
5. Generate feedback following guide format
6. Calculate overall score (average)
7. Provide approval recommendation

---

## Updates and Maintenance

### Resource Version Tracking

| Resource | Version | Date | Document ID |
|----------|---------|------|-------------|
| PRD Review Guide | 1.0 | 2025-12-30 | 1abFQ6IDCEyB1GP0WTSkwKQHeB_iQL5wlZkSEnxdvhYU |
| PRD Template | 1.0 | 2025-12-30 | 16YxSymNoB5M5YKkPLzB_sQorl7wIuTzH4VqKQU-99UI |

### Fallback Strategy

If Google Drive resources are unavailable:
- Use hardcoded 6 criteria (documented in SKILL.md)
- Use built-in template structure
- Note to user that guide couldn't be loaded
- Proceed with standard evaluation framework

---

## Related Resources

**Skills Using These Resources:**
- `prd-documentation` (this skill)

**Related Agent:**
- PRD Agent (`.claude/agents/prd-agent.md`)

**Related Documentation:**
- `AGENT_ARCHITECTURE.md` - Full architecture overview
- `SKILL.md` - Complete skill implementation

---

## Access Log Template

```
Date: [YYYY-MM-DD]
Resource: [PRD Review Guide / PRD Template]
Action: [Loaded/Updated/Failed]
Document ID: [ID]
Result: [Success/Failure]
Notes: [Observations]
```
