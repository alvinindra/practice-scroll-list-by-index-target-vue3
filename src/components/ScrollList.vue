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
const rootHeight = computed(() => props.visibleItems * 72) // Person Item Height * Visible Items should show

const personIndex = computed(() => props.index)

const vFocus = {
  mounted: (el) => el.focus()
}

onMounted(() => itemRefs.value[12].scrollTo({
  top: 100,
  behavior: 'smooth'
}))

watchEffect(() => {
  if (personIndex.value) {
    console.log(personIndex.value)
    itemRefs.value[personIndex.value].scrollTo({
      top: itemRefs.value[personIndex.value].clientHeight,
      behavior: 'smooth'
    })
  }
}) 
</script>

<template>
  <div class="scroll-list gap-4" :style="{ 'max-height': rootHeight + 'px' }" v-focus>
    <div v-for="person in listData" :key="person.name" ref="itemRefs">
      <PersonItem :person="person" />
    </div>
  </div>
</template>

<style scoped>
.scroll-list {
  overflow-y: scroll;
  scroll-behavior: smooth;
  padding: 1rem;
  border: 1px solid gray;
  border-style: dashed;
}

.scroll-list:focus {
  border-style: normal;
  border-color: blue;
}
</style>
