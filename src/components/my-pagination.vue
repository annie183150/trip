<template>
  <nav aria-label="Page navigation example">
    <ul class="pagination">
      <li class="page-item">
        <a
          @click="changePage(false)"
          aria-label="Previous"
          href="javascript:;"
          class="page-link"
          :class="{ disabled: currentPage === 1 }"
        >
          <span aria-hidden="true">&laquo;</span>
        </a>
      </li>
      <li class="page-item"><span v-if="currentPage > 3">...</span></li>
      <li class="page-item">
        <a
          @click="changePage(item)"
          href="javascript:;"
          :class="{ active: currentPage === item }"
          v-for="item in list"
          :key="item"
          >{{ item }}</a
        >
      </li>
      <li class="page-item"><span v-if="currentPage < pages - 2">...</span></li>
      <li class="page-item">
        <a
          @click="changePage(true)"
          class="page-link"
          aria-label="Next"
          href="javascript:;"
          :class="{ disabled: currentPage === pages }"
        >
          <span aria-hidden="true">&raquo;</span>
        </a>
      </li>
    </ul>
  </nav>
</template>
<script>
import { computed, ref } from "vue";

export default {
  name: "MyPagination",
  props: {
    total: {
      type: Number,
      default: 80,
    },
    pagesize: {
      type: Number,
      default: 10,
    },
    // 默认初始页码
    // page: {
    //   type: Number,
    //   default: 1
    // }
  },
  setup(props, { emit, attrs }) {
    // attrs表示父组件传递的属性，但是props没有接收的属性，这种属性不是响应式的
    // 动态计算中期的页码信息
    // 每页的条数
    // const pagesize = 8
    // 总页数
    const pages = computed(() => Math.ceil(props.total / props.pagesize));
    // 当前页码
    // console.log(attrs.page)
    const currentPage = ref(attrs.page || 1);
    // 动态计算页码列表
    const list = computed(() => {
      // 当父组件传递total的值发生变化时，计算属性会重新计算
      // pages = Math.ceil(props.total / props.pagesize)
      const result = [];
      // 总页码小于等于5；大于5
      if (pages.value <= 5) {
        // 总页码小于等于5的情况
        for (let i = 1; i <= pages.value; i++) {
          result.push(i);
        }
      } else {
        // 总页码大于5
        if (currentPage.value <= 2) {
          // 左侧临界值
          for (let i = 1; i <= 5; i++) {
            result.push(i);
          }
        } else if (currentPage.value >= pages.value - 1) {
          // 右侧临界值
          for (let i = pages.value - 4; i <= pages.value; i++) {
            result.push(i);
          }
        } else {
          // 中间的状态
          for (let i = currentPage.value - 2; i <= currentPage.value + 2; i++) {
            result.push(i);
          }
        }
      }
      return result;
    });
    // 控制上一页和下一页变化
    const changePage = (type) => {
      if (type === false) {
        // 上一页
        // 页面是第一页时，禁止点击操作
        if (currentPage.value === 1) return;
        if (currentPage.value > 1) {
          currentPage.value -= 1;
        }
      } else if (type === true) {
        // 下一页
        // 页面是最后页时，禁止点击操作
        if (currentPage.value === pages.value) return;
        if (currentPage.value < pages.value) {
          currentPage.value += 1;
        }
      } else {
        // 点击页码
        currentPage.value = type;
      }
      emit("change-page", currentPage.value);
    };
    return { list, currentPage, pages, changePage };
  },
};
</script>
<style></style>
