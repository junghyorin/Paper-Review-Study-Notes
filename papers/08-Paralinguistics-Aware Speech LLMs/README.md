# Paralinguistics-Aware Speech-Empowered Large Language Models for Natural Conversation

## Paper Info
- **Title**: Paralinguistics-Aware Speech-Empowered Large Language Models for Natural Conversation  
- **Authors**:  
  Heeseung Kim, Soonshin Seo, Kyeongseok Jeong, Ohsung Kwon, Soyoon Kim, Jungwhan Kim, Jaehong Lee,  
  Eunwoo Song, Myungwoo Oh, Jung-Woo Ha, Sungroh Yoon, Kang Min Yoo  
- **Affiliations**: Seoul National University, NAVER Cloud, NAVER AI Lab  
- **Venue / Year**: NeurIPS 2024
- **Link**: https://arxiv.org/abs/2402.05706

---

## Problem
기존 LLM 기반 대화 시스템은 대부분 텍스트 중심으로 설계되어 있어,  
음성 대화에서 중요한 운율(prosody), 감정(emotion), 억양(intonation)과 같은  
비언어적 정보(paralinguistics)를 충분히 반영하지 못한다.

일반적인 ASR → LLM → TTS 파이프라인은  
- 음성과 텍스트 간 표현 불일치  
- 단계별 오류 누적(error propagation)  
- 감정 및 억양 정보 손실  

이라는 구조적 한계를 가지며,  
이로 인해 자연스럽고 인간다운 음성 대화 생성에 한계가 있다.

---

## Key Idea
- **USDM (Unified Spoken Dialog Model)** 제안  
  - 음성–텍스트–음성을 하나의 end-to-end LLM 기반 프레임워크로 통합

- **Acoustic Unit 기반 음성 토큰화**
  - self-supervised speech model(XLS-R)의 중간 표현을 k-means(k=10,000)로 양자화
  - 실험을 통해 acoustic unit이 의미 정보뿐 아니라 감정·억양 등  
    paralinguistic 정보를 포함함을 검증

- **Unified Speech–Text Pretraining**
  - 음성과 텍스트를 interleaved sequence로 구성
  - cross-modal 관계를 task-specific objective 대신  
    - Continuation (speech→speech, text→text)  
    - Correspondence (speech ↔ text)  
    로 정의하여 학습

- 음성 대화 생성 과정에서  
  전사 → 응답 텍스트 생성 → 응답 음성 생성을  
  하나의 모델 내부에서 단계적으로 수행하여 LLM의 추론 능력을 적극 활용

---

## Why I Read This
음성과 텍스트를 분리된 모달리티가 아니라  
하나의 연속적인 표현 공간으로 결합하여  
더 자연스러운 대화 생성 방식을 탐구해보고 싶었다.

특히 이 논문은 음성의 비언어적 정보를 단순한 보조 신호가 아니라,  
LLM이 직접 이해하고 생성해야 할 핵심 요소로 다루고 있다는 점에서  
향후 speech-native LLM 및 자연스러운 음성 에이전트 연구에  
중요한 방향성을 제시한다고 느껴 읽게 되었다.

---

## One-line Takeaway
이 논문은 음성과 텍스트를 통합적으로 사전학습한 LLM이  
운율과 의미를 모두 고려한 자연스러운 음성 대화를 생성할 수 있음을 보여준다.

---

## Materials
- **Slides**:  
  `papers/08-Paralinguistics-Aware Speech LLMs/slides/Paralinguistics-Aware Speech-Empowered Large Language Models for Natural Conversation_ppt.pdf`

- 본 슬라이드는 개인 학습 및 논문 리뷰 목적으로 제작되었으며,  
  모든 그림과 실험 결과의 저작권은 원저자에게 있음.

