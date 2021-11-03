<template>
  <div class="home">
    <img src="" alt="" />
    <ul>
      <li></li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"; //下面有用到的方法，這裡都要import
import axios from "axios";

export default defineComponent({
  name: "Home",
  components: {},
  setup() {
    const data = ref({});
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Tourism/ScenicSpot?$top=30&$format=JSON"
      )
      .then((res: any) => {
        console.log(res.data);
        data.value = res.data;
      });
    return {
      data,
    };
  },
});
</script>
