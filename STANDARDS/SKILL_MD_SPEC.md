# SKILL.md 작성 규격서 (SKILL_MD_SPEC)
> **벤치마크 출처**: `ChromeDevTools/chrome-devtools-mcp` & `21st-dev/magic-mcp`

---

## 1. 개요 및 목적
`SKILL.md`는 에이전트가 특정 전문 작업(예: 접근성 디버깅, UI 컴포넌트 생성, 성능 분석)을 수행할 때 컨텍스트를 동적으로 확장하고 절차적 실행 경로를 안내하는 스킬 매니페스트 규격입니다.

---

## 2. Frontmatter 및 본문 스키마

```markdown
---
name: skill-identifier-name
description: A clear, actionable description of what this skill does and exactly WHEN to activate it (including trigger keywords and negative triggers).
---

# Skill Title

## Overview
Briefly summarize the objective and scope.

## Activation Criteria
- **Trigger when**: Explicit user intents or keywords.
- **Do NOT trigger when**: Alternative skills or tasks outside scope.

## Step-by-Step Workflow
1. Step 1: Pre-flight check & environment validation.
2. Step 2: Main execution & tool invocation.
3. Step 3: Verification & regression check.

## Best Practices & Examples
Concrete examples with exact commands or code snippets.
```
