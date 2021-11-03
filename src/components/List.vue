<template>
  <div class="list">
    <h1>{{ todoList }}</h1>
    <img :src="imgSrc" alt="" />
    <!-- <img src="https://picsum.photos/id/684/600/400" alt=""> -->
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "List",
  // props是負責接收父層傳進的資料，可以直接在DOM中使用
  props: {
    imgSrc: String,
    todoList: String,
  },
  setup() {
    return {};
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
