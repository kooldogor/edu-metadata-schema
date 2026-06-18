# 🎓 FAIR 원칙 기반의 교육 자원 재활용을 위한 메타데이터 스키마 (`edu`)

<!-- 학술적 신뢰도를 높이는 기술 배지 -->
![FAIR Principles](https://img.shields.io/badge/Data_Principle-FAIR-blueviolet?style=flat-square)
![XML Schema](https://img.shields.io/badge/Schema-W3C_XSD-blue?style=flat-square)
![Dublin Core](https://img.shields.io/badge/Standard-Dublin_Core-orange?style=flat-square)
![LRMI](https://img.shields.io/badge/Standard-LRMI_Terms-green?style=flat-square)
![License](https://img.shields.io/badge/License-CC_Standards-lightgrey?style=flat-square)

본 프로젝트는 교수자들이 심혈을 기울여 제작한 교수학습 자원이 단발성으로 소비되는 문제를 해결하기 위해, 오픈 데이터의 핵심인 **FAIR 원칙(Findable, Accessible, Interoperable, Reusable)**에 의거하여 설계된 애플리케이션 프로필(Application Profile) 기반 교육 메타데이터 표준입니다.

---

## 📂 1. 리포지토리 아키텍처 (Directory Tree & Download)
본 저장소는 모듈화된 아키텍처 설계 규격을 준수하여, 메인 스키마가 분할된 개별 외부 표준 스키마 요소를 상호 참조하도록 구성되었습니다. 
각 파일명을 클릭하시면 **소스 코드를 즉시 확인하거나 다운로드**하실 수 있습니다.

```text


├── [README.md](README.md)                # 프로젝트 종합 안내서 및 가이드라인 웹 메인
├── [learningresource.xsd](learningresource.xsd)     # [Main] 최상위 루트 컨테이너 구조 정의 스키마 파일 (FAIR 통합 레이어)
├── [cc.xsd](cc.xsd)                 # Creative Commons 저작권 표준 모듈 스키마 파일 (Reusable 보장)
├── [dc.xsd](dc.xsd)                 # Dublin Core Simple 서지 정보 표준 모듈 스키마 파일 (Findable 보장)
├── [dct.xsd](dct.xsd)                # Dublin Core Terms 교수학습 방식 정의 모듈 스키마 파일 (Interoperable 보장)
├── [kem.xsd](kem.xsd)                # KERIS 국가 교육과정 매핑 모듈 스키마 파일 (Interoperable 보장)
├── [lrmi.xsd](lrmi.xsd)               # LRMI 교육 자원 교육 속성 정의 모듈 스키마 파일 (Reusable 보장)
├── [lessonplan_2.xml](lessonplan_2.xml)       # [Sample 1] 물리학Ⅰ 정성적 탐구 수업 지도안 인스턴스 레코드
├── [PE.xml](PE.xml)                 # [Sample 2] 체육과 뜀틀 단계별 두려움 극복 지도안 인스턴스 레코드
└── [worksheet_2.xml](worksheet_2.xml)        # [Sample 3] 열에너지 보존 법칙 수준별 보충 활동지 인스턴스 레코드



## 📝 2. Opening Narrative (개요 및 설계 배경)

* **도메인 공간 명세:** 'FAIR 원칙에 기반한 고품질 교수학습 자원의 공유·아카이빙 및 교육 생태계 내 재활용(Reuse)'
* **기획 배경:** 현장 교수자들이 오랜 시간 축적한 정교하고 우수한 고급 자료들은 표준화된 교육 기술 메타데이터의 부재로 인해 동료 교사나 시스템에 의해 쉽게 검색(Find)되지 못했습니다. 또한, 포맷과 분류 체계가 통일되지 않아(Interoperable) 동료가 만든 자료를 내 수업 맥락에 맞추어 지속 가능하게 재가공 및 재활용(Reuse)하는 데 큰 기술적 장벽이 존재했습니다.
* **설계 의도:** 본 스키마는 디지털 교육 자원을 단순한 '텍스트 파일'이 아니라 기계와 인간이 모두 다각도로 판독할 수 있는 고부가가치 **'교수학습 자산'**으로 정의합니다. 외부 표준들과 호환성을 유지하면서도, 타 교사가 자원을 이식할 때 판단해야 할 **교수 방법론, 안전 가이드라인, 학생 개별화 수준 정보**를 확장하여 교육 자원의 지속 가능한 순환과 재활용성을 극대화했습니다.

---

## ⚖️ 3. FAIR 원칙에 따른 스키마 아키텍처 매핑

W3C XML Schema 설계 기법을 활용하여 오픈 데이터의 4대 핵심 가치를 구조적으로 수용했습니다.

* **🔍 Findable (발견 가능성):** 분산된 자원들이 고유하게 구별될 수 있도록 전역 식별자(`dc:identifier`)를 필수 프라이머리 키(PK)로 지정했습니다. 또한 포털 검색엔진이 자원의 정체성을 직관적으로 찾을 수 있도록 제목(`dc:title`), 제작자(`dc:creator`), 지배적인 교수학습 형태(`lrmi:learningResourceType`)를 바인딩했습니다.
* **🔓 Accessible (접근 가능성):** 타 시스템이 자원 구동 환경과 요구 소프트웨어를 사전에 검사할 수 있도록 MIME Type 표기를 준수하는 기술적 포맷(`dc:format`)을 필수 요소화했습니다. 스키마 자원 전체(`xsd`)를 개방형 공간인 GitHub Pages 공공 웹 경로에 퍼블리싱하여 상시 접근 가능하도록 개방했습니다.
* **🔄 Interoperability (상호운용성):** 글로벌 서지 표준(Dublin Core), 교육 메타데이터 표준(LRMI), 그리고 국내 공교육 나이스(NEIS) 분류 체계의 표준인 한국 교육 메타데이터(KEM) 체계를 단일 레코드 내에 통합 수용했습니다. 교수 방법(`dct:instructionalMethod`) 및 개별화 수준(`edu:tailoredLevel`) 등에 엄격한 데이터 타입을 정의하여 시스템 간 의미론적(Semantic) 상호운용성을 확보했습니다.
* **♻️ Reusable (재활용 가능성):** 타 교수자가 저작권 침해 우려 없이 안심하고 소스 자료를 재가공할 수 있도록 저작권 허락 조건(`cc:license`) 및 출처 명시 필드(`cc:attributionName`)를 강제했습니다. 다른 교사의 완성형 수업을 내 교실에 그대로 이식할 수 있도록 교육적 용도(`lrmi:educationalUse`), 학습자 맞춤형 수준(`edu:tailoredLevel`), 단원 내 배치 차시(`edu:lessonSequence`), 안전 주의사항(`edu:safetyCaution`) 등의 교수학습 컨텍스트 속성을 조밀하게 구성했습니다.







## 📊 4. 데이터 사전

본 스키마를 구성하는 메타데이터 요소의 제약 조건 및 정의 일람입니다.

### 1) 메타데이터 요소 개요 표

| 요소 이름 | 레이블 | 정의 및 목적 | 표준 소스 |
| --- | --- | --- | --- |
| dc title | 제목 | 자원의 명칭으로 검색의 일차적 기준 | Dublin Core |
| dc identifier | 식별자 | 자원의 고유한 참조 URI | Dublin Core |
| dc creator | 제작자 | 콘텐츠 생성에 책임이 있는 개인 또는 기관 | Dublin Core |
| lrmi learningResourceType | 학습 자원 유형 | 자원의 지배적인 교육적 형태 분류 | LRMI Terms |
| lrmi educationalUse | 교육적 용도 | 교수 학습 맥락에서의 주된 사용 목적 | LRMI Terms |
| edu tailoredLevel | 개별화 수준 | 타겟팅하는 학습자의 성취 수준 | edu Local |
| dct instructionalMethod | 교수 방법 | 설계된 교육적 프로세스 및 수업 방법 | Dublin Core Terms |
| edu lessonSequence | 차시 순서 | 자원이 사용되는 특정 차시 및 순서 | edu Local |
| lrmi interactivityType | 상호작용 유형 | 자원이 지원하는 학습 모드의 성격 | LRMI Terms |
| lrmi typicalAgeRange | 대상 연령대 | 학습자의 전형적인 연령 범위 | LRMI Terms |
| lrmi timeRequired | 소요 시간 | 자원 완료에 필요한 표준 시간 | LRMI Terms |
| lrmi alignmentObject | 성취기준 연계 | 교육 프레임워크 성취기준 매핑 | LRMI Terms |
| kem classification | 교육과정 분류 | 한국 국가 교육과정 체계 내 위치 정보 | KEM |
| cc license | 라이선스 | 저작권 이용 허락 조건의 URL | Creative Commons |
| cc attributionName | 출처 표기 | 저작권자의 성명 또는 기관명 | Creative Commons |
| dc format | 기술적 포맷 | 물리적 또는 디지털 매체 형식 | Dublin Core |
| edu difficulty | 학습 난이도 | 자원의 인지적 복잡성 | edu Local |
| edu safetyCaution | 안전 주의사항 | 실험 및 활동 시의 안전 정보 | edu Local |

### 2) 메타데이터 요소 상세 사전

| 번호 | 요소명 | 기수 | 데이터 값 | 정의 및 사용 목적 | 예시 |
| --- | --- | --- | --- | --- | --- |
| 1 | dc title | 필수 반복불가 | 문자열 | 자원에 부여된 공식 명칭 | 초등 4학년 분수 게임판 |
| 2 | dc identifier | 필수 반복불가 | URI | 시스템 간 데이터 교환을 위한 키 | http keris or kr res 001 |
| 3 | dc creator | 필수 반복가능 | 문자열 | 자원 제작 책임 개인 또는 기관 | 나현석 선유고등학교 |
| 4 | lrmi learningResourceType | 필수 반복가능 | 통제어휘 | 자원의 교육적 형태나 역할 분류 | lesson plan, worksheet |
| 5 | lrmi educationalUse | 필수 반복가능 | 통제어휘 | 교수 학습 과정에서의 목적 및 단계 | assessment, 동기유발자료 |
| 6 | lrmi interactivityType | 필수 반복불가 | 통제어휘 | 학습자에게 요구되는 학습 모드 | active |
| 7 | lrmi typicalAgeRange | 권장 반복불가 | 문자열 | 자원이 의도한 주 사용자의 연령 | 10대 |
| 8 | lrmi timeRequired | 권장 반복불가 | Duration | 활동 완료에 필요한 예상 시간 | PT40M 소요 |
| 9 | lrmi alignmentObject | 필수 반복가능 | 복합구조 | 국가 교육과정 성취기준 연계 | 12물리0105 |
| 10 | kem classification | 필수 반복가능 | 계층코드 | 한국 국가 교육과정 내 위치 매핑 | 2022 고등 과학 열 |
| 11 | cc license | 필수 반복불가 | URI | 적용된 라이선스의 공식 주소 | https creativecommons org |
| 12 | cc attributionName | 권장 반복가능 | 문자열 | 자원 재활용 시 명시할 저작자명 | 서울선유등학교 나현석 교사 |
| 13 | dc format | 필수 반복불가 | MIME | 자원의 디지털 파일 형식 | application pdf |
| 14 | edu difficulty | 권장 반복불가 | 통제어휘 | 자원이 요구하는 인지적 부하 정도 | 보통 |
| 15 | edu safetyCaution | 선택 반복가능 | 문자열 | 실험 및 활동 시 필수 안전 지침 | 젖은 손으로 만지지 마십시오 |
| 16 | edu tailoredLevel | 권장 반복가능 | 통제어휘 | 타겟 학습자 성취 수준 명시 | remediation 보충 자료 |
| 17 | dct instructionalMethod | 권장 반복가능 | 통제어휘 | 자원이 지원하는 구체적 수업 방식 | flippedLearning, 실험수업 |
| 18 | edu lessonSequence | 권장 반복불가 | 문자열 | 전체 수업 내 자원 사용 차시 | 3차시 본시 활동 |


# 🗂️ 5. 데이터 값 통제 어휘집 (Controlled Vocabulary Appendix)

교수 자원의 의미론적 결합과 기계 가독성을 확보하기 위해 아래의 엄격한 데이터 어휘 사전을 준수합니다.

### 📌 [부록 1] 개별화 수준 (`edu:tailoredLevel`)
성취기준 달성 정도에 따른 자료의 타겟 그룹을 정의한다.
* **`remediation`**: 성취기준 미달 학생(학업 성취율 40% 미만)을 위한 보충 및 기초 학력 지원 자료.
* **`basic`**: 성취기준의 핵심 내용을 표준적으로 다루는 기본 학습 자료.
* **`enrichment`**: 성취기준 도달 후 해당 개념을 보다 깊이 있게 탐구하거나 실생활에 적용하는 심화 자료.
* **`acceleration`**: 해당 성취기준을 넘어 다음 단계의 학습 내용이나 고차원적 과제를 다루는 속진 자료.

### 📌 [부록 2] 교수 방법론 (`dct:instructionalMethod`)
* **`flippedLearning`**: 교실 수업 전 사전 지식 습득을 유도하는 방식.
* **`inquiryBased`**: 탐구 질문을 던지고 가설을 검증하는 과학적 탐구 방식.
* **`collaborative`**: 학생 간의 상호작용과 협력을 강조하는 방식.

### 📌 [부록 3] 학습 자원 유형 (`lrmi:learningResourceType`)
LRMI 및 CEDS 표준을 기반으로 한국 교육 현장에 맞게 재구성한 리스트이다.
* **`lessonPlan`**: 수업 전체의 흐름과 시간 배분을 포함한 설계 문서.
* **`presentation`**: 시각적 발표 및 수업 보조를 위한 슬라이드 세트.
* **`worksheet`**: 학습자의 연습과 결과 기록을 위한 활동지.
* **`video`**: 교육적 목적을 지닌 영상 클립.
* **`assessment`**: 퀴즈, 시험, 성취도 측정 도구.
* **`rubric`**: 수행 평가 등을 위한 채점 기준표.
* **`aiPrompt`**: 인공지능 교수 학습 보조를 위한 명령 세트.
* **`manual`**: 장치나 교구의 사용법 및 안전 수칙 설명서.
* **`background`**: 교사 대상의 심화 지식 텍스트.
* **`curriculumMap`**: 자원과 교육과정 간의 연계 구조도.

### 📌 [부록 4] 교육적 용도 (`lrmi:educationalUse`)
자원이 교수 학습 과정의 어떤 단계에서 사용되는지 규정한다.
* **`instruction`**: 수업 중 직접적인 개념 전달 및 활동 유도.
* **`assessment`**: 학습 성취도 진단 및 결과 피드백.
* **`enrichment`**: 성취 기준 도달 후의 심화 및 확장 학습.
* **`remediation`**: 미달 학생을 위한 보충 및 기초 학력 지원.
* **`professionalSupport`**: 교사 연수 및 수업 설계 역량 강화.

### 📌 [부록 5] 난이도 수준 (`edu:difficulty`)
인지적 복잡성과 학습량을 기준으로 한 5단계 척도이다.
* **`Level 1 (Extremely Easy)`**: 기초적 개념 인식, 최소 성취수준 자료.
* **`Level 2 (Easy)`**: 기본적인 원리 이해 및 단순 적용.
* **`Level 3 (Medium)`**: 표준적인 성취기준 달성 수준.
* **`Level 4 (Hard)`**: 복합적 문제 해결 및 비판적 사고 요구.
* **`Level 5 (Extremely Hard)`**: 창의적 재구성 및 심화 프로젝트용.

### 📌 [부록 6] 한국 교육과정 분류 코드 (`kem:classification`)
2022 개정 교육과정 체계에 따른 예시 코드 집합이다.
* **`K22-E-MA`**: 2022 개정 초등 수학 (Elementary Math).
* **`K22-M-SC`**: 2022 개정 중등 과학 (Middle Science).
* **`K22-H-IN`**: 2022 개정 고등 정보 (High Information).

---

## 🛠️ 6. Technical Note: 외부 스키마 모듈화 통합 기법 (`xs:import`)

설계 초기 단계에서 분산되어 배포된 여러 벤더의 표준 규격을 하나의 인스턴스로 바인딩할 때, 요소 선언의 파편화와 네임스페이스 충돌 오류가 빈번히 발생했습니다. 

본 프로젝트는 이를 극복하기 위해 **독립형 분산 스키마 모듈화 아키텍처**를 수립했습니다. 최상위 컨테이너 레이어인 `learningresource.xsd`가 중심축이 되어 고유 타겟 네임스페이스(`http://metadata.edu/schema/`)를 유지한 상태에서, 로컬 경로에 분산된 개별 표준 모듈들(`dc.xsd`, `dct.xsd`, `lrmi.xsd`, `kem.xsd`, `cc.xsd`)을 기술적으로 임포트(`xs:import`)하여 유기적으로 확장 요소들과 격리 바인딩했습니다. 

이러한 모듈 구조적 설계를 통해 인스턴스 XML 파일 내의 `xsi:schemaLocation` 경로가 본 공공 저장소(GitHub Pages) 실시간 웹 주소를 바라보아도 파서 상에서 에러 없이 **유효성 검증(Validation Success)**을 통과했습니다.
