<script>
  import { X, Square, Minus } from "lucide-svelte";

  // always show time in New Orleans time
  let currentTime = new Date().toLocaleTimeString(
    "en-US",
    { timeZone: "America/Chicago" },
  );

  setInterval(() => {
    currentTime = new Date().toLocaleTimeString(
      "en-US",
      { timeZone: "America/Chicago" },
    );
  }, 1000);

  const handleMinimize = () => {
    alert("something funny should happen when you click this, I think");
  };

  const handleMaximize = () => {
    alert("something funny should happen when you click that too");
  };

  const handleClose = () => {
    // haha gotem
    window.location.href = "https://www.youtube.com/watch?v=dQw4w9WgXcQ";
  };
</script>

<header class="win98-header">
  <div class="title-bar">
    <div class="title-bar-text">Mardi.camp - Tech Twitter Mardi Gras 2025</div>
    <div class="title-bar-controls">
      <button aria-label="Minimize" on:click={handleMinimize}>
        <Minus size="16" color="#000" />
      </button>
      <button aria-label="Maximize" on:click={handleMaximize}>
        <Square class="mx-auto my-auto" size="12" color="#000" />
      </button>
      <button aria-label="Close" on:click={handleClose}>
        <X size="16" color="#000" />
      </button>
    </div>
  </div>
  <nav class="win98-menu">
    <ul>
      <li>
        <a href="https://www.mardigrasneworleans.com/parades/">
          Official NOMG schedule
        </a>
      </li>
      <!-- <li><a href="#">j</a></li> -->
      <!-- <li><a href="#">Bar</a></li> -->
    </ul>
    <div class="system-tray">
      <span>{currentTime} in New Orleans</span>
    </div>
  </nav>
</header>

<style>
  .win98-header {
    background-color: #000080;
    color: #fff;
    padding: 2px;
  }

  .win98-menu {
    display: flex;
    background-color: #c0c0c0;
    justify-content: space-between;
    padding: 0.25rem 0.5rem 0.25rem 0.5rem;
  }

 .win98-menu ul {
    padding: 0;
    margin: 0;
    display: flex;
    list-style-type: none;
  }

  .win98-menu a {
    color: #000;
    text-decoration: none;
  }

  .win98-menu a:hover {
    text-decoration: underline;
  }

  .title-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #000080;
    /* css padding direction order is top right bottom left */
    padding: 0.25rem 0.5rem 0.25rem 0.5rem;
  }

  .title-bar-text {
    font-weight: bold;
  }

  .title-bar-controls button {
    width: 16px;
    height: 14px;
    border: none;
    background-color: #c0c0c0;
    margin-left: 2px;
  }

  .system-tray {
    background-color: #c0c0c0;
    text-align: right;
    color: #000;
  }
</style>
