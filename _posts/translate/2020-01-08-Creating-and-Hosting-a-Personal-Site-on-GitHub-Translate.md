---
layout: post
title: "github로 개인 사이트를 만들고 배포하기"
date: 2020-01-08
category: translate
---

> Jekyll을 사용하여 개인 사이트와 블로그를 만들고 GitHub를 사용해 무료로 배포하기 위한 초보자 가이드

> 번역 - <http://jmcglone.com/guides/github-pages/>

이 가이드는 Git과 GitHub 초보자들이 [GitHub Pages](https://pages.github.com/)와 [Jekyll](https://jekyllrb.com/)을 시작할 수 있도록 돕기 위해 만들어졌습니다. 여러분이 Git, GitHub와 버전 관리에 대해 거의 알지 한다고 가정하고 있습니다. 우리는 HTML과 CSS를 사용할 것이므로 이들에 대해 기본적인 것들을 알고 있다면 도움이 될 것입니다. [Markdown](https://daringfireball.net/projects/markdown/)도 사용할 것이지만 이를 능숙하게 다룰 필요는 없습니다. 아이디어는 실천을 함으로써 배우는 것이므로, 이 가이드에서 사용된 코드는 모두 사용 가능하고 [GitHub 저장소](https://github.com/hankquinlan/hankquinlan.github.io/archive/master.zip)에서 다운받을 수도 있습니다. 여러분의 프로젝트 파일에 코드를 마음껏 복사하셔도 괜찮습니다.

왜 제 블로그(와 다른 프로젝트)에 GitHub와 GitHub Pages를 사용했는지 궁금하다면 [이 곳](http://jmcglone.com/notes/2014/05/03/using-github-to-create-and-host-a-personal-website)을 참조해주세요.
    
# 여러분이 알아야 할 것들
GitHub Pages를 더 많은 사용자들이 이용할 수 있도록 하기 위해, 이 가이드는 github.com의 웹 인터페이스를 사용하여 여러분의 사이트를 만드는 것에 초점을 두고 있습니다. 따라서 Git과 GitHub에 관련된 표준 도구를 일반화합니다. Git과 GitHub에 익숙해지기 위해(예를 들어 명령어나 터미널같은), 여러분이 알고 있어야 할 다른 훌륭한 가이드들이 있습니다. 북마크를 하고 이 가이드를 완전히 읽은 후 읽어보거나, 이미 알고 있다면 건너뛰셔도 좋습니다: 
Anna Debenham, Thinkful, and even GitHub itself go above and beyond making the command line or local workflow of GitHub hosting and Jekyll templates accessible to a wider audience.
[Anna Debenham](https://24ways.org/2013/get-started-with-github-pages/), [Thinkful](http://www.thinkful.com/learn/a-guide-to-using-github-pages/), 그리고 [GitHub](https://pages.github.com/)는 

또 [이 문서의 끝]()에서는 Git, GitHub Pages, Jekyll과 마크다운에 여러분이 더욱 익숙해질 수 있도록 도와 줄 매우 좋은 사이트들을 모아놨습니다. 좋은 가이드를 찾는대로 리스트를 업데이트하겠습니다.
    
# Git, GitHub 그리고 GitHub Pages가 무엇인가요?

Git, GitHub, 그리고 GitHub Pages는 모두 밀접하게 관련되어 있습니다. Git은 작업을 하기 위한 도구이고 GitHub와 GitHub Pages는 여러분이 한 작업을 저장하는 곳이라고 생각하세요. Git을 사용한 프로젝트는 GitHub나 GitHub Pages에 공개적으로 저장됩니다. 일반적으로 Git은 여러분의 컴퓨터에서 하는 작업이며, GitHub는 모든 작업을 서버에 공개적으로 저장하는 곳입니다.
    
## Git

[Git](https://git-scm.com/)은 프로젝트 파일의 변경 사항을 매 순간 추적하는 버전 관리 시스템입니다. Git은 일반적으로 변경된 내용(추가, 삭제된 내용), 파일을 수정한 사람, 파일의 메모 및 주석, 파일이 언제 만들어졌는지를 기록합니다. Git은 주로 협업을 자주 하는 소프트웨어 개발 프로젝트에 사용되어 협업을 가능하게 하고 개선할 수 있도록 도와주는 도구입니다. 이런 협업적 성격 덕분에 저작 및 편집 업무에서 도움을 주는 도구로써 출판계의 관심을 가지게 되었습니다.

Git은 효율적인 방식으로 여러 버전으로 파일을 유지하고 다른 위치에 저장된 혼란스러운 이름과 수많은 파일들을 파헤치지 않고 시간을 거슬러 찾아보고 싶은 사람들을 위한 것입니다. Git과 버전 관리를 마법의 취소 버튼처럼 생각하세요.

아래의 그림에서 각각의 단계는 "저장"을 나타냅니다. *Git이 없다면 초안과 최종안의 사이의 버전으로 되돌아갈 수 없습니다. 만약 최종안에서 첫 단락 변경하고 싶다면 복구가 불가능한 데이터를 삭제해야 합니다. 이 문제를 해결하려면 "다른 이름으로 저장" 옵션을 사용해 다른 이름으로 저장하고, 새로운 파일에서 첫 단락을 삭제해야 합니다.
    
![](http://jmcglone.com/img/guides/git-basics.png)
    
Git의 흐름은 양방향입니다. 각 변경 사항의 중요 부분은 버전에서 중요하다고 표시되고, 여러분은 계속 진행합니다. 만약 이전 단계로 돌아가야 한다면 여러분은 현재 데이터의 손실 없이 돌아갈 수 있습니다. 구글 문서의 "revision history"나 위키피디아의 "edit history"가 이런 방식으로 작동합니다. Git은 필요하다면 훨씬 자세하고 더 복잡해질 수 있습니다.

만약 기회가 생기면 [Git에 대한 15분 웹 자습서](http://try.github.io/)를 **강력히 추천**합니다.
    
## GitHub

GitHub는 Git을 사용한 소프트웨어나 웹 프로젝트(또는 다른 text 기반 프로젝트)를 위한 웹 호스팅 서비스입니다. 많은 경우에 대부분의 코드는 오픈소스이고, 개발자들이 코드를 쉽게 조사, 협업, 다운로드, 개선, 혼합, 재사용 등을 가능하게 합니다. 각 프로젝트의 코드가 저장되는 곳을 `repository(저장소)`라고 부릅니다.

GitHub에는 정말 멋지고 재미있는 저장소들이 정말 많으며, 매일 새로운 저장소가 추가됩니다. GitHub에서 인기 있는 오픈소스 소프트웨어 개발 프로젝트들은 다음과 같습니다: 

* [트위터 부트스트랩](https://github.com/twbs/bootstrap), *Twitter 개발진들이 만든 첫 모바일 웹사이트를 위한 매우 유명한 프론트-엔드 프레임워크
* [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate), 빠르게 웹사이트를 구축하기 위한 프론트-엔드 템플릿
* 자바스크립트 시각화 라이브러리 [D3](https://github.com/mbostock/d3)
* [Ruby on Rails](https://github.com/rails/rails), Ruby로 구축한 오픈 소스 웹 프레임워크

흔히 사람들은 그들의 코드를 작성한 파일을 호스팅하기 때문에, Ruby on Rails 프로젝트를 예시로 보듯, 실제로 작성한 코드를 볼 수 있습니다.
    
![](http://jmcglone.com/img/guides/github-ruby-on-rails.png)    

##  GitHub Pages

GitHub Pages는 GitHub를 통해 무료로 호스팅 되는 공개 웹 페이지입니다. GitHub 유저들은 개인 웹사이트(유저 당 하나의 웹사이트만 허용됨)와 특정 GitHub 프로젝트에 대한 사이트를 만들고 호스팅을 할 수 있습니다. GitHub Pages는 GitHub와 동일한 방식으로 작업을 할 수 있도록 해주지만, 저장소의 이름이 특정 방식으로 지정되어 있고 파일이 HTML이나 마크다운 형식이라면 파일을 웹사이트처럼 볼 수 있습니다. GitHub Pages는 GitHub의 자기 인식 버전입니다. GitHub Pages는 또한 우리가 배울 [Jekyll](https://jekyllrb.com/)이라고 부르는 강력한 [사이트 생성기](https://www.staticgen.com/) 포함합니다.
    
# GitHub Pages 시작하기

만약 이런 개념의 일부가 아직 이해되지 않아도 걱정하지 마세요. 이것을 배우는 가장 좋은 방법은 직접 해보는 것이므로 더 이상 시간을 낭비하지 말고 시작해봅시다.

1. 
저장소를 생성합시다. GitHub에 로그인을 하고 <https://github.com/new>에 들어가거나 New Repository 아이콘을 클릭하세요.    
    
![](http://jmcglone.com/img/guides/01-create-repo.png)    

{:start="2"}
2. 
저장소 이름을 `username.github.io`로 설정하세요. `username`은 여러분의 GitHub 사용자명(username)을 쓰세요. Public이 체크되어 있는지 확인하고 저장소 생성 시 README도 생성해주세요.    
    
 ![](http://jmcglone.com/img/guides/02-name-repo.png)    

{:start="3"}
3. 저장소 이름 옆에 있는 플러스 아이콘을 눌러 `index.html`파일을 생성하세요.     
    
![](http://jmcglone.com/img/guides/03-01-create-index-page.png)    
![](http://jmcglone.com/img/guides/03-02-create-index-page.png)    

GitHub 편집기에 다음 코드를 작성해주세요.

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

{:start="4"}
4. `index.html`을 커밋해봅시다. 페이지의 하단에 변경에 대한 설명을 작성하기 위한 입력창과 파일을 커밋하기 위한 버튼이 있습니다.    
    
![](http://jmcglone.com/img/guides/04-01-commit-index-page.png)    

축하합니다! 여러분은 방금 막 첫 GitHub 사이트를 만들었습니다. <https://username.github.io>에서 확인해보세요. 보통 사이트가 생성되기까지 5~10분 정도 걸리므로 그동안 HTML을 꾸며봅시다.

{:start="5"}
5. HTML을 꾸미기 위해 저장소로 돌아가서 `css/main.css`라는 파일을 생성해봅시다. 파일 이름 전에 붙이는 `css/`는 자동으로 `css`라는 하위 디렉토리를 생성합니다. 꽤 편리하죠.    
    
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

{:start="6"}      
6. HTML 문서의 `<head>`부분에 CSS 파일을 적용해줍시다. `index.html` 파일로 돌아가서 "Edit" 버튼을 눌러주세요.        
    
![](http://jmcglone.com/img/guides/07-01-edit-index-page.png)    
    
`main.css` 파일을 링크해주세요. (추가된 내용이 굵게 표시됩니다):

```
<!DOCTYPE html>    
<html>    
	<head>    
		<title>Hank Quinlan, Horrible Cop</title>    
		**<!-- link to main stylesheet -->** 
		**<link rel="stylesheet" type="text/css" href="/css/main.css">**  
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

GitHub Pages처럼 Jekyll은 자기인식을 하므로 만약 특정 규칙에 따라 지어진 이름의 폴더나 파일을 추가하고, GitHub에 커밋한다면, Jekyll이 마법같이 여러분의 사이트를 구축할 겁니다.

여러분의 컴퓨터에 Jekyll을 설정하여 사이트를 편집하고 바로 확인 할 수 있도록 하고 준비가 되면 GitHub 저장소에 변경 사항을 push하는 것이 좋지만, 우리는 그렇게 하지 않을 겁니다. 대신에 우리는 Jekyll이 어떻게 작동하는지 빠르게 알아보기 위해 GitHub 웹 인터페이스를 사용하여 우리의 GitHub 저장소에 구축해볼겁니다.    

## Jekyll이 무엇인가요?

Jekyll은 매우 강력한 정적 사이트 생성기입니다. 어떤 면에서, 이것은 사이트의 콘텐츠를 저장하기 위해 데이터베이스를 사용하기 전인 정적 HTML 시대로 돌아가는 겁니다. 개인 사이트같이 복잡한 구조가 없는 간단한 사이트에게 이것은 커다란 장점입니다. GitHub와 함께 사용하는 경우, 파일을 커밋할 때 마다 Jekyll은 여러분의 사이트의 HTML 페이지를 자동으로 재구축할 겁니다.

Jekyll은 템플릿에 의존하기 때문에 여러분의 웹사이트를 더 쉽게 관리합니다. 정적 사이트 생성기를 사용할 때 템플릿 (또는 Jekyll 명명법)은 여러분의의 가장 친한 친구입니다. navigation 아이템의 위치를 추가, 삭제 또는 변경하면 모든 페이지에서 navigatnoin 코드를 변경해야 하는 대신에, Jekyll이 모든 페이지에서 사용되는 레이아웃을 만들 수 있습니다. 이 튜토리얼에서 우리는 여러분의 웹사이트 구축을 도와줄 두 개의 Jekyll 템플릿을 생성할 겁니다.    

## github.com에서 Jekyll 세팅하기

여러분의 사이트에서 Jekyll을 사용하기 위해 [Jekyll 파일 구조](http://jekyllrb.com/docs/structure/)를 따라야 합니다. 이 구조에 대해 배우기 위해 우리의 GitHub 저장소에 이 구조를 구축할 겁니다.    

{:start="7"}
7. `.gitignore` 파일을 생성해주세요. 이 파일은 여러분이 커밋을 할 때마다 Jekyll이 자동으로 생성하는 `_site` 파일을 무시하도록 Git에게 말해줍니다. 이 디렉터리와 안에 있는 모든 파일은 여러분이 커밋을 할 때마다 쓰이므로, 이 디렉터리가 버전 관리되는 것을 원하지 않습니다.    

![](http://jmcglone.com/img/guides/08-01-create-gitignore.png)    

`.gitignore` 파일에 다음 코드를 추가해주세요.

```
_site/
```

{:start="8"}    
8. Jekyll에게 여러분의 프로젝트에 대한 몇가지 기본사항을 알려주는 `_config.yml` 파일을 만들어봅시다. 이 예제에서 우리는 Jekyll에게 우리 사이트의 이름과 우리가 사용할 마크다운의 버전을 알려줍니다.

```
name: Hank Quinian, Horrible Cop     
markdown: kramdown
```

*이 부분에서 여러분이 GitHub 웹 인터페이스를 사용하여 파일을 생성하였다고 믿고, 위 예시에 관한 스크린샷을 첨부하지 않겠습니다*    

{:start="9"}
9. `_layouts` 디렉터리를 생성하고, 디렉터리 안에 `default.html`이라는 이름의 파일을 생성해주세요. (새로운 파일을 생성하면서 디렉터리도 생성할 수 있습니다. 만약 잊어버렸다면 [`main.css` 단계]()를 다시 한번 확인해 주세요.)

이 파일은 `<head>`와 `<footer>`같은 반복되는 요소들을 포함하는 메인 레이아웃입니다. 이제 우리는 더 이상 새로 페이지를 만들 때마다 markup을 반복하여 작성하지 않아도 됩니다. 사이트의 관리가 더욱 쉬워졌죠. 그럼 다음 코드를 `index.html`에서 `default.html`로 옮겨봅시다.

```
<!DOCTYPE html>    
	<html>    
		<head>    
			<title>{% raw %}{{ page.title }}{% endraw %}</title>    
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
			
			{% raw %}{{ content }}{% endraw %}    
			
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

코드에 있는 `{% raw %}{{ page.title }}{% endraw %}`과 `{% raw %}{{ content }}{% endraw %}`를 잘 봐주세요. Jekyll에서 liquid tags라고 불리는 것들입니다. 이것들은 웹 페이지에 내용을 삽입하기 위해 사용됩니다. 자세한 건 잠시 후에 살펴보도록 합시다.    

{:start="10"}
10. 기본 레이아웃을 사용하기 위해 `index.html`을 업데이트해봅시다. 파일의 모든 코드를 다음과 같이 바꿔주세요.

```
---    
layout: default    
title: Hank Quinlan, Horrible Cop    
---    
<div class="blurb">    
	<h1>Hi there, I'm Hank Quinlan!</h1>    
	<p>I'm best known as the horrible cop from <em>A Touch of Evil</em> Don't trust me. <a href="/about">Read more about my life...</a></p>    
</div><!-- /.blurb -->    
```

파일의 상단에 있는 plain text를 주의해서 봐주세요. Jekyll은 이것을 Front-matter라고 부릅니다. 여러분의 사이트에서 이것을 포함한 모든 파일은 Jekyll이 처리할 겁니다. 파일의 첫 부분에 `layout: default`를 작성한 파일을 커밋을 할 때마다 Jekyll은 `_layout/default.html`을 불러와 {% raw %}`{{ content }}`{% endraw %} 부분에 커밋된 파일의 내용을 삽입하여 마법같이 HTML 문서를 생성할 겁니다. 정말 대단하죠!    

## 블로그 설정하기

Jekyll을 베이스로 한 블로그는 우리가 방금 전까지 익숙해진 것과 동일한 규칙을 사용합니다. 하지만 우리는 규칙을 추가함으로써 더 많은 규칙을 따라야 합니다. Jekyll은 여러분이 원하는 대로 사이트를 확장할 수 있도록 허용해주는 매우 융통성있는 친구입니다. 하지만 이 가이드에서는 우리는 오직 다음과 같은 기본 규칙만을 사용할 겁니다: 포스트 생성하기, 포스트 리스트를 보여주는 페이지 만들기, 포스트에 사용될 고유주소(permalink) 만들기, 블로그를 위한 RSS 피드 만들기

블로그의 포스트를 작성할 `post.html`라는 이름의 새로운 레이아웃을 만들고 각각의 포스트를 저장할 `_posts/`라는 폴더도 만들어봅시다.    

{:start="11"}
11. 레이아웃을 생성하는 것으로 시작해봅시다. `_layouts`폴더에 `post.html`을 생성해주세요. 포스트 레이아웃이 기본 레이아웃을 사용하는 것에 주의하시고, 포스트의 제목과 날짜를 표시하기 위해 몇 가지 태그를 추가해줍시다.

```
---    
layout: default    
---    
<h1>{% raw %}{{ page.title }}{% endraw %}</h1>    
<p class="meta">{% raw %}{{ page.date | date_to_string }}{% endraw %}</p>    

<div class="post">    
  {% raw %}{{ content }}{% endraw %}   
</div>    
```

{:start="12"}    
12. 블로그의 포스트를 저장할 `_posts/` 디렉터리를 만들어주세요. 폴더 안에 첫 포스트를 작성해봅시다. Jekyll은 파일의 이름을 짓는 것에 매우 엄격하므로 주의해주세요. 파일의 이름은 꼭 `YYYY-MM-DD-title-of-my-post.md`같은 형식이어야합니다. 이 파일 이름은 블로그 포스트에 사용될 고유주소로 바뀝니다. 그러니 이 예제에서는, `2014-04-30-hank-quinnlan-site-launched.md`라고 지은 파일을 생성합니다.

```
---    
layout: post    
title: "Hank Quinlan, Horrible Cop, Launches Site"    
date: 2014-04-30    
---    

Well. Finally got around to putting this old website together. Neat thing about it - powered by [Jekyll](http://jekyllrb.com) and I can use Markdown to author my posts. It actually is a lot easier than I thought it was going to be.    
```

`.md` 확장자는 마크다운의 약자입니다. 그리고 파일에서 사용된 마크다운 문법은 Jekyll에 의해 HTML로 변경됩니다. Wikitext처럼 [마크다운](https://daringfireball.net/projects/markdown/)은 plain text에 가까운 문법을 사용하는 마크업 언어입니다. 마크다운의 아이디어는 작성자의 방법을 벗어나서 HTML을 빠르게 작성하기 때문에 마크다운을 블로그 작성에 매우 적합하게 만듭니다. 마크다운 문법에 더욱 익숙해지고 싶다면 [마크다운 문법 정리 (PDF)](http://packetlife.net/media/library/16/Markdown.pdf)가 도움이 될 겁니다.

새로 작성한 포스트를 커밋했다면 <http://username.github.io/YYYY/MM/DD/name-of-your-post>로 들어가 확인해보세요.

모든 것이 순조롭지만 독자는 여러분의 포스트의 URL을 정확히 모를 겁니다. 그래서 다음으로 우리는 각 포스트의 제목과 링크를 리스트로 보여주는 페이지를 만들 겁니다. 여러분은 여러분의 메인 페이지에 이 리스트를 만들 수도 있고, 여러분의 포스트 리스트를 담은 페이지를 따로 만들 수도 있습니다. 우리는 후자로 만들 것입니다.    

{:start="13"}
13. `blog` 디렉터리를 만들고 폴더 안에 `index.html` 파일도 만들어주세요. 포스트 리스트를 보여주려면, 우리는 반복문을 사용하여 포스트가 정렬되지 않은 리스트를 만들 겁니다.

```
---    
layout: default    
title: Hank Quinlan's Blog    
---    
	<h1>{% raw %}{{ page.title }}{% endraw %}</h1>    
	<ul class="posts">    

	  {% raw %}{% for post in site.posts %}{% endraw %}    
	    <li><span>{% raw %}{{ post.date | date_to_string }}{% endraw %}</span> » <a href="{% raw %}{{ post.url }}{% endraw %}" title="{% raw %}{{ post.title }}{% endraw %}">{% raw %}{{ post.title }}{% endraw %}</a></li>    
	  {% raw %}{% endfor %}{% endraw %}    
	</ul>    
```

이제 <http://username.github.io/blog/>를 확인해보세요. 여러분이 작성한 첫 포스트가 링크되어 있는 것을 볼 수 있어야 합니다. 정말 잘했어요!


## 블로그 커스터마이징하기    

우리는 이제 막 Jekyll의 기능을 수박 겉핥기 수준으로만 배웠습니다. 이 가이드에서는 블로그에 사용할 수 있는 몇 가지 단계를 더 배워볼 겁니다.

여러분은 아마 블로그 포스트의 URL이 블로그 디렉터리를 포함하지 않는다는 것을 알았을 겁니다. Jekyll을 사용해 우리는 8단계에서 생성한 `_config.yml`를 약간 수정해서 고유주소의 구조를 제어할 수 있게 됩니다. 블로그 디렉터리를 포함하게 하기 위해 고유주소의 구조를 바꿔봅시다.    

{:start="14"}
14. `_config.yml` 파일을 수정해봅시다. 파일 끝부분에 다음 코드를 추가해주세요.

```
permalink: /blog/:year/:month/:day/:title
```

이제 여러분의 포스트는 <http://username.github.io/blog/YYYY/MM/DD/name-of-your-post.>에 표시될 겁니다.

블로그에 RSS 피드를 설정하는 것도 매우 간단합니다. 새로운 포스트를 작성할 때마다, 이것은 RSS 파일에 추가될 겁니다.    

{:start="15"}
15.  `blog/` 디렉터리 안에 `atom.xml`이라는 새로운 파일을 만들고 다음 코드를 추가해주세요:

```
---    
layout: feed    
---    
<?xml version="1.0" encoding="utf-8"?>    
<feed xmlns="http://www.w3.org/2005/Atom">    

	<title>Hank Quinlan's Blog</title>    
	<link href="http://hankquinlan.github.io/blog/atom.xml" rel="self"/>    
	<link href="http://hankquinlan.github.io/blog"/>    
	<updated>{% raw %}{{ site.time | date_to_xmlschema }}{% endraw %}</updated>    
	<id>http://hankquinlan.github.io/blog</id>    
	<author>    
		<name>Hank Quinlan</name>    
		<email>hankquinlanhub@gmail.com</email>    
	</author>    

	{% raw %}{% for post in site.posts %}{% endraw %}    
		<entry>    
			<title>{% raw %}{{ post.title }}{% endraw %}</title>    
			<link href="http://hankquinlan.github.io{% raw %}{{ post.url }}{% endraw %}"/>    
			<updated>{% raw %}{{ post.date | date_to_xmlschema }}{% endraw %}</updated>    
			<id>http://hankquinlan.github.io{% raw %}{{ post.id }}{% endraw %}</id>    
			<content type="html">{% raw %}{{ post.content | xml_escape }}{% endraw %}</content>    
		</entry>    
	{% raw %}{% endfor %}{% endraw %}    

</feed>    
```

이제 사용자가 여러분의 블로그를 구독하기 위해 feed aggregator에 포함할 수 있도록 사이트 어딘가에 RSS 피드를 위한 링크를 포함할 수 있습니다. 피드를 확인하기 위해 <http://username.github.io/blog/atom.xml>를 확인해보세요.

*Note: 크롬을 사용한다면 피드가 에러가 난 것처럼 보일 수 있지만 아닙니다. 크롬은 XML을 표시할 수 없습니다.*


# 마무리    

{:start="16"}
16. 거의 다 끝났습니다! `about/index.html`과 `cv/index.html`을 생성하고 커밋하는 것을 잊지 마세요. 이제 여러분이 어느 정도 요령을 터득한 거 같으니, 저는 이제 물러서서 여러분 스스로가 이 가이드를 끝낼 수 있도록 할 겁니다.    

{:start="17"}
17. 더욱 나아가기 전에, [Git 설치](https://help.github.com/articles/set-up-git)와 [Jekyll](http://jekyllrb.com/docs/installation/)을 읽을 시간을 가지세요. 이 튜토리얼은 웹 브라우저에서 Git에 대한 모든 것을 담고 있지만 실제론 중간지점에 불과합니다. **여러분의 GitHub 저장소에 이미지나 PDF 파일을 올리기 위해서는 이것을 읽어야 할겁니다.** GitHub 튜토리얼과 데스크탑 앱은 로컬 설정을 쉽게 해줍니다. 여러분은 이제 Git과 GitHub의 기본 지식에 대해 많이 알게 되었으므로 이것을 할 수 있어야 합니다. 어서 해보세요!    

# 다음 단계

이 가이드가 여러분에게 Git, GitHub, Jekyll 그리고 여러분의 사이트나 블로그를 구축할 수 있도록 자신감을 불어넣어 줬길 바랍니다. 여러분은 여기서 다른 많은 방향으로 나아갈 수 있습니다. 여러분이 이미 방향에 대한 생각을 시작했겠지만 여러분이 읽을 시간을 들일 가치가 있는 것들을 몇 개 모아봤습니다.

* [_includes](http://yeswejekyll.com/#_includes)를 생성하세요. 이것들은  `_layouts`과 비슷하고, 마크업을  스니펫(snippets)할 뿐이며 `_layouts`과 페이지에 삽입될 수 있습니다.
    * `_include` 파일을 만들고 구글 웹 로그 추적 코드를 `<head>`에 작성하여 여러분의 사이트를 방문한 사람들의 통계를 확인해보세요. 여기 [예제](https://github.com/jmcglone/jmcglone.github.io/blob/master/_includes/analytics.html)가 있습니다
    * 블로그에 댓글기능을 추가하고 싶나요? [DISQUS `_include`](https://github.com/jmcglone/jmcglone.github.io/blob/master/_includes/disqus.html)를 생성하고 [`post.html` 레이아웃에서 호출](https://github.com/jmcglone/jmcglone.github.io/blob/master/_layouts/post.html)하세요.

* github.io라는 URL이 싫은가요? [커스텀 도메인 설정하기](https://help.github.com/articles/using-a-custom-domain-with-github-pages/)

* [Add Blogging Pagination](https://jekyllrb.com/docs/pagination/)

* 더 나은 SEO를 위해 `sitemap.xml` 파일을 만드세요. [GitHub Pages가 자동으로 생성하는 것을 가질 수 있습니다.](https://help.github.com/articles/sitemaps-for-github-pages/) 제 사이트에서 [사용한 것](https://github.com/jmcglone/jmcglone.github.io/blob/master/sitemap.xml)도 확인해보세요.

* 코딩 전문가가 되어 여러분의 사이트의 `개발` branch를 만드세요. 버그를 고치고 새로운 기능을 추가할 때 마다, 여러분은 master branch의 복사본을 생성, 변경, master branch에 branch를 merge할 수 있습니다. [master branch를 깨끗하게 유지하기 위한 것입니다.](https://help.github.com/desktop-classic/guides/contributing/making-changes-in-a-branch/)

* 더 많은 영감이 필요한가요? [Jekyll 개발자들](https://jekyllrb.com/showcase/)이 [Jekyll을 사용한 거대한 사이트들의 리스트](https://github.com/jekyll/jekyll/wiki/Sites)를 어떻게 설정하거나 탐색했는지 확인해보세요.    

# 리소스

이 리스트를 날마다 업데이트하려고 노력하고 있습니다. 여러분이 공유하고 싶은 사이트가 있거나 작동하지 않는 링크가 있다면 [이곳](http://jmcglone.com/contact/)을 통해 알려주세요.    

## Git, GitHub, GitHub Pages

* [Git 문서](https://git-scm.com/doc)
* [15분만에 Git과 GitHub 배우기](http://try.github.io/)
* [GitHub Pages 도움말](https://help.github.com/categories/github-pages-basics/)
* [GitHub 도움말](https://help.github.com/)
* [GitHub 치트 시트](https://github.com/tiimgreen/github-cheat-sheet)
* [GitHub 용어 사전](https://help.github.com/articles/github-glossary/)
* [GitHub for Academics ](http://blogs.lse.ac.uk/impactofsocialsciences/2013/06/04/github-for-academics/)
    
## Jekyll

* [Jekyll을 사용한 사이트](https://github.com/jekyll/jekyll/wiki/Sites)
* [Jekyll에 블로그 등록](http://import.jekyllrb.com/docs/home/)
    
## 마크다운

* [공식 마크다운 사양](https://daringfireball.net/projects/markdown/)
* [출력 가능한 마크다운 정리 시트](http://packetlife.net/media/library/16/Markdown.pdf)
* [마크다운 정리 시트](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/)