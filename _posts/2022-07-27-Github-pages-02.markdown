---
layout: post
title: Github Blog 만들기 -2
subtitle: Github Pages를 이용하여 개발 블로그를 만들어 보자.
author: Shinak
categories: develope
tags: [Github, HowTo, Jekyll, Ruby]
banner:
  image: /assets/img/howTo_github/home.jpg
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "80vh"
  heading_style: "font-size: 4.25em; font-weight: bold"
  subheading_style: "color: gold"
---
## 2-1 블로그 꾸미기
저번 포스팅에서 Github 블로그를 성공적으로 개설 후 개인 작업환경에서 글을 쓰고 Github DeskTop을 이용하여 자신의 Github 블로그에 포스팅 하였습니다.  
하지만 아직 블로그라기에는 어딘가 조금 많이 부족해 보입니다. 이번 포스팅에서는 블로그에 여러 기능들을 추가하고 꾸미는 작업을 하겠습니다.  
블로그를 꾸미기 위해 저희는 Jekyll이라는 정적 웹 페이지 생성기를 사용할 계획입니다.  

*Note: Jekyll은 Html/Markdown으로 작성한 글을 레이아웃에 맞춰 웹 페이지로 생성해주는 프레임워크입니다.*

### 2-1 ex) 정적 웹 페이지 vs 동적 웹 페이지
그렇다면 정적 웹 페이지는 무엇일까요?  
웹은 크게 두가지로 나뉩니다. 정적(Static) 웹과 동적(Dynamic) 웹 입니다.

먼저, 정적 웹은 말 그대로 고정되어 있는 웹 페이지 입니다. 개발자가 작성한 Html/Css/JavaScript 같은 코드들을 그대로 전달하여 클라이언트의 브라우저에서 보여주는 웹 페이지이죠.  
해당 특성때문에 오해할 수도 있는데 정적 웹 페이지라 하여 매번 꼭 똑같은 화면을 보여주지는 않습니다.  
랜덤 함수나 현재 시간과 같은 내용들을 이용하여 페이지를 구성하면 매번 같은 내용의 코드를 전달하더라도 사용자는 다른 화면을 보게 될 수 있기 때문입니다.

그렇다면 동적 웹 페이지는 어떨까요? 동적 웹 페이지는 상황에 따른 다양한 화면을 표시하는 웹페이지 입니다.  
대표적인 예로 매번 새로운 게시글이 올라오는 SNS가 있습니다. 개발자가 새로운 게시물이 올라올 때 마다 일일이 코드를 수정하는 것이 아니라 서버가 알아서 데이터 베이스를 거쳐 값들을 가져와 사용자에게 업데이트 된 화면을 보여주게 됩니다.  

정리하자면, 정적 웹 페이지는 개발자가 미리 만들어둔 코드들로 이미 구성 되어있는 페이지이고 동적 웹 페이지는 호출될 때 마다 데이터 베이스로부터 데이터들을 가져와 서버가 페이지를 재구성하는 형태입니다.  
따라서 매번 새로운 내용들을 표시해야 되는 주식, 날씨, SNS와 같은 내용의 페이지는 동적 웹 페이지를 이용하는 것이 유리하고 매번 같은 내용을 표시하는 학교나 회사의 소개글, 블로그 같은 경우에는 쉽고 빠른 정적 웹 페이지를 이용하는 것이 효과적일 수 있겠죠.

## 2-2 Ruby 설치하기
이제 왜 정적 웹 페이지 생성기인 Jekyll을 사용해야 하는지 이해했다면 Jekyll을 설치해보겠습니다. Jekyll은 프로그래밍 언어인 Ruby를 통해 제작되었으므로 먼저 Ruby를 설치해야 합니다.

저는 [Ruby 공식 사이트][1]에서 현재 최신 버전인 `Ruby+Devkit 3.1.2-1 (x64)`을 받아 사용하였습니다.

![ruby](/assets/img/howTo_github/002/ruby.png)

정상적으로 설치를 완료하였다면, 왼쪽 아래 윈도우 검색창에서 ruby를 검색하여 Start Command Prompt with Ruby라는 앱을 실행 할 수 있습니다.

## 2-3 Jekyll 설치하기
이후 아래와 같은 명령어를 Prompt에 순차적으로 입력하여 jekyll을 설치해 줍니다.
 ```
 gem install jekyll bundler
 gem install webrick
 ```
*Note: gem은 ruby언어에서 자동으로 프로그램을 받도록 도와주는 패키지 시스템입니다.*


이후 자신의 로컬 repository로 이동해야 합니다. 해당 repository 주소는 VSCode에서 저번에 생성한 index.html을 우클릭 하여 파일 탐색기에서 표시를 클릭하여 확인할 수 있습니다.

![local](/assets/img/howTo_github/002/local.PNG)

또는, Github Desktop에서 Current repository를 클릭 후 밑에 보이는 repository에 커서를 가져다 대고 있거나 우클릭 하여 Show in Explorer으로 확인 할 수 있습니다.

