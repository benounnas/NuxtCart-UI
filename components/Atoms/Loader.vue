<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  addtionalCss?: string;
}
const props = defineProps<Props>();
</script>

<template>
  <div :class="[addtionalCss]">
    <Icon icon="line-md:loading-twotone-loop" class="w-full h-full" />
  </div>
</template>
