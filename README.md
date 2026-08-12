# 🎯 승진 심사 모의 면접

### Promotion Interview Simulator

회계법인 **파트너 패널 승진 인터뷰**를 텍스트 또는 음성으로 연습할 수 있는 **싱글 HTML 웹앱**입니다.

프레임워크 의존성 없이 **순수 HTML / CSS / JavaScript**로 작성되어 있으며, 정적 파일 그대로 브라우저에서 실행하거나 **GitHub Pages** 등 다양한 정적 호스팅 환경에 바로 배포할 수 있습니다.

---

## ✨ 주요 기능

### 01. 자료 준비

승진 인터뷰에 필요한 기본 조건과 참고 자료를 입력할 수 있습니다.

* **승진 대상 직급** 설정
* **면접 스타일** 선택

  * 압박형
  * 균형형
  * 코칭형
* **패널 구성** 선택

  * 1인 패널
  * 3인 패널
* **참고 자료 입력**

  * 자기소개서
  * 주요 실적
  * 평가 기준
  * 기타 인터뷰 참고자료
* 텍스트 직접 붙여넣기
* `.txt` / `.md` 파일 업로드 지원

---

### 02. 모의 면접

AI와 실제 승진 인터뷰와 유사한 방식으로 대화를 진행할 수 있습니다.

* 💬 **텍스트 채팅**
* 🎙️ **브라우저 음성 인식**
* 🔊 **AI 질문 음성 출력(TTS)**
* 입력 자료를 기반으로 한 맞춤형 질문
* 선택한 면접 스타일에 따른 질문 방식 조정
* 1인 / 3인 패널 방식 지원

---

### 03. 인터뷰 피드백

면접 종료 후 답변 내용을 바탕으로 구조화된 피드백을 제공합니다.

* ✅ 잘한 점
* ⚠️ 보완할 점
* 📊 종합 평가
* 💡 실전 인터뷰 팁
* 📋 전체 면접 기록 복사

---

# 🚀 실행 방법

별도의 설치 과정 없이 `index.html` 파일을 브라우저에서 열면 바로 사용할 수 있습니다.

```text
index.html
```

로컬 웹서버로 실행하고 싶다면 다음 명령어를 사용할 수 있습니다.

```bash
# 현재 디렉터리에서 간단한 웹서버 실행
python3 -m http.server 8000
```

이후 브라우저에서 다음 주소로 접속합니다.

```text
http://localhost:8000
```

---

# 🤖 AI 모델 및 OpenRouter 연결

이 앱은 **OpenRouter API**를 통해 AI 모델을 호출합니다.

기본적으로 다음 순서로 모델을 사용하도록 구성되어 있습니다.

| 우선순위 | 모델                              | 용도                     |
| ---- | ------------------------------- | ---------------------- |
| 1    | **Upstage: Solar Pro 3 (free)** | 기본 모델                  |
| 2    | **Google: Gemma 4 31B (free)**  | 기본 모델 호출 실패 또는 혼잡 시 대체 |

**Upstage Solar Pro 3**를 우선 사용하고, 해당 모델의 호출이 어렵거나 혼잡한 경우 **Google Gemma 4 31B**로 자동 대체합니다.

Solar Pro 3는 한국어 처리에 강점을 가진 모델이므로 한국어 기반 승진 인터뷰 연습에 우선 활용하도록 구성되어 있습니다.

---

## 🔑 OpenRouter API Key

> [!IMPORTANT]
> 이 앱을 사용하려면 **OpenRouter API Key가 반드시 필요합니다.**

별도의 서버나 백엔드 없이 **사용자의 브라우저에서 OpenRouter API를 직접 호출**하는 구조입니다.

따라서 다음 환경에서도 API Key가 필요합니다.

* 로컬 브라우저 실행
* GitHub Pages
* 기타 Static Hosting
* 브라우저 기반 미리보기 환경

API Key는 화면의 다음 위치에서 입력합니다.

```text
01 자료 준비 → F. OpenRouter API Key
```

키를 입력하면 바로 모의 면접 기능을 사용할 수 있습니다.

---

## API Key 발급

OpenRouter에서 API Key를 발급받을 수 있습니다.

