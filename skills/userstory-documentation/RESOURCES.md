# UserStory Documentation Skill - Google Drive Resources

## Overview

This document maps the Google Drive resources used by the `userstory-documentation` skill for both documentation and review purposes.

---

## Resource List

### 1. User Story Review Checklist

**Document Information:**
- **Name:** User Story Review Checklist (사용자 스토리 검토 체크리스트)
- **Google Drive ID:** `1xZvwxbvgpDmLC9r0Ni58DNh0hAvDhwAi9hzVxvAG7cs`
- **Type:** Validation Framework
- **Format:** Google Docs
- **Access Method:** `mcp__google-drive__getGoogleDocContent`

**Usage in Skill:**
- **Mode:** Review Mode
- **When:** User requests user story review or validation
- **How:** Load document to reference 3 C's, INVEST principles, and comprehensive checklist

**Content Summary:**
```
Title: 사용자 스토리 검토 체크리스트

Key Sections:
1. 목적 (Purpose)
   - Ensure user stories meet quality standards
   - Verify stories are ready for development

2. 검토 프레임워크 (Review Framework)
   I. The 3 C's (Fundamental Elements)
      - Card: Is the story well-written?
      - Conversation: Has there been sufficient discussion?
      - Confirmation: Are acceptance criteria clear?

   II. INVEST Principles (Quality Criteria)
      - Independent
      - Negotiable
      - Valuable
      - Estimable
      - Small
      - Testable

   III. Additional Considerations
      - User persona specificity
      - UI/UX design references
      - Non-functional requirements
      - Definition of Ready compliance

3. 평가 방법 (Evaluation Method)
   - Pass/Fail for each criterion
   - Overall Ready/Not Ready determination
   - Specific action items for improvement

4. 피드백 제공 포맷 (Feedback Format)
   - Part 1: 3 C's assessment
   - Part 2: INVEST assessment
   - Part 3: Additional checks
   - Overall status
   - Action items
   - Ready for development decision

Length: ~2,450 characters
```

**Integration Example:**
```python
# When review mode is triggered
def review_user_story(story_content):
    # Load review checklist from Google Drive
    checklist_content = mcp.google_drive.getGoogleDocContent(
        documentId="1xZvwxbvgpDmLC9r0Ni58DNh0hAvDhwAi9hzVxvAG7cs"
    )

    # Extract 3 C's and INVEST criteria
    criteria = extract_review_criteria(checklist_content)

    # Evaluate user story against each criterion
    three_cs = evaluate_3cs(story_content, criteria)
    invest = evaluate_invest(story_content, criteria)
    additional = evaluate_additional(story_content, criteria)

    # Determine Pass/Fail status
    status = determine_ready_status(three_cs, invest, additional)

    # Generate feedback using checklist format
    feedback = generate_feedback(three_cs, invest, additional, status)

    return feedback
```

---

### 2. User Story Template

**Document Information:**
- **Name:** User Story Template (사용자 스토리 템플릿)
- **Google Drive ID:** `19Ko83lFCidiuZgC5OhiXpvsFVxsOBhhvzF5QcELkHzg`
- **Type:** Documentation Template
- **Format:** Google Docs
- **Access Method:** `mcp__google-drive__getGoogleDocContent`

**Usage in Skill:**
- **Mode:** Documentation Mode
- **When:** User requests user story creation or needs template reference
- **How:** Load document to show standard structure and examples

**Content Summary:**
```
Title: User Story Template

Key Sections:
1. Standard Format
   - Title structure
   - "As a... I want... So that..." format
   - Description guidelines
   - Acceptance criteria format

2. Acceptance Criteria Patterns
   - Given-When-Then format
   - Checklist format
   - Edge cases and error scenarios

3. INVEST Guidelines
   - How to apply each principle
   - Common mistakes to avoid
   - Examples of good vs bad stories

4. Example User Stories
   - E-commerce examples
   - SaaS examples
   - Mobile app examples
   - With acceptance criteria

5. Vertical Slicing Guide
   - How to break down features
   - Avoiding horizontal slicing
   - Creating story hierarchies

Length: ~[to be measured]
```

**Integration Example:**
```python
# When documentation mode is triggered
def create_user_stories(requirements):
    # Load user story template from Google Drive
    template_content = mcp.google_drive.getGoogleDocContent(
        documentId="19Ko83lFCidiuZgC5OhiXpvsFVxsOBhhvzF5QcELkHzg"
    )

    # Extract template structure and patterns
    story_format = extract_story_format(template_content)
    ac_patterns = extract_ac_patterns(template_content)

    # Generate user stories following template
    stories = generate_stories(requirements, story_format, ac_patterns)

    # Apply INVEST principles
    validated_stories = apply_invest(stories)

    return validated_stories
```

