<template>
  <form @submit.prevent="submitIndex" class="input-index">
    <input v-model="indexValue" id="indexInput" name="indexValue" type="number" placeholder="Input the Index"
      class="mr-2 border rounded px-2 py-1" required />
    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">
      Enter
    </button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps(['index']);
const emit = defineEmits(['update:index']);
const indexValue = ref(props.index);

const submitIndex = () => {
  emit('update:index', Number(indexValue.value));
};
</script>

<style scoped>
.input-index {
  display: flex;
  align-items: center;
  margin: 24px auto;
}
</style>
