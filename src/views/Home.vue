<template>
  <div class="home">
    <div class="container">
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
