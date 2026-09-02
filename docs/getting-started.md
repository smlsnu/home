# 시작하기

## 1. 조직 가입

`smlsnu` 조직 초대 메일을 수락합니다. 초대가 오지 않았다면 Owner에게 GitHub 아이디를 알려주세요.

가입 후 소속되는 팀은 다음과 같습니다.

| 팀 | 대상 | 권한 |
|----|------|------|
| `lab-members` | 연구실 구성원 전원 | `basic_codes/`, `docs/` 수정 |
| `project-tpw` | TPW 프로젝트 참여자 | 추가로 `project_codes/tpw/` 수정 |

## 2. 도구 설치

### Git

=== "Windows"
    [git-scm.com](https://git-scm.com/download/win) 에서 설치. 설치 옵션은 기본값 그대로 두면 됩니다.

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

[code.visualstudio.com](https://code.visualstudio.com/) 에서 설치 후, 확장 **GitHub Pull Requests and Issues** 를 추가로 설치합니다.

좌하단 계정 아이콘 → **Sign in with GitHub** 으로 로그인해 두면 이후 인증 절차가 필요 없습니다.

## 3. 커밋 작성자 설정

터미널에서 한 번만 실행합니다. 이 정보가 커밋 기록에 남습니다.

```bash
git config --global user.name "홍길동"
git config --global user.email "your_id@snu.ac.kr"
```

## 4. 저장소 내려받기

=== "VS Code"
    `Ctrl+Shift+P` → **Git: Clone** → 아래 주소 입력 → 저장할 폴더 선택

    ```
    https://github.com/smlsnu/SML_SNU.git
    ```

=== "터미널"
    ```bash
    git clone https://github.com/smlsnu/SML_SNU.git
    cd SML_SNU
    ```

## 5. 실행 환경 만들기

```bash
conda env create -f environment.yml
conda activate sml
```

Miniforge/Anaconda가 없다면 [Miniforge](https://github.com/conda-forge/miniforge) 설치를 권장합니다.

## 다음 단계

[Git 사용법](git-guide.md) 으로 이동해 실제 작업 흐름을 익히세요.
