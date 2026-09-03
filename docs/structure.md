# 저장소 구성

연구실 코드는 **용도별로 저장소를 나누어** 관리합니다.
GitHub은 폴더 단위가 아니라 저장소 단위로 권한을 부여하기 때문에, 저장소를 나누는 것이
프로젝트별 접근 통제를 구현하는 방법입니다.

```
github.com/smlsnu/
├── home             안내 문서 (이 사이트)
├── basic-codes      공용 코드
├── project-rain     프로젝트별 코드
├── project-tq
├── project-rt
├── project-polar
└── project-env
```

## home

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

파일은 저장소 최상위에 평평하게 두고, **이름 앞의 분류 접두어**(`io_`, `plot_`, `calc_`, `util_`, `tut_`)로 구분합니다.
코드가 충분히 쌓이면 그때 폴더로 묶습니다.

## project-*

프로젝트별 분석 코드를 담습니다. 각 저장소는 같은 이름의 팀만 수정할 수 있습니다.

| 저장소 | 팀 |
|--------|-----|
| `project-rain` | `project-rain` |
| `project-tq` | `project-tq` |
| `project-rt` | `project-rt` |
| `project-polar` | `project-polar` |
| `project-env` | `project-env` |

### 폴더 구성

모든 프로젝트 저장소는 같은 구조를 씁니다.

```
project-rain/
├── code/            분석 스크립트·노트북
├── result/          팀원끼리 공유하는 결과 그림
├── README.md        목적·자료·실행 순서·담당자
├── environment.yml  conda 환경 (또는 requirements.txt)
└── .gitignore
```

`code/` 에는 실행 순서를 알 수 있도록 번호를 붙이는 것을 권합니다.
예: `001_download.py`, `002_preprocess.py`, `003_plot.py`

`result/` 에는 **그림만** 커밋할 수 있습니다.

| 확장자 | 허용 |
|--------|------|
| `.png` `.jpg` `.gif` `.svg` `.pdf` | 허용됨 |
| `.pkl` `.h5` `.nc` `.npy` 등 데이터 | 차단됨 |

!!! warning "용량 주의"
    한 파일 100 MB 초과는 GitHub이 거부합니다. 저장소 전체도 1 GB 이내를 권장합니다.
    같은 그림을 다시 그렸다면 새 파일을 추가하지 말고 **덮어쓰세요.** 이전 버전은 Git 이력에 남습니다.

### README에 반드시 포함할 것

- 프로젝트 목적, 대상 영역, 기간
- 담당자와 참여자
- 사용 자료의 종류·기간·획득 방법
- 스크립트 실행 순서

### 새 프로젝트 추가

조직 Owner에게 요청하세요. 아래 순서로 처리됩니다.

1. `smlsnu/project-<이름>` 저장소 생성
2. `project-<이름>` 팀 생성 → 해당 저장소에 Write
3. `lab-members` 팀 → 해당 저장소에 Read
4. 이 사이트의 저장소 목록에 추가

---

## 코드 작성 규칙

파일 이름 규칙, 머리말 양식, README 표 갱신 방법은 [코드 작성 규칙](conventions.md) 에 정리했습니다.
실행 환경 구성은 [실행 환경](environment.md) 을 참고하세요.

## 그 밖의 권장 사항

파일 상단에 **무엇을 하는 코드인지, 어떤 입력이 필요한지** 주석으로 명시하세요.

절대 경로는 파일 상단에 변수로 모아 두면 다른 사람이 쉽게 바꿀 수 있습니다.

```python
# 경로 설정 — 환경에 맞게 수정
DATA_DIR = '/home/username/data/ssmi'
OUT_DIR  = '/home/username/result'
```

데이터 파일은 함께 올리지 않고, 어디서 받는 자료인지 주석으로 설명하세요.
