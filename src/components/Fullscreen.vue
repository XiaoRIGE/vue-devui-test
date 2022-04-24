<template>
  <img alt="Vue logo" src="../assets/logo.png" />
  <h1 style="z-index:99999">以下是协议内容</h1>
  <!-- style="overflow:auto" -->
  <d-fullscreen v-model="isOpen" :z-index="20"   >
    <div class="demo-fullscreen-container">
      <d-button @click="isOpen = !isOpen">{{ btnContent }}</d-button>
      <div id="user-protocol">
        <p v-for="(item,index) in 100">{{`我是第${index}行内容`}}</p>
      </div>
    </div>
  </d-fullscreen>
</template>
<script>
import { ref, watch } from "vue";

export default {
  setup() {
    const isOpen = ref(false);
    const btnContent = ref("全屏");

    watch(isOpen, (newVal) => {
      if (newVal) {
        btnContent.value = "退出全屏";
      } else {
        btnContent.value = "全屏";
      }
    });

    return {
      isOpen,
      btnContent,
    };
  },
};
</script>
<style>
.demo-fullscreen-container {
  margin: 8px;
}
#user-protocol {
  padding: 22px 16px 24px 16px;
  font-size: 1.4rem;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(34, 34, 34, 1);
  line-height: 2rem;
  over-flow:scroll;
}
.demo-fullscreen-container:fullscreen {
  overflow: auto;
  height: 100vh;
}
.demo-fullscreen-container:-webkit-full-screen {
  overflow: auto;
  height: 100vh;
}

</style>
