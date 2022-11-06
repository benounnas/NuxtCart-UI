<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  icon: string;
  size?: "xss" | "xs" | "sm" | "md" | "lg" | "xl";
  customCss?: string;
}

const emit = defineEmits(["click"]);

const props = withDefaults(defineProps<Props>(), {});
const sizeSelected = ref({
  xss: 10,
  xs: 20,
  sm: 30,
  md: 40,
  lg: 50,
  xl: 60,
});
</script>
<template>
  <Icon
    :icon="icon"
    :width="sizeSelected[size]"
    :height="sizeSelected[size]"
    :class="customCss"
  />
</template>
