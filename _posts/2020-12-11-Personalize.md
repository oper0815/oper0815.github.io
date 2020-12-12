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

계정을 만드시고 그 다음에는 계정에 **권한**(IAM)을 부여해야 합니다. 클라우드에 익숙하지 않으면 이 개념이 어색할 수 있는데요, 쉽게 접근하면 '내 계정에 personalize 접근을 허용한다'라는 권한을 부여하는 것입니다. 또한 클라우드에는 스토리지가 있죠? personalize는 AWS의 스토리지인 S3를 통해 데이터를 받아옵니다. 따라서 위 과정에서 S3에 대한 접근 권한도 부여하게 됩니다. 자세한 방법은 2번 reference를 참고해주세요. (이 부분이 진행되지 않으면 이후 진행이 불가능합니다.)

Personalize를 구축하는 방법은 크게 3가지가 있습니다.

1. AWS console

2. AWS Python SDK

3. AWS CLI (Command Line Interface)

1번은 웹 상에서 AWS 콘솔을 통해 진행하며 가장 단순하고 하기 쉽다는 장점이 있습니다. 2번은 AWS CLI를 통해 작업하는 것, 3번은 AWS의 python API를 통해 Python 환경으로 작업하는 방법입니다.

단순한 테스트가 아닌 실제 서비스를 위해서는 스케쥴러, API Gateway 등 연동 부분도 고려해야 하므로 이 때는 2,3번으로 작업을 권장드리며, 지금은 1번 방법을 통한 구축 방법을 알아보겠습니다. 구축 순서는 다음과 같습니다. AWS 문서에 상세히 나와있어서 중요한 부분 위주로만 설명드리겠습니다.

* [S3에 데이터 적재](#S3에-데이터-적재)
* [데이터 로드 및 스키마 설정](#데이터-로드-및-스키마-설정)
* [솔루션 생성](#솔루션-생성)
* [Filter 설정](#Filter-설정)
* [Campaigns 생성](#Campaigns-생성)

## S3에 데이터 적재

위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다. 상세 과정은 다음과 같습니다.
* 버킷 생성
  + S3에 데이터를 저장하기 위해서는 **버킷**이라는 것을 생성해야 합니다. 버킷은 디렉토리 개념이며 버킷 이름은 유일한 이름을 가집니다. 
  + AWS 콘솔에서 S3에 들어가 버킷을 생성합니다.
* 버킷 권한 부여
  + Personalize가 S3에서 데이터를 접근하려면 권한이 필요합니다.
  + AWS Document에 나온대로 ([`Amazon S3 버킷에 업로드`](https://docs.aws.amazon.com/ko_kr/personalize/latest/dg/data-prep-upload-s3.html) 참고)
* 데이터 적재
  + Personalize가 처리할 수 있는 형태로 csv파일을 생성합니다.
  + Interaction.csv(필수), item.csv(선택), user.csv(선택)을 업로드합니다. (자세한 데이터의 형태는 아래에서 다루겠습니다.) 

## 데이터 로드 및 스키마 설정

S3에 데이터를 적재 후, 콘솔 상에서 데이터 로드 및 데이터에 대해 정의해주는 파트입니다.

* Personalize 추천 엔진의 데이터 형태
  + Personalize를 사용하기 위해선 Interaction.csv, user.csv, user.csv가 필요합니다. Interaction은 반드시 필요한 필수 데이터이며, 나머지 2개는 선택사항입니다.
  + Interaction.csv
    - User가 item과 상호작용한 데이터입니다. 필수 항목은 `USER ID`, `ITEM ID`, `TIMESTAMP`입니다.
    - 영화 추천의 경우에는 user가 item을 본 시간이며, 상품 추천의 경우에는 user가 item을 구매 or 클릭한 시간이라고 생각하시면 됩니다.
    - TIMESTAMP는 유닉스 시간을 사용합니다.
    - 이 3가지 외에 칼럼 추가도 가능합니다. 
    ```
    ex)영화 추천
    USER ID | ITEM ID | TIMESTAMP
    김부장    라라랜드   1596161659
    최대리    해리포터   1596166082
    김부장    존윅       1596171438
    ```
  + User.csv
    - 유저의 메타(정보)에 관한 데이터입니다.
    - 나이, 성별 등 유저의 고유 정보에 해당합니다.
    ```
    ex)영화 추천
    USER ID | SEX | AGE ...
    김부장    남    43
    최대리    여    32
    ```
  + Item.csv
    - 아이템의 메타(정보)에 관한 데이터입니다.
    - 가격, 장르 등 아이템의 고유 정보에 해당합니다.
    ```
    ex)영화 추천
    ITEM ID | GENRE | ACTOR | PRICE ...
    해리포터 | 판타지 | 래드클리프  | 0
    신과함께 | 드라마 | 하정우 | 1,000
    ```
    
* Dataset groups 생성
  + Dataset groups는 **프로젝트** 단위의 개념입니다. 콘솔의 `Create dataset Group`을 통해 생성합니다.
  + 이제 Dataset groups에 집어넣을 데이터를 정의해줍니다.
* 스키마 설정
  + Json
  
## 솔루션 생성

위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.

## Filter 설정

위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.

## Campaigns 생성

위에 말씀드린 것과 같이 Personalize는 S3를 통해 데이터를 적재해야 합니다.



## ☝ Reference
1. https://docs.aws.amazon.com/personalize/latest/dg/what-is-personalize.html
2. https://docs.aws.amazon.com/personalize/latest/dg/aws-personalize-set-up-permissions.html
