---
title: "[serverless] serverless로 AWS Lambda 배포 시 memory, timeout 설정하기"
date: "2020-12-02 22:23:00"
template: "post"
draft: false
category: "serverless"
tags:
  - "AWS"
  - "Lambda"
  - "serverless"
description: "serverless로 aws lamba 함수를 배포할 때, memory, timeout값을 설정하는 방법을 다룹니다."
---

이미지에서 dominant color를 추출하는 AWS Lambda 함수를 Serverless Framework로 배포하여 사용하고 있습니다. 이미지가 클 때 에러가 나는 경우가 있었는데, 너무 오래 걸려서 나는 timeout 이슈였습니다. 동료 개발자분이 Lambda함수의 memory와 timeout설정을 바꿔야겠다고 얘기해주셨습니다.

Lambda함수를 serverless로 배포하면 `memorySize`의 기본값은 `1024`, `timeout`은 `6`초라고 합니다. 이 설정은 aws console에서 확인할 수 있는데, 
Lambda -> 함수 -> 함수 상세 화면 -> 기본 설정에서 아래와 같이 볼 수 있고 편집도 할 수 있습니다.

![image](https://gblobscdn.gitbook.com/assets%2F-MFOfJZX0e3z30df_HuB%2F-MNYWQHF6BYJyVS7gSUq%2F-MNYa7_GaRVMUnjPYL88%2Fimage.png?alt=media&token=40f4f1a6-06d2-4aea-ac78-90c8a127dd15)

aws console에서 설정을 편집할 수 있지만, 새롭게 배포할 때는 serverless.yml에 명시된 설정값으로 배포가 되기 때문에 편집값이 초기화됩니다. 그래서 serverless.yml에 사용할 값을 명시해 주는 것이 좋습니다.

provider 항목의 `memorySize`, `timeout`을 변경해주시면 쉽게 적용할 수 있습니다.

![image](https://gblobscdn.gitbook.com/assets%2F-MFOfJZX0e3z30df_HuB%2F-MNYWQHF6BYJyVS7gSUq%2F-MNYamQjZ5NVijcgcJoq%2Fimage.png?alt=media&token=a91d5af7-6e1b-4b7d-9c5d-074bc0ad96ee)



참고
- [serverless.yml aws guide](https://www.serverless.com/framework/docs/providers/aws/guide/serverless.yml/)
