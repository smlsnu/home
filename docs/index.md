# SML SNU

서울대학교 **위성기상실험실(Satellite Meteorology Laboratory, SML)** GitHub 안내 사이트입니다.

연구실 구성원이 코드를 공유하고 프로젝트 진행 방식을 아카이빙하기 위한 규칙과 사용법을 정리해 둔 곳입니다.

[:material-github: 조직 페이지](https://github.com/smlsnu){ .md-button .md-button--primary }

---

## 빠르게 시작하기

- **처음이신가요?** → [시작하기](getting-started.md)
- **Git이 익숙하지 않다면** → [Git 사용법](git-guide.md)
- **어디에 코드를 올리나요?** → [저장소 구성](structure.md)
- **push가 거부되나요?** → [권한과 규칙](permissions.md) · [FAQ](faq.md)

---

## 저장소 목록

| 저장소 | 공개 | 내용 | 수정 가능 |
|--------|------|------|-----------|
| `docs` | public | 안내 문서 (이 사이트의 소스) | `lab-members` |
| `basic-codes` | private | 공용 유틸리티·시각화 템플릿·입문 예제 | `lab-members` |
| `project-rain` | private | 강수 프로젝트 | `project-rain` |
| `project-tq` | private | 온습도 프로젝트 | `project-tq` |
| `project-rt` | private | 복사전달 프로젝트 | `project-rt` |
| `project-polar` | private | 극지 프로젝트 | `project-polar` |
| `project-env` | private | 환경 프로젝트 | `project-env` |

프로젝트 저장소는 **해당 팀만 수정할 수 있습니다.** 연구실 구성원은 모든 저장소를 읽을 수 있습니다.

!!! warning "`docs` 저장소만 공개입니다"
    코드 저장소는 모두 비공개이지만, 이 안내 저장소는 사이트 발행을 위해 공개되어 있습니다.
    이 저장소에는 코드·데이터·API 키를 올리지 마세요.
