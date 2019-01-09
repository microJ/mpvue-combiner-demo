<template>
  <div class="container">请看控制台打印
    <button @tap="handleTap">点击前往新开页， 查看 onShow、onHide</button>
  </div>
</template>

<script>
import combiner from "@/combiner/";

export default combiner(
  {
    beforeLoad() {
      console.log("this is beforeLoad1");
    }
  },
  {
    beforeLoad() {
      console.log("this is beforeLoad2");
    },
    loaded(){
      console.log("this is loaded")
    }
  },
  {
    data() {
      return {};
    },
    onLoad() {
      console.log("this is onLoad~", 'isReady when onLoad:', this.$data.$isReady);
    },
    onReady() {
      console.log(`this is ${this.$data.$currentLifecycle}~`, 'isReady when onReady:', this.$data.$isReady);
    },
    onLifecycleChange(lifecycle) {
      console.log("onLifecycleChange:", lifecycle);
      if (lifecycle === "onReady") {
        console.log("onLifecycleChange to ready:", this.$data.$isReady);
      }
    },
    methods: {
      handleTap(){
        wx.navigateTo({
          url: "/pages/page1/main"
        })
      }
    }
  }
);
</script>

<style scoped>
</style>
