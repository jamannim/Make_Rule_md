# DESIGN.md 작성 규격서 및 템플릿 (DESIGN_MD_SPEC)
> **벤치마크 출처**: `VoltAgent/awesome-design-md` & Google Stitch / Google Labs 규격

---

## 1. 개요 및 목적
`DESIGN.md`는 AI 코딩 에이전트(Google Stitch, Claude, Cursor, Antigravity 등)가 무거운 Figma 파일이나 복잡한 JSON 스키마 없이도 일관되고 세련된 UI를 생성할 수 있도록 제공하는 **플레인 텍스트 기반 디자인 시스템 명세서**입니다.

---

## 2. 표준 템플릿 구조

`DESIGN.md`는 상단의 **YAML Frontmatter (기계 판독용 토큰)**와 하단의 **Markdown 본문 (인간 및 에이전트 이해용 원칙)**으로 구성됩니다.

```markdown
---
version: 1.0.0
name: Brand-Name-Design-System
description: A concise 3-4 sentence summary of the visual language, core aesthetic (e.g. minimalist, brutalist, luxury dark), dominant hues, and layout rhythm.

colors:
  # Primary Brand Palette
  primary: "#0066FF"
  primary-hover: "#0052CC"
  primary-active: "#003D99"
  primary-subtle: "#EBF3FF"

  # Neutral Surfaces & Canvas
  canvas: "#FFFFFF"
  canvas-subtle: "#F8FAFC"
  surface: "#FFFFFF"
  surface-hover: "#F1F5F9"
  border: "#E2E8F0"
  border-focus: "#0066FF"

  # Text & Content
  text-primary: "#0F172A"
  text-secondary: "#475569"
  text-muted: "#94A3B8"
  text-on-primary: "#FFFFFF"

  # Semantic Feedback
  success: "#10B981"
  warning: "#F59E0B"
  error: "#EF4444"
  info: "#3B82F6"

typography:
  font-family-display: "Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif"
  font-family-body: "Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif"
  font-family-code: "'JetBrains Mono', 'Fira Code', monospace"
  scale:
    display:
      size: "3rem"       # 48px
      lineHeight: "1.15"
      weight: "700"
      letterSpacing: "-0.025em"
    h1:
      size: "2.25rem"    # 36px
      lineHeight: "1.2"
      weight: "700"
      letterSpacing: "-0.02em"
    h2:
      size: "1.75rem"    # 28px
      lineHeight: "1.25"
      weight: "600"
      letterSpacing: "-0.015em"
    body:
      size: "1rem"       # 16px
      lineHeight: "1.5"
      weight: "400"
      letterSpacing: "0"
    caption:
      size: "0.875rem"   # 14px
      lineHeight: "1.4"
      weight: "400"
      letterSpacing: "0.01em"

spacing:
  base: "4px"
  xs: "4px"
  sm: "8px"
  md: "16px"
  lg: "24px"
  xl: "32px"
  xxl: "48px"

radius:
  sm: "4px"
  md: "8px"
  lg: "12px"
  full: "9999px"

shadows:
  subtle: "0 1px 3px 0 rgba(0, 0, 0, 0.05)"
  card: "0 4px 6px -1px rgba(0, 0, 0, 0.08), 0 2px 4px -2px rgba(0, 0, 0, 0.05)"
  elevated: "0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.05)"
---

# Design System Guidelines

## 1. Visual Philosophy
- **Clarity over Clutter**: Keep density balanced, avoid decorative borders that don't delineate functional zones.
- **Predictable Hierarchy**: Content scales strictly follow the typographic scale defined above.

## 2. Core Components

### 2.1 Buttons
- **Primary Button**: Solid `primary` background, `text-on-primary`, `radius.md`, medium weight text.
- **Secondary Button**: `surface` background, 1px `border`, `text-primary`.
- **States**: Hover changes surface brightness by 5%, Active depresses by 1px or scales to 0.99.

### 2.2 Cards & Containers
- Clean 1px hairlines using `border`.
- Padding defaults to `spacing.lg` (24px) for desktop and `spacing.md` (16px) for mobile.

## 3. Do's and Don'ts

| Do | Don't |
| :--- | :--- |
| Use predefined color variables and tokens. | Hardcode raw hex colors in component styles. |
| Maintain high contrast ratios (WCAG AAA/AA). | Use muted text for critical labels or callouts. |
| Use tabular numbers (`font-variant-numeric: tabular-nums`) for currency and data tables. | Use proportional figures for financial or numerical matrices. |
```
