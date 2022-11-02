<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { Link } from "types/breadcrumbs";
import { RouterLink, useLink } from "vue-router";

interface Props {
  links: Link[];
}

const emit = defineEmits(["click"]);
const routerProps = reactive({
  //@ts-ignore
  ...RouterLink.props,
  inactiveClass: String,
});
const { route } = useLink(routerProps);

const props = withDefaults(defineProps<Props>(), {});
</script>
<template>
  <div>
    <ul class="flex flex-row gap-2">
      <template v-for="link in links" :key="link.text">
        <NuxtLink
          :to="link.link"
          class="text-slate-600 font-light hover:text-slate-800 hover:font-normal"
          :class="[
            route.fullPath == link.link ? 'text-slate-800 font-normal' : '',
          ]"
        >
          {{ link.text }}
        </NuxtLink>
        <li
          class="text-slate-600 font-light"
          v-if="links.indexOf(link) + 1 !== links.length"
        >
          |
        </li>
      </template>
    </ul>
  </div>
</template>
