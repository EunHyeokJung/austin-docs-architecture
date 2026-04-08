# 2) Specs (예: React + TypeScript + Vite)

> ⚠️ 이 문서의 내용은 예시입니다. 실제 프로젝트에 맞게 수정하세요.

본 문서는 실제 구현에 사용할 기술 스펙과 운영 규칙을 정의합니다.  
(버전은 팀 컨벤션/템플릿에 맞춰 고정하면 됩니다.)

---

## A. Runtime / Core

- **프레임워크**: React 19
- **언어**: TypeScript 5.x (strict mode)
- **빌드 툴**: Vite 6
- **라우팅**: React Router v7
- **패키지 매니저**: pnpm

---

## B. Data Fetching / Server State

### TanStack Query (React Query)
- 목적: 서버 상태 캐싱/동기화, 로딩/에러 처리 표준화

#### 권장 규칙
- 캐시 키는 도메인 단위로 명확하게 설계 (예: `['tasks', taskId]`, `['users', 'me']`)
- Mutation 성공 시 관련 쿼리 invalidate 전략 통일
- staleTime은 도메인별로 설정 (자주 변하는 데이터: 0, 잘 안 변하는 데이터: 5분)

---

## C. Client State (전역 UI 상태)

### Zustand
- 목적: 클라이언트 UI 상태를 전역으로 관리

#### 권장 규칙
- 서버 데이터를 Zustand에 저장하지 않기 (서버 상태는 TanStack Query가 담당)
- persist 미들웨어는 사용자 설정(테마, 언어 등)에만 사용

---

## D. API Layer & 기타 스펙

- API 통신 도구: Axios (인터셉터로 인증 토큰 자동 주입)
- 스타일링: Tailwind CSS v4

#### 규칙(중요)
- API 호출은 반드시 `shared/api` 래퍼를 통해서만 수행 (직접 axios.get 금지)
- 디자인 토큰은 Tailwind 설정에 정의하고, 하드코딩된 색상/간격 금지

