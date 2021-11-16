<template>
  <h2>熱門美食</h2>
  <div class="row">
    <CardF
      v-for="(i, index) in foodList"
      :key="index"
      :imgSrc="i.Picture.PictureUrl1"
      :title="i.Name"
      :add="i.City"
    />
  </div>
  <div class="home-container">
    <MyPagination
      @change-page="changePage"
      :pagesize="10"
      :total="80"
      :page="1"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import axios from "axios";
import CardF from "@/components/CardF.vue";
import jsSHA from "jssha"; //module

export default defineComponent({
  components: {
    CardF,
  },
  props: {},
  setup() {
    const foodList = ref([]);
    const header = getAuthorizationHeader() as any;
    //在這裡請求景點資料API
    axios
      .get(
        "https://ptx.transportdata.tw/MOTC/v2/Tourism/Restaurant?$top=4&$format=JSON",
        header
      )
      .then((res: any) => {
        console.log(res.data);
        foodList.value = res.data;
      });
    // // 筛选条件准备
    // const reqParams = ref({
    //   // 当前页码
    //   page: 1,
    //   // 每页的条数
    //   pageSize: 10
    // })
    // // 控制页码的变化
    // const changePage = (page) => {
    //   // 修改分页参数，重新调用接口即可
    //   // console.log(page)
    //   reqParams.page = page
    // }

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
      foodList,
      // changePage ,
    };
  },
});
</script>

<style scoped lang="scss"></style>
