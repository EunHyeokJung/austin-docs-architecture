[English](README.md)

# Austin's Docs Architecture for AI

AI 코딩 에이전트와 사람이 같은 기준으로 협업할 수 있도록 설계한 docs-first 저장소 템플릿입니다.

긴 프롬프트를 매번 다시 설명하는 대신, 프로젝트 규칙과 제품 맥락을 저장소 안의 고정된 문서 구조로 관리합니다. 이때 docs는 프로젝트 운영을 위한 single source of truth(단일 진실의 원천) 역할을 합니다. 에이전트는 작업 전에 필요한 문서를 읽고, 범위와 규칙을 확인한 뒤, 구현과 기록을 이어서 수행합니다.

## 무엇을 해결하나

- 프로젝트 맥락이 채팅 히스토리에만 남아 사라지는 문제
- 세션이 바뀔 때마다 에이전트가 같은 설명을 반복해서 요구하는 문제
- 아키텍처, 스펙, 제품 범위가 코드와 따로 노는 문제
- 후속 TODO와 작업 이력이 흩어져 인수인계가 어려운 문제

## 핵심 구성

- `AGENTS.md`
  - 에이전트 공통 작업 합의서
  - 작업 전 필독 문서, 체크리스트, 변경 규칙 정의
- `docs/01-folder-architecture.md`
  - 저장소 구조와 폴더 책임 정의
- `docs/02-specs.md`
  - 기술 스택, 구현 규칙, 제약 사항 정의
- `docs/03-product-plan.md`
  - 제품 범위, 사용자, 핵심 기능 정의
- `docs/reports/`
  - 완료 작업과 중요한 변경 기록
- `docs/todo/`
  - 지금 처리하지 못한 후속 작업 관리

## 저장소 구조

```text
.
├─ README.md          # English
├─ README.ko.md       # 한국어
├─ LICENSE
├─ en                 # ← English template bundle
│  ├─ AGENTS.md
│  └─ docs
│     ├─ 01-folder-architecture.md
│     ├─ 02-specs.md
│     ├─ 03-product-plan.md
│     ├─ reports
│     │  └─ _template.md
│     └─ todo
│        ├─ 00-todo-list.md
│        └─ _template.md
└─ ko                 # ← 한국어 템플릿 번들
   ├─ AGENTS.md
   └─ docs
      ├─ 01-folder-architecture.md
      ├─ 02-specs.md
      ├─ 03-product-plan.md
      ├─ reports
      │  └─ _template.md
      └─ todo
         ├─ 00-todo-list.md
         └─ _template.md
```

각 언어 폴더(`en/`, `ko/`)에 `AGENTS.md` + `docs/` 완전한 템플릿 번들이 들어 있습니다.

## 동작 방식

1. 프로젝트 시작 시 `AGENTS.md`와 `docs/01`, `docs/02`, `docs/03`에 팀 규칙과 제품 맥락을 기록합니다.
2. 에이전트는 작업 전에 해당 문서와 `docs/todo/00-todo-list.md`를 읽습니다.
3. 요청이 문서와 충돌하면 문서를 먼저 갱신한 뒤 작업합니다.
4. 중요한 변경은 `docs/reports/`에 남기고, 막힌 후속 작업은 `docs/todo/`에 남깁니다.

## 추천 사용 시나리오

- 새 프로젝트를 시작하면서 AI 협업 규칙을 초기에 고정하고 싶은 팀
- 여러 에이전트와 개발자가 번갈아 작업하는 저장소
- 제품 문서, 기술 규칙, 작업 기록을 코드와 함께 관리하려는 팀
- docs-driven 개발 프로세스를 실험하거나 도입하려는 개인 개발자

## 시작 방법

> **가장 쉬운 방법:** AI에게 다음 내용을 요청하세요:  
> *"이 워크스페이스에 https://github.com/EunHyeokJung/austin-docs-architecture 를 적용해줘."*  
> AI가 아래의 모든 과정을 자동으로 처리합니다.

### AI 세팅 가이드 (에이전트용)

이 템플릿을 프로젝트에 적용하라는 요청을 받은 AI 에이전트는 아래 단계를 **순서대로** 수행하세요:

**Step 1 — 언어 선택**
- 사용자에게 선호 언어를 질문합니다: **영어(`en/`)** 또는 **한국어(`ko/`)**.
- 사용자가 지정하지 않으면, 프로젝트의 기존 파일이나 대화 언어로 추론합니다.

