<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  currentPrice: string | number;
  oldPrice: string | number;
  oldPriceCustomCss?: string;
  currentPriceCustomCss?: string;
}
const props = defineProps<Props>();
</script>

<template>
  <div>
    <span
      class="mr-1 line-through"
      :class="[oldPriceCustomCss ? oldPriceCustomCss : 'text-red-700 text-xs']"
    >
      {{ oldPrice + "$" }}
    </span>
    <span>
      {{ currentPrice + "$" }}
    </span>
  </div>
</template>
