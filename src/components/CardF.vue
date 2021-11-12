<template>
  <div class="col-12 col-md-4 col-lg-3 mb-3">
    <div class="card h-100">
      <img class="w-100 card-pic ps-2 pe-2" :src="imgSrc" alt="" />
      <hr />
      <div class="card-body d-flex">
        <p class="card-text me-5">{{ title }}</p>
        <p class="text-end ms-5">{{ add }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  // props是負責接收父層傳進的資料，可以直接在DOM中使用
  props: {
    imgSrc: {
      type: String,
      default: "放固定的沒有圖片的假圖URL",
    },
    title: {
      type: String,
    },
    add: {
      type: String,
    },
  },
  setup() {
    return {};
  },
});
</script>

<style scoped lang="scss"></style>
