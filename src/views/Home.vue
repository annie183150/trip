<template>
  <div class="home">
    <img src="" alt="" />
    <HotScene />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"; //下面有用到的方法，這裡都要import
import HotScene from "@/components/HotScenc.vue";
export default defineComponent({
  name: "Home",
  components: {
    HotScene,
  },
  setup() {
    const data = ref({});

    return {
      data,
    };
  },
});
</script>
