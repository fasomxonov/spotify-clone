<script setup>
import { ref, toRefs } from "vue";
import { RouterLink } from "vue-router";
import uniqolor from "uniqolor";
let randColor = ref("");
randColor.value = uniqolor.random();

const props = defineProps({
  category: String,
  image: String,
});
const { category } = toRefs(props);
</script>

<template>
  <router-link to="library">
    <div
      class="contrast-[2] brightness-[0.87] rounded-xl aspect-square relative overflow-hidden"
      :style="`background-color: ${randColor.color};`"
      v-if="randColor.color"
    >
      <div class="text-white pt-3 pl-4 font-semibold text-[23px]">
        {{ category }}
      </div>
      <img class="absolute contrast-[0.55] -right-3.5 bottom-0 max-w-[100px] rotate-[20deg]" :src="img || '' " alt="img">
    </div>
  </router-link>
</template>
