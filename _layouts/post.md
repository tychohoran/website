<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>{{site.title}} | {{page.title}}</title>
	<link rel="stylesheet" type="text/css" href="/styles.css">
</head>
<body>

	{% if page.accent_image %}
		{% assign classHead = "normal" %}
	{% else%}
		{% assign classHead = "center" %}
	{% endif %}

	<div id="post_wrapper" class="{{classHead}}">
		<nav id="post_nav">
			<a href="/" alt="">&#8617;<span>&#8201;</span>Home</a>
		</nav>
		{% if page.accent_image %}
			<img class="accent_image" alt="{{page.title}}" src="{{page.accent_image}}">
		{% endif %}
		<!-- <div id="post_top"> -->

			<header id="post_header" class="{{classHead}}">
					{{page.title}}
			</header>
			{% if page.description %}
			<div class="info_block {{classHead}}">
				{{- page.description | markdownify -}}
			</div>
			{% endif %}
			<div class="post_info {{classHead}}">
			{% if page.year %}
				<p class="post_year">{{page.year}}</p>
			{% endif %}
			{% if page.dimensions_x %}
				<p class="post_dimensions">{{page.dimensions_x}}" x {{page.dimensions_y}}"</p>
			{% endif %}
			{% if page.type %}
				<p class="post_type">{{page.type}}</p>
			{% endif %}
			{% if page.media %}
				<p class="post_type">{{page.media}}</p>
			{% endif %}
			{% if page.collaborators %}
				{{ page.collaborators | markdownify | rstrip | lstrip }}
			{% endif %}
			</div>
			{% if page.content %}
			<div class="post_content">
				{{ page.content | markdownify | rstrip | lstrip }}
			</div>
			{% endif %}
		<!-- </div> -->
		{% if page.detail_images %}
			<div id="carousel_wrapper">
			<a id="back_arrow" onClick="scrollBack()" href="#carousel_wrapper" style="display:none;">&#8592;</a>
			<a id="forward_arrow" onClick="scrollForward()" href="#carousel_wrapper">&#8594;</a>
			<div id="image_carousel" onscroll="scrollEval()">
			{% for detail_image in page.detail_images %}
				<img class="post_detail" alt="" src="{{detail_image}}">
			{% endfor %}
			</div>
			</div>
		{% endif %}
	</div>

	<script>
		function scrollForward() {
			const carousel = document.getElementById("image_carousel");
			carousel.scrollBy(carousel.offsetWidth, 0);
		}
		function scrollBack() {
			const carousel = document.getElementById("image_carousel");
			carousel.scrollBy(-carousel.offsetWidth, 0);
		}
		function scrollEval() {
			const carousel = document.getElementById("image_carousel");
			const forward = document.getElementById("forward_arrow");
			const back = document.getElementById("back_arrow");
			var end = carousel.scrollWidth - carousel.offsetWidth;
			if(carousel.scrollLeft > 0){
				back.style.display = "flex";
			} else {
				back.style.display = "none";
			}
			if(carousel.scrollLeft < end){
				forward.style.display = "flex";
			} else {
				forward.style.display = "none";
			}
		}
	</script>
</body>