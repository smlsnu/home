# 저장소 구성

연구실 코드는 **용도별로 저장소를 나누어** 관리합니다.
GitHub은 폴더 단위가 아니라 저장소 단위로 권한을 부여하기 때문에, 저장소를 나누는 것이
프로젝트별 접근 통제를 구현하는 방법입니다.

```
github.com/smlsnu/
├── docs             안내 문서 (이 사이트)
├── basic-codes      공용 코드
├── project-rain     강수
├── project-tq       온습도
├── project-rt       복사전달
├── project-polar    극지
└── project-env      환경
```

## docs

연구실 GitHub 사용 규칙과 안내를 담습니다. 코드는 넣지 않습니다.
`docs/` 안의 마크다운을 고쳐 push하면 몇 분 안에 이 사이트에 반영됩니다.

**유일하게 공개(public)된 저장소**이므로 코드·데이터·API 키를 올리지 마세요.

## basic-codes

연구실 구성원이 공통으로 쓰는 코드를 모읍니다. `lab-members` 팀이면 누구나 추가·수정할 수 있습니다.

**올리는 것**

- 자주 쓰는 유틸리티 (파일 입출력, 좌표 변환, 날짜 처리)
- 위성·재분석 자료 읽기 예제
- 지도·시계열 등 표준 시각화 템플릿
- 신입 연구원용 입문 노트북

**권장 구조**

```
basic-codes/
├── io/          자료 읽기·쓰기
├── plotting/    시각화 템플릿
├── utils/       좌표·시간·통계 유틸
└── tutorials/   입문 노트북
```

## project-*

프로젝트별 분석 코드를 담습니다. 각 저장소는 같은 이름의 팀만 수정할 수 있습니다.

| 저장소 | 팀 |
|--------|-----|
| `project-rain` | `project-rain` |
| `project-tq` | `project-tq` |
| `project-rt` | `project-rt` |
| `project-polar` | `project-polar` |
| `project-env` | `project-env` |

각 저장소에는 다음을 반드시 포함하세요.

- `README.md` — 목적, 사용 자료, 실행 순서, 담당자
- 실행 순서를 알 수 있는 번호 체계 또는 설명
- 필요한 외부 데이터의 위치와 획득 방법

### 새 프로젝트 추가

조직 Owner에게 요청하세요. 아래 순서로 처리됩니다.

1. `smlsnu/project-<이름>` 저장소 생성
2. `project-<이름>` 팀 생성 → 해당 저장소에 Write
3. `lab-members` 팀 → 해당 저장소에 Read
4. 이 사이트의 저장소 목록에 추가

---

## 코드 작성 권장 사항

파일 상단에 **무엇을 하는 코드인지, 어떤 입력이 필요한지** 주석으로 명시하세요.

절대 경로는 파일 상단에 변수로 모아 두면 다른 사람이 쉽게 바꿀 수 있습니다.

```python
# 경로 설정 — 환경에 맞게 수정
DATA_DIR = '/home/username/data/ssmi'
OUT_DIR  = '/home/username/result'
```

데이터 파일은 함께 올리지 않고, 어디서 받는 자료인지 주석으로 설명하세요.
