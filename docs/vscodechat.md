# VS Code Copilot Chat 완벽 가이드

VS Code의 Copilot Chat은 단순한 질의응답을 넘어, 코딩 작업을 효율적으로 도와주는 강력한 도구입니다. 이 문서에서는 세 가지 핵심 기능을 배웁니다.

## 시작하기 전에

### VS Code에서 Copilot Chat 열기

1. **방법 1**: `Ctrl + Shift + I` (Windows) 또는 `Cmd + Shift + I` (Mac)
2. **방법 2**: 왼쪽 사이드바의 채팅 아이콘 클릭
3. **방법 3**: 코드 선택 후 `Ctrl + I` (인라인 채팅)

## 세 가지 핵심 기능

---

## 1. Agents (`@`) - 전문가 지정하기

### 무엇인가요?

`@` 기호를 사용해서 Copilot에게 "어떤 정보를 참고해야 할지" 알려주는 기능입니다. 마치 특정 분야 전문가에게 질문하는 것과 같습니다.

### 주요 Agents

#### `@workspace` - 프로젝트 전문가 (가장 중요!)

**내 프로젝트 전체 코드를 이해하고 있는 전문가**

```
사용 예시:
@workspace 이 프로젝트에서 사용자 인증은 어떻게 구현되어 있어?
@workspace UserService 클래스를 참고해서 ProductService 만들어줘
@workspace API_KEY가 하드코딩된 곳을 모두 찾아줘
```

**언제 사용하나요?**
- 새로운 기능을 추가할 때 (기존 코드 스타일 유지)
- 프로젝트 전체에서 무언가를 찾을 때
- 기존 코드를 참고해서 비슷한 코드를 작성할 때

#### `@vscode` - VS Code 설정 전문가

**VS Code 에디터 자체를 제어하는 전문가**

```
사용 예시:
@vscode 키보드 단축키 설정 파일 열어줘
@vscode Python 확장 프로그램 추천해줘
@vscode 현재 테마를 'Monokai'로 변경해줘
```

**언제 사용하나요?**
- VS Code 설정을 변경하고 싶을 때
- 확장 프로그램을 찾을 때
- 에디터 기능에 대해 물어볼 때

#### `@terminal` - 터미널 명령어 전문가

**셸 명령어와 터미널 작업의 전문가**

```
사용 예시:
@terminal node_modules 폴더 용량 확인하는 명령어 알려줘
@terminal 마지막 git commit 취소하는 방법 알려줘
@terminal 현재 폴더에서 .log 파일 모두 삭제하는 명령어
```

**언제 사용하나요?**
- 터미널 명령어가 기억나지 않을 때
- 복잡한 셸 명령어를 만들어야 할 때

---

## 2. 일반 질문 - 개념 학습하기

### 무엇인가요?

Agent 없이 그냥 질문하는 기본 모드입니다. 일반적인 프로그래밍 지식이나 개념을 배울 때 사용합니다.

### 사용 방법

채팅창에 질문만 입력하면 됩니다. (명시적으로 `/ask`를 붙일 수도 있지만 필수는 아닙니다)

```
사용 예시:
JavaScript에서 Promise.all과 Promise.race의 차이점이 뭐야?
React의 useEffect 훅에 대해 설명해줘
Python으로 간단한 웹 스크래퍼 예제 코드 만들어줘
```

### 언제 사용하나요?

- 새로운 개념을 배우고 싶을 때
- 간단한 예제 코드가 필요할 때
- 프로그래밍 언어의 기능을 물어볼 때
- **현재 프로젝트와 관련 없는** 일반적인 질문

### Agent 질문과의 차이

```
일반 질문:
"사용자 인증은 어떻게 구현해?"
→ 일반적인 인증 방법 설명

@workspace를 사용한 질문:
"@workspace 사용자 인증은 어떻게 구현해?"
→ 내 프로젝트에서 실제로 구현된 방법 설명
```

---

## 3. Edit (인라인 수정) - 코드 바로 수정하기

### 무엇인가요?

**가장 생산적인 기능!** 코드를 선택하고 바로 수정 지시를 내릴 수 있습니다.

### 사용 방법

1. 수정하고 싶은 코드를 **마우스로 선택**
2. **`Ctrl + I`** (Windows) 또는 **`Cmd + I`** (Mac) 누르기
3. 인라인 채팅창에 수정 지시 입력
4. `Enter` 누르기
5. 미리보기 확인 후 `Accept` 또는 `Discard`

### 실전 예시

#### 예시 1: 주석 추가하기

```javascript
// 원본 코드 (선택 후 Ctrl+I)
function calculateTotal(items) {
  return items.reduce((sum, item) => sum + item.price, 0);
}

// 인라인 채팅에 입력: "JSDoc 주석 추가해줘"

// 결과:
/**
 * 아이템 배열의 총 가격을 계산합니다
 * @param {Array} items - 가격 정보를 가진 아이템 배열
 * @returns {number} 총 가격
 */
function calculateTotal(items) {
  return items.reduce((sum, item) => sum + item.price, 0);
}
```

