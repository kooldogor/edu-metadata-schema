# 🎓 FAIR 원칙 기반의 교육 자원 재활용을 위한 메타데이터 스키마 (`edu`)

<!-- 학술적 신뢰도를 높이는 기술 배지 -->
![FAIR Principles](https://img.shields.io/badge/Data_Principle-FAIR-blueviolet?style=flat-square)
![XML Schema](https://img.shields.io/badge/Schema-W3C_XSD-blue?style=flat-square)
![Dublin Core](https://img.shields.io/badge/Standard-Dublin_Core-orange?style=flat-square)
![LRMI](https://img.shields.io/badge/Standard-LRMI_Terms-green?style=flat-square)
![License](https://img.shields.io/badge/License-CC_Standards-lightgrey?style=flat-square)

본 프로젝트는 교수자들이 심혈을 기울여 제작한 교수학습 자원이 단발성으로 소비되는 문제를 해결하기 위해, 오픈 데이터의 핵심인 **FAIR 원칙(Findable, Accessible, Interoperable, Reusable)**에 의거하여 설계된 애플리케이션 프로필(Application Profile) 기반 교육 메타데이터 표준입니다.

---

## 📂 1. 리포지토리 아키텍처 (Directory Tree)
본 저장소는 모듈화된 아키텍처 설계 규격을 준수하여, 메인 스키마가 분할된 개별 외부 표준 스키마 요소를 상호 참조하도록 구성되었습니다.

```text
├── README.md               # 프로젝트 종합 안내서 및 가이드라인 웹 메인
├── learningresource.xsd    # [Main] 최상위 루트 컨테이너 구조 정의 스키마 파일 (FAIR 통합 레이어)
├── cc.xsd                  # Creative Commons 저작권 표준 모듈 스키마 파일 (Reusable 보장)
├── dc.xsd                  # Dublin Core Simple 서지 정보 표준 모듈 스키마 파일 (Findable 보장)
├── dct.xsd                 # Dublin Core Terms 교수학습 방식 정의 모듈 스키마 파일 (Interoperable 보장)
├── kem.xsd                 # KERIS 국가 교육과정 매핑 모듈 스키마 파일 (Interoperable 보장)
├── lrmi.xsd                # LRMI 교육 자원 교육 속성 정의 모듈 스키마 파일 (Reusable 보장)
├── lessonplan_2.xml        # [Sample 1] 물리학Ⅰ 정성적 탐구 수업 지도안 인스턴스 레코드
├── PE.xml                  # [Sample 2] 체육과 뜀틀 단계별 두려움 극복 지도안 인스턴스 레코드
└── worksheet_2.xml         # [Sample 3] 열에너지 보존 법칙 수준별 보충 활동지 인스턴스 레코드
