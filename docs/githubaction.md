# GitHub Actions로 쉽게 배포하기

이 문서에서는 GitHub Actions를 사용하여 개인 소개 페이지를 GitHub Pages에 배포하는 방법을 설명합니다. GitHub Actions를 활용하면 코드 변경 사항을 자동으로 배포할 수 있어 매우 편리합니다.

## 1. GitHub Actions 설정

GitHub Actions를 사용하기 위해서는 먼저 워크플로우 파일을 설정해야 합니다. 이 파일은 `.github/workflows/pages.yml`에 위치해야 하며, 다음과 같은 내용을 포함해야 합니다:

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

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'     # index.html이 리포 루트에 있는 경우

      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

## 2. Pages 권한 설정

1. GitHub 저장소로 이동합니다.
2. **Settings** 탭을 클릭합니다.
3. **Pages** 섹션으로 이동합니다.
4. "Source"를 **GitHub Actions**로 설정합니다.

## 3. 커밋 및 배포

변경 사항을 커밋하고 푸시하면 GitHub Actions가 자동으로 실행되어 페이지가 배포됩니다. 다음 명령어를 사용하여 커밋하고 푸시할 수 있습니다:

```bash
git add .
git commit -m "Deploying personal intro page"
git push origin main
```

## 4. 배포 확인

배포가 완료되면, 일반적으로 다음 URL에서 페이지를 확인할 수 있습니다:

```
https://<username>.github.io/<repo>/
```

리포 이름이 `<username>.github.io`인 경우, 루트 도메인으로 열립니다.

## 5. 트러블슈팅

- **404 오류**: 배포 후 1~2분 정도 캐시 전파 시간이 있을 수 있습니다. 리포가 private이면 Pages 권한 및 가시성을 확인하세요.
- **워크플로우 권한 오류**: 위 예시에서 `permissions: pages: write, id-token: write`가 꼭 필요합니다.

이 문서를 통해 GitHub Actions를 설정하고 개인 소개 페이지를 쉽게 배포할 수 있습니다.