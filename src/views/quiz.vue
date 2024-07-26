<template>
  <main>

    <quizHeader :questionPage="questionPage" :barPersen="barPersen"/>
    
    <quizContent :question="quis.questions[index]" @selectOption="onSelectOption"/>

    <button 
    @click="index++"
    :disabled="index === quis.questions.length - 1"
    >Next</button>
  </main>
</template>

<script setup>
import quizHeader from '@/components/quizHeader.vue';
import quizContent from '@/components/quizContent.vue';

import { ref, watch, computed } from 'vue'
import { useRoute } from 'vue-router';

import quizes from '../data/qizes.json';

const route = useRoute();
const id = parseInt(route.params.id);
const quis = quizes.find((q) => q.id === id);

const index = ref(0);
const numberCorrectQuest = ref(0);
// const questionPage = ref(`${index.value + 1} / ${quis.questions.length}`)

// melihat perubahan nilai
// watch(() => index.value, () => {
//   questionPage.value = `${index.value + 1} / ${quis.questions.length}`
// })

const questionPage = computed(() => {
  return `${index.value + 1} / ${quis.questions.length}`
});

const barPersen = computed(() => {
  return `${((index.value + 1) / quis.questions.length ) * 100}%`;
})

function onSelectOption(option) {
  if (option.correct) {
    numberCorrectQuest.value++;
  }
  index.value++;
} 

</script>

<style scoped>
main {
  width: 65%;
}
</style>