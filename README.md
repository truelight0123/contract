# 참빛 전자서명 (CHAMSIT Electronic Signature)

## 프로젝트 개요
참빛 구독 서비스 계약서 전자서명 시스템입니다.  
고객이 기본 정보, 계약 정보, CMS 계좌 정보를 입력하고 전자 서명 후 제출하면 데이터베이스에 저장됩니다.

---

## ✅ 구현 완료 기능

| 기능 | 설명 |
|------|------|
| 고객 정보 입력 | 이름, 연락처, 주소 입력 폼 |
| 계약 정보 입력 | 모델명, 월 구독료 입력 |
| CMS 계좌 입력 | 은행명, 계좌번호, 예금주 입력 |
| 전자서명 패드 | 마우스 & 터치 모두 지원, DPR(레티나) 대응 |
| 유효성 검사 | 모든 필드 입력 여부 + 전화번호 형식 체크 |
| 개인정보 동의 | 체크박스 동의 확인 |
| 데이터 저장 | REST Table API (`tables/signatures`) 로 서명 데이터 저장 |
| 성공 알림 | 제출 완료 후 팝업 오버레이 표시 |
| 폼 초기화 | 제출 성공 후 전체 폼 리셋 |
| 연락처 자동 포맷 | 숫자 입력 시 `010-0000-0000` 형식 자동 변환 |
| 단계 표시 | 입력 진행 상황을 상단 도트 인디케이터로 표시 |
| 반응형 디자인 | 모바일/태블릿/데스크톱 대응 |

---

## 📄 주요 파일

```
index.html       # 메인 전자서명 페이지
README.md        # 프로젝트 문서
```

---

## 🌐 API 엔드포인트

| 메서드 | 경로 | 설명 |
|--------|------|------|
| POST | `tables/signatures` | 서명 데이터 저장 |
| GET | `tables/signatures` | 서명 목록 조회 |
| GET | `tables/signatures/{id}` | 특정 서명 조회 |
| DELETE | `tables/signatures/{id}` | 서명 삭제 |

---

## 🗃️ 데이터 모델 (signatures 테이블)

| 필드명 | 타입 | 설명 |
|--------|------|------|
| id | text | 고유 식별자 (UUID, 자동 생성) |
| name | text | 고객 이름 |
| phone | text | 연락처 (010-xxxx-xxxx) |
| address | text | 주소 |
| model | text | 계약 모델명 |
| price | text | 월 구독료 |
| bank | text | 은행명 |
| account | text | 계좌번호 |
| owner | text | 예금주 |
| signature | rich_text | 전자서명 이미지 (Base64 PNG) |
| signed_at | datetime | 서명 일시 (ISO 8601) |
| created_at | datetime | 레코드 생성 시각 (자동) |
| updated_at | datetime | 레코드 수정 시각 (자동) |

---

## 🚧 미구현 기능 / 향후 개선 사항

- [ ] 관리자 페이지 (서명 목록 조회, 검색, 다운로드)
- [ ] PDF 계약서 자동 생성 및 이메일 발송
- [ ] 서명 이미지 미리보기 (관리자 뷰)
- [ ] Google Sheets 연동 (기존 Google Apps Script 방식)
- [ ] 다국어(영어) 지원

---

## 🛠️ 사용 기술

- **HTML5 / CSS3 / Vanilla JavaScript** (정적 웹사이트)
- **Noto Sans KR** (Google Fonts)
- **Font Awesome 6** (아이콘)
- **REST Table API** (데이터 저장소)
- **Canvas API** (전자서명 패드)
