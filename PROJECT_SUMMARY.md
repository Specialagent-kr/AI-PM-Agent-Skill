# AI PM Peer Agent — 프로젝트 요약

---

## 프로젝트 개요

Product Manager를 위한 AI 기반 동료 에이전트 시스템.
아이디어 생성부터 Google Docs 산출물 출력까지 전체 PM 워크플로우를 지원합니다.

**핵심 특징:**
- 6개 전문 스킬 (생성 + 검증 통합)
- 3개 Sub-Agent 아키텍처 (Idea · PRD · UserStory)
- Google Drive MCP 실시간 연동 (읽기·쓰기)
- 로컬 채팅 인터페이스 + Flask 백엔드

---

## 구현 완료 항목

### ✅ Phase 1: 기반 구축
- 프로젝트 구조 설계
- Google Drive MCP 서버 설정 및 OAuth 인증 완료
- idea-generation 스킬 초기 구현

### ✅ Phase 2: 스킬 개발 및 Sub-Agent 아키텍처
- 6개 스킬 전체 구현:
  - `idea-generation` (JTBD + DVF 검증)
  - `prd-documentation` (11섹션 + 6기준 검토)
  - `userstory-documentation` (INVEST + 3C's 검증)
  - `google-docs-writer` (Google Docs 내보내기)
  - `presentation-generator` (Google Slides 발표자료)
  - `pm-knowledge-base` (7개 프레임워크, references/ 구조)
- 3개 Sub-Agent 파일 작성 (idea-agent, prd-agent, userstory-agent)
- Google Drive 검증 리소스 5개 매핑

### ✅ Phase 3: 인프라 구축
- Google Drive MCP 연결 완료 (node 직접 실행, 글로벌 설치)
  - 바이너리: `C:\Users\jinso\AppData\Roaming\npm\node_modules\@piotr-agier\google-drive-mcp\dist\index.js`
  - OAuth 토큰: `C:\Users\jinso\.config\google-drive-mcp\tokens.json`
  - 인증 계정: master@proagent.kr
- 로컬 채팅 인터페이스 (`chat-interface.html`) 구현
- Flask 백엔드 서버 (`server.py`, port 5000) 구현
- `settings.local.json` MCP 활성화 설정 완료

---

## Sub-Agent 아키텍처

```
AI PM Agent
├── Idea Agent          → idea-generation 스킬
│   ├── 생성: JTBD → 경쟁사 분석 → 가치 제안 → RICE
│   └── 검증: 10가지 질문 → DVF → Go/No-Go
│
├── PRD Agent           → prd-documentation 스킬
│   ├── 작성: 11개 섹션 PRD 구조
│   └── 검토: 6가지 기준 (0-100점) → Approved/Revise/Reject
│
└── UserStory Agent     → userstory-documentation 스킬
    ├── 작성: 표준 포맷 + Given-When-Then AC
    └── 검증: 3C's + INVEST → Pass/Fail
```

---

## 전체 워크플로우

```
1. Idea Agent: 아이디어 생성·검증 → Go/No-Go
        ↓ [Go]
2. PRD Agent: PRD 작성·검토 → Approved/Revise/Reject
        ↓ [Approved]
3. UserStory Agent: 유저스토리 작성·검증 → Pass/Fail
        ↓ [Pass]
4. google-docs-writer: Google Docs 최종 출력
   presentation-generator: 발표자료 생성
```

---

## Google Drive 통합

### MCP 서버
- **패키지:** `@piotr-agier/google-drive-mcp` v1.2.0
- **실행:** node 직접 실행 (npx 제거 → 시작 시간 단축)
- **상태:** ✅ 연결 완료, OAuth 토큰 자동 갱신

### AI PM 폴더 리소스 (ID: `YOUR_ID`)

| 문서 | ID | 담당 |
|---|---|---|
| Product Idea Assessment Guide | `YOUR_ID` | Idea Agent |
| PRD Review Guide | `YOUR_ID` | PRD Agent |
| PRD Template | `YOUR_ID` | PRD Agent |
| User Story Review Checklist | `YOUR_ID` | UserStory Agent |
| User Story Template | `YOUR_ID` | UserStory Agent |

---

## 사용 예제

### 예제 1: 아이디어 생성 → PRD → 유저스토리
```
"모바일 앱 사용자 온보딩 개선 아이디어를 생성하고 검증해줘"
→ Idea Agent: JTBD 분석, DVF 검증, RICE 점수 → Go 판정

"이 아이디어로 PRD를 작성해줘"
→ PRD Agent: 11개 섹션 PRD 작성, 6가지 기준 검토 → Approved

"PRD를 기반으로 유저스토리를 만들고 검증해줘"
→ UserStory Agent: 스토리 작성, 3C's+INVEST 검증 → Pass
```

### 예제 2: 문서 출력
```
"작성한 PRD를 Google Docs로 내보내줘"
→ google-docs-writer: /Projects/온보딩 개선/PRD.gdoc 생성

"이해관계자 보고용 발표자료를 만들어줘"
→ presentation-generator: /Projects/온보딩 개선/발표자료.gslides 생성
```

---

## 프로젝트 파일 구조

```
AI PM/
├── .claude/
│   ├── skills/
│   │   ├── idea-generation/       (SKILL.md)
│   │   ├── prd-documentation/     (SKILL.md)
│   │   ├── userstory-documentation/ (SKILL.md)
│   │   ├── google-docs-writer/    (SKILL.md)
│   │   ├── presentation-generator/ (SKILL.md)
│   │   └── pm-knowledge-base/     (SKILL.md + references/)
│   ├── agents/
│   │   ├── idea-agent.md
│   │   ├── prd-agent.md
│   │   └── userstory-agent.md
│   └── settings.local.json
├── .mcp.json                      (MCP 서버 설정)
├── server.py                      (Flask 백엔드)
├── chat-interface.html            (채팅 UI)
├── CLAUDE.md                      (프로젝트 컨텍스트)
├── AGENT_ARCHITECTURE.md          (아키텍처 상세)
├── README.md                      (프로젝트 개요)
└── PROJECT_SUMMARY.md             (이 문서)
```

---

## 주요 성과

1. **통합 작성+검증 시스템**: 단순 문서 생성이 아닌 품질 검증까지 자동화
2. **Google Drive 실시간 연동**: 실제 PM 가이드를 검증 기준으로 활용
3. **6개 전문 스킬**: PM 전체 워크플로우 커버
4. **빠른 MCP 시작**: npx → node 직접 실행으로 지연 시간 제거
5. **채팅 UI**: 브라우저 기반 에이전트 선택 인터페이스

---

## 기술 스택

| 구분 | 기술 |
|---|---|
| AI 에이전트 | Claude Code CLI, Skills (YAML+Markdown) |
| MCP | @piotr-agier/google-drive-mcp v1.2.0 |
| 백엔드 | Flask (Python), REST API |
| 프론트엔드 | HTML/CSS/JS (chat-interface.html) |
| 인증 | Google OAuth 2.0 |
| 런타임 | Node.js v24.11.1 |
| 프레임워크 | JTBD, RICE, DVF, INVEST, 3C's, OKR |
