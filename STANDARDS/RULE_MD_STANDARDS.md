# 오픈소스 Markdown (*.md) 종합 표준 및 벤치마킹 규칙서
> **Make_Rule_md Master Guideline**  
> 본 문서는 GitHub 최고 수준의 오픈소스 프로젝트 5종(`awesome-design-md`, `Figma-Context-MCP`, `firecrawl-mcp-server`, `chrome-devtools-mcp`, `magic-mcp`)의 마크다운 규격을 실측·분석하여, AI 코딩 에이전트와 엔지니어가 모든 작업 전에 준수해야 할 통합 표준 규칙을 정의합니다.

---

## 1. 벤치마크 대상 및 역할 정의 (Reference Taxonomy)

| 파일 유형 | 주 독자 (Consumer) | 정의 및 핵심 역할 | 벤치마크 출처 |
| :--- | :--- | :--- | :--- |
| **`README.md`** | 개발자, 사용자, 오픈소스 기여자 | 프로젝트 개요, 아키텍처, 설치/설정 매트릭스, 도구 시그니처, 트러블슈팅 | `firecrawl-mcp-server`, `Figma-Context-MCP` |
| **`DESIGN.md`** | 디자인 에이전트 (Google Stitch, Claude, Cursor) | YAML 기반 디자인 토큰(색상, 타이포그래피, 간격 등) 및 UI 컴포넌트 시각 규칙 | `VoltAgent/awesome-design-md/design-md` |
| **`AGENTS.md` / `CLAUDE.md`** | AI 코딩 에이전트 (Antigravity, Codex, Cursor) | 프로젝트 빌드/테스트 제약, 엄격한 타입/테스팅 규칙, 허용 명령어 및 컨벤션 | `chrome-devtools-mcp`, `Figma-Context-MCP` |
| **`SKILL.md`** | 에이전트 스킬 엔진 / MCP Runner | 메타데이터(YAML frontmatter), 실행 절차, 스크립트/도구 트리거 조건 | `chrome-devtools-mcp/skills`, `magic-mcp/skills` |
| **`CONTRIBUTING.md`** | 오픈소스 기여자 | PR 규칙, Conventional Commits, 커뮤니케이션 매너, 릴리즈 워크플로우 | `Figma-Context-MCP`, `chrome-devtools-mcp` |

---

## 2. 공통 마크다운 포맷팅 표준 (Universal Authoring Rules)

### 2.1 헤더 및 메타데이터 구조
- **Dark/Light 대응 히어로 배너**: 테마에 반응하는 `<picture>` 태그를 활용하여 GitHub 다크모드 및 라이트모드에 완벽 대응.
- **배지(Badges) 표준화**:
  - 버전, 라이선스, 빌드 상태, 패키지 다운로드 수, 커뮤니티(Discord/Slack) 순환 배치.
  - 일관된 스타일(`flat-square` 또는 `classic`) 및 정확한 URL 검증.
- **목차(Table of Contents)**: 내용이 5개 섹션 이상일 경우 명확한 앵커 링크 제공.

### 2.2 코드 블록 및 문법 강조
- 반드시 정확한 언어 식별자 지정 (`bash`, `json`, `yaml`, `typescript`, `python` 등).
- 패키지 매니저 및 클라이언트별 탭/멀티 섹션 제공 (`npm`, `pnpm`, `yarn`, `bun` 또는 `npx`, `docker`).
- 주석 정책: 단순 동작 반복 주석은 금지하고 **존재 이유(Why)**, **비결정적 제약(Warnings)**, **의도적 미처리(Negative Space)** 위주로 작성.

### 2.3 경고/안내 배너 (Admonitions)
- GitHub 표준 Alert 블록 활용:
  ```markdown
  > [!NOTE] 배경 맥락, 아키텍처 의도 및 참고사항
  > [!TIP] 성능 최적화, 모범 사례 및 효율성 팁
  > [!IMPORTANT] 필수 요구조건 및 핵심 선행 절차
  > [!WARNING] 호환성 문제, 변경점 및 주의사항
  ```

