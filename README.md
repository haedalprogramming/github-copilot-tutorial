# 🎨 나만의 자기소개 페이지 만들기

코딩을 처음 배우는 분들도 **5분 만에** 멋진 자기소개 페이지를 만들 수 있습니다!  
GitHub Pages로 무료 호스팅까지 자동으로 됩니다. 🚀

## ✨ 특징

- ✅ **초보자 친화적**: 코딩 경험이 없어도 OK!
- ✅ **즉시 사용 가능**: 텍스트만 바꾸면 완성
- ✅ **반응형 디자인**: 모바일, 태블릿, PC 모두 지원
- ✅ **무료 호스팅**: GitHub Pages 자동 배포
- ✅ **빠른 로딩**: 가볍고 심플한 구조

---

## 🚀 5분 만에 시작하기

### 1️⃣ 이 레포를 내 것으로 만들기

1. 이 페이지 오른쪽 위의 **"Use this template"** 버튼 클릭
2. **"Create a new repository"** 선택
3. Repository name을 `{이름}-profile` 형식으로 입력 (예: `kangmin-profile`)
4. **Public**으로 설정
5. **"Create repository"** 클릭

### 2️⃣ 내 정보로 바꾸기

1. 생성한 레포지토리에서 **`index.html`** 파일 클릭
2. 📝 **Edit**(연필 아이콘) 클릭
3. 아래 부분을 **내 정보**로 수정:

```html
<!-- 이름 변경 -->
<h1>홍길동</h1> 
→ <h1>내 이름</h1>

<!-- 직업/위치 변경 -->
<div class="role">백엔드 개발자 · 서울</div>
→ <div class="role">학생 · 서울</div>

<!-- 자기소개 변경 -->
<p>문제를 단순하게 풀어내는 걸 좋아합니다...</p>
→ <p>내 소개글 작성...</p>

<!-- About 섹션 변경 -->
<p>…간단한 자기소개를 적어주세요…</p>
→ <p>내가 누구인지, 무엇을 좋아하는지 자유롭게 작성...</p>

<!-- Skills 변경 -->
<span class="badge">Go</span> 
→ <span class="badge">Python</span>

<!-- 연락처 변경 -->
<a href="mailto:you@example.com">you@example.com</a>
→ <a href="mailto:내이메일@gmail.com">내이메일@gmail.com</a>
```

4. 페이지 아래의 **"Commit changes"** 버튼 클릭
5. 커밋 메시지 입력 후 **"Commit changes"** 클릭

### 3️⃣ GitHub Pages 활성화

1. 레포지토리의 **Settings** 탭 클릭
2. 왼쪽 메뉴에서 **Pages** 클릭
3. **Source**를 **"GitHub Actions"**로 설정
4. 잠시 기다리면 자동으로 배포됩니다! ⏱️

### 4️⃣ 내 페이지 확인하기

약 1~2분 후, 아래 주소로 접속:
```
https://{내깃헙아이디}.github.io/{레포이름}/
```

**예시**: `https://kangminchoi.github.io/kangmin-profile/`

---

## 🎨 더 꾸미고 싶다면?

### 🌈 색상 바꾸기

`index.html`의 `<style>` 부분에서 색상 코드를 변경하세요:

```css
/* 예: 헤더에 그라데이션 배경 추가 */
header { 
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 80px 20px;
}
```

### 📸 프로필 사진 추가하기

1. `assets` 폴더에 프로필 이미지 업로드 (예: `profile.jpg`)
2. `index.html`의 `<header>` 부분에 추가:

```html
<header>
  <img src="assets/profile.jpg" alt="프로필 사진" 
       style="width:150px; height:150px; border-radius:50%; object-fit:cover; margin-bottom:20px;">
  <h1>내 이름</h1>
  ...
</header>
```

### ➕ 프로젝트/경력 섹션 추가하기

`<main>` 태그 안에 새 섹션 추가:

```html
<section>
  <h2>프로젝트</h2>
  <ul style="list-style: none; padding: 0;">
    <li style="margin-bottom: 16px;">
      <strong>프로젝트 이름</strong> - <a href="링크">GitHub</a>
      <p style="margin: 4px 0 0;">프로젝트 설명을 간단히 작성</p>
    </li>
  </ul>
</section>
```

### 🌙 다크 모드 추가하기

더 많은 예제는 [`examples/`](examples/) 폴더를 확인하세요!

---

## 📚 더 알아보기

### 🎓 코딩을 배우고 싶다면?

- [HTML 기초 배우기](https://developer.mozilla.org/ko/docs/Learn/HTML)
- [CSS 기초 배우기](https://developer.mozilla.org/ko/docs/Learn/CSS)
- [GitHub Pages 공식 문서](https://pages.github.com/)

### 💬 도움이 필요하신가요?

- 질문은 [Issues](../../issues)에 남겨주세요
- 더 많은 예제는 [`examples/`](examples/) 폴더를 확인하세요

---

## 🤝 기여하기

더 나은 템플릿을 위한 아이디어나 개선사항이 있다면 언제든지 PR을 보내주세요!

## 📄 라이센스

MIT License - 자유롭게 사용하세요!

---

<div align="center">
  
### 🌟 만든 페이지가 마음에 드시나요?
  
이 레포에 **Star**⭐를 눌러주세요!  
여러분의 멋진 페이지를 [Show and tell](../../discussions)에서 공유해주세요! 🎉

</div>
