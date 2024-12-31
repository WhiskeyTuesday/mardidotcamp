<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  import '../app.css';

  let { children } = $props();
</script>

<main class="win98-container">
  <Header />
  {@render children()}
  <Footer />
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: 'MS Sans Serif', Arial, sans-serif;
    background-color: #008080;
    color: #000;
  }

  .win98-container {
    width: 90%;
    max-width: 800px;
    margin: 20px auto;
    background-color: #c0c0c0;
    border: 2px solid #fff;
    box-shadow: 2px 2px 0 #000;
    padding: 2px;
  }
</style>
