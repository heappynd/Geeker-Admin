<template>
  <div>
    <Img v-model:image-url="imageUrl" :drag="true" :disabled="false" :file-size="1" :file-type="['image/webp']">
      <template #tip> 上传图片最大为 3M </template>
    </Img>

    <Imgs v-model:image-urls="imageUrls" :limit="3" :file-size="3">
      <template #tip> 上传图片最大为 3M </template>
    </Imgs>

    <SelectFilter :data="filterData"> </SelectFilter>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import Img from "@/components/Upload/Img.vue";
import Imgs from "@/components/Upload/Imgs.vue";
import SelectFilter from "@/components/SelectFilter/index.vue";

const imageUrl = ref("https://i.imgtg.com/2023/01/16/QRqMK.jpg");
const imageUrls = ref([]);

const filterData = [
  {
    title: "列表标题",
    key: "1", // 当前筛选项 key 值
    multiple: true, // 是否为多选
    options: [
      { label: "全部", value: "1" },
      { label: "选项2", value: "2" },
      { label: "选项3", value: "3" },
      { label: "选项4", value: "4" },
      { label: "选项5", value: "5" },
      { label: "选项6", value: "6" },
      { label: "选项7", value: "7" },
      { label: "选项8", value: "8" },
      { label: "选项9", value: "9" }
    ]
  }
];
</script>

<style scoped></style>
