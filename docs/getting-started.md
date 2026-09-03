# 시작하기

## 1. 조직 가입

`smlsnu` 조직 초대 메일을 수락합니다. 초대가 오지 않았다면 Owner에게 GitHub 아이디를 알려주세요.

가입 후 소속되는 팀은 다음과 같습니다.

| 팀 | 대상 | 권한 |
|----|------|------|
| `lab-members` | 연구실 구성원 전원 | `basic-codes`, `docs` 수정. 모든 프로젝트 저장소 읽기 |
| `project-<이름>` | 해당 프로젝트 참여자 | 그 프로젝트 저장소 수정 |

## 2. 도구 설치

### Git

=== "Windows"
    [git-scm.com](https://git-scm.com/download/win) 에서 설치합니다. 설치 옵션은 기본값 그대로 두면 됩니다.

=== "macOS"
    ```bash
    brew install git
    ```
    또는 터미널에서 `git --version` 실행 시 자동 설치 안내가 뜹니다.

=== "Linux"
    ```bash
    sudo apt install git      # Debian/Ubuntu
    sudo dnf install git      # Fedora/RHEL
    ```

### VS Code

[code.visualstudio.com](https://code.visualstudio.com/) 에서 설치한 뒤,
확장 **GitHub Pull Requests and Issues** 를 추가로 설치합니다.

좌하단 계정 아이콘 → **Sign in with GitHub** 으로 로그인해 두면 이후 인증 절차가 필요 없습니다.

## 3. 커밋 작성자 설정

터미널에서 한 번만 실행합니다. 이 정보가 커밋 기록에 남습니다.

```bash
git config --global user.name "홍길동"
git config --global user.email "your_id@snu.ac.kr"
```

## 4. 저장소 내려받기

저장소를 한 폴더 아래에 모아 두는 것을 권합니다.

```bash
mkdir ~/sml && cd ~/sml
git clone https://github.com/smlsnu/basic-codes.git
git clone https://github.com/smlsnu/project-rain.git    # 참여하는 프로젝트만
```

VS Code에서 하려면 `Ctrl+Shift+P` → **Git: Clone** → 저장소 주소 입력 → 저장할 폴더 선택.

!!! note "저장소가 보이지 않는다면"
    프로젝트 저장소는 비공개입니다. 조직 초대를 수락했고 해당 계정으로 로그인되어 있어야 합니다.

## 5. 실행 환경 만들기

각 저장소에 `environment.yml` 이 있습니다. conda 환경을 한 번 만들어 두면 모든 저장소에서 씁니다.

```bash
cd ~/sml/basic-codes
conda env create -f environment.yml
conda activate sml
```

Miniforge/Anaconda가 없다면 [Miniforge](https://github.com/conda-forge/miniforge) 설치를 권합니다.

## 다음 단계

[Git 사용법](git-guide.md) 으로 이동해 실제 작업 흐름을 익히세요.
