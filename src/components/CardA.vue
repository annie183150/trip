<template>
  <div class="col-12 col-md-4 col-lg-3 mb-3">
    <div class="row">
      <img class="card-pic ps-2 pe-2" :src="imgSrc" alt="" />
      <div class="col section2-col">
        <h3 class="text-start">{{ title }}</h3>
        <hr />
        <div class="col d-flex">
          <p class="text">{{ add }}</p>
          <p class="text">{{ organizer }}</p>
        </div>
        <p class="text-start">時間</p>
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
    organizer: {
      type: String,
    },
    // activityData: {
    //   type: Object,
    //   default: {}
    // },
  },
  setup() {
    return {};
  },
});
</script>

<style scoped lang="scss"></style>
