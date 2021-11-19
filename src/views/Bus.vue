<template>
  <div class="bus">
    <!-- 傳資料給List子元件 -->
    <BusList
      v-for="(i, index) in data"
      :key="index"
      :iNumber="i.RouteID"
      :iRoad="i.Headsign"
    />
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue"; //下面有用到的方法，這裡都要import
import axios from "axios";
import BusList from "@/components/BusList.vue";
import jsSHA from "jssha";

export default defineComponent({
  name: "bus",
  components: {
    BusList,
  },
  setup() {
    const data = ref({});
    const header = getAuthorizationHeader() as any;
    //在這裡請求景點資料API
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Bus/Route/City/Taichung?$top=1&$format=JSON",
        header
      )
      .then((res: any) => {
        console.log(res.data);
        data.value = res.data;
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
      data,
    };
  },
});
</script>
