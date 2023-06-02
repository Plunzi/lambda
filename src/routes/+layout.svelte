<script>
  import Navigation from "../lib/Navigation.svelte";
  import Footer from "../lib/Footer.svelte";
</script>

<Navigation />
<div id="page">
  <slot />
</div>
<Footer />

<style>
  :root {
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
    line-height: 1.5;
    font-weight: 400;

    color-scheme: light dark;
    color: rgba(255, 255, 255, 0.87);
    background-color: #242424;

    font-synthesis: none;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    -webkit-text-size-adjust: 100%;
  }

  :global(a) {
    font-weight: 500;
    color: #646cff;
    text-decoration: inherit;
  }
  :global(a):hover {
    color: #535bf2;
  }

  :global(body) {
    overflow: auto;
  }

  #page {
    width: 100%;
    padding-top: 5.5rem;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    transition: ease-in-out 1s;
  }

  :global(#page.focus) {
    padding: 0;
    height: calc(100vh - 2rem);
  }

  :global(body) {
    margin: 0;
    display: flex;
    flex-direction: column;
    height: 100vh;
    height: 100svh;
  }

  :global(h1) {
    font-size: 3.2em;
    line-height: 1.1;
  }

  :global(button) {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    font-family: inherit;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
  }
  :global(button):hover {
    border-color: #646cff;
  }
  :global(button):focus,
  :global(button):focus-visible {
    outline: 4px auto -webkit-focus-ring-color;
  }
</style>
