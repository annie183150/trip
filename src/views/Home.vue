<template>
  <div class="home">
    <div class="container">
      <div class="dropdown">
        <a
          class="btn btn-secondary dropdown-toggle"
          href="#"
          role="button"
          id="dropdownMenuLink"
          data-bs-toggle="dropdown"
          aria-expanded="false"
        >
          Dropdown link
        </a>

        <ul class="dropdown-menu" aria-labelledby="dropdownMenuLink">
          <li><a class="dropdown-item" href="#">Action</a></li>
          <li><a class="dropdown-item" href="#">Another action</a></li>
          <li><a class="dropdown-item" href="#">Something else here</a></li>
        </ul>
      </div>
      <HotScene />
      <HotFood />
      <HotActivity />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"; //下面有用到的方法，這裡都要import
import HotScene from "@/components/HotScenc.vue";
import HotFood from "@/components/HotFood.vue";
import HotActivity from "@/components/HotActivity.vue";
export default defineComponent({
  name: "Home",
  components: {
    HotScene,
    HotFood,
    HotActivity,
  },
  setup() {
    const data = ref({});

    return {
      data,
    };
  },
});
</script>
