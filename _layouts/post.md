<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>{{site.title}} | {{page.title}}</title>
	<link rel="stylesheet" type="text/css" href="/styles.css">
</head>
<body>
	<div id="post_wrapper">
		<nav id="post_nav">
			<a href="/" alt="">&#8617;<span>&#8201;</span>Home</a>
		</nav>
		<header id="post_header">
				{{page.title}}
		</header>
		<div class="post_info">
			<p class="post_year">{{page.year}}</p>
			<p class="post_dimensions">{{page.dimensions_x}}" x {{page.dimensions_y}}"</p>
			<p class="post_type">{{page.type}}</p>
			<p class="post_collaborators">{{page.collaborators | markdownify}}</p>
		</div>
		<br>
		<div class="info_block">
			{{page.content | markdownify}}
		</div>
		<div class="image_carousel">
			<img class="post_image" alt="{{page.title}}" src="{{page.image}}">
		</div>
	</div>
</body>