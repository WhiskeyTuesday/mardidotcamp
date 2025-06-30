<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  import { onMount } from 'svelte';
  import mascot from '$lib/mascot.png';

  let marqueeText = "Welcome to Mardi.camp - The ultimate (only) ingroup weirdo"
  + " twitter gathering at Mardi Gras 2026 (probably). Laisez les bon temps"
  + " rouler? I hardly know her";

  let stars = [];

 const MARDI_GRAS_COLORS = [
    '#582B7D', // Purple
    '#0AA14D', // Green
    '#B8860B'  // Gold
  ];

  onMount(() => {
    const newStars = [];
    for (let i = 0; i < 50; i++) {
      newStars.push({
        x: Math.random() * 100,
        y: Math.random() * 100,
        baseSize: Math.random() * 3 + 5, // Random size for each star
        twinkleSpeed: 0.5 + Math.random(), // Random speed for each star
        offset: Math.random() * Math.PI * 2, // Random starting point in animation
        color: MARDI_GRAS_COLORS[Math.floor(Math.random() * 3)]
      });
    }
    stars = newStars;
  });
</script>

<svelte:head>
  <link rel="icon" href="/favicon-2025.png" type="image/png" />
</svelte:head>

<main class="win98-container">
  <Header />
  <div class="content-wrapper">
    <marquee class="space-jam-marquee">{marqueeText}</marquee>

    <div class="win98-window">
      <div class="window-title">About Mardi.camp</div>
      <div class="window-content">
        <p>Come to mardi gras with your weird twitter friends!</p>
        <div class="mb-4">
          March 2nd to 6th 2025
          <div class="text-xs text-gray-500 max-w-sm">
            *That's when the airbnb is, you can obviously come
            earlier or stay longer. I'm not in charge of the
            Louisiana state border or anything (yet).Add commentMore actions
          </div>
        </div>
        <p>Location: New Orleans, Louisiana</p>
      </div>
    </div>

    <div class="win98-window">
      <div class="window-title">Vibes</div>
      <div class="window-content">
        <p>
          Mardi Gras doesn't have to be about taking drugs,
          drinking too much, and taking your clothes off.
        </p>
        <p>That said, don't let me stop you.</p>
        <p>
          My vibe is much more about hanging out with cool people,
          eating beignets, and watching the parades go by.
          More Frenchman Street than Bourbon Street, iykyk.
        </p>
        <p>
          But I'm not your dad so
          <a href="https://www.youtube.com/watch?v=PsQzRZyWidk">
            do what you wanna.
          </a>
        </p>
      </div>
    </div>

    <div class="win98-window">
      <div class="window-title">Logistics</div>
      <div class="window-content">
      </div>
    </div>

    <div class="win98-window">
      <div class="window-title">Activities</div>
      <div class="window-content">
        <ul>
          <li>March 2nd: Something?</li>
          <li>March 3rd: Lundi Gras</li>
          <li>March 4th: Mardi Gras</li>
          <li>March 5th: Ash Wednesday, seek absolution</li>
          <li>March 6th: Leave probably</li>
        </ul>
      </div>
    </div>

    <div class="win98-window">
      <div class="window-title">Featured Guests</div>
      <div class="window-content">
        <ul>
          <li>@WhiskeyTuesday</li>
          <li>@dschorno</li>
        </ul>
      </div>
    </div>

    <div class="win98-window">
      <div class="window-title">Contact</div>
      <div class="window-content">
        <p>
          DM @WhiskeyTuesday on twitter if you're interested
          in coming or have any questions or want to help
          other people figure out their plans or want to
          organize something or want me to put you on the
          featured guest list or whatever.
        </p>
      </div>
    </div>

   <div class="space-background">
      {#each stars as star, i}
        <div
          class="star"
          style="
            left: {star.x}%;
            top: {star.y}%;
            --twinkle-speed: {star.twinkleSpeed}s;
            --size: {star.baseSize}px;
            --delay: {-star.offset}s;
            --star-color: {star.color};
          "
        >
        </div>
      {/each}
      <img src={mascot} alt="Mascot" class="mascot">
    </div>
  </div>
  <Footer />
</main>

<style>
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

  .content-wrapper {
    padding: 10px;
    background-color: #008080;
    color: #fff;
  }

  .space-jam-marquee {
    background-color: #000;
    color: #ff0;
    font-weight: bold;
    padding: 5px;
    margin-bottom: 10px;
  }

  .win98-window {
    background-color: #c0c0c0;
    border: 2px solid #fff;
    box-shadow: 2px 2px 0 #000;
    margin-bottom: 10px;
  }

  .win98-window p {
    padding-bottom: 1rem;
  }

  .win98-window p:last-child {
    padding-bottom: 0;
  }

  .window-title {
    background-color: #000080;
    color: #fff;
    padding: 0.25rem;
    padding-left: 0.5rem;
    font-weight: bold;
  }

  .window-content {
    padding: 10px;
    color: #000;
  }

  .space-background {
    position: relative;
    height: 200px;
    background-color: #fde1a2;
    overflow: hidden;
  }

  .star {
    position: absolute;
    border-radius: 50%;
    width: var(--size);
    height: var(--size);
    animation: twinkle var(--twinkle-speed) infinite ease-in-out;
    animation-delay: var(--delay);
  }

  @keyframes twinkle {
    0%, 100% {
      background-color: color-mix(in srgb, var(--star-color) 30%, transparent);
      transform: scale(0.8);
    }
    50% {
      background-color: var(--star-color);
      transform: scale(1.2);
    }
  }

  .mascot {
    position: absolute;
    bottom: 10px;
    right: 10px;
    max-width: 25%;
    animation: bounce 2s infinite;
  }

  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
  }

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
