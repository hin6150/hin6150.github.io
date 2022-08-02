---
title: Github Blog 만들기 -1
author: Shinak
date: 2021-07-14 18:32:00 +0900
categories: [Blogging, Github]
tags: [Github, Git, HowTo]
---

## 글을 시작하며,
<hr>
Github Page를 이용하여 블로그를 만들면서 나름대로 찾아본 내용들을 정리하여 공유하고자 합니다.  
해당 포스팅에서는 Github Page를 생성한 뒤 Github Desktop을 이용하여 간단한 html 예제 파일을 push 하는 방법을 다룰 예정입니다. 

## Github_Remote Repository  
<hr>
### 1. Repository 만들기
먼저 블로그를 만들기 위해서는 [Github][0] 계정과 해당 블로그를 작업할 저장소(Repository)가 필요합니다.  
자신의 Github에서 Repositories 항목을 찾을 수 있는데, 이것은 Git으로 관리하는 프로젝트 저장소를 뜻하며 말 그대로 파일이나 폴더 등을 저장해 두는 장소 입니다.

![Repository](/assets/img/howTo_github/001/repository.PNG){: .shadow}  

위 사진과 같이, **Github메인 화면에서 + 아이콘을 클릭해** 새로운 저장소를 생성 할 수 있습니다.  
Github Page에서는 프로젝트, 사용자, 단체의 3가지 종류의 사이트를 제공 하고 있습니다. 
하지만 저희가 작업하는 환경은 개인용 블로그이므로, 사용자 Page를 생성하여 사용할 계획입니다.

*Note: Github Pages에 대한 더 자세한 설명은 해당 [링크][1]에서 확인 할 수 있습니다.*


![page](/assets/img/howTo_github/001/repository2.PNG){: .shadow}  

사용자 page를 만들기 위해서는 **Repository name을 `{owner}.github.io`와 같은 형식**으로 설정하면 됩니다.  
예제에서는 owner이 hin61500이므로, hin61500.github.io을 입력하게 됩니다.  
그리고 Public으로 설정 후 Readme.md 파일을 추가 선택을 하고 아래의 Create Repository 버튼을 클릭하여 저장소를 생성 해 줍니다.

### 2. Github Page 생성
이제 이렇게 생성된 Repository가 웹상에서 확인 할 수 있는 퍼블리싱(Publishing) 작업이 잘 수행되었는지 확인해야 합니다.


![Publishing](/assets/img/howTo_github/001/publishing.PNG){: .shadow}

Setting > Pages로 이동 후 **Your site is ready to be published at <https://hino61500.github.io/>**와 같은 문구가 출력되는지 확인 후 해당 링크로 이동하여 정상적으로 화면이 표시되는지 확인합니다.

*Note: Repository 생성 후 Page가 생성되기까지 10분정도 소요될 수 있습니다.*


![Publishing](/assets/img/howTo_github/001/publishing2.PNG){: .shadow}
만약 404 에러 화면 대신 **{owner}.github.io 문구가 출력**이 된다면 정상적으로 웹상에 퍼블리싱 된 것입니다.
  
*Note: Readme.md 파일을 생성하지 않은 경우 다르게 표시 될 수 있습니다.*

### ex) GitHub vs Git?
다음 단계는 생성된 저장소에 우리가 만들고자 하는 블로그에 해당하는 파일을 보내주는 것 입니다.  
다만, 해당 단계에 들어가기 전에 앞서 **Github와 Git이 무엇인지** 간단하게 확인하고 넘어가도록 하겠습니다.

**Git은 분산 버전 관리 시스템**이라 불립니다. 풀어서 설명하자면, **Git은 저장소에 있는 파일의 변화를 추적**합니다.  
언제, 누가, 무엇을, 어떻게, 왜 변화를 주었는지 24시간 확인하고 해당 변화를 저장합니다.  
그렇기에 사용자는 언제든지 파일이 변한 시점으로 돌아가는 것이 가능합니다.  
쉽게 말해서, 파일_최종_최종_최종과 같은 작업을 하지 않아도 된다는 점이죠. 

또한, Git은 **하나의 파일에 대한 다양한 가지**들을 생성하여 한번에 관리 할 수 있도록 도와줍니다.  
하나의 파일에서 여러가지 다른 **상황들을 독립적으로 저장**이 가능할 뿐만 아니라, 여러 상황들에서 **공통된 부분을 한번에 관리** 또한 가능하죠.  
이러한 특징은 다양한 사람들과 협업을 하는 경우에 개개인이 공통된 프로젝트의 독립적인 버전을 보유 하면서 전체 프로젝트의 관리를 용이하게 도와줍니다.

분산 버전 관리 시스템은 위와 같은 Git의 특징들을 사용하여 팀프로젝트를 중앙 서버를 통하지 않고 **개개인의 작업 환경에서 코드 작업이 가능**하도록 도와주는 시스템입니다.

그렇다면 Github란 무엇일까요? **Github는 Git을 지원하는 호스팅 플랫폼** 입니다.  
우리는 Github를 이용하여 Git을 이용하는 프로젝트들을 여러 다른 사람들과 작업 할 수 있는 것이죠.

