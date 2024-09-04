<template>
  <div>
    <WangEditor v-model:value="content" mode="simple" hide-tool-bar disabled></WangEditor>
    {{ content }}
  </div>
</template>

<script lang="tsx" setup>
import WangEditor from "@/components/WangEditor/index.vue";
import { ref } from "vue";

const content = ref("<p>hello world</p>");
</script>
