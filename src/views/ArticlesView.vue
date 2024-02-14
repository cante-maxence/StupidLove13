



<template>
<div class="flex justify-center mb-8">
  <input type="text" v-model="searchQuery" placeholder="Rechercher des articles..." 
    class="form-input px-4 py-2 w-full max-w-xl border rounded shadow-sm focus:outline-none focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50">
</div>




<div class="articles-container flex flex-wrap justify-center mt-20 gap-x-8 gap-y-12">
  <div v-for="article in filteredArticles" :key="article.id" 
    class="w-full sm:max-w-sm md:w-1/2 lg:w-1/3 px-6 py-12 text-center border rounded-lg transition duration-500 ease-in-out transform hover:-translate-y-1 hover:scale-110">
  
      <a :href="'/Articles/' + article.id" 
        class="inline-block text-white mb-4 text-2xl font-extrabold leading-7 transition-colors duration-300 hover:text-deep-purple-accent-100" 
        aria-label="Read article" :title="article.title">
        {{ article.title }}
      </a>
      
      <p class="text-zinc-100 mb-4">
        Auteur: {{ article.author }}<br> 
        Créé le: {{ new Date(article.createdAt.seconds * 1000).toLocaleDateString() }}
      </p>
      <a :href="'/Articles/' + article.id" 
        class="px-6 py-2 transition ease-in duration-200 text-white uppercase rounded-full hover:bg-red-800 hover:text-white border-2 border-gray-200 focus:outline-none">
        Lire l'article
      </a>
    </div>
  </div>
</template>

    
    








<script setup>
import { onMounted, ref, computed } from 'vue';
import { db } from '../../src/firebase-config';
import { collection, getDocs, query, orderBy } from 'firebase/firestore';

const searchQuery = ref('');
const articles = ref([]);

onMounted(async () => {
  const q = query(collection(db, "articles"), orderBy("createdAt", "desc"));
  const querySnapshot = await getDocs(q);
  articles.value = querySnapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
});

const filteredArticles = computed(() => {
  if (!searchQuery.value.trim()) return articles.value;
  return articles.value.filter(article =>
    article.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
    article.author.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});

</script>

<style scoped>
html {
  --s: 50px;
  --c: #191b22;
  --_s: calc(2*var(--s)) calc(2*var(--s));
  --_g: 35.36% 35.36% at;
  --_c: #0000 66%, #600000 68% 70%, #0000 72%;
  background:
    radial-gradient(var(--_g) 100% 25%, var(--_c)) var(--s) var(--s)/var(--_s),
    radial-gradient(var(--_g) 0 75%, var(--_c)) var(--s) var(--s)/var(--_s),
    radial-gradient(var(--_g) 100% 25%, var(--_c)) 0 0/var(--_s),
    radial-gradient(var(--_g) 0 75%, var(--_c)) 0 0/var(--_s),
    repeating-conic-gradient(var(--c) 0 25%, #0000 0 50%) 0 0/var(--_s),
    radial-gradient(var(--_c)) 0 calc(var(--s)/2)/var(--s) var(--s) var(--c);
  background-attachment: fixed;
}



.search-container {
  margin-bottom: 20px; /* Ajustez selon vos besoins */
  text-align: center;
}

.search-input {
  padding: 8px 12px;
  width: 100%;
  max-width: 400px; /* Ajustez selon la largeur désirée */
  border: 1px solid #ccc;
  border-radius: 8px; /* Bordures arrondies */
}
</style>

