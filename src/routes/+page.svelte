<script>
  function toggleNav() {
    const primaryNav = document.getElementById("primary-navigation");
    const primaryFoo = document.getElementById("primary-footer");
    const page = document.getElementById("page");
    if (primaryNav?.classList.contains("hide")) {
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
</script>

<div class="container wrapper">
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
</div>

<style lang="less">
  .container {
    padding: 1rem;
    display: flex;
    gap: 1rem;
    flex-grow: 1;
  }

  .wrapper {
    background: linear-gradient(
      45deg,
      #f17c58,
      #e94584,
      #24aadb,
      #27dbb1,
      #ffdc18,
      #ff3706
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

  h1 {
    padding: 0;
    margin: 0;
    background: #f2994a; /* fallback for old browsers */
    background: -webkit-linear-gradient(
      to right,
      #f2c94c,
      #f2994a
    ); /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(
      to right,
      #f2c94c,
      #f2994a
    ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
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
