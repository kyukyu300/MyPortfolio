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

---

## 💻 로컬 빌드 및 실행 재현 명령어 (P56)

저장소를 클론한 후 로컬 PC에서 사이트를 직접 실행하고 검증하는 절차입니다.

### 1. 저장소 복제 및 이동
```bash
git clone https://github.com/kyukyu300/MyPortfolio.git
cd MyPortfolio
```

### 2. 의존성 준비
```bash
python .github/pages_build.py --dependencies
```

### 3. 로컬 개발 서버 실행 (실시간 프리뷰)
```bash
# Hugo 로컬 서버 구동 (기본 포트: http://localhost:1313/MyPortfolio/)
hugo server --source site --buildDrafts --buildFuture
```
브라우저에서 `http://localhost:1313/MyPortfolio/` 주소로 접속하여 변경 사항을 실시간으로 확인할 수 있습니다.

### 4. 프로덕션 정적 사이트 빌드
```bash
# GitHub Pages 배포용 정적 파일 생성 (결과물은 public/ 폴더에 생성됨)
python .github/pages_build.py --build
```
빌드 성공 시 프로젝트 루트의 `public/` 디렉터리에 배포용 정적 HTML/CSS/JS 파일이 생성됩니다.
