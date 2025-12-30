# Large Language Models based ASR Error Correction for Child Conversations

## Paper Info
- Title: Large Language Models based ASR Error Correction for Child Conversations
- Authors: Anfeng Xu, Tiantian Feng, So Hyun Kim, Somer Bishop, Catherine Lord, Shrikanth Narayanan
- Venue / Year: INTERSPEECH, 2025
- Link: https://arxiv.org/abs/2505.16212

## Problem
- Automatic Speech Recognition(ASR)은 성인 음성에 비해
  아동 음성에서 현저히 높은 오류율을 보인다.
- 최근 LLM을 활용한 ASR 오류 수정 연구가 증가하고 있으나,
  **아동 대화(child-adult conversation)** 환경에서의 효과는 충분히 분석되지 않았다.

## Key Idea
- LLM을 ASR 후처리 단계에 적용하여
  아동 대화 음성에서 발생하는 ASR 오류를 수정한다.
- Zero-shot ASR 출력과 fine-tuned ASR 출력 모두에 대해
  LLM 기반 오류 수정의 효과와 한계를 체계적으로 분석한다.

## Why I Read This
- 아동 음성 인식은 내가 주로 관심있어하는 분야로 꼭 필요한 논문일 것 같아 읽었다.

## One-line Takeaway
> 이 논문은 **LLM이 아동 음성 ASR 오류를 일부 개선할 수 있지만,
> Whisper와 같은 autoregressive ASR 출력에는 한계가 있음을 보여준다.**

## Materials
- Slides: [`LLM-based ASR Error Correction for Child Conversations (Review Slides)`](slides/Large_Language_Models_based_ASR_Error_Correction_for_Child_Conversations_ppt.pdf)

> Slides are created for personal study and paper review purposes.
> Figures and experimental results belong to the original authors.
