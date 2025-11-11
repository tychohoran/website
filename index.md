---
---

<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>{{site.title}}</title>
	<link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
	<div id="wrapper">
		<div id="bio">
			{{site.bio_text | markdownify}}
		</div>
		<posts>
  {% for post in site.posts %}
  		<img src="{{post.image}}" alt="" class="post_image">
  {% endfor %}
	</posts>
	</div>
</body>