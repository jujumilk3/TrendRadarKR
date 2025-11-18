<div align="center" id="trendradar">

<a href="https://github.com/sansan0/TrendRadar" title="TrendRadar">
  <img src="/_image/banner.jpg" alt="TrendRadar Banner" width="50%">
</a>

🚀 **30초 만에 배포** — 당신의 스마트 트렌드 뉴스 어시스턴트

<a href="https://trendshift.io/repositories/14726" target="_blank"><img src="https://trendshift.io/api/badge/repositories/14726" alt="sansan0%2FTrendRadar | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>

[![GitHub Stars](https://img.shields.io/github/stars/sansan0/TrendRadar?style=flat-square&logo=github&color=yellow)](https://github.com/sansan0/TrendRadar/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/sansan0/TrendRadar?style=flat-square&logo=github&color=blue)](https://github.com/sansan0/TrendRadar/network/members)
[![License](https://img.shields.io/badge/license-GPL--3.0-blue.svg?style=flat-square)](LICENSE)
[![Version](https://img.shields.io/badge/version-v3.0.5-blue.svg)](https://github.com/sansan0/TrendRadar)

</div>

<div align="center">

**[中文](README.md)** | **[English](README-EN.md)** | **한국어**

</div>

> 이 프로젝트는 가볍고 배포하기 쉽게 설계되었습니다

## 📑 빠른 네비게이션

<div align="center">

| [🎯 핵심 기능](#-핵심-기능) | [🚀 빠른 시작](#-빠른-시작) | [🐳 Docker 배포](#-docker-배포) | [🤖 AI 분석](#-ai-분석) |
|:---:|:---:|:---:|:---:|

</div>

## ✨ 핵심 기능

### **멀티 플랫폼 트렌드 뉴스 집계**

**한국 플랫폼:**
- 네이버 (Naver)
- 다음 (Daum)
- 더쿠 (theqoo)
- 디시인사이드 (DCinside)
- 에펨코리아 (fmkorea)
- 클리앙 (Clien)
- 엠엘비파크 (mlbpark)
- 인스티즈 (instiz)
- 루리웹 (ruliweb)
- 와이고수 (ygosu)

**중국 플랫폼:**
- 知乎 (Zhihu)
- 抖音 (Douyin)
- Bilibili 热搜
- 华尔街见闻 (Wallstreetcn)
- 贴吧 (Tieba)
- 百度热搜 (Baidu Hot Search)
- 财联社 (CLS)
- 澎湃新闻 (ThePaper)
- 凤凰网 (Ifeng)
- 今日头条 (Toutiao)
- 微博 (Weibo)

기본적으로 여러 주요 플랫폼을 모니터링하며, 커스텀 플랫폼 추가를 지원합니다.

### **스마트 푸시 전략**

**3가지 푸시 모드**:

| 모드 | 대상 사용자 | 푸시 시점 | 표시 내용 | 활용 사례 |
|------|------------|----------|----------|-----------|
| **일일 요약**<br/>`daily` | 📋 관리자/일반 사용자 | 정시 푸시 (기본: 1시간마다) | 당일 모든 매칭 뉴스<br/>+ 신규 뉴스 영역 | 일일 리포트<br/>종합 트렌드 파악 |
| **현재 순위**<br/>`current` | 📰 콘텐츠 크리에이터 | 정시 푸시 (기본: 1시간마다) | 현재 순위 매칭 뉴스<br/>+ 신규 뉴스 영역 | 실시간 인기 추적<br/>지금 뜨는 콘텐츠 파악 |
| **증분 모니터링**<br/>`incremental` | 📈 트레이더/투자자 | 신규 항목 발생 시만 푸시 | 새로 등장한 매칭 뉴스 | 중복 정보 방지<br/>고빈도 모니터링 |

### **정밀한 콘텐츠 필터링**

개인 키워드(예: AI, 삼성, 정책)를 설정하여 관련 트렌드 뉴스만 수신하고 노이즈를 필터링합니다.

- 일반 단어, 필수 단어(+), 필터 단어(!) 지원
- 그룹 기반 관리로 다양한 주제별 독립적인 통계

키워드는 `config/frequency_words.txt`에서 설정합니다.

### **다양한 알림 채널**

- 📧 이메일 (Email)
- 💬 텔레그램 (Telegram)
- 🔔 기타 웹훅 지원 (Feishu, DingTalk, WeWork, ntfy)

### **유연한 배포 옵션**

- 🐳 Docker/Docker Compose
- ⚙️ GitHub Actions 자동화
- 🌐 GitHub Pages 배포
- 💻 로컬 Python 실행

## 🚀 빠른 시작

### 사전 요구사항

- Python 3.10 이상
- Git

### 1️⃣ 저장소 복제

```bash
git clone https://github.com/sansan0/TrendRadar.git
cd TrendRadar
```

### 2️⃣ 의존성 설치

**Windows:**
```bash
setup-windows.bat
```

**macOS/Linux:**
```bash
chmod +x setup-macos-linux.sh
./setup-macos-linux.sh
```

### 3️⃣ 설정 구성

`config/config.yaml` 파일을 편집합니다:

```yaml
# 푸시 모드 선택
report:
  mode: "daily"  # 옵션: "daily" | "incremental" | "current"

# 알림 설정
notification:
  enable_notification: true
  webhooks:
    email_from: "your-email@example.com"
    email_password: "your-app-password"
    email_to: "recipient@example.com"
    telegram_bot_token: "your-bot-token"  # 선택사항
    telegram_chat_id: "your-chat-id"      # 선택사항

# 모니터링 플랫폼 (필요에 따라 수정)
platforms:
  - id: "naver"
    name: "네이버"
  - id: "daum"
    name: "다음"
  # 더 많은 플랫폼 추가...
```

### 4️⃣ 키워드 설정

`config/frequency_words.txt`를 편집하여 관심 키워드를 추가합니다:

```txt
# 한국 기업 & 인물
삼성
이재용
갤럭시

네이버
카카오

# K-pop & 엔터테인먼트
BTS
블랙핑크
뉴진스

# 스포츠
손흥민
이강인
김민재

# 기타 관심 키워드 추가...
```

**키워드 구문:**
- 일반 키워드: `삼성` (포함하면 매칭)
- 필수 키워드: `+스마트폰` (반드시 포함해야 함)
- 필터 키워드: `!광고` (제외)

### 5️⃣ 실행

```bash
python main.py
```

## 🐳 Docker 배포

### Docker Compose 사용 (권장)

```bash
# docker-compose.yml 파일이 있는 디렉토리에서 실행
docker-compose up -d
```

### Docker 직접 실행

```bash
docker run -d \
  --name trendradar \
  -v $(pwd)/config:/app/config \
  -v $(pwd)/output:/app/output \
  wantcat/trendradar:latest
```

## 🤖 AI 분석

TrendRadar는 MCP(Model Context Protocol)를 통해 AI 분석을 지원합니다.

상세한 내용은 [README-MCP-FAQ.md](README-MCP-FAQ.md)를 참조하세요.

## 📝 주요 설정 파일

### config/config.yaml

프로젝트의 메인 설정 파일입니다:

- **crawler**: 크롤링 간격, 프록시 설정
- **report**: 푸시 모드 선택 (daily/current/incremental)
- **notification**: 알림 채널 설정
- **push_window**: 푸시 시간대 제어 (선택사항)
- **weight**: 뉴스 순위 가중치 설정
- **platforms**: 모니터링할 플랫폼 목록

### config/frequency_words.txt

모니터링할 키워드 목록입니다. 한 줄에 하나씩 입력하며, 빈 줄로 그룹을 구분할 수 있습니다.

## 🔧 문제 해결

### 이메일 알림이 작동하지 않는 경우

1. SMTP 서버 설정 확인
2. 이메일 제공업체의 앱 비밀번호 사용 (일반 비밀번호 아님)
3. Gmail의 경우: "보안 수준이 낮은 앱의 액세스" 활성화 또는 2단계 인증 후 앱 비밀번호 생성

### 뉴스를 가져올 수 없는 경우

1. 인터넷 연결 확인
2. 프록시 설정이 필요한 경우 config.yaml에서 활성화
3. 플랫폼 ID가 올바른지 확인 (대소문자 구분)

## ⭐ 관련 프로젝트

- [newsnow](https://github.com/ourongxing/newsnow) - 멀티 플랫폼 뉴스 API 제공

## 📄 라이선스

이 프로젝트는 [GPL-3.0 License](LICENSE) 하에 제공됩니다.

## 🤝 기여

기여는 언제나 환영합니다! 이슈를 열거나 풀 리퀘스트를 제출해 주세요.

## 📞 지원

- GitHub Issues: [문제 보고](https://github.com/sansan0/TrendRadar/issues)
- GitHub Discussions: [토론 참여](https://github.com/sansan0/TrendRadar/discussions)

---

<div align="center">

**TrendRadar로 생성** · [GitHub 오픈소스 프로젝트](https://github.com/sansan0/TrendRadar)

Made with ❤️ by the open source community

</div>
