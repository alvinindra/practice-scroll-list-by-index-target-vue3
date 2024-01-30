<script setup>
import { ref } from 'vue'
import ScrollList from './components/ScrollList.vue';
import InputIndex from './components/InputIndex.vue';

const index = ref(0)
const visibleItems = ref(5)
</script>

<template>
  <div class="flex flex-col gap-4">
    <ScrollList :visible-items="visibleItems" :index="index" />
    <InputIndex :index="index" />
  </div>
</template>
