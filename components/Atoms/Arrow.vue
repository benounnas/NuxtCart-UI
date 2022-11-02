<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  disabled?: boolean;
  bgColor?: string;
  textColor?: string;
  activeColor?: string;
}

const emit = defineEmits(["click"]);

const props = withDefaults(defineProps<Props>(), {
  disabled: false,
});
</script>
<template>
  <button
    class="w-[2.75rem] h-[2.75rem] py-0 px-[0.0625rem] flex items-center justify-center hover:shadow-lg bg-zinc-200 transition-colors delay-5 ease-out active:shadow-none"
    :class="[
      bgColor ?? 'hover:bg-zinc-900 ',
      textColor ?? 'hover:text-white',
      activeColor ?? 'active:bg-zinc-700 ',
    ]"
  >
    <Icon icon="fa6-solid:arrow-left-long" />
  </button>
</template>
