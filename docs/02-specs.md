# 2) Specs ([주요 스택 요약])

본 문서는 실제 구현에 사용할 기술 스펙과 운영 규칙을 정의합니다.  
(버전은 팀 컨벤션/템플릿에 맞춰 고정하면 됩니다.)

---

## A. Runtime / Core

- **프레임워크**: [React, Next.js, Vue 등]
- **언어**: TypeScript (권장)
- **빌드 툴**: [Vite, Webpack 등]
- **라우팅**: [React Router 등]
- **패키지 매니저**: [pnpm, npm, yarn 등]

---

## B. Data Fetching / Server State

### [데이터 페칭 라이브러리, 예: TanStack Query]
- 목적: 서버 상태 캐싱/동기화, 로딩/에러 처리 표준화

#### 권장 규칙
- [캐시 키 설계 규칙, 예: 도메인 단위로 명확하게 설계]
- [갱신 전략, 예: Mutation 성공 시 invalidate 전략 통일]

---

## C. Client State (전역 UI 상태)

### [상태 관리 라이브러리, 예: Zustand, Redux]
- 목적: 클라이언트 UI 상태를 전역으로 관리

#### 권장 규칙
- [규칙 1, 예: 서버 데이터는 저장하지 않기]
- [규칙 2, 예: 로컬 스토리지 동기화 방법]

---

## D. API Layer & 기타 스펙

- API 통신 도구: [Axios, Fetch, OpenAPI Generator 등]
- 스타일링: [Tailwind, Styled-components, CSS Modules 등]

#### 규칙(중요)
- [API 관련 핵심 제약, 예: 직접 호출 금지, 래퍼 사용 필수 등]
- [스타일링 관련 핵심 제약, 예: 디자인 토큰 필수 사용 등]

