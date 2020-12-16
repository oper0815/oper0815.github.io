---
title: "Tensorflow Certificate 취득기"
categories:
  - 자격증
tags:
  - Tensorflow certificate
last_modified_at: 2020-12-15
---

자격증 후기 List

1. `Tensorflow certificate`

2. `Google Professional Cloud Architect Certifications`  

3. `AWS Machine Learning-Specialty`

---

이번 포스트에서는 Tensorflow관련 자격증인 `Tensorflow certificate`에 대해 알아보겠습니다.

`Tensorflow certificate`는 구글 공인의 텐서플로우 자격증입니다. 다른 객관식형 자격증 시험과는 다르게 이 시험은 **코딩** 시험으로 텐서플로우 기반의 AI모델링에 대한 문제로 구성되어 있습니다. 저는 9월에 자격증을 취득했고, 자격증 대해서(문제), 자격증 준비 방법, 느낀점&팁에 대해 소개하겠습니다.

<img src="/assets/images/Tensorflow-certificate.JPG" width="100%" height="100%">
<br/>

## 자격증에 대해서 

이 자격증은 위에서 말씀드린 것과 같이 코딩 시험입니다. 상세 가이드는 [여기](https://www.tensorflow.org/extras/cert/TF_Certificate_Candidate_Handbook.pdf)를 참고하시면 되는데 이 중 주요 사항에 대해 말씀드리겠습니다.

* 개발 환경은 Tensorflow 2.x입니다. Tensorflow 1.x과는 다르게 2.x에서는 keras를 지원하고 실제 시험도 keras 라이브러리를 사용합니다.
* 온라인으로 응시했고 파이참을 통해 응시했습니다.(900x600 이상의 웹캠 필요)
* $100
* 총 5시간, 총 5문제
* 문제는 가이드에 나온 유형으로 출시됩니다. (각 대분류에서 하나씩 나오겠죠?)
  1. TensorFlow developer skills
  2. Building and training neural network models using TensorFlow 2.x
  3. Image classification
  4. Natural language processing (NLP)
  5. Time series, sequences and predictions 


## 자격증 준비 방법 & 팁

* 스터디 방법은 [코세라](https://www.coursera.org/professional-certificates/tensorflow-in-practice)로 하는 것이 가장 효과적입니다.
<img src="/assets/images/Tensorflow-certificate1.png" width="100%" height="100%">

* 모델을 짜는 방법도 중요하지만 각 다른 도메인의 데이터를 어떻게 처리하는지도 중요 포인트입니다!
* 시험은 코드 전체를 짜는 것이 아닌 문제에 따라 부분을 채워 넣는 방식으로 진행됩니다.
* 파이참을 통해 응시하는데 플러그인 준비는 미리 준비하세요. 저는 뒤늦게 세팅을 했는데 파이참이 대학원 때 설치한 버전이라 해당 자격증용 플러그인 지원을 안해서 새로 설치한 기억이.. 자세한 방법은 [가이드북](https://www.tensorflow.org/extras/cert/Setting_Up_TF_Developer_Certificate_Exam.pdf)에 있습니다.
* 저는 시험 결제를 하고 업무 때문에 2달 후에 봤는데요. 결제 후 응시 만기 기간은 6개월이라고 합니다. (시험을 보지 못하고 만료될까봐 구글 측에 직접 여쭤봤습니다.)
* 취득하면 링크드인과 Certificate Network에 이름을 게재할 수 있다고 합니다.
* 제출은 계속할 수 있습니다. 원하는 기준에 달성할 때까지 수정하면서 응시하세요.
* 저는 CPU로 응시했는데, 주변분들 후기를 보니 GPU 환경에서도 된다고 하네요. (한 문제에서 학습 시간이 20분 걸렸는데 2번 수정 후 클리어했습니다...)

## 느낀점

* Tensorflow 사용이 익숙한 사람은 몇가지 기본 항목만 학습하면 취득은 쉽다고 생각합니다. 관련 내용을 전혀 모르시는 분이라도 코세라로 학습하고 코딩 위주로 유형에 익숙해지면 그리 어렵지 않을 거 같습니다. 
* AI 전공한 사람들은 보통 영상처리, 자연어처리 등 특정 도메인만 코딩을 해보신 분들이 많은데 이 시험에서는 자연어처리, 영상처리, 시계열 데이터 모두 다루기 때문에 이런 부분에서는 기초를 쌓을 수 있습니다.
* 사실 코딩 수준이 매우 간단하여 주관적인 생각으로는 이 자격증이 있다고 **전문가**라고 보기는 어렵다고 생각합니다. 굳이 따지자면 '텐서플로우를 통해 기본적인 모델을 만들 수 있다.'의 의미정도?? 실제 현업에서 AI를 사용할 때 핵심은 모델링 보다는 데이터 전처리와 데이터 분석(EDA)인데 이런 부분은 시험에 반영이 잘 안되어 있습니다. 그래도 가격이 다른 시험에 비해 저렴하고 준비를 하면서 이전에 까먹은 부분을 다뤘기 때문에 저는 전체적으로는 만족스러웠습니다. 



## ☝ Reference

1. https://www.tensorflow.org/certificate
