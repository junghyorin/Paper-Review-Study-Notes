# MOPSA: Mixture of Prompt-Experts Based Speaker Adaptation for Elderly Speech Recognition

## Paper Info
- Title: MOPSA: Mixture of Prompt-Experts Based Speaker Adaptation for Elderly Speech Recognition
- Authors: Chengxi Deng, Xurong Xie, Shujie Hu, Mengzhe Geng, Yicong Jiang, Jiankun Zhao, Jiajun Deng, Guinan Li, Youjun Chen, Huimeng Wang, Haoning Xu, Mingyu Cui, Xunying Liu
- Venue / Year: INTERSPEECH 2025
- Link: https://arxiv.org/abs/2505.24224

## Problem
- Elderly speech recognition은 발음 불명확성, 인지 저하, 화자 간 이질성으로 인해
  기존 ASR foundation model에서 높은 오류율을 보인다.
- 기존 speaker adaptation 기법들은
  (1) unseen speaker에 대한 일반화 부족
  (2) test-time adaptation의 높은 지연
  (3) acoustic 중심의 제한적인 적응
  이라는 한계를 가진다.

## Key Idea
- Prompt-based adaptation과 Mixture-of-Experts(MoE)를 결합한
  **Mixture of Prompt-Experts (MOPSA)**를 제안한다.
- K-means로 클러스터링된 prompt-experts와
  router network를 통해 unseen speaker에 대해
  **zero-shot, real-time adaptation**을 수행한다.
- Encoder prompt와 Decoder prompt를 분리해
  acoustic variability와 linguistic variability를 동시에 모델링한다.

## Why I Read This
- Whisper 기반 ASR에서 speaker adaptation을
  실시간으로 수행하는 방법을 이해하고 싶었다.
- 아동 음성뿐 아니라 고령자 음성에서도 prompt 기반 접근이 얼마나 효과적인지 확인하기 위해 읽었다.

## One-line Takeaway
> 이 논문은 **prompt를 expert 단위로 분해하고 동적으로 조합함으로써,
> Whisper를 고령자 음성에 실시간으로 적응시키는 방법을 제시한다.**

## Materials
- Slides: [`MOPSA: Prompt-Experts based Speaker Adaptation for Elderly ASR (Review Slides)`](slides/MOPSA_%20Mixture%20of%20Prompt-Experts%20Based%20Speaker%20Adaptation%20for%20Elderly%20Speech%20Recognition%20(1).pdf)

> Slides are created for personal study and paper review purposes.
> Figures and experimental results belong to the original authors.

