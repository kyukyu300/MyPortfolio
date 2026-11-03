# 김규진 개인 포트폴리오 웹사이트 (MyPortfolio)

Hugo 정적 사이트 생성기와 GitHub Actions, GitHub Pages를 활용하여 구축한 김규진의 개인 포트폴리오 사이트입니다.  
컴퓨터공학 전공 지식과 웹/백엔드 개발 활동, AI 에이전트 프로젝트 기록을 담고 있습니다.

---

## 🌐 사이트 및 저장소 정보

- **공개 배포 URL**: [https://kyukyu300.github.io/MyPortfolio/](https://kyukyu300.github.io/MyPortfolio/)
- **소스 코드 저장소**: [https://github.com/kyukyu300/MyPortfolio](https://github.com/kyukyu300/MyPortfolio)
- **배포 브랜치**: `main` (GitHub Actions를 통한 자동 빌드 및 배포)
- **사이트 제작자**: 김규진 ([@kyukyu300](https://github.com/kyukyu300))

---

## 🛠️ 개발 환경 및 요구 도구 (P56)

본 프로젝트는 GitHub Actions CI 환경과 동일한 도구 버전을 기준으로 빌드 및 재현할 수 있습니다.

| 도구명 | 권장/운영 버전 | 비고 |
| :--- | :--- | :--- |
| **Hugo Extended** | `v0.167.0` | SCSS 파이프라인 컴파일을 위해 반드시 **Extended** 버전 필요 |
| **Dart Sass** | `v1.105.0` | 최신 SCSS 문법 컴파일용 Dart Sass 바이너리 |
| **Go** | `1.25.0` 이상 | Hugo Modules 및 의존성 패키지 관리 |
| **Python** | `3.12` 이상 | 배포 보조 스크립트 (`.github/pages_build.py`) 구동용 |
| **Git** | `2.40.0` 이상 | 버전 관리 및 GitHub Actions 연동 |
