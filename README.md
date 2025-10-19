# github-copilot-tutorial
이 레포는 GitHub Copilot CLI를 활용하여 개인 소개 페이지를 만드는 방법을 보여주는 템플릿입니다. 이 템플릿을 사용하여 쉽게 자기소개 페이지를 생성하고 GitHub Pages에 배포할 수 있습니다.

## 목차
1. [GitHub Copilot CLI란?](docs/whatisghcopilot.md)
2. [VS Code Copilot Chat 활용하기](docs/vscodechat.md)
3. [자기소개 페이지 만들기](docs/createintro.md)
4. [GitHub Actions로 배포하기](docs/githubaction.md)
4. [예제](examples/)

## 시작하기

이 레포를 템플릿으로 사용하여 개인 소개 페이지를 만들려면 아래 단계를 따라주세요.

### 1. 레포지토리 생성
GitHub에서 이 레포를 템플릿으로 사용하여 새 레포지토리를 생성합니다.

### 2. 로컬 클론
생성한 레포지토리를 로컬로 클론합니다.
```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

### 3. 필요한 패키지 설치
Node.js와 npm이 설치되어 있는지 확인한 후, 필요한 패키지를 설치합니다.
```bash
npm install
```

### 4. 개인 정보 수정
`index.html` 파일을 열어 본인의 정보로 수정합니다. `assets` 폴더에 있는 이미지 파일도 본인의 이미지로 교체하세요.

### 5. GitHub Actions 설정
`.github/workflows/pages.yml` 파일을 확인하여 GitHub Pages에 배포할 수 있도록 설정합니다. 기본적으로 설정되어 있으므로 추가적인 수정은 필요하지 않습니다.

### 6. 커밋 및 푸시
변경 사항을 커밋하고 원격 레포지토리에 푸시합니다.
```bash
git add .
git commit -m "feat: Update personal information"
git push origin main
```

### 7. GitHub Pages 확인
푸시가 완료되면 GitHub Pages에서 배포된 페이지를 확인할 수 있습니다. 주소는 보통 다음과 같습니다:
```
https://<username>.github.io/<repo-name>/
```

## 예제
이 레포에는 다양한 예제 페이지가 포함되어 있습니다. `examples/` 폴더를 확인하여 기본, 블로그 포함, 다크 모드 기능이 있는 페이지 예제를 살펴보세요.

## 기여
이 프로젝트에 기여하고 싶으신 분은 PR을 보내주세요. 여러분의 기여를 환영합니다!

## 라이센스
이 프로젝트는 MIT 라이센스 하에 배포됩니다.