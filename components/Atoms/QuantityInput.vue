<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  modelValue?: string | number | any;
  errors?: string[];
  label?: string;
  placeholder?: string;
  id?: string;

  disabled?: boolean;
  required?: boolean;
  type?: "text" | "password";
}

const emit = defineEmits(["update:modelValue", "clearErrors"]);

const onUpdate = (e: any) => {
  emit("update:modelValue", e.target.value);
};

const props = withDefaults(defineProps<Props>(), {
  modelValue: 0,
});
const clearErrors = () => {
  emit("clearErrors");
};
const increment = (e: any) => {
  emit("update:modelValue", props.modelValue + 1);
};
const decrement = (e: any) => {
  if (props.modelValue > 0) {
    emit("update:modelValue", props.modelValue - 1);
  }
};
</script>

<template>
  <div class="">
    <label for="on-error-email" class="text-gray-700">
      {{ label }}
      <span v-if="required" class="text-red-500 required-dot"> * </span>
    </label>
    <div
      class="flex relative border-transparent mt-1 rounded-r-lg"
      :class="[!!errors && errors.length > 0 ? 'ring-red-500 ring-2' : '']"
    >
      <button
        :disabled="modelValue <= 0"
        @click="decrement"
        class="inline-flex items-center px-3 border-t bg-white border-l border-b border-r border-gray-400 text-black shadow-sm text-sm"
      >
        <Icon :icon="'akar-icons:minus'" />
      </button>
      <input
        :value="modelValue"
        @input="onUpdate($event)"
        @focus="clearErrors"
        class="w-20 appearance-none border py-2 px-4 bg-white text-black placeholder-gray-400 shadow-sm text-base text-center"
      />

      <button
        @click="increment"
        class="inline-flex items-center px-3 border-t bg-white border-l border-b border-r border-gray-300 text-black shadow-sm text-sm"
      >
        <Icon :icon="'ant-design:plus-outlined'" />
      </button>
      <p class="absolute text-sm text-red-500 -bottom-6">
        <template v-for="e in errors" :key="e">{{ e }} <br /></template>
      </p>
    </div>
  </div>
</template>
