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
        We create high quality watches with focus on climate neutrality and
        pixel perfect <br /> design for all our products.
        <a href="https://link.dev">Check out or products</a> and details.
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

<!-- slide 2 -->

<div class="container wrapper" id="slide-2">
  <div class="left-content">
    <div class="center-piece">
      <h1>Projektziel</h1>
      <h2>Was wurde umgesetzt?</h2>
      <ul>
        <li>Website</li>
        <li>Styleguide</li>
        <li>3d Render der Uhr</li>
        <li>Visitenkarten</li>
        <li>Plakate</li>
      </ul>
    </div>
  </div>
  <div class="right-content">
    <div>
      <h2>Was wurde nicht umgesetzt?</h2>
      <ul>
        <li>Social Media (Optional)</li>
      </ul>
    </div>
  </div>
  <div class="slideNumber">
    <span>2</span>
  </div>
</div>

<!-- slide 3 -->

<div class="container wrapper" id="slide-3">
  <div class="left-content">
    <div class="center-piece">
      <h1 class="hours-absoulte">Arbeitsstunden</h1>
      <h2>Fynn <span class="hours-spent"> - 36 Stunden</span></h2>
      <div class="overlow-table">
        <table style="width:100%">
          <tr>
            <th>Datum</th>
            <th>Arbeit</th>
            <th>Stunden</th>
          </tr>
          <tr>
            <td>23.Feb</td>
            <td>Start, erste Übrlegungen</td>
            <td>1</td>
          </tr>
          <tr>
            <td>27. Feb</td>
            <td>Logo Design</td>
            <td>5</td>
          </tr>
          <tr>
            <td>1. März</td>
            <td>Logo Design, Plakat Sketch</td>
            <td>5</td>
          </tr>
          <tr>
            <td>2. März</td>
            <td>Logo Design</td>
            <td>3</td>
          </tr>
          <tr>
            <td>5. März</td>
            <td>Logo Design, Visitenkarte</td>
            <td>5</td>
          </tr>
          <tr>
            <td>13. März</td>
            <td>Logo Design Fertigstellung</td>
            <td>4</td>
          </tr>
          <tr>
            <td>17. März</td>
            <td>Visitenkarte</td>
            <td>2</td>
          </tr>
          <tr>
            <td>20. März</td>
            <td>Logo Variationen</td>
            <td>5</td>
          </tr>
          <tr>
            <td>13. April</td>
            <td>3D Uhr Angaben</td>
            <td>2</td>
          </tr>
          <tr>
            <td>27. April</td>
            <td>Infografik, Logo Tippfehler Ausbesserung</td>
            <td>2</td>
          </tr>
          <tr>
            <td>1. Juni</td>
            <td>XD Tutorials</td>
            <td>1</td>
          </tr>
          <tr>
            <td>2. Juni</td>
            <td>Infografik</td>
            <td>1</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
  <div class="middle-content">
    <div class="center-piece">
      <h2>Fabian <span class="hours-spent"> - 37,5 Stunden</span></h2>
      <div class="overlow-table">
        <table style="width:100%">
          <tr>
            <th>Datum</th>
            <th>Arbeit</th>
            <th>Stunden</th>
          </tr>
          <tr>
            <td>23. Feb</td>
            <td>Start, erste Übrlegungen</td>
            <td>2</td>
          </tr>
          <tr>
            <td>27. Feb</td>
            <td>Ideen für Logo und Styleguide</td>
            <td>2</td>
          </tr>
          <tr>
            <td>1. März</td>
            <td>Ideen für Logo und Styleguide</td>
            <td>2</td>
          </tr>
          <tr>
            <td>2. März</td>
            <td>PowerPoint Tutorials</td>
            <td>3</td>
          </tr>
          <tr>
            <td>13. März</td>
            <td>Styleguide start</td>
            <td>1</td>
          </tr>
          <tr>
            <td>20. März</td>
            <td>Schriftart ausgewählt</td>
            <td>1</td>
          </tr>
          <tr>
            <td>13. April</td>
            <td>Styleguide Slidemaster Tutorials</td>
            <td>2,5</td>
          </tr>
          <tr>
            <td>20. April</td>
            <td>Styleguide Layout Idee + Design</td>
            <td>3</td>
          </tr>
          <tr>
            <td>27. April</td>
            <td>Zwischenpräsentation</td>
            <td>2,5</td>
          </tr>
          <tr>
            <td>9. Mai</td>
            <td
              >Zwischenpräsentation Styleguide restliche Folien erstellt +
              Layout design</td
            >
            <td>2</td>
          </tr>
          <tr>
            <td>10. Mai</td>
            <td>Styleguide Layout</td>
            <td>1</td>
          </tr>
          <tr>
            <td>1. Juni</td>
            <td>Styleguide befüllt</td>
            <td>1</td>
          </tr>
          <tr>
            <td>2. Juni</td>
            <td>Styleguide befüllt</td>
            <td>2</td>
          </tr>
          <tr>
            <td>3. Juni</td>
            <td>Styleguide befüllt</td>
            <td>1,5</td>
          </tr>
          <tr>
            <td>12. Juni</td>
            <td>Styleguide befüllt</td>
            <td>2</td>
          </tr>
          <tr>
            <td>13. Juni</td>
            <td>Styleguide befüllt</td>
            <td>2,5</td>
          </tr>
          <tr>
            <td>14. Juni</td>
            <td>Styleguide befüllt</td>
            <td>2,5</td>
          </tr>
          <tr>
            <td>15. Juni</td>
            <td>Endpräsentation</td>
            <td>4</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
  <div class="right-content">
    <div class="center-piece">
      <h2>Lukas <span class="hours-spent"> - 84 Stunden</span></h2>
      <div class="overlow-table">
        <table style="width:100%">
          <tr>
            <th>Datum</th>
            <th>Arbeit</th>
            <th>Stunden</th>
          </tr>
          <tr>
            <td>23. März</td>
            <td>Start, erste Übrlegungen, Aufgabenteilung</td>
            <td>2</td>
          </tr>
          <tr>
            <td>24. März</td>
            <td>Logo Ideen visualisierung</td>
            <td>3</td>
          </tr>
          <tr>
            <td>26. März</td>
            <td>Blender Modelling & ThreeJS Rendering Testing</td>
            <td>4</td>
          </tr>
          <tr>
            <td>27. März</td>
            <td>Techstack Setup (Libraries + Dependencies + NodePackages)</td>
            <td>3</td>
          </tr>
          <tr>
            <td>30. März</td>
            <td>Fertigstellung von Vite und Svelte Setup</td>
            <td>1</td>
          </tr>
          <tr>
            <td>4. April</td>
            <td>Started Blender Object (Uhr)</td>
            <td>5</td>
          </tr>
          <tr>
            <td>10. April</td>
            <td>Erstellen einer simplen 3D Uhr</td>
            <td>10</td>
          </tr>
          <tr>
            <td>17. April</td>
            <td>Fertigstellung des finallen Uhrmantels</td>
            <td>8</td>
          </tr>
          <tr>
            <td>24. April</td>
            <td>Kreierung des Ziffernblattes</td>
            <td>6</td>
          </tr>
          <tr>
            <td>4. Mai</td>
            <td>Erstellen der Materialien und Posing für Render</td>
            <td>14</td>
          </tr>
          <tr>
            <td>11. Mai</td>
            <td>Design der Website</td>
            <td>9</td>
          </tr>
          <tr>
            <td>25. Mai</td>
            <td>Start der Homepage</td>
            <td>6</td>
          </tr>
          <tr>
            <td>28. Mai</td>
            <td>Präsentationsframework</td>
            <td>8</td>
          </tr>
          <tr>
            <td>14. Juni</td>
            <td>Blogpage</td>
            <td>1</td>
          </tr>
          <tr>
            <td>15. Juni</td>
            <td>Endpräsentation</td>
            <td>4</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
  <div class="slideNumber">
    <span>3</span>
  </div>
