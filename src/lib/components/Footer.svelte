<script>
  import { page } from '$app/stores';
</script>

<footer class="win98-footer">
  <p>© 2025 Mardi.camp - All rights reserved</p>
  <p>Best viewed with Netscape Navigator or Internet Explorer 5</p>
  <p>
    <a href="{$page.url.href}">mardi.camp</a> is powered by
    <a href="https://www.lcc.solutions">The Lifestyle™ Computer Company</a>
    and maintained by <a href="https://www.elijasorensen.com">Elija Sorensen</a>
  </p>
  <p>be good to each other stay cool</p>
</footer>

<style>
  .win98-footer {
    background-color: #c0c0c0;
    border-top: 2px solid #fff;
    padding: 10px;
    text-align: center;
    font-size: 0.8em;
    color: #000;
  }

  /* reinstate default HTML anchor styles */
  a {
    color: #00f;
    text-decoration: underline;
  }

  a:hover {
    text-decoration: none;
  }

  a:visited {
    color: #551a8b;
  }

  a:visited:hover {
    color: #551a8b;
  }
</style>
