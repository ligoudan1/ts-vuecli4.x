<template>
  <div id="app">
    <home></home>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
// 引入home组件
import home from "./home.vue";
// 引入组件装饰器
@Component({
  components:{
    home
  }
})
export default class App extends Vue {

}
</script>

<style lang="scss">
</style>
