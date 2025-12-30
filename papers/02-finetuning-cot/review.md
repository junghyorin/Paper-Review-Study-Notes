# Detailed Review

## 1. Background & Motivation
Fine-tuning은 대형 언어 모델을 특정 도메인이나 태스크에 적응시키는 데 널리 사용되는 기법이다.
그러나 fine-tuning은 성능 향상과 함께 catastrophic forgetting, 안전성 저하,
일반화 능력 감소와 같은 부작용을 초래할 수 있다.

이 논문은 기존 연구에서 상대적으로 덜 다루어진 질문을 제기한다.
**Fine-tuning은 모델의 Chain-of-Thought(CoT) 추론 능력에 어떤 영향을 미치는가?**
특히 단순한 정답 정확도가 아니라,
모델이 생성하는 추론 과정이 실제로 의미 있는지를 분석하는 데 초점을 둔다.

---

## 2. Research Questions
논문은 다음 네 가지 질문을 중심으로 실험을 설계한다.

1. Fine-tuning은 CoT 기반 추론 성능에 어떤 영향을 미치는가?
2. Fine-tuning 이후 CoT 추론은 얼마나 faithful한가?
3. Fine-tuning은 일반화 성능(IID / OOD)에 어떤 영향을 미치는가?
4. QLoRA rank와 같은 fine-tuning 강도는 CoT 성능 저하를 완화할 수 있는가?

이 질문들은 단순한 성능 비교를 넘어,
모델이 **추론을 어떻게 사용하고 있는지**를 이해하는 것을 목표로 한다.

---

## 3. Method Overview
논문은 QLoRA 기반의 supervised fine-tuning(SFT)을 사용하여
LLM을 다양한 reasoning 및 non-reasoning QA 데이터셋에 대해 fine-tune한다.

실험 설계는 크게 두 가지로 구성된다.
- Experiment 1: reasoning / non-reasoning 데이터로 fine-tuning 후 CoT 변화 관찰
- Experiment 2: fine-tuning 전후의 CoT 성능 및 사용 양상 비교

대부분의 fine-tuning 데이터는 중간 추론 단계를 포함하지 않은
QA 쌍으로 구성되며, GSM8K만 예외적으로 reasoning 단계를 포함한다.

---

## 4. Faithfulness of CoT Reasoning
논문은 CoT의 faithfulness를 평가하기 위해 세 가지 테스트를 제안한다.

- **Early Termination**: 추론 체인의 뒷부분을 단계적으로 제거
- **Filler Substitution**: 중간 이후 추론 단계를 의미 없는 토큰으로 대체
- **Paraphrasing**: 추론 단계를 다른 표현으로 재작성

이러한 변형 이후에도 최종 답변이 유지된다면,
해당 추론 단계는 실제 결정에 기여하지 않은 것으로 간주된다.

Faithfulness 평가는 *CoT Prediction Match* 지표를 통해 수행되며,
이 값이 높을수록 오히려 unfaithful reasoning이 많을 가능성을 의미한다.

---

## 5. Experimental Results: CoT Performance
실험 결과는 다음과 같은 경향을 보인다.

- Fine-tuning 이후 CoT 정확도는 특히 수학 추론(GSM8K)에서 크게 감소
- 이 현상은 작은 모델(LLaMA-3-8B)에서 더욱 두드러짐
- GPT-4는 상대적으로 안정적이지만,
  fine-tuning 이후에도 CoT 성능 저하가 관찰됨

즉, fine-tuning은 태스크 성능을 향상시킬 수 있지만,
복잡한 추론 능력을 반드시 보존하지는 않는다.

---

## 6. Experimental Results: CoT Faithfulness
Faithfulness 분석 결과는 CoT 정확도보다 더 중요한 시사점을 제공한다.

- GSM8K에서는 CoT가 비교적 faithful하게 유지됨
- CosmosQA, MedQA, MedMCQA와 같은 데이터셋에서는
  fine-tuning 이후 CoT faithfulness가 크게 감소
- 특히 LLaMA-3-8B를 commonsense 또는 medical QA로 fine-tune할 경우,
  CoT Prediction Match가 증가하여 추론 단계의 실질적 기여가 감소함

이는 모델이 CoT 형식은 유지하되,
실제로는 추론을 덜 활용하도록 학습되었음을 시사한다.

---

## 7. Generalization and Model Size Effects
일반화 성능(IID / OOD) 분석 결과,
모델 크기에 따른 차이가 뚜렷하게 나타난다.

- GPT 계열 모델은 fine-tuning 이후 전반적인 정확도 향상
- LLaMA-3-8B는 특정 데이터셋에 fine-tune할 경우
  다른 reasoning task에서 성능이 크게 저하됨

이는 작은 모델일수록 fine-tuning으로 인해
추론 능력과 일반화 능력이 동시에 손상될 가능성이 크다는 점을 보여준다.

---

## 8. Effect of QLoRA Rank
QLoRA rank를 증가시키면
일반적인 태스크 성능은 일부 개선되지만,
CoT 성능 저하와 faithfulness 감소를 근본적으로 방지하지는 못한다.

이는 단순히 더 많은 파라미터를 학습시키는 것만으로는
CoT degradation 문제를 해결할 수 없음을 의미한다.

---

## 9. Discussion & Implications
이 논문은 다음과 같은 중요한 메시지를 전달한다.

- CoT는 단순한 출력 형식이 아니라 학습 신호에 민감한 추론 전략이다.
- Fine-tuning 데이터가 추론을 요구하지 않을 경우,
  모델은 CoT를 형식적으로만 유지하게 된다.
- 이러한 현상은 특히 작은 모델에서 더 심각하게 나타난다.

이는 LLM의 “추론 능력”에 대해
보다 신중한 해석이 필요함을 시사한다.

---

## 10. My Thoughts
- Whisper나 ASR 후처리에서 단계적 reasoning을 사용하는 경우에도
  fine-tuning이 유사한 부작용을 일으킬 가능성이 있다.
- CoT를 보존하기 위한 reasoning-aware fine-tuning objective가 필요해 보인다.
- 작은 모델을 위한 CoT-preserving fine-tuning은
  독립적인 연구 주제가 될 수 있다.
