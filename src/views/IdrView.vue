<template>




<div class="px-4 mx-auto sm:max-w-xl md:max-w-full text-white lg:max-w-screen-xl md:px-24 lg:px-8 lg:py-10">
  <div class="max-w-xl  md:mx-auto sm:text-center lg:max-w-2xl ">
    <h2 class="max-w-lg  font-sans text-3xl font-bold leading-none tracking-tight sm:text-4xl md:mx-auto">
      Plusieurs Tests pour savoir quelle type de personnes vous-êtes ?
    </h2>
    <h3 class="text-base text-gray-100 md:text-lg">
      Des tests à faire dans les deux sens : Pour vous et pour lui.
    </h3>
    <!-- Container for tests -->
    <div id="app" class="flex flex-wrap justify-center gap-4 ">
      <!-- Each test component wrapped in a div for individual styling -->
      <div class="w-full ">
        <PersonalityTest />
      </div>
      <div class="w-full ">
        <RoucoulTest />
      </div>
      <div class="w-full ">
        <MusiqueTest />
      </div>
    </div>
  </div>
</div>






  </template>
  
  <script>
import PersonalityTest from '../components/PersonalityTest.vue';
import RoucoulTest from '../components/RoucoulTest.vue';
import MusiqueTest from '../components/MusiqueTest.vue';

export default {
  name: 'App',
  components: {
    PersonalityTest,
    RoucoulTest, // Ajoutez cette ligne pour enregistrer RoucoulTest comme composant
    MusiqueTest
  }
};

  </script>
  