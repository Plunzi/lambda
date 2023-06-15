<script>
	import PocketBase from 'pocketbase';
	import { onMount } from 'svelte';

	const pb = new PocketBase('https://blog.plunzi.sh/');
	const url = 'https://blog.plunzi.sh/';

	async function changeNavigationHighlight() {
		const links = document.querySelectorAll('.navigation-link');
		const activeLink = document.querySelector('.navigation-link.posts');

		links.forEach(async (link) => {
			link.classList.remove('active');
		});

		// @ts-ignore
		activeLink.classList.add('active');
	}

	onMount(async () => {
		const loadingTitle = document.querySelectorAll('.loading-title');
		const loadingContent = document.querySelectorAll('.loading-content');
		const loadingImages = document.querySelectorAll('.postCardImageContainer');
		const postLinks = document.querySelectorAll('.postLink');

		async function fetchPosts() {
			const records = await pb.collection('plunzish_news').getFullList({
				sort: '-created'
			});

			for (let i = 0; i < loadingTitle.length; i++) {
				if (records[i] == undefined) {
					break;
				} else {
					loadingTitle[i].innerHTML = records[i].title;
					loadingContent[i].innerHTML = records[i].content;
					loadingImages[
						i // @ts-ignore
					].style.backgroundImage = `url(${url}api/files/plunzish_news/${records[i].id}/${records[i].thumbnail}`;

					loadingTitle[i].classList.add('loading-finished');
					loadingContent[i].classList.add('loading-finished');

					postLinks[i].setAttribute('href', '/post/' + records[i].postIdentifier + '?updates');
				}
			}
		}

		fetchPosts();
		changeNavigationHighlight();
	});
</script>

<svelte:head>
	<link rel="stylesheet" href="/format.css" />
</svelte:head>

<main>
	<div class="description">
		<h1>Welcome to our announcements section!</h1>
		<p>
			Your go-to source for all things related to „Plunzish“! Get the latest scoop on our upcoming
			games, behind-the-scenes, sneak peeks, and exciting events. No registration required! Stay
			tuned for the latest „Plunzish“ news.
		</p>
		<br />
	</div>

	<div class="container">
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
		<a href="#loading" class="postLink">
			<div class="postCard circle-size" data-size="medium">
				<div class="postCardImageContainer" />
				<div class="postCardContent">
					<h1 class="loading-title">My Post Title</h1>
					<p class="loading-content">Hello World</p>
				</div>
			</div>
		</a>
	</div>
</main>

<style lang="scss">
	@import '../../lib/variables.scss';
	$white: rgb(255, 255, 255);

	$base-color: #1d1d1d;
	$shine-color: #303030;
	$animation-duration: 2s;
	$avatar-offset: 52 + 16;

	@mixin background-gradient {
		background-image: linear-gradient(90deg, $base-color 0px, $shine-color 60px, $base-color 120px);
		background-size: 600px;
	}

	.loading-title,
	.loading-content {
		@include background-gradient;
		animation: shine-lines $animation-duration infinite linear;
		border-radius: 0.5rem;
		width: 75%;
		padding: 0 0.5rem;
		color: transparent;
		transition: all 1s;
		line-height: 1.2em;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 3;
	}

	.postLink {
		display: inherit;
		text-decoration: none;
		border-radius: 1rem;
	}

	.loading-content {
		width: 50%;
		padding: 0 0.5rem;
		color: transparent;
	}

	:is(.loading-finished, p.loading-finished) {
		background: none;
		color: #fff;
		width: auto;
	}

	main {
		color: white;
		background: #000;
	}

	.description {
		width: 50%;
		margin-top: 4rem;
		padding: 3rem 10rem;
		background: #000;
		border-top: solid #383838 1px;
		border-bottom: solid #383838 1px;
	}

	.container {
		// background: rgba(0, 255, 255, 0.5);
		display: grid;
		gap: 3rem;
		grid-template-columns: repeat(auto-fit, minmax(22rem, 1fr));
		padding: 3rem 10rem;
		background: #1d1d1d;
		border-top: solid #383838 1px;
		border-bottom: solid #383838 1px;
	}

	.postCard {
		position: relative;
		background-color: $black-secondary;
		border: solid #383838 1px;
		border-radius: 1rem;
		display: flex;
		flex-direction: column;
		transition: ease 0.5s;
		transition-timing-function: cubic-bezier(0.5, 0, 0, 1);
		cursor: pointer;
		&:hover {
			border: solid rgb(255, 190, 51) 1px;
			box-shadow: rgb(255, 190, 51) 0px 1px 4px, rgb(255, 190, 51) 0px 0px 0px 3px;
			transform: scale(0.95);
		}
	}

	.postCardImageContainer {
		width: 100%;
		aspect-ratio: 16/7;
		border-radius: 1rem 1rem 0 0;
		background-image: linear-gradient(45deg, #1f1f1f 0%, #000000 100%);
		background-position: center;
		background-position: center;
		background-size: cover;
		border-bottom: solid #383838 1px;
	}

	.postCardContent {
		padding: 1rem;
	}

	@media only screen and (max-width: 850px) {
		main {
			.description {
				width: auto;
				& h1 {
					overflow-wrap: break-word;
					word-wrap: break-word;
					-ms-word-break: break-all;
					word-break: break-word;
					-ms-hyphens: auto;
					-moz-hyphens: auto;
					-webkit-hyphens: auto;
					hyphens: auto;
				}
			}
			& h1 {
				margin-block-start: 0;
			}
		}

		.description,
		.container {
			padding: 3rem 1rem;
		}
	}

  @media only screen and (min-width: 2000px) {
    .container {
      padding: 3rem 20rem;
    }

    .description {
      padding: 3rem 20rem;
    }
  }

	@media only screen and (max-width: 400px) {
		.container {
			grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
			& h1 {
				font-size: 2.25rem;
			}
		}
	}

	@keyframes shine-lines {
		0% {
			background-position: -10rem;
		}

		80%,
		100% {
			background-position: 30rem;
		}
	}

	@keyframes shine-avatar {
		0% {
			background-position: -100% + $avatar-offset;
		}

		40%,
		100% {
			background-position: 100% + $avatar-offset;
		}
	}
</style>
