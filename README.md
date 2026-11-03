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

---

## 📝 사이트 콘텐츠 및 설정 수정 가이드 (P57)

사이트의 주요 정보나 새로운 활동 글을 수정 및 추가할 때 변경해야 할 파일들의 위치와 역할입니다.

| 항목 | 파일 상대 경로 | 설명 및 수정 내용 |
| :--- | :--- | :--- |
| **전역 운영 설정** | `site/config/_default/hugo.toml` | 사이트 `baseURL`, 타이틀, 기본 언어(`ko`), permalinks 규칙 |
| **사이트 파라미터** | `site/config/_default/params.toml` | 사이드바 아바타 경로, 검색 위젯, 파비콘 설정 |
| **한국어 문구 설정** | `site/config/_default/languages.toml` | 사이드바 서브타이틀("컴퓨터공학을 배우고 성장하는...") 문구 |
| **소개 페이지** | `site/content/page/about/index.md` | 본인 소개, 관심 분야, 학습 목표, 기술 역량 표, 활동 목록 |
| **링크 페이지** | `site/content/page/links/index.md` | GitHub 프로필, 포트폴리오 저장소, 프로젝트 외부 링크 모음 |
| **활동 글 추가/수정** | `site/content/post/<폴더명>/index.md` | 대표 프로젝트 포스트 본문 및 캡처 이미지 (Page Bundle) |
| **커스텀 스타일** | `site/assets/scss/custom.scss` | 초점 링(Focus Ring), 반응형 줄바꿈, 터치 영역 스타일 |
| **프로필 아바타** | `site/assets/img/avatar.png` | 사이드바 및 파비콘으로 사용되는 프로필 이미지 (300x300) |

---

## 🚀 수정 후 Git 커밋 및 자동 재배포 확인 절차 (P57)

로컬에서 사이트 내용을 수정한 후 원격 저장소에 반영하고, GitHub Actions를 통해 자동 배포되는 것을 확인하는 전체 흐름입니다.

### 1. 변경 사항 커밋 및 푸시
```bash
# 수정된 파일 확인
git status

# 변경 파일 스테이징 및 의미 있는 커밋 메시지 작성
git add site/content/page/about/index.md
git commit -m "소개 페이지: 최신 활동 내용 업데이트"

# 원격 main 브랜치로 푸시 (또는 작업 브랜치 푸시 후 PR 병합)
git push origin main
```

### 2. GitHub Pages 및 Actions 설정 확인
- 저장소의 **Settings** 탭 ➡️ **Pages** 메뉴로 이동합니다.
- **Build and deployment** 항목의 **Source**가 반드시 **`GitHub Actions`**로 지정되어 있어야 합니다.

### 3. 자동 배포 진행 상황 확인
- 저장소 상단의 **Actions** 탭(`https://github.com/kyukyu300/MyPortfolio/actions`)으로 이동합니다.
- `main` 브랜치에 푸시된 커밋에 대해 `Deploy Hugo to GitHub Pages` 워크플로가 자동으로 트리거됩니다.
- `build` 단계(Hugo 빌드)와 `deploy` 단계(Pages 배포)가 모두 녹색 체크(`✓`)로 완료될 때까지 대기합니다 (약 40초~1분 소요).

### 4. 공개 사이트 배포 결과 확인
- 배포 완료 후 브라우저에서 공개 사이트([https://kyukyu300.github.io/MyPortfolio/](https://kyukyu300.github.io/MyPortfolio/))에 접속합니다.
- 브라우저 캐시로 인해 이전 화면이 보일 수 있으므로 **강력 새로고침**(`Cmd + Shift + R` 또는 `Ctrl + F5`)을 수행하여 변경 사항이 정상 반영되었는지 확인합니다.
