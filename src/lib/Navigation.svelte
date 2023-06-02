<nav id="primary-navigation">
  <div class="nav-header">
    <div class="logo-header">
      <div class="logo" />
      <p>Lambda</p>
    </div>
    <ul>
      <li>
        <p><a href="/" class="active">Home</a></p>
      </li>
      <li>
        <p><a href="test">News</a></p>
      </li>
      <li>
        <p><a href="test">Presentation</a></p>
      </li>
      <li>
        <p><a href="test">test</a></p>
      </li>
      <li>
        <p><a href="test">test</a></p>
      </li>
    </ul>
    <button>Purchase now!</button>
  </div>
</nav>

<style lang="less">
  .nav-header {
    padding: 0 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  :global(nav#primary-navigation.hide) {
    transform: translateY(-100%);
    transition: ease-in-out 1s;
  }

  .logo-header {
    display: flex;
  }

  :global(a.active) {
    background: #1a1a1a;
    border-radius: 8px;
    padding: 0.5rem 1rem;
  }

  .logo {
    margin-top: auto;
    margin-bottom: auto;
    width: 2rem;
    height: 2rem;
    border-radius: 8px;
    margin-right: 0.5rem;
    background-image: url("/primary.svg");
  }

  ul {
    display: flex;
    gap: 1rem;
    width: fit-content;
    padding-inline-start: 0;
  }

  li {
    list-style: none;
    & a {
      color: #737373;
    } & :hover {
      color: #fff;
    }
  }

  nav {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: black;
  }
</style>
