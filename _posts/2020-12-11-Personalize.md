---
title: "AWS personalize"
categories:
  - Cloud, Recommendation
tags:
  - 추천알고리즘
last_modified_at: 2020-12-11
---

이번 포스트에서는 퍼블릭 클라우드를 활용한 추천 엔진 구축에 대해 알아보겠습니다.

현재 퍼블릭 클라우드로 추천 시스템을 구축할 수 있는 방법은 다음과 같습니다.

1. AWS Personalize

2. GCP Recommendation

3. Azure Recommendation

이번에 다룰 SaaS 서비스는 **AWS Personalize**로 제 생각에는 클라우드 3사 중 가장 성능이 좋고, 각종 소스가 많아 구축하기 용이하다고 생각됩니다.

이제 추천 실제 엔진을 구축해보겠습니다. 클라우드를 사용하기 위해선 먼저 계정 생성을 해주셔야 합니다. 이전에는 계정 생성 시 무료 크레딧을 줬는데 지금은 주는지 확실하게 모르겠네요. 클라우드의 장점은 아시죠? 사용하는 만큼 돈을 낸다는 거! 자세한 방법은 아래 링크에 있으니 해당 document를 참고하시면서 따라해보세요. 

계정을 만드시고 Personalize를 사용하기 위해서는 먼저 계정에 권한을 부여해야 합니다. 클라우드에 익숙하지 않으면 이 개념이 어색할 수 있는데요, 쉽게 접근하면 '내 계정에 




## ☝ Reference
* https://docs.aws.amazon.com/personalize/latest/dg/aws-personalize-set-up-permissions.html
