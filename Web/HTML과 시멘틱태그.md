## HTML이란?

HTML은 약어로 (Hyper Text Markup Language) HyperText 기능을 가진 문서를 만드는 언어이다.

HyperText 란 웹페이지에서 다른페이지로 이동할 수 있도록 하는 기능을 말하며

Markup Language는 웹 브라우저에서 내 콘텐츠를 어떻게 표현해야 하는지 명령하는 언어 이다.

## 태그의 형식

<a href=”http://www.naver.com”>네이버로 이동</input>

<></> 로 감싸서 표현하며 <>를 태그(tag) 라고 부른며

태그 사이에 정의된 내용은 콘텐츠(content) 라고 부른다.

태그 안에 href 같은 것은 속성 (Attribute) 라고 불리며 태그내에서 속성을 지정해 줄 수 있다.

항상 열려있는 태그가 있으면 </> 로 닫는 태그가 존재해야 하며

<br/> <input/> 은 닫는태그를 여는태그와 함께 붙혀줘도 된다.

## block & inline

HTML Element 는 두가지로 나뉜다.

block & inline 이다.

웹 페이지 구조를 설계하는데 있어서 아주 중요한 개념이고 CSS에서도 등장하는 필수적으로 이해하고 있어야 하는 개념이다.

### block

- 한줄에 나열되고 그 한줄 전체를 차지한다.
    - block 태그로 작성 된 content가 두개 있으면 세로로 나열되서 나온다 (줄바꿈)
    - 기본적으로 넓이가 100% 에 맞춰져 있다. (스타일링 가능)
    - margin, width, height 등 크기를 가질 수 있다.
    - 특정 요소가 block인지 아닌지 확인할 때는 배경색을 입혀보면 된다.

> 주요 block 태그
> 

