<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  modelValue?: string | Number | any;
  errors?: string[];
  label?: string;
  placeholder?: string;
  id?: string;
  icon?: string;
  disabled?: boolean;
  required?: boolean;
  type?: "text" | "password";
}

const emit = defineEmits(["update:modelValue", "clearErrors"]);

const onUpdate = (e: any) => {
  emit("update:modelValue", e.target.value);
};

const props = defineProps<Props>();
const clearErrors = () => {
  emit("clearErrors");
};
</script>

<template>
  <div>
    <label for="on-error-email" class="text-gray-700">
      {{ label }}
      <span v-if="required" class="text-red-500 required-dot"> * </span>
    </label>
    <div
      class="flex relative border-transparent mt-1 rounded-l-lg rounded-r-lg"
      :class="[!!errors && errors.length > 0 ? 'ring-red-500 ring-2' : '']"
    >
      <span
        v-if="icon"
        class="inline-flex items-center px-3 border-t bg-white border-l border-b border-gray-300 text-gray-500 shadow-sm text-sm rounded-l-lg"
      >
        <Icon :icon="icon" />
      </span>
      <input
        :value="modelValue"
        @input="onUpdate($event)"
        @focus="clearErrors"
        class="rounded-r-lg flex-1 appearance-none border w-full py-2 px-4 bg-white text-gray-700 placeholder-gray-400 shadow-sm text-base focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent"
        :class="[!icon ? 'rounded-l-lg' : '']"
      />

      <Icon
        v-if="!!errors && errors.length > 0"
        icon="ant-design:warning-filled"
        class="absolute text-red-500 right-2 bottom-3"
      />

      <p class="absolute text-sm text-red-500 -bottom-6">
        <template v-for="e in errors" :key="e">{{ e }} <br /></template>
      </p>
    </div>
  </div>
</template>
