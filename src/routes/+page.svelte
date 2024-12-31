<script>
  import Content from '$lib/components/Content.svelte';
  import { onMount } from 'svelte';

  let marqueeText = "Welcome to Mardi.camp - The ultimate (only) ingroup weirdo twitter gathering at Mardi Gras 2025 (probably)";
  let stars = [];

  onMount(() => {
    for (let i = 0; i < 50; i++) {
      stars.push({
        x: Math.random() * 100,
        y: Math.random() * 100,
        size: Math.random() * 3 + 1
      });
    }
  });
</script>

<div class="content-wrapper">
  <marquee class="space-jam-marquee">{marqueeText}</marquee>

  <div class="win98-window">
    <div class="window-title">About Mardi.camp</div>
    <div class="window-content">
      <p>Come to mardi gras with your weird twitter friends!</p>
      <p>Or don't, I'm not your dad.</p>
      <p>Dates: March 2nd to 6th 2025 so far </p>
      <p class="text-sm text-gray-500">
        *everything subject to change
        I just came up with this idea as a joke ten minutes ago
      </p>
      <p>Location: New Orleans, Louisiana</p>
    </div>
  </div>

  <div class="win98-window">
    <div class="window-title">Vibes</div>
    <div class="window-content">
      <p>Mardi Gras doesn't have to be about taking drugs, drinking too much, and taking your clothes off.</p>
      <p>That said, don't let me stop you.</p>
      <p>My vibe is much more about hanging out with cool people, eating Beignets, and watching the parades go by. A much more Frenchman Street vibe than Bourbon Street.</p>
      <p>But I'm not your dad so <a href="https://www.youtube.com/watch?v=PsQzRZyWidk">do what you wanna</a></p>
      <br/>
    </div>
  </div>

  <div class="win98-window">
    <div class="window-title">Logistics</div>
    <div class="window-content">
      <p>I have put no thought into this, I have a hotel reservation I made months ago but you probably want to get together and figure out a big airbnb or make your own reservations sooner rather than later. Check back here for more information if anyone takes the initiative.</p>
    </div>
  </div>

  <div class="win98-window">
    <div class="window-title">Activities</div>
    <div class="window-content">
      <p>March 2nd: Something?</p>
      <p>March 3rd: Lundi Gras</p>
      <p>March 4th: Mardi Gras</p>
      <p>March 5th: Ash Wednesday, seek absolution</p>
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
      <p>DM @WhiskeyTuesday on twitter if you're interested in coming or have any questions or want to help other people figure out their plans or want to organize something or want me to put you on the featured guest list.</p>
      <p>Or don't, I'm not your dad.</p>
    </div>
  </div>

  <div class="space-background">
    {#each stars as star}
      <div class="star" style="left: {star.x}%; top: {star.y}%; width: {star.size}px; height: {star.size}px;"></div>
    {/each}
    <img src="https://placekitten.com/100/100" alt="Mascot" class="mascot">
  </div>
</div>

<style>
  /* I don't know where I overrode the default link colors but I'm putting them back */
  a {
    color: #00f;
  }

  a:hover {
    color: #f00;
  }

  a:visited {
    color: #800080;
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

  .window-title {
    background-color: #000080;
    color: #fff;
    padding: 2px;
    font-weight: bold;
  }

  .window-content {
    padding: 10px;
    color: #000;
  }

  .space-background {
    position: relative;
    height: 200px;
    background-color: #000;
    overflow: hidden;
  }

  .star {
    position: absolute;
    background-color: #fff;
    border-radius: 50%;
  }

  .mascot {
    position: absolute;
    bottom: 10px;
    right: 10px;
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
</style>
