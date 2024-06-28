<template>
  <div>{{ exampleWord }}</div>
</template>

<script setup>
import {defineProps} from 'vue'

/* eslint-disable-next-line no-unused-vars */
const props = defineProps({
  exampleWord: {
    type: String,
  }
});

</script>

<style scoped>
 div {
   font-size: 24px;
 }
</style>