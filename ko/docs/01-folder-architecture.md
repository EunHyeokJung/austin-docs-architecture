# 1) 폴더 아키텍처 (예: React SPA + FSD)

> ⚠️ 이 문서의 내용은 예시입니다. 실제 프로젝트에 맞게 수정하세요.

본 문서는 **TaskFlow** 서비스의 프론트엔드 폴더 아키텍처를 정의합니다.  
핵심 목표는 다음과 같습니다.

- 서비스 앱 레이어 분리
- FSD(Feature-Sliced Design) 기반 컴포넌트 구조화
- 상태 관리 책임 분리 (서버 상태 vs UI 상태)

---

## A. Top-level 구조 (추천)

```txt
root
├─ .github
│  ├─ workflows
│  └─ ISSUE_TEMPLATE
├─ apps
│  ├─ web                                # 메인 웹 앱
│  └─ admin                              # 관리자 웹 앱 (추후 추가)
│
├─ packages                              # (모노레포 사용 시)
│  ├─ ui                                 # 공용 UI 컴포넌트
│  └─ utils                              # 공용 유틸리티
│
├─ docs                                  # ✅ AI 에이전트 컨텍스트 폴더
│  ├─ 01-folder-architecture.md
│  ├─ 02-specs.md
│  ├─ 03-product-plan.md
│  ├─ reports
│  │  └─ _template.md
│  └─ todo
│     ├─ _template.md
│     └─ 00-todo-list.md
│
├─ package.json
└─ tsconfig.json
```

> `docs/reports`는 완료되었거나 기록이 필요한 작업 내역을 남기는 용도입니다.  
> `docs/todo`는 선행 작업/API 연동/정책 확정 등이 필요해 지금 당장 처리하지 못하는 후속 작업을 남기는 용도입니다.

---

## B. 내부 구조 (예: FSD 스타일)

내부는 **FSD(Feature-Sliced Design)**에 맞춰 아래처럼 구성합니다.

```txt
apps/web/src
├─ app                               # 애플리케이션 진입점 및 전역 설정
│  ├─ providers                      
│  ├─ router                         
│  └─ styles                         
│
├─ pages                             # 라우팅 단위 페이지 컴포넌트
│  ├─ dashboard
│  └─ settings
│
├─ widgets                           # 재사용 가능한 독립적인 뷰 블록
│  ├─ task-board
│  └─ sidebar
│
├─ features                          # 비즈니스 로직을 포함한 핵심 기능 단위
│  └─ create-task
│
├─ entities                          # 도메인 모델 및 도메인 로직
│  └─ task
│
└─ shared                            # 전역 공통/재사용 모듈 (UI 요소, API 등)
   ├─ api
   ├─ ui
   └─ lib
```

- 상위 레이어는 하위 레이어만 import 가능 (예: features → entities ✅, entities → features ❌)
- shared는 모든 레이어에서 import 가능
- 같은 레이어 간 직접 import 금지
