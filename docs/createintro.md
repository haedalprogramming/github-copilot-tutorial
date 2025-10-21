# GitHub Copilot으로 나만의 소개 페이지 만들기

AI의 도움을 받아 웹 개발을 배우면서, 실제로 인터넷에 공개되는 나만의 웹사이트를 만들어봅시다!

## 무엇을 만드나요?

- **개인 소개 페이지**: 나의 이름, 전공, 관심사를 소개하는 웹페이지
- **실제 웹사이트**: `https://<내아이디>.github.io/intro/` 주소로 접속 가능
- **포트폴리오 시작**: 나중에 취업할 때 보여줄 수 있는 프로젝트

## 준비물 확인

시작하기 전에 아래 항목들이 준비되어 있는지 확인하세요:

- ✅ GitHub 계정 (없다면 [github.com](https://github.com)에서 가입)
- ✅ GitHub Copilot CLI 설치 (이전 문서 참고)
- ✅ Git 설치 확인: 터미널에서 `git --version` 실행
- ✅ GitHub CLI 로그인: `gh auth login` 완료

## 1단계: 프로젝트 폴더 만들기

### 작업 폴더 생성

```bash
# 1. intro라는 폴더를 만들고 그 안으로 이동
mkdir intro && cd intro

# 2. 제대로 만들어졌는지 확인
pwd  # 현재 위치를 보여줍니다
```

**💡 팁:**
- `mkdir`은 "make directory"의 줄임말로 폴더를 만듭니다
- `&&`는 "그리고"라는 뜻으로 두 명령어를 연결합니다
- `cd`는 "change directory"로 폴더로 이동합니다

## 2단계: GitHub 저장소 만들기

### Git 저장소 초기화

```bash
# 1. Git 저장소로 만들기
git init -b main

# 2. GitHub에 저장소 생성
gh repo create intro --public --source=. --remote=origin
```

**설명:**
- `git init`: 현재 폴더를 Git으로 관리 시작
- `-b main`: 기본 브랜치 이름을 main으로 설정
- `gh repo create`: GitHub에 새 저장소를 만듭니다
- `--public`: 누구나 볼 수 있는 공개 저장소로 만듭니다

**⚠️ 주의:**
만약 "repository already exists" 에러가 나면, GitHub에 이미 같은 이름의 저장소가 있는 것입니다. 다른 이름을 사용하거나 GitHub에서 삭제 후 다시 시도하세요.

## 3단계: AI로 웹페이지 생성하기

### Copilot에게 코드 작성 요청

이제 가장 재미있는 부분입니다! AI에게 웹페이지를 만들어달라고 요청합니다.

```bash
gh copilot suggest "간단한 개인 소개 웹페이지를 만들어줘. 이름, 전공, 기술 스택, GitHub 링크가 들어가고, HTML과 CSS를 한 파일에 작성해줘. 한국어로 작성해줘."
```

**무슨 일이 일어나나요?**
1. Copilot이 여러분의 요청을 이해합니다
2. HTML과 CSS 코드를 생성합니다
3. 터미널에 코드를 보여줍니다

### 생성된 코드 저장하기

Copilot이 제안한 코드를 복사해서 `index.html` 파일로 저장하거나, 직접 만들어봅시다:

```bash
# 에디터로 파일 열기 (VS Code 사용 시)
code index.html

# 또는 다른 에디터로
nano index.html  # 또는 vim, notepad 등
```

**참고:** Copilot이 생성한 코드를 그대로 붙여넣으세요!

## 4단계: 내 정보로 수정하기

`index.html` 파일을 열어서 다음 부분들을 여러분의 정보로 바꿔주세요:

```html
<!-- 수정할 부분들 -->
<h1>홍길동</h1>  <!-- 여러분의 이름 -->
<p>컴퓨터공학과 3학년</p>  <!-- 여러분의 전공과 학년 -->
<p>안녕하세요! ...</p>  <!-- 자기소개 -->

<!-- 기술 스택 -->
<span>Python</span>
<span>JavaScript</span>  <!-- 여러분이 아는 언어 -->

<!-- 연락처 -->
<a href="https://github.com/여러분의아이디">GitHub</a>
<a href="mailto:여러분의이메일@example.com">Email</a>
```

**💡 초보자 팁:**
- HTML을 몰라도 괜찮습니다! 태그 안의 한글 텍스트만 수정하세요
- `<h1>`, `<p>` 같은 태그는 건드리지 마세요
- 저장은 `Ctrl + S` (Windows) 또는 `Cmd + S` (Mac)

## 5단계: 로컬에서 미리보기

GitHub에 올리기 전에 내 컴퓨터에서 먼저 확인해봅시다.

### 방법 1: 브라우저로 직접 열기

```bash
# 현재 폴더의 경로 확인
pwd

# 출력된 경로를 복사하고, 브라우저 주소창에 입력
# file:///Users/내이름/intro/index.html
```

파일 탐색기(Windows) 또는 Finder(Mac)에서 `index.html`을 더블클릭해도 됩니다!

### 방법 2: 간단한 서버 실행 (선택사항)

Python이 설치되어 있다면:

```bash
# Python 3
python3 -m http.server 8000

# 브라우저에서 http://localhost:8000 접속
```

**확인할 것:**
- 이름, 전공이 제대로 보이나요?
- 링크를 클릭하면 제대로 작동하나요?
- 디자인이 마음에 드나요?

## 6단계: GitHub에 업로드하기

### Git으로 변경사항 저장

```bash
# 1. 어떤 파일이 있는지 확인
git status

# 2. 모든 파일을 추가 (빨간색 → 초록색)
git add .

# 3. 변경사항을 저장 (커밋)
git commit -m "첫 번째 소개 페이지 완성"

# 4. GitHub에 업로드
git push -u origin main
```

**각 명령어의 의미:**
- `git add .`: "이 파일들을 저장할 준비 완료!"
- `git commit`: "이 시점을 기록해!"
- `git push`: "GitHub에 올려!"

**💡 자주 하는 실수:**
```bash
# 에러: "nothing to commit" → 파일을 수정하지 않았거나 add를 안 했습니다
# 해결: git add . 을 먼저 실행

# 에러: "failed to push" → 인터넷 연결 또는 권한 문제
# 해결: gh auth login 으로 다시 로그인
```

## 7단계: GitHub Pages로 배포하기

이제 여러분의 웹사이트를 인터넷에 공개할 차례입니다!

### GitHub 저장소 설정

1. 브라우저에서 `https://github.com/<내아이디>/intro` 접속
2. **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 클릭
4. **Source**를 **GitHub Actions**로 변경

### GitHub Actions 워크플로우 만들기

```bash
# 1. 필요한 폴더 생성
mkdir -p .github/workflows

# 2. 워크플로우 파일 생성
code .github/workflows/pages.yml
```

`pages.yml` 파일에 다음 내용을 붙여넣기:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ "main" ]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

**이 파일이 하는 일:**
- main 브랜치에 코드가 올라가면 자동으로 실행
- 여러분의 웹페이지를 인터넷에 배포

### 워크플로우 업로드

```bash
git add .
git commit -m "GitHub Actions 배포 설정 추가"
git push
```

## 8단계: 내 웹사이트 확인하기

### 배포 상태 확인

1. GitHub 저장소의 **Actions** 탭으로 이동
2. 노란색 점(진행 중) → 초록색 체크(성공) 될 때까지 기다리기
3. 보통 1-2분 정도 걸립니다

### 내 웹사이트 접속

```
https://<내GitHub아이디>.github.io/intro/
```

**축하합니다!** 🎉

여러분의 첫 웹사이트가 인터넷에 공개되었습니다!

## 문제 해결

### 404 에러가 나요

- GitHub Actions가 완료되었는지 확인
- URL이 정확한지 확인 (intro**s**가 아니라 intro)
- 저장소가 Public인지 확인

### 배포가 실패해요

- Actions 탭에서 에러 메시지 확인
- Settings > Pages에서 Source가 GitHub Actions인지 확인
- `pages.yml` 파일의 들여쓰기가 정확한지 확인

### 수정사항이 반영 안 돼요

```bash
# 캐시 문제일 수 있습니다
# 브라우저에서 Ctrl + Shift + R (강력 새로고침)

# 또는 다시 push
git add .
git commit -m "수정사항 반영"
git push
```

## 다음 단계

이제 기본 웹사이트를 만들었으니:

1. **디자인 개선**: CSS를 수정해서 더 예쁘게 만들기
2. **내용 추가**: 프로젝트, 블로그 링크 추가
3. **고급 기능**: [GitHub Actions 자세히 알아보기](githubaction.md)

**참고 자료:**
- [HTML 기초 배우기](https://developer.mozilla.org/ko/docs/Learn/HTML)
- [CSS 기초 배우기](https://developer.mozilla.org/ko/docs/Learn/CSS)
- [GitHub Pages 문서](https://docs.github.com/pages)