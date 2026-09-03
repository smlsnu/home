# Git 사용법 (VS Code 기준)

Git이 처음이어도 따라 할 수 있도록 VS Code 화면 기준으로 설명합니다.

## 개념 먼저

Git은 코드의 **변경 이력을 저장하는 도구**입니다. 세 단계를 거칩니다.

```
작업 폴더  ──stage──▶  스테이지  ──commit──▶  로컬 저장소  ──push──▶  GitHub
```

- **Stage**: 이번에 기록할 파일 고르기
- **Commit**: 고른 변경을 설명과 함께 로컬에 기록 (아직 GitHub에는 없음)
- **Push**: 로컬 기록을 GitHub로 올리기
- **Pull**: GitHub의 최신 내용을 내려받기

Source Control 패널(`Ctrl+Shift+G`)에서 모두 처리할 수 있습니다.

---

## 매일 쓰는 흐름

### ① 작업 시작 전 Pull

Source Control 패널의 `···` 메뉴 → **Pull**

!!! danger "가장 중요한 습관"
    이 단계를 건너뛰면 충돌이 발생합니다. 코드를 켜자마자 Pull 하는 습관을 들이세요.

### ② 코드 수정

변경한 파일이 Source Control 패널에 자동으로 나타납니다.
파일 이름을 클릭하면 **좌: 이전 / 우: 현재** 비교 화면이 열립니다. 올리기 전에 꼭 확인하세요.

### ③ Stage

파일 옆 **`+`** 버튼. 관련 없는 변경은 빼고 올리는 것이 좋습니다.

### ④ Commit

상단 입력창에 메시지를 쓰고 `Ctrl+Enter`.

### ⑤ Sync

**Sync Changes** 버튼. pull과 push를 함께 수행합니다.

---

## 커밋 메시지 쓰는 법

첫 줄은 50자 내외 한 줄 요약. 필요하면 빈 줄 뒤에 상세 설명.

```
Add rainfall anomaly plotting for 2020-2024

- 5년 이동평균 기반 anomaly 계산 추가
- 컬러바 범위를 ±10 mm 로 고정
```

권장 접두어: `Add` `Fix` `Update` `Remove` `Refactor` `Docs`

!!! tip
    "수정", "ㅇㅇ", "test" 같은 메시지는 나중에 본인이 가장 곤란해집니다.

---

## 브랜치

작은 수정은 `main`에 바로 커밋해도 됩니다.
며칠 걸리는 작업이나 남의 코드에 영향을 주는 변경은 브랜치를 만드세요.

- 좌하단 상태바의 브랜치 이름 클릭 → **Create new branch**
- 이름 규칙: `feature/이름-작업내용` (예: `feature/kimsj-rain-anomaly`)

```bash
git switch -c feature/kimsj-rain-anomaly
# ... 작업, commit ...
git push -u origin feature/kimsj-rain-anomaly
```

---

## Pull Request

**PR(Pull Request)** 은 "내 변경사항을 `main`에 반영해 달라"는 요청서입니다.
바로 반영하지 않고 다른 사람의 확인을 거치고 싶을 때 씁니다.

```
① 브랜치 생성          내 작업 공간을 따로 만듦
② 작업 후 commit·push   브랜치에만 올라감. main은 아직 그대로
③ PR 생성              "이 브랜치를 main에 합쳐 주세요" 요청
④ 리뷰                 다른 사람이 변경 내용을 보고 승인 또는 수정 요청
⑤ Merge                승인되면 main에 반영됨
```

**만드는 방법**

브랜치를 push하면 GitHub 저장소 페이지 상단에 **Compare & pull request** 버튼이 뜹니다.
누르고 제목과 설명을 쓴 뒤 **Create pull request** 를 누르면 끝입니다.
우측 **Reviewers** 에서 확인받을 사람을 지정할 수 있습니다.

VS Code에서는 **GitHub Pull Requests and Issues** 확장을 설치하면
좌측 패널에서 PR 생성·리뷰·병합을 모두 처리할 수 있습니다.

**리뷰하는 방법**

1. PR 페이지의 **Files changed** 탭에서 변경 내용을 봅니다.
2. 특정 줄에 마우스를 올리면 나타나는 `+` 로 그 줄에 댓글을 답니다.
3. **Review changes** → `Approve`(승인) 또는 `Request changes`(수정 요청) 선택.
4. 승인 후 **Merge pull request** 를 누르면 반영됩니다.

**언제 쓰나요**

강제되지는 않습니다. 다만 아래 경우에는 PR을 권합니다.

- 여러 사람이 함께 쓰는 코드를 크게 바꿀 때
- 프로젝트 팀장의 확인을 받고 싶을 때
- 작업 내용을 기록으로 남기고 싶을 때

혼자 쓰는 코드의 사소한 수정까지 PR로 올릴 필요는 없습니다.

## 충돌(conflict) 해결

같은 줄을 두 사람이 고치면 충돌이 납니다. 흔한 일이니 당황하지 마세요.

1. 충돌 파일이 Source Control의 **Merge Changes** 에 표시됩니다.
2. 파일을 열면 코드 위에 버튼이 나타납니다.
    - `Accept Current Change` — 내 변경 유지
    - `Accept Incoming Change` — 상대 변경 채택
    - `Accept Both Changes` — 둘 다 남기기
3. **Resolve in Merge Editor** 를 쓰면 3분할 화면으로 더 안전하게 비교할 수 있습니다.
4. 정리 후 Stage → Commit → Sync.

---

## 실수했을 때

| 상황 | 방법 |
|------|------|
| 커밋 전 변경을 되돌리고 싶다 | 파일 옆 **`↩` (Discard Changes)** |
| 방금 쓴 커밋 메시지를 고치고 싶다 | `···` → Commit → **Commit Staged (Amend)**. **push 전에만** |
| 실수로 파일을 지웠다 | `git log -- 경로` 로 찾아 `git checkout <커밋> -- 경로` |
| 뭘 해야 할지 모르겠다 | 아무것도 하지 말고 Owner에게 문의 |

!!! danger "`git push --force` 금지"
    남의 작업을 되돌릴 수 없게 지울 수 있습니다. 필요해 보이면 반드시 Owner에게 먼저 문의하세요.

---

## 유용한 확장

| 확장 | 용도 |
|------|------|
| GitHub Pull Requests and Issues | PR·이슈를 VS Code 안에서 처리 |
| GitLens | 각 줄을 누가 언제 썼는지 표시 |
| Git Graph | 브랜치 히스토리를 그래프로 확인 |

---

## 터미널 명령어 대조표

| 하려는 일 | 명령어 |
|-----------|--------|
| 최신 내용 받기 | `git pull` |
| 상태 확인 | `git status` |
| 변경 내용 보기 | `git diff` |
| 파일 stage | `git add 파일명` (전체: `git add .`) |
| 커밋 | `git commit -m "메시지"` |
| 업로드 | `git push` |
| 브랜치 만들고 이동 | `git switch -c 브랜치명` |
| 브랜치 이동 | `git switch 브랜치명` |
| 이력 보기 | `git log --oneline --graph` |
