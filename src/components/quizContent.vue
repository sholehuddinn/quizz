<template>
  <main>

    <section id="question-container">
      <h1 class="question-title">{{ question.text }}</h1>
    </section>
    
    <section id="options-container">
      <div 
      class="option" 
      v-for="option in question.answers" 
      :key="option.id"
      @click="emitSelectedOption(option)"
      >
        <p class="option-label">{{ option.label }}</p>
        <div class="option-val">{{ option.text }}</div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { defineProps } from 'vue';
import { defineEmits } from 'vue';

const { question } =  defineProps(['question']);
const emit = defineEmits(['selectOption']);


function emitSelectedOption() {
  emit('selectOption', option);
}

</script>

<style scoped>
  #question-container {
    margin-top: 40px;
  }
  .question-title {
    font-size: 30px;
    font-weight: bold;
    margin-bottom: 20px;
  }
  .option {
    display: flex;
    align-items: center;
    cursor: pointer;
    margin-bottom: 0%;
  }
  .option-label {
    font-size: 20px;
    font-weight: bold;
    width: 50px;
    height: 50px;
    background-color :aquamarine;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .option-val {
    font-size: 20px;
    font-weight: bold;
    padding: 0 20px;
    background-color: cadetblue;
    width: 100%;
    height: 50px;
    display: flex;
    align-items: center;
  }

</style>