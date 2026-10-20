<div align="center">

# Make_Rule_md

**오픈소스 Markdown (*.md) 표준 벤치마킹 및 AI 에이전트 작업 규격서**  
*Benchmarking Industry-Leading Open-Source Standards for Flawless Markdown & Code Generation*

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Standards: 5 Source Benchmarks](https://img.shields.io/badge/Benchmarks-5%20Verified%20Sources-10b981.svg)](#1-벤치마크-오픈소스-출처)
[![Design Tokens: Google Stitch](https://img.shields.io/badge/Spec-DESIGN.md%20%7C%20AGENTS.md-orange.svg)](#2-표준-명세서-목록)

</div>

<br/>

## 1. 개요 (Overview)

`Make_Rule_md`는 AI 코딩 에이전트(Antigravity, Cursor, Claude, Codex 등)와 엔지니어가 개발 및 문서화 작업을 수행하기 전에 **GitHub 최고 수준의 오픈소스 프로젝트 5종의 표준 마크다운 규격을 사전 참조하고 벤치마킹하여 결과물에 완벽히 녹여낼 수 있도록 구축된 통합 레퍼런스 저장소**입니다.

모든 작업 전에 본 저장소의 규격을 사전 점검함으로써, 단순 텍스트 나열을 넘어 기계 판독성(Machine-readability)과 인간 가독성(Human-readability), 엄격한 타입 안전성 및 토큰 효율성을 동시에 달성합니다.

---

## 2. 벤치마크 오픈소스 출처 (Reference Matrix)

본 저장소에는 사용자의 요청에 따라 다음 5대 대표 오픈소스의 공식 코드베이스 및 핵심 명세가 로컬로 복제되어 있습니다:

| 프로젝트명 | 복제 대상 및 주요 파일 | 원본 저장소 | 벤치마킹 핵심 역할 |
| :--- | :--- | :--- | :--- |
| **`awesome-design-md`** | `awesome-design-md/design-md` (160+개 브랜드 명세) | [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | `DESIGN.md` YAML 토큰 규격 (색상, 타이포, 간격) 및 시각 가이드라인 |
| **`Figma-Context-MCP`** | `Figma-Context-MCP/README.md`, `CLAUDE.md` | [GLips/Figma-Context-MCP](https://github.com/GLips/Figma-Context-MCP) | MCP README 히어로 배너, 토큰 효율화, 고가치 주석 정책 및 테스팅 철학 |
| **`firecrawl-mcp-server`** | `firecrawl-mcp-server/README.md` | [firecrawl/firecrawl-mcp-server](https://github.com/firecrawl/firecrawl-mcp-server) | 프로덕션 MCP README 표준, 도구 선택 매트릭스, 멀티 클라이언트 설치 가이드 |
| **`chrome-devtools-mcp`** | `chrome-devtools-mcp` (AGENTS.md, docs, skills) | [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | `AGENTS.md` Google 엔지니어링 표준, Zero `any`/`as`/`!` 엄격 타이핑 규칙 |
| **`magic-mcp`** | `magic-mcp` (README.md, llms-install.md, skills) | [21st-dev/magic-mcp](https://github.com/21st-dev/magic-mcp) | 현대적 UI 컴포넌트 생성 에이전트 규격, `llms-install.md`, 스킬 구조 |

*상세 커밋 및 메타데이터는 [`SOURCES.json`](SOURCES.json)에서 확인하실 수 있습니다.*

---

## 3. 표준 명세서 디렉토리 (Synthesized Standards)

벤치마킹된 오픈소스의 규칙을 체계화한 가이드라인은 [`STANDARDS/`](STANDARDS/) 디렉토리에 수록되어 있습니다:

1. **[`RULE_MD_STANDARDS.md`](STANDARDS/RULE_MD_STANDARDS.md)**: 오픈소스 Markdown (*.md) 종합 표준 및 사전 점검 체크리스트
2. **[`DESIGN_MD_SPEC.md`](STANDARDS/DESIGN_MD_SPEC.md)**: `DESIGN.md` 표준 (Google Stitch & VoltAgent 디자인 토큰 규격)
3. **[`MCP_README_SPEC.md`](STANDARDS/MCP_README_SPEC.md)**: MCP 서버 및 오픈소스 라이브러리 `README.md` 작성 규격서
4. **[`AGENTS_MD_SPEC.md`](STANDARDS/AGENTS_MD_SPEC.md)**: `AGENTS.md` / `CLAUDE.md` 에이전트 실행 및 엄격 제약 규격서
5. **[`SKILL_MD_SPEC.md`](STANDARDS/SKILL_MD_SPEC.md)**: 에이전트 확장 도구용 `SKILL.md` 작성 규격서

---

## 4. 디렉토리 구조 (Repository Layout)

```text
Make_Rule_md/
├── awesome-design-md/         # VoltAgent 공식 레포 (160+개 브랜드 DESIGN.md 포함)
│   └── design-md/             # Apple, Stripe, Linear, Supabase 등 실측 디자인 시스템
├── Figma-Context-MCP/         # Framelink MCP 레포 (README.md, CLAUDE.md 등)
├── firecrawl-mcp-server/      # Firecrawl 공식 MCP 레포 (README.md 등)
├── chrome-devtools-mcp/       # Google Chrome DevTools 공식 MCP 레포 (AGENTS.md 등)
├── magic-mcp/                 # 21st.dev Magic MCP 레포 (skills, llms-install.md 등)
├── STANDARDS/                 # 벤치마크 기반 종합 표준 규격서
│   ├── RULE_MD_STANDARDS.md   # 마크다운 종합 작성 표준
│   ├── DESIGN_MD_SPEC.md      # DESIGN.md 작성 규격
│   ├── MCP_README_SPEC.md     # README.md 작성 규격
│   ├── AGENTS_MD_SPEC.md      # AGENTS.md 작성 규격
│   └── SKILL_MD_SPEC.md       # SKILL.md 작성 규격
├── SOURCES.json               # 5개 원본 오픈소스 출처 및 커밋 메타데이터
└── README.md                  # 본 통합 레퍼런스 안내서
```

---

## 5. 작업 전 AI 에이전트 행동 지침 (Operational Directive)

AI 코딩 에이전트는 사용자의 요청으로 산출물을 생성하기 전 아래 순서를 반드시 따릅니다:

1. **사전 레퍼런스 점검**: 생성할 문서 형식에 맞는 `STANDARDS/` 내 명세서 및 벤치마크 원본 폴더의 실제 구현 코드를 열람합니다.
2. **엄격한 규칙 주입**:
   - UI/디자인 작업 시: `awesome-design-md/design-md`의 디자인 토큰 및 `DESIGN_MD_SPEC.md` 준수.
   - MCP/도구 설명서 작업 시: `firecrawl-mcp-server`의 도구 선택 매트릭스 및 `MCP_README_SPEC.md` 준수.
   - 개발/타입스크립트 작업 시: `chrome-devtools-mcp`의 엄격 타이핑(Zero `any`, Zero `as`) 원칙 준수.
3. **군더더기 및 중복 배제**: 제목-서브내용 간 텍스트 중복을 원천 차단하고 상위 맥락에서 단일화합니다.
4. **실측 검증(Zero Hallucination)**: 가상 수치나 미확인 URL을 기재하지 않고 실측 검증된 사실만 반영합니다.
