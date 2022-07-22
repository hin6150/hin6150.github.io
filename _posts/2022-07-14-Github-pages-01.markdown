---
layout: post
title: Github Blog 만들기
subtitle: Github Pages를 이용하여 개발 블로그를 만들어 보자.
author: Shinak
categories: develope
tags: [Jekyll, Github, HowTo]
banner:
  image: https://bit.ly/3xTmdUP
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold"
  subheading_style: "color: gold"
sidebar: []
---

## 1-1 글을 시작하며,
Github Page를 이용하여 블로그를 만들면서 나름대로 찾아본 내용들을 정리하여 공유하고자 합니다.

## 1-2 Repository 만들기
먼저 블로그를 만들기 위해서는 Github 계정과 해당 블로그를 작업할 저장소(Repository)가 필요합니다. 자신의 Github에서 Repositories 항목을 찾을 수 있는데, 이것은 Git으로 관리하는 프로젝트 저장소를 뜻하며 말 그대로 파일이나 폴더 등을 저장해 두는 장소 입니다.

위 사진과 같이, Github메인 화면에서 + 아이콘을 클릭해 새로운 저장소를 생성 할 수 있습니다. Github Page에서는 프로젝트, 사용자, 단체의 3가지 종류의 사이트를 제공 하고 있습니다. 이번 프로젝트에서는 개인용 블로그이므로, 사용자 Page를 생성하여 사용할 계획입니다.

Github Pages에 대한 더 자세한 설명은 https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages 해당 링크에서 확인 할 수 있습니다.

사용자 page를 만들기 위해서는 Repository name을 {owner}.github.io와 같은 형식으로 설정하면 됩니다. 저의 경우에는 owner이 hin6150이므로, hin6150.github.io가 됩니다. 이후 Public으로 설정 후 Readme.md파일을 추가 후 Create Repository버튼을 클릭해 저장소를 생성 해 줍니다.

## 1-3 Github Page 생성
이후, 이렇게 생성된 Repository가 웹상에서 확인 할 수 있는 퍼블리싱(Publishing) 작업이 잘 수행되었는지 확인해야 합니다. Setting > Pages로 이동 후 Your site is ready to be published at https://{owner}.github.io/와 같은 문구가 출력되는지 확인 후 해당 링크로 이동하여 정상적으로 화면이 표시되는지 확인합니다.(Repository 생성 후 Page가 생성되기까지 10분정도 소요될 수 있습니다.)

만약 404 에러 화면 대신 {owner}.github.io 문구가 출력이 된다면 정상적으로 웹상에 퍼블리싱 된 것입니다. 단, Readme.md 파일을 생성하지 않은 경우 다르게 표시 될 수 있습니다.

## 1-4 GitHub vs Git, Local vs Remote?
다음 단계는 생성된 저장소에 우리가 만들고자 하는 블로그에 해당하는 파일을 보내주는 것 입니다. 다만, 해당 단계에 들어가기 전에 앞서 Github와 Git이 무엇인지, 그리고 Local 저장소와 Remote 저장소의 차이가 무엇인지 간단하게 확인하고 넘어가도록 하겠습니다.

Git은 분산 버전 관리 시스템이라 불립니다. 풀어서 설명하자면, Git은 저장소에 있는 파일의 변화를 추적합니다. 언제, 누가, 무엇을, 어떻게, 왜 변화를 주었는지 24시간 확인하고 해당 변화를 저장합니다. 그렇기에 사용자는 언제든지 파일이 변한 시점으로 돌아가는 것이 가능합니다. 즉, 파일_최종_최종_최종과 같은 작업을 하지 않아도 된다는 점이죠. 

또한, Git은 하나의 파일에 대한 다양한 가지들을 생성하여 한번에 관리 할 수 있도록 도와줍니다. 하나의 파일에서 여러가지 다른 상황들을 독립적으로 저장이 가능할 뿐만 아니라, 여러 상황들에서 공통된 부분을 한번에 관리 또한 가능하죠. 이러한 특징은 다양한 사람들과 협업을 하는 경우에 개개인이 공통된 프로젝트의 독립적인 버전을 보유 하면서 전체 프로젝트의 관리를 용이하게 도와줍니다.

