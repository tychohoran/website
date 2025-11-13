---
---

<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>{{site.title}}</title>
	<link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body onscroll="calcScroll()">
	<div id="wrapper">
		<div id="bio">
			<div id="bio_text">
				<nav id="site_nav">
					<a href="#work" alt="" onclick="removeClick()">Work</a>
					<a href="" alt="">Writing</a>
					<a href="#Bio" alt="" onclick="darkenBioText()">Bio</a>
					<a href="" alt="">Contact</a>
				</nav>
				{{site.bio_text | markdownify}}
			</div>
		</div>
		<posts id="posts">
			<div class="top_spacer"></div>
			<div id="work">
  			{% for post in site.posts %}
		  		<div class="image_container">
		  			<a href="{{post.url}}" class="image_link">
		  				<img src="{{post.image}}" alt="" class="post_image">
		  			</a>
		  		</div>
  			{% endfor %}
  			</div>
		</posts>
	</div>
	<script>

		// Randomly Place the Images

		const images = document.getElementsByClassName("post_image");
		for (let i = 0; i < images.length; i++) {
			var random = Math.round(Math.random() * 89) - 44;
			images.item(i).style.left = random + "%";
		}

		// Paralax Effect
		function calcScroll() {
			const window_height = window.innerHeight;
			const bio_text = document.getElementById("bio_text");
			const bio_height = bio_text.offsetHeight;
			const max_scroll = document.body.scrollHeight;
			const scroll_position = document.body.scrollTop;
			const scroll_progress = scroll_position/(max_scroll - window_height);
			const bio_scroll = Math.round(scroll_progress * (bio_height - window_height));
			bio_text.style.transform = "translateY(-"+ bio_scroll +"px)";
			console.log(bio_scroll);
		}

		// Work Button

		function removeClick() {
			const bio = document.getElementById("bio_text");
			bio.classList.remove("clicked");
			const work = document.getElementById("work");
			work.classList.remove("clicked");
		}

		// Darken Bio Text
		function darkenBioText() {
			const bio = document.getElementById("bio_text");
			bio.classList.add("clicked");
			const work = document.getElementById("work");
			work.classList.add("clicked");
		}
	</script>
</body>