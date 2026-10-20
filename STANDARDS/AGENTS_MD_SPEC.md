# AGENTS.md / CLAUDE.md 작성 규격서 (AGENTS_MD_SPEC)
> **벤치마크 출처**: `ChromeDevTools/chrome-devtools-mcp` (Google DevTools 규격) & `GLips/Figma-Context-MCP` (Framelink 규격)

---

## 1. 개요 및 목적
`AGENTS.md` (또는 에디터별 `CLAUDE.md`)는 프로젝트를 수정하고 기능을 구현하는 **AI 코딩 에이전트 전용 가이드라인**입니다. 인간 개발자용 설명서와 달리, 에이전트의 불필요한 추론을 차단하고 엄격한 제약 조건을 주입하여 무결점 코드를 생산하도록 만듭니다.

---

## 2. 필수 규약 섹션 구성

### 2.1 빌드 및 실행 명령어 제약 (Allowed Commands)
- 프로젝트 스크립트 실행 범위를 `package.json` 또는 지정 명령어로 엄격히 제한:
  ```bash
  # 반드시 아래 정의된 명령어만 사용하여 검증할 것
  pnpm install          # 패키지 설치
  pnpm build            # tsc 빌드
  pnpm test             # 전체 테스트 실행
  pnpm test path/to/file.test.ts # 단일 테스트 파일 실행
  pnpm lint             # 정적 린터 검증
  pnpm format           # 코드 포맷팅
  ```

### 2.2 엄격한 타입 원칙 (Strict Typing Rules - No `as any`)
Google ChromeDevTools MCP의 엄격한 엔지니어링 표준 적용:
- **`any` 타입 절대 금지**: 모든 변수, 인자, 반환값은 명시적 인터페이스/타입으로 선언.
- **`as` 키워드(타입 단언) 금지**: 런타임 타입 가드나 검증 함수를 통해 타입 좁히기(Type Narrowing) 수행.
- **`!` (Non-null 단언) 금지**: 옵셔널 체이닝(`?.`)이나 명시적 널 체크 수행.
- **`// @ts-ignore`, `// @ts-nocheck`, `// @ts-expect-error` 금지**: 타입 에러를 억제하지 말고 계약을 올바르게 수정.

### 2.3 테스팅 아키텍처 원칙 (Testing Philosophy)
- **Functional Core, Imperative Shell**:
  - 순수 비즈니스 로직은 순수 함수로 구성하여 빠르고 격리된 유닛 테스트 수행.
  - 외부 I/O, 네트워크, 파일시스템, 브라우저 조작은 시스템 경계에서만 모킹.
- **불필요한 테스트 작성 금지**:
  - 타입 시스템(TypeScript)이 컴파일 타임에 보장하는 내용(타입 체크 등)은 런타임 테스트를 작성하지 않는다.
  - 프레임워크 자체의 동작(Express 라우트 바인딩, React 기본 렌더링 등)은 테스트하지 않고 비즈니스 로직만 테스트한다.

### 2.4 주석 정책 (Comment Policy)
- **금지되는 주석**:
  - 코드가 하는 일을 그대로 반복하는 주석
  - 주석 처리된 레거시 코드
  - 좋은 네이밍 대신 변명으로 달아둔 주석
- **권장되는 주석**:
  - **존재 이유 (Why this exists)**: 이 코드가 해결하는 도메인 문제와 가치
  - **설계 의도 (Why it works this way)**: 중요한 설계 결정 배경
  - **거절된 대안 (Why NOT)**: 검토했으나 실패하여 버린 접근법 (중복 시도 방지)
  - **주의사항 (Warnings)**: 순서 의존성, 비직관적인 함정
  - **의도적 부재 (Negative Space)**: 일부러 처리하지 않고 호출자에게 위임한 사유 명시

### 2.5 토큰 효율성 (Token Efficiency)
- LLM이 모델 가중치로 이미 자연스럽게 추론할 수 있는 기본값(예: CSS 기본 border 정렬 등)은 응답/문서에서 생략하고, 비표준 또는 편차 데이터만 명시하여 컨텍스트 윈도우를 최적화.
