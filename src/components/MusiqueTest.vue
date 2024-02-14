<template>
    <div class=" flex items-center justify-center p-4">
      <div class="text-white max-w-md mx-auto p-5 bg-black rounded-lg shadow-xl">
        <p class="text-xl md:text-2xl font-bold mb-6">Quelle chanson d'amour vous décrit ?</p>
        <div v-if="currentQuestion < questions.length" class="space-y-4">
          <p class="text-lg font-semibold">{{ questions[currentQuestion].text }}</p>
          <div class="space-y-2">
            <button v-for="(answer, index) in questions[currentQuestion].answers" :key="index"
                    @click="selectAnswer(answer.score)"
                    class="w-full px-4 py-2 bg-white text-black rounded-md hover:bg-red-200 transition">
              {{ answer.text }}
            </button>
          </div>
        </div>
        <div v-else class="text-center p-6 bg-gray-800/50 rounded-lg shadow-lg">
          <p class="text-xl md:text-2xl font-bold text-red-300 mb-6">Votre chanson d'amour est :</p>
          <p class="text-2xl md:text-3xl font-semibold mb-4">{{ interpretScore() }}</p>
          <button @click="restartQuiz" class="px-6 py-3 bg-red-500 text-white rounded-full hover:bg-red-600 font-semibold transition duration-300 ease-in-out shadow-md">
            Refaire le quiz
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        currentQuestion: 0,
        score: 0,
        questions: [
          {
            text: "Comment décririez-vous votre idéal romantique ?",
            answers: [
              { text: "Une aventure passionnée et tumultueuse", score: 2 },
              { text: "Une relation stable et durable", score: 1 },
              { text: "Je suis encore à la recherche de mon idéal", score: 0 },
            ]
          },
          {
          text: "Quel est votre état d'esprit actuel en amour ?",
          answers: [
            { text: "Optimiste et plein d'espoir", score: 3 },
            { text: "Réfléchi et sérieux", score: 2 },
            { text: "Incertain et en quête de réponses", score: 1 },
            { text: "Indifférent ou sceptique", score: 0 },
          ]
        },
        {
          text: "Quelle qualité valorisez-vous le plus dans une relation ?",
          answers: [
            { text: "La communication et l'ouverture", score: 3 },
            { text: "La loyauté et la confiance", score: 2 },
            { text: "La passion et l'intensité", score: 1 },
            { text: "L'indépendance et la liberté", score: 0 },
          ]
        },
        {
          text: "Quel type de rendez-vous préférez-vous ?",
          answers: [
            { text: "Un concert ou un spectacle vivant", score: 1 },
            { text: "Un dîner romantique chez soi", score: 2 },
            { text: "Une aventure en plein air", score: 3 },
            { text: "Un café pour une discussion intime", score: 0 },
          ]
        },
        {
          text: "Quelle chanson pourrait être votre hymne d'amour personnel ?",
          answers: [
            { text: "\"Perfect\" - Ed Sheeran", score: 2 },
            { text: "\"Can't Help Falling in Love\" - Elvis Presley", score: 3 },
            { text: "\"Love on the Brain\" - Rihanna", score: 1 },
            { text: "\"Somebody Else\" - The 1975", score: 0 },
          ]
        },
        {
          text: "Comment réagissez-vous à une déception amoureuse ?",
          answers: [
            { text: "Je prends du temps pour moi et réfléchis", score: 2 },
            { text: "Je me tourne vers mes amis pour du soutien", score: 3 },
            { text: "Je plonge dans le travail ou les hobbies pour oublier", score: 1 },
            { text: "Je passe rapidement à autre chose", score: 0 },
          ]
        },
          {
          text: "Comment décririez-vous votre vie amoureuse actuellement ?",
          answers: [
            { text: "Passionnée et intense", score: 2 },
            { text: "Stable et confortable", score: 1 },
            { text: "Solitaire et en recherche", score: 0 },
          ]
        },
        {
          text: "Quel type de musique préférez-vous pour une soirée romantique ?",
          answers: [
            { text: "Un slow classique", score: 2 },
            { text: "Une ballade pop moderne", score: 1 },
            { text: "Quelque chose de dynamique et joyeux", score: 0 },
          ]
        },
          {
            text: "Quel décor préférez-vous pour un rendez-vous amoureux ?",
            answers: [
              { text: "Un dîner aux chandelles dans un restaurant chic", score: 2 },
              { text: "Une balade romantique sur la plage au coucher du soleil", score: 1 },
              { text: "Un concert ou un événement culturel animé", score: 0 },
            ]
          },
          {
            text: "Quel trait de caractère appréciez-vous le plus chez votre partenaire ?",
            answers: [
              { text: "La passion et l'intensité", score: 2 },
              { text: "La fidélité et la stabilité", score: 1 },
              { text: "L'indépendance et le sens de l'aventure", score: 0 },
            ]
          },
          {
            text: "Quelle est votre réaction après une dispute amoureuse ?",
            answers: [
              { text: "Je cherche à résoudre le conflit avec passion", score: 2 },
              { text: "Je prends du recul et réfléchis calmement à une solution", score: 1 },
              { text: "Je m'éloigne pour donner de l'espace à chacun", score: 0 },
            ]
          },
          {
            text: "Comment imaginez-vous la Saint-Valentin idéale ?",
            answers: [
              { text: "Un geste grandiose et romantique", score: 2 },
              { text: "Un moment simple mais significatif", score: 1 },
              { text: "Je ne célèbre pas spécialement la Saint-Valentin", score: 0 },
            ]
          },
          // Ajouter d'autres questions pour approfondir l'analyse
        ],
      };
    },
    methods: {
      selectAnswer(score) {
        this.score += score;
        this.currentQuestion++;
      },
      interpretScore() {
        // Définissez les seuils de score pour chaque chanson
        // Les seuils et les chansons doivent être ajustés en fonction du nombre de questions et des scores possibles
        if (this.score <= 5) {
          return "\"Love Yourself\" - Justin Bieber";
        } else if (this.score <= 15) {
          return "\"Thinking Out Loud\" - Ed Sheeran";
        } else if (this.score <= 23) {
          return "\"At Last\" - Etta James";
        } else {
          return "\"All of Me\" - John Legend";
        }
      },
      restartQuiz() {
        this.currentQuestion = 0;
        this.score = 0;
      },
    }
  }
  </script>
  