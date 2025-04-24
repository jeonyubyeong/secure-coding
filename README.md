# 🛡️ Secure Coding - 중고 거래 플랫폼

Flask 기반의 중고 거래 웹 애플리케이션으로, 사용자 관리, 상품 등록 및 조회, 댓글 기능, 실시간 채팅 등 다양한 기능을 제공합니다. 이 프로젝트는 보안 코딩 원칙을 따르며, 사용자 입력 검증 및 세션 관리 등 핵심 보안 기능을 직접 구현했습니다.

---

## 🚀 주요 기능

- **회원가입 / 로그인 / 로그아웃**
- **프로필 관리**: 소개글 수정 및 비밀번호 변경
- **상품 등록, 조회, 삭제**
- **댓글 기능**: 상품별 댓글 등록 및 삭제
- **1:1 실시간 채팅**
- **전체 공개 채팅방 (Socket.IO)**
- **상품 신고 기능**
- **접속 유저별 권한 제어 및 로그인 확인 처리**

---

## 🛠️ 개발 환경

```yaml
name: secure_coding
channels:
  - defaults
dependencies:
  - python=3.9
  - pip
  - pip:
      - flask
      - flask-socketio
      - flask-sqlalchemy
      - python-socketio
      - eventlet
      - jinja2
      - werkzeug
```

설치:

```bash
git clone https://github.com/jeonyubyeong/secure-coding.git
python app.py  # 자동 DB 초기화 및 서버 실행
```

---

## ✅ 구현된 보안 체크리스트 (부분 기준)

| 항목 | 구현 상태 | 설명 |
|------|-----------|------|
| 입력 검증 | ✅ | 폼에서 필수 항목 검사, 서버 단에서 검증 로직 추가 |
| 출력 이스케이프 | ✅ | Jinja2 템플릿에서 자동 이스케이프 처리 |
| 인증 및 세션 관리 | ✅ | 세션 기반 로그인 및 로그아웃 구현 |
| 비밀번호 관리 | ✅ | 비밀번호 변경 기능 구현 *(해싱 미구현 → 개선 가능)* |
| 접근 제어 | ✅ | 로그인되지 않은 사용자의 접근 제한 (`session['user_id']`) |
| 사용자 리소스 접근 권한 | ✅ | 본인 상품/댓글만 삭제 가능 |
| 실시간 통신 보호 | ✅ | Socket.IO 기반 브로드캐스트 구현 (eventlet 사용 가능) |
| 데이터베이스 보호 | ✅ | SQLite + Prepared Statement 사용 (SQL Injection 방지) |
| 에러 처리 | ✅ | 에러 발생 시 Flash 메시지 출력 + 세션 상태 유지 |
| 신고 기능 | ✅ | 유저 간 신고 제출 가능, 관리자는 추후 확장 예정 |

---

## 📁 디렉토리 구조

```
secure_coding/
├── app.py
├── market.db
├── templates/
│   ├── base.html
│   ├── chat.html
│   ├── dashboard.html
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── profile.html
│   ├── product_list.html
│   ├── new_product.html
│   ├── view_product.html
│   ├── global_chat.html
│   └── report.html
├── static/
│   └── style.css (선택)
├── environment.yaml
└── README.md
```

---

## 🙌 참고

- 프로젝트 체크리스트: [`secure_coding_checklist.csv`](https://github.com/ugonfor/secure-coding/blob/main/secure_coding_checklist.csv)
- 실시간 채팅: `Flask-SocketIO`, `eventlet` 기반
- 템플릿 엔진: `Jinja2`

---

