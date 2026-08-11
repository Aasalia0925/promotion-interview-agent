# 🎯 승진 심사 모의 면접

### Promotion Interview Simulator

회계법인 **파트너 패널 승진 인터뷰**를 텍스트 또는 음성으로 연습할 수 있는 **싱글 HTML 기반 웹앱**입니다.

별도의 프레임워크나 빌드 과정 없이 **순수 HTML / CSS / JavaScript**로 작성되어 있으며, `index.html` 파일만으로 실행할 수 있습니다.

GitHub Pages를 비롯한 다양한 정적 웹 호스팅 환경에도 바로 배포할 수 있습니다.

---

## 📌 주요 특징

* 별도 프레임워크 불필요
* 별도 설치 과정 불필요
* 단일 `index.html` 기반
* 텍스트 기반 모의 면접 지원
* 브라우저 음성 인식 지원
* AI 질문 음성 출력(TTS) 지원
* OpenRouter API 연동
* GitHub Pages 배포 가능

---

## ✨ 주요 기능

### 01. 자료 준비

실제 승진 인터뷰 상황에 맞게 면접 조건과 참고자료를 설정할 수 있습니다.

**설정 가능한 항목**

| 구분       | 내용                    |
| -------- | --------------------- |
| 승진 대상 직급 | 승진 심사를 받는 대상 직급 설정    |
| 면접 스타일   | 압박형 / 균형형 / 코칭형       |
| 패널 구성    | 1인 패널 / 3인 패널         |
| 자기소개서    | 본인의 자기소개 및 주요 경력      |
| 주요 실적    | 프로젝트, 매출, 조직 기여도 등    |
| 평가 기준    | 회사 또는 조직의 승진 평가 기준    |
| 참고 자료    | 자유로운 추가 자료 입력         |
| API Key  | OpenRouter API Key 입력 |

자료는 다음 방식으로 입력할 수 있습니다.

* 직접 텍스트 붙여넣기
* `.txt` 파일 업로드
* `.md` 파일 업로드

---

### 02. 모의 면접

입력한 자료를 기반으로 AI가 실제 승진 인터뷰와 유사한 형태로 질문을 진행합니다.

#### 지원 방식

* 💬 **텍스트 채팅**
* 🎙️ **브라우저 음성 인식**
* 🔊 **AI 질문 음성 출력(TTS)**

음성 인식은 **Web Speech API**를 사용합니다.

면접 스타일 및 패널 구성에 따라 질문의 강도와 방식이 달라질 수 있도록 구성되어 있습니다.

---

### 03. 인터뷰 피드백

모의 면접 종료 후 답변 내용을 기반으로 구조화된 피드백을 제공합니다.

#### 제공되는 평가

* ✅ 잘한 점
* ⚠️ 보완할 점
* 📊 종합 평가
* 💡 실전 인터뷰 Tip

전체 인터뷰 기록도 복사할 수 있어 이후 별도로 검토하거나 보관할 수 있습니다.

---

# 🚀 실행 방법

가장 간단한 방법은 `index.html` 파일을 직접 브라우저에서 여는 것입니다.

```text
index.html
```

파일을 더블클릭하거나 브라우저로 열면 바로 사용할 수 있습니다.

---

## 로컬 웹서버 실행

브라우저 보안 정책이나 일부 기능 테스트를 위해 로컬 웹서버로 실행하고 싶다면 Python을 사용할 수 있습니다.

```bash
python3 -m http.server 8000
```

이후 브라우저에서 아래 주소로 접속합니다.

```text
http://localhost:8000
```

---

# 🔑 OpenRouter API 연결

> [!IMPORTANT]
> 이 앱을 사용하려면 **OpenRouter API Key가 반드시 필요합니다.**

이 앱은 별도의 서버나 백엔드를 두지 않고 **브라우저에서 OpenRouter API를 직접 호출**하는 구조입니다.

따라서 다음 환경 모두 API Key가 필요합니다.

* 로컬 브라우저 실행
* GitHub Pages
* 정적 웹 호스팅
* 기타 브라우저 기반 실행 환경

---

## API Key 입력

화면의 다음 메뉴에서 API Key를 입력합니다.

```text
01 자료 준비 → F. OpenRouter API Key
```

API Key를 입력하면 바로 AI 면접 기능을 사용할 수 있습니다.

OpenRouter 계정 및 API Key는 아래 사이트에서 생성할 수 있습니다.

