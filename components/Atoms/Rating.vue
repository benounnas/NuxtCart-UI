<script setup lang="ts">
interface Props {
  disabled?: boolean;
  rating?:
    | 0
    | 0.5
    | "0.5"
    | 1
    | 2
    | 3
    | 4
    | 5
    | "1"
    | "2"
    | "3"
    | "4"
    | "5"
    | 1.5
    | 2.5
    | 3.5
    | 4.5
    | 5.5
    | "1.5"
    | "2.5"
    | "3.5"
    | "4.5"
    | "5.5";
  size?: "xs" | "sm" | "md" | "lg";
}

const sizes = ref({
  xs: "rating-xs",
  sm: "rating-sm",
  md: "rating-md",
  lg: "rating-lg",
});
const emit = defineEmits(["click"]);
const modulo = computed<number>(() => Number(props.rating) % 2);
const props = withDefaults(defineProps<Props>(), {
  disabled: false,
  rating: 0,
});
const selected = (selected: number) => {
  emit("click", selected);
};
const half2 = ref(true);
</script>
<template>
  <div class="rating rating-half" :class="sizes[size]">
    <template v-if="!rating" v-for="(rating, index) in 5">
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1"
        @click="selected(index + 0.5)"
      />
      <input
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2"
        @click="selected(index + 1)"
      />
    </template>

    <template v-else v-for="(rate, index) in Math.floor(Number(rating))">
      <input
        disabled
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-1 cursor-default"
      />
      <input
        disabled
        type="radio"
        name="rating-10"
        class="bg-green-500 mask mask-star-2 mask-half-2 cursor-default"
      />
    </template>
    <input
      disabled
      v-model="half2"
      v-if="rating && modulo !== 0"
      type="radio"
      name="rating-10"
      class="bg-green-500 mask mask-star-2 mask-half-1 cursor-default"
    />
  </div>
</template>
