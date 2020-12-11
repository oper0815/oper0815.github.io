---
title: "AWS personalize"
categories:
  - Cloud
tags:
  - 추천알고리즘
last_modified_at: 2020-12-11
---

이번 포스트에서는 퍼블릭 클라우드를 활용한 추천 엔진 구축에 대해 알아보겠습니다.

현재 퍼블릭 클라우드로 추천 시스템을 구축할 수 있는 방법은 다음과 같습니다.

1. AWS Personalize

2. GCP Recommendation

3. Azure Recommendation

이번에 다룰 SaaS 서비스는 **AWS Personalize**로 제 생각에는 클라우드 3사 중 가장 성능이 좋고, 각종 소스가 많아 구축하기 용이하다고 생각됩니다. 현재 저희 회사에서 해당 솔루션을 가지고 상용화를 진행했는데 공유드리기에 적합하다 생각되어 포스트를 남기게 되었습니다.

<img src="/assets/images/peronsal1.JPG" width="35%" height="100%">

이제 Personalize를 통해 추천 실제 엔진을 구축해보겠습니다. 클라우드를 사용하기 위해선 먼저 **계정 생성**을 해주셔야 합니다. 이전에는 계정 생성 시 무료 크레딧을 줬는데 지금은 주는지 확실하게 모르겠네요. 클라우드의 장점은 아시죠? 사용하는 만큼 돈을 낸다는 거! 자세한 전체 방법은 아래 링크에 있으니 해당 document를 참고하시면서 따라해보세요. 혹시라도 문제가 생기거나 궁금한 내용은 댓글로 남겨주세요 :)

계정을 만드시고 그 다음에는 계정에 **권한**(IAM)을 부여해야 합니다. 클라우드에 익숙하지 않으면 이 개념이 어색할 수 있는데요, 쉽게 접근하면 '내 계정에 personalize 접근을 허용한다'라는 권한을 부여하는 것입니다. 또한 클라우드에는 스토리지가 있죠? personalize는 AWS의 스토리지인 S3를 통해 데이터를 받아옵니다. 따라서 위 과정에서 S3에 대한 접근 권한도 부여하게 됩니다. 자세한 방법은 2번 reference를 참고해주세요.

Personalize를 구축하는 방법은 크게 3가지가 있습니다.

1. AWS console

2. AWS Python SDK

3. AWS CLI (Command Line Interface)

1번은 웹 상에서 AWS 콘솔을 통해 진행하며 가장 단순하고 하기 쉽다는 장점이 있습니다. 2번은 AWS CLI를 통해 작업하는 것, 3번은 AWS의 python API를 통해 Python 환경으로 작업하는 방법입니다.

단순한 테스트가 아닌 실제 서비스를 위해서는 스케쥴러, API Gateway 등 연동 부분도 고려해야 하므로 이 때는 2,3번으로 작업을 권장드리며, 지금은 1번 방법을 통한 구축 방법을 알아보겠습니다. 구축 순서는 다음과 같습니다.

* [S3에 데이터 적재](#S3에_데이터_적재)
* [데이터 로드 및 스키마 설정](#데이터_로드_및_스키마_설정)
* [솔루션 생성](#솔루션_생성)
* [Filter 설정](#Filter_설정)
* [Campaigns 생성](#Campaigns_생성)

## S3에_데이터_적재
---
위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.

## 데이터_로드_및_스키마_설정
---
위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.

## 솔루션_생성
---
위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.

## Filter_설정
---
위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.

## Campaigns_생성
---
위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.



## ☝ Reference
1. https://docs.aws.amazon.com/personalize/latest/dg/what-is-personalize.html
2. https://docs.aws.amazon.com/personalize/latest/dg/aws-personalize-set-up-permissions.html
