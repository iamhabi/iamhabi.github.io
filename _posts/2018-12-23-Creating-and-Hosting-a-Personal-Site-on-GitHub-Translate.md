---
layout: post
title: "GitHub로 개인 사이트를 만들고 배포하기"
date: 2018-12-23
category: translate
---

> 번역 - <http://jmcglone.com/guides/github-pages/>

> Jekyll을 사용하여 개인 사이트와 블로그를 만들고 GitHub를 사용해 무료로 배포하기 위한 초보자 가이드

이 가이드는 Git과 GitHub 초보자들이 [GitHub Pages](https://pages.github.com/)와 [Jekyll](https://jekyllrb.com/)를 시작할 수 있도록 돕기 위한 것입니다.
여러분이 Git, GitHub와 버전 컨트롤에 대해 거의 알지 한다고 가정합니다.
우리는 HTML과 CSS를 사용할 것이므로 기본적인 것들을 알고 있다면 도움이 될겁니다.
우리는 [Markdown](https://daringfireball.net/projects/markdown/)도 사용할 것이지만 이를 능숙하게 다룰 수 없어도 괜찮습니다.
아이디어는 실천을 함으로써 배우는 것이므로, 이 가이드에서 사용된 코드는 모두 사용 가능하고 [GitHub 저장소](https://github.com/hankquinlan/hankquinlan.github.io/archive/master.zip)에서 다운받을 수도 있습니다. 
여러분의 파일에 코드를 마음껏 복사하셔도 괜찮습니다.

제가 GitHub와 GitHub Pages를 저의 개인 사이트(와 다른 프로젝트들)에 사용한 이유가 궁금하시면 [이 곳](http://jmcglone.com/notes/2014/05/03/using-github-to-create-and-host-a-personal-website)을 참조해주세요.

# 여러분이 알아야 할 것들

*GitHub Pages를 더 많은 사용자들이 이용할 수 있도록 하기 위해, 이 가이드는 github.com의 웹 인터페이스를 사용하여 여러분의 사이트를 만드는 것에 초점을 두고 있습니다. 따라서 Git과 GitHub에 관련된 표준 도구를 일반화합니다.

*Git과 GitHub에 관련된 익숙해지기 위해(예를 들어 명령어나 터미널같은), 여러분이 알고 있어야 할 다른 훌륭한 가이드들이 있습니다. 북마크를 하고 이 가이드를 완전히 읽은 후 읽어보거나 이미 알고 있다면 건너뛰셔도 좋습니다: [Anna Debenham](https://24ways.org/2013/get-started-with-github-pages/), [Thinkful](http://www.thinkful.com/learn/a-guide-to-using-github-pages/), 그리고 [GitHub](https://pages.github.com/)는 GitHub 호스팅이나 Jekyll의 명령어나 로컬 워크플로

또 [이 문서의 끝]()에서는 Git, GitHub Pages, Jekyll과 마크다운에 여러분이 더욱 익숙해질 수 있도록 도와 줄 수 있는 매우 좋은 사이트들을 모아놨습니다. 좋은 가이드를 새로 찾는대로 리스트를 업데이트하겠습니다.

# Git, GitHub 그리고 GitHub Pages가 뭔가요?

Git, GitHub, 그리고 GitHub Pages는 모두 밀접하게 관련되어있습니다. Git은 작업을 하기 위한 것이고 GitHub와 GitHub Pages는 여러분이 완료한 작업을 저장하는 곳이라고 생각하세요. Git을 사용한 프로젝트는 GitHub나 GitHub Pages에 공개적으로 저장되므로 일반적으로 Git은 여러분의 로컬 컴퓨터에서 하는 작업이며, GitHub는 모든 작업을 서버에 공개적으로 저장하는 곳입니다.

## Git

[Git](https://git-scm.com/)은 매 순간 프로젝트 파일의 변경 사항을 추적하는 버전 관리 시스템입니다. Git은 일반적으로 변경된 내용(추가, 삭제된 내용), 파일을 수정한 사람, 파일의 메모 및 주석, 파일이 언제 만들어졌는지를 기록합니다. Git은 주로 자주 협업을 하는 소프트웨어 개발 프로젝트에 사용되어 협업을 가능하게 하고 개선할 수 있도록 도와주는 도구입니다. However, 이런 협업적 성격덕분에 저작 및 편집 업무에서 도움을 주는 도구로써 출판계의 관심을 가지게 되었습니다.

Git은 효율적인 방식으로 파일을 여러 버전으로 유지하고 다른 위치에 저장된 혼란스러운 이름과 수많은 파일들을 juggling(?)하지 않고 시간을 거슬러 찾아보고 싶은 사람들을 위한 것입니다. Git과 버전 관리를 마법의 취소(되돌리기) 버튼처럼 생각하세요.

아래의 그림에서 각각의 단계는 "저장"을 나타냅니다. Git이 없다면 초안과 최종 초안의 사이의 버전으로 되돌아 갈 수 없습니다. *만약 최종 초안에서 첫 단락을 변경하고 싶다면 복구가 불가능한 데이터를 삭제해야 합니다. 이 문제를 해결하려면 "다른 이름으로 저장" 옵션을 사용해 다른 이름으로 저장하고, 새로운 파일에서 첫 단락을 삭제해야합니다.

![](http://jmcglone.com/img/guides/git-basics.png)

*Git의 흐름은 다중 방향입니다. 각 변경 사항의 중요 부분은 버전에서 중요하다고 표시되고, 계속 진행됩니다. 만약 전 단계로 돌아가야 한다면 여러분은 현재 데이터의 손실없이 돌아갈 수 있습니다. 구글 문서의 "revision history"나 위키피디아의 "edit history"가 이런 방식으로 작동합니다. Git은 훨씬 자세하고 더 복잡해질 수 있습니다.

만약 기회가 생기면 [Git에 대한 15분 웹 자습서](http://try.github.io/)를 **강력히 추천**합니다.

## GitHub

GitHub는 Git을 사용한 소프트웨어나 웹 프로젝트(또는 다른 text 기반 프로젝트)를 위한 웹 호스팅 서비스입니다. 많은 경우, 대부분의 코드는 공개적으로 이용가능하고, 개발자들이 코드를 쉽게 조사, 협업, 다운로드, 개선, 혼합, 사용등을 가능하게 합니다. 각 프로젝트의 코드가 저장되는 곳을 저장소라고 부릅니다.

GitHub에는 정말 멋지고 재미있는 저장소들이 정말 많으며, 매일 새로운 저장소가 추가됩니다. GitHub에서 코드를 사용할 수 있도록 해주는 인기있는 소프트웨어 개발 프로젝트들은 다음과 같습니다: 

* [트위터 부트스트랩](https://github.com/twbs/bootstrap), Twitter 개발진들이 만든 첫 모바일 웹사이트를 위한 매우 유명한 프론트-엔드 프레임워크
* [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate), 빠르게 웹사이트를 구축하기 위한 프론트-엔드 템플릿
* 자바스크립트 시각화 라이브러리 [D3](https://github.com/mbostock/d3)
* [Ruby on Rails](), Ruby로 구축한 오픈 소스 웹 프레임워크

흔히 사람들은 그들의 코드를 작성한 파일을 호스팅하기 때문에, Ruby on Rails 프로젝트를 예시로 보듯, 실제로 작성한 코드를 볼 수 있습니다.

![](http://jmcglone.com/img/guides/github-ruby-on-rails.png)

## GitHub Pages

GitHub Pages는 GitHub를 통해 무료로 호스팅되는 공개 웹 페이지입니다. GitHub 유저들은 개인 웹사이트(유저 당 한 사이트)와 특정 GitHub 프로젝트에 대한 사이트를 만들고 호스팅을 할 수 있습니다. Pages는 GitHub와 동일한 방식으로 작업을 할 수 있도록 해주며, 저장소의 이름이 특정 방식으로 지정되어 있고 파일이 HTML이나 마크다운이라면 파일을 웹사이트 형식으로 볼 수 있습니다. GitHub Pages는 GitHub의 *자각 버전입니다. Pages는 또한 우리가 배울 [Jekyll](https://jekyllrb.com/)이라고 부르는 강력한 [사이트 생성기](https://www.staticgen.com/) 포함합니다.

# GitHub Pages 시작하기

만약 이런 개념의 일부가 아직 이해되지 않아도 걱정하지 마세요. 이것을 배우는 가장 좋은 방법은 작업을 시작하는 것이므로 더 이상 시간을 낭비하지 말고 시작해봅시다.

1. 저장소를 생성합시다. GitHub에 로그인을 하고 <https://github.com/new>에 들어가거나 New Repository 아이콘을 클릭하세요.

![](http://jmcglone.com/img/guides/01-create-repo.png)

2. 저장소 이름을 `username.github.io`로 설정하세요. `username`은 여러분의 GitHub 닉네임을 쓰세요. Public이 체크되어있는지 확인하고 저장소 생성 시 README도 생성해주세요. 

![](http://jmcglone.com/img/guides/02-name-repo.png)

3. 저장소 이름 옆에 있는 플러스 아이콘을 눌러 `index.html`파일을 생성하세요.

![](http://jmcglone.com/img/guides/03-01-create-index-page.png)
![](http://jmcglone.com/img/guides/03-02-create-index-page.png)

*GitHub 에디터에 다음 markup을 작성해주세요.

```
<!DOCTYPE html>
<html>
	<head>
		<title>Hank Quinlan, Horrible Cop</title>
	</head>
	<body>
		<nav>
    		<ul>
        		<li><a href="/">Home</a></li>
	        	<li><a href="/about">About</a></li>
        		<li><a href="/cv">CV</a></li>
        		<li><a href="/blog">Blog</a></li>
    		</ul>
		</nav>
		<div class="container">
    		<div class="blurb">
        		<h1>Hi there, I'm Hank Quinlan!</h1>
				<p>I'm best known as the horrible cop from <em>A Touch of Evil</em> Don't trust me. <a href="/about">Read more about my life...</a></p>
    		</div><!-- /.blurb -->
		</div><!-- /.container -->
		<footer>
    		<ul>
        		<li><a href="mailto:hankquinlanhub@gmail.com">email</a></li>
        		<li><a href="https://github.com/hankquinlan">github.com/hankquinlan</a></li>
			</ul>
		</footer>
	</body>
</html>
```

4. `index.html`을 커밋합시다. 페이지의 하단에 변경에 대한 설명을 작성하기 위한 입력창과 파일을 커밋하기 위한 버튼이 있습니다.

![](http://jmcglone.com/img/guides/04-01-commit-index-page.png)

축하합니다! 여러분은 방금 막 여러분의 첫 GitHub 사이트를 만들었습니다. <https://username.github.io>에서 확인해보세요. 보통 사이트가 생성되기까지 5~10분 정도 걸리므로 그 동안 HTML을 꾸며봅시다.

5. To style the content go back to your repository home and create a new file named css/main.css. The css/ before the filename will automatically create a subdirectory called css. Pretty neat.

꾸미지기 위해 저장소로 돌아가서 `css/main.css`로 불리는 파일을 생성해봅시다. 파일 이름 전에 붙이는 `css/`는 자동으로 `css`라는 하위 디렉토리를 생성합니다. 꽤 깔끔하죠.

![](http://jmcglone.com/img/guides/05-01-create-css-file.png)

다음 코드를 `main.css`에 입력해주세요.

```
body {
    margin: 60px auto;
    width: 70%;
}
nav ul, footer ul {
    font-family:'Helvetica', 'Arial', 'Sans-Serif';
    padding: 0px;
    list-style: none;
    font-weight: bold;
}
nav ul li, footer ul li {
    display: inline;
    margin-right: 20px;
}
a {
    text-decoration: none;
    color: #999;
}
a:hover {
    text-decoration: underline;
}
h1 {
    font-size: 3em;
    font-family:'Helvetica', 'Arial', 'Sans-Serif';
}
p {
    font-size: 1.5em;
    line-height: 1.4em;
    color: #333;
}
footer {
    border-top: 1px solid #d5d5d5;
    font-size: .8em;
}

ul.posts { 
    margin: 20px auto 40px; 
    font-size: 1.5em;
}

ul.posts li {
    list-style: none;
}
```

새로 만든 CSS 파일을 꼭 커밋하세요!

![](http://jmcglone.com/img/guides/06-commit-css-file.png)

6. HTML 문서의 `<head>`부분에 CSS 파일을 Link해줍시다. `index.html` 파일로 돌아가서 "Edit" 버튼을 눌러주세요.

![](http://jmcglone.com/img/guides/07-01-edit-index-page.png)

`main.css` 파일을 추가하세요.(추가된 내용은 굵게 표시됩니다.):

```
<!DOCTYPE html>
<html>
	<head>
		<title>Hank Quinlan, Horrible Cop</title>
		<!-- link to main stylesheet -->
		<link rel="stylesheet" type="text/css" href="/css/main.css">
	</head>
	<body>
		<nav>
    		<ul>
        		<li><a href="/">Home</a></li>
	        	<li><a href="/about">About</a></li>
        		<li><a href="/cv">CV</a></li>
        		<li><a href="/blog">Blog</a></li>
    		</ul>
		</nav>
		<div class="container">
    		<div class="blurb">
        		<h1>Hi there, I'm Hank Quinlan!</h1>
				<p>I'm best known as the horrible cop from <em>A Touch of Evil</em> Don't trust me. <a href="/about">Read more about my life...</a></p>
    		</div><!-- /.blurb -->
		</div><!-- /.container -->
		<footer>
    		<ul>
        		<li><a href="mailto:hankquinlanhub@gmail.com">email</a></li>
        		<li><a href="https://github.com/hankquinlan">github.com/hankquinlan</a></li>
			</ul>
		</footer>
	</body>
</html>
```

<https://username.github.io>를 방문해 여러분이 꾸민 사이트를 확인해보세요. <https://hankquinlan.github.io>랑 똑같이 보여야 합니다.

# GitHub Pages에 Jekyll 사용하기