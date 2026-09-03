# 문서 수정 안내

이 저장소는 연구실 GitHub **안내 문서**만 담고 있습니다. 코드는 다른 저장소에 있습니다.

## 문서 고치기

1. `docs/` 안의 마크다운 파일을 수정합니다.
2. `main` 브랜치에 push합니다.
3. GitHub Actions가 자동으로 사이트를 다시 빌드합니다. 몇 분 뒤 반영됩니다.

사이트에서 각 페이지 우측 상단의 연필 아이콘을 누르면 해당 파일 편집 화면으로 바로 이동합니다.

## 페이지 추가

`docs/새파일.md` 를 만들고 `mkdocs.yml` 의 `nav:` 에 한 줄 추가합니다.

```yaml
nav:
  - 홈: index.md
  - 새 페이지: 새파일.md
```

## 로컬에서 미리보기

```bash
pip install mkdocs-material
mkdocs serve
```

`http://127.0.0.1:8000` 에서 확인할 수 있습니다.

## 주의

이 저장소는 **공개(public)** 입니다. 코드, 데이터, API 키, 미공개 연구 내용을 올리지 마세요.

코드 기여 규칙은 사이트의 [권한과 규칙](https://smlsnu.github.io/docs/permissions/) 을 참고하세요.
