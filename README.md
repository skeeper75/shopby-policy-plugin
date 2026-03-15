# shopby Policy Plugin

shopby Enterprise 기반 인쇄 사이트 정책 자문 플러그인입니다.

후니프린팅 사이트 리뉴얼 프로젝트에서 정책 수립 시 활용할 수 있는 포괄적인 자문 시스템을 제공합니다. 95개 IA 기능에 대한 shopby 플랫폼 대응 분류, 한국 인쇄업계 벤치마크, 구조화된 정책 문서 생성을 지원합니다.

## 설치

```bash
/plugin install github:innojini/shopby-policy-plugin
```

## 사용법

### /policy 명령어

```bash
# 정책 도메인 목록 및 사용 가이드 확인
/policy

# 특정 도메인 정책 자문
/policy 배송정책
/policy 결제방법
/policy B2B 후불결제는 shopby에서 지원하나요?
/policy 인쇄 옵션 구조를 어떻게 설계해야 하나요?
```

### 에이전트 직접 호출

```
expert-printing-policy 에이전트를 사용하여 회원 등급 정책을 분석해주세요.
```

## 기능 분류 체계

95개 IA 기능을 4가지 카테고리로 분류합니다:

| 분류 | 의미 | 기능 수 | 비율 |
|------|------|---------|------|
| NATIVE | shopby 기본 제공 | 38개 | 40% |
| SKIN | 스킨 커스텀 필요 (API 존재) | 26개 | 28% |
| CUSTOM | 커스텀 개발 필요 | 29개 | 31% |
| EXTERNAL | 외부 서비스 연동 | 2개 | 2% |

## 13개 정책 도메인

| No | 도메인 | 범위 |
|----|--------|------|
| 1 | 회원정책 | 가입, 로그인, 등급, B2B 회원 |
| 2 | 상품/옵션정책 | 인쇄 옵션, 가격 매트릭스, 카테고리 |
| 3 | 주문 워크플로우 | 파일 업로드, 장바구니, 결제, 주문완료 |
| 4 | 결제정책 | PG, 프린팅머니, 후불결제 |
| 5 | 배송정책 | 배송방법, 배송비, 납기일 |
| 6 | 취소/반품정책 | 맞춤 제작 상품 규정 |
| 7 | 고객서비스정책 | 문의 유형, SLA, 채널 |
| 8 | 마케팅정책 | 쿠폰, 리뷰, 체험단 |
| 9 | B2B 기업정책 | 법인고객, 대량주문 |
| 10 | 관리/운영정책 | 역할, 권한 |
| 11 | 거래처정책 | 거래처 관리, 오프라인 B2B |
| 12 | 회계정책 | 원장, 미수금 |
| 13 | 통계/리포트정책 | 매출, 생산, 팀별 통계 |

## 플러그인 구성요소

### 에이전트
- **expert-printing-policy** - 정책 수립 전문 에이전트 (Opus 모델)

### 스킬
- **innojini-shopby-policy-advisor** - 정책 자문 지식 베이스 스킬

### 슬래시 명령어
- **/policy** - 정책 자문 진입점

### 번들 참조 데이터
- `references/feature-mapping.md` - 95개 IA 기능 shopby 매핑 분석
- `skills/.../references/industry-benchmarks.md` - 한국 인쇄업계 벤치마크
- `skills/.../references/shopby-capability-matrix.md` - shopby 플랫폼 기능 매트릭스
- `templates/policy-document.md` - 정책 문서 템플릿

## 외부 문서 설정 (선택사항)

더 정확한 API 경로 및 관리자 설정 안내를 위해 shopby 공식 문서를 프로젝트에 배치할 수 있습니다. 이 문서들은 라이선스 문제로 플러그인에 포함되지 않습니다.

```
프로젝트 루트/
  ref/
    shopby/
      shopby_enterprise_docs/    # shopby Enterprise 관리자 문서
      shopby-api/                # shopby API 스펙 (YAML)
      shopby-api-docs-complete/  # shopby API 전체 문서
      aurora-react-skin-guide/   # Aurora React 스킨 가이드
```

외부 문서가 없어도 플러그인은 번들된 데이터(기능 매핑, 업계 벤치마크, 기능 매트릭스)만으로 정상 작동합니다.

## 커스텀 개발 Top 10

shopby에서 제공하지 않아 커스텀 개발이 필요한 핵심 항목:

1. 인쇄 옵션 종속 엔진 (용지 -> 두께 -> 사이즈 -> 수량 -> 후가공)
2. 동적 가격 매트릭스 (옵션 조합별 가격 계산)
3. 파일 업로드/검수 워크플로우 (포맷/해상도/재단선 검증)
4. 디자인 편집기 연동
5. 생산 공정 추적 (인쇄전 -> 인쇄 -> 후가공 -> QC -> 포장 -> 출고)
6. 옵션 보관함 (재주문용 인쇄 옵션 저장)
7. 프린팅머니 PG 충전
8. B2B 후불결제/미수금 관리
9. 체험단 관리 시스템
10. 오프라인 거래 원장

## 라이선스

MIT License - Copyright 2026 innojini
