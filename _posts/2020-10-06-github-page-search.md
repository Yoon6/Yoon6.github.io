---
title: Github Pages Search Console 등록하기
date: 2020-10-06 22:04:00 +0900
categories: [Programming, Github]
tags: [github-pages]     # TAG names should always be lowercase
---
Github Page를 만들었다고 구글에 검색이 되는 것은 아니다.

Google Search Console이라는 것을 사용하여 구글 검색엔진이 우리 사이트를 크롤링할 수 있도록 등록 해야한다.

# robots.txt 수정

```
User-agent: *

Allow:/ 

Sitemap: https://USERNAME.github.io/sitemap.xml
```

내용을 위와 같이 수정해준다.

`Allow: /` 는 크롤러에게 사이트의 모든 범위를 크롤링할 수 있게 허용하는 것이다.

# Search Console에 사이트 연결하기

구글에 search console을 검색하고 들어가자.

들어가서 `속성추가` 를 누르고 자신의 사이트를 등록하자.

그러면 소유권 인증을 해야하는데, html파일을 다운받고 자신의 root페이지(레포지토리 최상단)에 넣어주고 push해준다.

그리고 github action이 완료되면 '[USERNAME].github.io/google~~~.html'에 접속하여 제대로 업로드 되었는지 확인하고 확인을 누르면 소유권 확인이 된다.

# sitemap.xml 추가

![1.jpg](/assets/img/post/3/1.jpg)

위와 같이 `sitemap.xml`을 추가 한다.

사이트 노출까지는 시간이 1-2일 정도 걸린다. 

# 네이버 검색 노출

네이버에도 블로그를 노출 시킬 수 있다.

[네이버 서치어드바이저](https://searchadvisor.naver.com/) 여기로 가면 위에서와 같이 `naver~~~.html`로 사이트 인증을 해주고, `sitemap.xml`을 등록해주면 네이버 검색엔진에도 노출이 된다.

이 또한 즉시 반영되지는 않고 시간이 조금 걸린다.