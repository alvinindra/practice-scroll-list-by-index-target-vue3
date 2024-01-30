<script setup>
import { ref, onMounted } from 'vue';
import PersonItem from './PersonItem.vue';
import { listData } from '../assets/dataSource';

const props = defineProps({
  visibleItems: {
    type: Number,
    default: 5,
  },
  index: {
    type: Number,
    default: 0,
  },
})

const itemRefs = ref([]);

const vFocus = {
  mounted: (el) => el.focus(),
};

onMounted(() => [console.log(itemRefs.value[0])]);
</script>

<template>
  <div class="scroll-list gap-4">
    <PersonItem
      v-for="person in listData"
      :key="person.name"
      :person="person"
      ref="itemRefs"
    />
  </div>
</template>

<style scoped>
.scroll-list {
  max-height: 350px; /* Adjust the maximum height as needed */
  overflow-y: auto;
  padding: 1rem;
  border: 1px solid gray;
  border-style: dashed;
}

.scroll-list:focus {
  border-style: normal;
  border-color: blue;
}
</style>
