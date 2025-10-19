# github-copilot-tutorial
GiHub Copilot으로 자기소개페이지 만들기

좋아요! 아래 튜토리얼은 **GitHub Copilot CLI**를 활용해 “자기소개 페이지”를 만들고, **GitHub Actions + GitHub Pages**로 자동 배포까지 완료하는 전 과정을 담고 있어요. 그대로 따라 하면 로컬에서 커밋 → 푸시하면 곧바로 프로덕션에 반영되는 깔끔한 워크플로우가 완성됩니다.

---

# 1) 목표 아키텍처

* 저장소: `username/intro` (예시)
* 브랜치: `main`
* 배포: GitHub Actions로 빌드 → GitHub Pages(브랜치 기반 or Pages 전용 아티팩트) 자동 배포
* 산출물: `index.html` + 간단한 CSS/이미지

---

# 2) 사전 준비물

* GitHub 계정
* 최신 **Git** & **Node.js** (Copilot CLI 설치용)
* **GitHub CLI(gh)**: `https://cli.github.com/`에서 설치
* GitHub Copilot 사용 권한(조직/개인 구독)

---

# 3) Copilot CLI 설치 (두 가지 중 편한 방법 선택)

### 옵션 A) GitHub CLI 확장: `gh copilot`

> 최근 권장. GitHub CLI 안에서 Copilot 기능을 씁니다.

```bash
gh extension install github/gh-copilot
gh auth login        # GitHub 로그인
gh copilot auth login
```

주요 명령:

* `gh copilot explain "<명령>"` : 명령/코드 설명
* `gh copilot suggest -t shell "<하고 싶은 일>"` : 쉘 명령 제안
* `gh copilot suggest -t code "<원하는 코드>"` : 코드 제안 (스니펫 생성)

### 옵션 B) 독립 Copilot CLI(`copilot` 명령)

> `what-the-shell` 등 셸·git 명령 제안에 특화된 초기 CLI.

```bash
npm install -g @githubnext/github-copilot-cli
copilot auth login
```

주요 명령(예시):

* `copilot what-the-shell "<하고 싶은 일>"` → 제안 명령을 실행 전에 확인
* `copilot git-assist "<깃으로 하고 싶은 일>"`

> 어느 쪽이든 **한 가지만** 써도 충분합니다. 아래 예시는 `gh copilot` 기준으로 보여드리되, 같은 아이디어로 `copilot`에 묻는 방식도 병행 표기합니다.

---

# 4) 새 저장소 만들기 & 로컬 초기화

```bash
# 1) 새 디렉터리
mkdir intro && cd intro

# 2) gh로 원격 리포 생성 (public 권장)
gh repo create intro --public --source=. --remote=origin --push
# 또는 GitHub 웹에서 만들고, 이후 origin 추가: git remote add origin <repo-url>

# 3) 기본 Git 설정
git init -b main
```

> 헷갈리면 Copilot에 시켜보기:

```bash
gh copilot suggest -t shell "Create a new public repo named intro, set main as default branch, and add it as origin"
# 또는
copilot what-the-shell "새 디렉터리 만들고 main 브랜치로 git init하고 원격 origin 연결"
```

---

# 5) 자기소개 페이지 뼈대 생성 (Copilot에게 시키기)

아래처럼 “원하는 페이지”를 자연어로 설명하면, Copilot이 HTML/CSS 초안을 만들어줍니다.

### 프롬프트 예시 (코드 생성)

```bash
gh copilot suggest -t code "A simple, responsive personal intro page (Korean), with a hero section (name, role), about, skills badges, contact links (email, GitHub). Use semantic HTML5 and a minimal CSS in one file."
```

출력된 스니펫을 `index.html`로 저장하세요. 직접 작성하고 싶다면, 다음 최소 예시로 시작해도 됩니다:

```html
<!doctype html>
<html lang="ko">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>홍길동 – 소개</title>
  <style>
    :root { font-family: system-ui, sans-serif; }
    body { margin:0; line-height:1.6; }
    header { padding:64px 20px; text-align:center; }
    h1 { font-size:2.2rem; margin:0 0 8px; }
    .role { opacity:.7; margin-bottom:24px; }
    main { max-width:900px; margin:0 auto; padding:0 20px 80px; }
    section { margin:40px 0; }
    .badges { display:flex; flex-wrap:wrap; gap:8px; }
    .badge { padding:6px 10px; border:1px solid #ddd; border-radius:999px; }
    footer { text-align:center; padding:24px; border-top:1px solid #eee; color:#666; }
    a { color:inherit; }
  </style>
</head>
<body>
  <header>
    <h1>홍길동</h1>
    <div class="role">백엔드 개발자 · 서울</div>
    <p>문제를 단순하게 풀어내는 걸 좋아합니다. 요즘은 Go와 분산 시스템에 관심이 많아요.</p>
  </header>
  <main>
    <section>
      <h2>About</h2>
      <p>…간단한 자기소개를 적어주세요…</p>
    </section>
    <section>
      <h2>Skills</h2>
      <div class="badges">
        <span class="badge">Go</span>
        <span class="badge">Kotlin</span>
        <span class="badge">AWS</span>
        <span class="badge">Docker</span>
      </div>
    </section>
    <section>
      <h2>Contact</h2>
      <p>📧 <a href="mailto:you@example.com">you@example.com</a> · 🐙 <a href="https://github.com/yourid">GitHub</a></p>
    </section>
  </main>
  <footer>© <span id="y"></span> Hong Gil-dong</footer>
  <script>document.getElementById('y').textContent = new Date().getFullYear()</script>
</body>
</html>
```

