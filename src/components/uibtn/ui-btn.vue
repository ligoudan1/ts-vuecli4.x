<template>
  <!-- <button class="ui-btn" v-on="$listeners">button</button>接受外部点击事件（不推荐） -->
  <button
    class="ui-btn"
    :class="{
        'ui-large':large,
        'ui-small':small,
        'ui-disabled':disabled,
        'ui-tile':tile,
        'ui-rounded':rounded,
        'ui-circle':circle
        }"
    :style="`--color-init:${Tintcolor}`"
    @click="btnOnClick"
  >
    <!-- 使用插槽填充按钮名称 -->
    <slot>button</slot>
  </button>
</template>

<script lang="ts">
import { Component, Vue, Emit, Prop } from "vue-property-decorator";

// 引入组件装饰器
@Component({})
export default class uiBtn extends Vue {
  @Prop(Boolean) large: boolean | undefined;
  @Prop(Boolean) small: boolean | undefined;
  @Prop(Boolean) disabled: boolean | undefined;
  @Prop(Boolean) tile: boolean | undefined;
  @Prop(Boolean) rounded: boolean | undefined;
  @Prop(Boolean) circle: boolean | undefined;
  @Prop(String) color: string | undefined;

  
  //使用计算属性改变color颜色
  private get Tintcolor() {
      if (this.color) {
          return this.color;
      } else {
          return '#1059cf'
      }
  }
  @Emit("click")
  private emitClick(event: MouseEvent) {}
  private btnOnClick(event: MouseEvent) {
    // 解决禁用按钮点击事件
    !this.disabled ? this.emitClick(event) : null;
  }
}
</script>

<style lang="scss">
// 使用scss函数
@mixin resize($width, $height, $padding, $minWidth) {
  width: $width;
  height: $height;
  padding: 0 $padding;
  min-width: $minWidth;
}
.ui-btn {
  @include resize(64px, 34px, 16px, 64px);
  border: 0px;
  border-radius: 4px;
  font-size: 0.875rem;
  color: #000;
  background-color: var(--color-init,#1059cf);
  cursor: pointer;
  user-select: none;
  outline: none;
  &.ui-large {
    @include resize(80px, 45px, 16px, 64px);
  }
  &.ui-small {
    @include resize(50px, 25px, 0px, 0px);
  }
  &.ui-disabled {
    padding: 0px;
    color: #c0c4cc;
    cursor: not-allowed;
    background-image: none;
    background-color: #ebeef5;
  }
  &.ui-tile {
    padding: 0;
    border-radius: 0px;
  }
  &.ui-rounded {
    padding: 0;
    border-radius: 17px;
  }
  &.ui-circle {
    @include resize(30px, 30px, 0px, 0px);
    border-radius: 50%;
  }
}
</style>