---

## 3. 핵심 문서별 상세 벤치마킹 규칙

### 3.1 `DESIGN.md` 표준 (Google Stitch & VoltAgent 규격)
1. **Machine-Readable YAML Frontmatter 필수**:
   - `version`: 규격 버전 (예: `alpha`, `1.0.0`)
   - `name`: 디자인 시스템 명칭
   - `description`: 3-5줄의 시각 언어 요약 및 배경
   - `colors`: Primary, Surface, Canvas, Text, Accent, Border 색상 헥사코드
   - `typography`: 폰트 패밀리, 계층별(font-size, line-height, letter-spacing, font-weight)
   - `spacing`, `radius`, `shadows`: 단위(px/rem)가 명시된 토큰
2. **Human & Agent Readable Prose**:
   - `Design Principles`: 3~4대 핵심 원칙
   - `Component Specifications`: 버튼, 인풋, 카드 등의 구조적 상태 (Default, Hover, Active, Disabled)
   - `Do's and Don'ts`: 명확한 대비 표를 통한 환각 방지

### 3.2 `README.md` 표준 (MCP & Open Source 규격)
1. **문제 정의와 해결책 (Problem & Value Proposition)**:
   - "이 프로젝트가 왜 필요한가? 기존 방식(예: 스크린샷 붙여넣기, 수동 복사) 대비 어떤 가치를 주는가?"
2. **도구 선택 매트릭스 (Tool Decision Matrix)**:
   - 복수 개의 MCP 도구가 존재할 때, 어떤 상황에 어떤 도구를 호출해야 하는지 비교 표 제공.
3. **멀티 클라이언트 연동 가이드**:
   - Claude Desktop, Cursor, Windsurf, VS Code, Codex 등 주요 에이전트 설정 JSON 제공.
4. **엄격한 에러 처리 및 트러블슈팅 표**:
   - 예상 가능한 오류 코드와 명확한 해결 가이드 명시.

### 3.3 `AGENTS.md` / `CLAUDE.md` 표준 (Google DevTools & Framelink 규격)
1. **명령어 허용 범위 제한**:
   - 허용된 스크립트(`package.json` 또는 지정 CLI) 명시.
2. **엄격한 타입 안전성**:
   - `any` 금지, 타입 캐스팅(`as`) 금지, non-null 단언(`!`) 금지, `@ts-ignore` 금지.
3. **테스트 아키텍처 원칙**:
   - Functional core, Imperative shell: 순수 비즈니스 로직과 I/O 분리.
   - Mock 유닛 테스트와 실제 통합 테스트의 경계 명확화.
4. **토큰 효율성 (Token Efficiency)**:
   - LLM이 추론 가능한 기본값은 문서나 도구 출력에서 생략하고, 비표준/편차만 명시하여 컨텍스트 토큰 절약.

---

## 4. 작업 전 사전 점검 체크리스트 (Pre-Task Verification)

모든 작업(코드 생성, 문서 작성, PR 생성) 착수 전 다음 5단계를 교차 검증합니다:

- [ ] **1단계: 대상 문서 식별**: 작업 목적에 맞는 파일 형식(`README.md`, `DESIGN.md`, `AGENTS.md` 등)을 선정했는가?
- [ ] **2단계: 벤치마크 패턴 대조**: `Make_Rule_md` 내 해당 오픈소스 원본 문서를 열람하고 최신 모범 패턴을 확인했는가?
- [ ] **3단계: 불필요 텍스트/중복 제거**: UI 텍스트 및 마크다운 내 중복 설명과 군더더기 표현을 단일화했는가?
- [ ] **4단계: URL 및 수치 실측 검증**: 기재된 링크, 버전, 지표 수치가 실제 외부 원본과 100% 일치하는가?
- [ ] **5단계: 에이전트 컨텍스트 최적화**: 생성물이 LLM에게 불필요한 토큰 낭비 없이 명확한 제약을 전달하는가?
