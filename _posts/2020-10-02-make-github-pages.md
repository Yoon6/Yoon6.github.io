---
title: 깃 허브 페이지 만들기
date: 2020-10-02 22:36:00 +0900
categories: [Programming, Github]
tags: [github-pages]     # TAG names should always be lowercase
---
본인이 Github Pages를 이용하여 블로그를 만든 이유는 깃허브 잔디(contributions) 때문이다. 이 외에는 업로드 속도도 느리고, 사진 게시도 번거롭고, 트래픽관리, 구글 검색노출도 따로 설정해줘야하기 때문에 매우 번거롭고 ATP를 많이 써야한다.  

이 이유가 아니라면 Tistory등을 이용하는 것이 훨씬 좋은 것같다. 그럼에도 한번 세팅해놓으면, 마크다운 문서를 이용한 간단한 업로드를 할 수 있어 노션으로 작성한 문서를 비교적 쉽게 옮길 수 있어 선택했다.

이 포스팅에서는 jekyll을 이용할 것이고, [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/) 이 테마를 이용할 것이다.  [Chirpy-Demo](https://chirpy.cotes.info/) 데모페이지이다.

본 포스팅은 Windows기반으로 작성되었고, Git, Github 기본적인 사용법은 설명하지 않겠다.

# Github Pages 레포지토리 만들기

![Untitled.png](/assets/img/post/2/Untitled.png)

본인의 github에 레포지토리를 생성한다. 이름은 `[USERNAME].github.io`로 한다. 나의 경우는 `Yoon6.github.io`로 해야한다.

그리고 본인의 컴퓨터에 clone을 해오자. 그럼 `.git`과 `README.md`파일만 있을 것이다.

# jekyll 테마 가져오기

다른 테마를 쓰고 싶다면, 아래와 같은 jekyll테마 사이트 많이 있으니 찾아보기 바란다.

[Build software better, together](https://github.com/topics/jekyll-theme)

[Free Jekyll Themes](https://jekyllthemes.io/free)

![Untitled%201.png](/assets/img/post/2/Untitled%201.png)

jekyll-theme을 fork해서 쓰면 훨씬 편하지만, 그렇게하면 잔디(contributions)가 채워지지 않는다.

그래서 본인의 레포지토리에 복사해와서 사용할 것이다.

ZIP파일을 다운받고 위에서 clone해 두었던 local폴더에 내려받고 push를 해주자.

# Ruby, Jekyll 환경 설정하기

jekyll은 루비로 작성되어 있고, 정적 사이트를 만드는 도구이다. 그래서 Ruby도 설치해야한다.

![Untitled%202.png](/assets/img/post/2/Untitled%202.png)

[Ruby-Installer](https://rubyinstaller.org/downloads/)

위 사이트에 들어가서 루비를 다운받자. 본인은 `2.6.6-1(x64)`를 받았다.

설치를 완료하고 Start Command Prompt with Ruby를 실행하자.

![Untitled%203.png](/assets/img/post/2/Untitled%203.png)

- 첫 번째로 아래 명령어를 입력하자.

```bash
>chcp 65001
```

인코딩을 부여하기 위한 명령어로, 설정하지 않을 경우 이후 진행에 오류가 생길 수 있다.

- 위에서 clone했던 `[USERNAME].github.io` 폴더로 이동하자.

```bash
>cd Yoon6.github.io
```

![Untitled%204.png](/assets/img/post/2/Untitled%204.png)

- jekyll 라이브러리등을 설치하자.

```bash
Yoon6.github.io>gem install bundler jekyll minima jekyll-feed tzinfo-data rdiscount
```

```bash
Yoon6.github.io>install bundler
```

- 초기화 설정

```bash
Yoon6.github.io>jekyll new Yoon6.github.io
```

- 로컬에서 실행

```bash
Yoon6.github.io>bundle exec jekyll serve
```

혹시 이 과정에서 tzinfo오류가 발생한다면, root폴더의 Gemfile을 메모장으로 열어서 아래와 같이 

`gem 'tzinfo'`
`gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]`

두 줄을 `jekyll_plugins` 그룹에 넣어주자.

![Untitled%205.png](/assets/img/post/2/Untitled%205.png)

![Untitled%206.png](/assets/img/post/2/Untitled%206.png)

- 접속해보기

[http://127.0.0.1:4000/](http://127.0.0.1:4000/) 이 페이지로 접속해보자.

Chirpy 기본화면으로 설정되어 있을 것이다.

# 초기화, 초기설정

이제부터는 Chirpy테마의 README(tutorial)에 나와있는 내용이다. 다른 테마와는 조금 다를 수도 있지만, jekyll 을 사용하는 테마에서는 대부분 비슷할 것으로 예상된다. 각각의 테마의 tutorial을 참고하자.

## 초기화 하기

- Git bash로 들어가자.

```
$cd Yoon6.github.io
```

위에서 clone했던 폴더로 들어가자.

- init.sh실행하기

```
$bash tools/init.sh
```

`init.sh`를 실행하면 `.travis.xml`과 `_post`폴더의 문서와 `docs`폴더가 삭제된다. 

그리고 자동으로 커밋이 된다.

- push

```
$git add --all
$git commit -m "initialize"
$git push -u origin master
```

add-commit-push해주자.

## 깃허브 게시 설정

위에서 초기화 후 푸시를 해주고 조금 기다리면 깃허브에 gh-pages라는 부모없는(orphan)브랜치가 생겼을 것이다.

~~(만약에 안된다면 저장소를 지웠다가 다시 해보자. 필자는 다른 방법을 찾지 못했다.)~~

![Untitled%207.png](/assets/img/post/2/Untitled%207.png)

이 브랜치를 publishing source로 해주어야한다.

![Untitled%208.png](/assets/img/post/2/Untitled%208.png)

깃 허브는 보안상의 이유로, 깃 허브 페이지를 안전모드로 실행하는데, 이렇게 되면 블로그 게시에 사용되는 자동 툴들을 사용할 수 없다. 그래서 브랜치를 만들어서 Github Actions를 사용할 수 있게 하는 것이다.

이 작업을 하지 않으면 category, tag가 작동하지 않는다.

이제 publishing source는 gh-pages로 해놓고, 포스팅이나 환경설정 등은 master브랜치에 commit/push하면 Github Actions에 의해서 본인의 깃 허브 페이지에 반영되게 된다.

# 페이지 설정

## _config.yml

- `title:` 블로그 이름
- `tagline:` 블로그 이름 및에 설명글
- `url:` 본인의 주소
- `author:` 작성자 이름, 페이지 하단에 표시됨
- `avatar:` 프로필 이미지 설정
- `social:` 이메일, 깃허브, 트위터 등등
- `timezone: Asia/Seoul`로 설정

기본적으로는 이 정도만 바꾸면 된다.

## 포스팅

기본적으로 마크다운 문서로 작성한다. _post폴더에 2020-10-02-this-is-title과 같이 제목을 작성해야한다.

```
---
title: 머신러닝이란?
date: 2020-10-02 17:18:00 +0900
categories: [Programming, ML]
tags: [machine-learning]     # TAG names should always be lowercase
---
```

가장 상단에 위와 같이 제목, 날짜, 카테고리, 태그 등을 설정해준다.

그 밑으로는 마크다운 문법으로 작성해주면 된다.

이미지 업로드의 경우는 `![image1](/assets/img/post/1/untitled.png)`이런 식으로 설정해줘야 웹페이지에서 보였다.

그 외의 옵션들은 [Chirpy](https://chirpy.cotes.info/) 데모페이지의 tutorial을 참고하자.

## 업로드

위에서 했던 방법대로 add/commit/push한다.

```
$git add --all
$git commit -m "initialize"
$git push -u origin master
```

그리고 5-6분 정도 기다리면 업로드가 된다.

이 상태에서는 구글 검색이 안되기 때문에 따로 설정을 해주어야한다.
---

# 참고 자료

[[Jekyll Blog] GitHub 연동 및 Jekyll 설치](https://theorydb.github.io/envops/2019/05/03/envops-blog-github-pages-jekyll/)