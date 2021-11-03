<template>
  <p>熱門景點</p>
  <div class="container">
    <div class="row">
      <div class="col col-4">
        <Card
          v-for="(i, index) in sceneList"
          :key="index"
          :imgSrc="i.Picture.PictureUrl1"
          :title="i.Name"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import axios from "axios";
import Card from "@/components/Card.vue";

export default defineComponent({
  components: {
    Card,
  },
  props: {},
  setup() {
    const sceneList = ref([]);
    //在這裡請求景點資料API
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Tourism/ScenicSpot?$top=30&$format=JSON"
      )
      .then((res: any) => {
        console.log(res.data);
        sceneList.value = res.data;
      });
    return {
      sceneList,
    };
  },
});
</script>

<style scoped lang="scss"></style>
