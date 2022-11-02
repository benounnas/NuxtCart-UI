<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  label: string;
  type: "primary" | "secondary" | "warning" | "danger" | "info" | "success";
  primaryColorClass?: string;
  secondaryColorClass?: string;
  textColor: string;
}

const emit = defineEmits(["click"]);

const props = withDefaults(defineProps<Props>(), {
  textColor: "text-white",
});
</script>
<template>
  <div
    class="py-2 px-4 w-max flex items-center justify-center bg-zinc-200"
    :class="[
      type == 'primary' ? primaryColorClass ?? 'bg-indigo-800 ' : ' ',
      type == 'secondary' ? secondaryColorClass ?? 'bg-pink-700' : '',
      textColor,
      type == 'warning' ? 'bg-amber-400 text-black' : '',
      type == 'danger' ? 'bg-red-700 text-white' : '',
      type == 'danger' ? 'bg-red-700 text-white' : '',
      type == 'info' ? 'bg-blue-700 text-white' : '',
      type == 'success' ? 'bg-green-700 text-white' : '',
    ]"
  >
    {{ label }}
  </div>
</template>
