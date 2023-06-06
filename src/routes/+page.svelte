<script>
  import { onMount } from "svelte";

  let slideOptions = {
    minSlides: "1",
    maxSlides: "",
  };

  let slide = 1;
  let curMinSlide;

  function toggleNav() {
    const primaryNav = document.getElementById("primary-navigation");
    const primaryFoo = document.getElementById("primary-footer");
    const page = document.getElementById("page");
    if (primaryNav?.classList.contains("hide")) {
      // @ts-ignore
      primaryFoo.style.display = "block";
      setTimeout(() => {
        primaryNav?.classList.remove("hide");
        primaryFoo?.classList.remove("hide");
        page?.classList.remove("focus");
      }, 5);
    } else {
      primaryNav?.classList.add("hide");
      primaryFoo?.classList.add("hide");
      page?.classList.add("focus");
      setTimeout(() => {
        // @ts-ignore
        primaryFoo.style.display = "none";
      }, 500);
    }
  }

  function escapeSlide() {
    const primaryNav = document.getElementById("primary-navigation");
    const primaryFoo = document.getElementById("primary-footer");
    const page = document.getElementById("page");
    // @ts-ignore
    primaryFoo.style.display = "block";
    setTimeout(() => {
      primaryNav?.classList.remove("hide");
      primaryFoo?.classList.remove("hide");
      page?.classList.remove("focus");
    }, 5);

    const curSlide = "slide-" + slide;
    // @ts-ignore
    document.getElementById(curSlide).style.height = "calc(100vh - 12rem)";
    curMinSlide = slide;
  }

  function nextSlide() {
    const primaryNav = document.getElementById("primary-navigation");
    // @ts-ignore
    if (curMinSlide != undefined) {
    }

    if (Number(slideOptions.maxSlides) > slide) {
      if (!primaryNav?.classList.contains("hide")) {
        toggleNav();
        setTimeout(() => {
          const curSlide = "slide-" + slide;
          // @ts-ignore
          document.getElementById(curSlide).style.transform =
            "translateX(-100%)";
          slide = slide + 1;
          const newSlide = "slide-" + slide;
          // @ts-ignore
          document.getElementById(newSlide).style.transform = "translateX(0%)";
        }, 1000);
      } else {
        const curSlide = "slide-" + slide;
        // @ts-ignore
        document.getElementById(curSlide).style.transform = "translateX(-100%)";
        slide = slide + 1;
        const newSlide = "slide-" + slide;
        // @ts-ignore
        document.getElementById(newSlide).style.transform = "translateX(0%)";
      }
    }
  }

  // @ts-ignore
  function prevSlide() {
    if (Number(slideOptions.minSlides) < slide) {
      const curSlide = "slide-" + slide;
      // @ts-ignore
      document.getElementById(curSlide).style.transform = "translateX(100%)";
      slide = slide - 1;

      const prevSlide = "slide-" + slide;
      // @ts-ignore
      document.getElementById(prevSlide).style.transform = "translateX(0%)";
    }
  }

  // @ts-ignore
  function onKeyDown(e) {
    console.log(e.key);
    switch (e.key) {
      case "ArrowRight":
        nextSlide();
        break;
      case "ArrowLeft":
        prevSlide();
        break;
      case " ":
        nextSlide();
        break;
      case "Escape":
        escapeSlide();
        break;
      default:
        break;
    }
  }

  onMount(async () => {
    slideOptions = {
      minSlides: "1",
      maxSlides: String(document.getElementsByClassName("wrapper").length),
    };
    console.log(slideOptions.maxSlides);
  });
</script>

<div class="container wrapper" id="slide-1">
  <div class="left-content">
    <div class="center-piece">
      <h1>Lambda Watches</h1>
      <h2>The creators of your future watch!</h2>
      <p>
        Check out our latest product <a href="https://link.dev">link</a> to read
        the documentation
      </p>
    </div>
  </div>
  <div class="right-content">
    <img
      on:click={toggleNav}
      class="header-img"
      src="front.png"
      alt="watches front side"
    />
  </div>
  <div class="slideNumber">
    <span>1</span>
  </div>
</div>

<svelte:window on:keydown={onKeyDown} />

<div class="container wrapper" id="slide-2">
  <div class="left-content">
    <div class="center-piece">
      <h1>Play Snake</h1>
      <h2>Yep this presentation software breaks the limits of powerpoint.</h2>
      <p style="width: 75%;">
        You can literally display any feature 🏗️html / 🎨css / ⚙️js can display.
        Does not matter if you wanna play a 🐍game, display a 🎬video, load an
        🖼️image or break the whole page🗑️. You can do anything. 🧊
      </p>
    </div>
  </div>
  <div class="right-content">
    <iframe
      class="header-img"
      title="snake"
      src="https://snake.googlemaps.com/"
      height="75%"
      style="aspect-ratio: 1/1;"
      frameborder="0"
    />
  </div>
  <div class="slideNumber">
    <span>2</span>
  </div>
</div>

<style lang="less">
  #slide-1 .left-content .center-piece, #slide-2 .left-content .center-piece {
    padding-left: 4rem;
  }


  .container {
    position: relative;
    padding: 1rem;
    display: flex;
    gap: 1rem;
    flex-grow: 1;
    transition: ease 2s;
  }

  .slideNumber {
    color: black;
    position: absolute;
    right: 1.5rem;
    bottom: 1.5rem;
    background: #00000020;
    width: 4rem;
    height: 4rem;
    border-radius: 1rem;
    display: grid;
    justify-content: center;
    align-items: center;
    font-size: 1.5rem;
    & span {
      transform: translateY(0.1rem);
    }
  }

  #slide-2 {
    position: fixed;
    width: calc(100vw - 2rem);
    height: calc(100vh - 2rem);
    height: calc(100svh - 2rem);
    transform: translateX(100%);
  }

  .wrapper {
    background: linear-gradient(
      45deg,
      #ffffff,
      #ffffff
    );
    background-size: 600% 100%;
    animation: gradient 16s linear infinite;
    animation-direction: alternate;
  }
  @keyframes gradient {
    0% {
      background-position: 0%;
    }
    100% {
      background-position: 100%;
    }
  }

  .wrapper h1 {
    padding: 0;
    margin: 0;
    background: #f2994a; /* fallback for old browsers */
    background: -webkit-linear-gradient(
      to right,
      #000000,
      #333333
    ); /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(
      to right,
      #000000,
      #333333
    ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .wrapper h2 {
    color: #212121;
  }

  .wrapper p {
    color: #212121;
  }

  .left-content {
    background: #1a1a1a23;
    width: 100%;
    padding: 1rem;
    border-radius: 8px;
    display: flex;
    align-items: center;
  }

  .right-content {
    background: #1a1a1a23;
    width: 100%;
    padding: 1rem;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .header-img {
    width: 75%;
    background: #000;
    border-radius: 1rem;
    transition: ease-in-out 0.5s;
    border: #212121 5px solid;
    &:hover {
      transform: scale(1.05);
      border: #4c4c4c 5px solid;
      cursor: pointer;
    }
  }
</style>
