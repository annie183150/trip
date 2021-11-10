<template>
  <h2>熱門美食</h2>
  <div class="container">
    <div class="row">
      <CardA
        v-for="(i, index) in activeList"
        :key="index"
        :imgSrc="i.Picture.PictureUrl1"
        :title="i.Name"
        :add="i.Location"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import axios from "axios";
import CardA from "@/components/CardF.vue";
// import jsSHA from "jssha"      //module

export default defineComponent({
  components: {
    CardA,
  },
  props: {},
  setup() {
    const activeList = ref([]);
    //在這裡請求景點資料API
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Tourism/Activity?$top=10&$format=JSON"
      )
      //   ,{
      //     headers: getAuthorizationHeader()
      //   }
      // )
      .then((res: any) => {
        console.log(res.data);
        activeList.value = res.data;
      });

    // function getAuthorizationHeader() {
    // //  填入自己 ID、KEY 開始
    //     let AppID = 'f70ea7bbc4304a718dfa96268dda2944';
    //     let AppKey = 'mFNGIbOt9_GBHtjnhvbw9SD8Lbo';
    // //  填入自己 ID、KEY 結束
    //     let GMTString = new Date().toGMTString();
    //     let ShaObj = new jsSHA('SHA-1', 'TEXT');
    //     ShaObj.setHMACKey(AppKey, 'TEXT');
    //     ShaObj.update('x-date: ' + GMTString);
    //     let HMAC = ShaObj.getHMAC('B64');
    //     let Authorization = 'hmac username=\"' + AppID + '\", algorithm=\"hmac-sha1\", headers=\"x-date\", signature=\"' + HMAC + '\"';
    //     return { 'Authorization': Authorization, 'X-Date': GMTString };
    // };

    return {
      activeList,
    };
  },
});
</script>

<style scoped lang="scss"></style>
