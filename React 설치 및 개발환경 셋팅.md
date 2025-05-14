## 📌 오늘 배운 내용
- React 설치 및 개발환경 셋팅
   
## 1. Node.js 설치
- 구글에 **Node.js** 검색 후 LTS 버전 설치  
- M1 맥북 또는 ARM CPU 사용 시 **ARM64 버전** 선택  
- 설치 중 **chocolatey 관련 항목은 설치하지 않아도 됨**

---

## 2. Visual Studio Code 설치
- 구글에 "Visual Studio Code" 검색 후 설치

---

## 3. 작업 폴더 생성
- **한글 이름 ❌**, **OneDrive 등의 클라우드 폴더 ❌**  
- 가능한 로컬 드라이브에 **영문 이름의 폴더 생성**

---

## 4. React 프로젝트 생성 (Vite 사용)

### ✅ Windows
- 작업 폴더 내에서 `Shift + 우클릭 → PowerShell 열기`

### ✅ macOS
- 폴더 내에서 **두 손가락 클릭 → 터미널 열기**

### 📦 명령어 실행

 ```bash
  npm create vite@latest
```
- 프로젝트 이름 입력
- 템플릿 선택 시: React 선택
- 추가 질문은 대부분 No 선택

### 설치된 파일 설명
| 항목               | 설명 |
|--------------------|------|
| `node_modules/`     | 설치된 라이브러리들의 소스코드가 들어있는 폴더 |
| `public/`           | 이미지, 데이터 등 정적 파일 보관 (사이트 배포 시 원본 유지 가능) |
| `package.json`      | 프로젝트에 설치된 라이브러리와 명령어 정보가 기록된 파일 |
| `.config.js` 등     | `lint`, `vite` 등 각종 설정 파일 |
| `index.html`        | 실제 HTML 메인 페이지. 이 안에 `main.js`가 연결되어 있고, `main.js` 안에서 `App.jsx`를 불러와 렌더링 |

---

