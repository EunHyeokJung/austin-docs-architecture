<!-- 
[AI 에이전트 초기화 지침]
이 파일과 docs/ 내 문서들이 예시/플레이스홀더 상태라면, 아래 절차를 따르세요:

1. 프로젝트의 기존 코드베이스를 조회합니다 (package.json, 폴더 구조, 소스 파일, 설정 파일 등).
2. 코드가 없거나 정보가 부족하면 사용자에게 질문합니다:
   - 서비스의 핵심 목적, 주요 기능, 타겟 사용자는?
   - 사용할 기술 스택은? (프레임워크, 언어, 상태 관리, 스타일링 등)
   - 선호하는 폴더 구조, 아키텍처 패턴, 코딩 컨벤션이 있는지?
3. 파악한 정보를 바탕으로 아래 파일들의 예시 내용을 실제 프로젝트 정보로 교체합니다:
   - `AGENTS.md` — 체크리스트, 코드 규칙, 참조 경로 수정
   - `docs/01-folder-architecture.md` — 실제 폴더 구조와 책임 정의
   - `docs/02-specs.md` — 실제 기술 스택, 라이브러리, 구현 규칙 정의
   - `docs/03-product-plan.md` — 실제 제품 범위, 사용자, 기능 정의
4. 각 문서의 `⚠️ 예시` 경고를 삭제합니다.
5. 모든 문서 작성이 완료되면, 이 주석 블록(1번 줄부터 여기까지)을 완전히 삭제합니다.
-->

# Agent Working Agreement

This file is for any developer agent (Codex, Copilot, etc.) working in this repo.
The goal is to keep everyone aligned even when different agents are used.

## 반드시 읽기 (매 작업 전)
- `docs/01-folder-architecture.md`
- `docs/02-specs.md`
- `docs/03-product-plan.md`
- `docs/todo/00-todo-list.md`

## 작업 시작 체크리스트
- 위 필수 문서를 읽었는가
- `docs/todo/00-todo-list.md`를 확인했는가
- 작업이 [프로젝트의 핵심 목표/범위]를 벗어나지 않는가
- 폴더 구조와 [아키텍처 패턴 이름] 패턴 규칙을 지키는가
- API 사용은 [허용된 API 경로/규칙]만 사용하는가
- UI/스타일링은 [프로젝트의 스타일링 규칙] 방식인가
- 현재 작업과 관련된 TODO가 있으면 해당 `docs/todo/*.md`를 읽고 사용자에게 먼저 알렸는가

## 코드 변경 규칙 (요약)
- [예시: generated 직접 import 금지]
- [예시: shared/ui 우선 사용]
- [예시: 서버 상태는 TanStack Query, UI 상태는 Zustand]
- [내 프로젝트에 맞는 코드 컨벤션 추가]

## 문서 업데이트 규칙
- 구조/스펙/기획 변경 시 해당 문서(01/02/03)를 반드시 업데이트
- 이번 작업이 문서 내용과 다르면 먼저 문서를 갱신한 뒤 코드 수정
- 중대한 변경사항/기록 필요 작업은 `docs/reports`에 `yymmdd-HHMM-NN-작업키워드.md` 형식으로 기록
- 템플릿: `docs/reports/_template.md`
- 현재 바로 처리하지 못하지만 추후 반드시 진행해야 하는 작업이 생기면 `docs/todo`에 TODO 문서를 추가
- TODO 추가 시 `docs/todo/00-todo-list.md`에 한 줄 요약도 반드시 함께 갱신
- TODO 완료 시 해당 TODO 파일을 삭제하고, `docs/reports/`에 작업 기록을 남긴 뒤, `docs/todo/00-todo-list.md`에서도 제거
- TODO와 관련된 요청을 받으면 우선 `docs/todo/00-todo-list.md`를 확인하고, 관련 항목이 있으면 해당 TODO 문서를 읽은 뒤 사용자에게 관련 TODO 존재 여부와 반영 범위를 먼저 알릴 것

## 참고
- 이 문서는 에이전트용이므로 간결하게 유지
- 필요 시 여기에 규칙을 추가하되 01/02/03의 내용과 충돌하면 01/02/03을 우선
