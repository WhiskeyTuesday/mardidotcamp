<script>
  import { X, Square, Minus } from "lucide-svelte";

  let currentTime = new Date().toLocaleTimeString();

  setInterval(() => {
    currentTime = new Date().toLocaleTimeString();
  }, 1000);

  const handleMinimize = () => {
    alert("something funny should happen when you click that, don't you think?");
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
    <!-- <ul>
      <li><a href="#about">About</a></li>
      <li><a href="#schedule">Schedule</a></li>
      <li><a href="#register">Register</a></li>
    </ul> -->
  </nav>
  <div class="system-tray">
    <span>{currentTime}</span>
  </div>
</header>

<style>
  .win98-header {
    background-color: #000080;
    color: #fff;
    padding: 2px;
  }

  .title-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #000080;
    padding: 3px 2px 3px 3px;
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
    padding: 2px;
    color: #000;
  }
</style>