[<address>](https://www.w3schools.com/tags/tag_address.asp)[<article>](https://www.w3schools.com/tags/tag_article.asp)[<aside>](https://www.w3schools.com/tags/tag_aside.asp)[<blockquote>](https://www.w3schools.com/tags/tag_blockquote.asp)[<canvas>](https://www.w3schools.com/tags/tag_canvas.asp)[<dd>](https://www.w3schools.com/tags/tag_dd.asp)[<div>](https://www.w3schools.com/tags/tag_div.asp)[<dl>](https://www.w3schools.com/tags/tag_dl.asp)[<dt>](https://www.w3schools.com/tags/tag_dt.asp)[<fieldset>](https://www.w3schools.com/tags/tag_fieldset.asp)[<figcaption>](https://www.w3schools.com/tags/tag_figcaption.asp)[<figure>](https://www.w3schools.com/tags/tag_figure.asp)[<footer>](https://www.w3schools.com/tags/tag_footer.asp)[<form>](https://www.w3schools.com/tags/tag_form.asp)[<h1>-<h6>](https://www.w3schools.com/tags/tag_hn.asp)[<header>](https://www.w3schools.com/tags/tag_header.asp)[<hr>](https://www.w3schools.com/tags/tag_hr.asp)[<li>](https://www.w3schools.com/tags/tag_li.asp)[<main>](https://www.w3schools.com/tags/tag_main.asp)[<nav>](https://www.w3schools.com/tags/tag_nav.asp)[<noscript>](https://www.w3schools.com/tags/tag_noscript.asp)[<ol>](https://www.w3schools.com/tags/tag_ol.asp)[<p>](https://www.w3schools.com/tags/tag_p.asp)[<pre>](https://www.w3schools.com/tags/tag_pre.asp)[<section>](https://www.w3schools.com/tags/tag_section.asp)[<table>](https://www.w3schools.com/tags/tag_table.asp)[<tfoot>](https://www.w3schools.com/tags/tag_tfoot.asp)[<ul>](https://www.w3schools.com/tags/tag_ul.asp)[<video>](https://www.w3schools.com/tags/tag_video.asp)

### inline

- block 과 달리 줄을 바꾸지 않고 그대로 나열한다.
- margin-top, margin-bottom 속성을 적용해도 적용되지 않는다.
    - 인라인요소의 상 하는 margin이 아닌 line-height 로 적용된다.
- width, height 도 적용되지 않는다 내부 content의 부피에 자동으로 맞춰진다
- 인라인 속성을 가진 태그끼리 연속으로 사용되는 경우에는 최소한의 간격을 유지하기 위해서 좌, 우에 약 5px 가량의 외부 여백(margin)이 자동으로 발생한다.

## 시멘틱 태그

### 시멘틱태그 란?

시멘틱태그가 등장하기 전에는 div 로 묶어서 id 와 class로 구분하며 스타일링을 하였다.

그러다 보니 코드가 길어지면 원하는 정보를 찾기가 점점 힘들어졌다.

시멘틱태그는 웹의 구조를 나타내는 나타내는 태그이다 즉 레이아웃을 설계하기 위한 태그라고 보면 될거같다. 시멘틱태그는 전부 Block Element이다.

### 시멘틱태그를 왜 사용 할 까?

1. SEO (검색엔진) 최적화에 유리하다.
    - 검색엔진이 태그의 목적에 부합하게 설계되어 있으므로 더욱 빨리 효율적으로 정보를 파악할 수 있다.
2. 웹 접근성에 효율적이다.
- 일반적인 브라우저에서는 큰 차이가 없다. 하지만 스크린리더(시각장애인을 위한 웹 서핑 프로그램) 같은 환경에서는 웹 접근성과 사용성을 향상 시켜준다.

또한 유지보수가 편하다는 평가를 받고있다. (태그의 이름만 보고 파악)

### 시멘틱 태그의 종류

<header> : 머리글 , 제목 , 헤더

<nav> : 네비게이션 목차, 리스트 등 다른 페이지로 이동을 위한 링크 공간

<aside> : 좌측과 우측의 사이드공간 (본문 외에 부수적인 내용을 주로 표현)

<section> : 주제 , 카테고리별로 섹션을 구분하는 용도로 주로 사용 ( 예를 들어 Card)

<article> : 기사, 블로그 등 텍스트 위주의 페이지를 구성할 때 사용

<footer> : 문서 하단에 들어가는 정보를 담는 공간을 구분하는 태그 (기업소개 등)

<address> : content 작성자나 사이트의 소유자를 적는 태그

<hgroup> : 제목과 관련 된 부제목을 묶는 태그 

<main> : 중심주제 가장 중요한 내용을 작성하는 공간이다.

<details> : 주변 문맥에서 표시된 구절의 관련성 또는 중요성으로 인해 참조 또는 표기 목적으로 표시되거나 강조된 텍스트

<figure> : 이미지, 다이어그램 등 독립적인 content 정의 시 사용

<figcaption> : <figure> 요소의 설명 

<mark> : 현재 맥락의 관련이 깊거나 중요한 부분 강조

<time> : 시간의 특정지점 또는 구간

<summary> : details 요소에 대한 요약, 캡션 또는 범례를 지정. summary 요소를 클릭하면 상위 details 요소의 상태가 열리고 닫힘.

### 시멘틱 태그 활용 코드

```html
<!DOCTYPE html>
<!-- DOCTYPE : 문서의 형식을 선언 -->
<html lang="ko">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>시멘틱태그의 활용</title>
	</head>
	<body>
		<header>
			<h1>삼성</h1>
		</header>
		<nav>
			<ul>
				<li><a href="#">네이버로 이동</a></li>
				<li><a href="#">다음으로 이동</a></li>
				<li><a href="#">구글로 이동</a></li>
			</ul>
		</nav>
		<section>
			<main>
				<h1>고객의 상품 평!</h1>
				<article>
					<p>김지후 고객님</p>
					<span>정말 좋았어요!</span>
				</article>
			</main>
		</section>
		<aside>
			<h1>오늘의 광고!</h1>
			<p>맛있는 피자!</p>
			<p>위대한 피자!</p>
			<p>한민관도 5마리 먹는 치킨!</p>
		</aside>
		<footer>
			<h1>삼성</h1>
			<p>경기도 안양시 만안구 석수동 123-456</p>
			<p>010-5217-6194</p>
		</footer>
	</body>
</html>
```

# 참고한 자료

---

[](https://webclub.tistory.com/608)

[html 이란? 속 시원한 HTML 뜻 풀이](https://brunch.co.kr/@coveryou/14)

[HTML은 프로그래밍 언어인가? 라는 논쟁보다 중요한 것](https://yceffort.kr/2021/10/is-html-programming-language)