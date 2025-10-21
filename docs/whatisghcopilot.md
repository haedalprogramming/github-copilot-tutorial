# GitHub Copilot 시작하기

## GitHub Copilot이란?

GitHub Copilot은 AI가 코드 작성을 도와주는 도구입니다. 마치 옆에서 선배 개발자가 도와주는 것처럼, 여러분이 작성하는 코드를 이해하고 다음에 작성할 코드를 제안해줍니다.

### 왜 사용해야 할까요?

- **빠른 학습**: 코드 작성 중 실시간으로 예제를 보여줘서 새로운 것을 배우기 좋습니다
- **시간 절약**: 반복적인 코드 작성을 자동화하여 더 중요한 문제에 집중할 수 있습니다
- **오류 감소**: 자주 발생하는 실수를 방지할 수 있습니다

## 어디서 사용하나요?

1. **VS Code**: 코드 에디터에서 자동 완성 (가장 많이 사용)
2. **CLI (Command Line)**: 터미널에서 명령어 도움 받기

이 튜토리얼에서는 **CLI 사용법**을 중심으로 설명합니다.

## GitHub Copilot CLI란?

터미널에서 "이런 걸 하고 싶은데..."라고 말하면, AI가 적절한 명령어를 알려주는 도구입니다.

**예시:**
- "지난 주에 수정된 파일 찾기" → 실제 명령어 제안
- "Git 커밋 취소하기" → 안전한 방법 알려줌
- "Docker 컨테이너 정리하기" → 필요한 명령어 생성

## 설치하기

### 1단계: GitHub CLI 설치 확인

```bash
# GitHub CLI가 설치되어 있는지 확인
gh --version
```

만약 설치되어 있지 않다면:
- Mac: `brew install gh`
- Windows: [GitHub CLI 다운로드](https://cli.github.com/)

### 2단계: Copilot CLI 설치

```bash
# Copilot CLI 설치
gh extension install github/gh-copilot

# 설치 확인
gh copilot --version
```

### 3단계: GitHub 로그인

```bash
# GitHub 계정으로 로그인
gh auth login
```

## 기본 사용법

GitHub Copilot CLI의 3가지 핵심 명령어:

### 1. `suggest` - 명령어 알려줘!

하고 싶은 작업을 말하면 명령어를 알려줍니다.

```bash
gh copilot suggest "지난 주에 수정된 Python 파일 찾기"
```

**대학생 활용 예시:**
```bash
# 과제 파일 찾기
gh copilot suggest "오늘 수정한 .java 파일 모두 찾기"

# Git 사용법
gh copilot suggest "변경사항 커밋하고 푸시하기"

# 프로젝트 정리
gh copilot suggest "node_modules 폴더 용량 확인하기"
```

### 2. `explain` - 이 명령어가 뭐야?

복잡한 명령어를 쉽게 설명해줍니다.

```bash
gh copilot explain "git rebase -i HEAD~3"
```

**언제 사용하나요?**
- 인터넷에서 찾은 명령어가 무슨 뜻인지 모를 때
- 과제 자료에 나온 명령어를 이해하고 싶을 때
- 팀 프로젝트에서 다른 사람이 쓴 스크립트를 볼 때

### 3. `chat` - 계속 물어보기

대화하듯이 여러 질문을 할 수 있습니다.

```bash
gh copilot chat
```

**채팅 예시:**
```
> Node.js 프로젝트 시작하는 방법 알려줘
> package.json은 뭐야?
> express 설치하는 명령어는?
```

## 실습해보기

### 실습 1: Git 사용하기

```bash
# 1. 현재 상태 확인하는 명령어 물어보기
gh copilot suggest "git 현재 상태 확인하기"

# 2. 변경사항 저장하는 방법 물어보기
gh copilot suggest "모든 변경사항을 커밋하고 푸시하기"
```

### 실습 2: 파일 관리

```bash
# 과제 제출 전 정리
gh copilot suggest "현재 폴더에서 .class 파일 모두 삭제하기"

# 파일 찾기
gh copilot suggest "README로 시작하는 파일 찾기"
```

### 실습 3: 프로젝트 시작

```bash
# Python 프로젝트 시작
gh copilot suggest "Python 가상환경 만들고 활성화하기"

# React 프로젝트 시작
gh copilot suggest "create-react-app으로 새 프로젝트 만들기"
```

## 꿀팁!

1. **구체적으로 물어보세요**
   - ❌ "파일 찾기"
   - ✅ "지난 주에 수정된 모든 Python 파일 찾기"

2. **한국어도 됩니다**
   ```bash
   gh copilot suggest "현재 폴더 파일을 날짜순으로 보여줘"
   ```

3. **모르는 명령어는 explain으로 확인**
   - 안전하게 명령어를 이해하고 사용할 수 있습니다

4. **복잡한 작업은 chat 모드 사용**
   - 단계별로 도움받을 수 있습니다

## 실전: Git으로 과제 제출하기

GitHub에 코드를 업로드하는 과정을 Copilot CLI로 배워봅시다.

### 기본 흐름

```bash
# 1. 어떤 파일이 변경되었는지 확인
gh copilot suggest "git 현재 상태 확인하기"
# → git status 명령어를 알려줍니다

# 2. 변경사항 저장하기
gh copilot suggest "모든 변경사항을 '과제 제출' 메시지로 커밋하기"
# → git add . 와 git commit 명령어를 알려줍니다

# 3. GitHub에 업로드
gh copilot suggest "변경사항을 GitHub에 푸시하기"
# → git push 명령어를 알려줍니다
```

### 대화형 모드로 단계별 배우기

```bash
gh copilot chat
```

채팅 예시:
```
> Git이 처음인데, 코드를 GitHub에 올리는 방법 알려줘
> git add가 뭐야?
> 커밋 메시지는 어떻게 써야 해?
> push가 안 되는데 왜 그럴까?
```

### 자주 하는 실수 해결

```bash
# 커밋 메시지를 잘못 썼을 때
gh copilot suggest "마지막 커밋 메시지 수정하기"

# 파일을 잘못 추가했을 때
gh copilot suggest "git add 취소하기"

# 푸시가 안 될 때
gh copilot suggest "git push가 rejected될 때 해결 방법"
```

## 다음 단계

이제 기본을 배웠으니, 실제로 만들어봅시다!

1. **[자기소개 페이지 만들기](createintro.md)** - Copilot CLI로 나만의 웹사이트 만들기
2. **[GitHub Actions로 배포하기](githubaction.md)** - 자동으로 웹사이트 배포하기
3. **[VS Code Copilot Chat 활용하기](vscodechat.md)** - 코드 에디터에서 AI 활용하기

## 도움이 더 필요하면?

- [GitHub Copilot 공식 문서](https://docs.github.com/copilot)
- [GitHub CLI 문서](https://cli.github.com/manual/)
- 막히는 부분이 있다면 `gh copilot chat`으로 물어보세요!

