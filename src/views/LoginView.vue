<template>
  <div class="grid md:grid-cols-2 items-center min-h-screen p-4 gap-4">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div
        class="max-w-md mx-auto my-10 bg-white/10 p-4 sm:p-6 lg:p-8 rounded-md shadow-lg transform transition duration-500 hover:scale-105">
        <div class="text-center">
          <h1 class="my-3 text-2xl sm:text-3xl font-semibold text-white">Inscription</h1>
          <p class="text-white text-xs sm:text-sm md:text-base">Inscrivez-vous pour avoir un compte</p>
        </div>

        <div class="m-7">
          <form method="POST" id="signup-form" class="animate-fade-in-up">

            <div class="mb-6">
              <label for="email" class="block mb-2 text-xs sm:text-sm md:text-base text-white">Email</label>
              <input type="email" v-model="email" placeholder="CentralPerk@mail.com" required
                class="w-full px-3 py-2 placeholder-gray-300 bg-white/20 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-300 focus:border-indigo-300" />
            </div>
            <div class="mb-6">
              <label for="password" class="block mb-2 text-xs sm:text-sm md:text-base text-white">Mot de passe</label>
              <input type="password" v-model="password" placeholder="Votre mot de passe" required
                class="w-full px-3 py-2 placeholder-gray-300 bg-white/20 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-300 focus:border-indigo-300" />
            </div>
            <div class="mb-6">
              <button @click.prevent="signUp" type="button"
                class="w-full px-3 py-2 sm:py-3 md:py-4 text-white bg-red-600 rounded-md hover:bg-red-700 focus:outline-none shadow-lg transform transition duration-500 hover:scale-105">
                S'inscrire
              </button>
              <p class="text-xs sm:text-sm md:text-base text-center text-white">{{ resultMessage }}</p>
            </div>
            <p class="text-xs sm:text-sm md:text-base text-center text-white" id="signup-result"></p>
          </form>
        </div>
      </div>
    </div>


    <div class="grid  items-center min-h-screen p-4">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div
          class="max-w-md mx-auto my-10 bg-white/10 p-4 sm:p-6 lg:p-8 rounded-md shadow-lg transform transition duration-500 hover:scale-105">
          <div class="text-center">
            <h1 class="my-3 text-3xl font-semibold text-white">
              Connexion
            </h1>
            <p class="text-white text-sm">
              Connectez-vous pour accéder à votre compte
            </p>
          </div>

          <div class="m-7">
            <form method="POST" id="login-form" class="animate-fade-in-up">

              <div class="mb-6">
                <label for="email" class="block mb-2 text-sm text-white">Email</label>
                <input type="email" v-model="email" name="email" id="email" placeholder="CentralPerk@mail.com" required
                  class="w-full px-3 py-2 placeholder-gray-300 bg-white/20 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-300 focus:border-indigo-300" />
              </div>
              <div class="mb-6">
                <label for="password" class="block mb-2 text-sm text-white">Mot de passe</label>
                <input type="password" v-model="password" name="password" id="password" placeholder="Mot de passe"
                  required
                  class="w-full px-3 py-2 placeholder-gray-300 bg-white/20 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-300 focus:border-indigo-300" />
              </div>
              <div class="mb-6">
                <button @click.prevent="login" type="button"
                  class="w-full px-3 py-4 text-white bg-red-600 mb-4 rounded-md hover:bg-red-700 focus:outline-none shadow-lg transform transition duration-500 hover:scale-105">
                  Se connecter
                </button>
                <hr>
                <button type="button" @click="logout"
                  class="w-full px-3 mt-4 py-4 text-white bg-red-600 rounded-md hover:bg-red-700 focus:outline-none shadow-lg transform transition duration-500 hover:scale-105">
                  Déconnexion
                </button>
                <div v-if="email === 'pixelmax03@gmail.com'">
                  <button @click="goToAddArticle"
                  class="w-full px-3 mt-4 py-4 text-white bg-red-600 rounded-md hover:bg-red-700 focus:outline-none shadow-lg transform transition duration-500 hover:scale-105">
                    Ajouter un Article
                  </button>
                </div>
                <p class="text-base text-center text-white">{{ resultMessage }}</p>

              </div>
              <p class="text-base text-center text-white" id="login-result"></p>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script>
import { ref, onMounted } from 'vue';
import { auth } from '../firebase-config';
import {
  onAuthStateChanged,
  signOut,
  createUserWithEmailAndPassword,
  signInWithEmailAndPassword
} from "firebase/auth";
import { useRouter } from 'vue-router';

export default {
  name: 'AuthenticationComponent',
  setup() {
    const email = ref('');
    const password = ref('');
    const resultMessage = ref('');
    const user = ref(null); // Réactif pour stocker l'utilisateur actuel
    const router = useRouter();

    // Surveiller les changements d'état d'authentification
    onMounted(() => {
      onAuthStateChanged(auth, (currentUser) => {
        user.value = currentUser; // Met à jour l'utilisateur actuel
      });
    });

    // Fonction pour l'inscription de l'utilisateur
    const signUp = async () => {
      try {
        const userCredential = await createUserWithEmailAndPassword(auth, email.value, password.value);
        resultMessage.value = 'Inscription réussie';
        console.log(userCredential);
      } catch (error) {
        resultMessage.value = error.message;
        console.error(error);
      }
    };

    // Fonction pour la connexion de l'utilisateur
    const login = async () => {
      try {
        const userCredential = await signInWithEmailAndPassword(auth, email.value, password.value);
        resultMessage.value = 'Connexion réussie';
        console.log(userCredential);
      } catch (error) {
        resultMessage.value = error.message;
        console.error(error);
      }
    };

    // Fonction pour la déconnexion de l'utilisateur
    const logout = async () => {
      try {
        await signOut(auth);
        resultMessage.value = 'Déconnexion réussie';
        console.log("Déconnexion réussie");
      } catch (error) {
        console.error("Erreur de déconnexion: ", error);
        resultMessage.value = "Erreur lors de la déconnexion: " + error.message;
      }
    };

    // Fonction pour naviguer vers la page d'ajout d'article
    const goToAddArticle = () => {
      router.push('/AddArticle'); // Utilisez le chemin correct pour votre page d'ajout d'article
    };

    return { email, password, resultMessage, signUp, login, logout, user, goToAddArticle };
  }
};
</script>
