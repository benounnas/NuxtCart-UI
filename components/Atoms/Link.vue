<script setup lang="ts">
interface Props {
  link: string;
  text: string;
  hoverClass?: string;
  addtionalCss?: string;
}
const props = defineProps<Props>();
</script>
<template>
  <a
    :href="link"
    class="hover:underline-offset-3 hover:underline"
    :class="[hoverClass ? hoverClass : 'hover:text-indigo-800', addtionalCss]"
    target="_blank"
    >{{ text }}</a
  >
</template>
