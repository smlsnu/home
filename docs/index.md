---
hide:
  - navigation
  - toc
---

<div class="sml-hero" markdown="1">
<span class="sml-hero__eyebrow">Satellite Meteorology Laboratory · Seoul National University</span>

# 위성기상실험실 GitHub

연구실 코드를 함께 쓰고, 프로젝트 진행 과정을 남겨 두는 곳입니다.
Git이 처음이어도 이 문서만 따라오면 됩니다.

<div class="sml-hero__actions" markdown="1">
[시작하기](getting-started.md){ .md-button .md-button--primary }
[Git 사용법](git-guide.md){ .md-button }
[:material-github: 조직 페이지](https://github.com/smlsnu){ .md-button }
</div>
</div>

## 무엇부터 볼까요

<div class="sml-cards" markdown="1">

<a class="sml-card" href="getting-started/">
<span class="sml-card__icon">🚀</span>
<span class="sml-card__title">시작하기</span>
<span class="sml-card__desc">조직 가입, Git·VS Code 설치, 저장소 내려받기, conda 환경 준비까지 순서대로 안내합니다.</span>
</a>

<a class="sml-card" href="git-guide/">
<span class="sml-card__icon">🌿</span>
<span class="sml-card__title">Git 사용법</span>
<span class="sml-card__desc">VS Code 화면 기준으로 commit · push · pull · 브랜치 · 충돌 해결 · Pull Request를 설명합니다.</span>
</a>

<a class="sml-card" href="structure/">
<span class="sml-card__icon">🗂️</span>
<span class="sml-card__title">저장소 구성</span>
<span class="sml-card__desc">어떤 저장소가 있고 코드를 어디에 올려야 하는지, 폴더는 어떻게 나누는지 정리했습니다.</span>
</a>

<a class="sml-card" href="permissions/">
<span class="sml-card__icon">🔑</span>
<span class="sml-card__title">권한과 규칙</span>
<span class="sml-card__desc">팀별 권한 범위와 지켜야 할 규칙입니다. push가 거부될 때 먼저 확인하세요.</span>
</a>

<a class="sml-card" href="faq/">
<span class="sml-card__icon">💬</span>
<span class="sml-card__title">자주 묻는 질문</span>
<span class="sml-card__desc">clone 실패, 충돌, 데이터 파일 실수 커밋 등 자주 겪는 상황의 해결 방법입니다.</span>
</a>

<a class="sml-card" href="https://github.com/smlsnu">
<span class="sml-card__icon">📦</span>
<span class="sml-card__title">저장소 바로가기</span>
<span class="sml-card__desc">smlsnu 조직의 모든 저장소 목록을 GitHub에서 확인합니다.</span>
</a>

</div>

## 저장소 목록

| 저장소 | 공개 | 내용 | 수정 가능 |
|--------|------|------|-----------|
| [`home`](https://github.com/smlsnu/home) | public | 안내 문서 (이 사이트의 소스) | `lab-members` |
| [`basic-codes`](https://github.com/smlsnu/basic-codes) | private | 공용 유틸리티 · 시각화 템플릿 · 입문 예제 | `lab-members` |
| [`project-rain`](https://github.com/smlsnu/project-rain) | private | rain 프로젝트 | `project-rain` |
| [`project-tq`](https://github.com/smlsnu/project-tq) | private | tq 프로젝트 | `project-tq` |
| [`project-rt`](https://github.com/smlsnu/project-rt) | private | rt 프로젝트 | `project-rt` |
| [`project-polar`](https://github.com/smlsnu/project-polar) | private | polar 프로젝트 | `project-polar` |
| [`project-env`](https://github.com/smlsnu/project-env) | private | env 프로젝트 | `project-env` |

프로젝트 저장소는 **해당 팀만 수정할 수 있습니다.** 연구실 구성원은 모든 저장소를 읽을 수 있습니다.

## 세 가지 원칙

!!! danger "데이터 파일은 올리지 않습니다"
    `.pkl` `.h5` `.nc` `.gz` 등은 `.gitignore` 로 막아 두었습니다.
    저장소에는 **코드와 결과 그림**만 올라갑니다.

!!! warning "`home` 저장소는 공개되어 있습니다"
    사이트 발행을 위해 이 저장소만 public 입니다.
    코드 · 데이터 · API 키 · 미공개 연구 내용을 이곳에 올리지 마세요.

!!! tip "작업 시작 전에는 항상 Pull"
    이 습관 하나로 충돌의 대부분이 예방됩니다.
