<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  type: "primary" | "secondary" | "warning" | "danger" | "info" | "success";
  primaryColorClass?: string;
  secondaryColorClass?: string;
  textColor: string;
  activeColor?: string;
  otherCss?: string;
  iconLeft?: string;
  iconRight?: string;
}

const emit = defineEmits(["click"]);

const props = withDefaults(defineProps<Props>(), {
  textColor: "text-white",
});
const onClick = (): void => {
  emit("click");
};
</script>
<template>
  <button
    class="py-2 px-4 w-max flex items-center justify-center bg-zinc-200"
    :class="[
      type == 'primary'
        ? primaryColorClass ?? 'bg-indigo-800 hover:bg-indigo-700'
        : ' ',
      type == 'secondary'
        ? secondaryColorClass ??
          'bg-pink-700 hover:bg-pink-600 active:bg-pink-500'
        : '',
      type == 'warning' ? 'bg-amber-400 text-black' : '',
      type == 'danger' ? 'bg-red-700 text-white' : '',
      type == 'danger' ? 'bg-red-700 text-white' : '',
      type == 'info' ? 'bg-blue-700 text-white' : '',
      type == 'success' ? 'bg-green-700 text-white' : '',
      textColor,
      activeColor,
      otherCss,
    ]"
    @click="onClick"
  >
    <Icon v-if="iconLeft" :icon="iconLeft" class="mr-3" />
    <slot></slot>
    <Icon v-if="iconRight" :icon="iconRight" class="ml-3" />
  </button>
</template>
