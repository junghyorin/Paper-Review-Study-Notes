# Empowering Whisper as a Joint Multi-Talker and Target-Talker Speech Recognition System

## Paper Info
- Title: Empowering Whisper as a Joint Multi-Talker and Target-Talker Speech Recognition System
- Authors: Lingwei Meng, Jiawen Kang, Yuejiao Wang, Zengrui Jin, Xixin Wu, Xunying Liu, Helen Meng
- Venue / Year: INTERSPEECH 2024
- Link: https://arxiv.org/abs/2406.01287

## Problem
- Multi-talker ASR와 Target-talker ASR는 모두 겹침 발화 환경에서의 전사를 목표로 하지만,
  기존 연구들은 두 문제를 **별도로** 다루는 경우가 대부분이다.
- Cascade 방식은 objective mismatch 문제가 있고,
  End-to-End 방식은 보통 모델을 처음부터 학습하거나 full fine-tuning이 필요하다.
- Target-talker ASR의 경우, 외부 speaker embedding extractor에 대한 의존성이 크고,
  비타겟 화자의 전사는 버려지는 경우가 많다.

## Key Idea
- Whisper를 **Speech Foundation Model**로 고정(freeze)한 채,
  소수의 모듈만 추가하여
  **multi-talker ASR와 target-talker ASR를 동시에 해결**하는 joint framework를 제안한다.
- 핵심 구성은 Sidecar Separator, Target Talker Identifier(TTI),
  그리고 Soft Prompt Tuning이다.
- 외부 speaker embedding extractor 없이,
  3초 enrollment 음성만으로 target speaker를 식별한다.

## Why I Read This
- MOPSA의 선행 연구 논문이라서 같은 논문을 읽고 비슷한 생각을 할 수 있는지 궁금해서 읽어보았다.

## One-line Takeaway
> 이 논문은 **Whisper를 거의 건드리지 않고,
> 겹침 발화 인식과 타겟 화자 인식을 동시에 수행하는
> 가장 현실적인 joint ASR 확장 방식**을 제시한다.

## Materials
- Slides: [`Empowering Whisper: Joint Multi-Talker & Target-Talker ASR (Review Slides)`](slides/Empowering%20Whisper%20as%20a%20Joint%20Multi-Talker%20and%20Target-Talker%20Speech%20Recognition%20System_ppt.pdf)

> Slides are created for personal study and paper review purposes.
> Figures and experimental results belong to the original authors.

