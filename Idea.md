Claude에서 프로젝트 구상을 위한 첫 프롬프트 예시입니다.

#Goal
- Claude Code로 Product Manager를 위한 "AI PM Peer" Agent를 만들거야

#Context 

##Sub-Agent와  Skill을 아래와 같이 구성하고, 채팅 인터페이스로 구현할 할거야. 
- Sub Agent: Idea Agent, PRD Agent, UserStory Agent
- Skills: Idea Generation, PRD Documentation, UserStory Documentation, google-docs-writer, presentation-generator, pm-knowledge-base

##Claude Code에서 제공하는 Skill Creator(https://github.com/anthropics/skills/tree/main/skills/skill-creator)를 참고해서 표준에 따라 Skill들을 만들거야

##Agent와 Skill이 참고할 리소스는 Google Drive를 연동해서 참고

##채팅 인터페이스를 통해 "AI PM Peer" 에이전트와 소통

#Task
1. 위 작업을 위해 VS Code for Claude Code 환경에서 어떻게 프로젝트를 시작해야하는지 상세하게 가이드를 제공해(VS Code 및 Claude Code Extension은 설치된 상태야)
2. 위 구성안을 바탕으로 Claude Code에서 프로젝트 시작을 위한 지침을 제안해줘

-------

답변 예시입니다.

# AI PM Peer Agent 구축 가이드

## 1. VS Code에서 Claude Code 프로젝트 시작하기

### 1-1. 프로젝트 디렉토리 생성 및 초기화

```bash
# 프로젝트 폴더 생성
mkdir ai-pm-peer
cd ai-pm-peer

# VS Code로 열기
code .
```

### 1-2. Claude Code 활성화

VS Code에서:
1. **Command Palette** 열기 (`Cmd+Shift+P` on Mac, `Ctrl+Shift+P` on Windows)
2. "Claude Code: Start Session" 입력 후 선택
3. 또는 터미널에서 `claude` 명령어로 시작

### 1-3. 프로젝트 구조 설정

프로젝트를 다음과 같은 구조로 구성하는 것을 추천합니다:

```
ai-pm-peer/
├── .claude/
│   └── config.json          # Claude Code 설정
├── skills/
│   ├── idea-generation/
│   │   └── SKILL.md
│   ├── prd-documentation/
│   │   └── SKILL.md
│   ├── userstory-documentation/
│   │   └── SKILL.md
│   └── google-docs-writer/
│       └── SKILL.md
├── agents/
│   ├── idea-agent.md
│   ├── prd-agent.md
│   └── userstory-agent.md
├── templates/
│   ├── prd-template.md
│   └── userstory-template.md
├── docs/
│   └── agent-guide.md
└── README.md
```

### 1-4. Google Drive 연동 준비

Claude Code에서 Google Drive를 사용하려면:
1. Claude.ai 웹/앱에서 Google Drive 연동 완료
2. Claude Code는 동일한 계정의 연동 정보를 자동으로 사용

## 2. 구성안 검토 및 개선 제안

### 현재 구성안 분석

**강점:**
- Sub-Agent 분리가 명확함 (Idea, PRD, UserStory)
- Google Drive 연동으로 협업 가능
- Skill 기반 접근으로 확장 가능

**개선 제안:**

1. **Orchestrator Agent 추가**
   - 3개 Sub-Agent를 조율하는 메인 에이전트 필요
   - 사용자 요청을 적절한 Sub-Agent로 라우팅

2. **Skill 구성 재조정**
   ```
   - idea-generation (Idea Agent 전용)
   - prd-documentation (PRD Agent 전용)
   - userstory-documentation (UserStory Agent 전용)
   - google-docs-writer (공통 Skill)
   - pm-knowledge-base (공통 Skill - PM 베스트 프랙티스)
   ```

3. **워크플로우 연결**
   - Idea → PRD → UserStory의 순차적 흐름 지원
   - 각 단계의 아웃풋이 다음 단계의 인풋이 되도록

## 3. Claude Code에 줄 초기 지침

Claude Code를 시작할 때 아래 지침을 복사하여 붙여넣으세요:

---