---

## Evaluation Framework

### Part 1: The 3 C's (from Google Drive Resource)

#### 1. Card - Is the story well-written?

**Evaluation Points:**
- Does it follow "As a [user], I want [goal], so that [benefit]" format?
- Is the title clear and summarizes the content?
- Is the description concise and clear?

**Pass Criteria:**
- All 3 items must be checked
- Story is understandable by all team members
- User, goal, and benefit are all explicit

**Common Issues:**
- ❌ "As a user..." (too generic)
- ❌ Missing "so that" clause (no clear benefit)
- ❌ Title is vague ("Update feature")

---

#### 2. Conversation - Has there been sufficient discussion?

**Evaluation Points:**
- Has the story been discussed with the team?
  - Product Owner
  - Developers
  - QA/Testers
  - Designers
- Are discussion notes documented?
- Have questions and decisions been recorded?

**Pass Criteria:**
- Evidence of team collaboration
- Open questions are documented
- Design/technical decisions are noted

**Common Issues:**
- ❌ No discussion notes
- ❌ Written in isolation
- ❌ Unclear requirements not clarified

---

#### 3. Confirmation - Are acceptance criteria clear?

**Evaluation Points:**
- Do AC clearly define what "done" means?
- Are AC measurable and testable?
- Are edge cases and error scenarios covered?
- Can QA write test cases from the AC?

**Pass Criteria:**
- AC use Given-When-Then or clear checklist
- Success and failure paths defined
- Edge cases documented
- No ambiguity

**Common Issues:**
- ❌ Vague AC ("good UX", "fast performance")
- ❌ Only happy path (no error cases)
- ❌ Not testable or measurable

---

### Part 2: INVEST Principles (from Google Drive Resource)

#### I - Independent

**Question:** Can this story be developed, tested, and deployed independently?

**Evaluation Points:**
- Minimal dependencies on other stories
- Can be worked on in any order
- Doesn't block other stories
- Can be deployed without other changes

**Scoring:**
- ✅ PASS: No or minimal dependencies, explicitly documented
- ⚠️ PARTIAL: Some dependencies, but manageable
- ❌ FAIL: Heavy dependencies, must be combined with other stories

