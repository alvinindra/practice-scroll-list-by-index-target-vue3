<script setup>
import ScrollList from './components/ScrollList.vue';
import InputIndex from './components/InputIndex.vue';

const index = ref(0)
const visibleItems = ref(5)

</script>

<template>
  <div class="flex flex-col gap-4">
    <ScrollList :visible-items="visibleItems" />
    <InputIndex :index="index" />
  </div>
</template>
