# ⚡ 빠른 시작 가이드

이 가이드는 코딩이 처음인 분들을 위한 단계별 설명입니다.

## 📝 사전 준비

시작하기 전에 필요한 것:
- ✅ GitHub 계정 (없다면 [github.com](https://github.com)에서 무료 가입)
- ✅ 인터넷 브라우저
- ✅ 5분의 시간!

## 🎯 단계별 가이드

### 1단계: 템플릿 복사하기

1. 이 페이지 상단 오른쪽의 **녹색 "Use this template"** 버튼을 클릭
2. **"Create a new repository"**를 선택
3. 새 레포지토리 정보 입력:
   - **Repository name**: `내이름-profile` (예: `gildong-profile`)
   - **Public** 선택 (무료로 GitHub Pages를 사용하려면 Public이어야 합니다)
   - **"Create repository"** 버튼 클릭

### 2단계: 내 정보 입력하기

1. 방금 만든 레포지토리에서 **`index.html`** 파일 클릭
2. 오른쪽 위의 ✏️ **연필 아이콘(Edit this file)** 클릭
3. 아래 부분을 찾아서 **내 정보로 변경**:

#### 🏷️ 이름 변경 (8번째 줄 근처)
```html
<!-- 변경 전 -->
<h1>홍길동</h1>

<!-- 변경 후 -->
<h1>김철수</h1>  ← 내 이름 입력
```

#### 📍 역할과 위치 변경 (11번째 줄 근처)
```html
<!-- 변경 전 -->
<div class="role">백엔드 개발자 · 서울</div>

<!-- 변경 후 -->
<div class="role">대학생 · 부산</div>  ← 내 상태와 위치 입력
```

#### 💬 한 줄 소개 변경 (14번째 줄 근처)
```html
<!-- 변경 전 -->
<p class="intro">
  문제를 단순하게 풀어내는 걸 좋아합니다...
</p>

<!-- 변경 후 -->
<p class="intro">
  코딩을 배우고 있는 대학생입니다. 열심히 공부하고 있어요!
</p>
```

#### 📖 About 섹션 변경 (85번째 줄 근처)
```html
<!-- 자기소개를 자유롭게 작성하세요 -->
<p>
  안녕하세요! 저는 컴퓨터과학을 전공하는 학생입니다.<br>
  프로그래밍에 관심이 많고, 특히 웹 개발을 공부하고 있습니다.
</p>
```

#### 🛠 Skills 변경 (92번째 줄 근처)
```html
<!-- 자신이 할 수 있는 기술이나 배우고 있는 기술을 나열하세요 -->
<span class="badge">Python</span>
<span class="badge">HTML</span>
<span class="badge">CSS</span>
```

**더 추가하고 싶다면:**
```html
<span class="badge">새로운기술</span>
```

#### 📧 연락처 변경 (100번째 줄 근처)
```html
<!-- 내 이메일과 링크로 변경 -->
<p>📧 이메일: <a href="mailto:myemail@gmail.com">myemail@gmail.com</a></p>
<p>🐙 GitHub: <a href="https://github.com/mygithub" target="_blank">github.com/mygithub</a></p>
```

4. 수정이 끝나면 페이지 아래로 스크롤
5. **"Commit changes"** 버튼 클릭
6. 팝업창에서 다시 **"Commit changes"** 클릭

### 3단계: GitHub Pages 활성화하기

1. 레포지토리 상단의 **"Settings"** 탭 클릭
2. 왼쪽 메뉴에서 **"Pages"** 클릭
3. **"Source"** 부분에서:
   - **"GitHub Actions"** 선택
4. 자동으로 배포가 시작됩니다! 🚀

### 4단계: 내 페이지 확인하기

1. **1~2분** 정도 기다립니다
2. 브라우저에서 다음 주소로 접속:
   ```
   https://내깃헙아이디.github.io/레포이름/
   ```
   
   **예시:**
   - GitHub 아이디: `gildong`
   - 레포이름: `gildong-profile`
   - 주소: `https://gildong.github.io/gildong-profile/`

3. 🎉 **완성!** 내 자기소개 페이지가 나타납니다!

---

## ❓ 자주 묻는 질문

### Q: 페이지가 안 보여요!
**A:** 다음을 확인해보세요:
1. Settings → Pages에서 GitHub Actions가 선택되어 있나요?
2. 1-2분 정도 기다렸나요? (첫 배포는 시간이 걸립니다)
3. 주소를 정확히 입력했나요?

### Q: 수정한 내용이 반영이 안 돼요!
**A:** 
1. 파일을 수정한 후 **"Commit changes"**를 클릭했나요?
2. 1-2분 정도 기다린 후 페이지를 **새로고침**(Ctrl+F5 또는 Cmd+Shift+R)하세요

### Q: 사진을 추가하고 싶어요!
**A:** [README.md](README.md)의 "🎨 더 꾸미고 싶다면?" 섹션을 참고하세요!

### Q: 색상을 바꾸고 싶어요!
**A:** [README.md](README.md)의 "색상 변경" 부분을 참고하세요!

---

## 🎨 다음 단계

기본 페이지를 만들었다면:
- 📸 [프로필 사진 추가하기](README.md#-프로필-사진-추가하기)
- 🎨 [색상과 디자인 커스터마이징](README.md#-색상-바꾸기)
- 📂 [프로젝트 섹션 추가하기](README.md#-프로젝트-섹션-추가하기)

---

## 💬 도움이 필요하신가요?

- 💡 질문이 있다면 [Issues](../../issues)에 남겨주세요
- 📚 HTML/CSS 기초를 배우고 싶다면 [MDN 웹 문서](https://developer.mozilla.org/ko/)를 추천합니다
- 🌟 도움이 되었다면 이 레포지토리에 Star를 눌러주세요!