즉, 분산 버전 관리 시스템은 위와 같은 Git의 특징들을 사용하여 팀프로젝트를 중앙 서버를 통하지 않고 개개인의 작업 환경에서 코드 작업이 가능하도록 도와주는 시스템입니다.

그렇다면 Github란 무엇일까요? Github는 Git을 지원하는 호스팅 플랫폼 입니다. 즉, 우리는 Github를 이용하여 Git을 이용하는 프로젝트들을 여러 다른 사람들과 작업 할 수 있는 것이죠.

자, 여기까지 이해를 하였다면 다음 단계로 수행하는 작업이 무엇인지 감이 올 것입니다. 우리는 Github에 Repository를 만들어 Github Page를 생성하였습니다. 즉 호스팅 플랫폼인 원격(Remote) 저장소가 존재하는 셈이죠. 이러한 원격 저장소에서 작업을 하는 것은 효율이 떨어지므로 개개인의 작업 환경인 Local 저장소에서 작업 후 원격 저장소로 보내주는 작업을 통해야 합니다. 즉, Commit(Local 저장소 변경 사항 저장) & Push(Local > Remote)을 통해 블로그를 꾸미고, 글을 쓰는 작업들을 진행 해야합니다.

## 1-5 Github Desktop, VsCode 설치
Commit & Push를 위한 툴로 저희는 Github Desktop와 VsCode를 설치하여 사용 할 예정입니다. Github Desktop은 Git을 잘 모르더라도 Commit와 Push를 손쉽게 수행 할 수 있도록 도와주는 프로그램이고, VsCode는 사용자로 하여금 개인 작업환경에서 원활하게 작업을 할 수 있도록 도와주는 역할을 합니다.

먼저, Github Desktop을 정상적으로 설치 후 자신의 Github 계정과 연동하였다면 아래와 같은 화면이 보일 것 입니다. 해당 화면은 자신의 Github계정의 Repositories를 보여주는데, 이 중 저희가 작업할 Repository를 선택하여 Clone 합니다. 해당 작업은 Github에 올라와 있는 Repository를 자신의 개인 환경에 복사하여 Github Desktop으로 하여금 추척 하도록 설정하는 작업입니다. Clone을 성공적으로 하였다면, Github Desktop은 실시간으로 Local Repository의 변화를 감지하고 Remote Repository와의 차이점을 확인 할 것입니다. 위에서 설명한 Git의 역할과 유사합니다.

VsCode 또한 정상적으로 설치되었다면 첫번째 메뉴에 Open in Visual Studio Code 탭이 보일 것 입니다. 만약 보이지 않는다면 Select your editor in Options에서 에디터를 선택 할 수 있습니다.

## 1-6 Commit & Push
자, 1장의 마지막 단계입니다. 이제 저희는 Local Repository에 index.html이라는 파일을 생성하여 블로그의 첫 화면을 수정 할 것입니다. 먼저, VsCode를 열어 Local Repository 폴더 안에 index.html 파일을 생성합니다.

```index.html
<!doctype html>
<html>
    <head>
        <title>example 1-2</title>
    </head>
    <body>
        <H2>example 1-2</H2>
        <HR>
        example 1-2
    </body>
</html>
```

저는 위와 같은 간단한 예제 코드들을 이용하여 html을 구성하였습니다. 이후 Github Desktop에서 Local Repository의 변경사항인 index.html이라는 파일이 새로 생겼다는 것을 확인 할 수 있습니다. 이후, Commit to main 버튼을 이용하여 Local Repository의 변경사항을 저장 할 수 있습니다. 그리고 Push to Origin 버튼을 통해서 해당 변경사항을 Remote Repository인 Github로 전송 할 수 있습니다.

이제 자신의 Github page 주소로 이동하면 변경된 블로그를 확인 할 수 있습니다!

## 마무리하며,
틀리거나 미흡한 부분이 있다면 언제든지 지적해주세요! 또한, 해당 포스팅을 따라 진행하던 도중 어려운 부분이나 막히는 부분이 생기면 답글 달아주세요. 최대한 도와드리도록 노력하겠습니다!