이렇게 로컬 repository 주소를 확인 하였다면 다시 Prompt로 돌아와 "cd {repository 주소}" 명령어를 입력해 줍니다. 저는 저의 repository 주소가 C:\Users\Hin6150\Documents\GitHub\hino61500.github.io 이므로 아래와 같이 입력하였습니다.
```
cd C:\Users\Hin6150\Documents\GitHub\hino61500.github.io
```

만약 해당 경로에 한글이 존재한다면, cd 명령어 입력 후 chcp 65001 입력하여 “Active code page: 65001”가 출력되는지 확인합니다.

*Note: chcp 65001는 utf-8로 인코딩 시키는 명령어 입니다.*

이렇게 repository로 이동하였다면 이제 해당 위치에 Jekyll 폴더를 생성해야 합니다. 설치 명령어는 아래와 같습니다.
```
jekyll new ./
```
만약 <span style="color:red">Conflict: C:/Users/Hin6150/Documents/GitHub/hino61500.github.io exists and is not empty.</span>와 같은 에러가 출력된다면 해당 폴더에 .git을 제외한 파일들을 삭제하거나 jekyll new ./ --trace를 입력하여 해결합니다.

이후 아래와 같은 명령어를 순차적으로 실행한다면 Jekyll 설치는 끝났습니다.
```
bundle install
bundle add webrick
```

마지막으로 아래와 같은 명령어를 실행하여 서버가 정상적으로 실행되는지 확인해야 합니다.
```
bundle exec jekyll server
```
아래와 같은 메세지가 출력되었다면 localhost:4000을 url에 입력하여 서버가 설치되었는지 확인해봅시다.
```
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

![jekyll](/assets/img/howTo_github/002/jekyll.PNG)

이렇게 정상적으로 표시되었다면 성공입니다! Jekyll이 자신의 Local 환경에 정상적으로 설치된 것 입니다.  
이제 Github Desktop으로 가서 Commit to main을 클릭하여 자신의 Github 블로그에서도 해당 화면이 보이는지 확인해봅시다.

![commit](/assets/img/howTo_github/002/commit.PNG)

*Note: 여러개의 수정사항을 commit 할 시 수정내용을 입력해야 commit이 가능해집니다.*

## 2-4 Jekyll 테마 적용하기
Jekyll에는 여러가지 테마들이 존재합니다.

* <http://jekyllthemes.org/>
* <https://jekyllthemes.io/free>
* <http://themes.jekyllrc.org/>
* <https://jamstackthemes.dev/ssg/jekyll/>
* <https://github.com/topics/jekyll-theme>

해당 블로그는 [jekyll-theme-yat][2]이라는 테마를 사용하다 현재 [jekyll-theme-chirpy][3]으로 사용 중 입니다.  
어떤 테마를 선택하던지 기본적인 큰 틀은 똑같지만 자신이 구현하고자 하는 디자인이나 기능들이 포함되어 있는 테마로 블로그를 시작한다면 좀 더 수월하게 자신이 원하는 방향으로 블로그를 만들 수 있습니다.

*Note: 테마는 개인이 만들어 배포하는 것이므로 자잘한 오류들이 포함되어 있을 수 있습니다.*

자신이 원하는 테마를 찾았다면 Download 또는 Github 링크가 존재할 것입니다.  

![theme](/assets/img/howTo_github/002/theme.PNG)

Github 링크 같은 경우에는 해당 링크로 이동 한 뒤에 초록색 Code 버튼을 눌러 Download Zip을 선택하여 다운로드 하시면 됩니다.
해당 화면이 보이지 않는 경우 Repositories로 이동 후 찾으셨던 theme을 선택하셔서 다운로드 하시면 됩니다.

이후 해당 Zip파일을 압축해제하여 자신의 Local Repository로 붙여넣기를 수행하면 같은 파일이 있다는 경고문이 뜨는데, 이때 같은 파일은 덮어쓰기로 처리합니다.

마지막으로 prompt에서 아래 명령어를 입력 후 정상적으로 Jekyll 서버가 작동 하는지 확인합니다.
```
bundle install
```

*Note: 서버 작동 명령어는 bundle exec jekyll s 입니다.*

서버가 정상적으로 작동하는 것 또한 확인했다면 자신의 Github 블로그에 Commit을 통해 블로그에서도 정상적으로 작동이 되었는지 확인합니다.

## 2-5 마무리
만약 2-3 과정에서 정상적으로 서버가 구동되었지만, 2-4 과정에서 이상한 화면이 나왔다면 Theme 문제일 가능성이 높습니다. 다른 Theme을 구하시거나 문제가 되는 부분을 해결하시면 정상적으로 작동 될 것입니다.  

*Note: Jekyll 서버를 실행하게 되면 존재하는 오류 관련된 메세지들이 출력됩니다.*
*Note: Jekyll 서버는 구동하는데 Github Page에 출력이 되지 않는다면 Github Repository에서 Actions 항목에서 이유를 확인 할 수 있습니다.*

[1]:https://rubyinstaller.org/downloads/
[2]:https://github.com/jeffreytse/jekyll-theme-yat
[3]:https://github.com/cotes2020/jekyll-theme-chirpy