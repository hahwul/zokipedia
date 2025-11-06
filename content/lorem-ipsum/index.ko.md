+++
title = "Lorem ipsum"
date = 2025-11-01
updated = 2025-11-06
description = "Lorem ipsum 실전 가이드: 역사, 목적, 모범 사례, 접근성, 주의점, 대안, 예시까지."
tags = ["lorem-ipsum", "placeholder-text", "typography", "graphic-design", "web-development", "publishing", "design-systems", "content-strategy", "accessibility", "i18n", "seo"]
+++

# Lorem ipsum이란?

Lorem ipsum은 실제 콘텐츠가 없을 때 레이아웃, 타이포그래피, 컴포넌트를 프로토타이핑하기 위해 쓰는 플레이스홀더(더미) 텍스트입니다. 의미 있는 단어에서 오는 인지적 편향을 배제해, 시각적·구조적 의사결정(여백, 계층, 반응형 거동 등)을 카피와 분리해서 검증할 수 있게 합니다.

- 이런 용도로 사용하세요: 그리드 테스트, 행 길이(라인 길이), 줄 간격, 폰트 페어링, 컴포넌트 브레이크포인트, 콘텐츠 흐름 점검
- 이런 용도로는 사용하지 마세요: 톤, 명확성, 전환 카피, 규정 준수 문구 검증(이건 실제 카피가 필요합니다)

## 역사와 기원

일반적으로 “Lorem ipsum”은 기원전 45년경 키케로의 저서 “De finibus bonorum et malorum”에서 일부를 잘라내고 순서를 섞어 만든 텍스트에서 유래했습니다. 1960년대 레트라셋(Letraset) 전사 시트를 통해 상업적으로 확산되었고, 1980년대에는 Aldus PageMaker 같은 DTP 템플릿을 통해 널리 퍼졌습니다. 이후 워드프로세서, CMS 테마, UI 키트를 거치며 라틴 문자권 레이아웃의 사실상 기본 더미 텍스트가 되었습니다.

“Lorem ipsum”이라는 구는 대개 “dolorem ipsum(고통 그 자체)”에서 잘려 나온 형태로 보며, 현대의 변형은 의미를 띠지 않도록 문법과 어순을 의도적으로 흐트러뜨립니다.

## 팀이 여전히 사용하는 이유

- 의미와 레이아웃의 분리: 초기 피드백이 카피가 아닌 위계/간격에 집중되도록 유도합니다.
- 텍스처 표준화: 라틴 문자권의 글자·단어 빈도를 근사해 페이지의 텍스트 컬러(시각적 밀도)를 현실적으로 재현합니다.
- 빠른 반복: 타이포 스케일, 수직 리듬, 스크롤 거동 등을 초기 단계부터 반복적으로 테스트할 수 있습니다.

## 이런 경우에는 사용하지 마세요

다음 중 하나라도 해당하면 실제 콘텐츠(혹은 도메인에 맞는 현실적 텍스트)를 쓰세요.
- UX 카피 검증이 필요할 때(라벨, 에러, 온보딩, 가격)
- 법/컴플라이언스 텍스트가 필요한 경우(개인정보, 동의, 규제 산업)
- 현지화가 레이아웃에 영향을 줄 때(CJK, RTL, 독일어의 긴 합성어 등)
- 접근성 리뷰 범위에 스크린 리더/언어 감지가 포함될 때
- 공개 크롤링/프리뷰/SEO/애널리틱스에 노출될 때

## 접근성과 국제화(i18n) 고려 사항

- 언어 메타데이터: 보조기술이 읽어야 한다면 `lang="la"`로 감싸 발음을 힌트 주세요. 순수 장식이라면 `aria-hidden="true"`로 숨기되, 정보가 전혀 없을 때만 사용하세요.
- 반복 피로: 길고 반복적인 난해 텍스트는 스크린 리더 경험을 저하시킵니다. 짧고 다양한 샘플을 쓰거나 장식 목적이면 숨기세요.
- 대비와 포커스: 플레이스홀더 때문에 가독성 테스트에 필요한 대비가 낮아지지 않도록 스타일을 유지하세요.
- RTL과 CJK: 라틴 중심 더미 텍스트로는 양방향(RTL)이나 CJK의 글꼴 메트릭 문제를 드러내기 어렵습니다. 아랍어/히브리어는 RTL 콘텐츠, 한중일은 해당 언어용 더미를 써서 줄바꿈·킨소쿠(금칙) 규칙을 검증하세요.
- 잘림과 오버플로: 긴 단어와 혼합 스크립트를 포함해 줄바꿈, 말줄임표, 오버플로 클리핑 문제를 노출하세요.

## 실무 사용 가이드라인

