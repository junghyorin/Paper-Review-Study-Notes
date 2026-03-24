<h2>Paper Info</h2>
<ul>
  <li><strong>Title:</strong> Mitigating Interviewer Bias in Multimodal Depression Detection: An Approach with Adversarial Learning and Contextual Positional Encoding</li>
  <li><strong>Authors:</strong> Enshi Zhang, Christian Poellabauer</li>
  <li><strong>Affiliations:</strong> Florida International University</li>
  <li><strong>Venue / Year:</strong> EMNLP Findings 2025</li>
  <li><strong>Link:</strong> arXiv / EMNLP Findings paper</li>
</ul>

<h2>Problem</h2>
<p>
Clinical interview-based depression detection models can rely on interviewer question patterns rather than the participant’s actual condition.
Certain interviewer prompts may already contain clues about depression status, which allows models to learn shortcuts instead of patient-centered signals.
This issue is especially important because prior work showed that interviewer prompts alone can achieve surprisingly high performance.
</p>

<h2>Key Idea</h2>
<p>
This paper proposes a framework to reduce interviewer bias while preserving useful participant-related depression cues.
The model combines dialogue-level modeling, dialogue-based contextual positional encoding, and adversarial learning.
</p>
<ul>
  <li>Dialogue-level modeling learns the full question-answer flow of the interview</li>
  <li>D-CoPE incorporates both turn position and question semantics</li>
  <li>GRL-based adversarial learning suppresses interviewer question-function information in learned representations</li>
</ul>

<h2>Methods</h2>

<h3>1. Input Structure</h3>
<p>
Each interview is represented as a sequence of question-answer pairs.
For each turn, the interviewer question is used as text, and the participant response is represented with both transcribed text and speech audio.
</p>

<h3>2. Feature Extraction</h3>
<ul>
  <li>Text encoder: XLM-RoBERTa</li>
  <li>Audio encoder: Wav2Vec2-XLSR</li>
  <li>Participant audio features are projected to match the text feature dimension</li>
</ul>

<h3>3. Multimodal Fusion</h3>
<p>
Text and audio features are combined using gated fusion so that the model can emphasize informative modalities and suppress less useful ones.
</p>

<h3>4. D-CoPE</h3>
<p>
Traditional positional encoding only reflects order information.
In clinical interviews, however, the same turn index can have very different meanings depending on the interviewer’s question.
D-CoPE addresses this by combining turn position with question semantics and then adding the resulting contextual positional information to the multimodal fused representation.
</p>

<h3>5. Dialogue Transformer</h3>
<p>
A dialogue-level transformer models dependencies across question-answer turns and captures global interview context.
</p>

<h3>6. Adversarial Learning</h3>
<p>
The model introduces interviewer Question Function labels such as open-ended, supportive, specific probing, and others.
A Gradient Reversal Layer is used so that the learned representation becomes less predictive of these interviewer prompt categories while still remaining useful for depression prediction.
</p>

<h3>7. Prediction Tasks</h3>
<ul>
  <li>Classification with BCE loss</li>
  <li>Regression with MSE loss</li>
</ul>

<h2>Experiments</h2>

<h3>Datasets</h3>
<ul>
  <li>DAIC-WOZ: English clinical interviews</li>
  <li>EATD: Chinese depression dataset</li>
  <li>Androids: Italian depression dataset</li>
</ul>

<h3>Evaluation</h3>
<ul>
  <li>5-fold stratified cross-validation</li>
  <li>Classification metrics: F1, AUC-ROC</li>
  <li>Regression metrics: RMSE, MAE</li>
</ul>

<h3>Baselines and Ablations</h3>
<ul>
  <li>Participant-only, interviewer-only, and multimodal settings</li>
  <li>Ablations removing D-CoPE, adversarial learning, or specific modalities</li>
</ul>

<h2>Results</h2>
<p>
The proposed dialogue transformer with D-CoPE and adversarial learning shows strong and stable performance across datasets.
Ablation results indicate that D-CoPE contributes substantially to performance, and adversarial learning helps reduce reliance on interviewer prompt bias.
The paper also shows that interviewer-only information can still be highly predictive, reinforcing the need for bias mitigation.
</p>

<h2>Bias Analysis</h2>
<p>
The study analyzes where models focus during interviews and finds that interviewer-based evidence is often concentrated in specific later parts of the conversation.
In contrast, participant-based signals are more broadly distributed across the interview.
This supports the claim that models may exploit interviewer prompt patterns as shortcuts.
</p>

<h2>Limitations</h2>
<ul>
  <li>Limited size and diversity of available clinical interview datasets</li>
  <li>Question Function labels are generated automatically with LLMs and may be imperfect</li>
  <li>The framework is mainly designed for dyadic clinical interviews</li>
</ul>

<h2>One-line Takeaway</h2>
<p>
This paper proposes a multimodal dialogue framework that reduces interviewer prompt bias by combining contextual positional encoding and adversarial learning, leading to more reliable depression detection from clinical interviews.
</p>

<h2>Materials</h2>
<p>
Slides:<br>
papers/10-Mitigating-Interviewer-Bias/Slides/Mitigating Interviewer Bias in Multimodal Depression Detection_ An Approach with Adversarial Learning and Contextual Positional Encoding_ppt.pdf
</p>
