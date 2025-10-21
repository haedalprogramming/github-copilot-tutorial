# GitHub Actions로 자동 배포하기

## GitHub Actions가 뭔가요?

GitHub Actions는 "로봇 비서"같은 기능입니다. 여러분이 코드를 GitHub에 올리면, 자동으로:
- 웹사이트를 인터넷에 배포하거나
- 코드를 테스트하거나
- 다른 반복적인 작업을 수행합니다

**예를 들면:**
- 옛날: 코드 수정 → 수동으로 서버에 업로드 → 배포 확인 (10분)
- 지금: 코드 수정 → `git push` → 끝! (자동으로 배포됨, 2분)

## 왜 사용하나요?

### 시간 절약
```
수동 배포: 코드 수정할 때마다 5-10분
자동 배포: git push만 하면 끝! (1분)
```

### 실수 방지
- 사람이 하면 빠뜨리는 단계가 있을 수 있음
- 로봇은 항상 같은 순서로 정확하게 실행

### 협업에 좋음
- 팀 프로젝트에서 누가 push해도 같은 방식으로 배포됨
- 각자 배포 방법을 따로 알 필요 없음

## 이 문서에서 배울 것

개인 소개 페이지를 만들었다면, 이제 자동으로 배포되도록 설정해봅시다!

## 1단계: 워크플로우 파일 만들기

### 폴더 구조 만들기

```bash
# 1. 프로젝트 폴더로 이동
cd intro  # 또는 여러분의 프로젝트 폴더명

# 2. GitHub Actions 폴더 생성
mkdir -p .github/workflows

# 3. 확인
ls -la .github/workflows
```

**💡 왜 `.github/workflows`인가요?**
- GitHub은 이 폴더에서 자동화 설정 파일을 찾습니다
- 점(`.`)으로 시작하는 폴더는 숨김 폴더입니다

### 워크플로우 파일 작성

`pages.yml` 파일을 만들어봅시다:

```bash
# 에디터로 열기
code .github/workflows/pages.yml

# 또는
nano .github/workflows/pages.yml
```

다음 내용을 복사해서 붙여넣으세요:

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

### 각 부분이 하는 일

이 파일을 한 줄씩 이해해봅시다:

```yaml
name: Deploy to GitHub Pages
# 이 자동화의 이름 (GitHub에서 보이는 이름)

on:
  push:
    branches: [ "main" ]
# 언제 실행할까? → main 브랜치에 push될 때!

permissions:
  contents: read    # 코드를 읽을 권한
  pages: write      # GitHub Pages에 쓸 권한
  id-token: write   # 인증 토큰 쓸 권한

jobs:
  deploy:           # "deploy"라는 작업 시작
    runs-on: ubuntu-latest  # Ubuntu 리눅스 서버에서 실행

    steps:          # 순서대로 실행할 단계들
      - name: Checkout
        uses: actions/checkout@v4
        # 1단계: 내 코드를 가져오기

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
        # 2단계: 현재 폴더(.)의 모든 파일을 준비

      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
        # 3단계: GitHub Pages에 배포!
```

**쉽게 말하면:**
1. main 브랜치에 코드가 올라오면
2. Ubuntu 서버를 하나 빌려서
3. 내 코드를 가져와서
4. GitHub Pages에 올립니다!

## 2단계: GitHub Pages 설정

이제 GitHub 웹사이트에서 설정을 해야 합니다.

### 저장소 설정 페이지로 이동

1. 브라우저에서 `https://github.com/<내아이디>/intro` 접속
2. 상단의 **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 클릭

### Source 변경

**Build and deployment** 섹션에서:
- **Source**를 **GitHub Actions**로 변경

이렇게 하면 "이제부터 자동 배포를 사용하겠다"고 GitHub에 알리는 것입니다!

**💡 왜 이렇게 하나요?**
- 예전 방식: GitHub이 자동으로 배포 (제한적)
- 새로운 방식: GitHub Actions로 우리가 원하는 대로 배포 (유연함)

## 3단계: 코드 업로드하기

이제 워크플로우 파일을 GitHub에 올려봅시다!

