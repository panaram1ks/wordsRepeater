<template>
  <input v-model="inputValue" @keyup.enter="checkInput" :class="blackRedGreen">
</template>

<script setup>
import {ref, defineProps, defineEmits} from 'vue';

const inputValue = ref('');
const blackRedGreen = ref('');

/* eslint-disable-next-line no-unused-vars */
const props = defineProps({
  correctWord: String,
});

const emit = defineEmits([
    'input-correct'
  // ,'update:inputValue'
]);

const checkInput = () => {
  if (props.correctWord === inputValue.value) {
    blackRedGreen.value = 'correct'
    setTimeout(() => {
      inputValue.value = '';
      blackRedGreen.value = '';
      // emit('update:inputValue', inputValue.value);
      emit('input-correct');
    }, 2000);
  } else {
    blackRedGreen.value = 'incorrect'
  }
};
</script>

<style scoped>
input {
  width: 10%;
  font-size: 24px;
  padding: 5px;
}

.correct {
  color: green;
}

.incorrect {
  color: red;
}
</style>