<script setup>
import { ref, watch } from 'vue';
import srcQuiz from '../data/qizes';

import QuizCard from '../components/quizCard.vue';

const quizes = ref(srcQuiz);
const search = ref('');

watch(search, () => {
	quizes.value = srcQuiz.filter((quiz) => {
		return quiz.title.toLowerCase().includes(search.value.toLowerCase());
	});
});

</script>

<template>
  <main>
    <header>
      <h1 class="title">quizzVue</h1>
      <input type="text" id="search-input" placeholder="Search..."
        v-model.trim="search"
      >
    </header>
    <section id="quiz-container">
      <QuizCard v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" v-bind="quiz"/>
    </section>
  </main>
</template>

<style scoped>
  main {
    max-width: 900px;
    margin: 0 auto;
    padding: 2rem;
    background-color: #f5f5f5;
  }
  header {
    display: flex;
    align-items: center;
    padding: 1rem;
  }
  .title {
    font-size: 2rem;
    margin-right: 1rem;
  }
  #search-input {
    padding: 0.5rem;
    font-size: 1rem;
    border: none;
    margin-left: 1rem;
    border-radius: 5px;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
  }
  #quiz-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 20px;
  }
  
</style>
  