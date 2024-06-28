<script setup>
import {ref} from 'vue';
import WordInput from '@/views/input/WordInput.vue';
import WordExample from '@/views/input/WordExample.vue';

const words = ref(['test', 'example', 'learning', 'vue', 'javascript']);
const currentWord = ref(0);
const exampleWord = ref(words.value[currentWord.value]);
const inputValue = ref('');

const handleInputCorrect = () => {
  currentWord.value = (currentWord.value + 1) % words.value.length;
  exampleWord.value = words.value[currentWord.value];
};

</script>

<template>
  <WordExample :exampleWord="exampleWord"/>
  <WordInput v-model:inputValue="inputValue" :correctWord="exampleWord" @input-correct="handleInputCorrect"/>
</template>

<style scoped>
button {
  font-size: 24px;
  margin-top: 20px;
}
</style>