# 자주 묻는 질문

## push가 거부됩니다

```
remote: error: GH013: Repository rule violations found
remote: - Cannot update this protected file path
```

`project_codes/` 하위를 수정했는데 해당 프로젝트 팀에 속하지 않은 경우입니다.
Owner에게 팀 추가를 요청하거나, 수정 대상이 맞는지 확인하세요.

## Pull 할 때 충돌이 났습니다

[Git 사용법 → 충돌 해결](git-guide.md#충돌conflict-해결) 을 참고하세요.
작업 시작 전 항상 Pull 하면 대부분 예방됩니다.

## 조직 초대가 수락되지 않습니다

- 초대 메일의 링크가 아니라 [github.com/orgs/smlsnu/invitation](https://github.com/orgs/smlsnu/invitation) 으로 직접 접속해 보세요.
- 그래도 안 되면 GitHub 아이디를 Owner에게 다시 확인받으세요.

## 큰 데이터 파일을 실수로 커밋했습니다

**push 하기 전이라면**

```bash
git rm --cached 파일명
git commit --amend
```

**이미 push 했다면** 직접 처리하지 말고 Owner에게 알려 주세요. 히스토리 정리가 필요합니다.

## 개인 실험용 코드는 어디에 두나요

이 저장소가 아니라 **개인 GitHub 계정**에 두세요.
공유할 가치가 생겼을 때 `basic_codes/` 또는 해당 프로젝트 폴더로 옮기면 됩니다.

## 결과 그림은 올려도 되나요

원칙적으로 올리지 않습니다. 저장소가 무거워집니다.
문서에 꼭 필요한 그림만 `docs/` 아래에 넣으세요.

## 남의 코드를 수정해도 되나요

`basic_codes/`는 공용이므로 개선은 환영합니다. 다만

- 기존 동작을 바꾸는 수정은 브랜치 + PR로 진행하고 작성자에게 리뷰를 요청하세요
- 단순 버그 수정이나 주석 추가는 바로 커밋해도 됩니다

## 새 프로젝트를 시작하려면

Owner에게 요청하세요. 팀 생성 → ruleset bypass 추가 → 폴더 생성 순으로 처리됩니다.

## 저장소가 public인데 괜찮나요

분석 코드 자체는 공개해도 문제없는 경우가 대부분입니다. 다만

- 미발표 연구의 핵심 코드는 공개 시점을 지도교수와 상의하세요
- 데이터, API 키, 개인정보는 절대 올리지 마세요
- 민감한 코드가 필요하면 별도의 비공개 저장소를 요청하세요
