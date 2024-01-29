<template>
  <div class="person-item flex items-center mb-4">
    <img :src="person.avatar" :alt="`${person.name}'s avatar`" class="avatar" />
    <div class="flex-1">
      <h4 class="name text-lg font-bold mb-1">{{ person.name }}</h4>
      <p class="profession text-sm text-gray-600">{{ person.profession }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(['person']);
</script>

<style scoped>
.avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  margin-right: 10px;
}
</style>