👉 [OpenRouter](https://openrouter.ai)

로그인 후 **Keys** 메뉴에서 API Key를 생성합니다.

---

## 🤖 사용 모델

기본적으로 OpenRouter를 통해 다음 모델을 호출하도록 구성되어 있습니다.

```text
Google Gemma 4 31B
```

무료 모델을 사용하는 경우 모델 ID는 다음과 같은 형태로 설정할 수 있습니다.

```javascript
google/gemma-4-31b-it:free
```

---

## 모델 변경

다른 OpenRouter 모델을 사용하려면 `callClaude` 함수 내부의 `OPENROUTER_MODEL` 값을 변경하면 됩니다.

예:

```javascript
const OPENROUTER_MODEL = "google/gemma-4-31b-it:free";
```

원하는 모델의 OpenRouter Model ID로 변경하면 나머지 로직은 그대로 사용할 수 있습니다.

---

# ⚠️ API Key 보안 주의사항

> [!CAUTION]
> **API Key를 GitHub 공개 저장소에 절대로 업로드하지 마세요.**

현재 구조에서는 API Key를 브라우저에서 직접 입력합니다.

키는 OpenRouter API 호출을 위해 사용되며, 별도의 자체 서버로 전송하지 않는 구조입니다.

---

## 브라우저 저장 기능

`이 브라우저에 저장` 기능을 활성화하면 API Key가 브라우저의 `localStorage`에 저장됩니다.

따라서 다음 접속 시 API Key를 다시 입력하지 않아도 됩니다.

하지만 다음 환경에서는 사용하지 않는 것을 권장합니다.

* 공용 PC
* PC방
* 공유 업무용 PC
* 여러 사람이 동일한 브라우저 계정을 사용하는 환경

---

## GitHub 업로드 시 주의

이 프로젝트를 다른 사람과 공유하거나 GitHub 공개 Repository에 업로드할 경우 다음 사항을 반드시 확인하세요.

> **API Key가 코드 또는 HTML 파일에 포함되어 있지 않은지 반드시 확인합니다.**

현재 앱 구조에서는 API Key가 파일 자체가 아니라 브라우저 `localStorage`에 저장되도록 구성할 수 있지만, 개발 또는 테스트 과정에서 API Key를 직접 코드에 입력하지 않도록 주의해야 합니다.

예를 들어 다음과 같은 코드는 공개 저장소에 올리면 안 됩니다.

```javascript
const API_KEY = "sk-or-v1-xxxxxxxxxxxxxxxx";
```

---

# 🛡️ 데이터 보안 및 개인정보 주의사항

> [!WARNING]
> 자기소개서, 인사평가, 프로젝트 실적, 매출, 고객정보 등은 민감정보 또는 회사 내부정보가 포함될 수 있습니다.

무료 AI 모델은 서비스 제공자의 정책에 따라 입력 데이터가 모델 개선 등의 목적으로 활용될 가능성이 있습니다.

따라서 다음 정보는 가능한 한 제거하거나 비식별화하는 것을 권장합니다.

* 고객사 실명
* 임직원 실명
* 프로젝트 계약금액
* 내부 평가 결과
* 미공개 사업정보
* 개인정보
* 회사 기밀정보
* 고객사 보안정보
* 내부 시스템 정보

예를 들어 다음과 같이 변경하여 입력하는 것을 권장합니다.

```text
A사
금융사 B
국내 대형 제조기업
약 10억 원 규모 프로젝트
대형 클라우드 전환 프로젝트
```

OpenRouter 및 해당 모델의 **최신 데이터 처리 정책은 반드시 공식 정책을 확인하시기 바랍니다.**

👉 [OpenRouter](https://openrouter.ai)

---

# 🏢 여러 사람이 사용하는 경우

현재 구조는 개인 연습용으로 간단하게 사용할 수 있도록 **브라우저에서 OpenRouter API를 직접 호출**합니다.

하지만 여러 사용자가 사용하는 서비스로 배포하는 경우에는 다음 구조를 권장합니다.

```text
사용자 Browser
      │
      ▼
GitHub Pages / Web App
      │
      ▼
Serverless Proxy / Backend
      │
      ▼
OpenRouter API
```

API Key를 서버 또는 서버리스 환경에 보관하면 사용자가 직접 API Key를 입력하지 않아도 됩니다.

사용 가능한 예시는 다음과 같습니다.

* Cloudflare Workers
* AWS Lambda
* AWS API Gateway
* Azure Functions
* Google Cloud Functions
* Vercel Functions
* Netlify Functions

이 구조를 적용할 경우 `callClaude` 함수의 `fetch` 대상 URL과 인증 헤더 부분을 프록시 API에 맞게 변경하면 기존 UI 및 면접 로직은 대부분 그대로 재사용할 수 있습니다.

---

# 🌐 GitHub Pages 배포

별도의 빌드 과정이 없기 때문에 GitHub Pages를 통해 간단하게 배포할 수 있습니다.

Repository 구조 예시는 다음과 같습니다.

```text
promotion-interview-simulator/
│
├── index.html
├── README.md
└── LICENSE
```

GitHub Repository에서 다음 메뉴로 이동합니다.

```text
Settings
  └─ Pages
      └─ Build and deployment
```

배포할 Branch를 지정하면 GitHub Pages를 통해 웹앱을 실행할 수 있습니다.

---

# 🎙️ 브라우저 호환성

## 음성 인식

마이크 입력은 **Web Speech API**를 사용합니다.

다음 브라우저 사용을 권장합니다.

| 브라우저           | 권장 수준     |
| -------------- | --------- |
| Google Chrome  | ⭐⭐⭐⭐⭐     |
| Microsoft Edge | ⭐⭐⭐⭐⭐     |
| Safari         | ⭐⭐⭐       |
| Firefox        | 환경에 따라 제한 |

Chrome / Edge 계열에서 가장 안정적으로 동작합니다.

Web Speech API를 지원하지 않는 브라우저에서는 자동으로 **텍스트 입력 방식만 사용**할 수 있습니다.

---

## 음성 합성 — TTS

AI 질문을 읽어주는 TTS 기능은 대부분의 최신 브라우저에서 동작합니다.

브라우저 또는 운영체제에 한국어 음성이 설치되어 있지 않은 경우 기본 음성으로 대체될 수 있습니다.

---

# 🔒 보안 권장사항

개인적인 연습 용도라면 현재 구조로도 충분히 사용할 수 있습니다.

하지만 조직 또는 다수 사용자가 사용하는 환경이라면 다음 구조를 권장합니다.

```text
[권장]

Browser
   │
   ▼
Backend / Serverless Proxy
   │
   ├─ API Key 관리
   ├─ 사용자 인증
   ├─ Rate Limiting
   ├─ 입력 데이터 검증
   └─ 로그 및 접근통제
   │
   ▼
OpenRouter API
```

특히 다음 기능을 추가하면 보안성을 높일 수 있습니다.

* API Key 서버 측 보관
* 사용자 인증
* API 호출 횟수 제한
* 입력 데이터 크기 제한
* 민감정보 입력 경고
* 로그 내 개인정보 Masking
* CSP(Content Security Policy)
* CORS 제한
* 비정상 API 호출 차단

---

# 📁 프로젝트 구성

```text
promotion-interview-simulator/
│
├── index.html        # 웹앱 본체
├── README.md         # 프로젝트 설명
└── LICENSE           # 라이선스
```

본 프로젝트는 프레임워크 또는 별도의 라이브러리 설치가 필요하지 않습니다.

---

# 🧩 기술 구성

| 구분                 | 기술                            |
| ------------------ | ----------------------------- |
| Frontend           | HTML5                         |
| Styling            | CSS3                          |
| Logic              | Vanilla JavaScript            |
| AI API             | OpenRouter API                |
| Speech Recognition | Web Speech API                |
| TTS                | SpeechSynthesis API           |
| Storage            | Browser LocalStorage          |
| Hosting            | GitHub Pages 등 Static Hosting |

---

# 📄 라이선스

별도의 라이선스가 명시되지 않은 경우 **개인 및 사내 연습 목적**으로 자유롭게 사용하고 수정할 수 있습니다.

외부 배포 또는 상업적 활용을 계획하는 경우 사용하는 AI 모델 및 API 제공자의 라이선스와 이용약관을 별도로 확인하시기 바랍니다.

---

## 📌 Disclaimer

본 프로젝트는 **승진 인터뷰 연습을 지원하기 위한 도구**입니다.

AI가 제공하는 질문, 평가 및 피드백은 실제 회사의 승진 심사 결과를 보장하지 않으며, 실제 평가 기준 및 면접관의 판단과 다를 수 있습니다.

AI 피드백은 참고자료로 활용하고 실제 인터뷰 준비 시에는 회사의 공식 승진 기준, 조직 상황 및 실제 업무 성과를 함께 고려하시기 바랍니다.