이미지나 파비콘이 필요하면:

```bash
gh copilot suggest -t shell "download a CC0 avatar image to ./assets/avatar.jpg"
# 또는
copilot what-the-shell "CC0 라이선스 아바타 이미지를 assets/avatar.jpg로 저장"
```

---

# 6) GitHub Pages로 배포하는 GitHub Actions 설정

**가장 간단한 방법**은 정적 파일을 그대로 Pages에 올리는 것(빌드 없음)입니다.

## 6-1) Pages 권한/환경 설정

1. GitHub 저장소 → **Settings → Pages**
2. “Source”를 **GitHub Actions**로 설정

## 6-2) 워크플로우 파일 추가

`.github/workflows/pages.yml` 생성:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ "main" ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      # (빌드 과정이 없으면) 정적 파일을 그대로 업로드
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'     # index.html이 리포 루트에 있는 경우

      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

> **폴더 분리**를 선호하면 `path: 'dist'`로 바꾸고, `index.html` 등을 `dist/`에 두세요.
> “빌드가 필요한” 프레임워크(예: React/Vite)를 쓰는 경우엔 위에 `setup-node`/`npm ci && npm run build` 단계만 추가하면 됩니다.

Copilot 도움받기:

```bash
gh copilot suggest -t code "A GitHub Actions workflow that deploys a static site to GitHub Pages using actions/upload-pages-artifact and actions/deploy-pages when pushing to main."
```

---

# 7) 커밋 & 최초 배포

```bash
git add .
git commit -m "feat: my intro page"
git push -u origin main
```

푸시가 끝나면 **Actions** 탭의 `Deploy to GitHub Pages`가 실행됩니다. 성공 후 Pages 주소는 보통:

```
https://<username>.github.io/intro/
```

> 리포 이름이 `<username>.github.io`라면 루트 도메인 `https://<username>.github.io/`로 열립니다.

---

# 8) PR 기반 미리보기(선택)

기능 브랜치에서 변경 시 PR마다 미리보기(Preview URL)가 생기게 할 수도 있어요. Pages가 PR 배포를 지원하므로 워크플로우 트리거에 `pull_request`를 추가합니다.

```yaml
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
  workflow_dispatch:
```

---

# 9) 자주 쓰는 Copilot CLI 프롬프트 레시피

* **쉘 명령 도출**

  * `gh copilot suggest -t shell "Create .github/workflows/pages.yml with a workflow that deploys static site to GitHub Pages"`
  * `copilot what-the-shell "git에서 마지막 커밋 메시지 수정 후 강제 푸시"`

* **HTML/CSS 생성**

  * `gh copilot suggest -t code "Add a simple dark mode toggle to my index.html using CSS variables and a small inline script"`

* **이미지 최적화 명령**

  * `gh copilot suggest -t shell "Optimize all .jpg in assets to width 1600 keeping quality ~80 using ImageMagick"`

* **액션 디버깅 도움**

  * `gh copilot explain "Why does actions/deploy-pages@v4 need id-token: write permission?"`

---

# 10) 트러블슈팅

* **Pages 404**: 배포 후 1~2분 정도 캐시 전파 시간이 있을 수 있어요. 리포가 private이면 Pages 권한/가시성 확인.
* **워크플로우 권한 에러**: 위 예시는 `permissions: pages: write, id-token: write`가 꼭 필요합니다.
* **커스텀 도메인**: Settings → Pages에서 Custom domain 설정 후 DNS `CNAME` 레코드 추가.
* **빌드 추가 시**(Vite/Next 등):

  ```yaml
  - uses: actions/setup-node@v4
    with: { node-version: '20' }
  - run: npm ci
  - run: npm run build
  - uses: actions/upload-pages-artifact@v3
    with: { path: 'dist' }  # 프레임워크에 맞게 수정
  ```

---

# 11) 다음 단계(보너스)

* 다국어(i18n) 스위치, Open Graph 메타태그, SEO 메타데이터 추가
* 간단한 블로그 섹션(마크다운 → 정적 HTML 변환 스크립트)
* GitHub Actions에 Lighthouse CI 연결해 성능 리포트 남기기
* 연락 폼(Formspree 등 외부 서비스 연결)

---

필요하시면 **“템플릿 리포 + 완성된 워크플로우”**를 바로 쓸 수 있도록 최소 구현 코드를 만들어드릴게요. 어떤 스타일(라이트/다크, 컬러 톤, 섹션 구성)로 가고 싶으세요?
