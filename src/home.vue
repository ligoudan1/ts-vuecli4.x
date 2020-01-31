<template>
  <div class="home">
    <div class="btn-group">
      <label>正常：</label>
      <uiBtn @click="onclick">正常</uiBtn>
      <label>大：</label>
      <uiBtn @click="onclick" large>large</uiBtn>
      <label>小：</label>
      <uiBtn @click="onclick" small>small</uiBtn>
      <label>禁用：</label>
      <uiBtn @click="onclick" disabled>disabled</uiBtn>
    </div>
    <div class="btn-group">
      <label>无圆角：</label>
      <uiBtn @click="onclick" tile>tile</uiBtn>
      <label>半圆角：</label>
      <uiBtn @click="onclick" rounded>rounded</uiBtn>
      <label>圆：</label>
      <uiBtn @click="onclick" circle>R</uiBtn>
    </div>
    <div class="btn-group">
        <label>自定义颜色：</label>
        <uiBtn @click="onclick" color="red">red</uiBtn>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
// 引入按钮组件
import uiBtn from "./components/uibtn/ui-btn.vue";
// 引入组件装饰器
@Component({
  components: {
    uiBtn
  }
})
export default class home extends Vue {
  private onclick(event: MouseEvent) {
    console.log(event);
  }
}
</script>

<style lang="scss">
.home {
  width: 100%;
  height: 300px;
  .btn-group {
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: center;
    button {
      margin: 10px;
    }
  }
}
</style>
