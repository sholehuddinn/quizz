<template>
  <header>
      <h4>Question {{ questionPage }}</h4>
      <div class="bar">
        <p class="bar-progres" :style="{ width: barPersen }"></p>
      </div>
    </header>
</template>

<script setup>
import { defineProps } from 'vue';
const { questionPage, barPersen } = defineProps([
  'questionPage',
  'barPersen'
  ])

</script>

<style scoped>
  header {
    margin-top: 20px;
  }
  header h4 {
    font-size: 30px;
  }
  .bar {
    width: 100%;
    height: 50px;
    border: 3px solid greenyellow;
    
  }
  .bar-progres {
    height: 100%;
    width: 0;
    background-color: green;
    margin: 0%;
  }
</style>