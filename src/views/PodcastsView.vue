<template>





<main class="grid place-items-center min-h-screen  p-5">
  <div>
    <h1 class="text-4xl sm:text-5xl md:text-7xl font-bold text-gray-200 mb-5 text-center">Fait pour vous</h1>
    <figure class="max-w-screen-md mb-10 text-white mx-auto text-center">
      <svg class="w-10 h-10 mx-auto mb-3 text-gray-900 dark:text-gray-900" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 18 14">
          <path d="M6 0H2a2 2 0 0 0-2 2v4a2 2 0 0 0 2 2h4v1a3 3 0 0 1-3 3H2a1 1 0 0 0 0 2h1a5.006 5.006 0 0 0 5-5V2a2 2 0 0 0-2-2Zm10 0h-4a2 2 0 0 0-2 2v4a2 2 0 0 0 2 2h4v1a3 3 0 0 1-3 3h-1a1 1 0 0 0 0 2h1a5.006 5.006 0 0 0 5-5V2a2 2 0 0 0-2-2Z"/>
      </svg>
      <blockquote>
          <p class="text-2xl italic font-medium text-white">"Il est inutile de parler de l'amour, car l'amour possède sa propre voix, et parle de lui-même"</p>
      </blockquote>
      <figcaption class="flex items-center justify-center mt-6 space-x-3 rtl:space-x-reverse">
          
          <div class="flex items-center divide-x-2 rtl:divide-x-reverse divide-gray-00">
              <cite class="pe-3 font-medium text-white">Paulo Coelho   </cite>
              <cite class="ps-3 text-sm text-gray-100 dark:text-gray-900 pl-2 ml-2">   Écrivain</cite>
          </div>
      </figcaption>
  </figure>
    <section class="grid grid-cols-1 sm:grid-cols-3 gap-4">
      <!-- CARD 1 -->
      <div class="bg-red-900 shadow-lg rounded p-10">
        <div class="group relative">
          <!-- <img class="w-full md:w-72 block rounded" src="../public/type/paroles.jpg" alt="Album Cover" /> -->
          <audio id="audio1"  src="../c-koi-lamour.mp3" hidden></audio>
          <div class="absolute rounded bg-white bg-opacity-0 group-hover:bg-opacity-60 w-full h-full top-0 flex items-center justify-evenly group-hover:opacity-100 transition-opacity duration-300">
            <button onclick="document.getElementById('audio1').play()" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/play-circle-fill.svg" alt="Play" class="w-8 h-8">
            </button>
            <button onclick="document.getElementById('audio1').pause()" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/pause-fill.svg" alt="Pause" class="w-8 h-8">
            </button>
            <button onclick="changeVolume('audio1', 0.1)" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/volume-up-fill.svg" alt="Volume Up" class="w-8 h-8">
            </button>
            <button onclick="changeVolume('audio1', -0.1)" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/volume-down-fill.svg" alt="Volume Down" class="w-8 h-8">
            </button>
          </div>
        </div>
        <div class="p-5">
          <h3 class="text-white text-lg">C'est quoi l'Amour ?</h3>
          <p class="text-gray-400">finalement...</p>
        </div>
      </div>
      <!-- END OF CARD 1 -->
            <!-- CARD 2 -->
            <div class="bg-red-900 shadow-lg rounded p-10">
        <div class="group relative">
          <!-- <img class="w-full md:w-72 block rounded" src="../public/type/touch.jpg" alt="Album Cover" /> -->
          <audio id="audio2"  src="../10citations.mp3" hidden></audio>
          <div class="absolute rounded bg-white bg-opacity-0 group-hover:bg-opacity-60 w-full h-full top-0 flex items-center justify-evenly group-hover:opacity-100 transition-opacity duration-300">
            <button onclick="document.getElementById('audio2').play()" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/play-circle-fill.svg" alt="Play" class="w-8 h-8">
            </button>
            <button onclick="document.getElementById('audio2').pause()" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/pause-fill.svg" alt="Pause" class="w-8 h-8">
            </button>
            <button onclick="changeVolume('audio2', 0.1)" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/volume-up-fill.svg" alt="Volume Up" class="w-8 h-8">
            </button>
            <button onclick="changeVolume('audio2', -0.1)" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/volume-down-fill.svg" alt="Volume Down" class="w-8 h-8">
            </button>
          </div>
        </div>
        <div class="p-5">
          <h3 class="text-white text-lg">10 citations amoureuses</h3>
          <p class="text-gray-400">et notre avis</p>
        </div>
      </div>
      <!-- END OF CARD 2 -->
            <!-- CARD 3-->
            <div class="bg-red-900 shadow-lg rounded p-10">
        <div class="group relative">
          <!-- <img class="w-full md:w-72 block rounded" src="../public/type/moment.jpg" alt="Album Cover" /> -->
          <audio id="audio3"  src="../../lgbt.mp3" hidden></audio>
          <div class="absolute rounded bg-white bg-opacity-0 group-hover:bg-opacity-60 w-full h-full top-0 flex items-center justify-evenly group-hover:opacity-100 transition-opacity duration-300">
            <button onclick="document.getElementById('audio3').play()" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/play-circle-fill.svg" alt="Play" class="w-8 h-8">
            </button>
            <button onclick="document.getElementById('audio3').pause()" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/pause-fill.svg" alt="Pause" class="w-8 h-8">
            </button>
            <button onclick="changeVolume('audio3', 0.1)" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/volume-up-fill.svg" alt="Volume Up" class="w-8 h-8">
            </button>
            <button onclick="changeVolume('audio3', -0.1)" class="text-white hover:scale-110 transition transform hover:-translate-y-1">
              <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/icons/volume-down-fill.svg" alt="Volume Down" class="w-8 h-8">
            </button>
          </div>
        </div>
        <div class="p-5">
          <h3 class="text-white text-lg">C'est quoi "LGBTQIAA2S+" ?</h3>
          <p class="text-gray-400">avec des pincettes</p>
        </div>
      </div>
      <!-- END OF CARD 3 -->
    </section>
  </div>

</main>


</template>

<script>
  function changeVolume(audioId, change) {
    var audio = document.getElementById(audioId);
    audio.volume = Math.min(Math.max(0, audio.volume + change), 1); // Ensuring volume is between 0.0 and 1.0
  }
</script>