- 길이 타기팅: 예상 단어 수를 맞추세요(마이크로 카피 4–12단어, 문단 60–120단어). 행 길이 45–75자는 흔한 가독성 권장 범위입니다(주로 영문 기준).
- 변주: 문장 길이와 문장부호를 섞어 자연스러운 리듬과 하이픈 처리를 시뮬레이션하세요.
- 콘텐츠 토큰: 디자인 시스템에 `--placeholder-text-short`, `--placeholder-text-long`, `--placeholder-heading` 같은 토큰을 두어 컴포넌트 전반에서 샘플을 표준화하세요.
- 환경 구분: 더미 콘텐츠는 개발/스테이징에서만 보이도록 하고, “lorem ipsum”이 프로덕션에 포함되면 빌드가 실패하도록 체크를 추가하세요.

## 흔한 함정과 예방법

- 플레이스홀더 출고: CI에서 “lorem”/“ipsum”을 검색해 프로덕션 번들/템플릿에 있으면 빌드를 실패시키세요.
- 테스트 오탐: 더미 문자열에 의존한 테스트는 취약합니다. 문자열 단정 대신 테스트 ID나 구조를 검증하세요.
- 잘못된 승인: 이해관계자가 시각적 위계만 보고 승인했다가, 실제 카피의 밀도 변화로 번복될 수 있습니다. 가능한 빨리 초안 카피로 교체해 리스크를 낮추세요.

## Lorem ipsum의 대안

- 도메인 실감형 플레이스홀더: 보관본이나 익명화한 실제 도메인 텍스트(블로그 인트로, 상품 설명 등)를 사용
- 언어별 더미:
  - CJK: 해당 언어의 더미로 줄바꿈/문장부호 규칙 검증
  - RTL: 아랍어/히브리어로 양방향 처리와 글리프 셰이핑 확인
- 팬그램: 서체 견본에 유용(예: “The quick brown fox …”). 문단 테스트의 대체재는 아닙니다.
- 테마형 제너레이터: “Bacon Ipsum”, “Corporate Ipsum” 등—재미용으로 내부 데모에 한정하세요.
- 콘텐츠 스켈레톤: 의미 있는 헤딩과 중립적 짧은 본문으로 구조는 유지하되 인지적 노이즈를 줄입니다.

## 예시 문단

행 길이와 리듬을 평가하기 위한 중간 길이 문단(약 80–100단어):

> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer in commodo nibh. Sed vitae sem fermentum, posuere metus a, malesuada lacus. Quisque dictum, arcu a hendrerit consequat, leo dui ultricies est, sed lobortis massa neque non nisi. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Proin sed feugiat justo. Aliquam erat volutpat. Donec a luctus erat, quis aliquet orci. Duis viverra, nunc a placerat aliquam, sapien lorem cursus ipsum, at facilisis velit arcu in lectus.

카드/티저용 짧은 문단(약 40–60단어):

> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse vitae augue vehicula, condimentum odio ut, sodales urna. Donec pulvinar, velit at euismod suscipit, lacus nunc blandit risus, a faucibus massa arcu et nunc.

리스트/빈 상태용 스니펫:

- Lorem ipsum dolor sit amet, consectetur adipiscing elit.
- Curabitur non risus nec magna iaculis placerat.
- Vivamus posuere sapien et urna congue, nec dictum leo pretium.

## 길이와 읽기 시간 추정

- 대략적 단어 수: 단어 수 ≈ 문자 수 / 5 (영어 유사 텍스트 기준)
- 대략적 읽기 시간: 분 ≈ 단어 수 / 200 (성인 평균 묵독 속도)

이 지표는 블록 크기 산정에만 쓰고, 출고 전에는 반드시 실제 카피로 검증하세요.

## SEO와 분석 위생

- 인덱싱 제외: 비프로덕션/프리뷰 경로에는 `noindex`/`nofollow`를 적용하세요.
- 공유 카드: 오픈 그래프/트위터 카드에 플레이스홀더가 노출되지 않게 하세요.
- 사이트맵: 플레이스홀더 페이지는 프로덕션 사이트맵에 포함하지 마세요.

## 팀 체크리스트

Do:
- 사용자 테스트 전에 플레이스홀더를 초안 콘텐츠로 교체하세요.
- 보조기술 대상이면 `lang`을 적절히 지정하거나 장식용은 숨기세요.
- “lorem ipsum”의 프로덕션 유출을 막는 CI 체크를 추가하세요.

Don’t:
- 결제/동의 등 핵심 플로우를 플레이스홀더로 승인하지 마세요.
- 비라틴 레이아웃에 라틴 기반 더미만 의존하지 마세요.
- 분석 실험이나 A/B 테스트에 플레이스홀더를 사용하지 마세요.

## 라틴어 본문 예시

서체/타이포 견본에 자주 쓰는 표준 블록:

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## 수식 데모(타이포그래피 렌더링)

아래 수식은 레이아웃에서 수학 렌더링을 점검하기 위한 예시입니다.

{% math() %}
\sum_{i=0}^{n} r^i = \frac{r^{n+1} - 1}{r - 1} \quad \text{단, } r \neq 1
{% end %}