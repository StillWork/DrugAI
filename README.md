# 실습으로 배우는 신약개발 AI (DrugAI)

서울대학교 / 제약바이오 **신약개발 AI** 2일(12시간) 과정 실습 예제입니다.
모든 예제는 **Google Colab** 에서 바로 실행되며, **AI 배경지식 없이** 따라갈 수 있도록 구성했습니다.

> 강사: 김화종 (K-MELLODDY 사업단장) · hjkim3@gmail.com

## 실행 방법
각 노트북 상단의 [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com) 배지를 클릭하면 Colab 에서 바로 열립니다.
위에서부터 `Shift + Enter` 로 실행하세요. 설치 셀은 노트북마다 포함되어 있습니다.

## 예제 구성

| # | 노트북 | 강의 목차 연계 | 핵심 내용 | 데이터 | 환경 |
|:--:|---|---|---|---|---|
| 01 | [Colab·LLM 코딩과 분자 데이터](01_Colab_LLM_Molecules.ipynb) | ①②③ | Colab, LLM 코딩 워크플로우, SMILES·분자 표현형(기술자·지문·그래프), 약물다움 | ESOL 1,128 분자 | CPU 15분 |
| 02 | [머신러닝 기초 — 회귀·분류와 성능 평가](02_ML_Basics_Regression_Classification.ipynb) | ④ | MAE·RMSE·R², 혼동행렬·정밀도·재현율·F1·ROC-AUC, 모델 7종 비교, 과대적합 | ESOL · BBBP | CPU 15분 |
| 03 | [용해도 예측 회귀 모델 (QSAR)](03_QSAR_Solubility_Regression.ipynb) | ⑤ | 표현형별 성능 비교, 전문가 경험식과 대결, 오차 분석, **적용 범위(AD)** | ESOL 1,128 분자 | CPU 10분 |
| 04 | [독성 예측 분류 모델](04_Toxicity_Classification_Tox21.ipynb) | ⑥ | 불균형 데이터, 임계값·비용 기반 판단, PR 곡선, 독성 부분구조, 12개 엔드포인트 | Tox21 7,831 화합물 | CPU 10분 |
| 05 | [딥러닝 모델 유형 비교](05_Deep_Learning_Models.ipynb) | ⑦ | MLP·1D-CNN·LSTM·**GCN**·ChemBERTa 를 같은 문제로 비교, 학습 곡선 | BBBP 2,039 분자 | CPU/GPU 10분 |
| 06 | [모델 최적화](06_Model_Optimization.ipynb) | ⑧ | 특성공학, **스캐폴드 분할**, Grid/Random/**Optuna** 튜닝, 학습곡선, **SHAP**, 모델 카드 | ChEMBL BACE-1 1,513 | CPU 20분 |
| 07 | [가상 스크리닝과 분자 도킹](07_Virtual_Screening_Docking.ipynb) | ⑨ | 스크리닝 깔때기, **농축도(EF)**, **AutoDock Vina 실제 도킹**, 재도킹 검증, 3D 시각화 | BACE 라이브러리 · PDB 4B05 | CPU 15분 |
| 08 | [단백질 구조 예측](08_Protein_Structure_Prediction.ipynb) | ⑩ | AlphaFold DB, **pLDDT·PAE** 해석, 실험 구조와 RMSD 비교, ESMFold, **ESM-2 변이 스캐닝** | AlphaFold DB · PDB · UniProt | CPU 10분 |
| 09 | [신약 타겟 발굴 — 오믹스·네트워크](09_Target_Discovery_Omics_Network.ipynb) | ⑪ | Open Targets, **TCGA 전사체 차등발현**, 아형 분류, **PPI 네트워크 허브**, 타겟 우선순위 | Open Targets · TCGA BRCA · STRING | CPU 5분 |
| 10 | [생성형 AI 분자 설계](10_Generative_Molecular_Design.ipynb) | ⑫ | SMILES 생성모델, 유효성·신규성·다양성·QED·SA 평가, 생성→필터 깔때기, QSAR 연계 | ZINC 사전학습 GPT-2 | CPU/GPU 10분 |
| 11 | [파운데이션 모델과 공개 AI 툴](11_Foundation_Models_and_Public_Tools.ipynb) | 종합 | **ADMET-AI**(104개 항목), **ChemBERTa·MoLFormer** 임베딩·파인튜닝, ChEMBL·PubChem API, LLM 조수 | ChEMBL EGFR · 승인 약물 | CPU/GPU 15분 |

## 데이터 출처 (모두 공개 데이터)
| 데이터 | 출처 | 비고 |
|---|---|---|
| ESOL(Delaney) 용해도 | MoleculeNet / DeepChem | 1,128 분자 |
| BBBP 혈액뇌장벽 | MoleculeNet | 2,039 분자 |
| Tox21 | NIH·EPA·FDA 공동 | 7,831 화합물 × 12 시험 |
| BACE-1 | MoleculeNet (ChEMBL 기반) | 1,513 분자 |
| ChEMBL | EMBL-EBI REST API | 실시간 조회 |
| PubChem | NIH PUG REST API | 실시간 조회 |
| PDB 4B05 | RCSB PDB | BACE-1 + AZD3839 |
| AlphaFold DB | EMBL-EBI | 예측 구조·PAE·AlphaMissense |
| Open Targets | Open Targets Platform | 질병-타겟 연관 |
| TCGA BRCA | cBioPortal API | 981 환자 전사체 |
| STRING | STRING-DB | 단백질 상호작용 |

`data/` 폴더에는 API 응답이 느리거나 중단될 때를 대비한 **스냅샷 파일**이 들어 있습니다.
노트북은 실시간 API 를 먼저 시도하고, 실패하면 자동으로 스냅샷을 사용합니다.

## 학습 흐름
```
01 분자 표현형 ─┬─> 03 물성 예측(회귀) ─┐
                ├─> 04 독성 예측(분류) ─┤
02 성능 평가 ───┘                      ├─> 06 모델 최적화 ─> 07 스크리닝·도킹
05 딥러닝 모델 유형 ────────────────────┘                        ↑
09 타겟 발굴 ─> 08 표적 구조 예측 ──────────────────────────────┘
10 생성형 설계 ─> 11 파운데이션 모델·공개 툴 (ADMET 평가)
```

## 환경
- Google Colab (권장) — 설치 불필요
- GPU(T4) 권장: 05, 10, 11
- 로컬 실행 시: Python 3.10+ / `pip install rdkit scikit-learn xgboost torch transformers optuna shap py3Dmol vina meeko admet-ai`

## 라이선스
교육용으로 자유롭게 사용하실 수 있습니다. 각 데이터셋은 원 출처의 라이선스를 따릅니다.
