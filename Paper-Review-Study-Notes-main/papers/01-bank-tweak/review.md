# Detailed Review

## 1. Background & Motivation
Multi-Object Tracking(MOT)에서 ID switch를 줄이기 위해
많은 최신 방법들은 과거 프레임의 객체 특징을 feature bank 형태로 저장한다.
이 구조는 temporal consistency를 강화하지만,
동시에 공격 표면(attack surface)을 확장시킨다.

본 논문은 이러한 feature bank가 adversarial setting에서
얼마나 취약한지를 분석하는 데서 출발한다.

---

## 2. Problem Definition
- 입력: 비디오 시퀀스 및 tracker가 유지하는 feature bank
- 목표: tracker의 ID consistency를 붕괴시키는 adversarial perturbation 생성
- 제약: 시각적으로 눈에 띄지 않는 수준의 perturbation 유지

기존 공격과 달리, 단일 프레임 성능 저하가 아니라
**시간이 지날수록 누적되는 오류**를 유도하는 것이 핵심 목표이다.

---

## 3. Method Overview
BankTweak은 feature bank에 저장되는 representation이
잘못된 방향으로 누적되도록 입력 영상을 미세하게 조작한다.

전체 흐름은 다음과 같다:
1. Tracker가 사용하는 feature bank 구조 분석
2. Feature bank 업데이트 과정에 영향을 주는 gradient 계산
3. 장기적으로 ID confusion을 유도하는 perturbation 생성

이 방식은 tracker 내부 메모리 구조를 직접 겨냥한다는 점에서
일반적인 per-frame attack과 구별된다.

---

## 4. Key Techniques
- Feature bank-aware adversarial optimization
- Temporal accumulation 효과를 고려한 perturbation 설계
- Tracker의 association 단계에 간접적으로 영향을 주는 공격 전략

핵심은 공격이 “현재 프레임”이 아니라
**미래 프레임의 decision을 왜곡하도록 설계되었다는 점**이다.

---

## 5. Experiments & Results
실험 결과는 다음과 같은 경향을 보인다:
- Feature bank를 사용하는 tracker일수록 공격에 더 취약함
- 공격이 진행될수록 ID switch가 점진적으로 증가
- 기존 adversarial attack 대비 장기 추적 성능 저하가 더 큼

이는 feature bank가 robustness를 높이는 동시에
단일 실패가 누적되는 구조적 약점을 가짐을 보여준다.

---

## 6. Strengths
- Tracker 내부 구조(feature bank)를 정면으로 분석한 점
- 시간 축 관점에서 adversarial attack을 설계한 점
- 다양한 tracker에 일반적으로 적용 가능함을 보인 점

---

## 7. Limitations
- Feature bank를 사용하지 않는 tracker에는 적용이 제한적임
- 방어 기법에 대한 논의는 상대적으로 적음
- 실제 물리적 환경에서의 공격 가능성은 추가 검증이 필요함

---

## 8. My Questions & Thoughts
- 

