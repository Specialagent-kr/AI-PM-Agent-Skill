Claude에서 프로젝트 구상을 위한 첫 프롬프트 예시입니다.

#Goal
- Claude Code로 Product Manager를 위한 "AI PM Peer" Agent를 만들거야

#Context 
##Sub-Agent와  Skill을 아래와 같이 구성하고, 채팅 인터페이스로 구현할 할거야. 
- Sub Agent: Idea Agent, PRD Agent, UserStory Agent
- Skills: Idea Generation, PRD Documentation, UserStory Documentation, google-docs-writer, presentation-generator, pm-knowledge-base
##Claude Code에서 제공하는 Skill Creator(https://github.com/anthropics/skills/tree/main/skills/skill-creator)를 참고해서 표준에 따라 Skill들을 만들거야 
##Agent와 Skill이 참고할 리소스는 Google Drive를 연동해서 참고할거야
##채팅 인터페이스를 통해 "AI PM Peer" 에이전트와 소통할거야

#Task
1. 위 작업을 위해 VS Code for Claude Code 환경에서 어떻게 프로젝트를 시작해야하는지 상세하게 가이드를 제공해(VS Code 및 Claude Code Extension은 설치된 상태야)
2. 위 구성안을 바탕으로 Claude Code에서 프로젝트 시작을 위한 지침을 제안해줘
