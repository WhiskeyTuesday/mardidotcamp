<script>
  let currentTime = new Date().toLocaleTimeString();

  $: {
    setInterval(() => {
      currentTime = new Date().toLocaleTimeString();
    }, 1000);
  }
</script>

<header class="win98-header">
  <div class="title-bar">
    <div class="title-bar-text">Mardi.camp - Tech Twitter Mardi Gras 2025</div>
    <div class="title-bar-controls">
      <button aria-label="Minimize"></button>
      <button aria-label="Maximize"></button>
      <button aria-label="Close"></button>
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

  .win98-menu ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
    display: flex;
    background-color: #c0c0c0;
  }

  .win98-menu li {
    padding: 3px 6px;
  }

  .win98-menu a {
    color: #000;
    text-decoration: none;
  }

  .win98-menu a:hover {
    text-decoration: underline;
  }

  .system-tray {
    background-color: #c0c0c0;
    text-align: right;
    padding: 2px;
    color: #000;
  }
</style>