```markdown
# AI PM Peer Agent 개발 프로젝트

## 프로젝트 목표
Product Manager를 위한 AI 기반 동료 에이전트 시스템을 구축합니다.

## 시스템 아키텍처

### 1. Agent 구조
- **Main Orchestrator**: 사용자 요청을 분석하고 적절한 Sub-Agent로 라우팅
- **Idea Agent**: 제품 아이디어 생성 및 검증 지원
- **PRD Agent**: Product Requirements Document 작성 지원
- **UserStory Agent**: User Story 및 Acceptance Criteria 작성 지원

### 2. Skills (우선순위 순서)
1. **idea-generation**: 
   - 목적: 사용자 니즈 기반 아이디어 브레인스토밍
   - 기능: JTBD, 경쟁사 분석, 가치 제안 도출
   
2. **prd-documentation**:
   - 목적: 구조화된 PRD 문서 작성
   - 템플릿: 문제 정의, 솔루션, 성공 지표, 요구사항
   
3. **userstory-documentation**:
   - 목적: User Story 및 AC 작성
   - 형식: "As a [user], I want [goal], so that [benefit]"
   
4. **google-docs-writer**:
   - 목적: 생성된 문서를 Google Docs로 작성
   - 기능: 포맷팅, 협업자 공유

5. **pm-knowledge-base**:
   - 목적: PM 베스트 프랙티스 및 프레임워크 제공
   - 내용: RICE, Kano 모델, User Persona 등

### 3. 개발 단계별 작업

**Phase 1: 기본 구조 설정**
1. 프로젝트 폴더 구조 생성
2. README.md 작성
3. Skill Creator 참고하여 첫 번째 Skill 생성 (idea-generation부터 시작)

**Phase 2: Skills 개발**
1. 각 Skill의 SKILL.md 파일 작성
2. 실제 PM 워크플로우에 맞춰 템플릿 및 프롬프트 설계
3. Google Drive 연동 테스트

**Phase 3: Agent 구현**
1. Main Orchestrator 로직 구현
2. 각 Sub-Agent의 역할 및 프롬프트 정의
3. Agent 간 데이터 전달 메커니즘 구현

**Phase 4: 통합 및 테스트**
1. 채팅 인터페이스 구현
2. End-to-end 워크플로우 테스트 (Idea → PRD → UserStory)
3. Google Docs 출력 검증

## 즉시 시작할 작업

1. **먼저 Skill Creator Skill을 확인해주세요**:
   - `/mnt/skills/examples/skill-creator/SKILL.md` 파일을 읽고 Skill 작성 가이드라인 파악

2. **프로젝트 구조를 생성해주세요**:
   - 위에 제시된 폴더 구조 생성
   - README.md 초안 작성

3. **첫 번째 Skill (idea-generation) 개발을 시작해주세요**:
   - SKILL.md 파일 생성
   - PM의 아이디어 발상 프로세스를 반영한 구조 설계

4. **Google Drive 연동 확인**:
   - Google Drive에서 참고 문서 검색 기능 테스트
   - 문서 작성 기능 테스트

## 제약사항 및 고려사항
- Claude Code 환경에서 작동해야 함
- Google Drive Skill은 기존 Notion MCP 방식과 유사하게 구현
- 각 Skill은 독립적으로 실행 가능하면서도 연계 가능해야 함
- 채팅 인터페이스는 자연어 기반으로 직관적이어야 함

질문이나 명확히 할 부분이 있다면 물어봐주세요!
```

---

## 4. 다음 단계 실행 팁

### Claude Code와 대화 시작 예시:

```
"위 지침을 읽고 프로젝트를 시작해줘. 
먼저 Skill Creator를 확인하고, 
프로젝트 구조를 생성한 다음, 
idea-generation Skill부터 개발을 시작해줘."
```

### 개발 진행 중 유용한 명령:

1. **Skill 개발 시**: "skill-creator의 베스트 프랙티스를 참고해서 [스킬명] SKILL.md를 작성해줘"

2. **Google Drive 테스트**: "Google Drive에서 'PM 템플릿' 관련 문서를 검색해줘"

3. **통합 테스트**: "Idea Agent에게 '배달 음식 추천 서비스' 아이디어를 요청하는 시나리오를 실행해줘"

---

이 가이드대로 진행하면 체계적으로 AI PM Peer Agent를 구축할 수 있습니다. Claude Code는 파일 생성, 코드 작성, Google Drive 연동 등을 모두 처리할 수 있으므로, 명확한 지침을 주면 효율적으로 개발이 진행될 것입니다!
