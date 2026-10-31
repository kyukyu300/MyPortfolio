---
title: "Hugo와 GitHub Pages로 포트폴리오 사이트 만들기"
description: "Hugo 정적 사이트 생성기와 GitHub Pages를 이용해 개인 포트폴리오 사이트를 만든 과정을 기록합니다."
date: 2026-10-29
categories:
    - 프로젝트
tags:
    - Hugo
    - GitHub Pages
    - 웹개발
---

## 활동 개요

- **수행 시기**: 2026년 10월 (진행 중)
- **상태**: 진행 중
- **유형**: 개인 활동 (수업 과제 실습)

---

## 활동 목적

이 프로젝트의 목적은 **Hugo 정적 사이트 생성기**와 **GitHub Pages**를 활용해 개인 포트폴리오 사이트를 직접 구축하고 배포하는 것입니다.

단순히 사이트를 만드는 것에서 그치지 않고, 다음 문제들을 해결하는 것이 목표였습니다:
- Git을 통한 버전 관리를 실제로 적용하기
- GitHub Actions를 통해 자동 배포 파이프라인 구성하기
- 반응형 레이아웃과 접근성을 갖춘 사이트 완성하기

---

## 본인 역할 및 기여

**개인 활동**으로, 모든 과정을 직접 수행했습니다:
- Hugo 테마 선택 및 다운로드 (Stack 테마)
- 설정 파일 수정 (baseURL, 언어, 메뉴 등)
- 개인 소개 콘텐츠 작성
- GitHub 저장소 생성 및 연결
- GitHub Actions 워크플로 확인 및 배포

---

## 수행 과정

### 1단계 — 테마 선택 및 초기 설정

Hugo Themes에서 **Stack 테마**를 선택했습니다. 카드형 레이아웃으로 가독성이 좋고, 블로그와 포트폴리오 용도 모두에 적합해 보였기 때문입니다.

ZIP으로 다운로드한 후, 수업 제공 Python 스크립트를 활용해 GitHub Pages에 맞는 초기 구조를 준비했습니다.

### 2단계 — 설정 파일 수정

가장 중요한 작업은 `config/_default/hugo.toml`의 `baseURL`을 변경하는 것이었습니다.

```toml
# 변경 전 (데모 주소 — 채점 탈락)
baseURL = "https://demo.stack.cai.im/"

# 변경 후 (내 GitHub Pages 주소)
baseURL = "https://kyukyu300.github.io/MyPortfolio/"
```

또한 언어를 영어에서 한국어(`ko`)로 변경하고, 데모용 Disqus 댓글 설정과 Twitter 링크도 제거했습니다.

### 3단계 — 콘텐츠 작성

데모용 샘플 포스트(`pagination-test`, `Image Gallery` 등)를 모두 삭제하고, 실제 활동 내용으로 교체했습니다.

### 4단계 — GitHub Pages 배포

GitHub 저장소에 push하고, Settings → Pages에서 배포 Source를 **GitHub Actions**로 설정했습니다.

---

## 산출물 및 결과

- **배포된 사이트**: [https://kyukyu300.github.io/MyPortfolio/](https://kyukyu300.github.io/MyPortfolio/)
- **소스 저장소**: [https://github.com/kyukyu300/MyPortfolio](https://github.com/kyukyu300/MyPortfolio)
- GitHub Actions를 통한 자동 빌드·배포 파이프라인 완성

---

## 배운 점과 개선 방향

### 배운 점
- Hugo의 설정 파일 구조(`config/_default/`)와 각 파일의 역할을 이해했습니다.
- `baseURL`이 잘못 설정되면 자산 경로가 모두 깨진다는 것을 직접 확인했습니다.
- GitHub Actions의 워크플로 파일을 읽고 이해하는 능력이 생겼습니다.

### 개선 방향
- 커스텀 아바타 이미지를 직접 제작하여 적용하기
- 더 많은 활동·프로젝트 포스트 추가하기
- 다크/라이트 모드 테마 설정 최적화하기
