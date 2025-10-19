# GitHub Copilot이란?

GitHub Copilot은 AI 기반의 코드 보조 도구로, 개발자가 코드를 작성할 때 실시간으로 코드 제안 및 자동 완성을 제공합니다. GitHub와 OpenAI의 협력으로 개발된 이 도구는 다양한 프로그래밍 언어와 프레임워크를 지원하며, 개발자의 생산성을 크게 향상시킬 수 있습니다.

## 주요 기능

1. **코드 자동 완성**: 사용자가 입력하는 코드에 따라 적절한 코드를 자동으로 제안합니다.
2. **문서화 지원**: 함수나 클래스에 대한 설명을 자동으로 생성하여 코드의 가독성을 높입니다.
3. **다양한 언어 지원**: JavaScript, Python, TypeScript, Ruby 등 여러 프로그래밍 언어에서 사용할 수 있습니다.
4. **컨텍스트 인식**: 현재 작성 중인 코드의 맥락을 이해하고, 그에 맞는 제안을 제공합니다.
5. **커스터마이징**: 사용자가 선호하는 스타일이나 패턴에 맞춰 제안을 조정할 수 있습니다.

## GitHub Copilot CLI

GitHub Copilot CLI는 GitHub Copilot의 기능을 커맨드 라인에서 사용할 수 있도록 해주는 도구입니다. 이를 통해 개발자는 터미널에서 직접 명령어를 입력하고, 필요한 코드 스니펫이나 쉘 명령을 쉽게 생성할 수 있습니다. GitHub Copilot CLI를 사용하면 프로젝트의 초기 설정, 코드 작성, 배포 과정 등을 더욱 효율적으로 진행할 수 있습니다.

### 설치 방법

```bash
# GitHub CLI가 설치되어 있어야 합니다
gh extension install github/gh-copilot

# 설치 확인
gh copilot --version
```

### 주요 명령어

GitHub Copilot CLI는 세 가지 주요 명령어를 제공합니다:

#### 1. `gh copilot suggest` - 쉘 명령어 제안

자연어로 원하는 작업을 설명하면 적절한 쉘 명령어를 제안합니다.

```bash
# 예제 1: 파일 찾기
gh copilot suggest "find all .js files modified in the last 7 days"

# 예제 2: Git 작업
gh copilot suggest "git에서 마지막 3개의 커밋 취소하기"

# 예제 3: 시스템 정보
gh copilot suggest "디스크 사용량을 용량 순으로 정렬해서 보여줘"
```

#### 2. `gh copilot explain` - 명령어 설명

복잡한 쉘 명령어나 코드를 이해하기 쉽게 설명합니다.

```bash
# 예제 1: 복잡한 파이프라인 설명
gh copilot explain "find . -name '*.log' | xargs grep -i error | sort | uniq -c"

# 예제 2: Git 명령어 설명
gh copilot explain "git rebase -i HEAD~3"

# 예제 3: Docker 명령어 설명
gh copilot explain "docker run -d -p 8080:80 -v $(pwd):/app nginx"
```

#### 3. `gh copilot chat` - 대화형 모드

대화형 방식으로 지속적인 질문과 답변이 가능합니다.

```bash
# 대화형 모드 시작
gh copilot chat

# 채팅 예제:
# > AWS S3에 파일을 업로드하는 방법 알려줘
# > 위 명령어에서 권한 설정은 어떻게 해?
# > 여러 파일을 한번에 업로드하려면?
```

## 실제 사용 예제

### 예제 1: 프로젝트 초기화

```bash
# Node.js 프로젝트 설정 명령어 얻기
gh copilot suggest "create a new Node.js project with TypeScript and ESLint"

# 제안된 명령어 예시:
# mkdir my-project && cd my-project
# npm init -y
# npm install --save-dev typescript @types/node eslint
# npx tsc --init
```

### 예제 2: Git 작업 자동화

```bash
# 브랜치 정리 명령어
gh copilot suggest "delete all local git branches except main and develop"

# 제안된 명령어:
# git branch | grep -v "main\|develop" | xargs git branch -D
```

### 예제 3: 파일 작업

```bash
# 대용량 파일 찾기
gh copilot suggest "find files larger than 100MB in current directory"

# 제안된 명령어:
# find . -type f -size +100M
```

### 예제 4: Docker 작업

