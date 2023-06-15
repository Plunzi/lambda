<!-- <script>
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
</script> -->

<svelte:head>
  <link rel="stylesheet" href="/format.css" />
</svelte:head>

<main>
  <div class="description">
    <h1>Welcome to our news section!</h1>
    <p>
      Your go-to source for all things related to Lambda Watches! Get the latest
      scoop on our upcoming releases,<br /> behind-the-scenes, sneak peeks, and exciting
      events. No registration required! Stay tuned for the latest „Lambda“ news.
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

<style>
  .loading-title,
  .loading-content {
    background-image: linear-gradient(
      90deg,
      #e1e1e1 0px,
      #ebebeb 60px,
      #e1e1e1 120px
    );
    background-size: 600px;
    animation: shine-lines 2s infinite linear;
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
    padding: 3rem 10rem;
    background: #ffffff;
    color: #000;
    border-top: solid #383838 1px;
  }

  .container {
    display: grid;
    gap: 3rem;
    grid-template-columns: repeat(auto-fit, minmax(22rem, 1fr));
    padding: 3rem 10rem;
    background: #e0e0e0;
    border-top: solid #e0e0e0 1px;
    border-bottom: solid #e0e0e0 1px;
  }

  .postCard {
    position: relative;
    background-color: #d0d0d0;
    border: solid #adadad 1px;
    border-radius: 1rem;
    display: flex;
    flex-direction: column;
    transition: ease 0.5s;
    transition-timing-function: cubic-bezier(0.5, 0, 0, 1);
    cursor: pointer;
  }

  .postCard:hover {
    border: solid #d0d0d0 1px;
    box-shadow: #adadad 0px 1px 4px, #adadad 0px 0px 0px 3px;
    transform: scale(0.95);
  }

  .postCardImageContainer {
    width: 100%;
    aspect-ratio: 16/7;
    border-radius: 1rem 1rem 0 0;
    background-image: linear-gradient(45deg, #ffffff 0%, #d0d0d0 100%);
    background-position: center;
    background-position: center;
    background-size: cover;
    border-bottom: solid #d0d0d0 1px;
  }

  .postCardContent {
    padding: 1rem;
  }

  @media only screen and (max-width: 850px) {
    main .description {
      width: auto;
    }

    main h1 {
      margin-block-start: 0;
    }

    main .description h1 {
      overflow-wrap: break-word;
      word-wrap: break-word;
      -ms-word-break: break-all;
      word-break: break-word;
      -ms-hyphens: auto;
      -moz-hyphens: auto;
      -webkit-hyphens: auto;
      hyphens: auto;
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
    }

    .container h1 {
      font-size: 2.25rem;
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
      background-position: -100% + 52 + 16;
    }

    40%,
    100% {
      background-position: 100% + 52 + 16;
    }
  }
</style>
