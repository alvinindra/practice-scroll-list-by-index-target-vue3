<template>
  <form @submit.prevent="submitIndex" class="input-index">
    <input id="indexInput" name="indexValue" type="number" :value="props.index" placeholder="Input the Index"
      class="mr-2 border rounded px-2 py-1" required />
    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">
      Enter
    </button>
  </form>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'
const props = defineProps(['index'])
const emit = defineEmits(['update:index'])
const submitIndex = (event) => {
  emit('update:index', Number(event.target.indexValue.value))
};
</script>

<style scoped>
.input-index {
  display: flex;
  align-items: center;
  margin: 24px auto;
}
</style>
