<template>
  <header class="container mb-3">
    <img src="" alt="" />
  </header>
  <div class="container mb-3">
    <div class="row">
      <div class="col-6">
        <div class="point">
          <img src="https://picsum.photos/id/650/20/20" alt="" />
        </div>
      </div>
      <div class="col-6">
        <div class="point mt-5">
          <img src="https://picsum.photos/id/650/20/20" alt="" />
        </div>
      </div>
    </div>
  </div>

  <!-- 上方按鈕區 -->
  <div class="container selectNav">
    <div class="row h-100">
      <div class="col-12 col-md-3">
        <a href="#" class="btn w-100 miniSelectBtn">
          <div class="d-flex justify-content-around align-items-center">
            <div class="btn tab">
              <img
                class="w-100"
                src="https://picsum.photos/id/684/40/40"
                alt=""
              />
            </div>
            <p>公車動態</p>
            <i class="bi bi-chevron-double-right"></i>
          </div>
        </a>
      </div>
      <div class="col-12 col-md-3">
        <a href="#" class="btn w-100 miniSelectBtn">
          <div class="d-flex justify-content-around align-items-center">
            <div class="btn tab">
              <img
                class="w-100"
                src="https://picsum.photos/id/684/40/40"
                alt=""
              />
            </div>
            <p>站點查詢</p>
            <i class="bi bi-chevron-double-right"></i>
          </div>
        </a>
      </div>
      <div class="col-12 col-md-3">
        <a href="#" class="btn w-100 miniSelectBtn">
          <div class="d-flex justify-content-around align-items-center">
            <div class="btn tab">
              <img
                class="w-100"
                src="https://picsum.photos/id/684/40/40"
                alt=""
              />
            </div>
            <p>票價查詢</p>
            <i class="bi bi-chevron-double-right"></i>
          </div>
        </a>
      </div>
      <div class="col-12 col-md-3">
        <a href="#" class="btn w-100 miniSelectBtn">
          <div class="d-flex justify-content-around align-items-center">
            <div class="btn tab">
              <img
                class="w-100"
                src="https://picsum.photos/id/684/40/40"
                alt=""
              />
            </div>
            <p>公車動態</p>
            <i class="bi bi-chevron-double-right"></i>
          </div>
        </a>
      </div>
    </div>
  </div>
  <!-- 路線搜尋區 -->
  <div class="container">
    <!-- input -->
    <div class="dropdown m-5">
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
    <!--快取按鍵 -->
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
    // const imgsrc = require("../assets/image/326541236.png");
    return {
      // imgsrc,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
