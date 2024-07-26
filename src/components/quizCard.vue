<template>
  <div class="card" @click="goToQuizz()"> 
    <img :src="quiz.img" :alt="quiz.title">
    <div class="card-body">
      <h2>{{ quiz.title }}</h2>
      <p>{{ quiz.questions.length }} question</p>
    </div>
  </div>
</template>

<script setup>
const { quiz } = defineProps(['quiz'])



import { useRouter } from 'vue-router'

const router = useRouter()

function goToQuizz() {
  router.push({ name: 'quiz', params: { id: quiz.id } })
}
</script>

<style scoped>
  .card {
    width: 270px;
    margin-right: 30px;
    margin-bottom: 30px;
    border-radius: 5px;
    overflow: hidden;
    box-shadow: 0 0px 5px rgba(0, 0, 0, 0.1);   
    transition: transform 0.3s ease;
  }
  .card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    margin: 0;
  }
  .card-body {
    padding: 0 15px;
  }
  .card:hover {
    transform: scale(1.02);
  }
  .card h2 {
    margin-bottom: 0;
    font-weight: bold;
  }
</style>