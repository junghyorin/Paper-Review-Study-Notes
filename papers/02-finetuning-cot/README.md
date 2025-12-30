# On the Impact of Fine-Tuning on Chain-of-Thought Reasoning

## Paper Info
- Title: On the Impact of Fine-Tuning on Chain-of-Thought Reasoning
- Authors: Elita Lobo, Chirag Agarwal, Himabindu Lakkaraju, Luis Chiruzzo, Alan Ritter, Lu Wang
- Venue / Year: NAACL, 2025
- Link: https://arxiv.org/abs/2411.15382

## Problem
- Chain-of-Thought(CoT) prompting은 대형 언어 모델의 추론 성능을 향상시키는 효과적인 기법이다.
- 그러나 실제 환경에서는 모델이 다양한 목적의 fine-tuning을 거치며,
  이 과정이 CoT 기반 추론 능력에 어떤 영향을 미치는지에 대한 분석이 부족하다.

## Key Idea
- Fine-tuning이 모델의 CoT 추론 능력에 미치는 영향을 체계적으로 분석한다.
- Fine-tuning은 CoT 성능을 항상 유지하거나 향상시키지 않으며,
  설정에 따라 **추론 과정의 활용 방식 자체가 변화**할 수 있음을 보인다.

## Why I Read This
- LLM의 추론 능력이 prompting뿐 아니라 학습(fine-tuning) 과정에 의해
  어떻게 변형되는지 이해하고 싶어 읽었다.

## One-line Takeaway
> 이 논문은 fine-tuning이 Chain-of-Thought 추론을 보존하지 않을 수 있으며,
> 모델의 추론 사용 방식 자체를 변화시킬 수 있음을 보여준다.

## Materials
- Slides: [`On the Impact of Fine-Tuning on Chain-of-Thought Reasoning (Review Slides)`](slides/OntheImpactofFine-TuningonChain-of-ThoughtReasoning_ppt.pdf)

> Slides are created for personal study and paper review purposes.
> Figures and experimental results belong to the original authors.
