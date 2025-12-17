<script>
</script>

<svelte:head>
  <title>Attendee Guide - mardi.camp 2026</title>
  <link rel="icon" href="/favicon.svg" type="image/svg+xml" />
</svelte:head>

<main class="flex flex-col items-center justify-center min-h-screen">
  <div id="container" class="m-4 max-w-3xl">
    <div class="text-center text-white">
      <h1 class="text-4xl font-bold">mardi.camp</h1>
      <p class="text-2xl mt-2 font-bold text-yellow-300">Attendee Guide</p>
      <p class="text-lg mt-1">
        <a href="/" class="text-purple-300 hover:text-purple-400 transition-colors duration-150">&larr; Back to homepage</a>
      </p>
    </div>

    <!-- Neighborhoods -->
    <div class="mt-8">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
        <h2 class="text-2xl font-bold text-white text-center mb-4">Neighborhoods</h2>

        <div class="text-white space-y-4">
          <div>
            <h3 class="text-xl font-bold text-yellow-300">French Quarter</h3>
            <p>The historic heart of New Orleans. Jackson Square, St. Louis Cathedral, Bourbon Street (the chaos), and Royal Street (the charm). Tourist central but worth seeing.</p>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Frenchmen Street / Marigny</h3>
            <p>Where locals go for live music. Multiple clubs with brass bands, jazz, funk. Way better vibe than Bourbon if you want actual music.</p>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Uptown / St. Charles</h3>
            <p>Where most parades roll. Garden District mansions, oak-lined streets. Take the St. Charles streetcar.</p>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Mid-City</h3>
            <p>Endymion parade territory. City Park, the Sculpture Garden, and some great neighborhood spots.</p>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Treme</h3>
            <p>Oldest African American neighborhood in the US. Armstrong Park, second lines on Sundays. Respect the neighborhood.</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Food & Drink -->
    <div class="mt-8">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
        <h2 class="text-2xl font-bold text-white text-center mb-4">Food & Drink</h2>

        <div class="text-white space-y-4">
          <div>
            <h3 class="text-xl font-bold text-yellow-300">Coffee</h3>
            <ul class="list-disc list-inside ml-2">
              <li><strong>Cafe du Monde</strong> - Obligatory. Beignets and chicory coffee. Cash only, open 24 hours.</li>
              <li><strong>French Truck Coffee</strong> - Actually good coffee if you need a real espresso.</li>
            </ul>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Quick Eats</h3>
            <ul class="list-disc list-inside ml-2">
              <li><strong>Verti Marte</strong> - Legendary deli in the Quarter. Get any of the sandwiches trust me.</li>
              <li><strong>Clover Grill</strong> - 24-hour diner. Burgers cooked under a hubcap. Weird and great.</li>
            </ul>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Sit-down</h3>
            <ul class="list-disc list-inside ml-2">
              <li><strong>Stanley</strong> - On Jackson Square. Brunch spot, a little bougier.</li>
            </ul>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Bars & Music</h3>
            <ul class="list-disc list-inside ml-2">
              <li><strong>Kermit's Treme Mother-in-Law Lounge</strong> - Kermit Ruffins' spot. Brass band, BBQ, the real deal.</li>
              <li><strong>Bullet's Sports Bar</strong> - Dive bar in the 7th Ward. If you're feeling adventurous.</li>
              <li><strong>Tipitina's</strong> - Legendary Uptown music venue. Check the schedule.</li>
              <li><strong>Frenchmen Street</strong> - Just walk down and follow your ears. d.b.a., Spotted Cat, Blue Nile.</li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <!-- Things to See -->
    <div class="mt-8">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
        <h2 class="text-2xl font-bold text-white text-center mb-4">Things to See</h2>

        <div class="text-white space-y-4">
          <ul class="list-disc list-inside ml-2 space-y-2">
            <li><strong>National WWII Museum</strong> - Legitimately world-class. Plan half a day minimum.</li>
            <li><strong>Armstrong Park</strong> - Named for Louis Armstrong. Congo Square, where jazz was born.</li>
            <li><strong>St. Louis Cemetery No. 1</strong> - Above-ground tombs. Requires a tour guide now.</li>
            <li><strong>City Park</strong> - Sculpture garden, Besthoff collection, beautiful oaks.</li>
            <li><strong>Garden District walking tour</strong> - Mansions, history, Anne Rice's house (RIP).</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Costumes -->
    <div class="mt-8">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-purple-400">
        <h2 class="text-2xl font-bold text-white text-center mb-4 text-purple-300">Costumes & What to Wear</h2>

        <div class="text-white space-y-4">
          <p>Costumes are encouraged, especially on Mardi Gras day. You'll feel underdressed without one.</p>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Coordinated Group Themes</h3>
            <ul class="list-disc list-inside ml-2 space-y-2">
              <li><strong>Saturday (Valentine's Day / Endymion)</strong> - Some folks doing campy Valentine's costumes. Red, white, pink.</li>
              <li><strong>Tuesday (Mardi Gras)</strong> - Disco ball theme costumes for the St. Anne's parade.</li>
            </ul>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">General Tips</h3>
            <ul class="list-disc list-inside ml-2 space-y-2">
              <li>Shiny, sparkly, colorful. More is more.</li>
              <li>Mardi Gras colors: purple (justice), gold (power), green (faith).</li>
              <li>Comfortable shoes. You'll be standing and walking for hours.</li>
              <li>Layers. February in New Orleans can be 40F or 70F.</li>
              <li>Pockets or a small bag for your throws (beads, cups, doubloons).</li>
            </ul>
          </div>

          <div>
            <h3 class="text-xl font-bold text-yellow-300">Skull and Bones (Mardi Gras morning)</h3>
            <p>Some people we know are joining the Skull and Bones Gang on Mardi Gras morning. This is a traditional Black masking tradition, starts before dawn in the Treme. Skeleton costumes, door-knocking to wake people up and remind them of mortality. Not a tourist thing, but if you're invited and want to participate, ask in the groupchat.</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Practical Tips -->
    <div class="mt-8">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
        <h2 class="text-2xl font-bold text-white text-center mb-4">Practical Tips</h2>

        <div class="text-white space-y-4">
          <ul class="list-disc list-inside ml-2 space-y-2">
            <li><strong>Cash</strong> - Many places are cash-only or have ATM fees. Bring some.</li>
            <li><strong>Rideshare</strong> - Uber/Lyft work but surge pricing is real. The streetcar is $1.25.</li>
            <li><strong>Parade viewing</strong> - The organizers (me and Nathan) are bringing stepladders and camping chairs for the spot on Napoleon for the uptown parades. Some may be available for other days/times if you want to borrow them (lose it/break it, you bought it).</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Contact -->
    <div class="mt-8 mb-8">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-green-400">
        <h2 class="text-2xl font-bold text-white text-center mb-4 text-green-300">Questions?</h2>

        <p class="text-white text-center">
          Text or DM <a href="https://twitter.com/whiskeytuesday" class="text-purple-300 hover:text-purple-400" target="_blank" rel="noopener noreferrer">@whiskeytuesday</a> any time. Seriously, any time. I want you to have a good time.
        </p>
      </div>
    </div>

    <p class="text-center mb-8">
      <a href="/" class="text-purple-300 hover:text-purple-400 transition-colors duration-150">&larr; Back to homepage</a>
    </p>
  </div>

  <footer class="w-full bg-gray-800 text-white p-2 text-center opacity-50">
    <p class="text-sm">
      &copy; {new Date().getFullYear()}
      mardi.camp is a project of
      <a href="https://www.twitter.com/whiskeytuesday">
        @whiskeytuesday
      </a>
      be good to each other stay cool.
    </p>
    <p class="text-sm">The 2025 website is available <a href="/2025">here.</a></p>
  </footer>
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: 'MS Sans Serif', Arial, sans-serif;
    color: #000;
    background-image: linear-gradient(to bottom right, #0AA14D, #582B7D, #FFD700);
  }

  a {
    text-decoration: underline;
  }
</style>