```bash
# 1. 변경사항 확인
git status
# → .github/workflows/pages.yml 파일이 보여야 합니다

# 2. 파일 추가
git add .

# 3. 커밋
git commit -m "GitHub Actions 자동 배포 설정"

# 4. GitHub에 업로드
git push origin main
```

**이제 무슨 일이 일어날까요?**

1. `git push`를 하는 순간
2. GitHub이 `.github/workflows/pages.yml` 파일을 발견
3. "아, 자동 배포를 해야하는구나!" 하고 실행
4. 1-2분 후 웹사이트가 배포됨!

## 4단계: 배포 확인하기

### Actions 탭에서 진행상황 보기

1. GitHub 저장소 페이지로 이동
2. **Actions** 탭 클릭
3. 실행 중인 워크플로우 확인:
   - 🟡 노란색 점: 진행 중
   - ✅ 초록색 체크: 성공!
   - ❌ 빨간색 X: 실패 (아래 문제 해결 참고)

### 웹사이트 접속

성공했다면:

```
https://<내GitHub아이디>.github.io/intro/
```

**축하합니다!** 이제 코드를 수정하고 `git push`만 하면 자동으로 배포됩니다!

## 5단계: 자동 배포 테스트

정말로 자동으로 배포되는지 확인해봅시다!

```bash
# 1. index.html 파일 수정
code index.html
# → 이름이나 소개 내용을 조금 바꿔보세요

# 2. 변경사항 저장 및 업로드
git add .
git commit -m "소개 내용 수정"
git push

# 3. Actions 탭에서 자동 배포 확인
# 4. 1-2분 후 웹사이트에서 변경사항 확인
```

## 문제 해결

### ❌ 워크플로우가 실패했어요

**Actions 탭에서 에러 확인:**
1. Actions 탭 → 실패한 워크플로우 클릭
2. 빨간색 X가 있는 단계 클릭
3. 에러 메시지 읽기

**자주 발생하는 문제:**

#### "Error: No such file or directory"
```bash
# 해결: 파일 경로 확인
ls -la .github/workflows/
# pages.yml 파일이 있는지 확인
```

#### "Permission denied"
```bash
# 해결: Settings > Pages에서 Source가 GitHub Actions인지 확인
```

#### "pages.yml: Invalid YAML"
```yaml
# 들여쓰기를 정확히 맞추세요!
# YAML은 공백(스페이스)에 민감합니다
# 탭(Tab) 대신 스페이스 2개를 사용하세요
```

### 🌐 404 에러가 나요

**가능한 원인:**

1. **아직 배포 중**: 1-2분 기다려보세요
2. **URL이 틀렸어요**:
   - ❌ `https://github.com/아이디/intro`
   - ✅ `https://아이디.github.io/intro/`
3. **저장소가 Private**: Public으로 변경하세요
   - Settings → General → Danger Zone → Change visibility

### 🔄 변경사항이 반영 안 돼요

```bash
# 1. 브라우저 캐시 삭제
Ctrl + Shift + R (Windows)
Cmd + Shift + R (Mac)

# 2. Actions에서 배포 완료 확인
# → 초록색 체크 표시가 있어야 합니다

# 3. 시크릿 모드로 접속해보기
Ctrl + Shift + N (Windows)
Cmd + Shift + N (Mac)
```

## 배운 내용 정리

✅ GitHub Actions는 자동화 도구입니다
✅ `.github/workflows/` 폴더에 워크플로우 파일을 만듭니다
✅ `git push`만 하면 자동으로 배포됩니다
✅ Actions 탭에서 진행상황을 볼 수 있습니다

## 다음 단계

이제 자동 배포를 마스터했으니:

1. **더 배우기**: [VS Code Copilot Chat](vscodechat.md)으로 코딩 효율 높이기
2. **프로젝트 확장**: 블로그, 포트폴리오 추가
3. **고급 기능**: 테스트 자동화, 코드 품질 검사 추가

**참고 자료:**
- [GitHub Actions 공식 문서](https://docs.github.com/actions)
- [GitHub Pages 가이드](https://docs.github.com/pages)
- [YAML 문법 배우기](https://yaml.org/)