**Step 2 — 템플릿 번들을 프로젝트 루트에 복사**
- 선택한 언어 폴더의 `AGENTS.md`와 `docs/`를 프로젝트 루트로 복사합니다:

```bash
# 한국어
cp ko/AGENTS.md . && cp -r ko/docs . && rm -rf en ko

# English
cp en/AGENTS.md . && cp -r en/docs . && rm -rf en ko
```

**Step 3 — 프로젝트 파악**
- 프로젝트의 기존 코드베이스를 조회합니다: package.json, 폴더 구조, 소스 파일, 설정 파일 등.
- 프로젝트가 비어 있거나 코드가 없으면, 사용자에게 아래를 질문합니다:
  1. 서비스의 핵심 목적, 주요 기능, 타겟 사용자는?
  2. 사용할 기술 스택은? (프레임워크, 언어, 상태 관리, 스타일링 등)
  3. 선호하는 폴더 구조, 아키텍처 패턴, 코딩 컨벤션이 있는지?

**Step 4 — 문서 작성**
- 아래 파일들의 예시/플레이스홀더 내용을 실제 프로젝트 정보로 교체합니다:
  - `AGENTS.md` — 체크리스트, 코드 규칙, 참조 경로를 프로젝트에 맞게 수정
  - `docs/01-folder-architecture.md` — 실제 폴더 구조와 책임 정의
  - `docs/02-specs.md` — 실제 기술 스택, 라이브러리, 구현 규칙 정의
  - `docs/03-product-plan.md` — 실제 제품 범위, 사용자, 기능 정의
- 각 문서의 `⚠️ 예시` 경고를 삭제합니다.

**Step 5 — 정리**
- `AGENTS.md` 최상단의 초기화 주석 블록(`<!-- ... -->`)을 삭제합니다.
- 이 템플릿 저장소의 `README.md`, `README.ko.md`가 남아 있다면 삭제합니다 (프로젝트 자체 README를 사용해야 합니다).

**세팅 완료 후 프로젝트 구조:**

```text
.
├─ AGENTS.md
├─ docs
│  ├─ 01-folder-architecture.md
│  ├─ 02-specs.md
│  ├─ 03-product-plan.md
│  ├─ reports
│  │  └─ _template.md
│  └─ todo
│     ├─ 00-todo-list.md
│     └─ _template.md
└─ (프로젝트 파일들...)
```

### 수동 설치

직접 설정하고 싶다면:

1. 이 저장소를 클론 또는 복사합니다.
2. 원하는 언어의 번들을 프로젝트 루트로 복사합니다:

```bash
# 한국어
cp ko/AGENTS.md . && cp -r ko/docs . && rm -rf en ko

# English
cp en/AGENTS.md . && cp -r en/docs . && rm -rf en ko
```

3. `AGENTS.md`, `docs/01`, `docs/02`, `docs/03`의 예시 내용을 프로젝트에 맞게 교체합니다.
4. `AGENTS.md` 최상단의 초기화 주석 블록을 삭제합니다.
5. 작업 기록은 `docs/reports/`, 후속 작업은 `docs/todo/`에 정리합니다.

## 의도한 워크플로

<img width="1118" height="629" alt="austin-docs-architecture-workflow-chart" src="https://github.com/user-attachments/assets/3099d38c-c223-4416-ad4f-314563225952" />

## 운영 원칙

- 문서는 참고 자료가 아니라 실행 기준입니다.
- docs는 프로젝트 운영을 위한 single source of truth(단일 진실의 원천)로 관리합니다.
- 코드와 문서가 어긋나면 문서를 먼저 맞춥니다.
- TODO는 한곳에서 찾을 수 있어야 합니다.
- 작업 기록은 다음 사람과 다음 세션을 위해 남깁니다.

## License

이 저장소는 커스텀 템플릿 라이선스를 사용합니다.

- 프로젝트에 가져다 쓰고 수정할 수 있습니다.
- 상업용 서비스나 클라이언트 프로젝트에 사용할 수 있습니다.
- 이 구조 자체를 템플릿, 스타터, 보일러플레이트 상품으로 판매하거나 재배포할 수는 없습니다.

자세한 내용은 [LICENSE](LICENSE)를 참고하세요.
