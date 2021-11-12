<template>
  <h2>熱門景點</h2>
  <div class="row">
    <CardH
      v-for="(i, index) in sceneList"
      :key="index"
      :imgSrc="i.Picture.PictureUrl1"
      :title="i.Name"
      :description="i.Description"
      :add="i.City"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import axios from "axios";
import CardH from "@/components/CardH.vue";
import jsSHA from "jssha"; //module

export default defineComponent({
  components: {
    CardH,
  },
  props: {},
  setup() {
    const sceneList = ref([]);
    const header = getAuthorizationHeader() as any;
    //在這裡請求景點資料API
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Tourism/ScenicSpot?$top=4&$format=JSON",
        header
      )
      .then((res: any) => {
        console.log(res.data);
        sceneList.value = res.data;
      });

    //加密herder
    function getAuthorizationHeader() {
      //  填入自己 ID、KEY 開始
      let AppID = "f70ea7bbc4304a718dfa96268dda2944";
      let AppKey = "mFNGIbOt9_GBHtjnhvbw9SD8Lbo";
      //  填入自己 ID、KEY 結束
      let GMTString = new Date().toUTCString();
      let ShaObj = new jsSHA("SHA-1", "TEXT");
      ShaObj.setHMACKey(AppKey, "TEXT");
      ShaObj.update("x-date: " + GMTString);
      let HMAC = ShaObj.getHMAC("B64");
      let Authorization =
        'hmac username="' +
        AppID +
        '", algorithm="hmac-sha1", headers="x-date", signature="' +
        HMAC +
        '"';
      return { headers: { Authorization: Authorization, "X-Date": GMTString } };
    }
    return {
      sceneList,
    };
  },
});
</script>

<style scoped lang="scss"></style>
