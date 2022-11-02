<script setup lang="ts">
interface Props {
  title: string;
  description: string;
  headingLevel: 1 | 2 | 3 | 4 | 5 | 6;
}
const props = defineProps<Props>();
</script>
<template>
  <div class="hero">
    <div class="hero-content text-center">
      <div class="max-w-md py-4">
        <h1 v-if="headingLevel == 1" class="text-6xl">{{ title }}</h1>
        <h1 v-if="headingLevel == 2" class="text-5xl">{{ title }}</h1>
        <h1 v-if="headingLevel == 3" class="text-4xl">{{ title }}</h1>
        <h1 v-if="headingLevel == 4" class="text-3xl">{{ title }}</h1>
        <h1 v-if="headingLevel == 5" class="text-2xl">{{ title }}</h1>
        <h1 v-if="headingLevel == 6" class="text-xl">{{ title }}</h1>
        <p class="py-6">{{ description }}</p>
      </div>
    </div>
  </div>
</template>
