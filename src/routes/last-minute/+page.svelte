<script>
  import LookingAhead2027 from '$lib/components/LookingAhead2027.svelte';

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
        formStatus = result.message || "Thanks! I'll be in touch soon. Laissez les bons temps rouler!";
        form.reset();
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
  <title>Last Minute Signups - mardi.camp 2026</title>
  <link rel="icon" href="/favicon.svg" type="image/svg+xml" />
</svelte:head>

<main class="flex flex-col items-center justify-center min-h-screen">
  <div id="container" class="m-4">
    <div class="text-center text-white">
      <h1 class="text-4xl font-bold">mardi.camp</h1>
      <p class="text-2xl mt-2 font-bold text-yellow-300">Last Minute Signups</p>
      <p class="text-lg mt-2">February 12th - 19th, 2026</p>
      <p class="text-lg mt-1">
        <a href="/" class="text-purple-300 hover:text-purple-400 transition-colors duration-150">&larr; Back to homepage</a>
      </p>

      <div class="mt-8 max-w-2xl mx-auto text-left">
        <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
          <h2 class="text-2xl font-bold text-center mb-4">The Situation</h2>

          <p class="mb-4">
            We currently have about <strong>15 people</strong> coming to mardicamp 2026, and our current Airbnbs are full.
          </p>

          <p class="mb-4">
            That said, I can probably jam a few more people in somewhere if you're down to join us. And if enough new people sign up, we'll expand to another spot.
          </p>

          <p class="mb-4">
            <strong>Cost:</strong> Expect approximately <span class="text-yellow-300 font-bold">$1,100 USD</span> for the week (Feb 12th-19th). This covers accommodation and minor expenses (commemorative badge and maybe other fun extras).
          </p>

          <p class="mb-4">
            If we don't expand into another unit and just one or two people join up, I might be able to get you somewhere for cheaper, but I can't guarantee it. Last minute signups are necessarily going to be kind of manually planned.
          </p>

          <p class="mb-4">
            <strong>Event schedule:</strong> The schedule on the <a href="/" class="text-purple-300 hover:text-purple-400">homepage</a> will be filled out later today (Wednesday, December 17th).
          </p>

          <h3 class="text-xl font-bold mt-6 mb-3">Want to come?</h3>
          <p class="mb-4">
            DM me on Twitter <a href="https://twitter.com/whiskeytuesday" class="text-purple-300 hover:text-purple-400" target="_blank" rel="noopener noreferrer">@whiskeytuesday</a> or fill out the form below.
          </p>
        </div>
      </div>

      <!-- Signup Form -->
      <div class="mt-8 max-w-2xl mx-auto">
        <div class="bg-black bg-opacity-30 backdrop-blur-sm rounded-lg p-6 border border-yellow-300">
          <h2 class="text-2xl font-bold text-center mb-4">Last Minute Signup Form</h2>

          <form on:submit|preventDefault={handleSubmit} class="space-y-4 text-left">
            <input type="hidden" name="access_key" value="f9b8439f-cf20-40c1-809e-a88b2a9fcc45">
            <input type="hidden" name="subject" value="Mardicamp 2026 - LAST MINUTE SIGNUP">
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

            <div>
              <label for="additional-people" class="block text-white font-medium mb-2">How many people total (including you)?</label>
              <select
                id="additional-people"
                name="additional-people"
                class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                required
              >
                <option value="">Select number</option>
                <option value="1">Just me</option>
                <option value="2">2 people</option>
                <option value="3">3 people</option>
                <option value="4+">4+ people</option>
              </select>
            </div>

            <div>
              <label for="message" class="block text-white font-medium mb-2">Anything else I should know?</label>
              <textarea
                id="message"
                name="message"
                rows="3"
                class="w-full px-3 py-2 text-black border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-300"
                placeholder="Optional: Tell me about yourself, any constraints, etc."
              ></textarea>
            </div>

            <div class="text-center">
              <button
                type="submit"
                class="px-8 py-3 bg-green-600 text-white font-bold rounded-lg border border-yellow-300 hover:bg-green-700 transition-colors duration-150"
              >
                Sign Me Up
              </button>
            </div>
          </form>
        </div>
      </div>

      <!-- 2027 Teaser -->
      <div class="mt-8 max-w-2xl mx-auto">
        <LookingAhead2027 />
      </div>

      <p class="mt-8">
        <a href="/" class="text-purple-300 hover:text-purple-400 transition-colors duration-150">&larr; Back to homepage</a>
      </p>
    </div>
  </div>

  <footer class="w-full bg-gray-800 text-white p-2 text-center opacity-50 mt-8">
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
      <p class="text-lg mb-6 {formStatus.includes('Thanks') || formStatus.includes('Success') ? 'text-green-600' : formStatus && formStatus !== 'Submitting...' ? 'text-red-600' : 'text-gray-700'}">{formStatus || 'Submitting your information...'}</p>
      <button on:click={() => formStatus = ""} class="{formStatus && formStatus !== 'Submitting...' ? 'bg-purple-600 hover:bg-purple-700 text-white font-bold py-2 px-6 rounded-lg transition border border-yellow-300' : 'hidden'}">
        Close
      </button>
    </div>
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
