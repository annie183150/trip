<template>
  <div class="col-12 col-lg-6 mb-3">
    <div class="row g-0 h-100">
      <div class="col-md-7">
        <img class="w-100 card-pic" :src="imgSrc" alt=" " />
      </div>
      <div class="col-md-6 section2-row">
        <div class="card-body">
          <h5 class="card-title">{{ title }}</h5>
          <p class="card-text">{{ description }}</p>
          <p class="text-start">
            <small class="text-muted">{{ add }}</small>
          </p>
        </div>
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
    description: {
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
