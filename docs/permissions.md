# 권한과 규칙

## 두 개의 권한 층

```
조직 역할   →  smlsnu 조직에 무엇을 할 수 있나   (Owner / Member)
저장소 권한 →  각 저장소에 무엇을 할 수 있나     (Read / Write)
```

## 조직 역할

| 역할 | 권한 |
|------|------|
| **Owner** | 조직 전체 관리. 저장소·팀 생성, 권한 부여, 멤버 초대 |
| **Member** | 팀 소속에 따른 저장소 접근. 조직 설정은 변경 불가 |

## 팀과 저장소 권한

| 팀 | Write | Read |
|----|-------|------|
| `lab-members` | `docs`, `basic-codes` | 모든 프로젝트 저장소 |
| `project-rain` | `project-rain` | 〃 |
| `project-tq` | `project-tq` | 〃 |
| `project-rt` | `project-rt` | 〃 |
| `project-polar` | `project-polar` | 〃 |
| `project-env` | `project-env` | 〃 |

**Read** 는 조회와 clone만 가능합니다.
**Write** 는 push, 브랜치 생성, PR 병합이 가능하며, 저장소 설정 변경과 삭제는 불가능합니다.

## 권한이 없으면 어떻게 되나요

해당 팀에 속하지 않은 상태로 push하면 GitHub 서버가 거부합니다.

```
remote: Permission to smlsnu/project-rain.git denied to hong.
fatal: unable to access 'https://github.com/smlsnu/project-rain.git/':
       The requested URL returned error: 403
```

정상 동작입니다. 프로젝트에 참여하려면 해당 팀장 또는 Owner에게 요청하세요.

## 팀원 추가·제거

각 프로젝트 팀에는 **팀장(maintainer)** 을 둘 수 있습니다.
팀장은 자기 팀에 사람을 추가하거나 제거할 수 있으며, 그 결과 해당 저장소의 Write 권한이 함께 부여·회수됩니다.

저장소 자체의 권한 설정 변경과 새 저장소 생성은 Owner만 할 수 있습니다.

## 삭제에 대하여

!!! note "파일 삭제를 완전히 막을 수는 없습니다"
    Git에서 수정과 삭제는 같은 종류의 기록(커밋)입니다. 따라서 "수정은 되고 삭제만 금지"는
    구조적으로 불가능합니다.

    대신 **모든 삭제가 이력에 남고 언제든 복구 가능**하며, 누가 언제 지웠는지 추적됩니다.
    또한 clone한 모든 사람의 컴퓨터에 사본이 있으므로 실질적인 코드 손실은 일어나지 않습니다.

저장소 자체의 삭제는 Owner만 할 수 있도록 조직 설정에서 제한해 두었습니다.

---

## 절대 하지 말아야 할 것

- ❌ 데이터 파일 커밋 (`.pkl`, `.h5`, `.nc`, `.gz`, `.hdf`, `.he4`) — 저장소가 무거워져 못 쓰게 됩니다
- ❌ API 키·비밀번호·개인정보 하드코딩
- ❌ `git push --force` — 남의 작업을 지울 수 있습니다
- ❌ 참여하지 않는 프로젝트 저장소에 임의 접근 시도

!!! danger "키를 실수로 올렸다면"
    즉시 해당 키를 폐기(revoke)하고 Owner에게 알려 주세요.
    커밋을 되돌려도 히스토리에는 남기 때문에, 키 폐기가 유일하게 확실한 조치입니다.
