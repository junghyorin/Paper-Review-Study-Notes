<h2>Paper Info</h2>
<p>
Title: Mitigating Interviewer Bias in Multimodal Depression Detection<br>
Venue: EMNLP Findings 2025
</p>

<h2>Problem</h2>
<p>
임상 인터뷰 기반 우울증 탐지 모델은<br>
환자의 상태가 아니라 interviewer 질문 패턴에 의존하는 문제가 있음<br><br>

특정 질문 자체가 이미 우울 여부를 암시하며<br>
모델이 질문 패턴을 shortcut으로 학습하는 문제가 발생함
</p>

<h2>Key Idea</h2>
<p>
Interviewer bias를 제거하고 환자 중심 신호를 학습하기 위한 구조 제안
</p>
<ul>
  <li>Dialogue-level modeling으로 전체 대화 흐름 반영</li>
  <li>D-CoPE로 위치 + 질문 의미를 함께 반영</li>
  <li>Adversarial learning으로 질문 정보 제거</li>
</ul>

<h2>Methods</h2>
<ul>
  <li>입력: QA pair (질문 + 응답 텍스트 + 음성)</li>
  <li>텍스트: XLM-R, 오디오: Wav2Vec2 사용</li>
  <li>Gated fusion으로 멀티모달 결합</li>
  <li>D-CoPE로 turn 위치 + 질문 의미를 feature에 추가</li>
  <li>Dialogue Transformer로 전체 인터뷰 맥락 학습</li>
  <li>GRL을 통해 질문 스타일(QF) 정보 제거</li>
</ul>

<h2>Results</h2>
<p>
D-CoPE + Adversarial 구조가 가장 안정적인 성능을 보임<br>
interviewer-only 모델도 높은 성능 → bias 존재 확인<br>
질문 정보 제거 + 대화 맥락 반영이 핵심
</p>

<h2>One-line Takeaway</h2>
<p>
질문 패턴에 의존하는 bias를 제거하고<br>
환자 중심 신호를 학습하도록 만든 우울증 탐지 모델
</p>

## Materials
- Slides: [`Mitigating Interviewer Bias in Multimodal Depression Detection (Review Slides)`](papers/10-Mitigating-Interviewer-Bias/Slides/Mitigating%20Interviewer%20Bias%20in%20Multimodal%20Depression%20Detection_%20An%20Approach%20with%20Adversarial%20Learning%20and%20Contextual%20Positional%20Encoding_ppt.pdf)

> Slides are created for personal study and paper review purposes.  
> Figures and experimental results belong to the original authors.
