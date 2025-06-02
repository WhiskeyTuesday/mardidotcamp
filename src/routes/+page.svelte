<script>
  import { onMount } from 'svelte';
  import mascot from '$lib/mascot.png';
  import fates from '$lib/fates.jpeg';

  const mggreen = '#0AA14D';
  const mgpurple = '#582B7D';
  const mggold = '#FFD700';

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

  let daysUntil = Math.ceil((new Date('2026-02-17') - new Date()) / (1000 * 60 * 60 * 24));

  const events = [
    {
      date: 'January 31',
      name: 'Krewe de Vieux',
      time: '2:00 PM',
      location: 'French Quarter',
      memo: 'A fun and quirky parade to kick off the festivities.'
    },
    {
      date: 'February 1',
      name: 'Krewe of Joan of Arc',
      time: '7:00 PM',
      location: 'French Quarter',
      memo: 'Celebrating the legacy of Joan of Arc with a unique twist.'
    }
  ];

  let activeEvent = {};
</script>

<main class="flex flex-col items-center justify-center min-h-screen">
  <div id="container" class="m-4">
    <div class="text-center text-white">
      <h1 class="text-4xl font-bold">mardi.camp</h1>
      <p class="text-lg mt-2">
        The ultimate (only) ingroup weirdo twitter gathering at Mardi Gras 2026 (probably).
      </p>
      <p class="text-lg mt-2">
        <span title="Let the good times roll" class="italic">Laissez les bon temps rouler</span>? I hardly know her.
      </p>
      <p class="text-lg mt-8">{daysUntil} days until Mardi Gras 2026</p>
      <p class="text-lg mt-2">Mardi Camp events begin January 31st</p>
      <p class="text-lg mt-2 underline hover:text-purple-300 transition-colors duration-150">
        <a href="https://www.mardigrasneworleans.com/parades/">Official Mardi Gras Parade Schedule</a>
      </p>
      <button
        class="mt-4 mx-1 px-6 py-2 bg-purple-700 text-white rounded border border-yellow-300 hover:bg-purple-800 transition-colors duration-150"
        on:click={() => document.getElementById('ticketModal').classList.remove('hidden')}
      >
        Apply for tickets
      </button>

      <button
        class="mt-4 px-6 py-2 bg-purple-700 text-white rounded border border-yellow-300 hover:bg-purple-800 transition-colors duration-150"
        on:click={() => document.getElementById('scheduleModal').classList.remove('hidden')}
      >
        Mardicamp events
      </button>
    </div>
    <div class="flex flex-col items-center m-8">
      <p class="text-white text-lg text-center">
        Mardi Camp is an unregistered not-for-profit (in that I expect to lose money every year).
      </p>
      <div class="p-0.5 mt-4 bg-gradient-to-br from-yellow-300 via-amber-400 to-yellow-600 rounded-lg">
        <div class="bg-gray-900 rounded-md p-2 text-white max-w-80 h-auto rounded-lg shadow-lg">
          <img
            src={fates}
            alt="deepfates tweet about unprofitable twitter camps"
          />
        </div>
      </div>
    </div>
  </div>
  <footer class="w-full bg-gray-800 text-white p-2 text-center opacity-50">
    <p class="text-sm">
      © {new Date().getFullYear()}
      mardi.camp is a project of
      <a href="https://www.twitter.com/whiskeytuesday">
        @whiskeytuesday
      </a>
      be good to each other stay cool.
    </p>
    <p class="text-sm">The 2025 website is available <a href="/2025">here.</a> </p>
  </footer>
</main>

<div id="ticketModal" class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 hidden">
  <div class="bg-white p-6 m-2 rounded-lg shadow-lg max-w-md w-full">
    <h2 class="text-xl font-bold mb-4">Apply for Tickets</h2>
    <p class="mb-4">Tickets are not available yet! Check back later.</p>
    <button
      class="px-4 py-2 bg-purple-500 text-white rounded hover:bg-green-600 transition-colors duration-150 border border-yellow-300"
      on:click={() => document.getElementById('ticketModal').classList.add('hidden')}
    >
      Close
    </button>
  </div>
</div>

<div id="scheduleModal" class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 hidden">
  <div class="bg-white p-6 m-2 rounded-lg shadow-lg max-w-md w-full">
    <h2 class="text-xl font-bold mb-4">mardicamp events</h2>
    <p class="text-lg mb-4">Event schedule tbd</p>
    <!-- TODO add when events are programmed
    <table class="w-full text-left border-collapse">
      <thead>
        <tr>
          <th class="border-b-2 border-gray-300 p-2">Event </th>
          <th class="border-b-2 border-gray-300 p-2"></th>
        </tr>
      </thead>
      <tbody>
        {#each events as event}
          <tr class="hover:bg-gray-100 transition-colors duration-150">
            <td class="border-b p-2">{event.name}</td>
            <td class="border-b p-2">
              <button
                class="text-green-500 hover:underline border border-green-300 rounded px-2 py-1 transition-colors duration-150 hover:bg-purple-200"
                on:click={() => {
                  document.getElementById('detailsModal').classList.remove('hidden');
                  activeEvent = event;
                }}
              >
                View Details
              </button>
            </td>
          </tr>
        {/each}
      </tbody>
    </table>
    -->

    <button
      class="px-4 py-2 bg-purple-500 text-white rounded hover:bg-green-600 transition-colors duration-150 border border-yellow-300"
      on:click={() => document.getElementById('scheduleModal').classList.add('hidden')}
    >
      Close
    </button>
  </div>
</div>

<!-- details submodal -->
<div id="detailsModal" class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 hidden">
  <div class="bg-white p-6 m-2 rounded-lg shadow-lg max-w-md w-full">
    <h2 class="text-xl font-bold mb-4">Event details</h2>
    <p class="mb-4">{activeEvent.memo}</p>
    <p class="mb-4">Date: {activeEvent.date}</p>
    <p class="mb-4">Time: {activeEvent.time}</p>
    <p class="mb-4">Location: {activeEvent.location}</p>
    <button
      class="px-4 py-2 bg-purple-500 text-white rounded hover:bg-green-600 transition-colors duration-150 border border-yellow-300"
      on:click={() => document.getElementById('detailsModal').classList.add('hidden')}
    >
      Close
    </button>
  </div>
</div>

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
