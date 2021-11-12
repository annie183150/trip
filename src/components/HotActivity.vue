<template>
  <h2>近期活動</h2>
  <div class="row">
    <CardA
      v-for="(i, index) in activeList"
      :key="index"
      :imgSrc="i.Picture.PictureUrl1"
      :title="i.Name"
      :add="i.City"
      :organizer="i.Organizer"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import axios from "axios";
import CardA from "@/components/CardA.vue";
import jsSHA from "jssha"; //module

export default defineComponent({
  components: {
    CardA,
  },
  props: {},
  setup() {
    const activeList = ref([]);
    const header = getAuthorizationHeader() as any;
    //在這裡請求景點資料API
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Tourism/Activity/Taichung?$top=10&$format=JSON",
        header
      )
      .then((res: any) => {
        console.log(res.data);
        activeList.value = res.data;
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
      activeList,
    };
  },
});
</script>

<style scoped lang="scss"></style>
