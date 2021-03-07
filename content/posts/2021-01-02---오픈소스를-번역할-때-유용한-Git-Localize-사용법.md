---
title: "오픈소스를 번역할 때 유용한 Git Localize 사용법"
date: "2021-01-02 00:48:00"
template: "post"
draft: false
category: "Tools"
tags:
  - "Tools"
  - "Git Localize"
  - "오픈소스"
description: "오픈소스 번역을 도와주는 Git Localize의 사용법을 다룹니다."
---

## 바로가기
1. [등록하기](#register)
2. [번역하기](#translate)
3. [리뷰하기](#review)

<a name="register"></a>
# 등록하기
![Git Localize](https://user-images.githubusercontent.com/32301380/103441476-9e048f80-4c91-11eb-92b2-90674cde683c.png)

### Git Localize는 Git Repository의 내용 번역을 쉽게 도와주는 사이트입니다. [Git Localize](https://gitlocalize.com/)

로그인을 해서 `Add Repository`를 누르면 번역할 대상을 등록할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103441527-005d9000-4c92-11eb-839f-7b103eb0a26d.png)
![image](https://user-images.githubusercontent.com/32301380/103441536-1703e700-4c92-11eb-9b6b-2c55980ddf92.png)

다음으로 번역할 Repository를 고르는데, 접근 권한 설정이 되어 있어야 보이겠죠?
Repository를 고른 뒤에는, 대상 Branch를 작성합니다. 저는 번역용 Branch를 따로 생성해서 PR을 생성할 것이기 때문에 제가 새로 만든 Branch이름을 적었습니다.

`default branch`는 `master`인데, master를 main으로 바꾸신 분들은 main을 적어주세요!

![image](https://user-images.githubusercontent.com/32301380/103441547-2daa3e00-4c92-11eb-8ec3-892e576fe574.png)
![image](https://user-images.githubusercontent.com/32301380/103441603-706c1600-4c92-11eb-8bed-44568d5c06cd.png)

`Project Paths` 항목에서는 Repository 안에서 `번역할 대상을 지정`할 수 있습니다.
`Directory`로 설정하면 해당 Directory에 있는 모든 파일이 대상이 되며, `File`을 선택하면 특정 File만 선택할 수 있습니다.

`%lang%`이라는 placeholder는 번역 세팅에 따라 `target language`로 자동 변환됩니다.
예를 들어서, `target language`를 `ko`로 설정한다면 `Microsoft-Web-Dev-For-Beginners`에 있는 파일들을 번역하면 `Microsoft-Web-Dev-For-Beginners/ko`에 저장됩니다.

![image](https://user-images.githubusercontent.com/32301380/103441644-b628de80-4c92-11eb-8831-e0b19a209bca.png)


저는 모든 파일들을 번역할 것이 아니라 특정 파일들만 번역할 예정이라 `File`로 Path들을 추가해나갔습니다.
`%lang%` 부분이 `target language`로 자동 변환된다고 했죠? 제가 설정한걸 예로 들어보면 
`assignment.md` 파일을 번역하면 `./translations/assignment.ko.md`파일로 저장된다고 볼 수 있습니다!

![image](https://user-images.githubusercontent.com/32301380/103441685-04d67880-4c93-11eb-8172-a961ca59c94c.png)


그 다음엔 `Project languages` 설정입니다. 제가 이 글을 쓰게 된 이유이기도 합니다.
`ko`라고 검색하면 두개가 나오는데 [ko-KR]을 선택하고 제출하면, **계속 로딩만 되고 아무것도 안됩니다.**
**위에 있는 `[ko]`를 선택하셔야 합니다.**
그리고 나서 Submit 버튼을 누르시면 정상적으로 등록됩니다. 😎 파일이 많을수록 로딩이 오래 걸리니 조금만 기다려주시면 됩니다. 준비가 되면 이메일로 알려줍니다.

![image](https://user-images.githubusercontent.com/32301380/103441755-4bc46e00-4c93-11eb-8326-a4ab650983df.png)


등록이 되면 리스트에 등록한 결과가 나오며, 여러가지 메뉴가 나옵니다.
Overview 메뉴에서는 번역 상태를 볼수 있고 번역 언어도 관리할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103441817-d7d69580-4c93-11eb-9c0c-dfea934aea23.png)

Team 메뉴에서는 함께 작업할 유저들을 초대하고 관리할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103441820-e0c76700-4c93-11eb-9485-7998c08219c2.png)

Settings 메뉴에서는 Project Paths를 수정할 수 있으며 Sync Repository, Repository 제거 등을 할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103441821-e58c1b00-4c93-11eb-9e28-2b63d79cbf04.png)

Badge 메뉴에서는 프로젝트의 README.md에 추가할 수 있는 귀여운 배지를 제공해주네요!

![image](https://user-images.githubusercontent.com/32301380/103441822-e8870b80-4c93-11eb-8a84-3c55ee287fb8.png)

<a name="translate"></a>
# 번역하기

번역하려는 파일을 클릭하면 다음과 같은 화면이 나옵니다.

여기서 각각의 블럭들을 `segment`라고 부릅니다. 원본 `segment`랑 번역본 `segment`랑 일대일로 `link`되어 있습니다.

ex) Reading the Docs - 문서 읽기

Git Localize는 `Machine Translate`과 `Pretranslate from TM` 기능을 제공합니다.

![image](https://user-images.githubusercontent.com/32301380/103455092-4a478400-4d2d-11eb-97ce-57c66d250d2f.png)

`Machine Translate`은 말그대로 번역을 자동으로 한번 해주는 기능입니다. 버튼을 클릭하면, 기계가 번역할 수 있는 부분만큼 번역해줍니다. 번역이 막막할 때 큰 도움이 되는 기능입니다.

![image](https://user-images.githubusercontent.com/32301380/103455204-7fa0a180-4d2e-11eb-9b23-deb74d55678a.png)

`Pretranslate from TM`은 `suggestion`을 바탕으로 번역을 해주는 기능입니다. 여기서 `suggestion`은 이전에 다른 파일들을 번역했던 기록을 가지고 제안해주는 기능입니다. 밑에 `Suggestions`에서 그 기록들을 확인할 수 있습니다. 이 기능을 사용하면 협업할 때, `다른 작업자들이 해당 단어를 어떻게 번역했는지` 찾아보지 않아도 파악할 수 있어서 굉장히 좋습니다.
최초에 빨갛게 나오는 부분은 눌러보면 왼쪽의 원본이랑 `링크되지 않는 segment`라고 나오는데 왜 두개씩 나오는지는 아직 파악하지 못했습니다. 같은 것이 두개씩 나온거라서 저는 빨간색 부분은 삭제했습니다.

![image](https://user-images.githubusercontent.com/32301380/103455143-ab6f5780-4d2d-11eb-9446-e735e029c17b.png)

`segment`를 클릭하면 내용을 수정할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103455260-02296100-4d2f-11eb-937d-e47643bffca0.png)

<a name="review"></a>
# 리뷰하기
번역을 완료하면 `Create Review Request` 버튼을 눌러서 리뷰를 요청할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103455358-add2b100-4d2f-11eb-99f2-c79bc3a07791.png)

코멘트를 남기고 제출하면 리뷰 요청 목록에서 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/32301380/103455382-e3779a00-4d2f-11eb-872e-b5542bf31593.png)

![image](https://user-images.githubusercontent.com/32301380/103455397-07d37680-4d30-11eb-9946-48dfe7339c83.png)

파일 이름을 눌러서 들어가보면 Approve할 수 있도록 체크박스가 나옵니다.
**현재 `Approve all` 체크박스를 눌러서 `Approve`한 경우 승인 상황이 저장되지 않는 버그가 있습니다.** report를 넣어야겠네요!😎 `체크박스를 하나하나씩 일일이 눌러야` 저장이 되네요. 확인해보려면 approve후에 다른 페이지에 갔다가 다시 이 페이지로 돌아와보시면 됩니다.

![image](https://user-images.githubusercontent.com/32301380/103455417-5123c600-4d30-11eb-8bfd-33b1d075e2c0.png)

이렇게 나와야 잘 저장된 거겠죠?

![image](https://user-images.githubusercontent.com/32301380/103455509-14a49a00-4d31-11eb-955a-4d6acac73ddf.png)

해당 요청에 코멘트도 남길 수 있고, 리뷰를 마치고 `Send Pull Request` 기능을 활용해서 기존 저장소에 merge를 하면 번역이 끝나겠네요.

![image](https://user-images.githubusercontent.com/32301380/103455669-49fdb780-4d32-11eb-89d7-526808cd5a21.png)

![image](https://user-images.githubusercontent.com/32301380/103455406-35202480-4d30-11eb-9bfb-25d734426b93.png)


`Translated Texts` 메뉴를 이용하면 그 자리에서 번역 요약정보를 확인할 수 있습니다.
![image](https://user-images.githubusercontent.com/32301380/103455545-5cc3bc80-4d31-11eb-8f61-6680f24243f5.png)

이렇게 Git Localize에 등록하는 부분부터 번역, 리뷰하는 방법까지 알아봤습니다. 이번에 처음 써보면서 몇몇 버그도 발견했는데 잘 정리해서 Git Localize측에 알려주고 싶고, 좋은 도구를 찾은 거 같아 기분이 굉장히 좋습니다 :) 영어가 어려워서 번역을 망설이시는 분들도 Git Localize와 함께 다시 시작해보셨으면 하는 바램입니다.
