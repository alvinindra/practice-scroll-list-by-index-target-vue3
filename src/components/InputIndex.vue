<template>
  <form @submit.prevent="submitIndex" class="input-index">
    <input
      id="indexInput"
      type="number"
      v-model="indexValue"
      placeholder="Input the Index"
      class="mr-2 border rounded px-2 py-1"
      required
    />
    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">
      Enter
    </button>
  </form>
</template>

<script setup>
let indexValue = '';

const submitIndex = () => {
  // You can perform actions with the entered index, for example, emit an event
  // or call a method in the parent component.
  console.log('Entered Index:', indexValue);
};
</script>

<style scoped>
.input-index {
  display: flex;
  align-items: center;
  margin: 24px auto;
}
</style>