</div>

<div class="container wrapper" id="slide-4">
  <div class="left-content">
    <div class="center-piece">
      <h1>Resümee</h1>
      <h2>Was lief gut.</h2>
      <h2>Kommunikation :</h2>
      <p style="width: 75%;" />
    </div>
  </div>
  <div class="right-content">
    <div>
      <h2>Was lief nicht so gut.</h2>
      <h2>Kommunikation :</h2>
      <p style="width: 75%;">
        Benötigte Inhalte wurden erst spät an das Team weitergegeben und
        beeinträchtigten den Fortschritt massiv.
      </p>
      <h3>Zeitplanung :</h3>
      <p style="width: 75%;">
        Am Schluss fehlte die Motivation und Schlussende hat den Fokus auf
        andere Dinge erhöht. Dadurch wurde der Fortschritt verlangsamt.
      </p>
    </div>
  </div>
  <div class="slideNumber">
    <span>4</span>
  </div>
</div>

<style lang="less">
  .hours-spent {
    color: #4c4c4c;
  }

  #slide-2 .right-content {
    justify-content: left;
  }

  #slide-2 .right-content div {
    margin-left: 4rem;
  }

  h3 {
    color: #000;
    font-weight: 700;
    font-size: 1.5rem;
    margin-block-end: 0;
  }

  #slide-3 .center-piece {
    margin-top: 5.5rem;
  }

  #slide-1 .left-content .center-piece,
  #slide-2 .left-content .center-piece {
    padding-left: 4rem;
  }

  .overlow-table::-webkit-scrollbar {
    width: 0px;
  }

  .hours-absoulte {
    position: absolute;
    top: 2.5rem;
  }

  th {
    background: #1d1d1d;
    color: white;
    font-weight: 700;
  }

  tr:nth-child(even) td {
    background: #c4c4c4;
  }

  tr:nth-child(odd) td {
    background: #e0e0e0;
  }

  .overlow-table {
    overflow-y: scroll;
    height: 46.4rem;
    border-bottom: 1px solid #737373;
    border-top: 1px solid #737373;
  }

  .container {
    position: relative;
    padding: 1rem;
    display: flex;
    gap: 1rem;
    flex-grow: 1;
    transition: ease 2s;
  }

  .container ul,
  table {
    color: #1d1d1d;
  }

  th,
  td {
    padding: 1rem;
  }

  table,
  th,
  td {
    text-align: left;
    border: 1px solid black;
    border-collapse: collapse;
  }

  .slideNumber {
    color: black;
    position: absolute;
    right: 1.5rem;
    top: 1.5rem;
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

  #slide-2,
  #slide-3,
  #slide-4,
  #slide-5,
  #slide-6,
  #slide-7,
  #slide-8,
  #slide-9 {
    position: fixed;
    width: calc(100vw - 2rem);
    height: calc(100vh - 2rem);
    height: calc(100svh - 2rem);
    transform: translateX(100%);
  }

  .wrapper {
    background: linear-gradient(45deg, #ffffff, #ffffff);
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
    width: fit-content;
    padding: 1rem 1.5rem;
    border-radius: 1rem;
  }

  .wrapper ul {
    background: rgb(255, 255, 255);
    padding: 1rem 1.5rem;
    border-radius: 1rem;
    padding-left: 2.5rem;
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

  .middle-content {
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
