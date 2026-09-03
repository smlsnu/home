# 시작하기

처음 오셨다면 아래 다섯 단계를 순서대로 따라오면 됩니다.

## 1. 조직 가입

1. `smlsnu` 조직 초대 메일을 수락합니다.
2. 초대가 오지 않았다면 Owner에게 GitHub 아이디를 알려주세요.

가입 후 소속되는 팀은 다음과 같습니다.

| 팀 | 대상 | 권한 |
|----|------|------|
| `lab-members` | 연구실 구성원 전원 | `basic-codes` · `home` 수정, 모든 팀 저장소 읽기 |
| `team-<이름>` | 해당 팀 구성원 | 그 팀 저장소 수정 |

## 2. 도구 설치

### Git

=== "Windows"
    [git-scm.com](https://git-scm.com/download/win) 에서 설치합니다. 설치 옵션은 기본값 그대로 두면 됩니다.

=== "macOS"
    ```bash
    brew install git
    ```
    또는 터미널에서 `git --version` 을 실행하면 자동 설치 안내가 뜹니다.

=== "Linux"
    ```bash
    sudo apt install git      # Debian/Ubuntu
    sudo dnf install git      # Fedora/RHEL
    ```

### VS Code

1. [code.visualstudio.com](https://code.visualstudio.com/) 에서 설치합니다.
2. 확장 **GitHub Pull Requests and Issues** 를 추가로 설치합니다.
3. 좌하단 계정 아이콘 → **Sign in with GitHub** 으로 로그인합니다.

로그인해 두면 이후 인증 절차가 필요 없습니다.

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
git clone https://github.com/smlsnu/team-rain.git    # 소속된 팀만
```

VS Code에서 하려면 `Ctrl+Shift+P` → **Git: Clone** → 저장소 주소 입력 → 저장할 폴더 선택.

!!! note "저장소가 보이지 않는다면"
    팀 저장소는 비공개입니다. 아래를 확인하세요.

    - 조직 초대를 수락했는가
    - 해당 계정으로 GitHub에 로그인되어 있는가
    - 그 팀에 소속되어 있는가

## 5. 실행 환경 만들기

**환경은 저장소마다 따로 만듭니다.** 팀별로 필요한 패키지가 다르기 때문입니다.
각 저장소 README에 기준 도구(conda 또는 pip)가 적혀 있습니다.

=== "conda"
    ```bash
    cd ~/sml/team-rain
    conda env create -f environment.yml
    conda activate sml-rain
    ```

=== "pip"
    ```bash
    cd ~/sml/team-rain
    python -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    ```

자세한 규칙과 문제 해결은 [실행 환경](environment.md) 을 참고하세요.

## 다음 단계

- [Git 사용법](git-guide.md) — 실제 작업 흐름을 익힙니다.
- [코드 작성 규칙](conventions.md) — 파일 이름 규칙과 머리말 양식을 확인합니다.
