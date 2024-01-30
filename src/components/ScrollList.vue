<script setup>
import { ref, onMounted, computed, watchEffect } from 'vue';
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
const scrollContainer = ref(null);
const rootHeight = computed(() => props.visibleItems * 72) // Person Item Height * Visible Items should show

const personIndex = computed(() => props.index)

const vFocus = {
  mounted: (el) => el.focus()
}

watchEffect(() => {
  if (personIndex.value) {
    const targetItem = itemRefs.value[personIndex.value];
    const position = targetItem.clientHeight * personIndex.value; // Calculate the top offset position of the item
    console.log(personIndex.value, targetItem.clientHeight * personIndex.value)
    scrollContainer.value.scrollTo({
      top: personIndex.value === 0 ? 0 : position,
      behavior: 'smooth'
    });
  } else if (personIndex.value === 0) {
    scrollContainer.value?.scrollTo({
      top: 0,
      behavior: 'smooth'
    });
  }
}) 
</script>

<template>
  <div ref="scrollContainer" class="scroll-list gap-4" :style="{ 'max-height': rootHeight + 'px' }" v-focus>
    <div v-for="person in listData" :key="person.name" ref="itemRefs">
      <PersonItem :person="person" />
    </div>
  </div>
</template>

<style scoped>
.scroll-list {
  overflow-y: scroll;
  scroll-behavior: smooth;
  border: 1px solid gray;
  border-style: dashed;
}

.scroll-list:focus {
  border-style: normal;
  border-color: blue;
}
</style>