**Example:**
- ✅ PASS: "User can view saved payment methods" (standalone)
- ❌ FAIL: "User can save card details" depends on "User login system" (not independent if login doesn't exist)

---

#### N - Negotiable

**Question:** Does the story focus on outcome (what), not implementation (how)?

**Evaluation Points:**
- Describes user goal, not technical solution
- Team can discuss best implementation approach
- Leaves room for technical decisions
- Focuses on "what" and "why", not "how"

**Scoring:**
- ✅ PASS: Outcome-focused, implementation flexible
- ⚠️ PARTIAL: Some implementation details, but negotiable
- ❌ FAIL: Prescribes technical solution

**Example:**
- ✅ PASS: "User receives order confirmation email"
- ❌ FAIL: "Use SendGrid API to send confirmation via SMTP"

---

#### V - Valuable

**Question:** Does the story provide clear value to user or business?

**Evaluation Points:**
- Benefit is explicit in "so that" clause
- Value to user is clear
- Business impact is understood
- Not purely technical work

**Scoring:**
- ✅ PASS: Clear value in "so that" clause
- ⚠️ PARTIAL: Implicit value, but not clearly stated
- ❌ FAIL: No clear benefit or purely technical

**Example:**
- ✅ PASS: "...so that I can checkout faster on future purchases"
- ❌ FAIL: "...so that data is normalized" (technical, no user value)

---

#### E - Estimable

**Question:** Can the development team estimate effort?

**Evaluation Points:**
- Requirements are clear enough to estimate
- No major unknowns or uncertainties
- Scope is well-defined
- Technical feasibility is understood

**Scoring:**
- ✅ PASS: Team can confidently estimate (even if rough)
- ⚠️ PARTIAL: Some unknowns, but estimable within range
- ❌ FAIL: Too vague or too many unknowns

**Example:**
- ✅ PASS: "User can filter orders by date range" (clear scope)
- ❌ FAIL: "User has great experience" (vague, can't estimate)

---

#### S - Small

**Question:** Can the story be completed within one sprint?

**Evaluation Points:**
- Fits within sprint timebox (typically 1-2 weeks)
- Not an Epic disguised as a story
- Can be broken down if too large
- Delivers incremental value

**Scoring:**
- ✅ PASS: Fits in one sprint (1-2 weeks)
- ⚠️ PARTIAL: Slightly large, but doable
- ❌ FAIL: Too large, is actually an Epic

**Example:**
- ✅ PASS: "User can delete a saved payment method"
- ❌ FAIL: "User can manage all account settings" (Epic)

---

#### T - Testable

**Question:** Can we objectively verify completion?

**Evaluation Points:**
- Clear success/failure criteria
- AC are measurable
- QA can write test cases
- Demo-able to stakeholders

**Scoring:**
- ✅ PASS: Objectively verifiable with clear AC
- ⚠️ PARTIAL: Mostly testable, minor ambiguity
- ❌ FAIL: Subjective or no clear test criteria

**Example:**
- ✅ PASS: "Card is saved and appears in list" (testable)
- ❌ FAIL: "App feels faster" (not objectively testable)

---

### Part 3: Additional Considerations (from Google Drive Resource)

**Checklist:**

1. **User Persona Specificity**
   - [ ] Persona is specific (not generic "user")
   - [ ] Different roles identified if applicable
   - [ ] User needs are clear

**Evaluation:**
- ✅ "As a logged-in customer..."
- ✅ "As a mobile app user..."
- ❌ "As a user..." (too generic)

2. **UI/UX Design References**
   - [ ] Design mockups attached or linked
   - [ ] UI patterns referenced
   - [ ] Accessibility requirements noted

**Evaluation:**
- ✅ Figma/design link included
- ⚠️ Mockup pending, but noted
- ❌ No design reference

3. **Non-Functional Requirements**
   - [ ] Performance requirements defined
   - [ ] Security considerations noted
   - [ ] Scalability requirements documented
   - [ ] Accessibility standards specified

**Evaluation:**
- ✅ "Page loads in <2 seconds"
- ✅ "PCI-DSS compliant encryption"
- ❌ "Should be fast" (vague NFR)

4. **Definition of Ready**
   - [ ] Meets team's DoR checklist
   - [ ] Dependencies documented
   - [ ] Acceptance criteria complete
   - [ ] Estimated by team

**Evaluation:**
- ✅ All DoR items checked
- ⚠️ Partially ready, needs minor updates
- ❌ Does not meet DoR

---

## Feedback Format (from Google Drive Resource)

### 1. Review Report Structure

**Format:**
```
# User Story Review Report

## Story Title: [Title]

### Part 1: The 3 C's
- **Card:** ✅/❌ [Assessment]
  - [Specific findings]
- **Conversation:** ✅/❌ [Assessment]
  - [Specific findings]
- **Confirmation:** ✅/❌ [Assessment]
  - [Specific findings]

### Part 2: INVEST Principles
- **Independent:** ✅/⚠️/❌ [Assessment]
  - [Reason]
- **Negotiable:** ✅/⚠️/❌ [Assessment]
  - [Reason]
- **Valuable:** ✅/⚠️/❌ [Assessment]
  - [Reason]
- **Estimable:** ✅/⚠️/❌ [Assessment]
  - [Reason]
- **Small:** ✅/⚠️/❌ [Assessment]
  - [Reason]
- **Testable:** ✅/⚠️/❌ [Assessment]
  - [Reason]

### Part 3: Additional Considerations
- **User Persona:** ✅/❌ [Assessment]
- **UI/UX Design:** ✅/⚠️/❌ [Assessment]
- **Non-Functional Requirements:** ✅/⚠️/❌ [Assessment]
- **Definition of Ready:** ✅/❌ [Assessment]

---

## Overall Status: ✅ PASS / ⚠️ PARTIAL PASS / ❌ FAIL

---

## Action Items:
1. [Specific improvement 1]
2. [Specific improvement 2]
3. [Specific improvement 3]

---

## Ready for Development: YES / NO

**Recommendation:**
[Summary and next steps]
```

---

### 2. Pass/Fail Decision Logic

**PASS (Ready for Development):**
- All 3 C's: ✅ PASS
- INVEST: At least 5/6 ✅ PASS, 1 ⚠️ acceptable
- Additional: At least 3/4 ✅ or ⚠️
- Action items: Minor or none

**PARTIAL PASS (Needs Minor Revision):**
- All 3 C's: ✅ PASS
- INVEST: 4/6 ✅ PASS, 2 ⚠️ PARTIAL
- Additional: 2/4 ✅ or ⚠️
- Action items: Addressable within 1 day

**FAIL (Major Revision Required):**
- Any of 3 C's: ❌ FAIL
- INVEST: 3+ ❌ FAIL
- Additional: 3+ ❌ FAIL
- Action items: Significant rework needed

---

## Feedback Tone & Style (from Google Drive Resource)

### Guidelines

**구체적으로 (Be Specific):**
- Reference exact parts of the user story
- Quote text when highlighting issues
- Provide concrete examples

**건설적으로 (Be Constructive):**
- Focus on the story, not the author
- Frame as suggestions or questions
- Acknowledge strengths first

**액션아이템 제시 (Provide Action Items):**
- Make feedback actionable
- Suggest specific improvements
- Provide rewrite examples when helpful

**예시 제공 (Give Examples):**
```
Current: "As a user, I want the app to be fast"

Suggested:
"As a mobile user, I want the product list to load
within 2 seconds, so that I can browse without delays"

Why: This makes it testable (2 seconds), specific
(product list), and valuable (browse without delays).
```

**우선순위화 (Prioritize Feedback):**
- Mark must-fix vs. nice-to-have
- Highlight blockers first
- Group related feedback

---

## Usage Guidelines

### When to Reference Google Drive Resources

**User Story Review Checklist:**
- User says "review this user story"
- User asks "is this story ready?"
- User requests "story validation"
- User provides story for feedback
- Sprint planning preparation

**User Story Template:**
- User says "create user stories"
- User asks "how to write user stories"
- User needs "story format guidance"
- User is breaking down features
- Backlog refinement session

### Review Process

1. Load User Story Review Checklist from Google Drive
2. Extract 3 C's, INVEST, and additional criteria
3. Evaluate story against each criterion
4. Score each (Pass/Partial/Fail)
5. Generate feedback following checklist format
6. Provide action items
7. Determine Ready/Not Ready status
8. Provide recommendation

---

## Common User Story Patterns

### Pattern 1: CRUD Operations

**Template:**
```
As a [user persona]
I want to [create/read/update/delete] [object]
So that I can [manage/track/organize] [benefit]

AC:
Given [precondition]
When I [action]
Then [result]
And [additional result]
```

**Example:**
```
As a project manager
I want to delete completed tasks
So that I can keep my task list focused

AC:
Given I have completed tasks in my list
When I click "Delete" and confirm
Then the task is removed from my list
And the task count is updated
```

---

### Pattern 2: Notifications

**Template:**
```
As a [user persona]
I want to receive [notification type] when [event]
So that I can [respond/stay informed] [benefit]

AC:
Given [event occurs]
When [timing condition]
Then I receive [notification details]
And [notification behavior]
```

**Example:**
```
As a customer
I want to receive an email when my order ships
So that I know when to expect delivery

AC:
Given my order status changes to "shipped"
When the carrier picks up the package
Then I receive an email with tracking number
And the email includes estimated delivery date
```

---

### Pattern 3: Data Display/Filtering

**Template:**
```
As a [user persona]
I want to view/filter [data] by [criteria]
So that I can [find/analyze] [benefit]

AC:
Given [data exists]
When I [apply filter/sort]
Then I see [filtered results]
And [behavior details]
```

**Example:**
```
As a sales manager
I want to filter deals by status and date range
So that I can analyze pipeline performance

AC:
Given I have deals in various stages
When I select "Closed Won" and "Last 30 days"
Then I see only matching deals
And the total value is displayed
```

---

## Updates and Maintenance

### Resource Version Tracking

| Resource | Version | Date | Document ID |
|----------|---------|------|-------------|
| User Story Review Checklist | 1.0 | 2025-12-30 | 1xZvwxbvgpDmLC9r0Ni58DNh0hAvDhwAi9hzVxvAG7cs |
| User Story Template | 1.0 | 2025-12-30 | 19Ko83lFCidiuZgC5OhiXpvsFVxsOBhhvzF5QcELkHzg |

### Fallback Strategy

If Google Drive resources are unavailable:
- Use hardcoded 3 C's + INVEST framework (documented in SKILL.md)
- Use built-in template structure
- Note to user that checklist couldn't be loaded
- Proceed with standard evaluation framework

---

## Related Resources

**Skills Using These Resources:**
- `userstory-documentation` (this skill)

**Related Agents:**
- UserStory Agent (`.claude/agents/userstory-agent.md`)
- PRD Agent (provides requirements input)

**Related Documentation:**
- `AGENT_ARCHITECTURE.md` - Full architecture overview
- `SKILL.md` - Complete skill implementation

---

## Access Log Template

```
Date: [YYYY-MM-DD]
Resource: [User Story Review Checklist / User Story Template]
Action: [Loaded/Updated/Failed]
Document ID: [ID]
Result: [Success/Failure]
Notes: [Observations]
```
