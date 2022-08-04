---
title: Github Blog 만들기 -3
author: Shinak
date: 2021-08-02 19:58:00 +0900
categories: [Blogging, Theme]
tags: [Github, HowTo, Jekyll, chripy]
---

## 글을 시작하며
<hr>
이번 포스팅에서는 Jekyll Theme 중 해당 블로그에서 사용하고 있는 [Chripy Theme][1]을 예제로 가져와 해당 Theme를 블로그에 적용하는 것을 시작으로 자신의 블로그에 맞게 설정하는 방법까지 알아보고자 합니다.  
Github 블로그에서 사용하고 있는 수많은 Jekyll Theme를 자신의 블로그에 적용하는 방법은 저마다 다르지만, 큰 틀은 비슷하므로 Chripy theme가 아니더라도 비슷한 맥락으로 다른 Theme에서도 적용할 수 있으리라 생각됩니다.  

## Theme 설치
<hr>

### Download
<hr>
먼저 [Chripy Theme][1]을 다운로드하여 자신의 Local repository에 설치하여야 합니다.  
[링크][1]를 클릭 시 Chripy Theme의 Github repository로 이동하게 되는데, 상단 오른편에 있는 초록색 Code를 클릭 후 Download Zip을 이용하여 다운 후 자신의 repository 폴더에 붙여넣기 해줍니다.  

> *개인적으로는 repository 내 .git 폴더를 제외한 나머지를 모두 삭제 후 붙여넣는 것을 추천드립니다.*
{: .prompt-tip }

붙여넣기를 완료했다면 ruby prompt를 열어 Jekyll local Server을 작동하여 Theme가 올바르게 적용 되었는지 확인합니다.  
```terminal
bundle exec jekyll s
```

![localhost](/assets/img/howTo_github/003/localhost.PNG)
_설치 성공 화면_
올바르게 설치를 완료했다면 localhost:4000을 url에 입력하여 위와 같은 화면이 표시되는지 확인합니다.  
정상적으로 화면이 출력된다면 이제 Github Desktop을 들어가서 Push & Commit을 합니다.  


### Deploy
<hr>
```html
--- layout: home # Index page ---
```
하지만 예제로 사용하는 Chripy Theme에서는 Jekyll 화면과는 다르게 Github 블로그 화면에서는 위와 같이 오류 화면을 출력하는 것을 확인 할 수 있습니다.  
해당 오류는 Chripy Theme가 다른 Theme와는 다르게 Main Branch 에서 Deploy를 시키는 것이 아니라 추가적으로 Branch를 생성하여 Deploy를 하여 블로그 페이지를 생성하기 때문입니다.

> *좀 더 자세한 내용은 [개발자 가이드 페이지][2] 에서 확인 할 수 있습니다.*
{: .prompt-info }

그렇기에 Github 블로그를 생성하기 위해서는 아래와 같은 과정을 거쳐야 합니다.  

1. .github/workflows에 있는 pages-deploy.yml.hook파일을 pages-deploy.yml로 이름 수정하기.  
2. pages-deploy.yml의 4-5번째 줄에 있는 branches: master에서 master을 main으로 수정하기.  
3. Commit & Push 후 Repository에서 Actions 탭에서 Deploy가 성공 했는지 확인하기.  
4. Repository에서 Settings > Pages > Branch을 gh-pages로 수정 후 Save 하기.  

해당 과정을 수행하고 나면 정상적으로 Github Page가 표시되는 것을 확인 할 수 있습니다.
## Theme 수정
<hr>

### _config.yml
<hr>
이제 Github Page에 정상적으로 블로그가 생성된 것을 확인했으면 다시 Local Repository로 돌아와 세부적인 수정을 하도록 하겠습니다.  
블로그 이름, 언어 설정 등등 기본적인 수정사항은 모두 _config.yml에서 설정이 가능합니다.  

_config.yml 파일 내부에 주석으로 자세하게 설명이 되어 있으므로 이 부분은 따로 설명하지 않고 넘어가겠습니다.

### Comments 추가하기
<hr>

해당 Theme에서는 disqus, giscus, utterancse 3가지 댓글 기능을 지원하고 있습니다.  
각각 해당하는 링크를 참조하여 계정 생성을 하신 뒤 active 옆에 활성화 하고 싶은 댓글을 적으신 뒤 해당 댓글에 가서 관련 값들을 입력하시면 활성화가 됩니다.

## 마무리,
<hr>
Chripy Theme를 적용하면서 어려움을 겪었기에 해당 문제를 겪는 분들에게 도움이 되고자 간략하게 글을 적어두었습니다.  
좀 더 자세하게 적지 못한 부분은 추후에 수정을 할 예정입니다만 혹시 저와 같은 어려움을 겪어 Github에 Deploy를 실패하여 포기하시는 분들이 계실 까봐 초안을 업로드 해둡니다.  
감사합니다.

[1]:https://github.com/cotes2020/jekyll-theme-chirpy
[2]:https://chirpy.cotes.page/posts/getting-started/#deployment

