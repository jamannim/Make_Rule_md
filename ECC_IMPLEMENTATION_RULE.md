# [최우선 구현 규칙] ECC 5단계 라이프사이클 규칙서
> **Highest Priority Directive for All Agent Tasks**  
> **Source Benchmark**: [`affaan-m/ecc`](https://github.com/affaan-m/ecc)

본 문서는 사용자의 지시에 따라 **모든 구현 및 개발 작업 전반에서 최우선으로 준수해야 하는 작업 절차 규칙서**입니다.

---

## 작업 실행 원칙: 5단계 순차 라이프사이클

사용자가 프롬프트로 작업을 지시하면, 에이전트는 무조건 아래의 순서로 실행을 전개합니다:

1. **`[계획 (Plan)]`**
   - **Research & Reuse**: 기존 소스코드, 벤치마크 패턴, 외부 공식 문서를 사전 검증.
   - **Surgical Scope**: 변경 대상 파일과 인터페이스를 최소 범위로 확정하고 잠재 리스크 사전 도출.

2. **`[실행 (Execute)]`**
   - **Simplicity First**: 최소한의 코드로 구현 (조기 추상화 및 불필요한 방어 코드 배제).
   - **Strict Typing**: `any` 타입 및 안전하지 않은 타입 단언(`as`) 완전 금지.

3. **`[검증 (Verify)]`**
   - **Evidence Before Assertion**: 빌드, 타입 체크, 단위 테스트 등 실제 검증 명령어를 실행하여 종료 코드(Exit Code 0)와 출력 로그 실측.

4. **`[재시도 (Retry)]`** (검증 실패 시 자율 구동)
   - 근본 원인(Root Cause) 진단 -> 가설 수립 -> 정밀 수정 -> 재검증 통과 루프 수행.

5. **`[최종 완성 (Final Completion)]`**
   - 실측 증거 제시, 산출물 파일 링크(`file://`), 결론 우선 3~5줄 요약 보고.

*상세 명세는 [`STANDARDS/00_HIGHEST_PRIORITY_ECC_WORKFLOW.md`](STANDARDS/00_HIGHEST_PRIORITY_ECC_WORKFLOW.md)를 참조하십시오.*
