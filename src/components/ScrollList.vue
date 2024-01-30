<script setup>
import { ref, onMounted, computed, watch } from 'vue';
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

onMounted(() =>
  itemRefs[personIndex.value]?.value.scrollTo({
    top: itemRefs[personIndex.value].value.clientHeight,
    behavior: 'smooth'
  })
);

function scrollToPerson () {
  console.log(personIndex.value, itemRefs.value[1].clientHeight)
  itemRefs[personIndex.value]?.value.scrollTo({
    top: personIndex.value * itemRefs[personIndex.value].value.clientHeight,
    behavior: 'smooth'
  })
}

watch(() => personIndex.value, scrollToPerson) 
</script>

<template>
  <div class="scroll-list gap-4" :style="{ 'max-height': rootHeight + 'px' }" v-focus>
    <PersonItem v-for="person in listData" :key="person.name" :person="person" ref="itemRefs" />
  </div>
</template>

<style scoped>
.scroll-list {
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