```bash
# Docker 컨테이너 정리
gh copilot suggest "stop and remove all Docker containers"

# 제안된 명령어:
# docker stop $(docker ps -aq) && docker rm $(docker ps -aq)
```

### 예제 5: 시스템 모니터링

```bash
# 프로세스 모니터링
gh copilot suggest "show top 10 processes by memory usage"

# 제안된 명령어 (Mac):
# ps aux | sort -nrk 4 | head -10
```

## 팁과 트릭

1. **명확한 요청하기**: 가능한 구체적으로 원하는 작업을 설명하세요.
   ```bash
   # ❌ 나쁜 예: "파일 찾기"
   # ✅ 좋은 예: "지난 주에 수정된 모든 Python 파일 찾기"
   ```

2. **한국어 지원**: 한국어로도 명령어를 요청할 수 있습니다.
   ```bash
   gh copilot suggest "현재 폴더의 모든 파일을 날짜순으로 정렬해서 보여줘"
   ```

3. **대화형 모드 활용**: 복잡한 작업은 `chat` 모드에서 단계별로 진행하세요.

4. **설명 먼저 읽기**: 제안된 명령어를 실행하기 전에 `explain`으로 확인하세요.

## 사용 사례

- **프로젝트 초기화**: 새로운 프로젝트를 시작할 때 필요한 기본 파일 및 구조를 자동으로 생성합니다.
- **코드 스니펫 생성**: 특정 기능을 구현하기 위한 코드 조각을 빠르게 생성합니다.
- **문서화**: 코드에 대한 설명이나 주석을 자동으로 추가하여 문서화를 간소화합니다.
- **쉘 명령어 학습**: 복잡한 쉘 명령어를 이해하고 학습하는 데 도움을 받습니다.
- **작업 자동화**: 반복적인 터미널 작업을 빠르게 명령어로 변환합니다.

GitHub Copilot과 GitHub Copilot CLI를 활용하면 개발자는 반복적인 작업에서 벗어나 더 창의적이고 복잡한 문제 해결에 집중할 수 있습니다.

## GitHub Copilot CLI로 변경사항 업로드하기

GitHub Copilot CLI를 활용해서 변경사항을 GitHub에 업로드하는 방법입니다.

### 방법 1: `gh copilot suggest` 사용

터미널에서 자연어로 요청하세요:

```bash
# 1. Git 커밋 명령어 얻기
gh copilot suggest "git에 모든 변경사항을 추가하고 'docs: Add CLI examples' 메시지로 커밋하기"

# 제안된 명령어 실행:
# git add .
# git commit -m "docs: Add CLI examples"

# 2. 푸시 명령어 얻기
gh copilot suggest "변경사항을 main 브랜치에 푸시하기"

# 제안된 명령어 실행:
# git push origin main
```

### 방법 2: `gh copilot chat` 대화형 모드 사용

```bash
# 대화형 모드 시작
gh copilot chat

# 대화 예시:
# > 현재 폴더의 변경사항을 GitHub에 업로드하고 싶어
# Copilot이 단계별로 안내해줍니다:
# 1. git add .
# 2. git commit -m "your message"
# 3. git push

# > 커밋 메시지는 "docs: Add CLI examples"로 하고 싶어
# 구체적인 명령어를 제공해줍니다
```

### 방법 3: 학습한 내용 직접 적용

```bash
# 1. 변경사항 확인
git status

# 2. 모든 파일 스테이징
git add .

# 3. 커밋
git commit -m "docs: Add GitHub Copilot CLI examples and usage tips"

# 4. 푸시
git push origin main
```

### 복잡한 Git 작업 예제

```bash
# 특정 파일만 커밋하고 싶을 때
gh copilot suggest "docs 폴더의 변경사항만 커밋하기"

# 커밋 메시지 컨벤션 확인
gh copilot suggest "conventional commits 형식으로 문서 추가 커밋 메시지 만들기"

# 푸시 전에 리모트 확인
gh copilot suggest "git 리모트 저장소 주소 확인하기"

# 특정 브랜치로 푸시
gh copilot suggest "새로운 feature 브랜치를 만들고 푸시하기"
```

## 다음 단계

- [VS Code Copilot Chat 활용하기](vscodechat.md)
- [자기소개 페이지 만들기](createintro.md)
- [GitHub Actions로 배포하기](githubaction.md)

