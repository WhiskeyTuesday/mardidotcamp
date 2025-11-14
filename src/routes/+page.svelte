<script>
  import { onMount } from 'svelte';
  import mascot from '$lib/mascot.png';
  import fates from '$lib/fates.jpeg';

  const mggreen = '#0AA14D';
  const mgpurple = '#582B7D';
  const mggold = '#FFD700';

  /*
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
  */

  let daysUntil = Math.ceil((new Date('2026-02-17') - new Date()) / (1000 * 60 * 60 * 24));

  const events = [
    {
      date: 'February 11th',
      name: 'Airbnb load in',
      time: '4:00 PM',
      location: 'final location tbd',
      memo: 'Get settled in and ready for the week ahead.'
    },
    {
      date: 'February 12th',
      name: 'Krewe of Muses Parade',
      time: '6:00 PM',
      location: 'Uptown, St. Charles Ave',
      memo: 'The Muses parade is best known for its all-female riders and its signature high heeled shoe throws.'
    },
    {
      date: 'Onward',
      name: 'More events tbd',
      time: 'TBD',
      location: 'TBD',
      memo: 'Stay tuned for more events as I firm up plans!'
    }
  ];

  let activeEvent = {};

  // Form status tracking
  let formStatus = "";

  const handleSubmit = async (event) => {
    formStatus = "Submitting...";

    try {
      const form = event.target;
      const formData = new FormData(form);
      const object = Object.fromEntries(formData);

      // Validation: require at least email or twitter
      if (!object.email && !object.twitter) {
        formStatus = "Please provide either an email or Twitter handle.";
        return;
      }

      const json = JSON.stringify(object);

      const response = await fetch("https://api.web3forms.com/submit", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Accept: "application/json",
        },
        body: json,
      });

      const result = await response.json();

      if (result.success) {
        formStatus = result.message || "Thanks for signing up! Laissez les bons temps rouler!";
        form.reset(); // Reset the form on success
      } else {
        formStatus = result.message || "There was an error submitting your form.";
      }
    } catch (error) {
      formStatus = "There was an error submitting your form.";
      console.error("Form submission error:", error);
    }
  };
</script>

<svelte:head>
  <link rel="icon" href="/favicon.svg" type="image/svg+xml" />
