# Idea Generation Skill - Google Drive Resources

## Overview

This document maps the Google Drive resources used by the `idea-generation` skill for validation purposes.

---

## Resource List

### 1. Product Idea Assessment Guide

**Document Information:**
- **Name:** Product Idea Assessment Guide
- **Google Drive ID:** `11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU`
- **Type:** Validation Framework
- **Format:** Google Docs
- **Access Method:** `mcp__google-drive__getGoogleDocContent`

**Usage in Skill:**
- **Mode:** Validation Mode
- **When:** User requests idea validation or review
- **How:** Load document content to reference 10 fundamental questions

**Content Summary:**
```
Title: Assessing Product Opportunities

Key Sections:
1. Introduction to Product Opportunity Assessment
2. 10 Fundamental Questions:
   - What problem will this solve? (value proposition)
   - For whom do we solve that problem? (target market)
   - How big is the opportunity? (market size)
   - What alternatives are out there? (competitive landscape)
   - Why are we best suited to pursue this? (differentiator)
   - Why now? (market window)
   - How will we get this to market? (GTM strategy)
   - How will we measure success? (metrics/revenue)
   - What factors are critical to success? (requirements)
   - What's the recommendation? (go or no-go)
3. Guidance on answering each question
4. Importance of lightweight assessment
5. Strategic decision-making framework

Length: ~6,200 characters
```

**Integration Example:**
```python
# When validation mode is triggered
def validate_idea(idea_description):
    # Load validation guide from Google Drive
    guide_content = mcp.google_drive.getGoogleDocContent(
        documentId="11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU"
    )

    # Extract 10 questions
    questions = extract_validation_questions(guide_content)

    # Assess idea against each question
    assessment = assess_against_questions(idea_description, questions)

    return assessment
```

---

## Resource Access

### How to Load

**In SKILL.md:**
```markdown
When user requests idea validation:

1. Load Google Drive resource:
   - Use mcp__google-drive__getGoogleDocContent
   - Document ID: 11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU

2. Parse 10 fundamental questions from content

3. Guide user through answering each question

4. Provide DVF assessment
```

**Example Prompt:**
```
"To validate your product idea, I'll use the Product Opportunity
Assessment framework from Google Drive. This involves answering
10 fundamental questions to determine if this is a good
opportunity to pursue..."
```

---

## Validation Framework

### 10 Fundamental Questions (from Google Drive Resource)

**1. Value Proposition**
- Question: "Exactly what problem will this solve?"
- Focus: Clear, crisp problem statement
- Common Pitfall: Rambling list of features instead of problem

**2. Target Market**
- Question: "For whom do we solve that problem?"
- Focus: Specific user segments
- Guidance: Be concrete about who

**3. Market Size**
- Question: "How big is the opportunity?"
- Focus: Realistic sizing
- Sources: Analysts, trade associations, finance, bottom-up calculations

**4. Competitive Landscape**
- Question: "What alternatives are out there?"
- Focus: Direct and indirect competition
- Consider: Current workarounds

**5. Differentiator**
- Question: "Why are we best suited to pursue this?"
- Focus: Unique advantage
- Consider: Team, tech, market position

**6. Market Window**
- Question: "Why now?"
- Focus: Timing and urgency
- Consider: Market trends, tech changes

**7. Go-to-Market Strategy**
- Question: "How will we get this product to market?"
- Focus: Distribution and sales channels
- Impact: Significant on product requirements

**8. Metrics/Revenue Strategy**
- Question: "How will we measure success/make money?"
- Focus: Clear success criteria and business model
- Importance: Critical for business case

**9. Solution Requirements**
- Question: "What factors are critical to success?"
- Focus: Dependencies and constraints
- Note: Not full product spec, but key needs

**10. Recommendation**
- Question: "Given the above, what's the recommendation?"
- Focus: Clear go/no-go decision
- Guidance: Based on evidence from questions 1-9

---

## Usage Guidelines

### When to Reference Google Drive Resource

**Trigger Conditions:**
- User says "validate this idea"
- User asks "should we pursue this"
- User requests "idea assessment"
- User provides idea for review
- User asks about opportunity viability

**Validation Process:**
1. Load Google Drive assessment guide
2. Present 10 questions to user
3. Guide user through answering each
4. Synthesize responses
5. Apply DVF framework
6. Provide go/no-go recommendation

### When NOT to Load Resource

- User is in generation mode (brainstorming)
- User is asking about JTBD framework
- User wants competitive analysis only
- User is exploring, not validating

---

## Updates and Maintenance

### Resource Version Tracking

| Version | Date | Changes | Document ID |
|---------|------|---------|-------------|
| 1.0 | 2025-12-30 | Initial mapping | 11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU |

### How to Update

If Google Drive document is updated:
1. Note version and date in table above
2. Update Content Summary if structure changes
3. Update Integration Example if questions change
4. Test skill with new content

### Fallback Strategy

If Google Drive resource is unavailable:
- Use hardcoded 10 questions (documented in SKILL.md)
- Note to user that validation guide couldn't be loaded
- Proceed with standard assessment framework

---

## Related Resources

**Skills Using This Resource:**
- `idea-generation` (this skill)

**Related Agent:**
- Idea Agent (`.claude/agents/idea-agent.md`)

**Related Documentation:**
- `AGENT_ARCHITECTURE.md` - Full architecture overview
- `SKILL.md` - Complete skill implementation

---

## Access Log (for debugging)

**Template for access logging:**
```
Date: [YYYY-MM-DD]
Action: [Loaded/Updated/Failed]
Document ID: 11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU
Result: [Success/Failure]
Notes: [Any issues or observations]
```

**Example:**
```
Date: 2025-12-30
Action: Loaded
Document ID: 11sPz2NUUfuIBzWUQ76J-cjq1BEAWdnvIaLcbLr72zMU
Result: Success
Notes: Content retrieved successfully, 6,196 characters
```
