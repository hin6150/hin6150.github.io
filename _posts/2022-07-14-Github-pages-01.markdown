---
layout: post
title: Github Blog 만들기
subtitle: Github Pages를 이용하여 개발 블로그를 만들어 보자.
author: Shinak
categories: develope
tags: Jekyll Github
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
먼저 블로그를 만들기 위해서는 Github 계정과 해당 블로그를 작업할 저장소(Repositories)가 필요합니다. 자신의 Github에서 Repositories 항목을 찾을 수 있는데, 이것은 Git으로 관리하는 프로젝트 저장소를 뜻하며 말 그대로 파일이나 폴더 등을 저장해 두는 장소 입니다.

위 사진과 같이, Github메인 화면에서 + 아이콘을 클릭해 새로운 저장소를 생성 할 수 있습니다. Github Page에서는 프로젝트, 사용자, 단체의 3가지 종류의 사이트를 제공 하고 있습니다. 이번 프로젝트에서는 개인용 블로그이므로, 사용자 Page를 생성하여 사용할 계획입니다.

Github Pages에 대한 더 자세한 설명은 https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages 해당 링크에서 확인 할 수 있습니다.

사용자 page를 만들기 위해서는 Repository name을 {owner}.github.io와 같은 형식으로 설정하면 됩니다. 저의 경우에는 owner이 hin6150이므로, hin6150.github.io가 됩니다. 이후 Public으로 설정 후 Readme.md파일을 추가 후 Create Repository버튼을 클릭해 저장소를 생성 해 줍니다.

## 1-3 Github Page 생성
이후, 이렇게 생성된 Repository가 웹상에서 확인 할 수 있도록 퍼블리싱(Publishing) 작업이 잘 수행되었는지 확인해야 합니다. Setting > Pages로 이동 후 Your site is ready to be published at https://{owner}.github.io/와 같은 문구가 출력되는지 확인 후 해당 링크로 이동하여 정상적으로 화면이 표시되는지 확인합니다.(Repository 생성 후 Page가 생성되기까지 10분정도 소요될 수 있습니다.)

만약 404 에러 화면 대신 {owner}.github.io 문구가 출력이 된다면 정상적으로 웹상에 퍼블리싱 된 것입니다.

## 1-4 GitHub vs Git, Local vs Remote?
다음 단계는 생성된 저장소에 우리가 만들고자 하는 블로그에 해당하는 파일을 보내주는 것 입니다. 다만, 해당 단계에 들어가기 전에 앞서 Github와 Git이 무엇인지, 그리고 Local 저장소와 Remote 저장소의 차이가 무엇인지 간단하게 확인하고 넘어가도록 하겠습니다.

Git은 분산 버전 관리 시스템이라 불립니다. 풀어서 설명하자면, Git은 저장소에 있는 파일의 변화를 추적합니다. 언제, 누가, 무엇을, 어떻게, 왜 변화를 주었는지 24시간 확인하고 해당 변화를 저장합니다. 그렇기에 사용자는 언제든지 파일이 변한 시점으로 돌아가는 것이 가능합니다. 즉, 파일_최종_최종_최종과 같은 작업을 하지 않아도 된다는 점이죠. 

또한, Git은 하나의 파일에 대한 다양한 가지들을 생성하여 한번에 관리 할 수 있도록 도와줍니다. 하나의 파일에서 여러가지 다른 상황들을 독립적으로 저장이 가능할 뿐만 아니라, 여러 상황들에서 공통된 부분을 한번에 관리 또한 가능하죠.

그렇다면 Github는 무엇일까요?