</svelte:head>

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
      <p class="text-lg mt-2">mardi dot camp February 11th - 19th 2026</p>
      <p class="text-lg mt-2 underline hover:text-purple-300 transition-colors duration-150">
        <a href="https://www.mardigrasneworleans.com/parades/">Official Mardi Gras Parade Schedule</a>
      </p>

      <!-- buttons
      <button
        class="mt-4 mx-1 px-6 py-2 bg-purple-700 text-white rounded border border-yellow-300 hover:bg-purple-800 transition-colors duration-150"
        on:click={() => document.getElementById('ticketModal').classList.remove('hidden')}
      >
        Apply for tickets
      </button>
      -->

      <button
        class="mt-4 px-6 py-2 bg-purple-700 text-white rounded border border-yellow-300 hover:bg-purple-800 transition-colors duration-150"
        on:click={() => document.getElementById('scheduleModal').classList.remove('hidden')}
      >
        Mardicamp events
      </button>

      <h1 class="text-2xl font-bold mt-8">wtf is this?</h1>
      <p class="text-lg mt-2 width-full max-w-2xl mx-auto">
        New Orleans Mardi Gras 2026.
      </p>
      <p class="text-lg mt-2 width-full max-w-2xl mx-auto">
        Me, you maybe, and a bunch of our weird twitter/tpot/vibecamp/ingroup
        friends. Why? Well because it's fun.
      </p>

      <h1 class="text-2xl font-bold mt-8">isn't Mardi Gras just a big frat party with titties and beads?</h1>
      <p class="text-lg mt-2 width-full max-w-2xl mx-auto">
        Nah, Mardi Gras is very choose your own adventure.
      </p>
      <p class="text-lg mt-2 width-full max-w-2xl mx-auto">
        Bourbon Street can be fun and you probably want to at least see the
        madness but between the day and night parades, the music, the balls,
        the food scene; there's way more to it than drugs, drunkenness,
        and boobs. That said,
        <!-- do what you wanna youtube link -->
        <a
          href="https://www.youtube.com/watch?v=PsQzRZyWidk"
          class="text-purple-300 hover:text-purple-400 transition-colors duration-150"
          target="_blank"
          rel="noopener noreferrer"
        >
          don't let me stop you.
        </a>
      </p>
    </div>
    <!-- Signup Form Section -->
    <!--
    <div class="mt-12 max-w-2xl mx-auto">
      <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
        <h2 class="text-2xl font-bold text-white text-center mb-4">Subscribe for More Information</h2>
        <p class="text-white text-center mb-6">Get updates about Mardi Camp 2026 and help us plan accordingly!</p>

        <script src="https://web3forms.com/client/script.js" async defer></script>
        <form on:submit|preventDefault={handleSubmit} class="space-y-4">
          <input type="hidden" name="access_key" value="f9b8439f-cf20-40c1-809e-a88b2a9fcc45">
          <input type="hidden" name="subject" value="Mardicamp 2026 info signup">
          <input type="checkbox" name="botcheck" class="hidden" style="display: none;">
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div>
              <label for="email" class="block text-white font-medium mb-2">Email</label>
              <input
                type="email"
                id="email"
                name="email"
                class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                placeholder="your@email.com"
              >
              </div>
              <div>
                <label for="twitter" class="block text-white font-medium mb-2">Twitter @</label>
                <input
                  type="text"
                  id="twitter"
                  name="twitter"
                  class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                  placeholder="@yourhandle"
                >
                </div>
              </div>

              <div class="text-sm text-yellow-200 text-center">
                *At least one contact method (email or Twitter) is required
              </div>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                  <label for="attendance" class="block text-white font-medium mb-2">How likely are you to attend?</label>
                  <select
                    id="attendance"
                    name="attendance"
                    class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                    required
                  >
                    <option value="">Select likelihood</option>
                    <option value="definitely">Definitely attending</option>
                    <option value="very-likely">Very likely</option>
                    <option value="maybe">Maybe</option>
                    <option value="probably-not">Probably not</option>
                    <option value="just-curious">Just curious</option>
                  </select>
                </div>
                <div>
                  <label for="additional-people" class="block text-white font-medium mb-2">Additional people you'd bring</label>
                  <select
                    id="additional-people"
                    name="additional-people"
                    class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                    required
                  >
                    <option value="">Select number</option>
                    <option value="0">Just me</option>
                    <option value="1">1 other person</option>
                    <option value="2">2 other people</option>
                    <option value="3">3 other people</option>
                    <option value="4+">4+ other people</option>
                  </select>
                </div>
              </div>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="flex items-center">
                  <input
                    type="checkbox"
                    id="been-to-nola"
                    name="been-to-nola"
                    value="yes"
                    class="mr-2 h-4 w-4 text-purple-600 focus:ring-yellow-300 border-gray-300 rounded"
                  >
                    <label for="been-to-nola" class="text-white">I've been to New Orleans before</label>
                  </div>
                  <div class="flex items-center">
                    <input
                      type="checkbox"
                      id="been-to-carnival"
                      name="been-to-carnival"
                      value="yes"
                      class="mr-2 h-4 w-4 text-purple-600 focus:ring-yellow-300 border-gray-300 rounded"
                    >
                      <label for="been-to-carnival" class="text-white">I've been to New Orleans during carnival season</label>
                    </div>
                  </div>

                  <div>
                    <label for="accommodation" class="block text-white font-medium mb-2">Accommodation preference</label>
                    <select
                      id="accommodation"
                      name="accommodation"
                      class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                      required
                    >
                      <option value="">Select preference</option>
                      <option value="with-group">Stay with the group</option>
                      <option value="own-accommodation">Get my own accommodation</option>
                      <option value="depends">Depends on options/cost</option>
                      <option value="not-sure">Not sure yet</option>
                    </select>
                  </div>

                  <div>
                    <label for="vibe" class="block text-white font-medium mb-2">Which vibe are you most interested in?</label>
                    <select
                      id="vibe"
                      name="vibe"
                      class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                      required
                    >
                      <option value="">Select vibe</option>
                      <option value="party-bourbon">Party/Bourbon Street</option>
                      <option value="music-frenchman">Music/Frenchman Street</option>
                      <option value="parades-family">Parades/Family-friendly</option>
                      <option value="secret-third-thing">Secret third thing</option>
                      <option value="all-of-the-above">All of the above</option>
                      <option value="other">Other</option>
                    </select>
                  </div>

                  <div class="h-captcha" data-captcha="true"></div>
                  <div class="text-center">
                    <button
                      type="submit"
                      class="px-8 py-3 bg-green-600 text-white font-bold rounded-lg border border-yellow-300 hover:bg-green-700 transition-colors duration-150"
                    >
                      Subscribe for Updates
                    </button>
                  </div>
                </form>
              </div>
            </div>
            -->

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

        <!-- Form Status Modal -->
        <div id="formModal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center {formStatus ? '' : 'hidden'}">
          <div class="bg-white rounded-lg shadow-xl overflow-hidden w-full max-w-md border-2 border-yellow-300 relative">
            <div class="bg-purple-700 text-white p-4 text-center">
              <h3 class="font-bold text-xl">Form Submission</h3>
            </div>
            <div class="p-6 text-center">
              <!-- Spinner -->
              <div class="{formStatus && formStatus === 'Submitting...' ? 'mx-auto mb-4' : 'hidden'}">
                <svg class="animate-spin h-10 w-10 text-purple-700 mx-auto" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                  <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                  <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                </svg>
              </div>
              <p class="text-lg mb-6 {formStatus === 'Thanks for signing up! Laissez les bons temps rouler!' || formStatus.includes('Success') ? 'text-green-600' : formStatus && formStatus !== 'Submitting...' ? 'text-red-600' : 'text-gray-700'}">{formStatus || 'Submitting your information...'}</p>
              <button on:click={() => formStatus = ""} class="{formStatus && formStatus !== 'Submitting...' ? 'bg-purple-600 hover:bg-purple-700 text-white font-bold py-2 px-6 rounded-lg transition border border-yellow-300' : 'hidden'}">
                Close
              </button>
            </div>
            <!-- yellow horizontal line at bottom -->
            <div class="h-1 bg-yellow-300"></div>
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
