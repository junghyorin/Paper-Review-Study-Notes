# BankTweak

## Paper Info
- Title: BankTweak: Adversarial Attack against Multi-Object Trackers by Manipulating Feature Banks
- Authors: Woojin Shin, Donghwa Kang, Daejin Choi, Brent Byunghoon Kang, Jinkyu Lee, Hyeongboo Baek
- Venue / Year: IJCAI 2025
- Link: https://www.ijcai.org/proceedings/2025/206

## Problem
- 최신 Multi-Object Tracker들은 과거 프레임의 특징을 저장하는 feature bank를 활용해
  객체 ID를 안정적으로 유지한다.
- 그러나 기존 adversarial attack들은 이러한 feature bank 구조를 충분히 고려하지 않음

## Key Idea
- Feature bank를 직접 교란하도록 설계된 adversarial perturbation을 통해
  tracker의 장기 ID 유지 성능을 효과적으로 붕괴시킨다.
- 단일 프레임이 아니라 **시간 축 누적 효과**를 노린 공격이라는 점이 핵심...

## Why I Read This
- 학부인턴 첫 시작.

## One-line Takeaway
> 이 논문은 **feature bank라는 “기억 구조”를 공격 지점으로 삼아,
> multi-object tracker의 장기 추적 능력을 무너뜨린다.**

## Materials
- Slides: [`BankTweak review slides`](slides/BankTweak__Adversarial_Attack_against_Multi-Object_Trackers_by_Manipulating_Feature_Banks_(1).pdf)

> Slides are created for personal study and paper review purposes.
> Figures and experimental results belong to the original authors.
