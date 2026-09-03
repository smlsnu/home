# 실행 환경

프로젝트마다 필요한 패키지가 다르고, 구성원마다 conda와 pip 중 쓰는 도구도 다릅니다.
그래서 연구실 전체에 하나의 환경을 강요하지 않고, **저장소마다 환경을 따로 정의**합니다.

## 세 가지 원칙

**① 환경은 저장소마다 하나입니다.**

여러 프로젝트의 패키지를 한 환경에 몰아넣으면 버전 충돌이 납니다.
이름은 `sml-<저장소>` 형식을 씁니다.

| 저장소 | 환경 이름 |
|--------|-----------|
| `basic-codes` | `sml-basic` |
| `project-rain` | `sml-rain` |
| `project-tq` | `sml-tq` |

**② 저장소마다 기준 도구를 하나 정합니다.**

conda와 pip 중 무엇을 기준으로 삼을지 팀에서 정하고 README에 적습니다.
두 파일을 모두 두어도 되지만, **갱신 의무는 기준 파일에만** 있습니다.

| 기준 | 정의 파일 |
|------|-----------|
| conda | `environment.yml` |
| pip | `requirements.txt` |

**③ 패키지를 설치했으면 파일을 갱신해 커밋합니다.**

"제 컴퓨터에서는 되는데요"의 원인은 대부분 이 단계를 빠뜨린 것입니다.

---

## conda 를 쓸 때

### 환경 만들기

```bash
conda env create -f environment.yml
conda activate sml-rain
```

### 패키지 추가

```bash
conda install -c conda-forge cartopy
conda env export --from-history > environment.yml
git add environment.yml && git commit -m "Add cartopy"
```

!!! tip "`--from-history` 를 꼭 붙이세요"
    옵션 없이 내보내면 의존 패키지 수백 개와 운영체제별 빌드 번호까지 전부 기록되어,
    다른 컴퓨터에서 설치가 실패합니다.
    `--from-history` 는 **직접 설치한 패키지만** 남깁니다.

### Miniforge 설치

conda가 없다면 [Miniforge](https://github.com/conda-forge/miniforge) 를 권합니다.
`conda-forge` 채널이 기본으로 잡혀 있어 별도 설정이 필요 없습니다.

---

## pip 를 쓸 때

### 환경 만들기

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 패키지 추가

```bash
pip install xarray
pip freeze > requirements.txt
git add requirements.txt && git commit -m "Add xarray"
```

!!! warning "`.venv/` 는 커밋하지 않습니다"
    가상환경 폴더 자체는 수백 MB이며 `.gitignore` 로 막혀 있습니다.
    공유하는 것은 **패키지 목록**이지 설치된 파일이 아닙니다.

---

## 어느 쪽을 골라야 하나요

| 상황 | 권장 |
|------|------|
| `cartopy`, `pyhdf`, `netCDF4`, `gdal` 등을 씀 | **conda** |
| 순수 파이썬 패키지만 씀 | pip 로 충분함 |
| 서버에 conda가 이미 깔려 있음 | conda |
| 가볍게 시작하고 싶음 | pip |

위성·기상 자료를 다루는 패키지는 C 라이브러리에 의존하는 경우가 많아,
pip로 설치하면 컴파일 오류가 자주 납니다. 이때는 conda-forge가 훨씬 편합니다.

---

## Jupyter 에서 환경 쓰기

만든 환경을 노트북 커널로 등록해야 선택할 수 있습니다.

```bash
conda activate sml-rain          # 또는 source .venv/bin/activate
python -m ipykernel install --user --name sml-rain --display-name "Python (sml-rain)"
```

VS Code에서는 노트북 우상단의 커널 선택 버튼에서 고르면 됩니다.

---

## 자주 겪는 문제

??? question "`conda env create` 가 끝나지 않습니다"
    의존성 해결에 시간이 오래 걸리는 경우입니다. `mamba` 를 쓰면 훨씬 빠릅니다.
    ```bash
    conda install -n base -c conda-forge mamba
    mamba env create -f environment.yml
    ```

??? question "`environment.yml` 로 만든 환경이 다른 컴퓨터에서 실패합니다"
    `--from-history` 없이 내보낸 파일일 가능성이 큽니다.
    빌드 번호(`=py312h1234567_0`)가 붙어 있다면 다시 내보내세요.

??? question "패키지를 설치했는데 import 가 안 됩니다"
    환경을 활성화하지 않았거나, Jupyter가 다른 커널을 쓰고 있는 경우입니다.
    ```python
    import sys; print(sys.executable)
    ```
    출력 경로가 의도한 환경 안에 있는지 확인하세요.

??? question "팀원마다 패키지 버전이 다릅니다"
    기준 파일을 갱신하지 않고 각자 설치했기 때문입니다.
    한 사람이 정상 동작하는 환경에서 파일을 다시 내보내 커밋하고, 나머지는 환경을 새로 만드세요.
    ```bash
    conda env remove -n sml-rain
    conda env create -f environment.yml
    ```