### ex) Local >> Remote
자, 여기까지 이해를 하였다면 다음 단계로 수행하는 작업이 무엇인지 감이 올 것입니다.  
우리는 Github에 Repository를 만들어 Github Page를 생성하였습니다. 즉 호스팅 플랫폼인 **Github내에 원격(Remote) 저장소가 존재**하는 셈이죠.  
이러한 원격 저장소에서 작업을 하는 것은 즉각적인 피드백이 어려우므로 **개개인의 작업 환경인 Local 저장소에서 작업 후 Remote 저장소로** 보내주는 작업이 훨씬 효율적입니다.  
따라서 Commit(Local 저장소 변경 사항 저장) & Push(Local > Remote)를 통해 블로그를 꾸미고, 글을 쓰는 작업들을 진행하는 것이 좋습니다.

## Local Repository  
<hr>
### 1. Github Desktop, VsCode 설치
Commit & Push를 위한 툴로 저희는 [Github Desktop][2]와 [VsCode][3]를 설치하여 사용 할 예정입니다.  
Github Desktop은 Git을 잘 모르더라도 **Commit와 Push를 손쉽게 수행 할 수 있도록 도와주는 프로그램**이고, VsCode는 사용자로 하여금 **개인 작업환경에서 원활하게 작업**을 할 수 있도록 도와주는 역할을 합니다.

*Note: 자신이 편한 작업 환경이 있다면, 해당 환경에서 진행해도 괜찮습니다.*


![GithubDesktop](/assets/img/howTo_github/001/githubDesktop.PNG){: .shadow}

먼저, Github Desktop을 정상적으로 설치 후 자신의 Github 계정과 연동하였다면 위와와 같은 화면이 보일 것 입니다.  
해당 화면은 자신의 Github계정의 Repositories를 보여주는데, 이 중 **작업할 Repository를 선택하여 Clone** 합니다.

*Note: Clone 버튼은 **Your repositories** 밑에 있는 저장소를 클릭 시 생깁니다.*


![Clone](/assets/img/howTo_github/001/githubDesktop2.PNG){: .shadow}

클릭 시 위와 같은 화면이 표시되는데, 해당 작업은 Github에 올라와 있는 Repository를 자신의 개인 환경에 복사한 뒤 Github Desktop으로 하여금 추척 하도록 설정하는 작업입니다. 즉, Remote 저장소의 내용을 가져와 **Local Repository를 생성하는 작업**입니다.

Clone을 성공적으로 하였다면, Github Desktop은 실시간으로 Local Repository의 변화를 감지하고 Remote Repository와의 차이점을 확인 할 것입니다. 위에서 설명한 Git의 역할과 유사합니다.


![Editor](/assets/img/howTo_github/001/githubDesktop3.PNG){: .shadow}

VsCode 또한 정상적으로 설치되었다면 첫번째 메뉴에 **Open in Visual Studio Code** 탭이 보일 것 입니다.  
만약 보이지 않는다면 Select your editor in <span style="color:skyblue">Options</span>에서 에디터를 선택 할 수 있습니다.

### 2. Commit & Push
<hr>
자, 1장의 마지막 단계입니다.  
이제 저희는 Local Repository에 index.html이라는 파일을 생성하여 블로그의 첫 화면을 수정 할 것입니다.


![index.html](/assets/img/howTo_github/001/index_html.PNG){: .shadow}

먼저, VsCode를 열어 Local Repository 폴더 안에 index.html 파일을 생성합니다.

```shell
<!doctype html>
<html>
    <head>
        <title>example HTML</title>
    </head>
    <body>
        <H2>example HTML</H2>
        <HR>
        example HTML
    </body>
</html>
```
{: file="index.html" }

저는 위와 같은 간단한 예제 코드들을 이용하여 html을 구성하였습니다.


![commit](/assets/img/howTo_github/001/commit.PNG){: .shadow}

Github Desktop에서 Local Repository의 변경사항인 index.html이라는 파일이 새로 생겼다는 것을 확인 할 수 있습니다.  
*Note: 만약, Github Desktop에서 This file is empty가 떠있다면, index.html 파일을 저장해주세요.* 

이후, Commit to main 버튼을 이용하여 Local Repository의 변경사항을 저장 할 수 있습니다. 


![push](/assets/img/howTo_github/001/push.PNG){: .shadow}

그리고 Push to Origin 버튼을 통해서 해당 변경사항을 Remote Repository인 Github로 전송 할 수 있습니다.  
이제 자신의 Github page 주소로 이동하면 변경된 블로그를 확인 할 수 있습니다!

## 마무리하며,
<hr>
틀리거나 미흡한 부분이 있다면 언제든지 지적해주세요!  
또한, 해당 포스팅을 따라 진행하던 도중 어려운 부분이나 막히는 부분이 생기면 답글 달아주세요.  
최대한 도와드리도록 노력하겠습니다!

[0]: https://github.com/
[1]: https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages
[2]: https://desktop.github.com/
[3]: https://code.visualstudio.com/