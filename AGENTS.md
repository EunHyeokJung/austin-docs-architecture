<!-- 
[AI 에이전트 초기화 지침 - 이 폴더가 초기 템플릿 상태라면 반드시 읽으세요!]
현재 `docs/01-folder-architecture.md`, `docs/02-specs.md`, `docs/03-product-plan.md` 파일과 이 `AGENTS.md` 내부가 비어있거나 [괄호]로 된 템플릿 상태입니다.
사용자를 돕기 위해 아래와 같은 질문을 먼저 던져 프로젝트의 맥락을 파악하고, 답변을 바탕으로 각 문서들의 빈칸을 채워 프로젝트에 맞게 완성해주세요:
1. 개발하실 서비스의 핵심 목적과 주요 피처, 그리고 타겟 유저는 누구인가요?
2. 어떤 주요 기술 스택을 사용하시나요? (예: React, Next.js, 상태 관리 도구, 스타일링 라이브러리 등)
3. 선호하는 폴더 구조나 아키텍처 패턴, 코딩 컨벤션이 있으신가요? (예: FSD, Layered Architecture 등)

문서 내용 채우기 세팅이 모두 완료되면, 에이전트님은 이 주석 블록(1번 줄부터 여기까지)을 완전히 삭제해주세요.
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
- 중대한 변경사항/기록 필요 작업은 `docs/reports`에 `yymmdd-HHMM-number.md` 형식으로 기록
- 템플릿: `docs/reports/_template.md`
- 현재 바로 처리하지 못하지만 추후 반드시 진행해야 하는 작업이 생기면 `docs/todo`에 TODO 문서를 추가
- TODO 추가 시 `docs/todo/00-todo-list.md`에 한 줄 요약도 반드시 함께 갱신
- TODO와 관련된 요청을 받으면 우선 `docs/todo/00-todo-list.md`를 확인하고, 관련 항목이 있으면 해당 TODO 문서를 읽은 뒤 사용자에게 관련 TODO 존재 여부와 반영 범위를 먼저 알릴 것

## 참고
- 이 문서는 에이전트용이므로 간결하게 유지
- 필요 시 여기에 규칙을 추가하되 01/02/03의 내용과 충돌하면 01/02/03을 우선