👉 [OpenRouter](https://openrouter.ai)

로그인 후 다음 메뉴에서 생성합니다.

```text
OpenRouter
 └─ Keys
     └─ Create Key
```

무료 모델 이용을 위해 반드시 유료 결제가 필요한 것은 아닙니다.

---

# 📊 무료 모델 사용 제한

OpenRouter의 무료(`:free`) 모델에는 요청 횟수 제한이 적용될 수 있습니다.

예를 들어 무료 모델의 경우 계정 상태에 따라 다음과 같은 제한이 적용될 수 있습니다.

```text
분당 요청 제한
일일 요청 제한
```

개인적인 승진 인터뷰 연습 용도라면 일반적으로 제한 범위 내에서 사용할 수 있습니다.

> [!NOTE]
> OpenRouter의 Rate Limit 정책은 변경될 수 있으므로 실제 적용되는 최신 제한은 OpenRouter 계정 또는 공식 안내를 확인하는 것이 좋습니다.

---

# 🔐 API Key 저장 방식

API Key는 사용자의 브라우저에서 OpenRouter API 호출을 위해 사용됩니다.

`이 브라우저에 저장` 옵션을 활성화하면 브라우저의 `localStorage`에 API Key가 저장됩니다.

따라서 다음 접속 시 다시 입력하지 않아도 됩니다.

```javascript
localStorage
```

> [!WARNING]
> 공용 PC 또는 다른 사람과 함께 사용하는 PC에서는 **API Key 저장 기능 사용을 권장하지 않습니다.**

다음과 같은 환경에서는 저장하지 않는 것이 좋습니다.

* PC방
* 공용 PC
* 공용 업무용 PC
* 여러 사용자가 동일한 브라우저 프로필을 사용하는 환경

---

# 🚨 GitHub 업로드 시 API Key 주의

> [!CAUTION]
> **OpenRouter API Key를 GitHub Repository에 절대로 포함하지 마세요.**

현재 앱은 API Key를 파일이 아닌 브라우저 저장소에 저장하도록 구성할 수 있습니다.

하지만 개발 또는 테스트 과정에서 API Key를 HTML 또는 JavaScript 코드에 직접 입력한 상태로 GitHub에 Commit하지 않도록 주의해야 합니다.

예를 들어 다음과 같은 형태는 사용하지 않는 것이 좋습니다.

```javascript
const API_KEY = "sk-or-v1-xxxxxxxxxxxxxxxxxxxxxxxx";
```

GitHub에 업로드하기 전에 반드시 다음 항목을 확인하세요.

* HTML 파일에 API Key가 포함되어 있지 않은지 확인
* JavaScript에 API Key가 Hard Coding되어 있지 않은지 확인
* 테스트용 API Key 삭제
* Commit History에 API Key가 남아 있지 않은지 확인

API Key가 GitHub에 노출된 경우 단순히 코드를 삭제하는 것보다 **해당 Key를 폐기(Revoke)하고 새로 발급**하는 것이 안전합니다.

---

# 🛡️ 데이터 및 개인정보 주의사항

> [!WARNING]
> 자기소개서, 프로젝트 실적, 인사평가, 고객정보 등은 회사 내부정보 또는 민감한 정보가 포함될 수 있습니다.

무료 AI 모델의 데이터 처리 방식은 모델 및 서비스 제공자의 정책에 따라 다를 수 있습니다.

따라서 실제 인터뷰 자료를 입력할 때는 가능한 한 필요한 정보만 입력하고, 민감한 내용은 **비식별화**하는 것을 권장합니다.

### 입력 시 주의할 정보

* 고객사 실명
* 임직원 실명
* 주민등록번호 등 개인정보
* 프로젝트 세부 계약금액
* 내부 인사평가 정보
* 미공개 사업정보
* 고객사 보안정보
* 내부 시스템 구성정보
* 계정정보 및 인증정보
* 회사 기밀정보

예를 들어 다음과 같이 입력할 수 있습니다.

```text
KB○○카드 → 국내 대형 카드사
OO제조 → 국내 대형 제조기업
OO억원 프로젝트 → 대규모 보안 컨설팅 프로젝트
고객 담당자 이름 → 고객사 담당자
```

OpenRouter 및 사용 모델의 최신 데이터 정책은 각 모델 페이지에서 확인하는 것을 권장합니다.

---

# 🔄 모델 자동 대체

기본 모델이 일시적으로 사용할 수 없는 경우 다음 모델을 순차적으로 호출하도록 구성할 수 있습니다.

```javascript
const OPENROUTER_MODELS = [
  "upstage/solar-pro-3:free",
  "google/gemma-4-31b-it:free"
];
```

예를 들어 Solar Pro 3 호출이 실패하면 다음 모델인 Gemma를 호출하도록 구현할 수 있습니다.

```text
Solar Pro 3
     │
     ├─ 성공 → 응답 반환
     │
     └─ 실패
          │
          ▼
     Gemma 4 31B
          │
          └─ 응답 반환
```

---

# 🔧 다른 AI 모델 사용

다른 OpenRouter 모델을 사용하고 싶다면 `OPENROUTER_MODELS` 배열을 수정하면 됩니다.

예:

```javascript
const OPENROUTER_MODELS = [
  "upstage/solar-pro-3:free",
  "google/gemma-4-31b-it:free"
];
```

최대 3개 정도의 모델을 등록하여 순차적으로 호출하도록 구성할 수 있습니다.

모델 변경 시에는 반드시 OpenRouter에서 사용하는 **정확한 Model ID**를 입력해야 합니다.

---

# 🏢 여러 사람이 함께 사용하는 경우

현재 방식은 개인 연습용으로 간단하게 사용할 수 있도록 다음 구조를 사용합니다.

```text
Browser
   │
   │ OpenRouter API Key
   │
   ▼
OpenRouter API
   │
   ▼
AI Model
```

개인이 사용하는 경우에는 간단한 구조이지만, 여러 사람이 함께 사용하는 서비스로 운영할 경우에는 API Key 관리 측면에서 적절하지 않을 수 있습니다.

---

## 권장 구조

조직 또는 여러 사람이 사용하는 형태로 배포할 경우 **Backend 또는 Serverless Proxy**를 두는 것을 권장합니다.

```text
┌─────────────────────┐
│      사용자          │
│      Browser         │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ GitHub Pages / Web  │
│        App          │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Backend / Serverless│
│       Proxy         │
│                     │
│ • API Key 관리      │
│ • 사용자 인증       │
│ • Rate Limiting     │
│ • 입력값 검증       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   OpenRouter API    │
└──────────┬──────────┘
           │
           ▼
       AI Model
```

사용할 수 있는 서버리스 환경의 예시는 다음과 같습니다.

* Cloudflare Workers
* AWS Lambda
* AWS API Gateway
* Azure Functions
* Google Cloud Functions
* Vercel Functions
* Netlify Functions

이 구조를 적용할 경우 `callModelOnce` 함수의 다음 부분만 Proxy 환경에 맞게 변경하면 기존 인터뷰 로직을 대부분 그대로 사용할 수 있습니다.

```javascript
fetch(...)
```

주요 변경 대상은 다음과 같습니다.

```text
API URL
Authorization Header
Request Header
```

---

# 🎙️ 브라우저 호환성

## 음성 인식

마이크 기반 음성 입력은 **Web Speech API**를 사용합니다.

| Browser        |     권장 수준 |
| -------------- | --------: |
| Google Chrome  |     ⭐⭐⭐⭐⭐ |
| Microsoft Edge |     ⭐⭐⭐⭐⭐ |
| Safari         |       ⭐⭐⭐ |
| Firefox        | 환경에 따라 제한 |

음성 인식은 **Chrome / Edge 계열**에서 가장 안정적으로 동작합니다.

Web Speech API를 지원하지 않는 브라우저에서는 자동으로 **텍스트 입력 방식만 활성화**됩니다.

---

## 🔊 음성 합성 — TTS

AI 면접관의 질문을 음성으로 들을 수 있도록 브라우저의 음성 합성 기능을 사용합니다.

```javascript
SpeechSynthesis API
```

대부분의 최신 브라우저에서 사용할 수 있습니다.

설치된 한국어 음성이 없는 경우 운영체제 또는 브라우저의 기본 음성이 대신 사용될 수 있습니다.

---

# 📁 프로젝트 구조

프로젝트는 다음과 같이 매우 단순하게 구성할 수 있습니다.

```text
promotion-interview-simulator/
│
├── index.html
│
├── README.md
└── LICENSE
```

### 파일 설명

| 파일           | 설명          |
| ------------ | ----------- |
| `index.html` | 승진 모의 면접 웹앱 |
| `README.md`  | 프로젝트 설명     |
| `LICENSE`    | 라이선스 정보     |

별도의 Framework 또는 Build 과정이 필요하지 않습니다.

---

# 🧩 기술 구성

| 구분                 | 기술                            |
| ------------------ | ----------------------------- |
| Frontend           | HTML5                         |
| Styling            | CSS3                          |
| Application Logic  | Vanilla JavaScript            |
| AI API             | OpenRouter                    |
| Primary AI         | Upstage Solar Pro 3           |
| Fallback AI        | Google Gemma                  |
| Speech Recognition | Web Speech API                |
| Text-to-Speech     | SpeechSynthesis API           |
| Local Storage      | Browser LocalStorage          |
| Hosting            | GitHub Pages / Static Hosting |

---

# 🌐 GitHub Pages 배포

이 프로젝트는 별도의 Build 과정이 필요하지 않기 때문에 **GitHub Pages**를 이용해 바로 배포할 수 있습니다.

Repository 생성 후 다음과 같이 파일을 업로드합니다.

```text
promotion-interview-simulator/
│
├── index.html
└── README.md
```

GitHub Repository에서 다음 메뉴로 이동합니다.

```text
Settings
   │
   └─ Pages
       │
       └─ Build and deployment
```

배포할 Branch를 선택하면 GitHub Pages를 통해 웹앱에 접속할 수 있습니다.

예:

```text
https://사용자명.github.io/promotion-interview-simulator/
```

---

# 🔒 보안 권장사항

### 개인 사용

개인적으로 인터뷰를 연습하는 경우 현재의 브라우저 직접 API 호출 방식을 사용할 수 있습니다.

### 조직 / 다수 사용자

회사 내부에서 여러 사용자가 사용하는 경우에는 다음 보안 통제를 적용하는 것을 권장합니다.

* API Key 서버 측 관리
* 사용자 인증
* Rate Limiting
* 요청 크기 제한
* 입력 데이터 Validation
* 민감정보 입력 경고
* 로그 개인정보 Masking
* CORS 정책 적용
* CSP(Content Security Policy) 적용
* 비정상 API 요청 차단
* API 사용량 모니터링

---

# 📄 라이선스

별도 라이선스를 명시하지 않은 경우 **개인 및 사내 승진 인터뷰 연습 목적**으로 자유롭게 사용하고 수정할 수 있습니다.

외부 공개 또는 상업적 활용을 하는 경우에는 다음 사항을 별도로 확인하는 것을 권장합니다.

* OpenRouter 이용약관
* 사용 AI 모델의 라이선스
* AI 모델 Provider 이용정책
* 데이터 처리 정책

---

# 📌 Disclaimer

본 프로젝트는 **승진 인터뷰 연습을 지원하기 위한 AI 기반 보조 도구**입니다.

AI가 제공하는 질문, 평가 및 피드백은 실제 회사의 승진 심사 결과를 보장하지 않습니다.

실제 인터뷰에서는 다음 요소가 함께 고려될 수 있습니다.

* 회사의 승진 평가 기준
* 조직 및 사업 상황
* 개인의 실제 업무 성과
* 매출 및 사업 기여도
* 조직 리더십
* 인력 육성 성과
* 파트너 및 경영진 평가

따라서 AI 평가 결과는 **인터뷰 준비를 위한 참고자료**로 활용하는 것을 권장합니다.

---

## ⭐ 활용 Tip

승진 인터뷰 전에 다음 과정을 반복하면 보다 효과적으로 사용할 수 있습니다.

```text
1. 자기소개서 / 실적 입력
        ↓
2. 압박형 면접 진행
        ↓
3. AI 피드백 확인
        ↓
4. 부족한 답변 수정
        ↓
5. 다시 모의 면접
        ↓
6. 최종 답변 정리
```

**같은 질문에 대한 답변을 반복적으로 개선하는 방식**으로 활용하면 실제 승진 인터뷰 준비에 보다 효과적으로 사용할 수 있습니다.
