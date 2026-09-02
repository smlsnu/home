# SML_SNU

서울대학교 **위성기상실험실(Satellite Meteorology Laboratory, SML)** 공용 코드 저장소입니다.
연구실 구성원이 코드를 공유하고 프로젝트 진행 방식을 아카이빙하는 공간이며,
SML의 발전과 연구 능력 향상을 위해 여러분의 적극적인 참여를 부탁드립니다.

This is the shared code repository of the Satellite Meteorology Laboratory (SML),
Seoul National University, Korea.

📖 **문서 사이트: https://smlsnu.github.io/SML_SNU/**

---

## 저장소 구성

| 폴더 | 내용 | 수정 권한 |
|------|------|-----------|
| [`basic_codes/`](basic_codes/) | 공용 유틸리티, 입문용 예제, 자주 쓰는 분석·시각화 스니펫 | `lab-members` 팀 |
| [`project_codes/`](project_codes/) | 프로젝트별 분석 코드. 프로젝트마다 하위 폴더 하나 | 각 프로젝트 팀 |
| [`docs/`](docs/) | 문서 사이트 소스 (MkDocs) | `lab-members` 팀 |

`project_codes/` 하위는 **해당 프로젝트 팀만 수정·삭제할 수 있도록 저장소 규칙(ruleset)으로 보호**되어 있습니다.
팀에 속하지 않은 상태로 push하면 GitHub이 거부합니다.

## 처음 오셨다면

1. 조직(`smlsnu`) 초대를 수락합니다.
2. 저장소를 clone 합니다.
   ```bash
   git clone https://github.com/smlsnu/SML_SNU.git
   ```
3. [CONTRIBUTING.md](CONTRIBUTING.md) 를 읽고 작업 규칙과 VS Code 사용법을 확인합니다.

## 실행 환경

```bash
conda env create -f environment.yml
conda activate sml
```

## 중요 규칙

- **데이터 파일은 절대 커밋하지 않습니다** (`.pkl`, `.h5`, `.nc`, `.gz`, `.hdf` 등). `.gitignore`에 등록되어 있습니다.
- 개인 정보, API 키, 비밀번호를 코드에 하드코딩하지 않습니다. 이 저장소는 **공개(public)** 입니다.
- 결과 그림(PNG/GIF)은 원칙적으로 커밋하지 않습니다. 문서에 필요한 경우만 `docs/` 아래에 넣습니다.

## 문의

- 저장소 권한·팀 관련: 조직 Owner에게 문의
- 코드 관련: GitHub Issues 사용
