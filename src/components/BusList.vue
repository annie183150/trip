<template>
  <div class="dropdown">
    <a
      class="btn btn-bus dropdown-toggle"
      href="#"
      role="button"
      id="dropdownMenuLink"
      data-bs-toggle="dropdown"
      aria-expanded="false"
    >
      搜尋路線
    </a>

    <ul class="dropdown-menu bus-menu" aria-labelledby="dropdownMenuLink">
      <li><a class="dropdown-item" href="#">202</a></li>
      <li><a class="dropdown-item" href="#">203</a></li>
      <li><a class="dropdown-item" href="#">203</a></li>
      <li><a class="dropdown-item" href="#">203</a></li>
    </ul>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-12 col-md-3 m-3">
        <a href="#" class="btn miniSelectBtn">
          <div class="d-flex align-items-center">
            <div class="btn tab">
              <img src="https://picsum.photos/id/684/40/40" alt="" />
            </div>
            <p>公車動態</p>
            <i class="bi bi-chevron-double-right"></i>
          </div>
        </a>
      </div>
      <div class="col-12 col-md-3 m-3">
        <a href="#" class="btn miniSelectBtn">
          <div class="d-flex align-items-center">
            <div class="btn tab">
              <img src="https://picsum.photos/id/684/40/40" alt="" />
            </div>
            <p>公車動態</p>
            <i class="bi bi-chevron-double-right"></i>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  // props是負責接收父層傳進的資料，可以直接在DOM中使用
  props: {
    iNumber: {
      type: String,
    },
    iRoad: {
      type: String,
    },
  },
  setup() {
    return {};
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
