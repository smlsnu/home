# 자주 묻는 질문

## push가 거부됩니다

```
remote: Permission to smlsnu/project-rain.git denied to hong.
fatal: ... The requested URL returned error: 403
```

해당 프로젝트 팀에 속하지 않은 경우입니다. 팀장 또는 Owner에게 팀 추가를 요청하세요.

## clone이 안 됩니다

```
remote: Repository not found.
```

프로젝트 저장소는 모두 **비공개**입니다. 조직 초대를 수락했는지, GitHub에 로그인된 계정이
맞는지 확인하세요.

## Pull 할 때 충돌이 났습니다

[Git 사용법 → 충돌 해결](git-guide.md#conflict) 을 참고하세요.
작업 시작 전 항상 Pull 하면 대부분 예방됩니다.

## 조직 초대가 수락되지 않습니다

- 초대 메일의 링크 대신 [github.com/orgs/smlsnu/invitation](https://github.com/orgs/smlsnu/invitation) 으로 직접 접속해 보세요.
- 그래도 안 되면 GitHub 아이디를 Owner에게 다시 확인받으세요.

## 큰 데이터 파일을 실수로 커밋했습니다

**push 하기 전이라면**

```bash
git rm --cached 파일명
git commit --amend
```

**이미 push 했다면** 직접 처리하지 말고 Owner에게 알려 주세요. 히스토리 정리가 필요합니다.

## 개인 실험용 코드는 어디에 두나요

연구실 저장소가 아니라 **개인 GitHub 계정**에 두세요.
공유할 가치가 생겼을 때 `basic-codes` 또는 해당 프로젝트 저장소로 옮기면 됩니다.

## 결과 그림은 올려도 되나요

원칙적으로 올리지 않습니다. 저장소가 무거워집니다.
문서에 꼭 필요한 그림만 `home` 저장소의 `docs/` 아래에 넣으세요.

## 남의 코드를 수정해도 되나요

`basic-codes` 는 공용이므로 개선은 환영합니다. 다만

- 기존 동작을 바꾸는 수정은 브랜치와 PR로 진행하고 작성자에게 리뷰를 요청하세요
- 단순 버그 수정이나 주석 추가는 바로 커밋해도 됩니다

## 여러 프로젝트에 참여하고 있습니다

각 저장소를 따로 clone하면 됩니다. 한 폴더 아래에 나란히 두는 것을 권합니다.

```
~/sml/
├── basic-codes/
├── project-rain/
└── project-tq/
```

## 새 프로젝트를 시작하려면

Owner에게 요청하세요. 저장소 생성 → 팀 생성 → 권한 부여 순으로 처리됩니다.

## 패키지 버전이 팀원마다 다릅니다

기준 환경 파일을 갱신하지 않고 각자 설치했기 때문입니다.
[실행 환경 → 자주 겪는 문제](environment.md) 를 참고하세요.

## 파일 이름을 어떻게 지어야 하나요

[코드 작성 규칙](conventions.md) 에 저장소별 규칙과 예시가 있습니다.

## PR을 꼭 써야 하나요

강제하지는 않습니다. 다만 아래 경우에는 PR을 권합니다.

- 여러 사람이 함께 쓰는 코드를 크게 바꿀 때
- 프로젝트 팀장의 확인을 받고 싶을 때

사용법은 [Git 사용법 → Pull Request](git-guide.md#pull-request) 를 참고하세요.
