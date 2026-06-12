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
					<a href="#work" alt="" onclick="removeClick()">&#128444;<span>&#8201;</span>Work</a>
					<!-- <a href="" alt="">Writing</a> -->
					<a href="#bio" alt="" onclick="darkenBioText()">&#128105;&#127996;<span>&#8201;</span>Bio</a>
					<a href="#contact" alt="">&#128236;<span>&#8201;</span>Contact</a>
				</nav>
				{{site.bio_text | markdownify}}
				<div id="credits">{{site.credits_text | markdownify}}</div>
			</div>
		</div>
		<posts id="posts">
			<div class="top_spacer"></div>
			<div id="work">
  			{% for post in site.posts %}
		  		<div class="image_container">
		  			<a href="{% if post.visible_page %}{{post.url}}{% endif %}" class="image_link" style="width:calc({{post.dimensions_x}} * 35px);">
		  				<p class="image_caption">
		  					{{ post.title }}, {{ post.year }}
		  				</p>
		  				<img src="{{post.image}}" alt="" class="post_image">
		  				<p class="image_caption">
		  					{% if post.collaborators %}{{ post.collaborators | markdownify | strip_html}}{% endif %}
		  				</p>
		  			</a>
		  		</div>
  			{% endfor %}
  			<div id="contact">
  				<a href="mailto:tychohoran1@gmail.com" alt="Email Address" target="_blank">&#128140;<span>&#8201;</span>Email</a>
  				<a href="" alt="Teaching Portfolio2">&#127822;<span>&#8201;</span>Teaching</a>
  				<a href="https://docs.google.com/document/d/1zLW_gKqRLKTr6Tga7DSeWjlrjKWuRKOz2Zq5WzLAm-k/edit?usp=sharing" alt="Tycho Horan CV" target="_blank">&#128196;<span>&#8201;</span>CV</a>
  			</div>
  			</div>
		</posts>
	</div>
	<script>

		// Randomly Place the Images

		const images = document.getElementsByClassName("image_link");
		var last_place = 0;
		var last_width, ratio;
		for (let i = 0; i < images.length; i++) {
			var random = Math.random() * 100 - 50;
			var dif = Math.abs(last_place - random);
			var width = images[i].offsetWidth;
			if(!last_width){
				ratio = 0;
			} else {
				ratio = Math.min(Math.max(width,last_width)/11,50);
			}
			console.log(ratio);
			while(dif < ratio) {
				random = Math.random() * 100 - 49;
				dif = Math.abs(last_place - random);
			}
			images.item(i).style.left = Math.round(random * (150/width)) + "%";
			last_place = random;
			last_width = width;
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