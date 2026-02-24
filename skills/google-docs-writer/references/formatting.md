# Google Docs 포맷팅 가이드

## 텍스트 포맷팅

### 헤딩 계층 구조
- **H1 (문서 제목):** 문서당 하나만 사용
- **H2 (주요 섹션):** 문제, 목표, 요구사항 등 대분류
- **H3 (서브섹션):** 섹션 내 소분류 또는 스토리 제목
- **H4 (세부 항목):** 수락 기준, 세부 포인트 (드물게 사용)

### 폰트 및 크기
| 요소 | 크기 | 스타일 |
|------|------|--------|
| 제목 (H1) | 24pt | Bold |
| 섹션 (H2) | 18pt | Bold |
| 서브섹션 (H3) | 14pt | Bold |
| 본문 | 11pt | Regular |
| 캡션/메모 | 9pt | Italic 또는 회색 |

### 색상 체계
- **헤딩:** 진한 파란색 (#1a237e) 또는 진한 회색 (#424242)
- **본문:** 검정 (#000000)
- **메모/메타데이터:** 회색 (#757575)
- **승인/성공:** 초록 (#2e7d32)
- **위험/반려:** 빨강 (#c62828)
- **하이라이트:** 노란 배경 (#fff59d)

### 강조 표시
- **Bold:** 핵심 용어, 문제 설명, 결정 사항
- **Italic:** 유저스토리 형식, 인용, 강조
- **Underline:** 사용 지양 (대신 Bold 또는 색상 활용)

---

## 단락 포맷팅

### 줄 간격
- **헤딩:** 1.0 줄 간격
- **본문 단락:** 1.5 줄 간격
- **목록:** 1.15 줄 간격
- **표 내부:** 단일 간격

### 요소 간 여백
- **H2 이전:** 18pt 여백
- **H2 이후:** 6pt 여백
- **H3 이전:** 12pt 여백
- **H3 이후:** 6pt 여백
- **단락 사이:** 6pt 여백
- **표 앞뒤:** 12pt 여백

### 들여쓰기
- **본문 단락:** 들여쓰기 없음 (블록 스타일)
- **목록:** 0.5인치 좌측 들여쓰기
- **중첩 목록:** 레벨당 0.5인치 추가
- **인용:** 1인치 좌측 들여쓰기

### 정렬
- **헤딩:** 좌측 정렬
- **본문:** 좌측 정렬 (공식 문서는 양쪽 정렬)
- **표:** 텍스트 좌측, 숫자 우측 정렬
- **제목 페이지:** 가운데 정렬

---

## 표 포맷팅

### 표준 표 스타일
**헤더 행:**
- 배경: 연회색 (#f5f5f5)
- 텍스트: Bold, 진한 회색 (#424242)
- 테두리: 전체 테두리, 1pt

**데이터 행:**
- 배경: 흰색
- 텍스트: Regular, 검정
- 테두리: 연회색 (#e0e0e0), 0.5pt

### 주요 표 유형

**목표/지표 표:**
| 목표 | 지표 | 목표값 | 일정 |
|------|------|--------|------|

**요구사항 표:**
| ID | 요구사항 | 우선순위 | 상태 |
|----|----------|----------|------|

**위험 요소 표:**
| 위험 | 영향 | 확률 | 완화 방안 |
|------|------|------|-----------|

**경쟁사 분석 표:**
| 경쟁사 | 솔루션 | 강점 | 약점 |
|--------|--------|------|------|

---

## MCP 도구 사용 방법

### 문서 생성 및 업데이트
```
mcp__google-drive__createGoogleDoc
  - name: 문서 제목
  - content: 문서 내용 (텍스트)
  - parentFolderId: 폴더 ID (선택)

mcp__google-drive__updateGoogleDoc
  - documentId: 대상 문서 ID
  - content: 새 콘텐츠 (기존 내용 교체)

mcp__google-drive__getGoogleDocContent
  - documentId: 대상 문서 ID
  → 텍스트 인덱스 포함 문서 내용 반환
```

### 포맷팅 적용
```
mcp__google-drive__formatGoogleDocText
  - documentId, startIndex, endIndex
  - bold, italic, fontSize, foregroundColor

mcp__google-drive__formatGoogleDocParagraph
  - documentId, startIndex, endIndex
  - alignment, lineSpacing, spaceAbove, spaceBelow
  - namedStyleType: HEADING_1 ~ HEADING_6, NORMAL_TEXT
```

### 파일 관리
```
mcp__google-drive__createFolder
  - name: 폴더명
  - parent: 상위 폴더 ID (선택)

mcp__google-drive__moveItem
  - itemId: 파일/폴더 ID
  - destinationFolderId: 대상 폴더 ID

mcp__google-drive__search
  - query: 검색어

mcp__google-drive__listFolder
  - folderId: 폴더 ID
```
