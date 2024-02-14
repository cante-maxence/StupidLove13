<template>
  <div class="add-article text-white p-4 bg-gray-800 rounded-lg">
    <h2 class="text-xl font-bold mb-4">Ajouter un nouvel article</h2>
    <form @submit.prevent="submitArticle" class="space-y-4">
      <div class="border border-gray-200 rounded-lg bg-gray-50 dark:bg-gray-700 dark:border-gray-600">
        <div class="px-4 py-2 bg-white rounded-t-lg dark:bg-gray-800">
          <label for="title" class="sr-only">Titre</label>
          <input type="text" id="title" v-model="article.title" required class="w-full px-0 text-sm text-gray-900 bg-white border-0 dark:bg-gray-800 focus:ring-0 dark:text-white dark:placeholder-gray-400" placeholder="Titre de l'article">
        </div>
      </div>

      <div class="border border-gray-200 rounded-lg bg-gray-50 dark:bg-gray-700 dark:border-gray-600">
        <div class="px-4 pt-4 pb-20 bg-white rounded-t-lg dark:bg-gray-800">
          <label for="content" class="sr-only">Contenu</label>
          <textarea id="content" v-model="article.content" required rows="4" class="w-full px-0 text-sm text-gray-900 bg-white border-0 dark:bg-gray-800 focus:ring-0 dark:text-white dark:placeholder-gray-400" placeholder="Écrivez votre contenu ici..."></textarea>
        </div>
      </div>

      <div class="border border-gray-200 rounded-lg bg-gray-50 dark:bg-gray-700 dark:border-gray-600">
        <div class="px-4 py-2 bg-white rounded-t-lg dark:bg-gray-800">
          <label for="author" class="sr-only">Auteur</label>
          <input type="text" id="author" v-model="article.author" required class="w-full px-0 text-sm text-gray-900 bg-white border-0 dark:bg-gray-800 focus:ring-0 dark:text-white dark:placeholder-gray-400" placeholder="Nom de l'auteur">
        </div>
      </div>

      <div class="flex items-center justify-between">
        <button type="submit" class="inline-flex items-center py-2.5 px-4 text-xs font-medium text-center text-white bg-blue-700 rounded-lg focus:ring-4 focus:ring-blue-200 dark:focus:ring-blue-900 hover:bg-blue-800">
          Ajouter l'article
        </button>
      </div>
    </form>
  </div>
</template>
  
  <script>
  // Importation des fonctions nécessaires depuis Firebase
 import { db } from '../../src/firebase-config.js';
  import { collection, addDoc, serverTimestamp } from 'firebase/firestore';

  import { ref } from 'vue';

  

  export default {
    name: 'AddArticle',
    setup() {
      // Réactif state pour l'article à ajouter
      const article = ref({
        title: '',
        content: '',
        author: ''
      });
  
      // Fonction appelée lors de la soumission du formulaire
      async function submitArticle() {
        if (!article.value.title || !article.value.content || !article.value.author) {
          alert("Tous les champs sont requis !");
          return;
        }
        
        try {
          // Ajout de l'article dans la collection 'articles' de Firestore
          await addDoc(collection(db, "articles"), {
            title: article.value.title,
            content: article.value.content,
            author: article.value.author,
            createdAt: serverTimestamp()
          });
          alert("Article ajouté avec succès !");
          // Réinitialisation des champs après l'ajout
          article.value = { title: '', content: '', author: '' };
        } catch (error) {
          console.error("Erreur lors de l'ajout de l'article :", error);
          alert("Erreur lors de l'ajout de l'article.");
        }
      }
  
      return { article, submitArticle };
    }
  };
  </script>
  
  <!-- Style de base -->
  <style scoped>
  .add-article {
    max-width: 600px;
    margin: auto;
    padding: 20px;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  .form-group label {
    display: block;
    margin-bottom: 5px;
  }
  
  .form-group input[type="text"],
  .form-group textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  </style>
  