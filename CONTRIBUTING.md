# 기여 가이드

SML_SNU 저장소에 코드를 올리는 방법과 규칙입니다. Git이 처음이어도 따라 할 수 있게 작성했습니다.

---

## 1. 준비 (최초 1회)

### 1-1. 조직 초대 수락
`smlsnu` 조직 초대 메일을 수락합니다.

### 1-2. VS Code 준비
- 좌측 사이드바의 **Source Control** 아이콘 (`Ctrl+Shift+G`)이 Git 작업 공간입니다.
- 확장 **GitHub Pull Requests and Issues** 설치를 권장합니다.
- 좌하단 계정 아이콘 → **Sign in with GitHub** 으로 로그인하면 토큰 입력 없이 push 할 수 있습니다.

### 1-3. 커밋 작성자 설정
```bash
git config --global user.name "홍길동"
git config --global user.email "your_id@snu.ac.kr"
```

### 1-4. 저장소 clone
`Ctrl+Shift+P` → **Git: Clone** → 아래 주소 붙여넣기 → 저장 폴더 선택

```
https://github.com/smlsnu/SML_SNU.git
```

터미널로 하려면:
```bash
git clone https://github.com/smlsnu/SML_SNU.git
cd SML_SNU
```

---

## 2. 매일 쓰는 작업 흐름

### ① 작업 시작 전 반드시 Pull
Source Control 패널의 `···` 메뉴 → **Pull**
(생략하면 충돌이 발생합니다. 습관을 들여 주세요.)

### ② 코드 수정
변경한 파일이 Source Control 패널에 자동으로 나타납니다.
파일 이름을 클릭하면 좌우 비교 화면으로 무엇이 바뀌었는지 확인할 수 있습니다.

### ③ Stage
커밋에 포함할 파일 옆의 **`+`** 버튼을 누릅니다.
관련 없는 변경은 빼고 올리는 것이 좋습니다.

### ④ Commit
상단 입력창에 메시지를 쓰고 `Ctrl+Enter` (또는 **Commit** 버튼).

### ⑤ Sync
**Sync Changes** 버튼을 누릅니다. pull과 push를 함께 수행합니다.

---

## 3. 커밋 메시지 규칙

첫 줄은 50자 내외의 한 줄 요약, 필요하면 빈 줄 뒤에 상세 설명을 씁니다.

```
Add TPW anomaly plotting for 2020-2024

- 5년 이동평균 기반 anomaly 계산 추가
- 컬러바 범위를 ±10 mm 로 고정
```

권장 접두어: `Add` / `Fix` / `Update` / `Remove` / `Refactor` / `Docs`

---

## 4. 브랜치

작은 수정은 `main`에 바로 커밋해도 됩니다.
여러 날 걸리는 작업이나 다른 사람 코드에 영향을 주는 변경은 브랜치를 만드세요.

- 좌하단 상태바의 브랜치 이름 클릭 → **Create new branch**
- 이름 규칙: `feature/이름-작업내용` (예: `feature/kimsj-tpw-anomaly`)
- 작업이 끝나면 GitHub 웹에서 **Compare & pull request** → main으로 병합

```bash
git switch -c feature/kimsj-tpw-anomaly
# ... 작업 ...
git push -u origin feature/kimsj-tpw-anomaly
```

---

## 5. 충돌(conflict) 해결

Pull 할 때 같은 줄을 두 사람이 고쳤으면 충돌이 납니다. 드문 일이 아니니 당황하지 마세요.

1. 충돌 파일이 Source Control의 **Merge Changes** 에 표시됩니다.
2. 파일을 열면 코드 위에 `Accept Current Change` / `Accept Incoming Change` / `Accept Both Changes` 버튼이 나타납니다.
3. **Resolve in Merge Editor** 버튼을 쓰면 3분할 화면으로 더 안전하게 비교할 수 있습니다.
4. 정리한 뒤 Stage → Commit → Sync.

---

## 6. 실수했을 때

| 상황 | 방법 |
|------|------|
| 커밋 전 변경을 되돌리고 싶다 | 파일 옆 **`↩` (Discard Changes)** |
| 방금 쓴 커밋 메시지를 고치고 싶다 | `···` → Commit → **Commit Staged (Amend)** — **push 전에만** |
| 실수로 파일을 지웠다 | 히스토리에 남아 있습니다. `git log -- 파일경로` 로 찾아 `git checkout <커밋> -- 파일경로` |
| 뭘 해야 할지 모르겠다 | 아무것도 하지 말고 Owner에게 문의. 강제 push(`--force`)는 절대 하지 마세요. |

---

## 7. 폴더별 권한

| 폴더 | 수정 가능한 사람 |
|------|-----------------|
| `basic_codes/`, `docs/` | `lab-members` 팀 전원 |
| `project_codes/tpw/` | `project-tpw` 팀 |

`project_codes/` 하위를 수정할 권한이 없는 상태로 push하면 아래와 같은 에러가 납니다. 정상 동작이며, 필요하면 Owner에게 팀 추가를 요청하세요.

```
remote: error: GH013: Repository rule violations found
remote: - Cannot update this protected file path
```

`main` 브랜치는 강제 push와 브랜치 삭제가 차단되어 있습니다.

---

## 8. 절대 하지 말아야 할 것

- ❌ 데이터 파일 커밋 (`.pkl`, `.h5`, `.nc`, `.gz`, `.hdf`, `.he4`) — 저장소가 망가집니다
- ❌ API 키·비밀번호·개인정보 하드코딩 — **이 저장소는 공개(public)입니다**
- ❌ `git push --force`
- ❌ 남의 프로젝트 폴더 임의 수정

키를 실수로 올렸다면 즉시 해당 키를 폐기(revoke)하고 Owner에게 알려 주세요. 커밋을 지워도 히스토리에는 남습니다.