#### 예시 2: 리팩토링

```javascript
// 원본 코드 (선택 후 Ctrl+I)
const result = [];
for (let i = 0; i < users.length; i++) {
  if (users[i].age >= 18) {
    result.push(users[i].name);
  }
}

// 인라인 채팅: "filter와 map으로 리팩토링해줘"

// 결과:
const result = users
  .filter(user => user.age >= 18)
  .map(user => user.name);
```

#### 예시 3: 에러 처리 추가

```javascript
// 원본 (선택 후 Ctrl+I)
async function fetchUser(id) {
  const response = await fetch(`/api/users/${id}`);
  return response.json();
}

// 인라인 채팅: "try-catch 에러 처리 추가해줘"

// 결과:
async function fetchUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return await response.json();
  } catch (error) {
    console.error('Failed to fetch user:', error);
    throw error;
  }
}
```

### 언제 사용하나요?

- 함수에 주석을 추가하고 싶을 때
- 코드를 리팩토링하고 싶을 때
- 에러 처리를 추가하고 싶을 때
- 변수명을 더 명확하게 바꾸고 싶을 때
- 코드를 더 읽기 쉽게 만들고 싶을 때

---

## 빠른 참고표

| 기능 | 사용법 | 추천 상황 | 예시 |
|------|--------|-----------|------|
| **@workspace** | `@workspace` + 질문 | 내 프로젝트 관련 질문 | `@workspace` 인증 로직 어디 있어? |
| **@vscode** | `@vscode` + 질문 | VS Code 설정 | `@vscode` 단축키 설정 열어줘 |
| **@terminal** | `@terminal` + 질문 | 터미널 명령어 | `@terminal` git 브랜치 삭제 명령어 |
| **일반 질문** | 그냥 질문 | 개념 학습 | Promise 설명해줘 |
| **인라인 수정** | 코드 선택 + `Ctrl+I` | 코드 수정 | 주석 추가해줘 |

---

## 실습: 함께 해보기

### 실습 1: @workspace 사용하기

1. VS Code에서 프로젝트를 엽니다
2. Copilot Chat을 엽니다 (`Ctrl + Shift + I`)
3. 다음을 입력해보세요:
   ```
   @workspace 이 프로젝트의 구조를 설명해줘
   ```

### 실습 2: 인라인 수정 사용하기

1. 아무 JavaScript 파일을 엽니다
2. 함수 하나를 선택합니다
3. `Ctrl + I`를 누릅니다
4. "JSDoc 주석 추가해줘"를 입력합니다
5. 결과를 확인하고 Accept 클릭

### 실습 3: 터미널 명령어 찾기

1. Copilot Chat에서:
   ```
   @terminal 현재 폴더에서 가장 큰 파일 5개 찾는 명령어
   ```
2. 제안된 명령어를 터미널에서 실행해보세요

---

## 효율적인 워크플로우

### 새 기능 개발

```
1. @workspace를 사용해 프로젝트 이해
   "@workspace 로그인 기능은 어떻게 구현되어 있어?"

2. 일반 질문으로 개념 학습
   "OAuth 2.0에 대해 설명해줘"

3. 코드 작성

4. 인라인 수정으로 코드 개선
   코드 선택 → Ctrl+I → "주석과 에러 처리 추가해줘"
```

### 버그 수정

```
1. @workspace로 관련 코드 찾기
   "@workspace 사용자 등록 관련 코드 찾아줘"

2. 인라인 수정으로 버그 수정
   버그 코드 선택 → Ctrl+I → "null 체크 추가해줘"
```

### 학습

```
1. 일반 질문으로 개념 학습
   "React hooks의 useCallback과 useMemo 차이점?"

2. 예제 코드 요청
   "useCallback 사용 예제 보여줘"

3. 내 프로젝트에 적용
   "@workspace 이 컴포넌트에 useMemo 적용해줘"
```

---

## 팁과 트릭

### 구체적으로 질문하기

```
❌ 나쁜 예: "코드 고쳐줘"
✅ 좋은 예: "이 함수에 입력값 검증과 에러 처리를 추가해줘"
```

### 단계별로 진행하기

```
복잡한 작업은 한 번에 하지 말고:
1. "먼저 기본 구조만 만들어줘"
2. "이제 에러 처리 추가해줘"
3. "마지막으로 주석 추가해줘"
```

### Agent 조합하기

```
@workspace @terminal 이 프로젝트를 빌드하는 명령어 알려줘
```

---

## 다음 단계

이제 VS Code Copilot Chat을 활용할 준비가 되었습니다!

1. **연습하기**: 실제 프로젝트에서 사용해보세요
2. **더 배우기**: [GitHub Copilot 시작하기](whatisghcopilot.md)
3. **프로젝트 만들기**: [자기소개 페이지 만들기](createintro.md)

**참고 자료:**
- [GitHub Copilot 공식 문서](https://docs.github.com/copilot)
- [VS Code Copilot 가이드](https://code.visualstudio.com/docs/copilot)